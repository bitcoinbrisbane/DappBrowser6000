# etherWolf 

## Abstract

When users want to "surf" the internet they use a client called a browser.  The browser creates requests to servers and renders the returned texted into visual "pages" we call webpages.

To interact with the ethereum blockchain via dApps, standard web browsers such as Chrome use plugins like MetaMask to call the ethereum blockchain.  Local javascript based apps like Augur are another why for users to interface with the ethereum blockchain, but creating bespoke apps per dApp is cumbersome.

The goal of this project is to remove the burdern of users having to download plugins and bespoke dApps.  etherWolf aims to be the default etherum browser.

## Project Goals
* define a set of new HTML tags that allow developers to write HTML style code and interface directly with Ethereum smart contracts.  We call this standard EML (Etherum Markup Langauge).
* write a cross platform browser that renders the above EML into pages
* define an EIP for the EML
* define an EIP for a proxy contract

## Approach / Architecture (Proxy)

There are many other frameworks or templating engines / middlewares, such as Handlebars.  https://www.npmjs.com/package/handlebars

### Local proxy server

* Post the from to a NodeJS proxy https://github.com/bitcoinbrisbane/fireWolfProxy
* Parse the markup from the DOM using https://github.com/bitcoinbrisbane/node-html-parser
* Transpile the required tags into HTML
* Pass back the completed markup

## Work flows
The HTML is hosted on a tradtional web server.
The HTML is stored on a IPFS node.

## New Mime Types
* ens://
* eth://
* contract://
* token://
* ercx:// (Such as erc20://)

## ETH tag

Attributes
* command (height, gasprice, protocolversion)

Eg:

```
<p><eth command="height"/></p>
```

## Contract tag
The contract tag contains the following attributes.

* address
* network (Default to Main)
* height (Default to latest)
* ERC (If the contract adhears to an EIP)

## Function tag
This specification defines a new set of tags to be embedded in the mark up.  The browser will then interprate these and make the relavant contract calls.  They can be can be thought of like `<form>` tags, where the elements within the form are POSTed back to the server.

### Function Attirbutes

* action or contract:  Specify the contract
* name
* signature: The function signature
* hash:  Signature hash

### Function Elements
* type 
* index

### ReadOnly functions
* Functions that do not require an input, such as `totalSupply`.  These are transpiled into raw text.

Eg EML:

`<p><function name="totalSupply" signature="totalSupply()"/></p>`

Rendered HTML:

`<p>1000</p>`


* Functions that require inputs

```
<function action="0x00" name="balanceOf" signature="balanceOf(address _owner)" type="uint256">
        <input name="_owner" type="address"/>
</function>
```
### Writable

When a function requires gas, the browser with render a dialog box confirming the amount of gas estimated to call the function.

### Payable

When a function is payable, the browser with render a dialog box confirming the amount of ETH.

### Header values

Header key
`eth-network`

## Number type conversions
* hex
* decimal


## A worked ERC20 example.
Say a user wants to build a web page to interface with their ERC20 token.  They may want to display some of the readonly properties such as

* Name (field name)
* Symbol (field symbol)
* Total Supply (function totalSupply)

Readonly functions are implmented with the function tag.  The default is return index 0.

`<p><function name="totalSupply" signature="totalSupply()"/></p>`


The abi for the respective functions are:

### Name

```
{
        "constant": true,
        "inputs": [],
        "name": "name",
        "outputs": [
            {
                "name": "",
                "type": "string"
            }
        ],
        "payable": false,
        "stateMutability": "view",
        "type": "function"
    }
```

### Total Supply

```
{
        "constant": true,
        "inputs": [],
        "name": "totalSupply",
        "outputs": [
            {
                "name": "",
                "type": "uint256"
            }
        ],
        "payable": false,
        "stateMutability": "view",
        "type": "function"
    }
```

## Exmaple Markup


```
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<contract>0x00</contract>
<network>4</network>
</head>

<body>
  <h1><function name="totalSupply"></h1>
</body>

</html>
```

## ETH Entry Contract

The contract owner points to their ENS to this contract.
```
contract entry {
  address public ens;
}
```

## Reference
### Engines
https://ultralig.ht
https://github.com/cefsharp/CefSharp
https://github.com/PingmanTools/LiteHtmlSharp
