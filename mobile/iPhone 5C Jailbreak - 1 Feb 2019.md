## Looking to jailbreak iPhone 5 and  iPhone 5C?

I had quite a bit of problem getting SSH access to my iPhone 5C (Model A1456). Here are the steps I took to gain eventual access. Do take a look if you have trouble following the usual routes.

h3lix is a semi-untethered jailbreak for 32-bit devices running any version of iOS 10, developed by tihmstar and Siguza. h3lix works by sideloading an IPA using Cydia Impactor. It is one of five jailbreak projects based on the v0rtex exploit, the others being Saïgon for some 64-bit devices on 10.2.1, g0blin for some 64-bit devices on 10.3-10.3.3, doubleH3lix for some 64-bit devices on 10.x, and Meridian for 64-bit devices on 10.x.

Since iOS 10.3.3 is the last update for iPhone 5C, it means that the jailbreak process can be repeated even if one of your team mates updates your iPhone by accident (yes, that happened to me).

1. Download h3lix jailbreak from https://h3lix.tihmstar.net/.
2. Have the following information on hand - Apple ID and one set of app-specific password. This assumes your Apple ID is protected with two factor authentication (which it should).
3. Download Cydia Impactor from http://www.cydiaimpactor.com/.
4. Connect iPhone 5C to Mac computer.
5. Use h3lix to jailbreak.Drag the h3lix IPA file onto the Cydia Impactor window.
6. Provide the Apple ID and app-specific password when requested.
7. Execute the h3lix app on the iPhone. Go to Settings > General > Profiles and Device Management to trust the enterprise certificates by the developer. The iPhone must have access to https://ppq.apple.com during this phase.
8. Open the h3lix app and click the "jailbreak" button.
9. Open the h3lix app and click the "Run UiCache" button.
10. Install AFC2 and Mterminal from the Cydia store
11. Attempt to open Mterminal. If this fails, repeat steps 8 and 9.
12. In the terminal, use the following command:
`launchctl start com.openssh.sshd`
14. Set up the proxy redirection using a command such as  `iproxy 2222 22`
15. SSH into the iPhone using the command such as `ssh -p 2222 root@localhost`
16. Key in the password when requested. The default password is "alpine".
17. You will need to clear your SSH key from the known_hosts folder if you had connected via SSH to any device using the same port. The file location on MacOS may be in /Users/josz5930/.ssh/, if your user name is "josz5930".
18. Change your password to a long and complex password.

#### References:

* https://www.theiphonewiki.com/wiki/H3lix
* https://cydia.saurik.com/info/com.saurik.afc2d/
* https://www.unix.com/man-page/osx/1/launchctl/
* https://iphonedevwiki.net/index.php/SSH_Over_USB
* https://support.apple.com/en-us/HT204397
* https://support.apple.com/en-us/HT204460
* https://github.com/josz5930/secarticles/tree/master/mobile/res/iPhoneTunnel.app/
* Current link to iPhoneTunnel for Mac: https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/iphonetunnel-mac/iPhoneTunnel2.3-beta1.zip
