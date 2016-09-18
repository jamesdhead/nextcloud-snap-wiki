The world of Snappy is a brave new world - a very different environment to work in for a package or image developer. To help make it easier to navigate the Snappy world, this article provides a basic introduction (and links to more) as well as a walk-through of the process of building a Snap.

In order to be able to build some snaps, please begin by [setting up a development environment](https://github.com/nextcloud/nextcloud-snap/wiki/Creating-a-Snappy-development-environment)

## The basics

Snappy Ubuntu Core provides a base OS on which applications (snaps) are mounted as read-only images. A snap can not depend on other snaps so each contains all it needs beyond the base OS and is completely isolated from it. That is, in simple terms: if you ssh into a system running a Nextcloud snap (which comes with PHP, Apache and MySQL), running the php command will return a 'command not found'! Neither could the Nextcloud instance modify any of its own files, except those specifically put in a writable area. When upgrading, a new snap just replaces the old and hooks into the writable area of the old one. Upgrades are thus atomic and can be rolled back easily in case of problems. If you have multiple server snaps running, say one with Nextcloud and one with Drupal, on one system, you will have two Apache's, two mysql's and so on. Ubuntu Snappy uses a variety of clever tricks to keep the overhead under control, including automatic data de-duplication and memory sharing. Please visit the Ubuntu website to get the [big picture on Snappy](https://developer.ubuntu.com/en/snappy/).

Snaps are a great way to deploy and manage software, but you will need to be familiar with the following technologies:

* File system permissions
* Bash scripting
* Debian packaging
* Python and or Go
* Daemons 

## So how does building a Snap work?

### Overview

It starts with creating a folder structure with the source you want to build and the `snapcraft.yaml` file. This file is a recipe which is used to generate the snap from the source and whatever else you want it to pull in. snapcraft will take care of as much of the background work like pulling in dependencies as possible. So 'anything' includes things like packages of course, but a snapcraft can take care of building from source just as well.

### Step 1: get Snapcraft

```
$ sudo apt install snapcraft
```

### Step 2: create your project structure

Create a project directory and source directory

*Note: It's best practice to create your project in a folder which will contain all your snaps*

```
$ mkdir awesome-app
$ cd awesome-app 
$ mkdir src
$ cd src
```

*Note: We're going to use a C++ example as it doesn't require installing a PHP environment in the Snap*

Create a new file `main.cpp` with this content:

```
#include <iostream>

int main()
{
	std::cout << "Hello, world!" << std::endl;
	return 0;
}
```

And now create a `Makefile` with this content:

```
all: foo

foo:
	@g++ main.cpp -o foo

install:
	@mkdir -p $(DESTDIR)/bin
	@cp foo $(DESTDIR)/bin/

clean:
	@rm foo
```

*Note: Make sure all white space in front of the `@` signs are tabs, not spaces. You have to change this if you copy-paste from here per example.*

### Step 2b: optionally, build it to test

Install g++ and make to see if you can build main.cpp yourself:

```
$ sudo apt install g++ make
```

Now build the C++ file:

```
$ make
```

This should build the main.cpp and you get a 'foo' file you can execute which will tell you "Hello, world!":

```
$ ls
Makefile  foo  main.cpp  src
$ ./foo
Hello, world!
```

### Step 3: set up the snap

Go to the initial build folder (parent of src); install golang and init a snap folder

```
$ cd ..
$ sudo apt install golang-go
$ snapcraft init
```

This has created a very basic skeleton. Let's edit the snapcraft.yaml file:

```
name: awesome-app # you probably want to 'snapcraft register <name>'
version: '0.1' # just for humans, typically '1.2+git' or '1.3.2'
summary: My 1st snap ever # 79 char long summary
description: |
  This is my-snap's description. You have a paragraph or two to tell the
  most important story about your snap. Keep it under 100 words though,
  we live in tweetspace and your description wants to look good in the snap
  store.

grade: devel # must be 'stable' to release into candidate/stable channels
confinement: strict # use 'strict' once you have the right plugs and slots

apps:
  foo:
    command: foo
  
parts:
  foo:
    plugin: make
    source: src/
    build-packages:
     - g++
```

This part you can copy-paste as-is: yaml files use spaces.

The crucial section here is the parts section. It tells snapcraft there's one component to the snap `foo` which has to be built using the plugin `make` and can be found in the folder `src`; building will need `g++`. Note that this folder can have any name - you could've called it `foo` as well.

The 'apps' section will essentially export the 'foo' command outside of the snap and make it possible for users to call it from the command line. It will still run <strong>within</strong> the snap, though, isolated from everything else on the system.

You can comment out things like the icon but feel free to experiment!

### Step 4: build the snap

#### Fetching the files

Each part is composed of one or more deb package, source archive, git clone,

```
$ snapcraft pull
```

This will have created a `parts/foo/src` folder where the source is now located, ready for building (in the form of a link. In case of source from, say, git, it will download it).

#### Compiling each "part"

```
$ snapcraft build
```

This will have created a `parts/foo/install/foo` - the binary output of make.

#### Staging the parts

```
$ snapcraft stage
```

This will, if there are multiple parts, bring them into a common staging area in the `stage` folder.

#### Stripping binaries

```
$ snapcraft prime
```

Will turn the staging area into a final directory ready to be snapped. It will have a new folder, `prime` which includes commands, stripped binaries and metadata for the snap including icons and such.

#### Creating the snap

```
$ snapcraft snap
```

To create the final snap.

#### Quickest way to build a snap

You don't actually have to go through all these steps by hand: running `snapcraft` will execute all of them automatically.

*Note: You can target specific plugins by adding the plugin's name at the end of the command: `snapcraft stage apache`*

### Step 5: install the snap

Once done, you can install the snap typing:

```
$ sudo snap install awesome-app_0.1_amd64.snap --force-dangerous
```

If you've uploaded your snap to the snap store and signed it, you can just run:

```
$ sudo snap install foo
```

At this stage, you can call `awesome-app.foo` from the command line and it will execute like a normal command. Note that the first time, it creates the writable folders it needs, now and in the future and does that with the permissions of the user you first run it with. If you happen to use `sudo`, for example, the next run will also need root capabilities! You can delete the symlink and run the app again.

At this point, you've created and installed your first snap and the basic principles should be clear! Let's do one more 'advanced' thing before we wrap up.

If you now look in `/snap/bin` you find the binary for your snap and you can execute it. This uses the ubuntu container launcher to run your binary and it contains environment variables you can modify, as (super) user.

### Adding extra files

Here is how you could ship some configuration files with your Snap.

First create the files

```
# touch config1 config2
```

And use the copy plugin to copy them over from your work directory to the Snap itself.
```
	config:
		plugin: copy
		files:
			config1: config/1
			config2: config/2
```

Note that you could have named the part something other than `config`.

Also, the config files can be in the same folder as the yaml (like we just did), or in a folder under it.

On the right side, `config/1` tells snapcraft to put the file in that folder, relative to the root of the Snap.

You might want to run `snapcraft clean` before building a new snap, of course.

Note that after installing it, there will be two snap folders in `/snap/awesome-app`, one for each version and the symlink to the command in `/snap/bin` will still be the old one.

Run `snapcraft help plugins` for a list of plugins and `snapcraft help make` to get info on a specific plugin and how to use it.

### Making changes to a single part

You don't need to rebuild everything after having made changes to a part.
Simply run `snapcraft clean foo` followed by `snapcraft` in order to build a new snap after having made changes to the foo part. `snapcraft` is smart enough to not rebuild parts which have been snapped already.


## More information

* If you want to practice some more, [here is another tutorial](https://developer.ubuntu.com/en/snappy/build-apps/your-first-snap/) on the Snappy website
* Curious about the snapcraft.yaml syntax? [There is a page for that](https://developer.ubuntu.com/en/snappy/build-apps/snapcraft-syntax/)
* Snapcraft "parts" got you intrigued? [Here is a detailed overview](https://developer.ubuntu.com/en/snappy/build-apps/snapcraft-parts/)

## Time to get to work

Now you've learned the basics of the OS behind the Nextcloud box: Ubuntu Snappy. You can go in and [modify your Nextcloud](https://github.com/nextcloud/nextcloud-snap/wiki/Building-your-first-Nextcloud-snap); more importantly, you know how we make our snaps and how you could contribute to that! 
