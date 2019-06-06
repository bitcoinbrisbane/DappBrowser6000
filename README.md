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
This specification defines a new set of tags to be embedded in the mark up.  The browser will then interprate these and make the relavant contract calls.

### Attributes

* Name
* Signature
* Hash

### Functions
Functions are the 

### Readonly functions
* Functions that do not require an input, such as `totalSupply`.  These are transpiled into raw text.
* Functions that require inputs

### Writeable functions

### Payable

### Header values

Header key
`eth-network`

### Function tags

Fields and functions without inputs are represented with the function tag.  In solidity, functions can be either pure, view.

`<function name="totalSupply"></function>`

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
