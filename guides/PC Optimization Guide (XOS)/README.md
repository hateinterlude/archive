> [!NOTE]
> Last updated May 19th, 2025

# How to optimise your PC
I use XOS, a free debloated version of Windows 11. [XOS Discord](https://discord.gg/XTYEjZNPgX)

## The following software will not work after setup:
- Intel XTU
- Windows Defender & Security Center & System Guard & SmartScreen & Guarded Host

If you sign in to your Microsoft Account at any point, select “Microsoft apps only”, otherwise this will break your sign in.

Let me know if you need any extra help @ twitter: alyxrtw

## Requirements
- USB stick (I used a 32gb one, 16gb should be enough)
- An external hard drive (big enough for backing up data and storing other files needed for setup)
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
- Download [Ventoy (.zip)](https://www.ventoy.net/en/download.html) 
> Allows you to select between multiple ISOs from a USB to install on your system
- Download [the latest version of XOS from their Discord](https://discord.gg/XTYEjZNPgX)
> The current debloated Windows I use
- Download [Windows 11 ISO](https://www.microsoft.com/en-us/software-download/windows11) 
> Normal Windows 11 ISO in whatever case that something goes wrong - scroll down to “Download Windows 11 Disk Image (ISO) for x64 devices”, select “Windows 11 (multi-edition ISO for x64 devices)“ from the dropdown menu, click “Download Now”, select “English” (either one) and click “Confirm”, then finally download the ISO by clicking on “64-bit Download”

## Installing Ventoy and XOS
1. Connect your USB stick
2. If present, backup data from your USB stick 
3. Unzip Ventoy
4. Open Ventoy2Disk.exe found in the Ventoy folder
5. Click on “Option” and ensure that “Secure Boot Support” is checked
6. Click on the “Install” button
7. Click “Yes” (twice)
8. Ventoy should be installed, open Explorer and you should see something like this:
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image2.png)
9. Take the two ISOs you downloaded (Windows 11 and xOS 11) and place them into Ventoy like so: 
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image11.png)
10. Hold SHIFT while clicking on Restart. This should take you to a blue screen with options.
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image5.png)
11. Click on “Use a device”
12. Click on your USB drive. Your system will now boot into your USB drive.
13. If your screen says Security Violation, just hit ENTER, click any key to perform MOK management and it’ll take you to this screen:
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image12.png)
14. Use your arrow keys to select “Enroll key from disk” and hit ENTER
15. Hit ENTER on “VTOYEFI”
16. Select “ENROLL_THIS_KEY_IN_MOKMANAGER.cer” and hit ENTER
17. Select “Continue” and hit ENTER
18. Select “Yes” and hit ENTER
19. Select “Reboot” and hit ENTER
20. You should be taken to Ventoy, with this screen:
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image8.png)
21. Use your arrow keys to select the XOS .iso and hit ENTER
22. Select “Boot in normal mode” and hit ENTER
23. You should now see the Windows logo show.
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image4.png)
24. Wait a while for setup to prepare, then you should be seeing this screen:
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image10.png)
25. Select your time format and keyboard method as you’d like. Click “Next”
26. You should see your drive with Windows installed. Click on Format. Please make sure you have a backup of your data as all will be lost after this. Click on the drive you just formatted and click “Next”.
27. Wait for Windows to install. Your system should reboot into the Windows Setup.
28. Select your region, keyboard layout, input your user and make a password (or just continue with an empty box if you do not need a password).
29. Wait for Windows Setup to complete.
30. Connect your hard drive with your network drivers on it. Install your network drivers on your system. You should now be able to connect to Wi-Fi and/or use Ethernet.
31. You should see this screen:
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image14.png)
So do not do anything. Your system will reboot.
## Setting up XOS
1. After your system reboots, there should be an XOS folder on your desktop. Open it.
2. Right click on your Desktop and click Personalize. Activate Windows by clicking on Activate Now. You should be able to change your accent color and wallpaper after this.
3. Click on “1-localization”. You can sync your time by clicking on “sync-date-and-time” and under “Additional settings”, click on “Sync now”
4. Go back and click on “2-browser-installations”. Open “browser-install.exe”
5. After Chocolatey is installed, type the number of which browser you want, like so (e.g. 2 for Google Chrome):
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image6.png)
6. If you want to import your passwords that you have inside the CSV file, open Google Chrome, type in chrome://password-manager/settings in the URL bar and next to “Import passwords” click on “Select file”, then select the CSV file that you saved beforehand.
> ### For NVIDIA GPU
> - Go back and click on “3-setup-gpu-drivers”. Go to “nvidia” and open NVCleanstall.
> - Install the best driver for your system, select which components you want (e.g. ShadowPlay), click “Next” and install your drivers.
> - Go into the “tweaks-run-after-driver-installation” folder. Presumably (I do not have a NVIDIA card), you should be able to import the xos.nip file. You can also disable NVIDIA telemetry by running “breaks-geforce-experience-disable-nvidia-telemetry.bat”. 

