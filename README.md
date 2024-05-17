# Demonstration of snyk-filter in a Github pipeline

- package.json contains a lot of vulnerable dependencies
- snyk-filter configuration will cause pipeline failure if any vulnerability with CVSS score ABOVE 9.8 is found


## To test locally

```
snyk test --json | snyk-filter
```

Sample output:

```
Testing snyk-filter...
✗ Critical severity vulnerability found on vm2@3.9.3
- desc: Sandbox Bypass
- info: https://snyk.io/vuln/SNYK-JS-VM2-3018201
- from: juice-shop@12.3.0 > juicy-chat-bot@0.6.5 > vm2@3.9.3


✗ Critical severity vulnerability found on vm2@3.9.3
- desc: Sandbox Escape
- info: https://snyk.io/vuln/SNYK-JS-VM2-5415299
- from: juice-shop@12.3.0 > juicy-chat-bot@0.6.5 > vm2@3.9.3


Organisation: checks
Licenses enabled

Tested 913 dependencies for known issues
juice-shop - Vulnerabilities with CVSS Score of 9.9+ found
Snyk Test Failed
```