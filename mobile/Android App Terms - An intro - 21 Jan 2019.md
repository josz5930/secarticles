Oh Dalvik, what's OAT, ART, ODEX?
====
Let's go through some terms relating to Android applications.

__APK__ - Android Package. A package file format that is used by the Android system. Yyou can use the unzip command to extract an APK contents, which leads some to comment that it is a glorified ZIP file.

The command to extract the contents of an APK file is:

`unzip josz5930.apk -d josFolder`

__DEX__ - A Dex file contains code (Dalvik bytecode) that is ultimately executed by the Android Runtime. Every APK has a single classes.dex file, which references any classes or methods used within an app. Essentially, any Activity, Object, or Fragment used within your codebase will be transformed into bytes within a Dex file that can be run as an Android app. 

Using the dex tool, you can convert the .class files into .dex files. The command is similar to the following:

`dx.bat --dex --verbose --output .\bin\classes.dex .\bin\classes`  

__ODEX__ - Optimized Dalvik EXcutable file. To optimize the Dalvik bytecode, the original DEX file (e.g. classes.dex) is transformed into another file that contains "optimized bytecode". In Android 4.4 and below, DEX files were optimized to this ODEX format via the _dexopt_ utility.

An odex is basically a pre-processed version of an application's classes.dex that is execution-ready for Dalvik. When an application is odexed, the classes.dex is removed from the APK archive and it does not write anything to the Dalvik cache. An application that is not odexed ends up with 2 copies of the classes.dex file--the packaged one in the APK, and the processed one in the Dalvik cache. It also takes a little longer to launch the first time since Dalvik has to extract and process the classes.dex file.

__OAT__- The file format of the file produced by optimizing DEX files via an Ahead of Time (AOT) compilation using the _dex2oat_ utility. More accurately, the result of running the utility is a compiled OAT native code file that is wrapped by the ELF format.

__Java VM__ - Unlike normal assembly language, Java programs are compiled into Java bytecode so that programs written in Java are able to be run in any environment with the Java Runtime Environment (JRE). This is due to the capability of the Java Virtual Machine that is part of the JRE that interprets the bytecode and translates it into machine code.

__Dalvik VM__ - Similar to the Java VM, Dalvik VM does the execution of bytecode on the Android system. Unlike Java VM, Dalvik VM uses a register based model and is optimized to run on Android.

__ART__ - This can refer to the Android Runtime or a file format. The replacement of the Dalvik Virtual machine since Android 5.0 and later. It was also with Android 5.0 that the Just in Time approach was replaced with "Ahead of Time" approach.


#####References & links:
* [Dalvik,ART与ODEX相爱相生](https://www.jianshu.com/p/389911e2cdfb)
* [Android Formats, LIEF](https://lief.quarkslab.com/doc/latest/tutorials/10_android_formats.html)
* [Comparative Analysis of Mobile App Reverse Engineering Methods on Dalvik and ART](https://pdfs.semanticscholar.org/d67f/abdd7e65c2551c2c86f201a67c7f7a143373.pdf)
* ["What does OAT mean?" - StackOverflow](https://stackoverflow.com/questions/28435860/what-does-oat-mean)
* [关于Dalvik、ART、DEX、ODEX、JIT、AOT、OAT](http://rangerzhou.top/2017/06/30/Something_about_Dalvik_ART_DEX_ODEX_JIT_AOT_OAT/)
* [What Is Odex And Deodex In Android [Complete Guide]
](https://www.addictivetips.com/mobile/what-is-odex-and-deodex-in-android-complete-guide/)
* [Quora - What is a .dex file? What is dexopt? What is odex? What is dexoat? What is ELF? How does this all work?
](https://www.quora.com/What-is-a-dex-file-What-is-dexopt-What-is-odex-What-is-dexoat-What-is-ELF-How-does-this-all-work)
* [Android application package, Wikipedia](https://en.wikipedia.org/wiki/Android_application_package)
* [Android Runtime – DVM vs ART, AOT vs JIT](https://www.journaldev.com/23464/android-runtime-dvm-vs-art-aot-vs-jit)
* [JSR-000202 JavaTM Class File Specification Update](https://jcp.org/aboutJava/communityprocess/final/jsr202/index.html)