
### Physical penetration testing - Getting past the first door

Physical Penetration Testing is something that is performed by a penetration test team to understand the true effectiveness of physical security controls. These controls are placed in areas containing access to information - such as data centers, offices, substations and critical infrastructure rooms.

Physical access controls include locks, sensors, cameras, man-traps, security guards, etc. In this article, I will be writing on technical bypass techniques for doors and locks. A future article may cover other controls (e.g. security guards) or non-technical attacks (e.g. Character impersonation). 

The technical bypass techniques mentioned is applied mostly at the "Vulnerability identification" and "exploitation" phases of the Physical Penetration Testing. As a reminder, the physical penetration test can be split into the following phases:

* Passive Reconnaissance
* Open Source Intelligence (OSINT)
* Active Reconnaissance (drones, onsite covert observation)
* Vulnerability Identification
* Exploitation

Most of the information that is written below is from the talk "I'll let myself in: Tactics of Physical Pen Testers" (27 October 2017), that Deviant Ollam gave in Wild West Hackin' Fest 2017.


| Physical Element  |Attack   |Defence   |
|---|:-:|---|
| Door Hinge  |  Use a nail to knock away the hinge | Use security hinges and Jamb Pin Screws to secure the door hinge  |
| Door Latch | insert latch slipping tool into the place in-between the door | Use dead latches with proper door fitment (e.g. strike plate is the correct size) |
| Crash bars  |  push crash bars from outside using a hook |Ensure there is no gap between for hooks to go through. (Weather strips do not count)|
| Deadbolts with thumb turn |  Use a professional thumb turner and exploit any gaps |  Don't use deadbolt with thumb turn |
|  Request-to-Exit (REX) sensors  |  Spray gas with Dust Off spray dusters or any liquid through gaps . The door of gas trips the sensor, allowing the door to open.| Use a dual technology REX sensor, which can sense temperature change via infra red sensor and also uses a microwave radar that sense a human shape. |
| Modern door Lever Style Handle |  Hook to pull the lever from under the door |  Use a shroud around the door or require card access to exit the door. |
| Keyed doors  | Stealing keys left around in the open and unguarded key boxes | Don't leave keys unguarded |
|  Telephony Access Control Boxes |  Usee common master keys found on Amazon, Ebay, etc (e.g. 222343 key, A126 linear key, Door King 16120), opening the panel and connecting the switches (e.g. for Door King) | Don't let that be the only control|
|  Electronic badge systems | RFID card cloners  | Use RFID shields to prevent malicious data reads  |

And some pictures of the attack tools (from the talk):

* Thumb Turn Flipper

![Thumb Turn Flipper](https://raw.githubusercontent.com/josz5930/secarticles/master/tutorial/img/physicalpt-9nov2018-1.jpg)

* Under door attack hooks

![Under Door Attacks using a hook](https://raw.githubusercontent.com/josz5930/secarticles/master/tutorial/img/physicalpt-9nov2018-2.jpg)

*  Connecting switches within the telephony access box

![Connect solders of a keyed-alike system](https://raw.githubusercontent.com/josz5930/secarticles/master/tutorial/img/physicalpt-9nov2018-3.jpg)

* Typical master keys

![Typical master keys](https://raw.githubusercontent.com/josz5930/secarticles/master/tutorial/img/physicalpt-9nov2018-4.jpg)

References/ Sources: 

* [I'll Let Myself In: Tactics of Physical Pen Testers, Deviant Ollam at Wild West Hackin' Fest 2017] (https://www.youtube.com/watch?v=rnmcRTnTNC8&feature=youtu.be)
* [Overview Of Physical Penetration Testing, RedTeam Security Consulting](https://www.redteamsecure.com/physical-penetration-testing/)







