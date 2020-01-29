# jbackup

A small shell script for building and executing rsync runs in a generic way.

## Usage

jbackup takes a single argument - a path to a 'profile' which is just a shell
script with the following variables and methods defined:

```
# Arguments passed directly to rsync
RSYNC_SRC="..."
RSYNC_DEST="..."
RSYNC_OPTIONS="..."

# Shell functions called before and after rsync executes
pre_command() {
	# mount drives or prepare for sync
}
post_command() {
	# umount drives or perform cleanup commands
}
```

See [profiles/](profiles/) in this repo for profile examples. I recommend
placing your custom profiles in `$HOME/.jbackup/`

## Behavior

jbackup must be run as root. jbackup will abort executing your profile if
either `rsync`, `pre\_command`, or `post\_command` return a non-zero value. 

I recommend using `set -e` in your post/post commands so jbackup aborts when an
error is encountered.

## Motivation

jbackup is useful when rsync runs need an initial setup and teardown process,
for example mounting and umounting drives. jbackup was created to centralize a
number of standalone scripts I had accumulated that executed nearly the same
commands but with slightly different arguments. With jbackup this functionality
now exists in simple standardized profile modules.
