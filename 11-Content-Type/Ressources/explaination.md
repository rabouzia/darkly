# Content-Type Bypass Exploit

## Vulnerability Description
This exploit demonstrates a **Content-Type Bypass** vulnerability where file upload restrictions can be circumvented by manipulating the HTTP Content-Type header, allowing unauthorized file types to be uploaded and executed.

## Attack Methodology

### Reconnaissance
- Identify the file upload functionality
- Analyze the application's file type validation
- Determine the Content-Type header handling
- Map the application's upload restrictions

### Exploitation Steps
1. **Identify the file upload endpoint** and its restrictions
2. **Prepare a malicious PHP payload** for upload
3. **Intercept the upload request** using a proxy tool
4. **Modify the Content-Type header** from `application/x-php` to `image/jpeg`
5. **Submit the request** with the manipulated Content-Type
6. **Bypass file type validation** and upload the malicious file

### Technical Details
- **Vulnerability Type**: Content-Type Bypass / File Upload Bypass
- **Attack Vector**: HTTP Header Manipulation
- **Original Content-Type**: `application/x-php`
- **Manipulated Content-Type**: `image/jpeg`
- **Payload**: Malicious PHP file
- **Impact**: Unauthorized file upload and potential code execution
- **Difficulty Level**: Medium

## Root Cause Analysis
The application relies solely on the Content-Type header for file type validation without proper file content analysis, allowing attackers to bypass upload restrictions by manipulating header values.

## Mitigation Strategies

### Immediate Fixes
1. **Implement file content analysis** instead of relying on headers
2. **Use file signature validation** (magic bytes) for type checking
3. **Add server-side file type verification**
4. **Implement proper file upload restrictions**

### Long-term Security Measures
1. **Web Application Firewall (WAF)** with upload protection
2. **Regular security audits** of file handling mechanisms
3. **Static code analysis** to identify vulnerable patterns
4. **Security testing** including automated upload bypass detection

## Security Best Practices
- Always validate file content, not just headers
- Implement proper file type restrictions
- Use secure file upload handling
- Regular security assessments and penetration testing
- Implement proper error handling without information disclosure

## File Upload Security Measures
- File content analysis and validation
- File signature verification
- Proper file type restrictions
- Secure file storage and access controls
- Regular security testing and monitoring

## Flag
The exploit successfully bypasses file upload restrictions by manipulating the Content-Type header to obtain the flag.
