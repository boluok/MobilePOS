# Thames

An Android application that enables you to collect payment with card either using the app directly or calling on the app from your own android app to process payment for you.

## Setup

Download the Thames apk and follow the following steps to setup:

1. Click Admin and setup an admin password
2. Click Termianl Identification and set your terminal Id
3. Click Set Terminal Parameters and fill appropriately 
4. Click Communications then click configure host select 'RUBIES LIVE' and proceed
5. Click Key Download and click load keys once you get response "Keys loaded succesfully" you are all set and good to go.


### Connecting from your own application

To initiate payment with card from your own app at the point of transaction call on Thames with the amount

NOTE: If amount is not passed the user will be given the option to enter their own amount
```
val intent = Intent("com.thames.pos.CardPayment")
            intent.putExtra("amount","200")
            startActivityForResult( intent,CARD_PAYMENT_RESULT_CODE);
```

Receive result in onActivity for result:

```
override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent?) {
        super.onActivityResult(requestCode, resultCode, data)
        val result = data
        val responseCode = result?.getStringExtra("responseCode")
        val responseMessage = result?.getStringExtra("responseMessage")
        val amount = result?.getStringExtra("amount")
        val ref = result?.getStringExtra("ref")
    }
```

### Responses
You can get the following responses after a transaction:

| Response Code | Description/Format                                                              |
| --------------- | ------------------------------------------------------------------------------- |
| 00          | Approved |
| 01         | Refer to card Issuer|
| 02          | Refer to card Issuer |
| 03         | Invalid Merchant|
| 04          | Pick-up card |
| 05         | Do not honor|
| 06          | Error |
| 07         | Pick-up Card|
| 08          | Honor with identification |
| 09         | Request in progress|
| 10          | Partially Approved |
| 11         | Approved, VIP|
| 12          | Invalid Transaction |
| 13         | Invalid Amount|
| 14          | Invalid card number |
| 15         | No such issuer|
| 16          | Approved, update track 3 |
| 17         | Customer cancellation|
| 18          | Customer Dispute |
| 19         | Re-enter transaction|
| 20          | Invalid response |
| 21         | No action taken|
| 22          | Suspected malfunction |
| 23         | Unacceptable transaction fee|
| 24          | File update not supported |
| 25         | Unable to locate record|
| 26          | Duplicate record |
| 27         | File update edit error|
| 28          | File update file locked |
| 29         | File update failed|
| 30          | Format error |
| 31         | Bank not supported|
| 32          | Approved |
| 33         | Completed, partially|
| 34          | Expired card |
| 35         | Contact acquirer|
| 36          | Restricted card |
| 37         | Call acquirer security|
| 38          | PIN tries exceeded |
| 39         | No credit account|


   

 
  
       
