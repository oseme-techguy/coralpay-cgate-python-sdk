CoralPay Python SDK for PGP Encryption on CoralPay's C'Gate
============================================================

This is the Python SDK for integrating with CoralPay's Cgate USSD payment gateway. 
It handles the encryption of the requests to C'Gate and the decryption of the response from C'Gate.  

It uses the imported C'Gate public PGP key for the encryption and it uses your private PGP key and Passphrase for Decrypting the responses from C'Gate.  
  
This SDK has a hard dependency on GnuPG and runs on Windows and Unix-based machines.


----------  
  
  
Get code running
-------------

Make sure you have python3 installed on the machine.

> **Steps:**
> - Set up your virtual environment
> - Make sure you have pip installed
> - Run ```pip install pipenv==2018.6.25```
> - Then Run ```pip install pip==18.0```
> - then run ```pipenv install```

----------
  


### Installation

coralpay-cgate-python-sdk requires gpg to be installed on the environment to run.



```sh
$ pip install --save oseme-techguy/coralpay-cgate-python-sdk
```

### Usage


```python
pgp_object = CoralPayPGPEncryption('/path/to/home/directory/.gnupg')
```

#### Instantiate
```python
pgp_object = CoralPayPGPEncryption('/path/to/home/directory/.gnupg')
```



#### Using SDK Encrypt Method
```python
data = { Amount: 1200, Channel: "WEB", TraceID: "1234567890" }
data = str(data)
key_id = "the-fingerprint-for-cgate-public-key-here"
result = pgp_object.encrypt_request(data, key_id, False, True)
```

#### Using SDK Decrypt Method
```python
data = "85010C0363B256F42F0382020108009EA68E0FECCA50539E34D51ED22232D2C3CD16E7C70CBD928A09EF7FFEE928E47BFC4455E3C83FF7B8BE533A88BAB554246B75C1C94C22073B2EBA392C187F9DEC4B3B10DB9C0272C9969DE96B3E0D6EA70919B80843491E99BEC2D7033FE53DB471838CF3D01FFEBA2F9F12102049C63F1F168BCE7E69C406ED56957841F41102738314A3F23191A768A53CA1DF6A3A063F5E8DE38E1733F4965C028A309242E0391DEB0B27AF79E170E0161D2A405D82BEDDB93A4885C181C4C298F1505F0232A1403EA3BE61009DEB65F6B777778BC238871B196A3BC21033EF0D59BF5EA899379C66D3F39CA93694D26F275090F642F71DFD4D4A8C4C5B2E926220D6BC15C9A3587B91FD054705D4AA026054DDF66923EAB1233C68DE15F97B26E6B0933DB4067B34EA510E22AF25E6FDF78CCEDB99E0785D3A90523948C671687889034F6DCE18809C3683004039DFAB19EFF02CAA6A3AF19AA81F2FB8BAD54D33441904A7CED65D73ACE83F4CB869ABC6534A6949C1962F70046F399EAA1A2209A58921BAD5F86F0BFE5638722BA081462C74E9B1F34D4485A474595D1B62F8E35D0DA2BD4719895D"

key_id = "the-fingerprint-for-your-private-key-here"
passphrase = "the-passphrase-for-your-private-key-here"
result = pgp_object.decrypt_response(data, key_id, passphrase)
```

