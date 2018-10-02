# PHP-SDK
Payger Merchant API - PHP SDK

The Payger SDK for PHP is a library that enables PHP developers to easily make requests to the Payger Merchant API.



To use the library you must first set the pair Key and Secret as the library Username and Password. Please use set userName and setPassword for this. After that you must call connect which will generate a new token for authentication. The following request will use the token and if it expires will request for a new one.

## Set credentials, connect and generate a new token
```
Payger::setUsername( $key );
Payger::setPassword( $secret );
Payger::connect();
```

After that is pretty straight forward methods get, post put or delete depending on what you want from the API, please see some examples below.

##Exchange Rates - get current rate for conversion between your currency and a crypto currency
```
$args = array(
		'from'   => 'USD',
		'to'     => 'BTC',
		'amount' => 3.00
	);
$response = Payger::get( 'merchants/exchange-rates', $args );
```

## Creates new payment
````
$args = array (
		'externalId'        => '001',
		'description'       => 'Description',
        'inputCurrency'	    => 'BTC',
        'outputCurrency'    => 'USD',
        'source'            => 'Your Website',
		'outputAmount'	    => 3.0,
        'buyerName'	        => 'Buyer Name',
		'buyerEmailAddress'	=> 'Buyer Address',
		'callback'          => array( 'url' => 'Callback URL', 'method' => 'POST' ),
	);

$response = Payger::post( 'merchants/payments/', $args );
````
## Cancel Payment
```
Payger::delete( 'merchants/payments/' . $payment_id );
```

#Installation

Payger PHP-SDK is a developer library, not a plugin, which means you need to include it somewhere in your own project. You can use Composer:

````
composer require payger/php-sdk
````
Or you can download the library and include it manually:

````
require_once 'php-sdk/Payger.php';
````

