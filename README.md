# Bitwig Overlay
Bitwig is one of the few delivering commercial studio software for Linux. Software is available as .deb-files and updated quite regular. The purpose of this overlay is to simplify the installation and upgrade of Bitwig Studio and possibly accompanying software later on.

# Usage instuctions
## Dependencies

This is an overlay developed and tested on Funtoo Linux. It should probably work very well in Gentoo and Sabayon Linux as well, however I have no means to verify that. 

Overlays in general depends on layman and the assumption here relies on layman being installed. 


## Installation
### Layman
A non official overlay (as this is) is not directly fetchable with layman. You have to manually register the overlay. 

Start by copying  `bitwig-overlay.xml` into `/etc/layman/overlays`

Run `layman-updater -R` to re-read the overlay-directory.

You will now also have to run `layman -L` to list all overlays or layman will not find syncthing-overlay. 

Finally add the overlay to portage: `layman -a bitwig-overlay`

As a security measure layman will ask for confirmation before this overlay is added. 

You can now install included applications as usual using emerge.

### Git
You can install it using Gentoo's git sync mechanism as well. Just:

```bash
# create the appropriate directory
mkdir /etc/portage/repos.conf.d

# install the repo file
cat << EOF > /etc/portage/repos.conf.d/bitwig-overlay.repo
[bitwig-overlay]
location = /usr/local/portage/bitwig-overlay
sync-type = git
sync-uri = https://github.com/bitwigstudio/bitwig-overlay.git
auto-sync = yes
EOF

# sync it 
emaint sync -r bitwig-overlay

# install it
emerge bitwig-studio
```

# Bug, comments and requests
Please post a ticket here on GitHub. 