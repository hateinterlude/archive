# How to Create a Windows VM using LXD (Ubuntu)

Requirements:
Windows 11 ISO - download [here](https://www.microsoft.com/en-us/software-download/windows11)

`snap install distrobuilder --classic`
sudo distrobuilder repack-windows /path/to/iso win.iso

sudo lxd init
hit ENTER for everything (default settings) unless you want to change anything

sudo lxc init win11 --empty --vm -c security.secureboot=false -c limits.cpu=4 -c limits.memory=4GB
sudo lxc config device add win11 vtpm tpm path=/dev/tpm0
sudo lxc config device override win11 root size=50GB
sudo lxc config device add win11 install disk source=/home/user/Downloads/win11.iso boot.priority=10
sudo lxc start win11
sudo lxc console win11 --type=vga

if error: xhost + local:

Hit any key to run the installer
Once installed you can remove the install drive with:
`sudo lxc config device remove win11 install`

Starting and Stopping the VM
sudo lxc stop win11 --force
sudo lxc start win11
sudo lxc console win11 --type=vga

Deleting the VM:
sudo lxc delete win11

Click no for everything and send only required data

After installation
SHIFT+F10
start ms-cxh:localonly​
start ms-cxh://setaddlocalonly​


