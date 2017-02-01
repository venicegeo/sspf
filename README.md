# SSPF

This small script parses the JSON returned from a threadfix server
and returns 1 if the criteria set is higher.

## Example

```
$ curl  --fail --silent 'https://threadfix.yourserver.io/rest/applications/$THREADFIXAPPID?apiKey=$THREADFIXKEY | ./sspf.py
```

**Not complete**
