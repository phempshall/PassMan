# PassMan 


This is a Proof of Concept deterministic PBKDF2 based javascript password manager inspired by the password manager located on [SS64.com](https://ss64.com/pass/) but with additional features and cryptographic updates.

A live example version can be found at [https://phempshall.github.io/PassMan/passman.html](https://phempshall.github.io/PassMan/passman.html) however it is recommended you clone this git and configure the master seed rather than use the preconfigured live example version.


##### Features:

- pbkdf2
	- configurable iteration count
	- configurable bit length
	- configurable master seed
- custom seeds
- session timeout
- unique identicons
- one-click copy-to-clipboard
- configurable password length*
- multiple outputs
	- hexidecimal
	- base64
	- base94
- single self-contained html file

*\*lengths max: 160 (base94), 128 (hex), 88 (base64)*


**16 character password examples:**

 - **Hex:** `c9d3928f7a6b061f`
 - **Base64:** `06sMPNDV3nwTWFTi`
 - **Base94:** `P66?|Q.L!cP=&Ot;`


## Installation

Clone this git and then see below for configuration.


## Configuration

Configuration is done through the `PassMan.config` JSON object. You can edit the existing configuration within the `<HEAD>` of the `passman.html` file.

A basic, semi-self-documenting version is below for reference:

```
PassMan.config = {
	masterSeed : "some-random-seed-phrase", // will be converted to SHA256-HEX
	iterations : 10000, // pbkdf2 iteration count
	length : 512, // pbkdf2 bit length
	options : {
		sessionTimeout : true, // resets page after sessionDuration expires
		sessionDuration : 60, // time in seconds
	},
	db : [
		{
			category : "Category name 1",
			sites : [
				{
					name    : "Site 1",
					url     : "https://www.site1.com",
					seed    : "site1",
					length  : 16,
					output  : "base94"
				},
				{
					name    : "Site 2",
					url     : "https://www.site2.com",
					seed    : "site2",
					length  : 16,
					output  : "base64"
				},
			]
		},
		{
			category : "Category name 2",
			sites : [
				{
					name    : "Site",
					url     : "https://www.site.com",
					seed    : "site.com",
					length  : '', // leave empty for max length output
					output  : "hex"
				},
			]
		},
	]
};
```

## Usage

Once configured (see above) run `passman.html` and simply input your master password. Then generate the relevant password for your chosen website by `clicking` on the `green lock icon`. Your password will appear for the website. Simply `click within the password area` and it will disappear while simultaneously copying the password to your clipboard for you.



## License

```
PassMan
https://www.paulhempshall.com/io/PassMan/
Copyright (C) 2017 Paul Hempshall.

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
```

https://opensource.org/licenses/GPL-3.0


## Third-party Notices

- Stanford JavaScript Crypto Library **BSD-2/GPL-2** https://github.com/bitwiseshiftleft/sjcl

- Flotsam **MIT** https://github.com/spencertipping/flotsam

- Identicon.js **BSD-2** https://github.com/stewartlord/identicon.js/tree/master



---
[![Bitcoin](https://img.shields.io/badge/donations-Bitcoin-orange.svg)](https://blockchain.info/address/1K1AhrU5JS8euypB3Vw2iGxXqsbwcf9kxN)   [![Litecoin](https://img.shields.io/badge/donations-Litecoin-lightgrey.svg)](http://ltc.blockr.io/address/info/LLowTnsW4d3uymbZiiFZLUkejZCcdcmW6F)   [![Dogecoin](https://img.shields.io/badge/donations-Dogecoin-yellow.svg)](https://dogechain.info/address/DGB5acV5rfEZaovAM1PNHmbbecrrwb1jsG)   [![Dash](https://img.shields.io/badge/donations-Dash-blue.svg)](https://explorer.dash.org/address/XpRyt7DGjprwZxV5Bqh9y2WmBzWaKPmqX5)    [![Ethereum](https://img.shields.io/badge/donations-Ethereum-93a1c6.svg)](https://etherscan.io/address/0xe8b4f8842bf14b9a4ce675461153ea21ca742bc7)
