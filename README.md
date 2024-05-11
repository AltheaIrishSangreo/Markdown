# Ethical Hacking Technical Report

**Client:** Yahoo  
**Date:**  
**Prepared by:** Althea Irish Sangreo and John Llenard Nagal

**Executive Summary:**
This report details the findings of a simulated ethical hacking engagement for Yahoo, focusing on potential security vulnerabilities within their systems and infrastructure. The methodology employed a combination of automated vulnerability scanning tools and manual penetration testing techniques, aiming to identify weaknesses that could be exploited by malicious actors. It's important to note that this is a hypothetical scenario and does not reflect the actual state of Yahoo's security.

**Vulnerability Summary:**
1. **Insecure Direct Object References (IDOR):**
   - **Critical:** An attacker could exploit an IDOR vulnerability in a user profile URL to access another user's highly sensitive information, such as financial data or email history.
   - **High:** An attacker could manipulate a product ID in the Yahoo Shopping cart to view or modify the order details of another user's cart.
2. **Session Management Vulnerabilities:**
   - **Critical:** A vulnerability in Yahoo Mail's session management could allow an attacker to steal a user's session cookie and gain complete access to their email account, including contacts and sent/received messages.
   - **High:** Lack of session timeout functionality in Yahoo Finance could allow an attacker to access a user's account even after a long period of inactivity, enabling unauthorized transactions.
3. **API Security Issues:**
   - **Critical:** An unauthenticated API endpoint in Yahoo Fantasy Sports could allow attackers to manipulate player statistics or league settings, potentially impacting gameplay integrity.
   - **High:** Predictable API keys used for third-party developer access to Yahoo News could be vulnerable to brute-force attacks, allowing unauthorized access to news content.
4. **Cross-Site Scripting (XSS) Persistent Vulnerabilities:**
   - **Critical:** A persistent XSS vulnerability stored on Yahoo Answers could allow attackers to inject malicious scripts into all user responses, potentially stealing user cookies or redirecting users to phishing websites on a large scale.
   - **High:** A reflected XSS vulnerability in the Yahoo Search bar could allow attackers to inject malicious scripts that target specific users performing certain searches, potentially stealing their login credentials.
5. **Insufficient Password Hashing:**
   - **Critical:** Passwords stored using a weak hashing algorithm (e.g., MD5) could be cracked by attackers, allowing unauthorized access to Yahoo accounts.
   - **High:** Passwords stored only as a hash without a salt could be vulnerable to pre-computed rainbow tables, enabling attackers to gain access with minimal effort.
6. **Outmoded Software on Legacy Systems:**
   - **Critical:** A critical vulnerability exists in an outdated operating system running on a legacy system supporting Yahoo Mail, potentially allowing attackers to compromise the entire email service.
   - **High:** Legacy application software used for Yahoo Finance is known to have unpatched vulnerabilities, increasing the attack surface for unauthorized access.
7. **Insider Threat Potential:**
   - **Critical:** A disgruntled employee with high-level access privileges could steal sensitive user data from Yahoo Answers or disrupt critical functionalities.
   - **High:** Weak access controls in Yahoo Messenger allow employees to access user data beyond their job requirements, increasing the risk of accidental data leaks.
8. **Denial-of-Service (DoS) Vulnerabilities in Core Services:**
   - **Critical:** A critical vulnerability in a core service like Yahoo Search could be exploited to launch a large-scale DoS attack, overwhelming the service and preventing users from accessing search results.
   - **High:** A simple DoS attack by flooding Yahoo Mail servers with login requests could render the service unavailable to legitimate users.
9. **Mobile App Security Weaknesses:**
   - **Critical:** An insecure storage mechanism in the Yahoo Finance mobile app could allow attackers to access sensitive user data (e.g., financial information) stored on the device.
   - **High:** The Yahoo Sports mobile app transmits data without encryption, making it vulnerable to interception by attackers on unsecured Wi-Fi networks.
10. **Third-Party Integration Vulnerabilities:**
    - **Critical:** A critical vulnerability exists in a third-party library integrated into Yahoo News, potentially allowing attackers to gain access to the main application or manipulate news content.
    - **High:** Outdated third-party plugins used on Yahoo Weather are known to have unpatched vulnerabilities, creating an additional attack vector for malicious actors.

**Recommendations:**
1. **Insecure Direct Object References (IDOR):**
   - Implement robust access control mechanisms that validate user permissions before granting access to user data. This could involve utilizing role-based access control (RBAC) or attribute-based access control (ABAC).
   - Sanitize all user inputs within URLs to prevent manipulation of object identifiers.
   - Implement additional authentication steps for accessing sensitive data within shopping carts, such as two-factor authentication (2FA).
   - Consider masking or anonymizing certain user data within shopping carts by default, revealing only essential details.
