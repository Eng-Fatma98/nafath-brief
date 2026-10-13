Version: NAFATH-V4

Track: Networking

## Overview

A national service provider faces complex security risks across its entire digital supply chain. Securing this environment requires an integrated approach across software, artificial intelligence, mobile applications, networking, cybersecurity, and data management. In software, configurations must be separated from source code to prevent sensitive secrets from leaking. AI systems require defenses against adversarial attacks such as evasion and data poisoning to maintain model integrity. Mobile applications must follow security standards like OWASP MASVS to ensure client-side safety. System-level vulnerabilities like Log4Shell demonstrate the constant need for rapid patch management in cybersecurity. Data integrity relies on maintaining a Software Bill of Materials (SBOM) to track components. Finally, at the network layer, routing protocols must be secured with RPKI to prevent BGP route hijacking.

## Software
According to the Twelve-Factor App methodology, configuration that varies between deployments should be stored in environment variables rather than hardcoded in the codebase. This separation ensures that sensitive secrets, database credentials, and API keys are never accidentally exposed in version control systems, thereby protecting the software supply chain from credential leaks and unauthorized access.

Resource: The Twelve-Factor App - https://12factor.net/

## AI
Adversarial machine learning attacks primarily include evasion attacks, where input data is subtly modified at test time to fool the model into making incorrect predictions, and poisoning attacks, where malicious data is injected into the training set to compromise the model's underlying behavior. These differ in their objective and timing, as poisoning targets the training phase while evasion targets the operational inference phase.

Resource: NIST Artificial Intelligence Risk Management Framework - https://www.nist.gov/itl/ai-risk-management-framework

## Mobile
The OWASP Mobile Application Security Verification Standard (MASVS) is a comprehensive security standard for mobile app development that defines security requirements for both Android and iOS architectures. It is used by security teams and developers to verify the security posture of a mobile app, ensure proper cryptographic storage, secure network communication, and protect against reverse engineering.

Resource: OWASP Mobile Application Security - https://owasp.org/www-project-mobile-security/

## Networking
At the network layer, securing BGP (Border Gateway Protocol) routing infrastructure is critical to prevent malicious route hijacking and interception. Implementing Resource Public Key Infrastructure (RPKI) with Route Origin Authorizations (ROAs) enables routers cryptographically to validate the origin autonomy of Autonomous System (AS) announcements, ensuring robust path verification across service provider networks.

Resource: Cloudflare RPKI Documentation - https://www.cloudflare.com/learning/ssl/what-is-rpki/

## Cybersecurity
Modern enterprise architectures must maintain rigorous patch management protocols to mitigate zero-day vulnerabilities such as Log4Shell (CVE-2021-44228). Automated dependency scanning and continuous runtime application self-protection (RASP) mechanisms help security operations teams identify unpatched libraries and block exploitation vectors before perimeter breaches occur.

Resource: National Vulnerability Database (NVD) - https://nvd.nist.gov/vuln/detail/CVE-2021-44228

## Data
Ensuring software supply chain integrity requires maintaining an accurate Software Bill of Materials (SBOM) for every application release. An SBOM acts as a comprehensive inventory of all third-party libraries, open-source components, and dependencies, enabling organizations rapidly to assess impact when new vulnerabilities are disclosed.

Resource: CISA Software Bill of Materials - https://www.cisa.gov/sbom

## Misconception in My Track
A common misconception regarding BGP security is believing that deploying RPKI completely prevents all types of internet traffic hijacking and spoofing. While RPKI with Route Origin Authorizations (ROAs) effectively stops Route Origin Hijacking by validating the origin Autonomous System (AS), it does not protect against path manipulation or AS-path shortening attacks where a malicious actor alters intermediate hops in the AS path. The section "What RPKI does not do" in Cloudflare's documentation confirms that RPKI only validates the origin AS, not the full AS path.

## Open Question
How effectively can autonomous systems combine RPKI with Autonomous System Provider Authorization (ASPA) mechanisms to validate both origin and full path routing integrity in real-time enterprise operations?
