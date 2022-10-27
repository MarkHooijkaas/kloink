# `kloink`: Klone/Link specific versions of git repositories
The idea of `kloink` is that you install a specific version of a git repository
using git clone into a central dir.
This clone can be used in multiple places using a link to the cached version.

Kloink has several goals
- easy to use
- robust for all kinds of situation
- flexible, but will work with minimal configuration
- can be used from commandline, but also in automated build scripts.
Just type:
```
kloink <appname> <version>
```

# Usage
Usage: kloink [options] <name> <version>

This program does a git clone of a repository to have possibly multiple version (tags/branches)
of the same repo.

Options can be:
       --ssh         git clone using ssh (the default)
       --https       git clone using https

# Configuration:
kloink has several options.
These can be set in several manners:
- using command line options (many still need to be implemented)
- through environment variables starting with `KLOINK_`
- in a config file called `~/.config/kloink/kloink.conf`
- using sane defaults

## environment variables
The most important variables are:
- `KLOINK_DIR`: the directory in which all clones will be stored (default ~/.cache/kloink )
- `KLOINK_KLONE_PROTOCOL`: The `git clone` protocol if not specified (default is ssh)
- `KLOINK_SSH_REPO`: the repository when doing a git clone using ssh protocol
- `KLOINK_HTTPS_REPO`: the repository when doing a git clone using https protocol
- `KLOINK_REPO_PSW`: password that is used when git asks for a password with https checkout

## Config file `~/.config/kloink/kloink.conf`
This config file is sourced at the beginning of kloink.
In this file you should not override any of the above vars,
because this will make it impossible to use a different var in your environment.
You can do this:
```
# do not override KLOINK_DIR if it is already set
KLOINK_DIR=${KLOINK_DIR:-my-own-value}
```
or similar in bash:
```
# use bash default value mechanism, and colon to not evaluate this line
: ${KLOINK_DIR:=my-own-value}
```

A final option is to use special default variables that are only used if the
normal var is not set, e.g
```
KLOINK_DEFAULT_DIR=my-own-value
```

This can be used to set the following variables:
- `KLOINK_DEFAULT_DIR`
- `KLOINK_DEFAULT_SSH_REPO`
- `KLOINK_DEFAULT_HTTPS_REPO`
These DEFAULT vars are used to set the following vars, if they are not set.
This way the defaults in kloink.conf, will not be used if these var are set
