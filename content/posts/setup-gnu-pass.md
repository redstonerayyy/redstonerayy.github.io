---
title: Setup GNU Pass
releasedate: "13.10.23"
lastchanged: "13.10.23"
type: post
summary: "Explains in detail on how to setup the GNU Pass password manager. Shows the most important commands and how to import and export GPG Keys."
---

### setup

```sh
sudo pacman -Syu pass # install gnu pass
gpg --gen-key  # generate key; choice of name, ... not important; use secure password
gpg -K # list keys and their ids
gpg --edit-key <key-id> # change expiration date to `never expire`
gpg> expire # use expire command in key menu
gpg> 0 # select never expire
pass init <key-id> # initialize new password store
pass git init # use git for versions/rollbacks
```

## usage

```sh
pass insert github # open prompt to insert a password into the store
pass generate <name or path> # e.g. pass generate github/work
pass find <term> # search for password entries
pass grep "<some search for all files>"
pass edit <name or path> # edit password e.g. add email or other information
pass show <name or path> # prints whole password file to stdout
pass show -c <name or path> # copy first line (password) to clipboard
pass rm <name or path> # remove password
```

## export gpg keys

```sh
gpg --output public.pgp --armor --export <email/id of key> # export public key
gpg --output private.pgp --armor --export-secret-key <email/id of key> # export private key
```

## import gpg keys

```sh
gpg --import private.pgp # import private key; requires the password of it
gpg --import public.pgp # import public key
gpg --edit-key <key id> # trust the key to add new password on other maschines
gpg> trust # trust command in gpg menu
gpg> 5 # highest trust level
```

## shell hacks

```sh
export VARIABLE=$(pass show my/nice/api/token)
```
