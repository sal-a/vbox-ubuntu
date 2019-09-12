# Installing VirtualBox and Ubuntu
(last updated 9-12-2019)

## 1.  Download the latest version of VirtualBox from www.virtualbox.org for your operating system.
- Install VirtualBox and follow the default prompts for a standard installation. Once the application opens, go to Step 2.

## 2. Download an .iso file for Ubuntu from https://ubuntu.com/download/desktop
- There are several options. I recommend the current LTS (Long term support) version, such as Ubuntu 18.04.3 LTS

## 3.  Create new VM in VirtualBox
- On the VirtualBox application, Click the NEW icon
- Type in the name of your VM (which will be used to create a folder for related files)
- If you type in "ubuntu" you may see the Type auto-select to Linux and the Version auto-select to Ubuntu (64bit). If these fields do not auto-select, choose them. Then, select Next.
- You will have to choose home much RAM to allot to the VM. You should generally choose no more than 25% of system's RAM. Unless you are planning on becoming a Linux power user, just choose 2GB.  Note, for VirtualBox 6 and Ubuntu 18-04, you need at least 2GB of RAM.
- Select OK and when prompted to choose hard disk type, the default of VirtualBox Disk Image (VDI), is fine. Select Next.
- You will be asked to choose between a fixed size and dynamically allocated hard drive.  Stay with the default Dynamically Allocated drive unless you are planning on using Linux a lot and have sufficient drive space. Select Next.
- You will be asked to choose how much hard drive space to use. If you have the space, I recommend selecting 20 GB of hard drive space.
- Note that at this point, you have only created a blank VM without an assigned Operating System. 

4.  Install Ubuntu onto the VM
- In the left panel of your VIrtualBox application, you should see a VM with the name entered previously. Double click on the VM.
- You will be asked to select the startup disk. Click the folder icon and navigate to the Ubuntu .iso file you downloaded earlier. Select ok/continue and you will soon see the VM boot into the Ubuntu desktop. At this point, Ubuntu is running in the VM, but it has not been installed permanently into the VM yet, that comes next.
- On the Ubuntu desktop you'll see a button named “Install Ubuntu”.  That looks too good to pass on... click it to start the install process.
- The install process asks some questions like language and keyboard type. The defaults are fine unless you want to choose something else.
- You will be asked if you want to install a full installation or a minimal installation.  If you think you are going to use Ubuntu often, go ahead and do a full install, but I usually go with a minimal install and update later if required.  The same screen also asks if you want Updates and Third Party Software. I recommend you choose both. Select and continue.
- Next you will be asked installation type.  Choose the default option of "Erase Disk and Install Ubuntu".  Don't worry, it is only going to erase the hard drive of the VM you created on VirtualBox. You will be asked if you are sure you want to continue - yes, you do.
- Next you will select the time zone you want for the VM. Choose wisely.
- You will be asked for your name, a name for your VM, a user name, and then a password (twice). Enter what you want.
- You have the option to login automatically when you launch the VM. Its OK to choose this feature if you are not going to use the VM to store sensitive information, but its up to you.  Same goes for whether you choose to encrypt your home folder. The easiest options for use are to login automatically and not encrypt your home folder, but, again, it is up to you.
- Select CONTINUE and the install process starts.  This will take 6-12 minutes, depending on your computer. When installation is complete, select the button to Restart the System.  This will restart your VM, not your primary computer OS.

5. Mount Ubuntu Guest Additions
- After your Ubuntu VM reboots, you will see a small and fully functional Ubuntu desktop, but when you expand the window, the screen size doesn't change and stays too small. We need to fix that. The solution is to mount and add the Guest Additions.
- On the top menu of the window of your Ubuntu VM, select Devices and then "Install Guest Additions CD Image". This will mount the CD to your VM and commence the installation process.  Once complete, you should be able to resize the Ubuntu window and it will rescale automatically.  You can then right click on the Guest Additionals CD image on the desktop and eject it to remove it from the desktop.

6. Shared File Folder settings
- At this point, you are close to having a fully functional Ubuntu VM, but there are a few things we can do to make our lives easier in the future.
- Shutdown the Ubuntu VM.  In the VirtualBox application, choose the SETTINGS icon.
- Click on the Shared Folders icon in the left pane of the Settings window. From here, select the blue + Folder icon in the upper right portion of the Shared Folders settings window.
- Select the dropdown arrow in the Folder Path field, and select the OTHER folder to allow you to search your main computer file structure.
- I recommend you choose an easy-to-find location on your computer for your shared folder, and only use that folder for transferring files between your host computer and the Ubuntu VM.  I installed Ubuntu on a PC, so I chose to create a folder on my C: drive called vmshare and that is what I selected in this step.  Make sure you check the box to Auto Mount the share drive.
- After you select your shared folder on the host computer, click OK on the main Settings window, which will bring you back to the main VirtualBox application.
- DoubleClick the Ubuntu VM in the VirtualBox application left pane to boot Ubuntu.  
- Once Ubuntu boots, you can open the File cabinet and click on the share drive.  BUT... you won't be able to access the share drive yet because you have not given yourself permissions (in Linux) to access that folder. Let's do that.
- Click on the Apps icon in the bottom left of the Ubuntu window and type in Terminal in the search box.  This will bring up a bash (born-again-shell) shell, aka the CLI.
- Type in the following at the cursor:  sudo adduser {your Linux user name created earlier} vboxsf
[this command means the following:  As a super user, add the user {user name} to the vboxsf group]
- You will be prompted for your administrator password.  Once done, you should log off (might need to fully power down) and when you re-launch Ubuntu, you will have read-write permissions for the shared folder.  This is going to come in very handy later.

7.  VM Snapshot
- Since you just loaded your Ubuntu VM and made some modifications, it is important for you to take your first "snapshot" of your VM.  Snapshots allow you to restore your Ubuntu VM to a previously-saved state in just a few seconds. This comes in very handy if you do something, install an application, or get infected with Malware that impacts the performance of your VM - simply restore from a previous snapshot and you VM will revert to its form at the time the snapshot was taken.
- Your Ubuntu VM should be running and the desktop showing.  In the top menu bar of the Ubuntu VM window, select the MACHINES item and then click on SNAPSHOTS
- You will get a window to name your snapshot and a field to describe. I usually name it the date taken and then provide a brief description of the state of the machine (like it is a fresh load with Guest Additions installed and not much else). Select OK when you are done.
- At this point, you are done with the core installation. Feel free to explore and turn off the VM when you are ready. 
