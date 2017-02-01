# SSPF

This small script parses the JSON returned from a threadfix server
for a project's vulnerabilities and returns 1 if any vulnerabilities
above a certain threshold are found.

Currently, in the `sspf.py`, the threshold criteria is hard-coded:

`criteria = ['highVulnCount', 'criticalVulnCount']`

If the results contain any number other than 0 for `highVulnCount` or
`criticalVulnCount` the return code is 1. Otherwise the return code is 0
which indicates a success.

## Example

```
$ curl  --fail --silent 'https://threadfix.yourserver.io/rest/applications/$THREADFIXAPPID?apiKey=$THREADFIXKEY | ./sspf.py
```

## Implementing within a Jenkins Pipeline

```
...
  stage("Scan Pass/Fail") {
    sh "echo 'Scan Pass/Fail running'"
    git url: "https://github.com/venicegeo/sspf"
    sh  "curl  --fail --silent 'https://threadfix.yourserver.io/rest/applications/$THREADFIXAPPID?apiKey=$THREADFIXKEY | ./sspf.py"
  }
...
```

**Not complete**
