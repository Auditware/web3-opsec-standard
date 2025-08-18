<div align="center"> <img src="../../../images/guide logos/telegram.svg" alt="Telegram Logo" width="64" height="64"> <h2><a href="https://telegram.org/" target="_blank" rel="noopener noreferrer">Telegram</a> Configuration Guide</h2> </div>

## Individual Account Settings

**All organization members must configure their personal Telegram accounts with the following settings:**

- Account Settings:
    - Privacy & Security >
        - Security >
            - [ ]  Two-Step Verification > **On**
                - Do not set a password hint, do add a recovery email
            - [ ]  Local passcode > **On** (recommended)
            - Active sessions >
                - [ ]  Review and delete all unused sessions
                - [ ]  Terminate old sessions > **1 month**
        - Privacy >
            - [ ]  Phone Number > Who can see my phone number > **Nobody**
            - [ ]  Phone Number > Who can find me by my number > **My Contacts**
            - [ ]  Phone Number > Exceptions > Remove all
            - [ ]  Last Seen & Online > Who can see my timestamp > **Nobody**/**My Contacts**
            - [ ]  Last Seen & Online > Exceptions > Remove all
            - [ ]  Date of Birth > Who can see my date of birth > **Nobody**
            - [ ]  Date of Birth > Exceptions > Remove all
            - [ ]  Calls > Who can call me > **Nobody**/**My Contacts**
            - [ ]  Calls > Exceptions > Remove all
            - [ ]  Calls > Peer-to-peer > Use peer-to-peer with > **Nobody**/**My Contacts**
                
                > **Note**: Peer-to-peer calls leak your IP address to callers. Set to **Nobody** to preserve anonymity
                
            - [ ]  Calls > Peer-to-peer > Exceptions > Always allow > Remove all
            - [ ]  Groups & Channels > Who can add me to groups and channels > **Nobody**/**My contacts**
            - [ ]  Groups & Channels > Exceptions > Remove all
            - [ ]  Voice Messages > Who can send me voice messages > **Nobody**/**My contacts**
            - [ ]  Voice Messages > Exceptions > Remove all
            - [ ]  Messages > Who can send me messages > **My Contacts and Premium Users**
        - [ ]  New chats from unknown users > Archive and Mute > **Enabled**
        - [ ]  Bots and website > **Clear Payment and Shipping Info**
    - Advanced >
        - [ ]  Automatic media download > Disable all types in all cases
            
            > **Note**: Automatic media download leaves you exposed to advanced malware attacks
            
        - [ ]  Version and updates > Update automatically > **Enabled**
        - [ ]  Version and updates > Install beta versions > **Disabled**

> **Authentication Guidelines**: When establishing a secret chat, [compare the encryption keys](https://core.telegram.org/techfaq#q-how-are-secret-chats-authenticated) outside of telegram, in an established/authenticated channel, outside of telegram. When establishing a peer-to-peer (encrypted) call, [compare the emojis](https://core.telegram.org/techfaq#q-how-are-voice-and-video-calls-authenticated) in an established/authenticated channel, outside of telegram. These are your defenses against man-in-the-middle attacks. You **must** confirm these details if using Telegram for private communications. That said, it is suggested to use a secure platform like [Signal](https://signal.org/) for confidential communication.

---

## Channel & Group Settings (Admin Configuration)

#### Channel Settings
- Open channel > click channel name > **Channel settings**
    - [ ]  Sign messages > **Enable** (if non-repudiation is desired)
    - [ ]  Administrators > Review the list and remove any unnecessary

#### Group Settings
- Open group > click group name > click three dots > **Manage group**
    - [ ]  Channel type > **Private** (if public discoverability is not necessary)
    - [ ]  Channel type > Content protection > **Enabled** (if confidentiality is needed)
    - [ ]  Sign messages > **Enabled**
    - [ ]  Chat history for new members > **Hidden**
        - This is not available if Topics are enabled
    - **Permissions:**
        - [ ]  Send media > should be restricted appropriately
            - At minimum, **Files** and **Embed links** should be disabled
        - [ ]  Add members > **Disabled** (if not necessary) [[1]](#member-control)
        - [ ]  Pin messages > **Disabled**
        - [ ]  Change group info > **Disabled**
        - [ ]  Slow mode > At least **10s**, if not obstructive
        - [ ]  Exceptions should be restricted to valid use cases
            - Team members should have exceptions granted to them for these rather than them being admins, when possible
    - [ ]  **Invite links** > Review and remove unnecessary
        - Links should be limited by time period or number of users, when not obstructive
    - [ ]  **Administrators** > Review and remove unnecessary & review permissions of each admin
        - Again, it is recommended to add exceptions for team members rather than add them as admins, when possible
        - Remove unnecessary permissions, especially **Add new admins**
        - **Aggressive Anti-Spam** > **Enabled**
    - [ ]  **Members** > Review and remove unnecessary (If a confidential channel)

#### Additional Recommendations
- Add a disclaimer in the description and/or as a pinned message to your channel that states that you will not DM users, and that support will only be offered via the public channel and dedicated support channels [[2]](#security-disclaimers)
- Add a suffix to admin usernames, for example: "MyName | will never DM you"
- Each admin must follow the guidance for securing their individual accounts

---

## Notes

### <a id="member-control"></a>[1] Member Control
Restricting the ability to add only to admins allows for revocability of invite links to stop raids or to freeze the channel if needed.

### <a id="security-disclaimers"></a>[2] Security Disclaimers
Telegram channels and groups should not be used for any confidential communication, as they are not end-to-end encrypted, except for 1:1 "secret chats" (which should not be commingled with unencrypted chats).

Example disclaimer: "We will NEVER message you directly to offer support or assistance with our product. For support, please email us at support@<company>.com. DO NOT interact with anyone DMing and claiming to be a <company> member. Please report scams to reports@<company>.com"
