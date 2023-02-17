## Notice
   As of January 26th, 2023, the domain Snap Camera normally uses is now offline. We will not be able to recover any lenses that are missing, please do not create issues looking for lenses or messaging me about it. If I find a way to bring the missing lenses I will make an update, but as of now, we do not have the ability to do this. 

   If you do not have 1.21.0 installed for Windows, you can search for the installer, be careful though some installers may have extra software packed in with them. You can check the installer is the original one from Snap Camera by uploading your installer to https://emn178.github.io/online-tools/md5_checksum.html. If you get an MD5 of anything other than `ec0816368314db8a35ddf06784ffadfe` I recommend finding a site with the installer.


# SnapCameraPreservation
The purpose of this project is to allow users to still use and find snap chat lenses with the snap camera application after the Jan 25th, 2023 shutdown.

This project uses a modified version of the 1.21.0 version of Snap Chat for Windows. Be sure to install that one before following the instructions on this page.

# Instructions for PC
Head over to https://snapchatreverse.jaku.tv/snap/ and make sure you have 1.19.0 or 1.21.0 installed. Provide the site with your 1.19.0 or 1.21.0 version of "Snap Camera.exe" located at the default install location of "C:\Program Files\Snap Inc\Snap Camera". Do not patch the installer. 

Make sure the correct patch file for your version is selected on the site before applying the patch. 

After applying the patch, you NEED to replace the original "Snap Camera.exe" file with the newly created patched file, you will need to remove/rename the original file and then rename the patched file to "Snap Camera.exe" when neither one is running. Check Task Manager to kill the original Snap Camera process to ensure this goes smoothly.

Open a folder to "C:\Program Files\Snap Inc\Snap Camera", find the same "Snap Camera" or "Snap Camera.exe" file you used on the website, rename it to "Snap Camera - org", and now take the downloaded patched file and put it in this folder. Rename the patched file to just be "Snap Camera" or "Snap Camera.exe" if your original file had the .exe do not add the .exe if you didn't already have it.

Now you can run the file from there, and everything should be working as expected.


If you have issues, make sure you don't have any Adblock or things blocking the patch site and that you are patching the correct version. Additionally, make sure that the original Snap Camera application is stopped and not running at all. I recommend checking your task manager and searching for "Snap Camera" and closing it there to be sure. If it is running, you will not be able to replace its file with mine.

I cannot host the EXE due to copyright, but I can patch it if you provide the original exe.

You'll know you are communicating with my server because a new category will be listed in the app called "Jaku Snap Backup".

If you see the above, go ahead and click on each of your saved lenses and activate them once to ensure they are backed up. After that, you are free to sit back and relax.

# Instructions for Mac
Patching the application similar to Windows does not work. The built-in security of MacOS is preventing modified binaries to run, and attempts to resign are failing. However, another solution for MacOS users exists, it's not my favorite approach, but it does work and is available for users.

Download the [studio-app.snapchat.com.crt.zip](https://github.com/jaku/SnapCameraPreservation/raw/main/studio-app.snapchat.com.zip) file in this repository, and extract it. You should now have a studio-app.snapchat.com.crt file. Double-clicking it should open up your Keychain Manager. Click on the login option on the left-hand side of the Keychain Manager, and then on the right-hand side, click Certificates. You should see studio-app.snapchat.com listed with a red icon to the left of the name. Go ahead and right-click on this file and select "Get Info", click the Trust arrow at the top, and for the option "When using this certificate," select "Always Trust", close this window, and it should prompt you for your MacOS password.

Almost done!

Open up terminal, you can type terminal into spotlight/search to do this. Next, you'll need to type this into the terminal ```echo "66.228.41.64    studio-app.snapchat.com" | sudo tee -a /etc/hosts```, it will prompt for your local computer's password. But from there, you should be all set.

With that, you can now close the terminal window and open Snap Camera. If everything works you should see "Jaku Snap Backup" as one of the categories.

# Unlock Lenses?
**The below will no longer work now that they shut down the servers.**

Since starting this project, I learned that some lenses are not available in the search of Snap Camera and instead must be directly searched for by their URL in the search box. I'm happy to report that these also work on this project, and as an extra bonus I made it so that you can use links like ``https://lens.snapchat.com/81f476238cf84615ba349efe82b36c27`` instead of the ``https://www.snapchat.com/unlock/?type=SNAPCODE&uuid=81f476238cf84615ba349efe82b36c27&metadata=01`` style links. 

**The above will no longer work now that they shut down the servers.**

# How does this work?
I've modified the Snap Camera.exe (for Windows) to use my servers instead of the Snap Chat servers. This was done with a hex editor, and 2 modifications were made. Instead of communicating with studio-app.snapchat.com it now communicates with snapchatreverse.jaku.tv.For Mac users, we aren't changing the host but instead telling it that the host's IP is something else and installing a self-signed certificate. By doing so my server then communicates to the Snap servers to get the lens data as if you were accessing it directly and downloads the lenses to an S3 bucket on Amazon. 

I then wrote a server that relays the information from the camera app to the snap chat servers (for now), which downloads the lenses separately and communicates back to the app in the way it expects.  


# Where is the code?
The server code can be found in the server folder. You can see how the server worked by relaying the information from the Snap Chat servers when the servers were online. I also created a reference folder that contains all the known endpoints and their expected responses.

# Who are you, and why are you doing this?
I am Jaku. If you're familiar with the software on Twitch called Crowd Control, then you're already familiar with some of my work as I run the company behind that. Or maybe you were an Animal Crossing fan and played in 2020 and used https://turnip.exchange, I, along with another friend (Ross), built that. You can find more about me at https://about.me/jaku, but overall I just like to build things and have been building things for Twitch streamers, gamers, and others for over seven years now. I have a background that allows for this stuff, and I enjoy working on them. 


# I have more questions or comments.
Feel free to submit an issue on Github with questions or message me on Twitter at https://twitter.com/jaku, but please be sure to read this page first as I cannot help with recovering missing lenses. 
