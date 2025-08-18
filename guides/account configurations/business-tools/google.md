<div align="center">
  <img src="../../../images/guide logos/google.svg" alt="Google Logo" width="64" height="64">
  <h2><a href="https://workspace.google.com/" target="_blank" rel="noopener noreferrer">Google</a> Configuration Guide</h2>
</div>

## Individual Account Settings

**All organization members must configure their personal Google accounts with the following settings:**

- Account Settings:
    - Settings > Security > 2-Step Verification
        - [ ]  Enable any, but passkeys or authenticator recommended
        - [ ]  Remove any App passwords
    - [ ]  Settings > Security > Skip passwords when possible > **Enabled**
        - *Skipping password entry allows you to renew logins in public places without having to type out your password or store it in your clipboard*
    - [ ]  Settings > Security > Recovery email > **Enabled**
    - [ ]  Settings > Security > Recovery phone > **Disabled**
    - [ ]  Settings > Security > Third-party apps with account access > Remove all unnecessary
    - [ ]  Settings > Security > Your devices > Log out from all unnecessary devices
    - [ ]  Security > Enhanced Safe Browsing > **Enabled**

---

## Admin Settings (Workspace Configuration)

#### Rules and Notifications
- [Rules](https://admin.google.com/ac/ax) > Enable notifications for security events
    - [ ]  "User's password changed"
    - [ ]  "Suspicious login"
    - [ ]  "User granted Admin privilege"
    - [ ]  "User's Admin privilege revoked"
    - [ ]  "Primary admin changed"
    - [ ]  "Leaked password"
    - [ ]  "Device compromised" [[1]](#security-alerts)

#### Security Settings
- [ ]  Security > Overview > Less Secure Apps > **Disable access to less secure apps**
- [ ]  Security > Authentication > 2-Step Verification > **Allow users to turn on 2-Step Verification**
    - [ ]  Enforcement > **On**
        - [ ]  Methods > **Any except verification codes via text, phone call** or **Only security key** [[2]](#2fa-enrollment)
- Security > Authentication > Account Recovery >
    - [ ]  Super admin account recovery > **On** (if fewer than 3 super admins on account)
    - [ ]  User account recovery > **On**
- [ ]  Security > Authentication > Password Management > **Enforce strong password**
    - [ ]  Length > Minimum length > At least **12**
- [ ]  Security > Access and data control > Google Cloud session control > Reauthentication policy > **Require reauthentication**
    - [ ]  Exempt Trusted apps > **Off**
    - [ ]  Reauthentication frequency > **16**

#### Apps and Data Control
- [ ]  Apps > Google Workspace > Drive and Docs > Sharing options >
    - [ ]  Sharing outside of organization > **OFF** or **ALLOWLISTED DOMAINS**
        - [ ]  Allow users in organization to receive files from users or shared drives outside of organization/allowlisted domains > **Off**
        - [ ]  When sharing outside of organization is allowed, users in organization can make files and published web content visible to anyone with the link > **Off**
    - [ ]  Distributing content outside of organization > **No one**
- [ ]  Apps > Google Workspace > Settings for Google Chat > Service Settings > **OFF for everyone**

#### Gmail Security
- Apps > Google Workspace > Settings for Gmail >
    - [ ]  Authenticate email > Set up **DKIM** with your DNS provider
    - **Safety >**
        - [ ]  Attachments > **Enable** all protections and set to quarantine
        - [ ]  IMAP [view time protections](https://support.google.com/a/answer/10036904?sjid=9191352966703497335-NC) > **Enabled**
        - [ ]  Links and external images > **Enable** all
        - [ ]  Spoofing and authentication > **Enable** all and set to quarantine
            - [ ]  **Protect against any unauthenticated emails** can be set to **Keep email in inbox and show warning** in order to prevent blocking external emails

#### Email Authentication
- **SPF & DMARC**
    - Follow these guides to confirm and/or set up SPF and DMARC:
        - https://support.google.com/a/answer/33786?hl=en&sjid=5876544508252018851-NC#spf-already-setup
        - https://support.google.com/a/answer/2466580?hl=en#dmarc-step2

#### Optional Enhancement
- Enroll in the [Advanced Protection Program](https://landing.google.com/advancedprotection/) for high-risk users or your entire organization

---

## Notes

### <a id="security-alerts"></a>[1] Security Alerts
Other alerts should be enabled by default, but it is recommended to go through the list and enable any others that would indicate concerns.

### <a id="2fa-enrollment"></a>[2] 2FA Enrollment
You can confirm user enrollment status at Directory > Users, under the **2-step verification enrollment** and **Advanced Protection Program enrollment** columns.
