---
title: UX Writing Samples
tags: 
  - ux writing
  - tech writing
description: Take a look at the before and after samples.
---



# UX Writing Samples
Take a look at the UX writing sample before and after versions.

## Mobile SDK Release Notes

>**Project:**  Work related  
>**Description:** Write simple release notes for the customer by giving them either the scenario in which the problem occurred and, most importantly, what the bug is preventing, or both.   
>**Date of rewrite:** May 21, 2019   

#### Original

![Original Release Notes](../assets/img/xapi-writing-sample05212019.png)



#### Rewrite 

The iOS Mobile Messaging SDK version 3.8 is compatible with Xcode 10.2, Swift version 5.0.1 (swiftlang-1001.0.82.4 clang-1001.0.46.5), and supported on iOS versions 10 through 12.

**Important:** The iOS Mobile Messaging SDK version 3.8 is not compatible with simulators when running in an Objective-C project.

##### Bug Fixes

- When the `unreadMessagesDividerEnabled` attribute equaled **false**, the conversation window did not jump/scroll to the latest messages received by the agent as expected.

   By default, the Unread Message Divider separator appears in the message view.   When enabled, this feature does not prevent the badge or message text from displaying on the **Scroll to Bottom** button. Instead, the Unread Message Divider system message displays above the unread messages within the view of the user when returning to the conversation view. When disabled, the separator does not appear, and the unread message badge count displays on the **Scroll to Bottom** button. 

- Fallback to Signup Flow still existed. The bug prevented users from starting an authenticated conversation, and instead, the conversation started an unauthenticated visitor mode chat.

- Send Image (From Gallery) failed. The bug prevented users from uploading images larger than 3MB, resulting in a ‘file too large’ message. Version 3.8 of the Mobile Messaging SDK increased the image size limit to 5MB. 

- **On iOS 12.2 Swift 5**, the conversation screen did not show the sent or received messages and the margins appeared between messages. 

- Accessibility: voice over read old conversations.  The bug prevented the voice over feature, when enabled, to read the current conversation, and instead, skipping back to old conversations. 

- When trying to reconnect with a JWT after the initial token expired, an INVALID JWT warning appeared and showed a black bar even though the conversation continued without error.  

- Before the token expired, the agent did not receive one or more messages resulting in data loss. The bug prevented messages from being sent regardless of the token expiration.

- **For iOS versions lower than 12.** When starting an unauthenticated conversation then backgrounding the app and then foregrounding it again, the loading screen remained displayed. The bug prevented users from going in and out of the conversation without issue.


## Group Policies
>**Project:**  UX writing challenge <br>
>**Description:** Simplify, simplify, simplify.<br>
>**Date of rewrite:** January 8, 2019 <br>

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
| Disabled or not configured **(default)** | Allowed/turned on. |
| Enabled | Prevent/turned off. |

>> **Related policies:** Prevent users from turning on browser syncing.

<hr />

#### Prevent enterprise websites from loading non-enterprise content...


|Original  |Rewrite  |
|---------|---------|
|![Orginal browser group policy](../assets/img/gp-browser-before2.png)     |By default, non-enterprise sites open in Internet Explorer and Microsoft Edge outside of the Windows Defender Application Guard container.<p><table><tr><th>Setting</th><th>Description</th></tr><tr><td>Disabled or not configured <b>(default)</b></td><td>Allowed </td></tr><tr><td>Enabled</td><td>Prevented</td></tr></table></p>  |


#### Enable automatic MDM enrollment using default Azure AD credentials


|Original  |Rewrite  |
|---------|---------|
|![Orginal MDM group policy](../assets/img/gp-mdm-before1.png)     |With this policy, you can automatically enroll a device to the Mobile Device Management (MDM) service configured in Azure Active Directory (AAD).  The device must be registered in AAD for enrollment to succeed. Once enrolled successfully, the device gets managed remotely by the MDM service.  <p><table><tr><th>Setting</th><th>Description</th></tr><tr><td>Not configured <b>(default)</b></td><td>Automatic MDM enrollment does not initiate. </td></tr><tr><td>Enabled</td><td>A task gets created to initiate MDM enrollment.</td></tr><tr><td>Disabled</td><td>Unenroll MDM.</td></tr></table></p>         |


#### Disable MDM Enrollment


|Original  |Rewrite  |
|---------|---------|
|![Orginal MDM group policy](../assets/img/gp-mdm-before2.png)     |With this policy, you can prevent Mobile Device Management (MDM) enrollment for all users.   <p><table><tr><th>Setting</th><th>Description</th></tr><tr><td>Disabled or not configured <b>(default)</b></td><td>Automatic MDM enrollment initiates. Enable MDM enrollment for all users. </td></tr><tr><td>Enabled</td><td>Disable MDM enrollment for all users. It does not unenroll existing MDM enrollments.</td></tr></table></p>         |


