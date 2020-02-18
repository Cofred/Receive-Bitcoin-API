# Bitcoin Receive Payment API

# Using this API merchant will be able to implement Bitcoin receive using their merchant account details.

HTTP Method: POST

# Resource Url

https://cofredpay.com/api/v1/receive_btc

# Headers

See our Guide for how to setup Header https://github.com/cofred/Header-Authentication

# Authentication Headers Example

merchant_id: VF9CMTY3WURPZUpJdkNnVWJWRXE=   // Base64 Encoded

secret_code: I8AtLUljNqcdS4F76OVy2Zf1bJvGwsP95rE

terminal_id: YINCU

access_token: dUp4dEtybVg0Ump4MEFT  // Base64 Encoded

timestamp: 1505628722 // Current Time in Unix Format

# Request Parameters

Field	M/O	Format	Description

callback_url	M	 URL On this url you will receive payment notifications

Reference	M		Alpha Numeric	Merchant Reference ID
				
# DoPayment Response

A HTTP response code 200 is sent back for a success

# Response Parameters

Field	Description

responseCode	Response Code

reference	Reference ID sent by merchant

address	Generated Bitcoin address

qr_imageurl	QR Image link for generated address

# Sample Response

200

{
  "responseCode":"200",
  "responseMessage":"Transaction successfull!",
  "reference":356789323,
  "address":"13VnRDeJan5smLTkZzwBdZjDv6F3LYpS6R",
  "qr_imageurl":"Image URL here..."
}

# Communication

Requests will be sent over the REST protocol using POST Method.

# Process to receive callback

Once payment received on the address we will send callback response on the given url.

Callback is sent by POST method in Json format.

Callback sample

{ 
"address":"13VnRDeJan5smLTkZzwBdZjDv6F3LYpS6R",
"amount":"0.001", 
"reference":"356789323", 
"hash":Bitcoin Transaction Hash, 
"confirmations":'0 or 1' 
}

Params Details

address - Receiving Address
amount - Received amount in BTC
reference - Reference sent by Merchant
hash - Bitcoin generated Hash ID
confirmations - 0 For transaction intiated and 1 for Transaction approved and Credit to your merchant account
