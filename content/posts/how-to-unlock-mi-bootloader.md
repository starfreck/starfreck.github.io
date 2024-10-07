---
title: "How to unlock Mi Bootloader?"
date: "2021-06-18"
description: "How to unlock Mi Bootloader?"
tags: [
    "Mi",
]
categories: ["Mobile"]
series: ["Unlock"]
cover:
  image: "https://images.unsplash.com/photo-1579728866437-6397f3d89ec3?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxMTc3M3wwfDF8c2VhcmNofDE0fHx1bmxvY2t8ZW58MHx8fHwxNjIzOTk0NzEy&ixlib=rb-1.2.1&q=80&w=2000"
ShowToc: true
TocOpen: true
ShowReadingTime: true
ShowWordCount: true
---

## Download Mi Unlocker Tool

Go Here to download MiUnlocker: [https://en.miui.com/unlock/download_en.html](https://en.miui.com/unlock/download_en.html)

## Steps

1. Extract the zipped archive of MI Unlock tool to the root of your system drive, like C:\any_folder. I extracted it to C:\unlock, so the path of the tool's executable became "C:\unlock\miflash_unlock.exe"

2. Run MiUsbDriver.exe from the folder with as administrator and click "Install". Make sure it says "Driver installed" after that. If it already says that, hit install again just to make sure. Click "Retesting" to see if it remains the same. Close the program after.

3. Put your device into fastboot mode (make sure to turn on USB debugging and OEM unlocking in the developer options), and connect it through USB 2.0 port. (I don't know if 2.0/3.0 makes a difference but if you have 2.0 available, use it).

4. Go to device manager. Expand "Android Phone", right click "Android Bootloader Interface" and click properties. Click on "Driver" tab. See if the driver provider is "Xiaomi Technology, Inc.", driver date is "11/3/2016", and driver version is "16.0.0.0".
IF it's not, then close the properties window, right click android bootloader interface and click "Update driver". Click "Browse my computer for driver..." then "Let me pick from a list ...". Uncheck "Show compatible hardware", click "Xiaomi Technology, Inc." from the left side, then "Android Bootloader Interface" from the right and click next. After it's installed, check the properties to make sure it says what I mentioned above.

5. Go to unlock tool folder. Go to driver\win10 folder, right click android_winusb.inf and click install. You'll get operation completed successfully message.

6. Go back to unlock folder and run the tool as administrator. Now before clicking agree, click on the settings gear on the top right corner. Make sure MI Usb Driver says "Already installed". This is really important. Otherwise IT WON'T WORK. If it doesn't say that check previous steps and make sure your didn't miss any. Beyond that I have no idea.

7. Now you're good to go. Click agree, sign in and voila, your phone shall be connected, ready to unlock.

## Referances:

- [MI Unlock Tool cannot detect phone](https://forum.xda-developers.com/t/resolved-mi-unlock-tool-cannot-detect-phone.3663139/)