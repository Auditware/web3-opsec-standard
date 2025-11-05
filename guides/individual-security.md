<div align="center">
  <h1>Individual Security Checklist</h1>
  <p><em>A checklist guide for individuals to follow to maximize their OpSec</em></p>
</div>

---
## Overview


---
# Wallets & Transactions
### Hardware Wallets
- [ ] Hardware wallets should be obtained through verified supply chains:
	- Direct from manufacturer
	- Via a physical trusted retailer
	- NOT from a third party or reseller
- [ ] Wallet device authenticity must be cryptographically verifiable upon receipt to ensure firmware integrity (i.e. as part of the initial set up process)
- [ ] Hardware wallets must have a large screen capable of displaying complete transaction data
	- [ ] Clear signing technology is recommended, but is not a silver bullet and should not replace thorough transaction scrutiny
- [ ] Wallets should have secure PIN entry with randomized entry layouts OR biometric login
	- [ ] PIN entry must have time-based lockouts to prevent brute force attacks
	- [ ] PINs must be at least 6 digits long
- [ ] Wallets should be physically secured in a safe or secret hiding place when not in use
#### Wallet Backups
 - [ ] Seed phrases must be stored on disaster-resistant, physical media. 
 - [ ] Seed phrases must not be stored in plain text - importing them must require a passphrase, additional word, or be scrambled with a random word order; with the secret stored in a password manager
 - [ ] Private keys and seed phrases must be generated on wallet devices and must never be exported (they should never touch another device in any form - no pictures stored or backups in a password manager)
	 - [ ] Alternatively, seed phrases can be sharded (requiring N of M shards to recompose) - e.g. by using Shamir's Secret Sharing algorithm, with each shard recommended to be shared with a trusted guardian (3rd party custodian service, family members, password manager, personal physical media, etc.)
#### Multi-sig Participation
 - [ ] Multi-sig operations must be performed on devices dedicated only to those transactions and transaction verification tools (i.e. you should have a laptop dedicated only to transacting)
	 - [ ] Signing devices must be operated on private, authenticated networks or over trusted VPNs
	 - [ ] Active network monitoring should be in place (e.g. Little Snitch, Lulu, or GlassWire - with default deny on all network requests and only the minimum necessary IPs to execute transactions allowed)
# Endpoints
### Devices
 - [ ] Each organization member must have a device dedicated to organization-related activities and work
 - [ ] Devices should have biometric login options, secure boot, and support for full disk encryption
 - [ ] Personal devices must never be used for work activities or have access to organization accounts
#### Device Supply Chain Security
 - [ ] Dedicated devices should be procured by the organization directly from manufacturers or authorized distributors
 - [ ] Devices must be delivered securely and inspected for tampering upon receipt
 - [ ] Hardware authenticity must be verified through cryptographic attestation when available
