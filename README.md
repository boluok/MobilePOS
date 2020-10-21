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
