OdyssusOTA on Windows
=

If you are on Mac OS, you can follow [this tutorial](https://www.youtube.com/watch?v=Wo7mGdMcjxw) for OdysseusOTA, [this tutorial](https://www.youtube.com/watch?v=fh0tB6fp0Sc) for OdysseusOTA2 and [this post](http://dayt0n.com/articles/Odysseus/) for Odysseus guide. If you want, you can downgrade 32-bit devices with Odysseus on Windows by clicking [here]()

WARNING: do not do it, unless you have read and understood these instructions.
If *anything* goes wrong during the restore process, you will have to restore
to the latest, most likely unjailbreakable firmware.  Basically, you are on
your own.  I will not be held responsible for anything YOU do.
"..."
This works only on certain jailbroken 32bit devices.  By that, I mean devices
I have keys for.  

The untether on your device must have tfp0 enabled.
Early versions of Pangu did not enable tfp0, but latest versions of Pangu, TaiG
and evasi0n all have tfp0 activated.

You need an internet connection to do this downgrade.

-[@xerub](http://twitter.com/xerub)


If some of the applications in this utility get a dll error, you can go [here](), download the missing dll and put it into the folder.

First, you go to download [putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html), [WinSCP](https://winscp.net/eng/download.php) and the original ipsw file of the firmware that you want to downgrade. You can find ipsw file at [http://ipsw.me](http://ipsw.me)

Commands to do with Windows cmd:


**1. cd the folder**

`cd odysseusota-windows`

**2. build custom ipsw**

`ipsw.exe path_to_original_ipsw_restore.ipsw custom_downgrade.ipsw -bbupdate`
DON'T FORGET *-bbupdate* !!!

**3. get shsh blobs from Apple**

`idevicerestore.exe -t custom_downgrade.ipsw`

**4. extract pwnediBSS**

*xpwntool.exe `unzip -j custom_downgrade.ipsw 'Firmware/dfu/iBSS*' | awk.exe '/inflating/{print $2}'` pwnediBSS*

**5. copy kloader and pwnediBSS to the device**

Now you go to open WinSCP, connect to your device in SSH (SFTP) and copy kloader and pwnediBSS to the root of the device. Host name: *IP_OF_YOUR_DEVICE* Password (default): *alpine* Port: *22*

**6. run kloader and enter in pwned DFU mode**

Now, open putty and connect to the same data of the step 5., and run this command:
`cd / && chmod +x ./kloader && ./kloader pwnediBSS`

Now the screen of your device is black, disconnect and reconnect it to the computer and run this command to start downgrade:

`idevicerestore.exe -w custom_downgrade.ipsw`

**Done! Downgrade started ;P**

#**CREDITS**


Thanks a lot to @xerub for releasing iPad Bundles

Credits:
@Sn0wCooder for Odysseus for Windows

@xerub and @tihmstar for odysseus tool

@planetbeing, dborca for the awesome xpwn

@winocm for ios-kexec-utils

@westbaer, p0sixninja, iH8sn0w, GreySyntax for irecovery

@libimobiledevice people for libimobiledevice

@iH8sn0w for some ideas and code

@daytonhasty for some ideas, testing and writeup

@JonathanSeals for some ideas

@citrusui for the cool name