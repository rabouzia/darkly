# Stored Cross-Site Scripting (XSS) Exploit

## Vulnerability Description
This exploit demonstrates a **Stored Cross-Site Scripting (XSS)** vulnerability where malicious JavaScript code is permanently stored in the application's database and executed whenever the stored content is displayed to users.

## Attack Methodology

### Reconnaissance
- Identify input fields that store data (feedback forms, comments, etc.)
- Analyze the application's data storage and retrieval mechanisms
- Determine how stored content is displayed to users
- Map the application's content handling logic

### Exploitation Steps
1. **Identify the vulnerable input field** (feedback form)
2. **Analyze the data storage mechanism** and display context
3. **Construct malicious payload** for stored XSS
4. **Submit the payload** through the feedback form: `<script>alert('XSS')</script>`
5. **Trigger the stored XSS** when the feedback is displayed

### Technical Details
- **Vulnerability Type**: Stored Cross-Site Scripting (XSS)
- **Attack Vector**: Persistent XSS through Feedback Form
- **Payload**: `<script>alert('XSS')</script>`
- **Storage Location**: Application database
- **Impact**: Persistent malicious script execution for all users
- **Difficulty Level**: Medium

## Root Cause Analysis
The application fails to properly validate and sanitize user input before storing it in the database, allowing malicious scripts to be permanently stored and executed when displayed.

## Mitigation Strategies

### Immediate Fixes
1. **Implement proper input validation** and sanitization
2. **Use output encoding** to prevent script execution
3. **Implement Content Security Policy (CSP)** headers
4. **Add input filtering** for script tags and JavaScript

### Long-term Security Measures
1. **Web Application Firewall (WAF)** with XSS protection
2. **Regular security audits** of input handling
3. **Static code analysis** to identify vulnerable patterns
4. **Security testing** including automated XSS detection

## Security Best Practices
- Always validate and sanitize user input before storage
- Implement proper output encoding
- Use Content Security Policy (CSP)
- Regular security assessments and penetration testing
- Implement proper error handling without information disclosure

## XSS Prevention Techniques
- Input validation and sanitization
- Output encoding (HTML, JavaScript, CSS)
- Content Security Policy (CSP)
- HttpOnly cookies for session management
- Regular security testing and code reviews

## Flag
The exploit successfully stores malicious JavaScript in the application database through the feedback form to obtain the flag.