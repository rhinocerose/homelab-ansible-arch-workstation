# Automated ArchLinux 
This ansible playbook automates my personal Arch Linux installation. 
The goal is a fully encrypted and secure desktop system.  All
dotfiles are kept in an independent repository. They are managed using
[rcm](https://robots.thoughtbot.com/rcm-for-rc-files-in-dotfiles-repos) and 
will only get installed if the `dotfiles` variable is defined.

## System overview
* Full disk encryption
* LVM on LUKS partitioning scheme
* Plymouth support for a nice boot screen

## Special configuration
* Customized i3 window manager with
[i3status-rs](https://github.com/greshake/i3status-rust) bar
* z-shell with automatic oh-my-zsh integration
* `rxvt-unicode` and `kitty` true color terminals
* `tmux` with vim bindings

## Additional security features
* Sensitive and internet facing applications are sandboxed using firejail
* Restrictive and comprahensive iptables rules
* Use of linux-hardened
* Automatic mac address spoofer for wireless network devices
* No bullshit installed

## Install base system

You can eighter install your own minimal system or you follow the instructions
provided in the two installation guides below.

* [INSTALL\_BIOS](/doc/INSTALL_BIOS.md)
to setup a LVM on LUKS system using syslinux in MBR BIOS boot mode.
* [INSTALL\_EFI](/doc/INSTALL_EFI.md)
to setup a LVM on LUKS system using grub2 in GPT EFI boot mode.

The Ansible playbook does not depend on any specific installation method.

## How to run the ansible playbooks

First install ansible 

``` bash
$ sudo pacman -S ansible 
``` 

then download the playbook and make sure you adjust the values of the global 
config in `group_vars/all` to match your system stats. Then run it.

``` bash
$ git clone --recurse-submodules -j8 https://github.com/id101010/ansible-archlinux.git 
$ cd ansible-archlinux/ansible
$ ansible-playbook -i inventory/localhost playbook.yml [--tags $LIMIT_TO_TAG]
``` 

Lean back and watch the installation.
