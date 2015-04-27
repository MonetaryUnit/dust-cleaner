dust-cleaner
==========

Joins "dust" payments created by pools into bigger transactions with minimal or zero fees.

Requirements:
-------------------------
Generic:
* MonetaryUnit >=1.0.0.1
* Python >=2.6

Linux:
* sudo apt-get install python-pip -y
* sudo pip install requests

Running dust-cleaner.py:
-------------------------
* Install your local monetaryunitd
* Import the private keys with the 'dust' payments into the local wallet
* Run dust-cleaner.py in test mode first, to confirm that your wallet is properly
set and that you are using the correct parameters.

`./dust-cleaner.py <destination-address>`

Replace `<destination-address>` with the MonetaryUnit address to receive the new
created transaction.

For additional options:

`./dust-cleaner.py --help`

Hints:
------
* Large txs will take more time to confirm.
* The script will try to create a zero-fee tx by default.
* To collect larger amounts, try adding a max fee with -f
* When adding a fee, the script will try to create a max size tx up to ~350000 bytes or the max allowed by your fee.

Example (~0.2 MUE x 193 with no fee):
----------------------
```
% python dust-cleaner.py 7SPjhFXBs8WXrWmTYxokLTy8smVGaA8N6b --go
```
Output:
-------
```
Dust cleaning:
- Number of transactions: 193
- Transaction fee: 0 MUE
- Dust to collect: 38.60002 MUE

Preparing transaction.
Dust collected.
```
https://muechain.info/tx/480b518c24725d4443e87136c54969bfdda2506cb0f977da3589060c55ffff20


Example (~0.2 MUE x 2364 with max fee):
-----------------------------
```
% python dust-cleaner.py -f 2 7SPjhFXBs8WXrWmTYxokLTy8smVGaA8N6b --go
```
Output:
-------
```
Dust cleaning:
- Number of transactions: 2364
- Transaction fee: 1.2 MUE
- Dust to collect: 471.60005 MUE

Preparing transaction.
Dust collected.
```
https://muechain.info/block/000000002f88cd602162601d8a7606fb9ecf758f4032a0a18203834d12570910
