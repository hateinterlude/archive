# How to optimise your PC
I use XOS, a free debloated version of Windows 11. [XOS Discord](https://discord.gg/XTYEjZNPgX)

## The following software will not work after setup:
Intel XTU
Windows Defender & Security Center & System Guard & SmartScreen & Guarded Host

If you sign in to your Microsoft Account at any point, select “Microsoft apps only”, otherwise this will break your sign in.

Let me know if you need any extra help @ twitter/discord: alyxrtw

## Requirements
- USB stick (I used a 32gb one, 16gb should be enough)
- A Hard drive (big enough for backing up data and storing other files needed for setup) 
- A lot of patience and a few hours at most

## What to do beforehand
- Backup all your files onto a hard drive (like photos, videos, etc), if you are unsure about other game data you can just copy the whole of C:\Users to your hard drive
- Make a list of what programs you need to reinstall (you can find what is installed on your computer by going to Control Panel -> Uninstall a program
- If you have passwords saved on your browser, go to chrome://password-manager/settings and click on “Download” next to “Export passwords”. You should have a .csv file exported, save it to your hard drive
- Copy the VALORANT “Config” folder found at C:\Users\[your username here]\AppData\Local\VALORANT\Saved\ to your hard drive
- Download your network drivers for your system put them onto your hard drive
- Download [this .bat file](https://cdn.discordapp.com/attachments/1294815650186788916/1354502185697939538/enable-vbs-and-hyper-v.bat?ex=6822d3b6&is=68218236&hm=7dabafe9badbc80053a3aad97e7ac79f5ef2c9d841d8c893b93e19f62e33d568&) and save it to your hard drive
- Update your BIOS if not done already
- Ensure that Secure Boot is enabled (Look into your BIOS settings)
- Download [Ventoy (.zip)](https://sourceforge.net/projects/ventoy/files/v1.1.05/ventoy-1.1.05-windows.zip/download) 
> Allows you to select between multiple ISOs from a USB to install on your system
- Download [XOS 11 23H2 ISO](https://drive.google.com/file/d/1F9xoCeYEPrrDPtZErHPvzHZ406V2pgrI) 
> The current debloated Windows I use
- Download [Windows 11 ISO](https://www.microsoft.com/en-us/software-download/windows11) 
> Normal Windows 11 ISO in whatever case that something goes wrong - scroll down to “Download Windows 11 Disk Image (ISO) for x64 devices”, select “Windows 11 (multi-edition ISO for x64 devices)“ from the dropdown menu, click “Download Now”, select “English” (either one) and click “Confirm”, then finally download the ISO by clicking on “64-bit Download”

## Installing Ventoy and XOS
Connect your USB stick
If present, backup data from your USB stick 
Unzip Ventoy
Open Ventoy2Disk.exe found in the Ventoy folder
Click on “Option” and ensure that “Secure Boot Support” is checked
Click on the “Install” button
Click “Yes” (twice)
Ventoy should be installed, open Explorer and you should see something like this:
![image](https://github.com/hateinterlude/archive/blob/main/guides/PC%20Optimization%20Guide%20(XOS)/images/image2.png?raw=true)
Take the two ISOs you downloaded (Windows 11 and xOS 11) and place them into Ventoy like so: 
Hold SHIFT while clicking on Restart. This should take you to a blue screen with options.
Click on “Use a device”
Click on your USB drive. Your system will now boot into your USB drive.
If your screen says Security Violation, just hit ENTER, click any key to perform MOK management and it’ll take you to this screen:
Use your arrow keys to select “Enroll key from disk” and hit ENTER
Hit ENTER on “VTOYEFI”
Select “ENROLL_THIS_KEY_IN_MOKMANAGER.cer” and hit ENTER
Select “Continue” and hit ENTER
Select “Yes” and hit ENTER
Select “Reboot” and hit ENTER
You should be taken to Ventoy, with this screen:
Use your arrow keys to select the XOS .iso and hit ENTER
Select “Boot in normal mode” and hit ENTER
You should now see the Windows logo show.
Wait a while for setup to prepare, then you should be seeing this screen:
Select your time format and keyboard method as you’d like. Click “Next”
You should see your drive with Windows installed. Click on Format. Please make sure you have a backup of your data as all will be lost after this. Click on the drive you just formatted and click “Next”.
Wait for Windows to install. Your system should reboot into the Windows Setup.
Select your region, keyboard layout, input your user and make a password (or just continue with an empty box if you do not need a password).
Wait for Windows Setup to complete.
Connect your hard drive with your network drivers on it. Install your network drivers on your system. You should now be able to connect to Wi-Fi and/or use Ethernet.
You should see this screen:So do not do anything. Your system will reboot.
## Setting up XOS
After your system reboots, there should be an XOS folder on your desktop. Open it.
Right click on your Desktop and click Personalize. Activate Windows by clicking on Activate Now. You should be able to change your accent color and wallpaper after this.
Click on “1-localization”. You can sync your time by clicking on “sync-date-and-time” and under “Additional settings”, click on “Sync now”
Go back and click on “2-browser-installations”. Open “browser-install.exe”
After Chocolatey is installed, type the number of which browser you want, like so (e.g. 2 for Google Chrome):
If you want to import your passwords that you have inside the CSV file, open Google Chrome, go to chrome://password-manager/settings and next to “Import passwords” click on “Select file”, then select the CSV file that you saved beforehand.
### For NVIDIA GPU
Go back and click on “3-setup-gpu-drivers”. Go to “nvidia” and open NVCleanstall.
Install the best driver for your system, select which components you want (e.g. ShadowPlay), click “Next” and install your drivers.
Go into the “tweaks-run-after-driver-installation” folder. Presumably, you should be able to import the xos.nip file. You can also disable NVIDIA telemetry by running “breaks-geforce-experience-disable-nvidia-telemetry.bat”. 

Install the rest of the drivers for your system by going here. I would install only the Bluetooth and Thunderbolt drivers (the others aren’t really necessary by the looks of it).
You can enable Bluetooth by going into “configure-services-and-features” -> “bluetooth” and running “enable-bluetooth.bat”.
Run the .bat file you have on your hard drive (enable-vbs-and-hyper-v.bat). This should allow Valorant to run on your PC without Vanguard throwing any errors after installation.
Go to “tuning” -> “tweaking tools” and right click on “msi-mode-utility.exe”. Click on “Run as administrator.”
Scroll until you see your GPU. Click on “Undefined” next to your GPU and set it to “High”. Click on “Apply” on the top right. Close the app.
XOS is now set up. You can install and run your games like normal. I will also list some other tweaks that may prove useful to you.
## Valorant Config
After installing Valorant and opening it, go to C:\Users\[your username here]\AppData\Local\VALORANT\Saved\ and replace the Config folder with the one you have on your backup drive.
Recommendations/What I have done personally
This is what I have done personally to my system and I recommend you do the same as well.
Windows Settings
XOS allows apps to be run as admin without asking for user confirmation. I do not agree with this decision. I would recommend that you go to the Control Panel -> User Accounts -> User Accounts and click on “Change User Account Control settings”. Set the notch to the 2nd or 3rd one like so:rer

When you press WIN + R at the same time, you see this box:
I do not want every single task run here created with admin privileges so to change this, I typed in regedit, opened Registry Editor and went to Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System.
Double click “EnableLUA” and change “Value data” from “0” to “1”. Click “OK” and close Registry Editor. Reboot system. The changes should be applied.

You can delete the .txt file and whatnot from your desktop because it is unnecessary. The XOS folder which allows you to change settings can always be found at C:\XOS, just do not delete the folder and delete the shortcut instead.
Spotify Modification
Here is a tweaked version of Spotify which you can install here (ad-free listening experience, full list of features can be found here). Just run the .bat file and everything will be done for you.
Disable Hardware Acceleration by going into Settings, scrolling all the way down and making sure that “Enable hardware acceleration” is toggled OFF.
Discord Modification
If you do not already know about this, here is Vencord, a way to modify your Discord Client. Make sure that normal Discord is installed first (you can install it from here) and then open VencordInstaller.exe. Click on “Install OpenAsar”, click “Accept” and click on “Install OpenAsar” again. OpenAsar allows your Discord to run and open faster. You can also install Vencord if you’d like by just clicking on “Install”.

Here is my Game Overlay settings:
Everything is disabled because any overlay has a negative impact on my performance. I also recommend that you turn off Hardware Acceleration by going to “Advanced” -> checking the toggle OFF for “Hardware Acceleration”.
Taskbar Modification
I use TranslucentTB to make my taskbar transparent like so:
Disabling Steam Webhelper
Steam Webhelper is known to consume a lot of CPU while playing games on Steam. Download https://github.com/hateinterlude/archive/raw/fee6ece791aef447e379bfd9bf4275c976fdca93/files/umpdc.dll and place it in C:\Program Files (x86)\Steam to allow the option to disable Webhelper.


