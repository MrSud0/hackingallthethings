---
  title: "Android"
---
# Intro
**Native and Hybrid applications**
Native are either Java (Java, Kotlin) or IOS  (Swift or Objective C)
Hybrid use HTML, CSS, Javascript in frameworks like Apache Cordova, PhoneGap, Ionic etc.

Smali
.apk file, contains a .dex file which contains binary Dalvik bytrecode
Smali runs on Dalvik VM, which is Android's JVM.

In dalvik's bytecode, registers are always 32 bits, and can hold any type of value. 2 registers are used to hold 64 bit types (Long and Double).
#### Application infrastructure
- Manifest (AndroidManifest.XML), The manifest file in binary XML format
- Dalvik byteode (classes.dex), application code complied in the dex format
- Resources.arsc, file containing precompiled application resources, in binary XML.
- Signatures (Meta-INF), Folder containing the MANIFEST.MF file, which stores meta data about the contents of the JAR. which sometimes will be store in a folder named original.The signature of the APK is also stored in this folder.
- Asset (assets/), optional folder containing applications assets, which can be retrieved by AssetManager.
- Native liraries (lib/), optional folder containing applications assets, which can be retrieved by AssetManager.
- Resources (res/), folder containing resources not compiled into resources.arsc

#### AndroidManifest.xml common attributes
- Manifest tag	contains android installation mode, package name, build versions
- Permissions	custom permission and protection level
- uses-permissions	requests a permission that must be granted in order for it to operate, full list of permission api can refer here.
- uses-feature	Declares a single hardware or software feature that is used by the application.
- Application	The declaration of the application. Will contains all the activity
- Activity	Declares an activity that implements part of the application visual user interface.
- intent-filter	Specifies the types of intents that an activity, service, or broadcast receiver can respond to.
- service	Declare a service as one of the application components.
- receiver	Broadcast receivers enable applications to receive intents that are broadcast by the system or by other applications, even when other components of the application are not running.
- provider	Declares a content provider component. A content provider is a subclass of ContentProvider that supplies structured access to data managed by the application.
# Techniques
# Chekclist
# Resources
