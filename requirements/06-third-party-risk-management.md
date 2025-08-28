# Domain 6: Third-Party Risk Management

## Risks

- R-TR-001: Malicious Browser Extensions and IDE Plugins
- R-TR-002: Compromised Software Dependencies and Packages
- R-TR-003: Typosquatting and Package Name Confusion Attacks
- R-TR-004: Supply Chain Compromise of Critical Vendors
- R-TR-005: Third-Party Data Breaches Affecting Organization
- R-TR-006: Vendor Privileged Access Abuse
- R-TR-007: Malicious or Backdoored Development Tools
- R-TR-008: Cloud Service Provider Security Failures
- R-TR-009: Third-Party API and Service Compromise
- R-TR-010: Vendor Business Continuity Failures

### **Browser Extensions and IDE Plugin Security**

**SP-TR-001: Extension and Plugin Vetting**
- All browser extensions and IDE plugins must be reviewed and approved before installation
- Extensions must be obtained only from official stores (Chrome Web Store, Firefox Add-ons, Microsoft Edge Add-ons, VS Code Marketplace, etc.)
- User-installed extensions must be prohibited on organization devices
- Browser extension permissions must be reviewed and minimized to necessary functions only
- Extensions with excessive permissions (read all websites, access to downloads, etc.) should be avoided

**SP-TR-002: Cursor and IDE Plugin Security**
- Cursor AI extensions and plugins must be thoroughly vetted before installation
- AI-powered extensions that process code should be restricted to approved vendors only
- Code completion and AI assistant extensions must not have access to send code to external services without explicit approval
- Extensions that modify code or have write access to files require additional security review
- Regular audits of installed extensions must be performed to identify unused or suspicious plugins

**SP-TR-003: Extension Monitoring and Management**
- Organizations must maintain an approved extension whitelist
- Automated monitoring should detect installation of non-approved extensions
- Extension updates must be tested in sandbox environments before deployment
- Extensions with known vulnerabilities must be immediately removed
- Browser extension management policies must be enforced through enterprise management tools

### **Package and Dependency Security**

**SP-TR-004: Package Verification and Integrity**
- All software packages must be verified for authenticity before installation
- Package signatures and checksums must be validated against known good sources
- Packages should be obtained from official repositories and trusted mirrors only
- Private package repositories should be used for internal dependencies
- Package integrity monitoring must detect tampering or modification

**SP-TR-005: Typosquatting Detection and Prevention**
- Package names must be verified against known typosquatting patterns before installation
- Visual verification techniques must be used to detect character substitution attacks:
  - Copy package names into code blocks to display in monospace font for character verification
  - Use monospace fonts (Consolas, Monaco, Courier New) that clearly distinguish similar characters
  - Compare package names character-by-character against official documentation
- Automated typosquatting detection tools should be integrated into package management workflows
- Dependency confusion attacks must be prevented through private repository prioritization

**SP-TR-006: Dependency Management and Scanning**
- All dependencies must be scanned for known vulnerabilities before deployment
- Software Bill of Materials (SBOM) must be maintained for all applications
- Dependency pinning must be used to prevent automatic updates to compromised versions
- Regular dependency audits must identify outdated or vulnerable components
- Critical dependencies should have multiple trusted sources or mirrors identified

### **Vendor and Service Provider Security**

**SP-TR-007: Vendor Security Assessment**
- All vendors with access to organization systems or data must undergo security assessment
- Vendor assessments must include:
  - Security certifications and compliance attestations
  - Incident response capabilities and history
  - Data handling and privacy practices
  - Access controls and authentication requirements
  - Business continuity and disaster recovery plans
- High-risk vendors must provide additional security documentation and undergo on-site assessments

**SP-TR-008: Vendor Access Management**
- Vendor access to organization systems must be time-limited and purpose-specific
- Just-in-time access provisioning should be used for vendor support activities
- Vendor access must be monitored and logged with immutable audit trails
- Multi-factor authentication must be required for all vendor access
- Vendor access must be reviewed and revalidated on a regular schedule

**SP-TR-009: Cloud Service Provider Security**
- Cloud service providers must meet or exceed organization security requirements
- Cloud security configurations must be continuously monitored and validated
- Data sovereignty and jurisdiction requirements must be enforced
- Cloud service provider security incident notification must be required
- Multi-cloud strategies should be implemented to reduce single provider dependency

