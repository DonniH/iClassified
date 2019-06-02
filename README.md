# Intro

I did not create the software, nor am I developer, the software has always been publicly available at this github repository: https://github.com/ColdHeat/iclass. I am simply creating my own fork with more details and clarification since the original has been neglected for a while. Contributions are welcome. As always these types of programs are meant only to be used for education and/or security penetration purposes only. I highly recommend all vendors to upgrade to iClass SE (and use the SE card) since legacy card can be so easily be cloned as seen below

# Installing iClassified

In order to read and write to cards, you will, at the minimum, need a reader/writer. The simplest way to get one is to get a reader/writer from the HID OMNIKEY line. The preferred and tested reader is the HID OMNIKEY 5321 v2 Cli its fairly cheap at around $50. The model number does matter, as the **HID OMINKEY 5321 Sam CL will not work with this program**. Other have used an HID OMNIKEY 6321 CLi though I have never tested it. iClassifed will work on Windows XP or Windows 10 (32 bit only!!). I used Windows XP on VMware. 

To build the software you want to start off by downloading the [MinGW installer assistant](https://sourceforge.net/projects/mingw/files/Installer/mingw-get-setup.exe/download). Install it and select:

* mingw-developer-toolkit
* mingw32-gcc-g++
* msys-base

It should look something like this:

![mingw](https://cloud.githubusercontent.com/assets/166333/15988849/91724b5c-302d-11e6-994c-33d24211e87e.png)

Then go to `Installation > Apply Changes` on the menu bar to install part of your build environment. 

Now go to `C:\MinGW\msys\1.0` and copy everything over to `C:\MinGW`. 

![copying](https://cloud.githubusercontent.com/assets/166333/15988850/98ea89a8-302d-11e6-9620-c5b45406ff87.png)

Next, open the `msys.bat` file (located in the MinGW folder) to get a small shell environment. A new "home" folder should apprear. Now download the iClass folder, extract the zip, and copy all the files into the "home" folder
![dowload](https://i.postimg.cc/5y9NmBj9/4846194367660032.png)
![copy](https://i.postimg.cc/MH03zBYB/On-Paste-20190524-132429.png)
Now that the files have been copied go back into the `iclassified` directory (type in "cd iclassified" or whatever its named; might be named your username; just go into wherever you copied the new files from Github) and type in `make`.

If everything runs well the files `iclass.exe` and `iclassified.o` should appear in your "home" folder. If you get the error "The application failed to initialize properly (0xc0150002)" then you may need to install [Microsoft Visual C++ 2008 Redistributable Package (x86)](https://www.microsoft.com/en-au/download/details.aspx?id=29).

At this point you should plug in your OMNIKEY reader and install the following [drivers](http://www.proxmark.org/files/Various%20Hardware/OMNIKEY%205x21/OMNIKESY5x21_V1_2_0_14.exe).

**Only the drivers from 2009 and below will work with iClassiified!**

# Installing the driver on Windows (work the same with Windows XP)

The following is shown using a 6321 cli reader, but the process is the same across the board.
> First, you must install the driver provided in the repo.
> 
> In device manager, you should see your Omnikey listed under "Smart card readers"
> Right click on the Omnikey, then select "Properties"
> ![1](https://user-images.githubusercontent.com/13852784/37375974-513af2c8-26df-11e8-8f2a-9351d7c54c15.png)
> 
> In the properties for the Omnikey, click the "Drivers" tab
> ![2](https://user-images.githubusercontent.com/13852784/37375975-516c3086-26df-11e8-9e6f-39fccf5704c0.png)
> 
> In the drivers page, click "Update Driver"
> ![3](https://user-images.githubusercontent.com/13852784/37375977-5185e738-26df-11e8-97d8-5020b9ac16e6.png)
> 
> Click on "Browse my computer for driver software"
> ![4](https://user-images.githubusercontent.com/13852784/37375979-51c4cf70-26df-11e8-9450-fb34072a761f.png)
> 
> Click on "Let me pick from a list of available drivers on my computer"
> ![5](https://user-images.githubusercontent.com/13852784/37375980-522f508e-26df-11e8-998a-d847b4ed267c.png)
> 
> Click on "Have Disk..."
> ![6 5](https://user-images.githubusercontent.com/13852784/37375981-527ebba6-26df-11e8-9541-cef789872eb0.png)
> 
> Click on "Browse"
> ![6](https://user-images.githubusercontent.com/13852784/37375982-52da6abe-26df-11e8-9f06-18cbb418fd60.png)
> 
> Click on "This PC"
> Then select you C:\ drive
> ![7](https://user-images.githubusercontent.com/13852784/37375983-537426a4-26df-11e8-9616-5ff6435c920c.png)
> 
> Click on the folder entitled "OMNIKEY" (or where ever you installed the Omnikey driver)
> ![8](https://user-images.githubusercontent.com/13852784/37375984-53d7b7fa-26df-11e8-88ec-0c128d1ad05d.png)
> 
> Click on the folder entitled "5x21_V1_2_0_14"
> ![9](https://user-images.githubusercontent.com/13852784/37375985-53fdaeec-26df-11e8-97ef-96e8b88c8ecd.png)
> 
> Click on the folder entitled "W32"
> ![10](https://user-images.githubusercontent.com/13852784/37375986-5481a8c8-26df-11e8-80f9-7f96e4369ad2.png)
> 
> Click on the file called "cxru0wdm"
> Click "Open"
> ![11](https://user-images.githubusercontent.com/13852784/37375987-560ef8f8-26df-11e8-9d14-630defc65cb3.png)
> 
> Click "OK" in the "Install From Disk" window
> ![12](https://user-images.githubusercontent.com/13852784/37375988-565e66fe-26df-11e8-8ad2-6245fe7752a6.png)
> 
> Click "Next" in the update drivers window
> ![13](https://user-images.githubusercontent.com/13852784/37375989-56cf66ce-26df-11e8-834a-3b4d2e232ca1.png)
> 
> Now if you go back into the properties of your Omnikey, you should see that the driver has been downgraded, so it should now work with the software provided in this repo!
> ![14](https://user-images.githubusercontent.com/13852784/37375991-575f9a96-26df-11e8-9cf9-62015e51eec2.png)



If all goes well you should be able to execute `iclass.exe read` to read a card and `iclass.exe write` to write to a card.

![writing](https://cloud.githubusercontent.com/assets/166333/15988852/a08fa5d0-302d-11e6-99c5-3b80d4a7d195.png)


# Reading and Writing Cards

After you compile the program using the "make" command you should have the iclass.exe program. This will now allow you to read and write the required data blocks (6,7,8,9) that you need to make a clone of the card. In order for the card to be cloned succesfully it is crucial that those 4 blocks are cloned.

### To Read All the blocks in a card:
Use the "iclass.exe read" command to read the entire set of data blocks.

### To Read a blocks in a card:
Use the "iclass read" command to read a data block (e.g. "iclass read 6")

### To Write date to a block

Use the "iclass write" command to write each of the four blocks. (e.g. "iclass write 6  030303030003E017"  to write block 6)


# Troubleshooting

### Can't find Omnikey Reader
Either you are using a newer driver or the wrong reader. Only the 5321 or 6321 v2 Cli works.

### Could not connect retrieve smart card reader list
Your reader is not plugged in correctly 

### Authentication Failed
Your using a high security iClass card, iClassified can't read those card. Security secured:+1:


  
