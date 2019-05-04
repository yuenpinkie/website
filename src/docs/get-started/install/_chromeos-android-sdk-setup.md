## Android setup (without Android Studio)

### Install Java

```terminal
$ sudo apt update
$ sudo apt install default-jre
$ sudo apt install default-jdk
```

### Install the Android SDK's

Download the [Android SDK tools]({{site.android-dev})/studio/#downloads and 
select the “Command Line Tools only” option.

Drag and drop the downloaded zip into your Linux Files folder through the 
Chrome OS Files app. This moves it to the home directory, notated as $TOOLS_PATH 
going forward (`~/`)

Unzip the tools and then add it to your path

```terminal
$ unzip ~/sdk-tools-linux*
$ export PATH="$PATH:$TOOLS_PATH/tools/bin"
```

Download the SDK packages using the sdkmanager tool (version numbers here are 
the latest at time of publishing):

```terminal
$ sdkmanager "build-tools;28.0.3" "emulator" "tools" "platform-tools" 
"platforms;android-28" "extras;google;google_play_services" 
"extras;google;webdriver" "system-images;android-28;google_apis_playstore;x86_64"
```

Add the Android platform tools to your path (you should find this where you 
ran the sdkmanager command: probably `~/`)

```terminal
$ export PATH="$PATH:[/path/to/platform/tools]/platform-tools
```

Set the ANDROID_HOME variable to where you unzipped sdk-tools before (aka 
you’re $TOOLS_PATH):

```terminal
$ export ANDROID_HOME="$TOOLS_PATH"
```

Now, run flutter doctor to accept the android-licenses:

```terminal
$ flutter doctor --android-licenses
```