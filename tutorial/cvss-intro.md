###Determining technical severity of vulnerabilities using CVSS v3

There are many ways different entities and security assessors determine the severity of a vulnerability. One of the ways is the use of the Common Vulnerability Scoring System (CVSS) by FIRST.

The use of CVSS to determine the technical severity has several benefits such as:

* standardization of scores - calculations with the same component ratings will lead to the same score as the algorithm is the same
* Transparency in calculation - with a single line, the scores of each components can be communicated. For example, by sending the vector string "CVSS:3.0/AV:P/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H", we can see quickly that the attack vector has the value of "Physical".

Let us practice calculating the CVSS score for a reported vulnerability, CVE-2018-6867. We shall be using version 3.0.

The vulnerability description is as follows:

>Cross Site Scripting (XSS) exists in PHP Scripts Mall Alibaba Clone Script 1.0.2 via a profile parameter.

Reading the steps written in the proof of concept and understanding the target application/script, we can determine:

* like most Cross Site Scripting attacks, the payload can be delivered over the network (the payload can be sent over a router and routed successfully to the destination site)
* There are no specialized access conditions required to deliver the payload. The attack works repeatedly if an attacker can key in the input into the affected field.
* The attacker requires some access to save the profile
* In order to access the affected component and be affected, some interaction is required from the user.
* Some sensitive information may be changed or read

Using this information, we can calculate a severity rating of 5.4 (regarded as a medium risk). For communication of the information above, we can easily use a single string "AV:N/AC:L/PR:L/UI:R/S:C/C:L/I:L/A:N" to communicate the score of the individual components (as above).

Using CVSS provides an objective technical perspective for vulnerabilities and testers should be familiar with how to calculate it.

References:

* CVE-2018-6867 on NVD - https://nvd.nist.gov/vuln/detail/CVE-2018-6867
* CVSS examples - https://www.first.org/cvss/examples
* CVE-2018-6867 on Exploit DB - https://www.exploit-db.com/exploits/44171/

For further research:

* CVSS v3.0 specification document - https://www.first.org/cvss/cvss-v30-specification-v1.7.pdf
* Microsoft's Security Update Severity Rating System - https://technet.microsoft.com/en-us/security/gg309177.aspx
