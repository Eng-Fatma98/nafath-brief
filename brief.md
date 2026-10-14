Version: NAFATH-V4

Track: Networking

 Overview

As a national service provider operating critical infrastructure reliant on global and regional software supply chains, including software developments and components in China, ensuring robust security across six core domains is essential. In software engineering, sensitive system secrets are kept separate from the source code using environment variables. Artificial intelligence platforms require continuous defenses against data poisoning and evasion attacks to maintain model integrity. Customer-facing mobile applications follow rigorous standards like OWASP MASVS to ensure client-side safety. Cybersecurity operations rapidly resolve system-level vulnerabilities such as Log4Shell. Data management relies on maintaining a Software Bill of Materials (SBOM) for complete supply chain transparency. Finally, at the network layer, routing protocols are secured with RPKI to prevent BGP route hijacking.

 Software
According to the Twelve-Factor App methodology, configuration that varies between deployments should be stored in environment variables rather than hardcoded in the codebase. This separation ensures that sensitive secrets, database credentials, and API keys are never accidentally exposed in version control systems, thereby protecting the software supply chain from credential leaks and unauthorized access.

Resource: The Twelve-Factor App - https://12factor.net/

 AI
Adversarial machine learning attacks primarily include evasion attacks, where input data is subtly modified at test time to fool the model into making incorrect predictions, and poisoning attacks, where malicious data is injected into the training set to compromise the model's underlying behavior. These differ in their objective and timing, as poisoning targets the training phase while evasion targets the operational inference phase.

Resource: NIST Artificial Intelligence Risk Management Framework - https://www.nist.gov/itl/ai-risk-management-framework

Mobile
The OWASP Mobile Application Security Verification Standard (MASVS) is a comprehensive security standard for mobile app development that defines security requirements for both Android and iOS architectures. It is used by security teams and developers to verify the security posture of a mobile app, ensure proper cryptographic storage, secure network communication, and protect against reverse engineering.

Resource: OWASP Mobile Application Security - https://owasp.org/www-project-mobile-security/

Networking
At the network layer, securing BGP (Border Gateway Protocol) routing infrastructure is critical to prevent malicious route hijacking and interception. Implementing Resource Public Key Infrastructure (RPKI) with Route Origin Authorizations (ROAs) enables routers cryptographically to validate the origin autonomy of Autonomous System (AS) announcements, ensuring robust path verification across service provider networks.

Resource: Cloudflare RPKI Documentation - https://www.cloudflare.com/learning/ssl/what-is-rpki/

Cybersecurity

Log4Shell (CVE-2021-4428) was a critical Remote Code Execution (RCE) vulnerability in the Apache Log4j2 library. It allowed unauthenticated remote attackers to execute arbitrary code by supplying a specially crafted string that triggered a JNDI lookup to a malicious LDAP server. The vulnerability was rated with maximum severity (CVSS 10.0) due to its widespread presence and ease of exploitation. It was fixed by updating Log4j to version 2.15.0 or later, which disabled JNDI lookups by default.

Resource: CISA Alert AA21-351A - Mitigating Log4Shell - https://www.cisa.gov/news-events/alerts/2021/12/17/cisa-releases-guidance-mitigating-apache-log4j-vulnerability-log4shell

Data

A Software Bill of Materials (SBOM) is a formal nested inventory of software components and dependency relationships. According to the NTIA guidelines, an SBOM must contain seven minimum baseline data fields: Supplier Name, Component Name, Version of the Component, Other Unique Identifiers, Dependency Relationship, Author of SBOM Data, and Timestamp. These details enable organizations to track dependencies and quickly identify vulnerable software components across the supply chain.

Resource: NTIA Minimum Elements For a Software Bill of Materials (SBOM) - https://www.ntia.doc.gov/files/ntia/publications/ntia_minimum_element_list_.pdf


 Misconception in My Track
 
A common misconception regarding BGP security is believing that deploying RPKI completely prevents all types of internet traffic hijacking and spoofing. While RPKI with Route Origin Authorizations (ROAs) effectively stops Route Origin Hijacking by validating the origin Autonomous System (AS), it does not protect against path manipulation or AS-path shortening attacks where a malicious actor alters intermediate hops in the AS path. The section "What RPKI does not do" in Cloudflare's documentation confirms that RPKI only validates the origin AS, not the full AS path.

Open Question

How effectively can autonomous systems combine RPKI with Autonomous System Provider Authorization (ASPA) mechanisms to validate both origin and full path routing integrity in real-time enterprise operations?
