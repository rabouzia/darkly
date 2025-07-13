# Force Link Redirect Exploit

## Vulnerability Description
This exploit demonstrates a **Force Link Redirect** vulnerability where social media links can be manipulated to redirect users to unauthorized destinations, potentially leading to phishing attacks or information disclosure.

## Attack Methodology

### Reconnaissance
- Identify social media links in the application
- Analyze the link structure and parameters
- Determine the redirect mechanism
- Map the application's link handling logic

### Exploitation Steps
1. **Identify the vulnerable social media link** (Twitter link)
2. **Analyze the link structure** to understand the redirect mechanism
3. **Modify the link destination** to point to an unauthorized URL
4. **Change the target URL** from Twitter to `intra.42.fr`
5. **Trigger the redirect** to access the unauthorized destination

### Technical Details
- **Vulnerability Type**: Force Link Redirect / Open Redirect
- **Attack Vector**: URL Parameter Manipulation
- **Original Target**: Twitter social media link
- **Manipulated Target**: `intra.42.fr`
- **Impact**: Unauthorized redirect to external domains
- **Difficulty Level**: Low

## Root Cause Analysis
The application fails to validate redirect URLs and allows arbitrary external domains to be used as redirect destinations, enabling potential phishing attacks.

## Mitigation Strategies

### Immediate Fixes
1. **Implement URL validation** for redirect destinations
2. **Use whitelist approach** for allowed redirect domains
3. **Add redirect confirmation** for external domains
4. **Implement proper error handling** without information disclosure

### Long-term Security Measures
1. **Web Application Firewall (WAF)** with redirect protection
2. **Regular security audits** of redirect mechanisms
3. **Static code analysis** to identify vulnerable patterns
4. **Security testing** including automated redirect detection

## Security Best Practices
- Always validate redirect URLs against a whitelist
- Implement redirect confirmation for external domains
- Use proper URL encoding and validation
- Regular security assessments and penetration testing
- Implement proper error handling without information disclosure

## Redirect Security Measures
- URL validation and sanitization
- Whitelist of allowed redirect domains
- User confirmation for external redirects
- Proper URL encoding
- Security headers and monitoring

## Flag
The exploit successfully manipulates the social media link to redirect to an unauthorized destination and obtain the flag.