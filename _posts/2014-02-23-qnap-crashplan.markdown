---
layout: post
title:  "Installing Crashplan on QNap"
date:   2014-02-23
categories: nas qnap crashplan
---

I still remember when I had an Iomega IX2-200. I bought it a year ago for more than I paid in the QNap. It came with 2x1Gb hard drives that did not last a year. I tried to upgrade it to 2x3Gb drive, but it was PAINFUL. Iomega doesn't offer any easy way to reinstall / initialize the OS in a new HD. So, everything you can do is based on hacks that you gather on the web. After a couple of weeks I managed to upgrade it. I even installed the new Cloud Edition firmware. However, in one unfortunate day, I tried to setup Crashplan to start automatically after reboot. I restarted the NAS, and... It never came back again. 

I was so frustrated that I decided to purchased a new NAS. After doing some research I bought a QNap TS-212P. The price is seemed to be pretty good if you consider the hardware and software that comes with it. As a matter of fact it seemed to be the best deal I could find in Amazon. 

Now all I had to do is to recover my files from Crashplan. I googled for some instructions and I found this [blog](http://orawik.blogspot.com/2012/08/set-up-crashplan-on-qnap-nas-using-qpkg.html). The steps on the post are quite clear, but I'd like to add some extra reference that helped me install Crashplan.

The Java installation was not quite as stated on the article. I followed the instructions described [here](http://wiki.qnap.com/wiki/Category:JavaRuntimeEnviroment). After setting it up, make sure you ssh to your NAS and verify that java is in your path. 

The other missing piece is how to configure Crashplan on your desktop to remotely access and configure the Crashplan client running in your NAS. Notice that I said 'client', because the idea is to backup your files to NAS and your NAS will push it to Crashplan. Find the ui.properties file on your desktop. I use a Mac, so in my case it's under _/Applications/CrashPlan.app/Contents/Resources/Java/conf/ui.properties_. Now edit the following line:

```
serviceHost=<NAS IP>
```

After that, reload Crashplan service on your Mac:

```
sudo launchctl unload /Library/LaunchDaemons/com.crashplan.engine.plist
sudo launchctl load /Library/LaunchDaemons/com.crashplan.engine.plist
```

...and voilà!