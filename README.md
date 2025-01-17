# Domination-File-Traversal

The Domination Web Server (Versions 2.3 and below) has a critical vulnerability related to file path traversal that poses a significant risk to its users. Specifically, this attack allows unauthorized access to arbitrary files on the server by manipulating the URL path filename.

During testing, it was determined that when submitting the payload %2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5c%2e%2e%5cwindows%5cwin.ini to the endpoint at http://89.232.192.133:8808/html/js/kinetic-v4.5.4.min.js, the application responds with the contents of the requested win.ini file. This demonstrates a clear lack of input validation that allows an attacker to traverse the file system beyond the intended directory. Further investigation identified several other endpoints susceptible to similar exploitation, including:

- /html/js/kinetic-v4.5.4.min.js
- /html/css/default.css
- /html/css/jquery.selectbox.css

These vulnerable endpoints can potentially expose sensitive information, ranging from configuration settings to user credentials and application source code. Path traversal vulnerabilities occur when user input is mishandled during filesystem operations, allowing malicious actors to exploit the directory structure of the server with relative ease. This can lead to unauthorized access to sensitive information such as configuration files, passwords, and other crucial data. However, the implications of this vulnerability extend beyond immediate data exposure. An attacker could leverage the information gained to mount further attacks, escalate privileges, or compromise the integrity of the entire server. Even more alarming, this type of vulnerability can be automated, making it a preferred target for malicious agents seeking to exploit system weaknesses on a larger scale.
