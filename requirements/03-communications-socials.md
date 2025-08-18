# Domain 3: Communications & Social Media

## Risks

- R-CS-001: Account Takeover and Impersonation Attacks
- R-CS-002: Social Engineering Targeting Team Members
- R-CS-003: Community Scams and Phishing Campaigns
- R-CS-004: Information Disclosure Through Insecure Communications
- R-CS-005: Coordinated Attacks on Multiple Platforms
- R-CS-006: Platform-Specific Vulnerabilities

### **Account Security**

**SP-CS-001: Multi-Factor Authentication for All Accounts**
- All organizational communication accounts must implement multi-factor authentication
- SMS-based authentication must not be used as a primary or backup factor
- Hardware security keys should be used where supported by platforms

**SP-CS-002: Account Recovery Protection**
- Account recovery options can be used, but SMS recovery should not be enabled
- Recovery email addresses must be dedicated organizational accounts with strong security and 2FA

### **Secure Communications**

**SP-CS-003: End-to-End Encrypted Channels**
- Encrypted communication should be used for confidential communications and coordination of admin operations
- Signal or equivalent end-to-end encrypted messaging platforms can be used

**SP-CS-004: Email Authentication**
- SPF, DKIM, and DMARC email domain records must be properly configured and enabled
- Email filtering should be enabled to block known malicious content and spam
- All internal emails should be encrypted and signed with an authentic PGP key, with the public keys shared via a trusted channel

**SP-CS-005: External Party Verification**
- Interactions with new external identities and communication channels must have their authenticity confirmed with that party via a secure channel (existing authenticated channels, video chats, social consensus, in person discussion)
- Communication channels with trusted external parties must have strong authentication requirements (signed and encrypted emails, encrypted Signal chats, secure Slack chats, etc.)

**SP-CS-006: Secure File Sharing and Viewing**
- Files received from external parties must never be directly opened, they must be sanitized with an approved software or service (e.g. [Dangerzone](https://dangerzone.rocks/), [VirusTotal](https://www.virustotal.com/gui/home/upload), or [Google Drive](https://support.google.com/drive/answer/141702))
- Internally shared files must be distributed via secure file sharing platforms, never via email or chat

**SP-CS-007: Critical Operations Confirmations**
- Internal operations coordination must be confirmed in a secure channel (camera-on video calls, end-to-end encrypted chats, in person)
- Redundant channels for confirmation of operational details are recommended
