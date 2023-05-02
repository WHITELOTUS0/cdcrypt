# cdrypt

## This package encrpts and decrypts data(string format)

## Installation
```zsh
npm install cdcrypt
```

## How it works

 It uses the **crypto** module built into Node.js to perform AES-256-CBC encryption and decryption. 
 It has two functions: **encrypt** and **decrypt**

 The **encrypt** function takes a string as input and returns an object with two properties: **iv**, which is the initialization vector used in the encryption process, and **encryptedData**, which is the encrypted data as a hex string

 The **decrypt** function takes the encrypted object as input and returns the decrypted string. It first converts the **iv** and **encryptedData** properties from hex strings to buffers, and then uses the **crypto.createDecipheriv()** method to create a decipher object. The **update()** method is called with the encrypted text as input, and then the **final()** method is called to complete the decryption process. The resulting buffer is then converted to a string using the **toString()** method.

 The example usage at the bottom of the code shows how to use the **encrypt** and **decrypt** functions. The original text is encrypted and then decrypted, and the original and decrypted texts are logged to the console for verification

### Example Usage
```javascript
const cdcrypt = require("cdcrypt")


let originalText = 'This is a secret message';
let encryptedText = cdcrypt.encrypt(originalText);
let decryptedText = cdcrypt.decrypt(encryptedText);
console.log('Original Text:', originalText);
console.log('Encrypted Text:', encryptedText);
console.log('Decrypted Text:', decryptedText);
```

### Output
```console
Original Text: This is a secret message
Encrypted Text: {
  iv: '84ab48f30e98b91e56fd389a4233b40c',
  encryptedData: 'c98e79f0abee86d7a249cd55dc5b2773b2ee96840c23ffd3a908fce55cef4bcd'
}
Decrypted Text: This is a secret message
```