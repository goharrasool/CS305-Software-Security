# CS305-Software-Security
**Briefly summarize your client, Artemis Financial, and its software requirements. Who was the client? What issue did the company want you to address?**

Artemis Financial is a financial services company that wanted to upgrade its web application to meet modern software security standards. The company required an enhancement to protect sensitive financial data-in-transit, ensure data integrity across transfers, and audit third-party dependencies for known security vulnerabilities. I was tasked with refactoring their Spring Boot application to enforce HTTPS/TLS encrypted communication, implementing a cryptographic SHA-256 hashing mechanism for payload verification, and integrating automated dependency scanning.

**What did you do well when you found your client’s software security vulnerabilities? Why is it important to code securely? What value does software security add to a company’s overall well-being?**

I excelled at systematically auditing the codebase, identifying weak transmission protocols (unencrypted HTTP), and isolating third-party software dependencies through static analysis. Coding securely is essential because software vulnerabilities can lead to data breaches, unauthorized data tampering, and severe financial or reputational damage. Secure coding adds immense value to a company’s overall well-being by protecting sensitive client assets, ensuring regulatory compliance, and building stakeholder trust.

**Which part of the vulnerability assessment was challenging or helpful to you?**

The most challenging part of the assessment was managing external dependency syncs and API rate limits during OWASP static scans (such as handling NVD API 403 blocks in cloud environments). The most helpful aspect was learning how static analysis tools continuously flag known vulnerabilities across nested third-party libraries (pom.xml), allowing developers to proactively remediate risks before deployment.

**How did you increase layers of security? In the future, what would you use to assess vulnerabilities and decide which mitigation techniques to use?**

I implemented defense-in-depth by adding multiple security layers:   
**Transport Security:** Enabled HTTPS/TLS on port 8443 using a 2048-bit RSA PKCS12 keystore (ssl-server.p12).   
**Data Integrity:** Refactored the application using Java’s java.security.MessageDigest to generate SHA-256 cryptographic checksums.   
**Dependency Auditing:** Integrated the dependency-check-maven plugin into the build lifecycle.   
In the future, I will use tools like OWASP Dependency-Check, Snyk, and SonarQube to assess vulnerabilities and rely on CVSS (Common Vulnerability Scoring System) severity scores to prioritize mitigation efforts.

**How did you make certain the code and software application were functional and secure? After refactoring the code, how did you check to see whether you introduced new vulnerabilities?**

To verify that the code was both functional and secure, I performed functional testing by running the application (mvn spring-boot:run) and verifying the endpoints in the browser. I confirmed that navigating to https://localhost:8443/hash successfully established an encrypted TLS connection and rendered the expected data payload alongside its valid SHA-256 checksum. To ensure no new vulnerabilities were introduced during refactoring, I re-executed Maven static analysis scans to confirm zero detected vulnerabilities (BUILD SUCCESS).

**What resources, tools, or coding practices did you use that might be helpful in future assignments or tasks?**

Key tools and practices used in this project include:
**Java Cryptography Architecture (MessageDigest):** Generating cryptographic hash digests.   
**Java Keytool:** Generating PKCS12 keystores and RSA key pairs (keytool).   
**OWASP Dependency-Check Maven Plugin:** Auditing open-source library dependencies.   
**GitHub Codespaces & Embedded Tomcat:** Configuring SSL/TLS properties in application.properties.   
These tools and DevSecOps practices will be invaluable for future software engineering tasks requiring secure API development, data protection, and continuous vulnerability management.   

**Employers sometimes ask for examples of work that you have successfully completed to show your skills, knowledge, and experience. What might you show future employers from this assignment?**

From this assignment, I can showcase:
A fully refactored, functional Java Spring Boot application configured for HTTPS/TLS.   
Clean implementation of SHA-256 cryptographic checksum generation.   
An OWASP Dependency-Check HTML vulnerability audit report demonstrating zero high-risk dependency vulnerabilities.   
A comprehensive Practices for Secure Software Report documenting cryptographic choices, SSL configurations, and security best practices.
