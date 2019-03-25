# dapp Browser 6000

## Abstract
Unlike the internet, where we have a set of clients browsers, we do not have a *real* DAPP Browser.  The goal of this project, is to mix html and etheruem smart contract abi files, so the browser can render th epage without the need to use `web3.js` etc.

* A repository smart contract to hold the contract address and html links

## ETH Entry Contract

The contract owner could point thier ENS to this contract.

```
contract entry {
  
}
```

## A worked ERC20 example.
Say a user wants to build a web page to interface with their ERC20 token.  They may want to display some of the readonly properties such as

* Name
* Symbol
* Total Supply

Readonly functions are used within the

* h tags
* p tags

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
  <h1>{{ name=totalSupply }}</h1>
</body>

</html>
```

Input tags -> input functions


Reading collections
