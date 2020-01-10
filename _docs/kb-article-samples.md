---
title: KB Article Sample
tags: 
  - tech writing
  - kb articles 
description: Knowledgebase articles solve issues with products or services. Customers should not be left to decipher highly technical content. Plus, they don't have the time to sift through mountains of information. My approach to writing knowledgebase articles is by focusing on a specific problem/solution and the audience. 
---

# KB Article Sample

I approach knowledge base articles with a UX approach because they solve issues with products or services. Customers should not be left to decipher highly technical content. Plus, they don't have the time to sift through mountains of information. My approach to writing knowledge base articles is by focusing on a specific problem/solution and the audience. 



<hr />

### XenApp - Slow logon issues

>**Project:**  UX and KB writing challenge  <br />
>**Description:**  I like to keep up with the writing trends.  I also like to challenge myself by rewritting and reformatting KB articles.  I learned how to write technical KB articles using an Information Technology Infrastructure Library (ITIL) format for both helpdesk professionals and customer self service.<br />
>**Original:** [How to Troubleshoot Slow Logons on XenApp](https://support.citrix.com/article/CTX101705)<br />
>**Date of rewrite:** January 10, 2020 

| Article # | Product(s) |
| --------- | ---------- |
| CTX101705 | - XenDesktop 7.8<br />- XenDesktop 7.7<br />- XenDesktop 7.6 FP3<br />-XenApp |

{% include alert.html type="warning" title="Important" content="Make sure to log into the same server using Microsoft's RDP client instead of the Citrix Receiver. By doing this, you can determine whether the issue is a profile, logon script, network, or other user environment issue." %}


##### Profile issues

1. **For existing users**, remove any references to a profile path from the the following:

   - Remote Desktop User 
   - Profile path with in Active Directory (AD) users and computers, if applicable
   - Computer Management

   **Tip!** Create a local account directly on the Remote Desktop Server to ensure that the profile loads directly from the server. Retest the logon.   
   

2. **For new user accounts**, accounts without a local profile, and anonymous accounts need to generate a local profile upon logon. The creation of the original profile might take time. Make sure to verify if local copies of the user profiles are cached or deleted on logoff.  If so, this slows down logons if they get deleted on logoff using a Microsoft Policy. The profile rebuilding on the server each time the user logs in slows down the logon. 

3. **Is Citrix User Profile Management (UPM) being used to manage user profiles?** If so, disable the service on one server and then retest.  If the issue improves, look over your Citrix UPM policies because there might be a configuration causing the problem.  To enable UPM logging, see [CTX126723 - How to Enable and Retrieve Profile Management Log Files](). 



##### Logon script issues

Remove any references to a logon script within:
   - Active Directory uses and computers
   - Computer Management
   - Any sore of computer or group policy.

   **Tip!** Create a local account directly on the Remote Desktop Server to ensure that the profile loads directly from the server. Retest the logon.

{% include alert.html type="success" title="Tip!" content="To help troubleshoot the resources in the script, comment out (REM) or input pause statements throughout each section of the logon script. " %}

##### Network issues

The root cause that indicate a network issue are:

- The Remote Desktop Server is searching for fonts by name and not finding them.
- A user encounters a black screen for 1 to 20 minutes before the logon completes. 
- An application is searching for fonts (usually created by older apps). Occassonal occurance.


##### Permissions issues


##### General troubleshooting steps


| Keywords | |
| Author: | Patti Short |
| Created: |  |
| Modified | |

<hr />

### Routing error on outbound shipment

>**Project:** Work-related; self-service KB article for manufacturing<br>
>**Description:**  Written for the support desk professionals in a manufacturing environment.  <br>
>**Date of rewrite:** January 8, 2019 

##### Root cause
Uknown

##### Scenario
While confirming shipment, a routing error message displays.

##### Required information
Shipment number


##### Solution

1. Change the auto assignment to your group or yourself.
2. From the left nav pane, expand **Beverages \> Sales and Distribution \> Shipping and Receiving.**
3. Select **Work With Shipments**.
4. In QBE, do the following:
   1. Enter the shipment number.
   2. Type an asterisk for Branch/Plant. 
   3. Click **Find**.
5. Check the routing status:
   <details><summary>Does a <b>9</b> display and is the Promised ship date blank?</summary><p>
    <ol start="a">
    <li>To the left of the shipment, click the check box to select it. </li>
    <li>On the toolbar, click <b>Row</b> and then select <b>Routing options.</b><div class="note" style="padding: 3px 0px; margin: 6pt 0pt;background-color: yellow;"><b>Note.</b> If the <i>A detail rate was not found</i> error message displays, close the message.</div></li>
    <li>Very that the check box is still selected.</li>
    <li>On the toolbar, click <b>Select</b> and then click the <b>Dates/Times</b> tab.</li>
    <li>Re-enter the promised delivery date and time even if it's already populated.</li>
    <li>Click the <b>Recalculate promised ship date and time</b> check box to select it and click <b>OK</b>. <div class="note" style="padding: 3px 0px; margin: 6pt 0pt;background-color: yellow;"><b>Note.</b> If the <i>Promised ship date and time in past</i> message displays, click <b>OK</b>.</div></li>
    <li>You can proceed to step 6.</li>
    </ol>
   </p>
   </details>

    <details><summary>Is the <b>Promised ship date</b> populated?</summary><br><p>&nbsp;&nbsp;&nbsp;&nbsp;You can proceed to step 6.</p>
   </details>
6. On the toolbar, click <b>Row</b> and then select <b>Routing options</b>.
7. Select the route and click **Select.**
8. Select the route again, and on the toolbar, click **Select**.

If the error still appears, try again or escalate to your team lead.