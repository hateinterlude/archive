# How to Create a Windows VM using LXD (Ubuntu)

These instructions are straightforward for creating a Windows 11 virtual machine off the bat, read comments under commands if you would like guidance on how to change anything else

## Requirements:
Windows 11 ISO - download [here](https://www.microsoft.com/en-us/software-download/windows11) <br/>
> or use any Windows ISO of your choice
LXD: `snap install lxd` <br/>
Distrobuilder: `snap install distrobuilder --classic` <br/>
A Spice client to view your VM: `sudo apt-get install -y --no-install-recommends virt-viewer` <br/>
> You can use virt-viewer or any other Spice client

## Creating the VM
Run these commands in order:
`sudo distrobuilder repack-windows [PATHTOTHEISOHERE] win11.iso`
> change win11 to whatever name you'd like

`sudo lxd init`
> hit ENTER for everything (default settings) unless you want to change anything

`sudo lxc init win11 --empty --vm -c security.secureboot=false -c limits.cpu=4 -c limits.memory=8GB`
> win11 is the name of the VM, you can change this to whatever you want <br/>
change `security.secureboot` to true if you'd like secure boot enabled <br/>
change `limits.cpu` to how many cores you want for your VM <br/>
change `limits.memory` to how many GB you would like to allocate for your VM <br/>
`sudo lxc config device add win11 vtpm tpm path=/dev/tpm0` <br/>
> this enables TPM and is a requirement for installing regular Windows 11, skip if not installing an OS that requires TPM <br/>
`sudo lxc config device override win11 root size=50GB` <br/>
> change `size` to how big you want your virtual drive to be, recommended is 52GB <br/>
`sudo lxc config device add win11 install disk source=[ABSOLUTEPATHTOYOURPACKEDISO] boot.priority=10`
> [ABSOLUTEPATHTOYOURPACKEDISO e.g. /home/[YOURUSERHERE]/Downloads/win11.iso <br/>
`sudo lxc start win11` <br/>
`sudo lxc console win11 --type=vga` <br/>
> if you have an error when running this command, run `xhost + local:` and run `sudo lxc console win11 --type=vga` again <br/>

Hit any key to run the installer from the ISO
Once Windows is installed, stop your VM (see below) and remove the install drive with:
`sudo lxc config device remove win11 install`

## Post-Creation
Starting and Stopping the VM:
`sudo lxc stop [YOURVMNAME] --force`
> stop the VM
`sudo lxc start [YOURVMNAME]`
> start the VM
`sudo lxc console [YOURVMNAME] --type=vga`
> open the display for the VM
`sudo lxc delete [YOURVMNAME]`
> delete your VM

## Post installation (Windows 11)
### I do not want to sign in to my Microsoft account
Hit SHIFT+F10 to open CMD and type one of the following commands:
`start ms-cxh:localonly​` OR `start ms-cxh://setaddlocalonly​`
Type in your preferred username and password if you'd like
Click no for everything analytics wise and send only required data


