Introduction
========
This is a port of [jsrsasign](https://github.com/kjur/jsrsasign) modified to work with demandware.
Many things have been thrown out in order to make it easier to work with (for example only SHA1 digest is supported).

The rest is mostly copy paste.

Notes
=====
Please note that this code seems to perform very poorly and that there is a request with demandware to provide a native implementation.
If you plane to use this make sure to also vote for the idea on [xchange](https://xchange.demandware.com/ideas/1849)

Pull requests are welcome! :)

Usage Sample
=========
```
importPackage( dw.system );
importPackage( dw.crypto );
importPackage( dw.util );

importScript( 'crypto/base64.ds' );
importScript( 'crypto/asn1hex.ds' );
importScript( 'crypto/rsa.ds' );
importScript( 'crypto/BigInteger.ds' );
importScript( 'crypto/sha1.ds' );

function execute( args : PipelineDictionary ) : Number
{

    var a : String = '1234567890abcdef';
    var b = hex2b64(a);
    var c = b64tohex(b);
    
var pub = 'MII...QAB';

    var priv = "-----BEGIN RSA PRIVATE KEY-----\
MIIC....SuVM=\
-----END RSA PRIVATE KEY-----";


  var r : Object = new RSAKey();
r.readPrivateKeyFromPEMString(priv);


var s = 'Test'
var base64_encoded_digest = b64_sha1(s);
var hSig = r.signString(base64_encoded_digest, "sha1");
  
       return PIPELET_NEXT;
}
```

Other
===
See License.txt
