# Domain 5: General Security

## Risks

- R-GS-001: Delayed Incident Detection
- R-GS-002: Inadequate Response Procedures
- R-GS-003: Lack of Monitoring Responsibility
- R-GS-004: Tampering of Monitoring Mechanisms
- R-GS-005: Communication Failures During Incidents
- R-GS-006: Insufficient Backup and Recovery Capabilities
- R-GS-007: Social Engineering Attacks
- R-GS-008: Recruitment and Contractor Compromise  
- R-GS-009: Spear Phishing and Email Spoofing
- R-GS-010: Communication Platform Manipulation
- R-GS-011: Weak Passwords
- R-GS-012: Account Takeover Via Credential Leakage
- R-GS-013: Compromise of Phone Number by SIM Swapping
- R-GS-014: Lost Account Access
- R-GS-015: Overly Broad Access
- R-GS-016: SSO Single Point of Failure
- R-GS-017: Malicious or Compromised Insiders


### **Incident Response Planning**

**SP-GS-001: Comprehensive Incident Response Runbook**
- Organizations must maintain documented incident response plans for all critical systems
- Response procedures must define roles, responsibilities, and escalation paths
- Response procedures should be as prescriptive as possible such that anyone on the team could perform the required actions with no assistance required

**SP-GS-002: Web3-Specific Response Procedures**
- Incident response plans must include multi-sig wallet compromise scenarios
- Smart contract circuit breakers should be set up to automatically halt ongoing attacks as they occur

**SP-GS-003: Incident Response Controls**
- Incident response runbooks must include pre-configured response tactics including:
	- Rapid code deployment rollbacks
    - Accounts access ripcord (immediate revocation of all access of an organization member)
    - Redundant database backups with tested restore procedures (multiple storage media are recommended)
    - Multiple availability zones and fallback regions
    - Multi-sig wallet freezes
- Managed EDR (Endpoint Detection and Response) should be in place to allow rapid response to device compromise

**SP-GS-004: Immutable Incident Monitoring and Alerting**
- Immutable logs of sensitive actions must be in place
- Logs and alerting channels must be configured such that it is either impossible to disable or edit them, or that any such action would trigger an insuppressible alert (via a separate alerting mechanism) indicating that the logs have been altered
- Signed Git commits must be required (to enforce non-repudiation of code changes)
- Alerts should be delivered via multiple redundant channels (e.g. Telegram channel, Discord bot, email)

### **Security Training & Ownership**

**SP-GS-005: Phishing Simulation and Testing**
- Organizations must conduct regular phishing simulation exercises
- Simulations must include Web3-specific phishing scenarios
- Additional training must be provided to personnel who fail simulations

**SP-GS-006: Social Engineering Prevention**
- Organizations must provide social engineering awareness training
- Personnel should be trained to recognize common social engineering tactics
- Reporting mechanisms should be available for suspicious contact attempts

**SP-GS-007: Security Ownership**
- Organizations should designate one or more members of the team to be the security champion of the organization
- The security champion should have the additional duties of tracking security posture, pushing for necessary security improvements, and interfacing with security partners

### **Security Policy**

**SP-GS-008: Password Management**
- Passwords and secrets should be:
    - Not reused
    - 20-32 characters
    - Automatically generated with the full character set (letters, numbers, and symbols)
