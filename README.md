Usage: klone [options] <name> <version>

This program does a git clone of a repository to have possibly multiple version (tags/branches)
of the same repo.

Options can be:
       --ssh         git clone using ssh (the default)
       --https       git clone using https

Configuration:
If a file ~/.config/klone/klone.conf exists, this file is sourced.
This can typically be used to set the following variables:
- **KLONE_DEFAULT_DIR**
- **KLONE_DEFAULT_SSH_REPO**
- **KLONE_DEFAULT_HTTPS_REPO**
These DEFAULT vars are used to set the following vars, if they are not set.
This way the defaults in klone.conf, will not be used if these var are set
- **KLONE_DIR** : the directory in which all clones will be stored (default ~/klone )
- **KLONE_SSH_REPO** : the repository when doing a git clone using ssh protocol
- **KLONE_HTTPS_REPO** : the repository when doing a git clone using https protocol

- **KLONE_PROTO** : default protocol if not specified (default is ssh)
- **KLONE_REPO_PSW** : password that is used when git asks for a password with https checkout
