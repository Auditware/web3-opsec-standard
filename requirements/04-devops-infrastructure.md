# Domain 4: DevOps & Infrastructure

## Risks

- R-DI-001: Compromised Development Environments
- R-DI-002: Insecure Cloud Configurations
- R-DI-003: Supply Chain Attacks Through Dependencies
- R-DI-004: Privileged Access Abuse
- R-DI-005: CI/CD Pipeline Manipulation
- R-DI-006: Infrastructure Secrets Exposure
- R-DI-007: Malware Infection in Trusted Code
- R-DI-008: Impersonated Code Commits
- R-DI-009: Forced Manual Deployments

### **Development Environment Security**

**SP-DI-001: Isolated Development Environments**
- Development activities should be performed in containerized or virtualized environments
- Each code repo should have its own isolated environment to prevent cross contamination
- Code execution must be sandboxed to prevent host system compromise and malware infection

### **Source Code Management**

**SP-DI-002: Repository Security Controls**
- All source code repos must be private by default
- Branch protection rules must be enabled for main/production branches to prevent forced merges
- Signed commits must be required for all code changes
- At least two-person approval must be required for pull requests to protected branches

**SP-DI-003: Source Code Security Scanning**
- Source code must be continuously scanned for accidentally committed secrets
- Dependency security scanning should be in place for production code repos

### **Secrets Management**

**SP-DI-004: Secure Secrets Storage**
- Secrets must not be stored in source code or configuration files unless encrypted
- Dedicated secrets management systems must be used for production secrets
- Production secrets should not be accessible by humans

### **CI/CD Pipeline Security**

**SP-DI-005: Pipeline Access Controls**
- Deployment pipeline modifications must require multi-party approvals
- Pipeline secrets must be managed through secure secret stores, and only accessible by system accounts
- Separate service accounts with minimal permissions must be used for pipeline execution
- Manual deployment steps and permissions for humans must not be allowed

### **Infrastructure as Code**

**SP-DI-006: Infrastructure as Code (IaC)**
- All infrastructure must be defined and managed through code
- IaC definitions must be automatically deployed, with no manual steps or permissions required for humans
- Infrastructure changes must go through a multi-party approval process
- IaC security scanning must be performed before deployment using automated tools

### **Access Management**

**SP-DI-007: Infrastructure Access Controls**
- Infrastructure access must use individual (non-shared) accounts with multi-factor authentication
- Privileged access must be time-limited and require explicit team approval by multiple parties
- Just-in-time (JIT) access control should be implemented for privileged manual operations
- Where JIT access control is not possible, auto-expiring (or planned manually revoked) credentials should be used
- All access activities must be fully logged and monitored in redundant, immutable channels

**SP-DI-008: Break-Glass Accounts**
- Break-glass procedures should be established for emergency access to infrastructure and deployments
- Emergency access to these accounts must be monitored and fully audited upon any usage
- Break-glass account usage must trigger immediate, immutable alerts to the entire team
- Post-incident reviews should be conducted for all break-glass usage

### **Disaster Recovery**

**SP-DI-009: Backup and Disaster Recovery**
- Critical systems should have automated backup and recovery procedures
- A disaster recovery plan should be defined
- Backup systems should be tested regularly

### **Smart Contract Security**

**SP-DI-010: Contract State Monitoring**
- Invariant monitoring should be set up for deployed and owned smart contracts, with well-defined invariants
- Alerts for all major attack indicators should be defined, including at least:
    - Changes in ETH and applicable ERC20 balances
    - Changes in contract ownership and admin permissions
    - Usage of protected functions
- Alerts must be delivered to immutable channels that cannot be silently supressed
- Alerts and invariant monitoring should be enforced at the relayer level, blocking execution and requiring override in order to process flagged transactions
