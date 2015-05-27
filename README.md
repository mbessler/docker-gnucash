# GnuCash in a Container

Dockerized GnuCash (http://www.gnucash.org). Currently based on Ubuntu 15.04.

## Building:
* `docker build -t gnucash .`

## Running:
* Allow Xlib calls from container: `xhost +LOCAL:`
* Start GnuCash in containter: 
  * `docker run --rm --name gnucash -e DISPLAY=unix$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix   gnucash`
* Or, mach user from host and map $HOME to $HOME/gnucash-home on host:
  * `mkdir ~/gnucash-home`
  * `docker run --rm --name gnucash -e DISPLAY=unix$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix -v /etc/passwd:/etc/passwd -v /etc/group:/etc/group  -e HOME=${HOME} -e USER=${USER} -e LOGNAME=${LOGNAME} -u ${USER} -v /where/you/keep/your/gnucash_files:/gnucash gnucash -v $HOME/gnucash-home:$HOME  gnucash  [options] /gnucash/[gnucash file]` 
