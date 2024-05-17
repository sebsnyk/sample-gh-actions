# Demonstration of snyk-filter & snyk-delta in a Github pipeline

- package.json contains a lot of vulnerable dependencies
- snyk-filter configuration will cause pipeline failure if any vulnerability with CVSS score ABOVE 9.8 is found
- snyk-delta points to a pre-monitored project and will show a minimal diff in dependencies


## To test locally (snyk-filter)

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

## To test locally (snyk-delta)

```
snyk test --json | snyk-delta --baselineOrg $SNYK_ORG --baselineProject $SNYK_PROJECT
```

Sample output:

```

                                uuuuuuuuuuuuuuuuuuuu
                              u" uuuuuuuuuuuuuuuuuu "u
                            u" u$$$$$$$$$$$$$$$$$$$$u "u
                          u" u$$$$$$$$$$$$$$$$$$$$$$$$u "u
                        u" u$$$$$$$$$$$$$$$$$$$$$$$$$$$$u "u
                      u" u$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$u "u
                    u" u$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$u "u
                    $ $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$ $
                    $ $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$ $
                    $ $$$" ... "$...  ...$" ... "$$$  ... "$$$ $
                    $ $$$u `"$$$$$$$  $$$  $$$$$  $$  $$$  $$$ $
                    $ $$$$$$uu "$$$$  $$$  $$$$$  $$  """ u$$$ $
                    $ $$$""$$$  $$$$  $$$u "$$$" u$$  $$$$$$$$ $
                    $ $$$$....,$$$$$..$$$$$....,$$$$..$$$$$$$$ $
                    $ $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$ $
                    "u "$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$" u"
                      "u "$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$" u"
                        "u "$$$$$$$$$$$$$$$$$$$$$$$$$$$$" u"
                          "u "$$$$$$$$$$$$$$$$$$$$$$$$" u"
                            "u "$$$$$$$$$$$$$$$$$$$$" u"
                              "u """""""""""""""""" u"
                                """"""""""""""""""""


New issues introduced !
Security Vulnerabilities:
  1/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => har-validator@2.0.6 => chalk@1.1.3 => has-ansi@2.0.0 => ansi-regex@2.1.1
    Fixed in: ansi-regex 3.0.1, 4.1.1, 5.0.1, 6.0.1
    Fixable by upgrade:  thelounge@3.1.0


  2/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => har-validator@2.0.6 => chalk@1.1.3 => strip-ansi@3.0.1 => ansi-regex@2.1.1
    Fixed in: ansi-regex 3.0.1, 4.1.1, 5.0.1, 6.0.1
    Fixable by upgrade:  thelounge@3.1.0


  3/165: Prototype Pollution [High Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => form-data@1.0.1 => async@2.6.3
    Fixed in: async 2.6.4, 3.2.2
    Fixable by upgrade:  thelounge@3.1.0


  4/165: Remote Memory Exposure [High Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => bl@1.0.3
    Fixed in: bl 2.2.1, 3.0.1, 4.0.3, 1.2.3
    Fixable by upgrade:  thelounge@3.1.0


  5/165: Denial of Service (DoS) [High Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => engine.io@1.3.1
    Fixed in: engine.io 4.0.0
    Fixable by upgrade:  thelounge@4.3.0=>socket.io@3.1.2=>engine.io@4.1.2


  6/165: Denial of Service (DoS) [High Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => engine.io@1.3.1
    Fixed in: engine.io 3.6.1, 6.2.1
    Fixable by upgrade:  thelounge@4.4.0=>socket.io@4.6.1=>engine.io@6.4.2


  7/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  8/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  9/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  10/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  11/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  12/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  13/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  14/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  15/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  16/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  17/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  18/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  19/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  20/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  21/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  22/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  23/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  24/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  25/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  26/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  27/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  28/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  29/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  30/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  31/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  32/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  33/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  34/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  35/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  36/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  37/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  38/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  39/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  40/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  41/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es6-iterator@2.0.3 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  42/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es6-iterator@2.0.3 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  43/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-iterator@2.0.3 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  44/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-iterator@2.0.3 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  45/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  46/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  47/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  48/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  49/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  50/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  51/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  52/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  53/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  54/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  55/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  56/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  57/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es6-symbol@3.1.1 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  58/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es6-symbol@3.1.1 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  59/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => event-emitter@0.3.5 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  60/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => event-emitter@0.3.5 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  61/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => event-emitter@0.3.5 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  62/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => event-emitter@0.3.5 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  63/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  64/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  65/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  66/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  67/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  68/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  69/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  70/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  71/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  72/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  73/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  74/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  75/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es6-iterator@2.0.3 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  76/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es6-iterator@2.0.3 => es5-ext@0.10.53 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  77/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  78/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  79/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  80/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  81/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  82/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  83/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  84/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  85/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  86/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  87/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  88/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  89/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es6-symbol@3.1.1 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  90/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es6-symbol@3.1.1 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  91/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => event-emitter@0.3.5 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  92/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => event-emitter@0.3.5 => d@1.0.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  93/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  94/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => es6-symbol@3.1.1 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  95/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => fontkit@1.8.1 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>fontkit@1.9.0


  96/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: pdfkit@0.11.0 => linebreak@1.0.2 => brfs@2.0.2 => static-module@3.0.4 => scope-analyzer@2.1.2 => es6-map@0.1.5 => es6-set@0.1.5 => event-emitter@0.3.5 => es5-ext@0.10.53 => es6-iterator@2.0.3 => es6-symbol@3.1.3 => d@1.0.1 => es5-ext@0.10.53
    Fixed in: es5-ext 0.10.63
    Fixable by upgrade:  pdfkit@0.11.0=>linebreak@1.1.0


  97/165: Open Redirect [Medium Severity]
    Via: thelounge@1.0.1 => express@4.13.4
    Fixed in: express 4.19.2, 5.0.0-beta.3


  98/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => hawk@3.1.3
    Fixed in: hawk 9.0.1
    Fixable by upgrade:  thelounge@3.1.0


  99/165: Regular Expression Denial of Service (ReDoS) [Medium Severity]
    Via: thelounge@1.0.1 => lodash@2.4.2
    Fixed in: lodash 4.17.21
    Fixable by upgrade:  thelounge@4.3.0=>lodash@4.17.21


  100/165: Command Injection [High Severity]
    Via: thelounge@1.0.1 => lodash@2.4.2
    Fixed in: lodash 4.17.21
    Fixable by upgrade:  thelounge@4.3.0=>lodash@4.17.21


  101/165: Prototype Pollution [High Severity]
    Via: thelounge@1.0.1 => lodash@2.4.2
    Fixed in: lodash 4.17.12
    Fixable by upgrade:  thelounge@3.1.0=>lodash@4.17.14


  102/165: Prototype Pollution [High Severity]
    Via: thelounge@1.0.1 => lodash@2.4.2
    Fixed in: lodash 4.17.17
    Fixable by upgrade:  thelounge@4.2.0=>lodash@4.17.20


  103/165: Prototype Pollution [High Severity]
    Via: thelounge@1.0.1 => lodash@2.4.2
    Fixed in: lodash 4.17.17
    Fixable by upgrade:  thelounge@4.2.0=>lodash@4.17.20


  104/165: Prototype Pollution [High Severity]
    Via: thelounge@1.0.1 => lodash@2.4.2
    Fixed in: lodash 4.17.11
    Fixable by upgrade:  thelounge@3.0.0=>lodash@4.17.11


  105/165: Regular Expression Denial of Service (ReDoS) [Medium Severity]
    Via: thelounge@1.0.1 => lodash@2.4.2
    Fixed in: lodash 4.17.11
    Fixable by upgrade:  thelounge@3.0.0=>lodash@4.17.11


  106/165: Prototype Pollution [Medium Severity]
    Via: thelounge@1.0.1 => lodash@2.4.2
    Fixed in: lodash 4.17.5
    Fixable by upgrade:  thelounge@2.7.1=>lodash@4.17.5


  107/165: Prototype Pollution [Low Severity]
    Via: thelounge@1.0.1 => mkdirp@0.5.1 => minimist@0.0.8
    Fixed in: minimist 0.2.4, 1.2.6
    Fixable by upgrade:  thelounge@2.0.0


  108/165: Prototype Pollution [Medium Severity]
    Via: thelounge@1.0.1 => mkdirp@0.5.1 => minimist@0.0.8
    Fixed in: minimist 0.2.1, 1.2.3
    Fixable by upgrade:  thelounge@2.0.0


  109/165: Directory Traversal [High Severity]
    Via: thelounge@1.0.1 => moment@2.11.2
    Fixed in: moment 2.29.2
    Fixable by upgrade:  thelounge@3.0.0


  110/165: Regular Expression Denial of Service (ReDoS) [Medium Severity]
    Via: thelounge@1.0.1 => moment@2.11.2
    Fixed in: moment 2.15.2
    Fixable by upgrade:  thelounge@2.2.0=>moment@2.17.1


  111/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => moment@2.11.2
    Fixed in: moment 2.19.3
    Fixable by upgrade:  thelounge@2.7.0=>moment@2.20.1


  112/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: thelounge@1.0.1 => cheerio@0.20.0 => css-select@1.2.0 => nth-check@1.0.2
    Fixed in: nth-check 2.0.1


  113/165: Prototype Poisoning [High Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => qs@4.0.0
    Fixed in: qs 6.2.4, 6.3.3, 6.4.1, 6.5.3, 6.6.1, 6.7.3, 6.8.3, 6.9.7, 6.10.3
    Fixable by upgrade:  thelounge@4.3.1=>express@4.17.3=>qs@6.9.7


  114/165: Prototype Override Protection Bypass [High Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => qs@4.0.0
    Fixed in: qs 6.0.4, 6.1.2, 6.2.3, 6.3.2
    Fixable by upgrade:  thelounge@2.2.2=>express@4.15.2=>qs@6.4.0


  115/165: Prototype Poisoning [High Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => qs@6.0.4
    Fixed in: qs 6.2.4, 6.3.3, 6.4.1, 6.5.3, 6.6.1, 6.7.3, 6.8.3, 6.9.7, 6.10.3
    Fixable by upgrade:  thelounge@3.1.0


  116/165: Server-side Request Forgery (SSRF) [Medium Severity]
    Via: thelounge@1.0.1 => cheerio@0.20.0 => jsdom@7.2.2 => request@2.88.2
    Fixed in: request
    Fixable by upgrade:  thelounge@2.2.0=>cheerio@0.22.0


  117/165: Server-side Request Forgery (SSRF) [Medium Severity]
    Via: thelounge@1.0.1 => request@2.69.0
    Fixed in: request
    Fixable by upgrade:  thelounge@3.1.0


  118/165: Insecure Defaults [Medium Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6
    Fixed in: socket.io 2.4.0
    Fixable by upgrade:  thelounge@4.3.0=>socket.io@3.1.2


  119/165: Denial of Service (DoS) [High Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-adapter@0.2.0 => socket.io-parser@2.1.2
    Fixed in: socket.io-parser 3.3.2, 3.4.1
    Fixable by upgrade:  thelounge@2.6.0=>socket.io@2.0.4=>socket.io-adapter@1.1.2


  120/165: Improper Input Validation [Critical Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-adapter@0.2.0 => socket.io-parser@2.1.2
    Fixed in: socket.io-parser 3.3.3, 3.4.2, 4.0.5, 4.2.1
    Fixable by upgrade:  thelounge@2.6.0=>socket.io@2.0.4=>socket.io-adapter@1.1.2


  121/165: Denial of Service (DoS) [High Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-parser@2.2.0
    Fixed in: socket.io-parser 3.3.2, 3.4.1
    Fixable by upgrade:  thelounge@3.0.0=>socket.io@2.2.0=>socket.io-parser@3.3.3


  122/165: Improper Input Validation [Critical Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-parser@2.2.0
    Fixed in: socket.io-parser 3.3.3, 3.4.2, 4.0.5, 4.2.1
    Fixable by upgrade:  thelounge@3.0.0=>socket.io@2.2.0=>socket.io-parser@3.3.3


  123/165: Denial of Service (DoS) [High Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-client@1.0.6 => socket.io-parser@2.2.0
    Fixed in: socket.io-parser 3.3.2, 3.4.1
    Fixable by upgrade:  thelounge@3.0.0=>socket.io@2.2.0=>socket.io-client@2.2.0=>socket.io-parser@3.3.3


  124/165: Improper Input Validation [Critical Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-client@1.0.6 => socket.io-parser@2.2.0
    Fixed in: socket.io-parser 3.3.3, 3.4.2, 4.0.5, 4.2.1
    Fixable by upgrade:  thelounge@3.0.0=>socket.io@2.2.0=>socket.io-client@2.2.0=>socket.io-parser@3.3.3


  125/165: Information Exposure [Medium Severity]
    Via: thelounge@1.0.1
    Fixed in: thelounge


  126/165: Cross-site Scripting (XSS) [Medium Severity]
    Via: thelounge@1.0.1
    Fixed in: thelounge 1.5.0
    Fixable by upgrade:  thelounge@1.5.0


  127/165: Prototype Pollution [Medium Severity]
    Via: thelounge@1.0.1 => cheerio@0.20.0 => jsdom@7.2.2 => tough-cookie@2.5.0
    Fixed in: tough-cookie 4.1.3
    Fixable by upgrade:  thelounge@2.2.0=>cheerio@0.22.0


  128/165: Prototype Pollution [Medium Severity]
    Via: thelounge@1.0.1 => cheerio@0.20.0 => jsdom@7.2.2 => request@2.88.2 => tough-cookie@2.5.0
    Fixed in: tough-cookie 4.1.3
    Fixable by upgrade:  thelounge@2.2.0=>cheerio@0.22.0


  129/165: Prototype Pollution [Medium Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => tough-cookie@2.2.2
    Fixed in: tough-cookie 4.1.3
    Fixable by upgrade:  thelounge@3.1.0


  130/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => tough-cookie@2.2.2
    Fixed in: tough-cookie 2.3.0
    Fixable by upgrade:  thelounge@3.1.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:tough-cookie:20160722:0


  131/165: Regular Expression Denial of Service (ReDoS) [Medium Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => tough-cookie@2.2.2
    Fixed in: tough-cookie 2.3.3
    Fixable by upgrade:  thelounge@3.1.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:tough-cookie:20170905:0, patch:npm:tough-cookie:20170905:1, patch:npm:tough-cookie:20170905:2


  132/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => cheerio@0.20.0 => jsdom@7.2.2 => escodegen@1.14.3 => optionator@0.8.3 => word-wrap@1.2.3
    Fixed in: word-wrap 1.2.4
    Fixable by upgrade:  thelounge@1.0.1=>cheerio@0.20.0=>jsdom@7.2.2=>escodegen@1.14.3=>optionator@0.8.3=>word-wrap@1.2.5


  133/165: Regular Expression Denial of Service (ReDoS) [Medium Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => engine.io@1.3.1 => ws@0.4.31
    Fixed in: ws 7.4.6, 6.2.2, 5.2.3
    Fixable by upgrade:  thelounge@3.3.0=>socket.io@2.3.0=>engine.io@3.4.2=>ws@7.5.9


  134/165: Remote Memory Exposure [Medium Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => engine.io@1.3.1 => ws@0.4.31
    Fixed in: ws 1.0.1
    Fixable by upgrade:  thelounge@1.4.0=>socket.io@1.4.5=>engine.io@1.6.8=>ws@1.0.1
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:ws:20160104:0, patch:npm:ws:20160104:1, patch:npm:ws:20160104:2, patch:npm:ws:20160104:3


  135/165: Denial of Service (DoS) [High Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => engine.io@1.3.1 => ws@0.4.31
    Fixed in: ws 1.1.1
    Fixable by upgrade:  thelounge@2.2.0=>socket.io@1.7.2=>engine.io@1.8.2=>ws@1.1.1


  136/165: Insecure Randomness [Medium Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => engine.io@1.3.1 => ws@0.4.31
    Fixed in: ws 1.1.2
    Fixable by upgrade:  thelounge@2.2.2=>socket.io@1.7.3=>engine.io@1.8.3=>ws@1.1.2
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:ws:20160920:0


  137/165: Denial of Service (DoS) [High Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => engine.io@1.3.1 => ws@0.4.31
    Fixed in: ws 1.1.5, 3.3.1
    Fixable by upgrade:  thelounge@2.4.0=>socket.io@1.7.4=>engine.io@1.8.5=>ws@1.1.5


  138/165: Regular Expression Denial of Service (ReDoS) [Medium Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-client@1.0.6 => engine.io-client@1.3.1 => ws@0.4.31
    Fixed in: ws 7.4.6, 6.2.2, 5.2.3
    Fixable by upgrade:  thelounge@4.3.0=>socket.io@3.1.2


  139/165: Remote Memory Exposure [Medium Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-client@1.0.6 => engine.io-client@1.3.1 => ws@0.4.31
    Fixed in: ws 1.0.1
    Fixable by upgrade:  thelounge@1.4.0=>socket.io@1.4.5=>socket.io-client@1.4.5=>engine.io-client@1.6.8=>ws@1.0.1
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:ws:20160104:0, patch:npm:ws:20160104:1, patch:npm:ws:20160104:2, patch:npm:ws:20160104:3


  140/165: Denial of Service (DoS) [High Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-client@1.0.6 => engine.io-client@1.3.1 => ws@0.4.31
    Fixed in: ws 1.1.1
    Fixable by upgrade:  thelounge@2.2.0=>socket.io@1.7.2=>socket.io-client@1.7.2=>engine.io-client@1.8.2=>ws@1.1.1


  141/165: Insecure Randomness [Medium Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-client@1.0.6 => engine.io-client@1.3.1 => ws@0.4.31
    Fixed in: ws 1.1.2
    Fixable by upgrade:  thelounge@2.2.2=>socket.io@1.7.3=>socket.io-client@1.7.3=>engine.io-client@1.8.3=>ws@1.1.2
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:ws:20160920:0


  142/165: Denial of Service (DoS) [High Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-client@1.0.6 => engine.io-client@1.3.1 => ws@0.4.31
    Fixed in: ws 1.1.5, 3.3.1
    Fixable by upgrade:  thelounge@2.4.0=>socket.io@1.7.4=>socket.io-client@1.7.4=>engine.io-client@1.8.6=>ws@1.1.5


  143/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => debug@2.2.0
    Fixed in: debug 2.6.9, 3.1.0, 3.2.7, 4.3.1
    Fixable by upgrade:  thelounge@2.5.0=>express@4.16.0=>debug@2.6.9
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:debug:20170905:0, patch:npm:debug:20170905:1, patch:npm:debug:20170905:2, patch:npm:debug:20170905:3


  144/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => finalhandler@0.4.1 => debug@2.2.0
    Fixed in: debug 2.6.9, 3.1.0, 3.2.7, 4.3.1
    Fixable by upgrade:  thelounge@2.2.2=>express@4.15.2=>finalhandler@1.0.6=>debug@2.6.9
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:debug:20170905:0, patch:npm:debug:20170905:1, patch:npm:debug:20170905:2, patch:npm:debug:20170905:3


  145/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => send@0.13.1 => debug@2.2.0
    Fixed in: debug 2.6.9, 3.1.0, 3.2.7, 4.3.1
    Fixable by upgrade:  thelounge@2.5.0=>express@4.16.0=>send@0.16.0=>debug@2.6.9
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:debug:20170905:0, patch:npm:debug:20170905:1, patch:npm:debug:20170905:2, patch:npm:debug:20170905:3


  146/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => serve-static@1.10.3 => send@0.13.2 => debug@2.2.0
    Fixed in: debug 2.6.9, 3.1.0, 3.2.7, 4.3.1
    Fixable by upgrade:  thelounge@2.5.0=>express@4.16.0=>serve-static@1.13.0=>send@0.16.0=>debug@2.6.9
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:debug:20170905:0, patch:npm:debug:20170905:1, patch:npm:debug:20170905:2, patch:npm:debug:20170905:3


  147/165: Insecure Defaults [High Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-client@1.0.6 => engine.io-client@1.3.1
    Fixed in: engine.io-client 1.6.9
    Fixable by upgrade:  thelounge@2.2.0=>socket.io@1.7.2=>socket.io-client@1.7.2=>engine.io-client@1.8.2


  148/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => fresh@0.3.0
    Fixed in: fresh 0.5.2
    Fixable by upgrade:  thelounge@2.5.0=>express@4.16.0=>fresh@0.5.2


  149/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => send@0.13.1 => fresh@0.3.0
    Fixed in: fresh 0.5.2
    Fixable by upgrade:  thelounge@2.5.0=>express@4.16.0=>send@0.16.0=>fresh@0.5.2


  150/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => serve-static@1.10.3 => send@0.13.2 => fresh@0.3.0
    Fixed in: fresh 0.5.2
    Fixable by upgrade:  thelounge@2.5.0=>express@4.16.0=>serve-static@1.13.0=>send@0.16.0=>fresh@0.5.2


  151/165: Prototype Pollution [Medium Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => hawk@3.1.3 => hoek@2.16.3
    Fixed in: hoek 4.2.1, 5.0.3
    Fixable by upgrade:  thelounge@3.1.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:hoek:20180212:0, patch:npm:hoek:20180212:1


  152/165: Prototype Pollution [Medium Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => hawk@3.1.3 => boom@2.10.1 => hoek@2.16.3
    Fixed in: hoek 4.2.1, 5.0.3
    Fixable by upgrade:  thelounge@3.1.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:hoek:20180212:0, patch:npm:hoek:20180212:1


  153/165: Prototype Pollution [Medium Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => hawk@3.1.3 => sntp@1.0.9 => hoek@2.16.3
    Fixed in: hoek 4.2.1, 5.0.3
    Fixable by upgrade:  thelounge@3.1.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:hoek:20180212:0, patch:npm:hoek:20180212:1


  154/165: Prototype Pollution [Medium Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => hawk@3.1.3 => cryptiles@2.0.5 => boom@2.10.1 => hoek@2.16.3
    Fixed in: hoek 4.2.1, 5.0.3
    Fixable by upgrade:  thelounge@3.1.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:hoek:20180212:0, patch:npm:hoek:20180212:1


  155/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => send@0.13.1 => mime@1.3.4
    Fixed in: mime 1.4.1, 2.0.3
    Fixable by upgrade:  thelounge@2.5.0=>express@4.16.0=>send@0.16.0=>mime@1.4.1
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:mime:20170907:0


  156/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => serve-static@1.10.3 => send@0.13.2 => mime@1.3.4
    Fixed in: mime 1.4.1, 2.0.3
    Fixable by upgrade:  thelounge@2.5.0=>express@4.16.0=>serve-static@1.13.0=>send@0.16.0=>mime@1.4.1
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:mime:20170907:0


  157/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => debug@2.2.0 => ms@0.7.1
    Fixed in: ms 2.0.0
    Fixable by upgrade:  thelounge@2.4.0=>express@4.15.3=>debug@2.6.7=>ms@2.0.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:ms:20170412:0, patch:npm:ms:20170412:1, patch:npm:ms:20170412:2


  158/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => send@0.13.1 => ms@0.7.1
    Fixed in: ms 2.0.0
    Fixable by upgrade:  thelounge@2.4.0=>express@4.15.3=>send@0.15.3=>ms@2.0.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:ms:20170412:0, patch:npm:ms:20170412:1, patch:npm:ms:20170412:2


  159/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => finalhandler@0.4.1 => debug@2.2.0 => ms@0.7.1
    Fixed in: ms 2.0.0
    Fixable by upgrade:  thelounge@2.2.2=>express@4.15.2=>finalhandler@1.0.6=>debug@2.6.9=>ms@2.0.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:ms:20170412:0, patch:npm:ms:20170412:1, patch:npm:ms:20170412:2


  160/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => send@0.13.1 => debug@2.2.0 => ms@0.7.1
    Fixed in: ms 2.0.0
    Fixable by upgrade:  thelounge@2.4.0=>express@4.15.3=>send@0.15.3=>debug@2.6.7=>ms@2.0.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:ms:20170412:0, patch:npm:ms:20170412:1, patch:npm:ms:20170412:2


  161/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => serve-static@1.10.3 => send@0.13.2 => ms@0.7.1
    Fixed in: ms 2.0.0
    Fixable by upgrade:  thelounge@2.4.0=>express@4.15.3=>serve-static@1.12.3=>send@0.15.3=>ms@2.0.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:ms:20170412:0, patch:npm:ms:20170412:1, patch:npm:ms:20170412:2


  162/165: Regular Expression Denial of Service (ReDoS) [Low Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => serve-static@1.10.3 => send@0.13.2 => debug@2.2.0 => ms@0.7.1
    Fixed in: ms 2.0.0
    Fixable by upgrade:  thelounge@2.4.0=>express@4.15.3=>serve-static@1.12.3=>send@0.15.3=>debug@2.6.7=>ms@2.0.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:ms:20170412:0, patch:npm:ms:20170412:1, patch:npm:ms:20170412:2


  163/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: thelounge@1.0.1 => express@4.13.4 => accepts@1.2.13 => negotiator@0.5.3
    Fixed in: negotiator 0.6.1
    Fixable by upgrade:  thelounge@2.2.0=>express@4.14.0=>accepts@1.3.8=>negotiator@0.6.3
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:negotiator:20160616:0, patch:npm:negotiator:20160616:1, patch:npm:negotiator:20160616:2, patch:npm:negotiator:20160616:3


  164/165: Regular Expression Denial of Service (ReDoS) [High Severity]
    Via: thelounge@1.0.1 => socket.io@1.0.6 => socket.io-client@1.0.6 => engine.io-client@1.3.1 => parsejson@0.0.1
    Fixed in: parsejson
    Fixable by upgrade:  thelounge@2.6.0=>socket.io@2.0.4=>socket.io-client@2.0.4=>engine.io-client@3.1.6


  165/165: Uninitialized Memory Exposure [Medium Severity]
    Via: thelounge@1.0.1 => request@2.69.0 => tunnel-agent@0.4.3
    Fixed in: tunnel-agent 0.6.0
    Fixable by upgrade:  thelounge@3.1.0
    Fixable by patch (​https://support.snyk.io/hc/en-us/articles/360003891078-Snyk-patches-to-fix​) :  patch:npm:tunnel-agent:20170305:0
```