---
title: How-to Writing Samples
tags: 
  - ux writing
  - tech writing
  - how-tos 
description: How-to's are easy-to-follow instructions that explain step-by-step how to perform a task or use a specific feature in an app. Instructions are the way you do things, for example, making cookies includes the ingredients, how to mix the ingredients, and how and at what temperature you should make them. 

 
---

# How-to Writing Samples

When I write how-to's, I use the [minimalism](https://www.technicallywriteit.com/the-art-of-saying-less-minimalism/) approach. How-to's are easy-to-follow, action-oriented instructions that explain step-by-step how to perform a task or use a specific feature in an app. Instructions are the way you do things, for example, making cookies includes the ingredients, how to mix the ingredients, and how and at what temperature you should make them. 

<hr />

### Mobile SDK - Photo and file sharing

Mobile SDK v3.9 introduces a feature for agents within the app to share photos or files with the consumers.  Agents can share a reference photo or photos of any product to visually guide consumers with product awareness, steps on how to use the product, or review comments of a product.  Agents can also share files to provide consumers with information such as mortgage documents, product catalog, or transaction details as requested by consumers. Agents can even share photos or files in a resolved conversation to resume the conversation with the consumer.

When the agent shares any supported file type, if the consumer isn't within the conversation view, they get a notification from the customer app only if the push notification is enabled. Otherwise, when the consumer returns, a thumbnail for the photo or file appears in the conversation window.

- **Files:** the consumer can tap on it to view it full screen, share it through the default app on the device, or save it to a location on the device.

   The Android SDK supports opening any file types other than images through the picker application. The consumer can either long click on the thumbnail or open the file through the picker application to share and save the file.

   The iOS SDK supports the opening of all the supported file types on the device as per the iOS operating system.

- **Photos:** the consumer can tap on the photo to view it full screen or share it through the default app on their device.  Consumers cannot download images; they can only preview or share images.

#### Supported formats

- PNG
- JPG/JPEG
- GIF (non-animated) - previewed as a static image only
- PDF
- DOCX
- PPTX
- XLSX

#### Photo and file sizes

- Thumbnail - 30 KB (base64-encoded)
- Max upload size allowed - 5 MB uncompressed

**For SDKs previous to 3.8.** The max upload size allowed is 3 MB.

#### Notes and limitations

- Photo sharing is two way (agent-to-consumer and consumer-to-agent). Still, file sharing is one way only (agent to consumer).

  **For SDKs previous to 3.8:** Photo-sharing is one-way only (from consumer-to-agent, but not vice versa) and available for the Mobile Message SDK only.

- If an attempt to view a photo is unsuccessful, an error icon covers the thumbnail.

- If an attempt to download a file is unsuccessful, an error icon covers the thumbnail.  Upon retry, the file attempts to download again. Retry can be attempted as many times as possible (in case of a poor network) till the file download successfully.

- The consumer can return to a resolved conversation to view the photos, as long as the photos are part of the conversation history.

- If an agent sends an unsupported file, a message shows indicating the file type is not supported, and the agent should retry sending a supported file format. On the consumer side, they see an empty message with no content.

- For authenticated users, backgrounding the app while loading the photo does not get interrupted.

- For unauthenticated sessions, consumers must tap the photo again with each visit because the history gets cleared when a session expires or logs the consumer out.

#### How photo sharing works - Android

**For Android SDK 3.0 on an Oreo Device (8.0 &amp; 8.1).** Add support for Notification Channel.

##### Step 1. Enable or disable photo sharing

1. Change the boolean value:

   `<bool name="enable_photo_sharing">`

   By default, this value is **false**.

2. Contact your Account Team to have the feature enabled on your account.

##### Step 2. Change settings

1. Set the max number of photos or files to save on disk:

   `<integer name="max_number_stored_images">`

   `<integer name="max_number_stored_documents">`

   The default is 20. If exceeding the max value of photos or files, the SDK deletes the oldest file.

2. Set the max image size:

   `<integer name="max_image_size_kb">`

   The default max image is 3000kb.

3. Change the color of the attachment menu:

   `<color name="attachment_menu_item_background_color">`

   `<color name="lp_attachment_menu_background_color">`

   `<color name="lp_attachment_menu_item_text_color">`

   `<color name="lp_attachment_menu_item_icon_color">`

