#Secrets in URLs

When going on the internet, there are times that sites provide URLs that contain information that should be secrets which grants access to certain restricted information. Such URLs are known as "capability URLs". These URLs are often used so that a "need" to access the resource without authentication or for "low friction" purposes.

The Architectural Recommendations of the W3C Tag "Good Practices for Capability URLs" defines capability URLs as one that grants access to a resource to anyone who has the URL. There are particular application design patterns for which this is useful as they remove the necessity for users to log in to a site and are easily delegated to others. But their use can open up some security issues. URLs are not generally required to be kept secret, and there are various routes through which capability URLs can leak into unintended hands. This document provides some good practices for web developers who wish to incorporate capability URLs into their applications, to minimise these risks."

Password reset links are an obvious example of such URLs. Other less common examples are Sharepoint links with guest access, unlisted Youtube videos, etc.

There are several risks that need to be considered when considering the use of such capability URLs. Some of them are:

1) Someone monitoring traffic on the network and gaining access to the secret information in the URL. For example, a connection via "open" wifi. If the URL is transmitted over a non-encrypted channel (for example, HTTP without TLS/SSL), a passive attacker on the network would be able to gain access to the information. For this reason, all capability links should be transmitted over TLS.

2) An malicious user with access to your computer(even momentarily) can access all capability URLs in the browser history. To mitigate such risks, the capability URLs should be set to expire after a certain amount of time or after a number of uses. For example, the password reset link should only work once.

3) Third-parties may also accidentally gain access from the capability URLs. For example, when there are scripts on the resource page that does a HTTP request to the third party service. In this case, the HTTP referer header may leak the capability URL to the third party service. Pages that use such capability URLs should be screened for calls to external domains. Other places where capability URLs may exist are web server access logs, web statistics reportings, etc.

4) A casual shoulder surfer may memorize the URL when walking pass the user's computer. We can use a long and randomized string for the "secret" portion of the URL to counter such attacks. 

5) The "secret" information is shared among all the authorized persons in the URL. Unlike a password, it is usually difficult to change at an instance. Therefore, consider requiring authentication instead of solely relying on the capability URL for information or functions that needs confidentiality.

6) A malicious user may guess the "secret" information of the URL. In order to hinder such users, long randomized non-consecutive strings should be used for such "secret" information. This makes it difficult for an attacker to use techniques such as enumeration to generate valid URLs from existing capability URLs.

__References:__

* https://w3ctag.github.io/capability-urls/
* https://security.stackexchange.com/questions/33738/are-secret-urls-secure-over-https/33744
* https://security.stackexchange.com/questions/89108/is-a-website-published-in-an-obscure-directory-comparably-secure-to-being-placed
* https://security.stackexchange.com/questions/118975/a-secret-in-a-url
* https://stackoverflow.com/questions/4833314/are-secret-urls-truly-secure
* https://crypto.stackexchange.com/questions/25715/what-is-the-difference-between-online-and-offline-brute-force-attacks