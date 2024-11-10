# Simon says, "Set up SAML SSO."

You get a new software platform at your company. Great, another username and password to put in your password manager (you are using a password manager...right?). This isn't a new thing. With technology developing and expanding continuously, businesses across the globe end up with some degree of "tech sprawl". You might have documentation in one platform, CRM in another, some security software, communications platforms, and who knows what else. All of these things do authentication differently. Some support multifactor authentication (MFA), while others do not. Some of them don't offer customizable password policies. Some might not even log/audit logins. With cybersecurity threats on the rise and increasingly complex enterprise environments spanning cloud SaaS applications to hybrid infrastructure, designing and administering user authentication securely and efficiently is more important than ever.
One answer to this problem in modern IT environments is SAML Single Sign-On (SSO). This method of authentication allows users to authenticate using a single account from your identity provider and gain access to multiple services without needing to log in with separate credentials to each one. You can probably see how this would be of benefit already, but let's take a look at how it works, what some of the benefits are, as well as the "SSO tax".

## What is SSO? What is SAML?
There are a variety of single sign-on options, but in this article, we'll talk about Security Assertion Markup Language--or "SAML"--specifically. It is a popular open standard for exchanging authentication and authorization data between two systems: the Identity Provider (also known as the "IdP") and the Service Provider (or "SP). 
When paired with Single Sign-On (SSO), SAML allows users to authenticate once with the Identity Provider and access multiple Service Providers without needing to enter credentials repeatedly for each service.

## How SAML Works
SAML uses XML-based messages (technically called "assertions") to communicate between the IdP and SP. The high-level overview of this process is explained below:
1. User Accesses an Application: The user tries to access a service or application (the SP). If the user isn’t already authenticated, they are redirected to the IdP for login.
2. Redirect to Identity Provider: The SP sends a request to the IdP, typically via a browser redirect. This request includes information like the user’s destination, session information, and a unique identifier.
3. User Authentication at the IdP:  If the user has not yet authenticated, they will be prompted by the IdP (e.g., via a login page). If they have already logged in (e.g., in a prior session), they are typically not prompted again.
4. Generation of SAML Assertion: Upon successful authentication, the IdP generates a SAML assertion, which contains the user’s identity (e.g., username, email, role, permissions, etc.) and a cryptographic signature to ensure integrity and prevent tampering. This assertion is then sent back to the SP.
5. Assertion Validation: The SP receives the SAML assertion, validates its integrity by verifying the signature, and checks if the user is authorized to access the requested resource.
6. Access Granted: If the assertion is valid and the user is authorized, the SP grants access to the requested service. The user can now interact with the service without being prompted to log in again during the current session.

## Benefits of SAML SSO
We alluded to one of the benefits of SAML SSO in the introduction to this article, but there are a variety of reasons you may want to consider configuring SAML SSO where it is available in your environment.

### Improved Security  
There are several ways SAML SSO can improve the security of your systems. First, single sign-on reduces the number of times credentials need to be transmitted between systems, and that is inherently a good thing. Additionally, the fewer passwords a user is required to remember, the less likely they are to do something insecure such as writing it down on a sticky note. Finally, some software and platforms do not support password requirements, multi-factor authentication, or advanced security options such as conditional access policies. By using SAML SSO, you can take advantage of all of these advanced security features if your Identity Provider of choice offers them. This can be a good way to shore up security of your accounts without having to rip out and change entire platforms.

### Simplified User Experience  
There's no doubt about it, SAML SSO reduces friction for users by streamlining access to multiple applications. Only needing to remember a single set of credentials and authenticate once to gain access to various resources makes it easier to stay both secure and productive without dealing with repeated login prompts and credentials for a bunch of different systems.

### Centralized User Management  
For IT admins, SAML SSO provides a centralized place to manage user identities, meaning that user account management, provisioning, deprovisioning, and role-based access control (RBAC), can be handled centrally at the Identity Provider. Changes made at the IdP level (e.g., password resets, group memberships) are automatically propagated to all connected Service Providers without needing to go touch all of those applications and services.

### Reduced Administrative Overhead  
The administrative burden of maintaining users and authentication is significantly reduced by the implementation of SAML SSO. Instead of maintaining separate authentication systems for each service (and who knows how many disparate user accounts), IT teams need only manage the Identity Provider, which consolidates authentication management for all connected applications. This reduces the complexity of password resets, audit trails, and security policies. This can lead to reduced IT support costs as well.

### Compliance and Auditing  
Not every system will natively have login auditing that is usable. While this is a nice-to-have in a lot of situations, it is a mandatory requirement under certain regulatory requirements such as HIPAA, GDPR, and many others. SAML SSO helps organizations comply with regulatory requirements by providing a more structured and auditable approach to user access. The centralized nature of the IdP allows for better monitoring and reporting of user activities, enabling administrators to track logins, access patterns, and more.

### Scalability and Flexibility  
As organizations grow, SAML single sign-on makes it easier to integrate additional services into the environment. Whether adopting new cloud services/SaaS applications, or expanding on-premises infrastructure, Security Assertion Markup Language paired with SSO provides a scalable and flexible approach to adding new service providers with minimal administrative effort, and without increasing the overhead for IT support in the process.

## Best Practices to Consider
As with anything, SAML SSO will only be as good as you make it. To get the most, IT personnel should follow some best practices when implementing this standard:
- Implement multi-factor authentication at the IdP level to add an extra layer of security. In this day and age, this is a critical requirement! MFA can be additionally paired with conditional access policies if your Identity Provider supports them for an added layer of protection.
- Continuously monitor authentication logs and configure alerts for unusual login patterns, such as failed login attempts, which could indicate potential breaches. Your Identity Provider may have options for alerting and reporting on failed or suspicious login attempts as well as account lockouts.
- You have the option to sign assertions during SAML single sign-on. If you Service Providers support it, you should always use HTTPS to encrypt SAML traffic to protect sensitive data in transit.
- To follow the principle of least privilege, be sure to set up roles in your IdP and permissions in your SPs to grant users the permissions they need, and nothing more.

## The SSO Tax
Well, it can't all be good, right? Companies that make software and systems that businesses use have caught on to the fact that SAML single sign-on is a highly desired feature and have configured their pricing accordingly. In recent years, the premium added to the base pricing for many platforms has become so egregious, that sites such as https://ssotax.org/ were born to help IT personnel gain insight into just how much extra cash (er...purchase orders) they will have to shell out to use it. Some software suites like Adobe increase their cost by 10-35%, while others gouge their customers hundreds if not thousands of percents more (looking at you, ClickUp, GitHub, and Cloudflare).

## Conclusion
SAML Single Sign-On (SSO) is a powerful and effective solution for managing authentication in modern IT environments comprised of disparate systems and applications. By centralizing authentication and providing a seamless, secure experience for end-users, enterprises can reduce security risks, simplify user management, and improve productivity. For IT administrators and engineers, adopting SAML SSO is a strategic move toward improving both security and operational efficiency. With the right implementation and best practices, SAML SSO can significantly enhance the overall IT infrastructure and security posture, enabling organizations to scale securely and efficiently.