4. Change the text of buttons:

   `<string name="lp_accessibility_gallery">`

   `<string name="lp_accessibility_camera">`

5. Define the max number of stored images allowed locally.

   `<integer name="max_number_stored_images">`

   The default max number is 20.

6. Define the resize dimensions:

   `<integer name="thumbnail_longer_dimension_resize">`

   The default thumbnail dimension is 100.

   `<integer name="full_image_longer_dimension_resize">`

   The default full image dimension is 800.

7. Set the compression rate (percentage) for full images:

   `<integer name="full_image_compression_rate">`

   The default compression rate is 50.

   More advanced configurations (image size, compression rate, etc..) can be found under Photo Sharing in the Configuring the SDK section.

#### How photo sharing works - iOS

##### Step 1. Set the requirements for Custom View Controller Mode

When using Custom View Controller Mode, you must remove the Conversation view when leaving the App. To avoid dismissing the View when presenting CSAT/SecureForms/PhotoSharing View, you should only dismiss the Conversation view if Moving From ParentView:

```swift

if (self.conversationQuery != nil && self.isMovingToParentViewController){

  LPMessagingSDK.instance.removeConversation(self.conversationQuery!)

}
```

When using ViewController Mode, on the Navigation Bar Back Button, you can simply call **LPMessagingSDK.instance.removeConversation(self.conversationQuery!)**.

##### Step 2. Add app privacy settings

1. Set the photo library privacy settings:
  
   - **Key:** NSPhotoLibraryUsageDescription
   - **Value:**"Photo Library Privacy Setting for Mobile App Messaging SDK for iOS"

2. Set the camera privacy settings:

   - **Key:** NSCameraUsageDescription
   - **Value:**"Camera Privacy Setting for Mobile App Messaging SDK for iOS"

    Values for these descriptions are up to the brand to define; these are only examples.

3. Set the file-sharing privacy settings:

   - UIFileSharingEnabled: Application supports iTunes file sharing
   - Privacy - Photo Library Usage Description
   - Privacy - Photo Library Additions Usage Description

    iOS supports the preview of file types per iOS operating system and requires some configurations to be enabled ("YES") within the Host App's plist file. Enabling supports file sharing and the export and saving of photos.

4. Save documents or photos to a directory belonging to the host app, enable the following flag with **caution**.  
  
   >**Note:** A current limitation within the SDK causes the SQL files to be public if enabling this setting. Therefore, we suggest you do not enable this setting until a fix is available in a future release.  If this functionality is essential to your user flow, enable at the user's risk.

   LSSupportsOpeningDocumentsInPlace: Supports opening documents in place

##### Step 3. Enable or disable photo and file sharing

1. Change the boolean value:

   `LPConfig.defaultConfiguration.enablePhotoSharing`

   By default, the value is set to **false**.

   `LPConfig.defaultConfiguration.enableFileSharing`

   By default, the value is **true**.

2. Contact your Account Team to have the feature enabled on your account.

##### Step 4. Change the settings

1. Set the max number of photos or files to save on disk:

   `LPConfig.defaultConfiguration.maxNumberOfSavedFilesOnDisk`

   The default is 20. If exceeding the max value of photos or files, the SDK deletes the oldest file.

2. Change the background color of attachment menu:

   `LPConfig.defaultConfiguration.photosharingMenuBackgroundColor`

3. Change the text of buttons:

   `LPConfig.defaultConfiguration.photosharingMenuButtonsTextColor`

4. Change the menu button&#39;s background color:

   `LPConfig.defaultConfiguration.photosharingMenuButtonsBackgroundColor`

5. Change the menu button&#39;s tint color:

   `LPConfig.defaultConfiguration.photosharingMenuButtonsTintColor`

7. Customize the navigation bar on UIDocumentationInteractionController:

   **Window Mode:**

   The UIDocumentationInteractionController adopts applicable branding customizations that have been set, for example:

   - `conversationNavigationBackgroundColor` sets the NavController tint color with translucence set to false.
   - `conversationNavigationTintColor` colors the L & R bar buttons as well as the title color.

   **View Controller Mode:**

      Your custom applicable navigation bar traits apply to the UIDocumentationInteractionController.

      You can find all the related configurations in the [resources ID table](), under Photo Sharing.