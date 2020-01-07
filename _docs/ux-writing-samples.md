---
title: Before & After Writing Samples
tags: 
  - ux writing
  - tech writing
  - group policies
  - release notes
  - before/after
description: UX Writing is the production of written content that becomes part of, and supports, a product’s user experience. My expertise is in taking the guesswork out of complex technical content for busy IT professionals. I am passionate about creating content experiences that help IT Pros achieve more with technology. Please take a look at the before and after samples, and you be the judge.
---


# Before & After Writing Samples

I approach a before/after project with UX writing in mind, which is the production of written content that becomes part of, and supports, a product’s user experience. My expertise is in taking the guesswork out of complex technical content for busy IT professionals. I am passionate about creating content experiences that help IT Pros achieve more with technology. Please take a look at the before and after samples, and you be the judge.


<hr />



## Group Policies
>**Project:**  UX writing challenge   
>**Description:** Simplify, simplify, simplify.  Here I wanted to continue what I had been doing while I was an FTE with Microsoft reworking the Mirosoft Edge Group Policies for the IT Pros.  <br />
>**Date of the rewrite:** January 8, 2019   

#### Do not sync browser setting 

##### Original
Prevent the "browser" group from syncing to and from this PC. This turns off and disables the "browser" group on the "sync your settings" page in PC settings. The "browser" group contains settings and info like history and favorites.

If you enable this policy setting, the "browser" group, including info like history and favorites, will not be synced.

Use the option "Allow users to turn browser syncing on" so that syncing is turned off by default but not disabled.

If you do not set or disable this setting, syncing of the "browser" group is on by default and configuration by the user.

##### Rewrite 

By default, the “browser” group syncs automatically between user’s devices allowing users to make changes. The “browser” group uses the Sync your Settings option in Settings to sync information such as history and favorites.

| Setting | Description |
| ------- | ----------- |
| Disabled or not configured **(default)** | Allowed/turned on |
| Enabled | Prevent/turned off |

>> **Related policies:** Prevent users from turning on browser syncing.

<hr />

#### Prevent enterprise websites from loading non-enterprise content

##### Original

![Orginal browser group policy](../assets/img/gp-browser-before2.png)

##### Rewrite 

By default, non-enterprise sites open in Internet Explorer and Microsoft Edge outside of the Windows Defender Application Guard container.

| Setting | Description |
| ------- | ----------- |
| Disabled or not configured **(default)** | Allowed |
| Enabled | Prevent |

<hr />
#### Enable automatic MDM enrollment using default Azure AD credentials

##### Original 

![Orginal MDM group policy](../assets/img/gp-mdm-before1.png)

##### Rewrite

With this policy, you can automatically enroll a device to the Mobile Device Management (MDM) service configured in Azure Active Directory (AAD).  The device must be registered in AAD for enrollment to succeed. Once enrolled successfully, the device gets managed remotely by the MDM service.  

| Setting | Description |
| ------- | ----------- |
| Not configured **(default)** | Automatic MDM enrollment does not initiate.  |
| Disabled | Unenroll from MDM. |
| Enabled | A task gets created to initiate MDM enrollment. |

<hr />

#### Disable MDM Enrollment

##### Original 

![Orginal MDM group policy](../assets/img/gp-mdm-before2.png)

##### Rewrite

With this policy, you can prevent Mobile Device Management (MDM) enrollment for all users.   

| Setting | Description |
| ------- | ----------- |
| Disabled or not configured **(default)** | Automatic MDM enrollment initiates. Enable MDM enrollment for all users. |
| Enabled | Disable MDM enrollment for all users. It does not unenroll existing MDM enrollments. |

## How-to Video Scripts

>**Project:**  Work-related<br />
>**Description:**  I was provided with how-to videos to do the voice over, but the script needed work, and the video had no audio to reference.  So I needed to be resourceful and found the user guide, which helped. But to write a quality script, I needed to watch the video many times to add context to the actions in the video. I also did the editing and final production of both audio (in Audacity) and video (Adobe Premiere Pro).  <br />
>**Date of project:** October/November 2019  


#### Checksum Configuration

