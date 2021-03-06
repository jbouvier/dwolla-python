# dwolla-python: Python Wrapper for Dwolla's API
=================================================================================

## Version

1.2.0

## Requirements
- [Python](http://www.python.org/)
- [Dwolla Application](https://www.dwolla.com/applications)

## Installation

Automatic installation using [pip](http://pypi.python.org/pypi):

    pip install dwolla

## Usage

```python
from dwolla import DwollaUser
DwollaUser = DwollaUser('[OAuth Token Goes Here]')

transactionId = DwollaUser.send_funds(1.00, '812-626-8794', '[PIN]')
print transactionId
```

## Examples / Quickstart

This repo includes various usage examples, including:

* Authenticating with OAuth [oauth.py]
* Sending money [send.py]
* Fetching account information [accountInfo.py]
* Grabbing a user's contacts [contacts.py]
* Listing a user's funding sources [fundingSources.py]
* Creating offsite gateway sessions [offsiteGateway.py]
* Registering a new Dwolla user account [registerUser.py]

## Methods

DwollaClientApp class:

    init_oauth_url(redircet_uri, scope) ==> (string) OAuth permissions page URL
    get_oauth_token(code)               ==> (string) a never-expiring OAuth access token
    get_account_info(account_id)        ==> (array) the user entity for {account_id}
    get_nearby_spots([lat, lon, range, limit])  ==> (array) list of nearby spots matching the search criteria
    register_user(email, password, pin, firstName, lastName, address, address2, city, state, zip, phone, dateOfBirth[, organization, ein, type, acceptTerms])   ==> (dict) the newly created user record

DwollaUser class:

    get_balance()                           ==> (string) the Dwolla balance of the account associated with the token
    get_account_info(account_id)            ==> (dict) the user entity associated with the token
    get_contacts([search, types, limit])    ==> (array) list of contacts matching the search criteria
    get_transaction(transaction_id)         ==> (dict) transaction details
    get_transaction_list([since, types, limit, skip])       ==> (array) a list of recent transactions matching the search criteria
    get_transaction_stats([types, start_date, end_date])    ==> (dict) statistics about the account associated with the token
    send_funds(amount, dest, pin[, notes, assume_cost, facil_amount, dest_type])    ==> (string) transaction ID
    request_funds(amount, source, pin[, notes, facil_amount, source_type])          ==> (string) request ID
    get_funding_sources()   ==> (array) a list of funding sources associated with the token
    get_funding_source(id)  ==> (dict) information about the {id} funding source

DwollaGateway class:
    
    set_mode(mode)          ==> (bool) did mode change?
    start_gateway_session() ==> (bool) did session start?
    add_gateway_product(name, amount[, desc, qty])              ==> (bool) was product added?
    verify_gateway_signature(signature, checkout_id, amount)    ==> (bool) is signature valid?
    get_gateway_URL(destination_id[, order_id, discount, shipping, tax, notes, callback])    ==> (string) checkout URL

## Credits

This wrapper is a forked extension of Thomas Hansen's 'dwolla-python' module.

- Thomas Hansen &lt;thomas.hansen@gmail.com&gt;
- Jordan Bouvier &lt;jbouvier@gmail.com&gt;
- Michael Schonfeld &lt;michael@dwolla.com&gt;

## Support

- Dwolla API &lt;api@dwolla.com&gt;
- Michael Schonfeld &lt;michael@dwolla.com&gt;

## References / Documentation

http://developers.dwolla.com/dev

## License 

(The MIT License)

Copyright (c) 2012 Dwolla &lt;michael@dwolla.com&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.