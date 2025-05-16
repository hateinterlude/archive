# How to Create a Windows VM using LXD (Ubuntu)

These instructions are straightforward for creating a Windows 11 virtual machine off the bat, read comments under commands if you would like guidance on how to change anything else

## Requirements:
- Windows 11 ISO - download [here](https://www.microsoft.com/en-us/software-download/windows11)
> Or use any Windows ISO of your choice

- LXD: 
```
snap install lxd
```

- Distrobuilder: 
```
snap install distrobuilder --classic
```

- A Spice client to view your VM:
```
sudo apt install virt-viewer
```
> You can use `virt-viewer` or any other Spice client

## Creating the VM
Run these commands in order:
```
sudo distrobuilder repack-windows [PATHTOTHEDOWNLOADEDISOHERE] win11.iso
```
> Change `win11` to whatever name you'd like, if you want

```
sudo lxd init
```
> Hit ENTER for everything (default settings) unless you want to change anything

```
sudo lxc init win11 --empty --vm -c security.secureboot=false -c limits.cpu=4 -c limits.memory=8GB
```
> `win11` is the name of the VM, you can change this to whatever you want <br/>
Change `security.secureboot` to true if you'd like secure boot enabled <br/>
Change `limits.cpu` to how many cores you want for your VM <br/>
Change `limits.memory` to how much GB you would like to allocate for your VM <br/>

```
sudo lxc config device add win11 vtpm tpm path=/dev/tpm0
```
> This enables TPM and is a requirement for installing regular Windows 11, skip if not installing an OS that requires TPM

```
sudo lxc config device override win11 root size=50GB
```
> Change `size` to how big you want your virtual drive to be, recommended is 52GB <br/>
Make sure you have enough storage otherwise your Windows might bootloop after some extra space is used

```
sudo lxc config device add win11 install disk source=[ABSOLUTEPATHTOYOURPACKEDISO] boot.priority=10
```
> [ABSOLUTEPATHTOYOURPACKEDISO] e.g. /home/[YOURUSERHERE]/Downloads/win11.iso

```
sudo lxc start win11
```

```
sudo lxc console win11 --type=vga
```
> If you run into an error `Authorization required, but no authorization protocol specified` after running this command, run `xhost + local:` and run `sudo lxc console win11 --type=vga` again

Hit any key to run the installer from the ISO
Once Windows is installed, stop your VM (see below) and remove the install drive with:
```
sudo lxc config device remove win11 install
```

## Post-Creation
Starting and Stopping the VM:
```
sudo lxc stop [YOURVMNAME] --force
```
> Stop the VM

```
sudo lxc start [YOURVMNAME]
```
> Start the VM

```
sudo lxc console [YOURVMNAME] --type=vga
```
> Open the display for the VM

```
sudo lxc delete [YOURVMNAME]
```
> Delete your VM

## Post installation (Windows 11)
### I do not want to sign in to my Microsoft account
Hit SHIFT+F10 to open CMD and type one of the following commands:
```
start ms-cxh:localonly​
```
OR
```
start ms-cxh://setaddlocalonly​
```
Type in your preferred username and password if you'd like
Click no for everything analytics wise and send only required data

### Activate Windows
1. Hit WIN+X, open Terminal (Admin) and run this command:
```
irm https://get.activated.win | iex
```
2. Once loaded, hit 1 to activate Windows and wait
3. Done!

