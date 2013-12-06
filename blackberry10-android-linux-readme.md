<!--- http://notehub.org/2013/12/6/blackberry-10-android-sdk-for-linux --> 
#BlackBerry 10 Android SDK for Linux

Not much has to be done for this SDK to work with Linux as it is just shell scripts and java. All i did was removed the windows batch scripts and chmod 755 the bin dir. With that being said all you have to do is do a git clone and your on your way to converting android apk file to blackberry 10 bar files.

**Requirements**

*	[Ubuntu](http://www.ubuntu.com/)
*	[Openjdk](http://openjdk.java.net/)

>BlackBerry will only support the other sdk's if you are using Ubuntu, so if you plan one using the [Blackberry NDK](http://developer.blackberry.com/native/) and may need support i would suggest Ubuntu. This will run on most Linux distros the way it is. I do all my work on [Debian](http://debian.org). 


**Installation**

		git clone https://github.com/badtoyz/BB10-Android-SDK-2.0.1-beta.git
		cd BB10-Android-SDK-2.0.1-beta

		
**Contact me**

[Email](mailto:badtoyz@gmail.com) - [Twitter](https://twitter.com/badtoyz) - [Github](https://github.com/badtoyz)