# OPNsense Setup Guide
Goal: To configure a versatile firewall device to enhance understanding of key cybersecurity fundamentals. Including. ACL / Rules / Dns Filtering / IPS/IDS / Log review

Step 1.  Decide what environment you wish to deploy your OPNsense installation in. For me, I had funds saved to build a home lab and chose a mini PC available on Amazon. Those on a strict budget might choose to forego this expense by using a virtual machine, but I wanted a Bare Metal configuration.
When choosing my hardware, I took into consideration what the Firewall would be used for long term. My goal was to configure IDS/IPS , VLAN capabilities and VPN along with general DHCP, DNS etc.
Based on these features, I chose a mini pc with an Intel N100 processor, two 1gb network cards (1 for WAN and one for LAN) 16gb of RAM, to ensure rich system resources for IDS/IPS which are known resource hogs, and a 512gb solid state hard drive in case someday I decided to repurpose the mini pc.
All that for 170 dollars with free shipping.  Sure, I could have purchased a Netgate box that came preinstalled with PFsense, but where is the fun in that?


Step 2. Choosing the correct file format and version to download.  Since I am using physical resources, I chose the AMD64 VGA format. If you choose to use a USB drive to install your OPNsense, this is the way to go. 
![image](https://github.com/CyberDanMan/OPNsense/assets/164780036/8b2ee239-81bb-48ff-9b12-d9603896ea12)

Step 3. Moving the downloaded installer image to your USB drive. Now that we have the package to install, we need to format our USB drive to be bootable. I used a free program called RUFUS. It is free and super easy to use and if you do get tripped up, there is a lot of easy to find documentation online. After RUFUS completes formatting the drive, simply move the file onto the USB drive.
Rufus - Create bootable USB drives the easy way - https://rufus.ie/en/


Step 4. Booting to the USB drive. Depending on what computer you have decided to use, the following steps could be different.  The main idea here is you need to boot to the USB drive you just formatted with RUFUS.  For my mini pc, the ESC button did the trick to enter into the boot menu where  I selected the drive and the OPNsense environment began to load.
NOTE:  Having a Cat6 or equivalent cable connected to the hardware is desired, if you can connect a WAN cable to your modem or internet facing hardware it is also helpful. I had both a cable connected directly to my laptop and a cable connected to my Cable Modem.

Step 5.  The Install.  A menu will load with seven options right away, disregard this for the installation we are completing. The process will automatically continue.
![image](https://github.com/CyberDanMan/OPNsense/assets/164780036/655946bf-b276-43a2-8880-c639d1abb878)

 
If you are watching the text while the files are loading, there will be a brief prompt that says “Press any key to start the configuration importer, this process can be ignored  as it not useful for our purposes. This process is for restoring backups or if you have a baseline installation file to install.

 ![image](https://github.com/CyberDanMan/OPNsense/assets/164780036/1b2dcd4c-0afb-45f4-bd76-da24708637dc)

OPNsense will auto assign Wan and Lan ports during the initial setup, we can always edit these interfaces later. For now, ensuring you have connected a single ethernet cable  to one of the network cards and getting an IP from the OPNsense live environment is desired.
Next, will be the login area.  Here you will want to use the following credentials.
installer / opnsense
OPNsense will auto assign a LAN connection if you have a cable connected.

Once you have logged in, the next question will be regarding keyboard layout. The first option provided by this menu is desirable for most installations. “Continue with default Keymap”
Next, the setup process will ask you to choose a hard drive formatting option. The documentation I read prior to install stated that for most use cases, ZFS is the default option here. Choose “ZFS”  .
The next step will be RAID (redundant array of independent disks) related. Since I only have one drive in my mini pc, I chose “stripe” if you have more than one drive, you can select the RAID type that matches your desired configuration. Choose the hard disk you want the software installed on and hit enter.
The installer will prompt you to ensure you have chosen the correct drive and remind you that it will erase all current data before you can proceed. Choose “Y” if you have ensured the chosen drive is correct.
After approving the drive, the installation process will continue.
The next step will be the option to change the “root” account password. It is highly recommended to alter this password as a method of device hardening. Default credentials are bad news.  I updated my password and allowed the system to reboot.
Once the system is back up, you will need to login using “root” and the new password you created in the last step. 
OPNsense will then provide you with a menu. We will choose 1 to “Assign Interfaces”

The next step will ask if you want to setup LAGG interfaces (link Aggregation) I chose to bypass this step.

![image](https://github.com/CyberDanMan/OPNsense/assets/164780036/3b3fe9ac-4a0d-46d0-9cc2-a4349fadbd64)

 
OPNsense install will continue and ask about  VLAN configuration, I chose to bypass this as well for the time being. I will be configuring them later, but in the GUI. I do have an OMADA switch and EAP that are capable of VLAN tagging, but that process will defined in a later walk through.
 
OPNsense will then ask you to  define the WAN and LAN interfaces for your device, or you can choose to have OPNsense auto assign these. Since my mini pc had each network port listed with its information, I was able to assign the left port to WAN and the right port to LAN in standard fashion. Allowing OPNsense to auto assign interfaces here is fine, you can always update them later if needed.
After setting up the interfaces, I chose option six in the ensuing menu to reboot the system. This is optional, but I wanted to have a clean boot of the system before trying to log into the GUI.

Step 6- Web GUI. Now that the OPNsense install is completed, you can access the web based gui by using the default IP address of 192.168.1.1 ( make sure you are connected via ethernet cable to the firewall device).  After bypassing the warning screen in your browser, you will get to the login menu. Using root for username and whatever password you configured will allow you to login to the OPNsense firewall to begin configuration!  Have fun and I hope this guide helps.
 

![image](https://github.com/CyberDanMan/OPNsense/assets/164780036/c493d61a-e4f0-465c-b4c0-6fa5522404dd)









 

