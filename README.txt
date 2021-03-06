ProcessWire BigCommerceAPI
=====================

Copyright 2015 by Clip Magic, ABN: 49279932735


ABOUT BIGCOMMERCEAPI
====================

This module uses the BigCommerce API to integrate a BigCommerce store
with your ProcessWire CMS website. All functions available in the 
API are exposed to your ProcessWire template.


REQUIREMENTS
============

  * ProcessWire 2.6 or newer 
  * Apache web server or 100% compatible
  * PHP 5.6 or above


HOW TO INSTALL
==============

1. Copy the BigCommerceAPI files into this directory: /site/modules/BigCommerceAPI/ 
2. In your ProcessWire admin, go to Modules and "Check for new modules".
3. Click "Install" for the BigCommerceAPI module. 
4. Enter your BigCommerce api credentials - BasicAuth OR OAuth and 'submit'.


BIGCOMMERCE FROM THE API
=====================

BigCommerceAPI does not autoload so you need to instantiate it in your template:

   $bc = wire('modules')->get('BigCommerceAPI');

You may execute any BigCommerce API commands from the Bigcommerce/Api/Client
namespace, eg: 

	$product = $bc->api('getProduct',125);
  
where the first parameter is the BigCommerce API function name and subsequent
parameters are the function name arguments.



TERMS AND CONDITIONS
====================

In no event shall Clip Magic or ProcessWire be liable for any special, 
indirect, consequential, exemplary, or incidental damages whatsoever, including, 
without limitation, damage for loss of business profits, business interruption, 
loss of business information, loss of goodwill, or other pecuniary loss whether 
based in contract, tort, negligence, strict liability, or otherwise, arising out of 
the use or inability to use ProcessWire BigCommerceAPI, even if Clip Magic / 
ProcessWire has been advised of the possibility of such damages. 

BigCommerceAPI is provided "as-is" without warranty of any kind, either expressed or 
implied, including, but not limited to, the implied warranties of merchantability and
fitness for a particular purpose. The entire risk as to the quality and performance
of the program is with you. Should the program prove defective, you assume the cost 
of all necessary servicing, repair or correction. If within 7 days of purchase, you 
may request a full refund. Should you run into any trouble with BigCommerceAPI, please
email for support. 


Thanks for using BigCommerceAPI!

---

ProcessWire BigCommerceAPI
Copyright 2015 by Clip Magic, ABN: 49279932735
All rights reserved.


