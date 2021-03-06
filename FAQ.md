# MBPMid2010_GPUFix F.A.Q.s - Frequently Asked Questions (and Answers)

[The GPU Panic](#the-gpu-panic) • 
[How does it works ?](#how-does-it-works-) • 
[System Integrity Protection (SIP)](#system-integrity-protection-sip) • 
[Getting Help](#getting-help) • 
[Troubleshooting](#troubleshooting) •

## The GPU Panic

#### Q: What causes my MacBook Pro to restart ?
At start, the bug is hardware : it's due to a bad type choice on a decoupling capacitor used on GPU motherboard part :
<img src="http://i.imgur.com/SFQfnWU.jpg" height="300">

It has been detected that the problem happens every time that `G-State` change between 2 to 0.

G-States go from 0 to 3, are related to the thresholds inside `AppleGraphicsPowerManagement.kext`, like this:
- G-state 0 *(maximum speed)*
- G-state 3 *(lowest speed)*.

The problem can be solved by keeping it always at `G-State 2` *(medium speed).*


## How does it works ?

#### Q: What is the algorithm doing ?


## System Integrity Protection (SIP)

#### Q: What is System Integrity Protection ?
> System Integrity Protection (SIP, sometimes referred to as rootless) is a security feature of Apple's macOS operating system introduced in OS X El Capitan. It comprises a number of mechanisms that are enforced by the kernel. A centerpiece is the protection of system-owned files and directories against modifications by processes without a specific "entitlement", even when executed by the root user or a user with root privileges (`sudo`).

More information can be found on [Apple website](https://support.apple.com/en-us/HT204899)

#### Q: How do I disable it ?
You can follow this [YouTube tutorial](https://www.youtube.com/watch?v=Wmhal4shmVo)

#### Q: Why should it be disabled ?
Patched kernel extension file needs to be reloaded and it can't be reloaded without SIP disabled.

#### Q: Do your app re-enables SIP after patching ?
There is no way for an app to modify SIP setting. You have to re-enable it manually.

Also, if you activated updates on your Macbook, the patched file will be overwrited and you'll need to run the patch software again. So I would not recommend re-enabling the SIP.

**No need to re-enable SIP to get the patch working though.**

## Getting Help 


#### Q: Where can I find help?
You can [open an issue](https://github.com/julian-poidevin/MBPMid2010_GPUFix/issues/new), contact me on [twitter](https://twitter.com/ju_vallejo) or post a message in [MacRumors forum application thread](https://forums.macrumors.com/threads/mbpmid2010_gpufix-finally-a-fix-for-kernel-panic-of-macbook-pro-2010.2044304/).

## Troubleshooting

#### Q: The app is asking for a password, what is this password ?
This is your **session password**, the one you use to log in.

#### Q: The fix does not work when an external screen is plugged
As said in Disclaimer section of the project, the fix will not work when using external screen. In this particular mode GPU internal firmware has more privilege than the kernel extension file : it's kinda overriding the fix. [Hardware fix](https://forums.macrumors.com/threads/gpu-kernel-panic-in-mid-2010-whats-the-best-fix.1890097/#post-23312990) is necessary if you want to use external screen.