##### Original
The system configuration checksum is a Nodegrid feature that creates a checksum of all the configuration files to enable a quick and easy way to find out if the Nodegrid has changed. 
To create a system configuration checksum, go to “System”, then “Toolkit”, and then “System Configuration Checksum”. The checksum can either be MD5 or SHA256. In our example, we will create a MD5 checksum by selecting “Create a checksum of the current configuration” and click “Apply”. You will then view your MD5 checksum for all the configuration files.

##### Rewrite (w/final video)

The system configuration checksum is a Nodegrid feature that creates a checksum of all your configuration files.  
This gives you a quick and easy way to detect changes in the Nodegrid. 

To create a system configuration checksum, go to **System>Toolkit** and then select **System Configuration Checksum**. 

The checksum can either be MD5 or SHA256.

But for our example, we’ll create an MD5 checksum by selecting **Create a checksum of the current configuration** and then clicking **Apply**. 

You can see the MD5 checksum for all your configuration files.  

Now, click **Finish**.

<p style="margin-bottom: 3pt;"><iframe width="100%" height="315" src="https://www.youtube.com/embed/FSEV17CUB9g" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
								</p>


#### Adding a new license

##### Original

This short video will show you how to add a new license. Some Nodegrid features like Clustering, Docker containers… require a license for activation. To activate your license, go to System, then click on “Add” and enter your license key and then click on “Save”. 


##### Rewrite 

A license is required for each managed device for Nodegrid access and control. 

The required license for each serial port of the Nodegrid is included with the product. 

Some Nodegrid features, like Clustering and Docker containers require a license for activation. 

At the top of the Nodegrid manager, click **System**.  

Here is where all licenses enrolled in this Nodegrid displays with other information, like license key, expiration date, and application.   

To add a license, click **Add**.  

Enter your license key.   

Now, click **Save**.   

You can see the new license in the list. 


## Mobile SDK Release Notes

>**Project:**  Work-related  
>**Description:** Write simple release notes for the customer by giving them either the scenario in which the problem occurred and, most importantly, what the bug is preventing or both.   
>**Date of the rewrite:** May 21, 2019   

#### Original

![Original Release Notes](../assets/img/xapi-writing-sample05212019.png)



#### Rewrite 

The iOS Mobile SDK version 3.8 is compatible with Xcode 10.2, Swift version 5.0.1 (swiftlang-1001.0.82.4 clang-1001.0.46.5), and supported on iOS versions 10 through 12.

**Important:** The iOS Mobile SDK version 3.8 is not compatible with simulators when running in an Objective-C project.

##### Bug Fixes

- When the `unreadMessagesDividerEnabled` attribute equaled **false**, the conversation window did not jump/scroll to the latest messages received by the agent as expected.

   By default, the Unread Message Divider separator appears in the message view.   When enabled, this feature does not prevent the badge or message text from displaying on the **Scroll to Bottom** button. Instead, the Unread Message Divider system message shows above the unread messages within the view of the user when returning to the conversation view. When disabled, the separator does not appear, and the unread message badge count displays on the **Scroll to Bottom** button. 

- Fallback to Signup Flow still existed. The bug prevented users from starting an authenticated conversation, and instead, the conversation started an unauthenticated visitor mode chat.

- Send Image (From Gallery) failed. The bug prevented users from uploading images larger than 3MB, resulting in a ‘file too large’ message. Version 3.8 of the Mobile SDK increased the image size limit to 5MB. 

- **On iOS 12.2 Swift 5**, the conversation screen did not show the sent or received messages, and the margins appeared between messages. 

- Accessibility: voice over read old conversations.  The bug prevented the voice over feature, when enabled, to read the current conversation, and instead, skipping back to past conversations. 

- When trying to reconnect with a JWT after the initial token expired, an INVALID JWT warning appeared and showed a black bar even though the conversation continued without error.  

- Before the token expired, the agent did not receive one or more messages resulting in data loss. The bug prevented messages from being sent regardless of the token expiration.

- **For iOS versions lower than 12.** When starting an unauthenticated conversation, then backgrounding the app and then foregrounding it again, the loading screen remained displayed. The bug prevented users from going in and out of the conversation without issue.