### **Supply Chain Security**

**SP-TR-010: Software Supply Chain Integrity**
- All software must be obtained through verified supply chains with integrity checking
- Build and deployment pipelines must include supply chain verification steps
- Third-party software updates must be tested in isolated environments before deployment
- Software provenance and attestation must be verified for critical components
- Supply chain attacks must be detected through behavioral monitoring and anomaly detection

**SP-TR-011: Hardware Supply Chain Security**
- Hardware must be obtained directly from manufacturers or authorized distributors
- Hardware authenticity must be verified through cryptographic attestation when available
- Physical inspection must be performed on critical hardware components
- Hardware with unknown or suspicious provenance must be rejected
- Hardware supply chain documentation must be maintained for audit purposes

### **Third-Party Monitoring and Incident Response**

**SP-TR-012: Third-Party Security Monitoring**
- Continuous monitoring must be implemented for third-party security incidents
- Threat intelligence feeds must include vendor and supply chain compromise indicators
- Third-party breach notifications must trigger immediate security assessments
- Vendor security posture must be continuously evaluated and scored
- Automated alerting must notify security teams of third-party security events

**SP-TR-013: Third-Party Incident Response**
- Incident response plans must include third-party compromise scenarios
- Procedures must be established for immediate vendor access revocation
- Data impact assessments must be performed for third-party breaches
- Legal and regulatory notification requirements must be defined for vendor incidents
- Vendor incident response coordination must be tested through tabletop exercises

## Typosquatting Detection Checklist

### **Visual Verification Techniques**

**Character Substitution Detection**
- [ ] Copy package/extension names into a code block to display in monospace font for character verification
- [ ] Use monospace fonts that clearly distinguish similar characters:
  - Consolas, Monaco, or Courier New for clear character distinction
  - Avoid serif fonts (Times New Roman, Georgia) which make similar characters harder to distinguish
- [ ] Manually compare each character against official documentation
- [ ] Check for common substitutions:
  - [ ] i (lowercase i) vs l (lowercase L) vs 1 (number one) vs | (pipe)
  - [ ] O (capital O) vs 0 (zero) vs o (lowercase o)
  - [ ] rn (r+n) vs m (single m)
  - [ ] vv (v+v) vs w (single w)
  - [ ] cl (c+l) vs d (single d)

**Domain and Package Name Verification**
- [ ] Verify package name against official project documentation
- [ ] Check package repository URL for authenticity
- [ ] Compare download counts and publication dates with known legitimate packages
- [ ] Verify package maintainer identity and history
- [ ] Cross-reference package name with multiple trusted sources

### **Automated Detection Tools**

**Package Management Security**
- [ ] Use tools like `npm audit`, `yarn audit`, or `safety check` for vulnerability scanning
- [ ] Implement dependency pinning to prevent automatic updates
- [ ] Use private package repositories to prevent dependency confusion
- [ ] Enable package signature verification where available
- [ ] Integrate typosquatting detection tools into CI/CD pipelines

**Browser Extension Security**
- [ ] Review extension permissions before installation
- [ ] Verify extension developer identity and reputation
- [ ] Check extension review history and user feedback
- [ ] Confirm extension source code availability for open source extensions
- [ ] Monitor extension update frequency and change logs

### **Implementation Checklist**

**Before Installing Any Third-Party Component**
- [ ] Verify the official name and source
- [ ] Copy name into code block: `package-name-here` to check for character substitution
- [ ] Confirm package/extension source is official (GitHub, npm registry, Chrome Web Store, etc.)
- [ ] Review permissions and access requirements
- [ ] Check security scan results and vulnerability reports
- [ ] Verify digital signatures or checksums where available
- [ ] Review maintainer identity and project history
- [ ] Confirm business justification for installation

**After Installation**
- [ ] Monitor for unusual network activity or system behavior
- [ ] Review logs for suspicious API calls or data access
- [ ] Perform regular updates only from verified sources
- [ ] Audit installed components quarterly for continued necessity
- [ ] Remove unused or obsolete third-party components immediately

**Ongoing Monitoring**
- [ ] Subscribe to security advisories for installed components
- [ ] Monitor vendor security posture and incident reports
- [ ] Regularly scan for dependency vulnerabilities
- [ ] Maintain inventory of all third-party components
- [ ] Test incident response procedures for third-party compromises
