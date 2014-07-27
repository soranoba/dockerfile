Git
==========

## About
The environment that you can use Git.

installed:
- git
- git contrib
 - diff-highlight
 - workdir
 - completion

In addition, copy git and ssh settings to guest OS from host OS.

## Compile
If you want different version of the OS that is already exist this repository, please look at the Makefile.

```:Makefile
1: OS = ubuntu.... <- add here.
```

Please add your desired version and execute "make".

## Run

```bash
$ cd ubuntu:12.04
$ make
```

[Please look here for more information.](../#how-to-use)
