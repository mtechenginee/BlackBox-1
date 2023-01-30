![xx](assets/banner.png)

# Unreal Engine BlackBox
> The only people who have anything to fear from free software are those whose products are worth even less. 
>
> <p align="right">——David Emery</p>

![](https://img.shields.io/badge/language-java-brightgreen.svg)
![Repository Size](https://img.shields.io/github/repo-size/MrCode403/BlackBox)
![CI](https://github.com/MrCode403/BlackBox/actions/workflows/build-apk.yml/badge.svg)
[![Total downloads](https://img.shields.io/github/downloads/MrCode403/BlackBox/total)](https://github.com/MrCode403/BlackBox/releases)
![Commit Activity](https://img.shields.io/github/commit-activity/m/MrCode403/BlackBox)
<img src="https://img.shields.io/github/v/release/MrCode403/BlackBox?include_prereleases&amp;label=latest%20release" alt="Latest release">

BlackBox BlackBox is a virtual engine that can clone and run virtual applications on Android, and has the ability to run without installation. The black box can control the running virtual application and do whatever it wants.

## support
4x is not considered for the time being, it is currently compatible with 5.0 ~ 12.0 and will follow up with the follow-up new system.

If conditions permit, downgrade targetSdkVersion to 28 or below for better compatibility.

*** Stability has not been extensively tested, it is only for learning and communication, please do not use it for other purposes ***

## Download the compiled version
Stable and beta downloads
- Stable version A verified stable version is manually released by the administrator. [Download URL](https://github.com/FBlackBox/BlackBox/releases)
- Beta version The latest code version is automatically compiled by the machine, you can experience the latest experience and there may be problems. [Download URL](https://github.com/AutoBlackBox/BlackBox/tags)

## how to use
### Step 1. Initialization, add the following code initialization in Application

```java
    @Override
    protected void attachBaseContext(Context base) {
        super.attachBaseContext(base);
        try {
            BlackBoxCore.get().doAttachBaseContext(base, new ClientConfiguration() {
                @Override
                public String getHostPackageName() {
                    return base.getPackageName();
                }
            });
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    @Override
    public void onCreate() {
        super.onCreate();
        BlackBoxCore.get().doCreate();
    }
```

### Step 2. Install the application into the black box
```java
    // Installed apps can provide a package name
    BlackBoxCore.get().installPackageAsUser("com.tencent.mm", userId);
    
    // Uninstalled apps can provide paths
    BlackBoxCore.get().installPackageAsUser(new File("/sdcard/com.tencent.mm.apk"), userId);
```

### Step 2. Run the application in the black box
```java
   BlackBoxCore.get().launchApk("com.tencent.mm", userId);
```

### Open multiple applications
<img src="assets/multiw.gif" width="50%">

### Related APIs
#### Get the installed applications in the black box
```java
   // flgas should be the same as the normal way to obtain installed applications
   BlackBoxCore.get().getInstalledApplications(flags, userId);
   
   BlackBoxCore.get().getInstalledPackages(flags, userId);
```

#### Get the User information in the black box
```java
   List<BUserInfo> users = BlackBoxCore.get().getUsers();
```
For more other operations, you can probably see the BlackBoxCore function name.


#### Xposed related
- Added support for using XP modules
- Xposed has been roughly detected, [Xposed Checker](https://www.coolapk.com/apk/190247), [XposedDetector](https://github.com/vvb2060/XposedDetector) cannot detect


## How to participate in the development?
### The application is divided into 2 modules
- app module, user operation and UI module
- Bcore module, this module is the core module of BlackBox, responsible for completing the scheduling of the entire black box.

If you need to participate in the development, please directly pr. For related tutorials, please Google or see [How to submit the first pull request on GitHub](https://chinese.freecodecamp.org/news/how-to-make-your-first -pull-request-on-github/)
### PR Notice
1. Both Chinese and English instructions are acceptable, but the problem must be explained in detail
2. Please follow the code style and design of the original project

## plan
 - More Service API virtualization (currently many use system API, only a few have been implemented)
 - Provide more interfaces to developers (virtual positioning, application injection, etc.)

## sponsorship
This project is a free and open source project, and the daily maintenance consumes a lot of energy. Feel free to speed things up or buy the author a cup of coffee.

- BTC: 3FCo9QtaSbGMhmZYzvL4XUoJUUxZeSdha4
- USDT（TRC20）: TDzBj9eV1Cdmmj9xd5Y1YLsQqC8zVgi7yd

## Thanks
- [VirtualApp](https://github.com/asLody/VirtualApp)
- [VirtualAPK](https://github.com/didi/VirtualAPK)
- [BlackReflection](https://github.com/CodingGay/BlackReflection)
- [FreeReflection](https://github.com/tiann/FreeReflection)
- [Pine](https://github.com/canyie/pine)

### License

> ```
> Copyright 2022 BlackBox
>
> Licensed under the Apache License, Version 2.0 (the "License");
> you may not use this file except in compliance with the License.
> You may obtain a copy of the License at
>
>    http://www.apache.org/licenses/LICENSE-2.0
>
> Unless required by applicable law or agreed to in writing, software
> distributed under the License is distributed on an "AS IS" BASIS,
> WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
> See the License for the specific language governing permissions and
> limitations under the License.
> ```
