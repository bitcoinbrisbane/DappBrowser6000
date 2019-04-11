# dapp Browser 6000

## Abstract
Unlike the internet, where we have a set of clients browsers, we do not have a *real* DAPP Browser.  The goal of this project, is to mix html and etheruem smart contract abi files, so the browser can render th epage without the need to use `web3.js` etc.

A developer can simply add new tags to html markup

* A repository smart contract to hold the contract address and html links

## Browser Engines

Browers work by:

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

## New tags

### Header values

Note these could be stored in headers too.
`<contract></contract>` 
`<network></network>`

or headers
`x-contract`
`x-network`

### Function tags

Fields and functions without inputs are represented with the function tag.  In solidity, functions can be either pure, view.

`<function name="totalSupply">`

## ETH Entry Contract

The contract owner points to their ENS to this contract.

```
contract entry {
  
}
```

## A worked ERC20 example.
Say a user wants to build a web page to interface with their ERC20 token.  They may want to display some of the readonly properties such as

* Name (name)
* Symbol (symbol)
* Total Supply (totalSupply)


Readonly functions are implmented with the function tag.  The default is return index 0.

`<function name="totalSupply"></function>`

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

## Markup

Read only tags:
* Head tags:  contract

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

Input tags -> input functions


Reading collections

## Engines
https://ultralig.ht
https://github.com/cefsharp/CefSharp
https://github.com/PingmanTools/LiteHtmlSharp
