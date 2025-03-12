# Authentication and Authorization

**Duration:** 33 minutes  
**XP:** 600

## User Identity and Access Management

### Key Authentication Points
- Access control starts with user authentication
- Individual accounts require username/password
- 2FA strongly recommended for security
- Identity providers (IdP) enhance capabilities

### SAML SSO Integration
**Supported Providers:**
- Active Directory Federation Services (AD FS)
- Microsoft Entra ID
- Okta
- OneLogin
- PingOne
- Shibboleth

## Repository Access Control

### Repository Types
- Public - Open to everyone
- Private - Limited to creator and shared users
- Internal - Organization members only

### Authentication Methods

#### SAML SSO
- Admin connects GitHub to IdP
- Users authenticate via IdP
- Enforced authentication through IdP

#### Two-Factor Authentication (2FA)

| Method | Security Level | Notes |
|--------|---------------|-------|
| Security Keys | Highest | Phishing-resistant, requires physical key |
| TOTP Apps | High | Cloud-based, globally reliable |
| SMS | Basic | Fallback option only |

## User Authorization

### Authorization Process
- Follows successful authentication
- Controls access to organization resources
- Manages personal access tokens
- Handles SSH keys and OAuth apps

### SAML SSO Authorization
- Repository access control
- Issue and PR permissions
- SCIM integration for automation
- User lifecycle management

## Team Synchronization

### Features
- IdP-based team management
- Automatic user synchronization
- Custom team mappings
- Dynamic configuration

### Usage Limits
| Resource | Limit |
|----------|--------|
| Team members | 5,000 |
| Organization members | 10,000 |
| Organization teams | 1,500 |

## Additional Resources
- Identity provider setup guides
- Authorization best practices
- Security compliance documentation
