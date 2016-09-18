## Tips

Be verbose in your init scripts. It helps track down problems

--

Use `security-template: unconfined` in your interfaces at the beginning, to set things up, then try to make it work with the restrictions put in place by Snappy.

## Pitfalls

All custom commands use a wrapper which changes the working dir to $SNAP_DATA, so you must give a path as an argument if you expect an output in the folder your script is working in

*Note: should be fixed in Snappy 2.0*

--

A reboot may not stop daemons properly and services may not start properly if the pid from a previous session is still there.

--

When working on a single part, you may get an error message about conflicting folder content when reaching the staging stage. It's very likely that one of your dependencies has been updated while the the other part still contains references to the old packages. Just `snappy clean` the relevant parts.

--

Only rely on Debian packages for libraries and compile all the apps you want to include as parts. There are, of course, exceptions, but apps which have lots of libraries and configuration files won't be so portable when installed from pre-defined packages.

--

If your daemon fails to be loaded it could be because:
* It's not executable
* It contains Windows EOL. Make sure you use LF

--

It's not possible to check if your "staged" binaries are properly linked unless you use LD_LIBRARY_PATH

--

Do not strip libtool's `.la` files from the snap

--

**Always** clean (most) parts **before** switching branch