- A password manager must be used (1Pass or Bitwarden recommended)
- Password manager master passwords should be complex, and at least 20 characters with a mix of phonetic phrases, numbers, and special characters
    - [https://xkcd.com/936/](https://xkcd.com/936/)
- Organization password manager accounts should be separate from personal password manager accounts

**SP-GS-009: Account Sharing**
- Account delegation must be used where possible, rather than credential sharing
- Secrets must be shared with the minimum set of people necessary
- For shared accounts where delegation is not possible, temporary credentials should be provisioned as needed, rather than long-lived ones (or credentials should be rotated after each use)
- Account credentials must not be shared, in order to enforce non-repudiation of actions taken

**SP-GS-009: Principle of Least Privilege**
- Admin privileges must only be granted to the minimum necessary roles
- Dedicated accounts must be used for admin activities, separate from the general accounts of admin users
- Permission changes and admin account usage should be logged and actively monitored

**SP-GS-011: Login Methods**
- SSO (Single Sign-On - e.g. Log in with Google/Github/Apple) can be used for non-sensitive accounts, but must not be enabled for highly sensitive access (financial, administrative, deployments, infrastructure, etc.)
- 2FA must be enforced on all accounts
    - FIDO security keys are recommended, but mobile authenticator apps acceptable
    - SMS-based 2FA must never be used unless no other option is available
    - 2FA seeds should not be stored in password managers
- Passkeys are recommended as a primary login method when available

**SP-GS-012: Superadmin Break Glass Accounts**
- Owner/superadmin privileges for all services must be limited to a single account
- Owner/superadmin should also have a separate individual account if necessary to take non-admin actions
- These accounts must be treated as break glass accounts and their usage should trigger an alert to the entire team

**SP-GS-013: SIM Swap Mitigation**
- All members must set a SIM PIN to mitigate physical theft of SIM cards
- All members should add additional number transfer security requirements through their phone provider:
	- **AT&T** - Go to your myAT&T Profile and log in > My Linked Accounts > Manage extra security for your account > turn on Extra security
	- **T-Mobile** - Add account [Takeover Protection](https://www.t-mobile.com/support/plans-features/account-takeover-protection) to your account
	- **Verizon** - Enable [Number Lock](https://myvpostpay.verizon.com/ui/acct/secure/profile/security/portsecurity). This can be done by phone, through the app, or on [their website](https://myvpostpay.verizon.com/ui/acct/secure/profile/security/portsecurity)
	- **Google Fi** - Enable [Number Lock](https://support.google.com/fi/answer/15147412?hl=en#zippy=%2Cturn-on-number-lock)
- All members must register a Signal account for their phone number (even if not using Signal), to prevent account impersonation via SIM swap attacks

### **Insider Threat Resistance**

**SP-GS-014: Malicious Insider Threat Modeling**
- Insider threat modeling should be performed on each permission level within the org (admin, developer, SRE, DBA, member, etc.)
	- For each permission level, determine the highest amount of damage that an attacker with that access could cause
	- For the highest levels of damage that the business could not recover from, put in place security controls that mitigate or prevent that damage, including:
		- Two-party approvals of sensitive actions
		- Automated time-locks using system accounts and scripts for admin actions
		- Segmentation of assets (e.g. on-chain assets distributed amongst multiple wallets, different deployers for front-end and back-end)

**SP-GS-015: Insider Access Minimization**
- Permissions of each organization member on all services and accounts must be reviewed and reduced to the absolute minimum required to perform their role
- Issuing short-lived credentials at the time of use rather than permanent accounts is recommended
- Elevated privileges (like deploy keys or admin actions) must be designated only to break-glass accounts
	- Break-glass accounts differ from typical accounts in that they are heavily monitored (alerts on any actions taken), and their credentials are designed for one-time use
	- These account credentials can be held by admins in a secure vault, or you can use [Shamir’s Secret Sharing](https://en.wikipedia.org/wiki/Shamir%27s_secret_sharing) to create a quorum necessary to reconstruct the credentials for additional security
	- Break-glass accounts and credentials should be deleted after use and recreated to be ready for future events

### **Social Engineering Defense**

**SP-GS-016: Safe Technical Assessments**
- Provide isolated environments for all technical tests and code challenges
- Never let candidates download or run code on their personal devices
- Use secure platforms for all technical assessments
- Train your hiring team to spot and report suspicious behavior during assessments

**SP-GS-017: Employee Training Against Scams**
- Train employees to recognize fake job offers targeting Web3 workers
- Teach team members to verify and report suspicious recruitment attempts
- Never let employees share passwords or wallet info with external recruiters
- Create easy ways for employees to report recruitment scams

**SP-GS-018: Communication Security**
- Train employees to verify who they're talking to before switching platforms
- Don't let employees click links in messages from unknown people
- Teach team about scams that move from LinkedIn/Twitter to Telegram
- Use only official company email for professional communications

**SP-GS-019: Email Protection**
- Set up email authentication to prevent domain spoofing
- Run regular phishing tests using Web3-specific scenarios
- Train employees never to share credentials via email
- Have employees verify unusual requests through other channels
- Use email security tools to scan for malicious links and attachments

**SP-GS-020: Response to Social Engineering**
- Have a plan to quickly isolate devices that might be infected
- Make it easy for employees to report social engineering attempts
- Share attack methods with the Web3 security community
- Review access immediately for any targeted employee
- Monitor systems used by potentially compromised team members

## Social Engineering Prevention Checklist

### **Technical Assessment Security**
- [ ] Isolated environments set up for all technical tests
- [ ] Policy: no personal device usage for candidate evaluations
- [ ] Hiring team trained to spot suspicious behavior during assessments
- [ ] Secure platforms used for all technical assessments

### **Employee Protection**
- [ ] Team trained to recognize fake Web3 job scams
- [ ] Easy reporting system for suspicious recruitment attempts
- [ ] Policy: no sharing passwords or wallet info with recruiters
- [ ] Training on platform switching scams (LinkedIn→Telegram)
- [ ] Official company email required for professional communications

### **Email and Communication Security**
- [ ] Email authentication (SPF, DKIM, DMARC) set up
- [ ] Regular phishing tests with Web3 scenarios
- [ ] Email security tools scanning for malicious links
- [ ] Process to verify unusual requests through other channels
- [ ] Clear escalation procedures for suspected attacks

### **Incident Response**
- [ ] Device isolation plan for suspected compromises
- [ ] Employee reporting system for social engineering attempts
- [ ] Information sharing with Web3 security community
- [ ] Automatic access review when employee is targeted
- [ ] Enhanced monitoring for potentially compromised systems
