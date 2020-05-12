# Vanquishing Vishing - the power of three
Phishing via phone calls, or "Vishing" is one of the avenues of social engineering that sails past corporate firewalls, airgaps and email monitoring solutions.  I will be sharing a summary of three different attempts in research to solve this issue by preventing the call from ever happening.

### Definition
Wikipedia gives a good introduction of phishing via phone[\[1\]](https://en.wikipedia.org/w/index.php?title=Voice_phishing&oldid=928368353) :
>Voice phishing is a form of criminal phone fraud, using social engineering over the telephone system to gain access to private personal and financial information for the purpose of financial reward. It is sometimes referred to as 'vishing'- a portmanteau of "voice" and phishing. Landline telephone services have traditionally been trustworthy; terminated in physical locations known to the telephone company, and associated with a bill-payer. Now however, vishing fraudsters often use modern Voice over IP (VoIP) features such as caller ID spoofing and automated systems (IVR) to make it difficult for legal authorities to monitor, trace or block. Voice phishing is typically used to steal credit card numbers or other information used in identity theft schemes from individuals.

### Attack Scenario

In order to gain information via social engineering, the following are an example of some steps that lead to the social engineering attack happening:

1. The attacker performs a call to the victim - which can be done via a physical phone, an automated dialer or a communications platform such as Twilio.
2. The victim answers the phone.
3. If an automated system is used, the victim may be instructed to call back to a certain number. Alternatively, the victim may be instructed to call back the bank at the legitimate number, but the attacker holds the phone line "open" after the person puts down the phone (a.k.a. the "[no hang up scam](https://www.saga.co.uk/magazine/money/spending/consumer-rights/avoid-getting-caught-by-a-phone-scam)").

By impersonating a trusted entity (e.g. your bank, the police), the attacker will attempt to get the victim to disclose sensitive information or perform an action (e.g. transfer money, do a password reset).

### Stopping the chain

I read/watched three different articles/webcasts that propose methods to prevent some of the attacks from happening. This is done by making sure the victim does not pick up the call. They are:

1. Fighting Voice Spam with a Virtual Assistant , Georgia Tech Institute for Information Security & Privacy Cybersecurity Lecture Series [\[2\]](https://smartech.gatech.edu/bitstream/handle/1853/62473/pandit.mp4?sequence=1&isAllowed=y)
2. CEIVE: Combating Caller ID Spoofing on 4G Mobile Phones Via Callee-Only Inference and Verification, Chunyi Peng of Purdue University[\[3\]](https://www.cs.purdue.edu/homes/chunyi/pubs/mobicom18-deng.pdf)
3. Detection of a spear-phishing phone call, US Patent US10244109B2 of International Business Machines Corp [\[4\]](https://patentimages.storage.googleapis.com/32/8b/d7/446e90b18d8de2/US10244109.pdf)

In the first proposal, an application called RobocallGuard is proposed. This method is built on the basis on the caller knowing the person being called. Practically, this will be paired with a whitelist of "good numbers" and a blacklist of "bad numbers". When the call connects and the number if not in either whitelist or blacklist, the application on the smart phone challenges callers to provide the name of the person they are calling.  Using the [Snowboy](http://docs.kitt.ai/snowboy/) engine, the application detects to see if the keyword of the owner's name is said. I am particularly pleased that this prevents AI enhanced robocalls and some opportunistic calls, as the attacker will not know the name of the callee. This method is also indifferent to the use of caller ID spoofing and works equally well. I also like that the engine requires little training due to the limited number of words that needs to be matched against.

In the second proposal, an application named CEIVE is proposed. The aim of the countermeasure is to prevent caller ID spoofing; a phishing call from a legitimate or unlisted number is not prevented. This method is built on the calling state of the phone line that is purported to be making the call. The use of inference engine in this control measure was necessary due to differences in caller setup signalling; the authors write of how  "the sequence of call setup signaling messages varies with carriers, call technologies, call settings, and even seemingly-random factors (controlled by network operations)." By observing the SIP response codes for different carriers and learning them in the initial training phase and refining it in an optional retraining of the decision trees, the proof of concept Android application was able to identify most spoofed calls. A notable exception occurs when the adversary attempts to cause the spoofed number to be busy as well. Such an exception is not unthinkable - many Facebook/TikTok clips show how an adversary calls the person being spoofed  (victim 2) so that the person will switch off his/her phone. Nevertheless, this method has some benefit to prevent call spoofing and presents no additional wait time to legitimate callers (unlike proposal one).

In the third proposal, the patent describes a procedure to calculate a score using several identifiable traits before and during a conversation.  The traits include reputation of the phone number on caller id,  caller id characteristics, known voiceprint (e.g. voiceprint often associated with spear phishing), known sequence of words (i.e. words often used in spear-phishing attempts), unusual computing activity on the receiving phone, etc. I look forward to an actual implementation or proof of concept from IBM that implements this fully. For example, how does such a system detect unusual computing activity while protecting its own subsystems from compromise?

### Conclusion
By reducing the number of such calls, it raises the cost  of an adversary ( in terms of effort, money and time) seeking to perform an information gathering attempt via vishing from a large group of individuals in a corporation.  The above summary gives a good primer on the different defenses proposed to secure the human from vishing.

