When working on snaps, you may have to set the executable bit on some of your scripts. Some IDEs then ignore those changes and push your files with the 0644 mask. The solution is to commit from a tool like git bash.

### Get current permissions

```
$ git ls-files --stage src/php
100644 905d81cad99f841f991b0f6035c60c00437e0e7d 0       php/shell.php
```

### Change permissions

```
$ git update-index --chmod=+x src/php/shell.php
100755 905d81cad99f841f991b0f6035c60c00437e0e7d 0       php/shell.php
```

### Commit

```
$ git commit -m "Add a PHP shell
> Fixes #58532"
[php-shell b16dce5] Add a PHP shell Fixes #58532
 1 files changed, 784 insertions(+), 50 deletions(-)
 create mode 100755 src/php/shell.php
```