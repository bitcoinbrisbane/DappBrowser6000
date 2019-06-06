# fireWolf

## Abstract
Unlike the internet where we have a set of clients browsers that render standardise HTML markup we do not have a *real* DAPP browser.  The goal of this project is to define a set of new HTML tags that allow developers to write HTML style code and interface directly with Ethereum smart contracts.

## Browser Engines

Browers work by the following process:

Some of the engines used are
* WebKit
* Gecko

I like the engine `litehtml` and see they take bitcoin tips.  There is also a c# wrapper which could be helpful.

## Approach

* Parse the markup into a DOM
* Paint the markup

## Senarios
The HTML is hosted on a tradtional web server.
The HTML is stored on a IPFS node.

## Function tag
This specification defines a new set of tags to be embedded in the mark up.  The browser will then interprate these and make the relavant contract calls.  They can be can be thought of like `<form>` tags, where the elements within the form are POSTed back to the server.

### Function Attirbutes

* Action or Contract
* Name
* Signature: The function signature
* Hash

### Function Elements
* Type 
* Index

### Functions
Functions are the 

### Readonly functions
* Functions that do not require an input, such as `totalSupply`.  These are transpiled into raw text.

Eg:

`<p><function name="totalSupply" signature="totalSupply()"/></p>`

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
  
}
```

## Reference
### Engines
https://ultralig.ht
https://github.com/cefsharp/CefSharp
https://github.com/PingmanTools/LiteHtmlSharp