7. Install the rest of the drivers for your system.
8. You can enable Bluetooth by going into “configure-services-and-features” -> “bluetooth” and running “enable-bluetooth.bat”.
9. Run the .bat file you have on your hard drive (enable-vbs-and-hyper-v.bat). This should allow Valorant to run on your PC without Vanguard throwing any errors after installation.
10. Go to “tuning” -> “tweaking tools” and right click on “msi-mode-utility.exe”. Click on “Run as administrator.”
11. Scroll until you see your GPU. Click on “Undefined” next to your GPU and set it to “High”. Click on “Apply” on the top right. Close the app.
12. XOS is now set up. You can install and run your games like normal. I will also list some other tweaks that may prove useful to you.
## Valorant Config
After installing Valorant and opening it, go to C:\Users\[your username here]\AppData\Local\VALORANT\Saved\ and replace the Config folder with the one you have on your backup drive.

# Extras
This is what I have done personally to my system, you can do this if you want
## Windows Settings
XOS allows apps to be run as admin without asking for user confirmation. I changed this by going to Control Panel -> User Accounts -> User Accounts and clicking on “Change User Account Control settings”. Set the notch to the 2nd or 3rd one like so:
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image13.png)

When you press WIN + R at the same time, you see this box:
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image9.png)
I do not want every single task run here created with admin privileges so to change this, I typed in regedit, opened Registry Editor and went to Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System.
Double click “EnableLUA” and change “Value data” from “0” to “1”. Click “OK” and close Registry Editor. Reboot system. The changes should be applied.

You can delete the .txt file and whatnot from your desktop because it is unnecessary. The XOS folder which allows you to change settings can always be found at C:\XOS, just do not delete the folder and delete the shortcut instead.
## Spotify Modification
Here is a tweaked version of Spotify which you can install [here](https://raw.githack.com/amd64fox/SpotX/main/scripts/Install_Auto.bat) (ad-free listening experience, full list of features can be found [here](https://github.com/SpotX-Official/SpotX)). Just run the .bat file and everything will be done for you.
Disable Hardware Acceleration by going into Settings, scrolling all the way down and making sure that “Enable hardware acceleration” is toggled OFF.
## Discord Modification
Here is [Vencord](https://vencord.dev/download/), a way to modify your Discord Client and enable plugins, themes, etc. Make sure that normal Discord is installed first (you can install it from [here](https://discord.com/download)) and then open VencordInstaller.exe. Click on “Install OpenAsar”, click “Accept” and click on “Install OpenAsar” again. OpenAsar allows your Discord to run and open faster. You can also install Vencord if you’d like by just clicking on “Install”.

Here is my Discord Game Overlay settings:
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image3.png)
Everything is disabled because any overlay has a negative impact on my performance. I also recommend that you turn off Hardware Acceleration by going to “Advanced” -> checking the toggle OFF for “Hardware Acceleration”.
## Taskbar Modification
I use [TranslucentTB](https://apps.microsoft.com/detail/9pf4kz2vn4w9) to make my taskbar transparent like so:
![image](/guides/PC%20Optimization%20Guide%20(XOS)/images/image1.png)
## Disabling Steam Webhelper
Steam Webhelper is known to consume a lot of CPU while playing games on Steam. Download [this file](https://github.com/hateinterlude/archive/raw/fee6ece791aef447e379bfd9bf4275c976fdca93/files/umpdc.dll) and place it in C:\Program Files (x86)\Steam to allow the option to disable Webhelper.


