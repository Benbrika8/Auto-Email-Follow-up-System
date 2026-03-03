# Security Policy

## Supported Versions

Security updates are provided for the following versions:

| Version | Supported          |
| ------- | ------------------ |
| 1.0.x   | :white_check_mark: |
| < 1.0   | :x:                |

## Reporting a Vulnerability

We take security vulnerabilities seriously. If you discover a security issue, please follow responsible disclosure practices.

### How to Report

**Do NOT open a public GitHub issue for security vulnerabilities.**

Instead, report security issues privately:

1. Use GitHub Security Advisory (preferred): Go to repository → Security → Advisories → Report a vulnerability
2. Send email to: benbrika.salaheddine@gmail.com with subject "SECURITY: Auto Email Follow-up System"
3. Include detailed description of the vulnerability
4. Provide steps to reproduce the issue
5. Include potential impact assessment
6. Suggest a fix if you have one

### What to Include

A good security report includes:

- **Type of vulnerability** (e.g., credential exposure, injection, authentication bypass)
- **Workflow components affected** (specific nodes or configurations)
- **Steps to reproduce** (detailed, step-by-step)
- **Impact assessment** (what data or systems are at risk)
- **Suggested remediation** (if you have recommendations)
- **Your contact information** (for follow-up questions)

### Response Timeline

We aim to respond to security reports:

- **Initial Response**: Within 48 hours
- **Vulnerability Confirmation**: Within 7 days
- **Fix Development**: 14-30 days (depending on severity)
- **Public Disclosure**: After fix is deployed and users notified

### Severity Levels

We classify vulnerabilities using industry-standard severity ratings:

**Critical (CVSS 9.0-10.0)**
- Credential exposure in workflow JSON
- Remote code execution vulnerabilities
- Unauthorized access to email accounts
- OAuth token theft or bypass

**High (CVSS 7.0-8.9)**
- Authentication bypass
- Privilege escalation
- Sensitive data exposure in logs
- Email injection attacks

**Medium (CVSS 4.0-6.9)**
- Cross-site scripting (XSS) in N8N UI
- Information disclosure
- Denial of service vulnerabilities
- Weak encryption or authentication

**Low (CVSS 0.1-3.9)**
- Minor information leaks
- Non-exploitable bugs with security implications
- Configuration weaknesses

## Security Best Practices

### For Users

When deploying this workflow, follow these security guidelines:

#### Credential Management

- **Never commit credentials** to Git repositories
- **Use OAuth2 authentication** for Gmail (not username/password)
- **Rotate credentials regularly** (every 90 days recommended)
- **Use separate service accounts** for production vs development
- **Store credentials securely** in N8N credential store only
- **Enable 2FA** on all Gmail accounts used by workflow
- **Review credential permissions** regularly and revoke unused tokens

#### N8N Instance Security

- **Enable HTTPS** for all N8N instances (especially self-hosted)
- **Use strong authentication** on N8N UI (not default password)
- **Restrict network access** to N8N instance (firewall rules, VPN)
- **Keep N8N updated** to latest version for security patches
- **Enable audit logging** to track workflow executions
- **Disable public workflow sharing** unless intentional
- **Use environment variables** for sensitive configuration
- **Regular backups** of N8N database and workflows

#### Gmail API Security

- **Minimal scopes** - Only grant required Gmail permissions (read, send, modify)
- **Monitor API usage** in Google Cloud Console for anomalies
- **Set up quota alerts** to detect unusual activity
- **Review OAuth consent screen** regularly
- **Revoke unused tokens** in Google Account settings
- **Enable Gmail security alerts** for unusual access patterns
- **Use dedicated service accounts** for production workflows

#### Workflow Configuration

- **Validate input data** before processing in code nodes
- **Sanitize email content** to prevent injection attacks
- **Implement rate limiting** to prevent abuse
- **Add spam filtering** before auto-responding to emails
- **Log security events** (failed authentications, unusual patterns)
- **Avoid hardcoding secrets** in workflow JSON
- **Use try-catch blocks** in JavaScript code nodes
- **Validate email addresses** before sending responses

#### Data Privacy

- **Comply with regulations** (GDPR, CCPA, etc.) for email data
- **Minimize data retention** - don't store emails longer than needed
- **Encrypt sensitive data** at rest and in transit
- **Anonymize logs** - remove PII from execution logs
- **Document data handling** in privacy policy
- **Implement data deletion** procedures for customer requests
- **Audit data access** regularly
- **Train team on privacy best practices**

### For Contributors

When contributing code:

