uc_franko
==========

A [Franko][Franko] payment method for the
[Ubercart][Ubercart] shopping cart for [Drupal][Drupal].

Version: @@uc_bitcoin-version@@

Features
--------

* Generates a new Franko address for every order
* Provides payment address to customer on site at checkout, plus in a
  subsequent email
* Configurable timeout after which unpaid transactions will be canceled
  automatically
* Configurable number of Bitcoin network confirmations after which an order
  is considered paid
* HTTP or HTTPS access to bitcoind

Requirements
------------

### Base requirements
* Ubercart 2.x
* Drupal 6.x

### PHP requirements:
* PHP5
* cURL support  
* SSL support (if you're using HTTPS to talk to bitcoind)

Limitations
-----------

* It is assumed that Franko is the *only* currency accepted.
* All prices are assumed to be in Bitcoins, and no currency conversions are
  performed.
* Checks for payment receipt are performed via Drupal cron, at least until
  bitcoind allows attaching a JSON-RPC callback to an address.
* Orders for downloadables are not tagged as "shipped" once paid.
* No localization support.

Installation
------------

* Install Drupal 6 <http://drupal.org/documentation/install>.
* Install Ubercart 2 <http://www.ubercart.org/docs/user/8075/installing_ubercart>.
* Transfer the contents of the distribution archives to the `modules/` directory
  of your Drupal installation. 

Configuration
-------------

* Log into your Drupal installation as an administrator.
* Navigate to Administer->Site building->Modules and enable the Franko module
* Navigate to Administer->Store administration->Configuration->Payment settings
* Click "Edit" at top, then "Payment methods"
* Enable the Franko payment method and disable all others
* Expand the "Franko settings" dropdown and proceed as follows:
	* Configure your bitcoind server information.
	* If you are using HTTPS to talk to bitcoind and would like to validate
      the connection using bitcoind's own SSL certificate, enter the
      absolute path to the certificate file (server.cert) you've uploaded
      to the server.
	* Configure your payment timeout and number of transaction confirmations
      required.
	* Save configuration.
* Navigate to Administer->Store administration->Configuration->Store settings
* Clik "Edit", then "Format settings"
* Expand the "Currency format" dropdown
* Set "Default currency" and "Currency sign" to "FRK"
* Save configuration

Donate
------

* FRK payments: F7dGXokdVJfX1UYoT8FtUHT6aC46vT6JWC
  http://www.copiamarket.com/franko-faucet/

Authors
-------

* [Mike Gogulski](http://github.com/mikegogulski) -
  <http://www.nostate.com/> <http://www.gogulski.com/>
* [Sir Defaced] (http://www.twitter.com/xdefaced) - 
  <http://www.frankos.org/>

Credits
-------

uc_franko incorporates code from:

* [XML-RPC for PHP][XML-RPC-PHP] by Edd Dumbill (for JSON-RPC support)
* [bitcoin-php][bitcoin-php] by Mike Gogulski (Bitcoin support library)

License
-------

uc_franko is free and unencumbered public domain software. For more
information, see <http://unlicense.org/> or the accompanying UNLICENSE file.


[Franko]:		http://www.frankos.org/
[Ubercart]:		http://www.ubercart.org/
[Drupal]:		http://www.drupal.org/
[XML-RPC-PHP]:	http://phpxmlrpc.sourceforge.net/
[bitcoin-php]:	http://github.com/mikegogulski/bitcoin-php
