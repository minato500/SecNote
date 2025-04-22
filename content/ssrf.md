# SSRF(Server Side Request Forgery)

SSRF occurs when an server side application allows an attacker to make the server perform HTTP requests to internal or external resources on behalf of the attacker. It does this by taking a URL or partial URL from the user and then making a request to that endpoint often the application will then process the results and then return some data back to the user

## Reasons of SSRF

1. Accept the user supplied URL or hostname
2. Make a server side request based on that URL given by the user
3. Does not validate the destination

## Attacker point of view

1. External SSRF

Making requests to the external domain and can be used to scan internet services

Example: http://victim_url/fetch?url=http://attacker.com/malware.js

2. Internal SSRF

Access to the internal networks such as 127.0.0.1, 192.162.x.x,10.x.x.x to reach internal admin panels, DB console,etc. Sometime leads to Remote Code Execution(RCE)

## Type of SSRF

1. Blind SSRF

It is similar to blind SQL Injection attack, in this case of Blind Server Side Request Forgery, we won't be able to view the results of our payload in the HTTP response and a lot of them might take some time to timeout, or they might instantly come back saying that it doesn't exist

In other cases the endpoint of probing for might exist and the timing of response may be differ

## Prevention

1. Input Validation

Only allowing specific domain in the whitelisting, rejecting IP addresses directly such as 127.0.0.1, reject malformed or encoded inputs

2. Disable Unused Protocols

Block file://,gopher://,ftp:// unless it is needed
