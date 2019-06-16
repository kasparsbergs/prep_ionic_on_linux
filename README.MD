# Ionic setup checklist on linux

## Android Studio


Download [android-studio-ide-xxx.xxxxxxx-linux.tar.gz](https://developer.android.com/studio/index.html)


## Gradle
As of Cordova-Android 6.4.0 Gradle is now required to be installed to build Android.

[SDKMAN!](https://sdkman.io/) is a tool for managing parallel versions of multiple Software Development Kits on most Unix-based systems.

```bash
curl -s "https://get.sdkman.io" | bash
```

```bash
sdk install gradle 5.4.1
```

## Java JDK 8

[Download java sdk 8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)



**Step 1:**
Download the latest JDK(jdk-8u212-linux-x64.tar.gz) from this official [link](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

**Step 2:**
Open the terminal (Ctrl + Alt + T) and enter the following command.

    sudo mkdir /usr/lib/jvm

**Step 3:**
Enter the following command to change the directory.

    cd /usr/lib/jvm

**Step 4:**
Extract the jdk-8u212-linux-x64.tar.gz file in that directory using this command.

    sudo tar -xvzf ~/Downloads/jdk-8u212-linux-x64.tar.gz

**Step 5:**
Enter the following command to open the environment variables file.

    sudo -H gedit /etc/environment

**Step 6:**
In the opened file, add the following bin folders to the existing PATH variable.

    /usr/lib/jvm/jdk1.8.0_212/bin
    /usr/lib/jvm/jdk1.8.0_212/jre/bin

The PATH variables have to be separated by colon.
Notice that the installed JDK version is 1.8 update 212. Depending on your JDK version, the paths can be different.
Add the following environment variables at the end of the file.

    J2SDKDIR="/usr/lib/jvm/jdk1.8.0_212"
    J2REDIR="/usr/lib/jvm/jdk1.8.0_212/jre"
    JAVA_HOME="/usr/lib/jvm/jdk1.8.0_212"

The environment file before the modification:

    PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
The environment file after the modification:

    PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/lib/jvm/jdk1.8.0_212/bin:/usr/lib/jvm/jdk1.8.0_212/jre/bin"
    J2SDKDIR="/usr/lib/jvm/jdk1.8.0_212"
    J2REDIR="/usr/lib/jvm/jdk1.8.0_212/jre"
    JAVA_HOME="/usr/lib/jvm/jdk1.8.0_212"



## what's in the `.bashrc`
```bash
# export JAVA_HOME
export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_212/

#  android sdk (DEPRECATED)
export ANDROID_HOME=/home/kb/Android/Sdk
#  android root dir
export ANDROID_SDK_ROOT=/home/kb/Android

#THIS MUST BE AT THE END OF THE FILE FOR SDKMAN TO WORK!!!
export SDKMAN_DIR="/home/kb/.sdkman"
[[ -s "/home/kb/.sdkman/bin/sdkman-init.sh" ]] && source "/home/kb/.sdkman/bin/sdkman-init.sh"
```

## Ionic needs node.js 8 and better

    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash

then 
    
    nvm install 8

## ok now we need to install some npm packages

    npm i -g ionic cordova native-run @angular/cli


## create ionic app

    ionic start myApp tabs

## set the android phone to development mode and connect it to the pc

from within `/myApp` run this command 

 
    ionic cordova run android


---

> if everything is configured correct the app should cpmpile in android studio and open in the phone. 

- it is possible to [use capacitor instead of cordova](https://capacitor.ionicframework.com/docs/getting-started/with-ionic/#existing-ionic-project)

      ionic start myApp tabs --capacitor


- Android studio provides very fast emulators for the latest android API's






