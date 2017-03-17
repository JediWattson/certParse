# certParse
use for creating keys with sql on google cloud, no copy and paste, just pipe with python
```python
import sys
import json

sc = open("server-ca.pem", 'w')
cc = open("client-cert.pem", 'w')
cp = open("client-key.pem", 'w')



i = ""
for l in sys.stdin:
        i += l


i = json.loads(i)

try:
        sc.write(i["serverCaCert"]["cert"])
        cc.write(i["clientCert"]["certInfo"]["cert"])
        cp.write( i["clientCert"]["certPrivateKey"])
except:
        print i
else:
        print "success"
sc.close()
cc.close()
cp.close()
```
