# Thwarting "Spoofy" Business with SPF, DKIM, and DMARC

Most of us have received emails that look like they’re from a trusted source but are actually from cybercriminals. With phishing attempts and cybersecurity incidents being commonplace in the modern work environment, IT teams these days focus heavily on a variety of security measures including user education. Email is a core part of most businesses' communication, and setting up authentication on email messages is a straightforward way to help mitigate the risk of bad actors from sending email message that look like they're from your company when they're really not. This protection takes the form of three different parts: SPF, DKIM, and DMARC.

## Sender Policy Framework (SPF)
Imagine if every time someone received a letter in via the postal service, the back of the envelope said "if the return address on the front isn't my address, don't deliver this letter" and the letter carrier would discard it. In a way, that's what the Sender Policy Framework--or "SPF"--is. SPF is like a list of approved senders for your domain. When the recipient's mail server receives your email, it uses DNS to look up a TXT record for the domain that you sent your email from; this record contains the list of places that are approved to send email for your domain.

As an example, if you have a mail server with a public IP address of 52.96.165.98 (this is just a random Office 365 IP address as an example, but you'd use your public IP address that your mail server sends from) and that mail server sends mail as user@domain.tld, the recipient's mail server will do a DNS lookup for domain.tld and find the TXT record that is the SPF record. They look like this:
```
"v=spf1 ipv4:52.96.165.98 -all"
```
The recipient's mail server sees that domain.tld messages should come strictly from 52.96.165.98, and that the message did indeed come from that IP address, so it will pass the SPF check. If the source of the message is not included in the sender domain's SPF record, then the message will fail the SPF check. This helps unauthorized sources from sending emails that look like they're from you, but actually are not. There are limitations to SPF's efficacy, such as when a message is forwarded (the source IP address of the message may change to an address not in your domain's SPF record), but for this high-level overview we won't go into all of those. In any case, SPF is easy to enable and a worthy protection to put in place for your domain.

## DomainKeys Identified Mail (DKIM)
To add another layer of security, DomainKeys Identified Mail--or "DKIM"--adds a digital signature to your emails, ensuring they haven’t been tampered with during transit. Imagine you and the recipient have a secret way to verify that the contents of an envelope haven’t been tampered with—like placing a distinctive mark on the seal. This is similar to what DKIM does with email."

While not an exact example, this is similar to what DKIM does. Using a cryptographic key pair (public and private), outbound emails are signed, and the recipient's mail servers can check the signature against the DKIM information published in a TXT record for your domain to make sure that the email really did come from where it said it did, and that it was not tampered with in transit.

This is a strong protection for email, but it is limited by the fact that it requires key management, which is not supported by every platform and service provider. Some will fully support it, some will partially support it, and some outright don't support DKIM at all. Key management can become burdensome and is typically the responsibility of the domain's administrator. That said, if you use platforms largely popular with enterprises, there's a good chance that DKIM is supported, and if it is supported, there's a good chance you should configure it.

## Domain-based Message Authentication, Reporting, and Conformance (DMARC)
Finally, there is Domain-based Message Authentication, Reporting, and Conformance--also known as "DMARC". In the analogy, if the return address is wrong and the envelope seal is missing the distinctive mark, the recipient would likely toss it out. This is what DMARC does—providing instructions on how to handle messages that fail the SPF or DKIM checks.

This protective measure acts as a policy/enforcement layer for SPF and DKIM, providing instructions as to how messages not authenticated by SPF or DKIM should be handled. DMARC checks if the incoming email message passes SPM and DKIM checks, then decides whether to accept, quarantine, or reject messages that fail those checks. 

Like SPF and DKIM, this is accomplished using TXT records in your domain's public DNS. Not only does this help prevent spoofing, but it provides visibility as to who is sending on behalf of your domain. Unlike SPF and DKIM, DMARC has those two checks as dependencies, and cannot be used by itself. While it has these requirements, it also relies on simple DNS records, and there are relatively few (if any) valid reasons to disregard setting up DMARC.

As an aside, because this is the policy/enforcement layer and management of larger quantities of domains can become cumbersome, businesses with many domains may benefit from using a third-party DMARC management tool to put all of the policies in a single place for ease of management and visibility. There are a variety of them available, including popular options such as dmarcly and Mimecast DMARC Analyzer.

---

All together SPF, DKIM, and DMARC form an effective email security strategy. SPF dictates who can send mail for your domain, DKIM ensures the integrity of messages supposedly sent from your domain, and DMARC provides policies and enforcement to catch unauthorized emails. Understanding and implementing all three of these methods adds a significant level of protection against bad actors who are getting up to "spoofy" business and trying to send email-based threats your way and is something that you should consider doing if you have not already set it up.
