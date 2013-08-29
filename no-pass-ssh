#!/bin/bash

## no-pass-ssh | set up ssh keys such that a password is no longer required upon login from this host
## written by nydel - direct mail to nydel.no-pass-ssh@isismelting.com
## version 1.0.1a - open source utility okay for fair use
## dependent upon openssh - written on version 6.0p1 on debian/ubuntu linux

echo && echo "[no-pass-ssh] - make ssh connections without being prompted for password"
read -p "[no-pass-ssh] - syntax: \"no-pass-ssh {login@hostname}\" - (ctrl-c) to abort" && echo
myArray=("$@")
REMOTELOGPASS="${myArray[0]}"
MYUSERNAME=`echo $USER`
read -p "[no-pass-ssh] - press (return) through the prompts to follow:" && echo
ssh-keygen -t rsa -P ""
echo && read -p "[no-pass-ssh] - good; now you will be prompted twice to enter your password:" && echo
MYFILEPUB=`echo "/home/$MYUSERNAME/.ssh/id_rsa.pub"`
ssh $REMOTELOGPASS mkdir -p .ssh
cat $MYFILEPUB | ssh $REMOTELOGPASS 'cat >> .ssh/authorized_keys'
echo && echo "[no-pass-ssh] - try \"ssh {login@hostname}\" now:"
read -p "[no-pass-ssh] - you should no longer be prompted for a password!" && echo
