---
title: Quick Start Writing Sample
tags: 
  - tech writing
  - quick start 
description: Knowledgebase articles solve issues with products or services. Customers should not be left to decipher highly technical content. Plus, they don't have the time to sift through mountains of information. My approach to writing knowledgebase articles is by focusing on a specific problem/solution and the audience. 
---

# Quick Start Writing Sample

>**Project:**  Work-related <br>
>**Description:**  I was tasked to rework the developer documentation, specifically the Mobile SDK Quick Start Guide.<br>
>**Date of rewrite:** June 2019 

<hr />

The SDK provides brands with a secure way to foster connections with their customers and increase app engagement and retention. Use this Quick Start guide to get you up and running with a project. When done, you'll be able to send messages between an Android device and the messaging platform.

### Prerequisites

-   Followed the [Getting Started Guide]() to create an account, retrieve your domain, authorize API calls, and authenticate with the platform.

-   Downloaded and installed the [latest version](https://developer.android.com/studio) of **Android Studio**.

-   Downloaded and installed the [latest version](https://gradle.org/install/) of **Gradle**.

### Step 1: Install the Messaging SDK into your project

You can install the Mobile App Messaging SDK using a couple of different methods:

-   *Automatically add the SDK files using Gradle*

-   *Manually copy the SDK files to your project*

#### **Option 1: Automatically add the SDK files using Gradle**

You can use Gradle, an automation tool, to scale your projects effortlessly.

1. In your project, locate and double-click **Gradle Scripts > build.gradle (Module: app)**.

   ![](https://www.pscmdesigns.com/images/quick-start-guide1.png)

2. In the **dependencies** section, add:

   ```java
    dependencies {
        implementation "com.pscmdesigns.android:messaging_sdk:3.7.0"
    }
   ```

   **Example: Build.gradle (Module: app) file**
   ```java
    apply plugin: "com.android.application"
    
    android {
        compileSdkVersion 26
        defaultConfig {
        applicationId "com.mybrand.app"
        minSdkVersion 19
        targetSdkVersion 27
        versionCode 1
        versionName "1.0"
        }
        buildTypes {
            release {
                minifyEnabled false
                proguardFiles getDefaultProguardFile("proguard-android.txt"),
                "proguard-rules.pro"
            }
        }
    }
    dependencies {
        implementation fileTree(dir: "libs", include: ["\*.jar"])
        implementation "com.android.support:appcompat-v7:26.1.0"
        implementation "com.android.support.constraint:constraint-layout:1.0.2"
        testImplementation "junit:junit:4.12"
        androidTestImplementation "com.android.support.test:runner:1.0.1"
        androidTestImplementation
        "com.android.support.test.espresso:espresso-core:3.0.1"
        //  SDK
        implementation "com.pscmdesigns.android:messaging_sdk:3.7.0"
    }
   ```

#### **Option 2: Manually copying the SDK files to your project**

1. [Download]() the latest SDK package.

2. Extract the file to a folder on your computer. The package contains all of the files you need to add to your project. Also in the package, you get a sample app that demonstrates how to use the SDK.

3. In your Android Studio project, go to **File \> New \> Import module**.

4. Navigate to the folder where you extracted the SDK, select the **messaging_sdk module**, and then click **Finish**.

5. In your **build.gradle** of your app, and in the android section, make sure  the *compileSdkVersion* is at least version **26**:

   ```java
    android {
        compileSdkVersion 26
        buildToolsVersion "26.0.0"
    repositories {
            flatDir {
                dirs project(":messaging_sdk").file("aars")
            }
    }
   ```

6. In the **defaultConfig** section, make sure the *minSDKVersion* is set **19**:

   ```java
    defaultConfig {
        applicationId "com.mybrand.app"
        minSdkVersion 19
        targetSdkVersion 27
        versionCode 1
        versionName "1.0"
    testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
    }
   ```

7. In the **dependencies** section, add:

   ```java
   compile project(":messaging_sdk")
   ```

8. **Build.gradle file example:**

   ```java
    apply plugin: "com.android.application"

    android {
        repositories {
            flatDir {
                dirs project(":messaging_sdk").file("aars")
            }
        }
        compileSdkVersion 26
        buildToolsVersion "26.0.0"
            defaultConfig {
                applicationId "com.mybrand.app"
                minSdkVersion 19
                targetSdkVersion 27
                versionCode 1
                versionName "1.0"
                testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
                multiDexEnabled true
    
        }
        buildTypes {
            release {
                minifyEnabled false
                proguardFiles getDefaultProguardFile("proguard-android.txt"),"proguard-rules.pro"
            }
        }
    }

    dependencies {
        compile fileTree(dir: "libs", include: ["\*.jar"])
        androidTestCompile("com.android.support.test.espresso:espresso-core:2.2.2", {
            exclude group: "com.android.support", module: "support-annotations"
        })
        compile "com.android.support.constraint:constraint-layout:1.0.2"
        compile "com.google.firebase:firebase-messaging:11.6.0"
        compile "com.google.firebase:firebase-core:11.6.0"

        testCompile "junit:junit:4.12"
        // SDK
        compile project(path: ":messaging_sdk")
    }

    apply plugin: "com.google.gms.google-services"
   ```

9. In your **settings.gradle** of your app, add:

    ```java
    include ":messaging_sdk"
    ```

### Step 2: Integrate code for basic deployment

1. Add permissions to your app’s AndroidManifest.xml file:

   ```xml
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

2. Add imports to your class imports section:

   ```java
    import com.pscmdesigns.api.PscmDesignsCallback;
    import com.pscmdesigns.infra.InitPscmDesignsProperties;
    import com.pscmdesigns.infra.callbacks.InitPscmDesignsCallBack;
    import com.pscmdesigns.messaging.TaskType;
    import com.pscmdesigns.messaging.model.AgentData;
    import com.pscmdesigns.messaging.sdk.api.PscmDesigns;
   ```

### Step 3: Initialize the Messaging SDK

Before you can show a conversation, you must initialize the Messaging SDK.

{% include alert.html type="info" title="Note" content="If you want to use the Monitoring API, you must initialize the Messaging SDK with Monitoring Params." %}



1. **Set your app ID and view controller.** Provide your APP_ID as a string your application's class.

   ```java
    private static final String APP_ID = "com.mybrand.app";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
   ```

2. **Select your choice of authentication** for initializing the SDK instance:

   - [Code Flow]() (authenticated)
     The back-end verifies the authentication token sent by the SDK with your system servers. If the key cannot be verified on your company’s
backend servers, this call fails.

     ```java
     LPAuthenticationParams().setAuthKey("yourAuthCode").
     ```

     >**Tip!** Alternatively, when using this method, you can also set a special redirect URL when authenticating by calling: `lpAuthenticationParams.setHostAppRedirectUri("yourRedirectUrl")`.


   - [Implicit Flow]() (authenticated)

     ```java
     LPAuthenticationParams().setHostAppJWT("yourJwt")
     ```

     Once the Authentication key expires, you get notified with a callback / local intent `void onTokenExpired`.

     To re-connect with a new Authentication key, use `reconnect(LPAuthenticationParams lpAuthenticationParams)`.

     Errors while trying to connect uses callback: `void onError(TaskType type, String message);`.

   - **Unauth Flow**

     ```java
     String brandID = "53949244";
     String appInstallID = "46bcf782-feee-490d-861d-2b5feb4437c8";
     ```

   - **Signup Flow**

     ```java
     String brandID = "62219232";
     ```

3. **Show the conversation view.** If your system implementation involves an authentication step, you must call our showConversation method provided by
    the LPMessagingSDK instance. It pushes a new navigation stack containing the conversation view. Choose an authentication method:

    - **Activity mode**
 
      ```java
      pscmdesigns.showConversation(Activity activity, LPAuthenticationParams lpAuthenticationParams, ConversationViewParams params‎);
      ```

    - **Fragment mode (Attach the returned fragment to a container in your activity)**

      ```java
      pscmdesigns.getConversationFragment(LPAuthenticationParams lpAuthenticationParams, ConversationViewParams params‎);
      ```

      When using fragment mode, you could use the provided SDK callbacks in your app in order to implement functionalities such as menu items, action bar
indications, agent name, and typing indicator.

1. **Initialize your application.** We have provided examples to use to help
    you get started. The demo account has basic features available for
    demonstrating the Conversational Commerce experience in the LiveEngage
    console.

    - **CodeFlow**
      ```java
      public void startCodeFlow(View v) {
        String brandID = "62219232";
        final String authCode = "k16336";
        pscmdesigns.initialize(this, new InitLivePersonProperties(brandID, APP_ID, new InitLivePersonCallBack() {

            @Override
            public void onInitSucceed() {
                LPAuthenticationParams lpAuthenticationParams = new LPAuthenticationParams(LPAuthenticationParams.LPAuthenticationType.AUTH);
                lpAuthenticationParams.setAuthKey(authCode);
                pscmdesigns.showConversation(MainActivity.this, lpAuthenticationParams, new ConversationViewParams());
            }

            @Override
            public void onInitFailed(Exception e) {
            }
        }));
      }
      ```

   - **ImplicitFlow**

    ```java
    public void startImplicitFlow(View v) {
        String brandID = "42391995";
        final String jwt =
        "eyJhbGciOiJSUzI1NiJ9.eyAgInN1YiI6ICJoZWxsbyIsICAiaXNzIjogImh0dHBzOi8vTFAtQXV0aC5jb20iLCAgImV4cCI6MTU1Mzc5NDAyMSwgICJpYXQiOjE1NTM3OTM0MjF9.GP0iCe1k3aQbWHp-FYKhpfK-MZqktQ8pByTTF5lAHTelCyDAxhgHyMIq5J9mJnSoIdTlUbmscRHpy2MCop-AlYx5Sz66y1aX38AD8Rat1k_SnbPNbvbEysomb_SjxZ3uleN_OCzrSqGJrLXP6yIN2UiuuvKM62i-e-aQVIWzIXWMxjgmH9n_ZUOkgq_0jY3Me8r78dKsitc-jvzGzbasv81u40fR-7Y-ViOZliFOLjVBl2VWCbgcrGerLUyWVJQW69Hn3TlvvVpSVZk-IUU8hpYorcItIb-XNV2mOVkuZmzlGo7a1nIhJCCWzP5qaQvCCecSHTTHbcROwwE7dk6vKg";
        pscmdesigns.initialize(this, new InitLivePersonProperties(brandID, APP_ID, new InitLivePersonCallBack() {
            @Override
            public void onInitSucceed() {
                LPAuthenticationParams lpAuthenticationParams = new LPAuthenticationParams(LPAuthenticationParams.LPAuthenticationType.AUTH);
                lpAuthenticationParams.setHostAppJWT(jwt);
                pscmdesigns.showConversation(MainActivity.this, lpAuthenticationParams, new ConversationViewParams());
            }
            @Override
            public void onInitFailed(Exception e) {
            }
        }));
    }
    ```

   - **UnauthFlow**

       ```java
       public void startUnauthFlow(View v) {
           String brandID = "53949244";
           String appInstallID = "46bcf782-feee-490d-861d-2b5feb4437c8";
           final MonitoringInitParams monitoringInitParams = new MonitoringInitParams(appInstallID);
           pscmdesigns.initialize(this, new InitLivePersonProperties(brandID, APP_ID, monitoringInitParams, new InitLivePersonCallBack() {
               @Override
               public void onInitSucceed() {
                   LPAuthenticationParams lpAuthenticationParams = new LPAuthenticationParams(LPAuthenticationParams.LPAuthenticationType.UN_AUTH);
                   pscmdesigns.showConversation(MainActivity.this, lpAuthenticationParams, new ConversationViewParams());
               }
               @Override
               public void onInitFailed(Exception e) {
               }
           }));
       }
       ```

   - **SignupFlow**

       ```java
       public void startSignupFlow(View v) {
           String brandID = "62219232";
           pscmdesigns.initialize(this, new InitLivePersonProperties(brandID, APP_ID, new InitLivePersonCallBack() {
               @Override
               public void onInitSucceed() {
                   LPAuthenticationParams lpAuthenticationParams = new LPAuthenticationParams(LPAuthenticationParams.LPAuthenticationType.SIGN_UP);
                   pscmdesigns.showConversation(MainActivity.this, lpAuthenticationParams, new ConversationViewParams());
               }
               @Override
               public void onInitFailed(Exception e) {
               }
           }));
       }
       ```

| **Element**       | **Description**     |
|-------------------|--------------------------|
| **brandID**       | Your account ID. If you don’t have one, please contact your representative.        |
| **APP_ID**        | Your application ID (com.mybrand.app), which is used in the `registerLPPusher` method. |
| **onInitSuccess** | Callback that indicates the init process has finished successfully.        |
| **onInitFailed**  | Callback that indicates the init process has failed.     |

**Example implementation:**

```java
private static final String APP_ID = "com.mybrand.app";

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
}

public void startCodeFlow(View v) {
    String brandID = "62219232";
    final String authCode = "k16336";
    pscmdesigns.initialize(this, new InitLivePersonProperties(brandID, APP_ID, new InitLivePersonCallBack() {
        @Override
            public void onInitSucceed() {
                LPAuthenticationParams lpAuthenticationParams = new LPAuthenticationParams(LPAuthenticationParams.LPAuthenticationType.AUTH);
                lpAuthenticationParams.setAuthKey(authCode);
                pscmdesigns.showConversation(MainActivity.this, lpAuthenticationParams, new ConversationViewParams());
        }
        @Override
        public void onInitFailed(Exception e) {
        }
    }));
}
```

{% include alert.html type="info" title="Note" content="Make sure that the init process, from the onInitSucceed callback, finished successfully." %}

[Step 1: Install the Messaging SDK into your project](#step-1-install-the-messaging-sdk-into-your-project)
[Step 2: Integrate code for basic deployment](#step-2-integrate-code-for-basic-deployment)
[Step 3. Initialize the Messaging SDK](#step-3-initialize-the-messaging-sdk)
[Next Steps](#next-steps)

### Next Steps

Congratulations! You're all set.

You can now do any of the following:

-   [Configure push notifications]().
    Push and local notifications are a key factor that makes the experience better for consumers - they never have to stay in your app or keep the window open as they will get a proactive notification as soon as a reply or notice is available.

-   [Enable features in your AndroidManifest.xml file]().
    If you had your account team or support enable vibrate on new message, photo sharing, or audio messaging, you must add these features to your app's AndroidManifest.xml file.