- **Remove all credentials** from workflow JSON exports
- **Don't commit API keys** or tokens to Git
- **Sanitize code examples** - use placeholder values
- **Review third-party dependencies** for known vulnerabilities
- **Follow secure coding practices** in JavaScript code nodes
- **Test security features** before submitting PRs
- **Document security changes** in pull request descriptions
- **Use `.gitignore`** to prevent credential leaks

## Known Security Considerations

### Current Workflow Design

**Email Content Handling**
- Workflow processes email content in JavaScript nodes
- Risk: Malicious email content could cause code execution issues
- Mitigation: Input validation and sanitization implemented in classifier

**Credential Storage**
- N8N stores credentials encrypted in its database
- Risk: Database compromise exposes credentials
- Mitigation: Use N8N cloud or secure self-hosted infrastructure with encryption at rest

**Gmail API Permissions**
- Workflow requires read, send, and modify Gmail permissions
- Risk: Compromised credentials allow email account access
- Mitigation: OAuth2 with token rotation, minimal scopes, monitoring for anomalies

**Automated Responses**
- Workflow auto-replies to emails without human review
- Risk: Could respond to spam, phishing, or malicious emails
- Mitigation: Recommended to add spam filtering before classification (not included in v1.0)

**JavaScript Code Execution**
- Custom code runs in N8N's Node.js environment
- Risk: Malicious code injection if workflow modified by unauthorized users
- Mitigation: Restrict N8N access, review all code changes, use version control

## Security Updates

Subscribe to security notifications:

- Watch GitHub repository for security advisories
- Enable GitHub notifications for security alerts
- Follow [@Benbrika8](https://github.com/Benbrika8) for critical announcements
- Check CHANGELOG.md for security-related patches
- Join N8N community for platform security updates

## Vulnerability Disclosure Policy

### Public Disclosure Timeline

After a security fix is released:

1. **Day 0**: Security fix deployed in latest version on GitHub
2. **Day 7**: Email notification sent to known production users (if applicable)
3. **Day 30**: Public security advisory published on GitHub
4. **Day 60**: Full technical details disclosed (if appropriate and safe)

### Credit and Recognition

We appreciate security researchers who responsibly disclose vulnerabilities:

- Researchers credited in security advisory (with permission)
- Listed in CHANGELOG.md under security fixes
- Public acknowledgment on GitHub and social media (optional)
- Fast-track priority for future contributions

## Bug Bounty Program

Currently, this project does not offer a paid bug bounty program. However, we deeply appreciate responsible security research and will:

- Provide public recognition for valid reports
- Prioritize your issues and pull requests
- Consider you for future paid consulting opportunities
- Reference your work in security documentation

## Security Checklist for Deployment

Before deploying to production:

- [ ] Gmail OAuth2 credentials configured with minimal scopes
- [ ] N8N instance secured with HTTPS and strong authentication
- [ ] Firewall rules restrict access to N8N instance
- [ ] All credentials removed from workflow JSON before committing to Git
- [ ] `.gitignore` file properly configured
- [ ] Workflow tested with malicious input samples
- [ ] Gmail API quota alerts configured in Google Cloud Console
- [ ] Audit logging enabled in N8N
- [ ] Regular credential rotation scheduled (90 days)
- [ ] Team trained on security best practices
- [ ] Incident response plan documented
- [ ] Data privacy compliance reviewed (GDPR/CCPA)

## Incident Response

If you suspect a security breach:

1. **Immediately disable** the affected workflow in N8N
2. **Revoke OAuth tokens** in Google Account settings
3. **Review N8N execution logs** for suspicious activity
4. **Check Gmail account** for unauthorized access or sent emails
5. **Rotate all credentials** (new OAuth tokens, N8N passwords)
6. **Investigate root cause** before re-enabling workflow
7. **Report incident** to maintainer via security advisory
8. **Document lessons learned** and update security procedures

## Contact

**Security Contact**: benbrika.salaheddine@gmail.com

**Maintainer**: Salah Eddine Benbrika ([Benbrika8](https://github.com/Benbrika8))

**GitHub Security Advisories**: [Report a vulnerability](https://github.com/Benbrika8/auto-email-followup/security/advisories/new)

---

**Last Updated**: March 3, 2026

*This security policy is subject to change. Check back regularly for updates.*

---

## Additional Resources

- [N8N Security Best Practices](https://docs.n8n.io/hosting/security/)
- [Gmail API Security Guidelines](https://developers.google.com/gmail/api/guides/security)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [CWE/SANS Top 25](https://cwe.mitre.org/top25/)