#### Device Configuration
 - [ ] Full disk encryption must be required on all organization devices
 - [ ] Inactivity screen locks must be enabled, with a period of no more than 5 minutes before requiring password re-entry
 - [ ] A secure DNS provider should be used (e.g. Cloudflare's [1.1.1.1](https://www.cloudflare.com/learning/dns/what-is-1.1.1.1/))
 - [ ] OS and browser security updates must always be installed as soon as possible when they are available
 - [ ] Users must operate with standard (non-administrative) accounts for daily activities
 - [ ] Administrative privileges must only be granted on a just-in-time basis with proper approval and logging
#### Secure Device Usage
 - [ ] Endpoints must implement automatic screen locks with timeout periods ≤5 minutes
 - [ ] Biometric authentication should be used to prevent password leakage to cameras and onlookers when in public
 - [ ] Privacy screens should be used when working in public spaces
 - [ ] Trusted VPNs should be used when on any public Wi-Fi
 - [ ] When traveling, an organization-managed VPN should be used to secure network traffic
 - [ ] Applications must never be run with root or administrator privileges unless absolutely necessary for specific system tasks
#### Home Network Security
 - [ ] Home WiFi networks should have recommended security settings:
	 - [ ] A strong password (at least 20 characters)
	 - [ ] Router and modem updated to the latest firmware
	 - [ ] Rotated admin login credentials (not the default for the device)
	 - [ ] Have a separate network for guest devices
	 - [ ] Use WPA3/WPA2 encryption (AES, not TKIP)
	 - [ ] Disable WPS
	 - [ ] Disable remote management
#### Network Monitoring and Firewall
 - [ ] All endpoints must have active network monitoring in place
 - [ ] Network monitoring tools must track outbound connections and block all traffic unless explicitly approved
 - [ ] Network firewalls must be enabled
#### Malware Detection
 - [ ] All organization devices should have basic antivirus software enabled (built-in OS antivirus is acceptable, but must be properly enabled without any rule exceptions)
 - [ ] Antivirus software should be regularly updated as soon as new releases are available
#### Browser Security and Isolation
  - [ ]   Organization members should implement browser app isolation
  - [ ] Suggested set up: One browser for session-based, sensitive activities; another browser for opening links and temporary browsing
  - [ ] Wallet extensions should only be used on a browser dedicated only to transacting
#### Secure External File Interaction
 - [ ] Files received from outside the organization must only be opened in a secure sandbox or after being sanitized (e.g. via [Dangerzone](https://dangerzone.rocks/) or Google Docs)
 - [ ] Internally shared files must be distributed via a dedicated file sharing platform (Google Drive/Docs, Dropbox, Notion, etc.), and never sent as email or DM attachments (to prevent social engineering malware delivery vectors)
 - [ ] Shared links should always be manually navigated to or re-typed (to avoid homograph attacks)
#### Browser Extension and Plugin Vetting
 - [ ] All browser extensions must be reviewed and approved before installation
 - [ ] Extensions must be obtained only from official stores (Chrome Web Store, Firefox Add-ons, Microsoft Edge Add-ons, etc.)
 - [ ] User-installed extensions (i.e. manually installed from file) must be prohibited on organization devices
 - [ ] Browser extension permissions must be reviewed and minimized to necessary functions only
 - [ ] Extensions with excessive permissions (read all websites, access to file system, etc.) should be avoided
#### Secure Workspace Requirements
 - [ ] Dedicated workspace areas must be established for performing sensitive operations
 - [ ] Workspaces must be positioned to prevent unauthorized visual access to screens and activities
 - [ ] Privileged operations should never be performed in public spaces
#### Remote Work Physical Security
 - [ ] Work areas must be isolated from common areas where visitors or family members have access
 - [ ] Organizational devices and materials must be securely stored when not in use
 - [ ] Privacy screens should be used on all devices to prevent visual eavesdropping when in public spaces
 - [ ] Computer screens must be locked when unattended
 - [ ] Biometric login and SSO should be used in public spaces to prevent password leakage
#### Account Recovery Protection
 - [ ] Account recovery options can be used, but SMS recovery should not be enabled
 - [ ] Recovery email addresses must be dedicated organizational accounts with strong security and 2FA
#### End-to-End Encrypted Channels
 - [ ] Encrypted communication should be used for confidential communications and coordination of admin operations
 - [ ] Signal or equivalent end-to-end encrypted messaging platforms can be used
#### Secure File Sharing and Viewing
 - [ ] Files received from external parties must never be directly opened, they must be sanitized with an approved software or service (e.g. [Dangerzone](https://dangerzone.rocks/), [VirusTotal](https://www.virustotal.com/gui/home/upload), or [Google Drive](https://support.google.com/drive/answer/141702))
 - [ ] Internally shared files must be distributed via secure file sharing platforms, never via email or chat
#### Critical Operations Confirmations
- [ ] Internal operations coordination must be confirmed in a secure channel (camera-on video calls, end-to-end encrypted chats, in person)
- [ ] Redundant channels for confirmation of operational details are recommended
#### Organization Identity
 - [ ] Organization members must perform all email communication using official emails
 - [ ] Externally verifiable PGP keys should be used to sign emails for external parties to verify authenticity of organization emails
 - [ ] External direct messaging profiles must be linked to from trusted sources (e.g. company websites or well-established social media accounts)
#### IDE Plugin Security
- [ ] IDE extensions and plugins must be thoroughly vetted before installation
- [ ] Extensions must be obtained only from official repositories (e.g. VS Code Marketplace)
- [ ] AI-powered extensions that process code should be restricted to approved providers only
- [ ] Regular reviews of installed extensions must be performed to identify unused or unrecognized plugins
#### Isolated Development Environments
- [ ] Development activities should be performed in containerized or virtualized environments
- [ ] Each code repo should have its own isolated environment to prevent cross contamination
- [ ] Code execution must be sandboxed to prevent host system compromise and malware infection
#### Password Management
- [ ] Passwords and secrets should be:
	- [ ] Not reused
	- [ ] 20-32 characters
	- [ ] Automatically generated with the full character set (letters, numbers, and symbols)
	- [ ] A password manager must be used (1Pass or Bitwarden recommended)
	- [ ] Password manager master passwords should be complex, and at least 20 characters with a mix of phonetic phrases, numbers, and special characters
	- [ ] [https://xkcd.com/936/](https://xkcd.com/936/)
	- [ ] Organization password manager accounts should be separate from personal password manager accounts
#### Login Methods
- [ ] SSO (Single Sign-On - e.g. Log in with Google/Github/Apple) can be used for non-sensitive accounts, but must not be enabled for highly sensitive access (financial, administrative, deployments, infrastructure, etc.)
- [ ] 2FA must be enforced on all accounts
- [ ] FIDO security keys are recommended, but mobile authenticator apps acceptable
- [ ] SMS-based 2FA must never be used unless no other option is available
- [ ] 2FA seeds should not be stored in password managers
- [ ] Passkeys are recommended as a primary login method when available
#### Multi-Factor Authentication for All Accounts
- [ ] All organizational communication accounts must implement multi-factor authentication
- [ ] SMS-based authentication must not be used as a primary or backup factor
- [ ] Hardware security keys should be used where supported by platforms
#### SIM Swap Mitigation
- [ ] All members must set a SIM PIN to mitigate physical theft of SIM cards
- [ ] All members should add additional number transfer security requirements through their phone provider:
	- [ ] **AT&T** - Go to your myAT&T Profile and log in > My Linked Accounts > Manage extra security for your account > turn on Extra security
	- [ ] **T-Mobile** - Add account [Takeover Protection](https://www.t-mobile.com/support/plans-features/account-takeover-protection) to your account
	- [ ] **Verizon** - Enable [Number Lock](https://myvpostpay.verizon.com/ui/acct/secure/profile/security/portsecurity). This can be done by phone, through the app, or on [their website](https://myvpostpay.verizon.com/ui/acct/secure/profile/security/portsecurity)
	- [ ] **Google Fi** - Enable [Number Lock](https://support.google.com/fi/answer/15147412?hl=en#zippy=%2Cturn-on-number-lock)
- [ ] All members must register a Signal account for their phone number (even if not using Signal), to prevent account impersonation via SIM swap attacks