2. **Session Management Vulnerabilities:**
   - Implement secure session management practices, including using strong session IDs, enforcing HTTPS for all logins and data transfers, and setting appropriate session timeouts to automatically log out inactive users.
   - Consider utilizing secure cookies with the HttpOnly flag to prevent client-side scripting access.
   - Implement session timeouts for Yahoo Finance that automatically log out inactive users after a set period.
   - Educate users on the importance of logging out of their accounts after use to minimize the risk of unauthorized access.
3. **API Security Issues:**
   - Implement proper authentication and authorization mechanisms for all API endpoints. This may involve API keys, tokens, or OAuth for secure access control.
   - Regularly review and update API access permissions to ensure only authorized applications and users have access.
   - Utilize strong and unpredictable API keys for third-party developer access. Consider rotating API keys regularly for added security.
   - Implement rate limiting on API endpoints to prevent brute-force attacks against API keys.
4. **Cross-Site Scripting (XSS) Persistent Vulnerabilities:**
   - Implement rigorous input validation and sanitization on all user inputs within Yahoo Answers to prevent the injection of malicious scripts.
   - Consider deploying web application firewalls (WAFs) to detect and block XSS attacks in real-time.
   - Implement input validation and sanitization on search queries within Yahoo Search to prevent XSS attacks.
   - Regularly update and patch web application software to address known XSS vulnerabilities.
5. **Insufficient Password Hashing:**
   - Immediately migrate to a robust password hashing algorithm, such as bcrypt or Argon2, to securely store user passwords.
   - Re-hash all existing user passwords using the new hashing algorithm.
   - Implement password salting to prevent the use of rainbow tables for cracking passwords. Enforce strong password policies with minimum length and complexity requirements.
   - Consider offering multi-factor authentication (2FA) as an additional layer of security for user accounts.
6. **Outmoded Software on Legacy Systems:**
   - Develop a clear plan to upgrade or migrate away from outdated operating systems supporting critical services like Yahoo Mail.
   - Prioritize patching all known vulnerabilities in the legacy application software used for Yahoo Finance.
   - Implement a vulnerability management program to identify and patch vulnerabilities in legacy systems promptly.
   - Consider virtual patching solutions as a temporary measure to mitigate vulnerabilities in legacy software.
7. **Insider Threat Potential:**
   - Implement the principle of least privilege (POLP) for access control, granting employees only the minimum access permissions required for their job roles.
   - Conduct regular security awareness training for employees to educate them on social engineering tactics and best practices for data handling.
   - Implement data access logging and monitoring to track user activity and identify suspicious access patterns.
   - Regularly review user access permissions to ensure they remain aligned with current job roles.
8. **Denial-of-Service (DoS) Vulnerabilities in Core Services:**
   - Implement DoS mitigation strategies for core services like Yahoo Search, such as rate limiting, traffic filtering, and DDoS protection solutions.
   - Conduct DoS attack simulations to identify and address potential weaknesses in service infrastructure.
   - Implement rate limiting on login attempts to Yahoo Mail to prevent DoS attacks by flooding the service with login requests.
   - Utilize cloud-based infrastructure providers with built-in DDoS protection capabilities.
9. **Mobile App Security Weaknesses:**
   - Implement secure data storage mechanisms within the Yahoo Finance mobile app, such as encryption at rest and in transit.
   - Utilize secure communication protocols like HTTPS for all data transmissions within the mobile app.
   - Implement data encryption within the Yahoo Sports mobile app to protect sensitive user information while in transit over unsecured Wi-Fi networks.
   - Regularly update the Yahoo Sports mobile app to address any security vulnerabilities.
10. **Third-Party Integration Vulnerabilities:**
    - Conduct thorough security assessments of third-party libraries before integrating them into Yahoo News. Regularly update these libraries to address any identified vulnerabilities.
    - Utilize secure communication protocols like HTTPS for all data transmissions within the mobile app.
    - Consider alternative libraries with a strong security track record if critical vulnerabilities are found in currently used libraries.
    - Update all third-party plugins used on Yahoo Weather to the latest versions to address known vulnerabilities.
    - Monitor security advisories from third-party vendors and prioritize patching vulnerabilities within integrated components.


## Conclusion:
The comprehensive assessment of Yahoo's systems and infrastructure has uncovered numerous critical vulnerabilities and security flaws across various domains, including web applications, session management, API security, and mobile app security. Addressing these vulnerabilities is imperative to safeguarding user data and ensuring the integrity of Yahoo's services. By diligently implementing the recommended remediation measures, Yahoo can bolster its security posture, mitigate the risk of cyber threats, and enhance user trust in its platforms.


**Signature:** ![signature](signature.png)
