# Local File Inclusion (LFI) Exploit

## Vulnerability Description
This exploit demonstrates a **Local File Inclusion (LFI)** vulnerability where the application allows arbitrary file access through path traversal techniques, enabling access to sensitive system files.

## Attack Methodology

### Reconnaissance
- Identify the vulnerable parameter (page parameter)
- Analyze the file inclusion mechanism
- Determine the base directory structure
- Map the application's file handling logic

### Exploitation Steps
1. **Identify the vulnerable endpoint** that accepts file paths
2. **Analyze the path handling** to understand directory traversal possibilities
3. **Construct path traversal payload** using `../` sequences
4. **Target sensitive system files** like `/etc/passwd`
5. **Execute the payload**: `http://localhost:8080/?page=../../../../../../../../../etc/passwd`

### Technical Details
- **Vulnerability Type**: Local File Inclusion (LFI)
- **Attack Vector**: Path Traversal
- **Payload**: `../../../../../../../../../etc/passwd`
- **Impact**: Unauthorized access to sensitive system files
- **Difficulty Level**: Medium

## Root Cause Analysis
The application fails to properly validate and sanitize file path inputs, allowing directory traversal sequences to access files outside the intended directory scope.

## Mitigation Strategies

### Immediate Fixes
1. **Implement strict input validation** for file paths
2. **Use whitelist approach** for allowed files/directories
3. **Normalize and validate paths** before file operations
4. **Implement proper error handling** without information disclosure

### Long-term Security Measures
1. **Web Application Firewall (WAF)** with LFI protection
2. **Regular security audits** of file handling code
3. **Static code analysis** to identify vulnerable patterns
4. **Security testing** including automated LFI detection

## Security Best Practices
- Always validate and sanitize file path inputs
- Use absolute paths with proper validation
- Implement file access controls and permissions
- Regular security assessments and penetration testing
- Use security headers and proper error handling

## Common LFI Payloads
- `/etc/passwd` - User account information
- `/etc/hosts` - Host file
- `/proc/version` - System version information
- `/var/log/apache2/access.log` - Web server logs

## Flag
The exploit successfully accesses sensitive system files through path traversal to obtain the flag.