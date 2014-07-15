dockerfile
==========

## About
dockerで作った作業環境。

## How to use
#### Requires
- [docker](http://docker.io)
- make

#### Build

```
$ make
```

dockerはデフォルトでsudo実行しないといけない為、うまくいかない場合はsudo makeを試してください。

#### Run

```
$ make run
```

## Module
### erlang
erlang + hipe + emacs + erlang-mode + [git](#git) + rebar

- erlang 17.01
 - Ubuntu 14.04

- erlang R16.03b
 - Ubuntu 12.10

<a name="git">
### git
git + git_completion

- Ubuntu 12.10

Copy to guest OS from host OS's git and ssh settings. 

## Licence
MIT Licence

お好きにどうぞ。
