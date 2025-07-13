# URL-based Cross-Site Scripting (XSS) Exploit

## Vulnerability Description
This exploit demonstrates a **URL-based Cross-Site Scripting (XSS)** vulnerability where malicious JavaScript code is embedded in URL parameters and executed in the victim's browser context, specifically targeting the media page functionality.

## Attack Methodology

### Reconnaissance
- Identify URL parameters that are reflected in the response
- Analyze the application's URL parameter handling
- Determine the context where URL input is displayed
- Map the application's parameter processing logic

### Exploitation Steps
1. **Identify the vulnerable URL parameter** (src parameter in media page)
2. **Analyze the response context** where the URL input is reflected
3. **Construct malicious payload** using data URI scheme with base64 encoding
4. **Encode the payload** to bypass potential filters
5. **Execute the payload**: `?page=media&src=data:text/html;base64,PHNjcmlwdD5hbGVydCgxKTs8L3NjcmlwdD4=`

### Technical Details
- **Vulnerability Type**: URL-based Cross-Site Scripting (XSS)
- **Attack Vector**: Data URI Injection with Base64 Encoding
- **Payload**: `data:text/html;base64,PHNjcmlwdD5hbGVydCgxKTs8L3NjcmlwdD4=`
- **Decoded Payload**: `<script>alert(1);</script>`
- **Target Parameter**: `src` in media page
- **Impact**: Arbitrary JavaScript execution in victim's browser
- **Difficulty Level**: Medium

## Root Cause Analysis
The application fails to properly validate and sanitize URL parameters, particularly data URI schemes, allowing malicious JavaScript to be executed in the browser context through URL manipulation.

## Mitigation Strategies

### Immediate Fixes
1. **Filter data URI schemes** in URL parameters
2. **Implement proper input validation** and sanitization
3. **Use Content Security Policy (CSP)** headers
4. **Encode output** to prevent script execution

### Long-term Security Measures
1. **Web Application Firewall (WAF)** with XSS protection
2. **Regular security audits** of URL parameter handling
3. **Static code analysis** to identify vulnerable patterns
4. **Security testing** including automated XSS detection

## Security Best Practices
- Always validate and sanitize URL parameters
- Implement Content Security Policy (CSP)
- Use proper output encoding
- Regular security assessments and penetration testing
- Implement proper error handling without information disclosure

## XSS Prevention Techniques
- Input validation and sanitization
- Output encoding (HTML, JavaScript, CSS)
- Content Security Policy (CSP)
- HttpOnly cookies for session management
- Regular security testing and code reviews

## Flag
The exploit successfully executes malicious JavaScript through URL parameter manipulation to obtain the flag.