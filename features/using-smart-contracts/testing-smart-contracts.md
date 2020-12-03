---
description: Want to practice your skills? We have the tools for you!
---

# Resources: Test Contracts

To help test that you're accessing your smart contracts in the correct way, we have created and deployed a number of test contracts to all the major networks to allow you to test against: 



Mainnet: 

[https://etherscan.io/address/0x29f7324836a88d04ce760e240e6cd7f0780aa255\#code](https://etherscan.io/address/0x29f7324836a88d04ce760e240e6cd7f0780aa255#code)

Ropsten:

[https://ropsten.etherscan.io/address/0xe2a6dd166b1840db90b2e4462ca7a90187562ddc\#code](https://ropsten.etherscan.io/address/0xe2a6dd166b1840db90b2e4462ca7a90187562ddc#code)

Rinkeby:

[https://rinkeby.etherscan.io/address/0x6eefcb4ea22ed10f0094e0e6a8076275c7422220\#code](https://rinkeby.etherscan.io/address/0x6eefcb4ea22ed10f0094e0e6a8076275c7422220#code)

### Kovan: 

[https://kovan.etherscan.io/address/0x08c64b4d01881e29c5f4a8454de7e29ec395b544\#code](https://kovan.etherscan.io/address/0x08c64b4d01881e29c5f4a8454de7e29ec395b544#code)

### Goerli:

[https://goerli.etherscan.io/address/0x08c64b4d01881e29c5f4a8454de7e29ec395b544\#code](https://goerli.etherscan.io/address/0x08c64b4d01881e29c5f4a8454de7e29ec395b544#code)

xDai: 





GithubGist: 

[https://gist.github.com/crazyrabbitLTC/ed45a52cdcc559feb6ac5703ee93c8b2](https://gist.github.com/crazyrabbitLTC/ed45a52cdcc559feb6ac5703ee93c8b2)

Solidity Code: 

```text
pragma solidity 0.5.0;

contract DappHeroTest {
    uint public important = 777;
    bytes32 public hello = "Howdy";
    
    address public owner;
    
    event EventTrigger(address indexed sender, uint value);
    event ValueSent(address indexed sender);
    event EmitString(string message);
    event ValueSentWithMessage(address indexed sender, bytes32 message);

    constructor() public {
       owner = msg.sender;
    }

    function viewNoArgsMultipleReturn() public view returns(uint importantNumber, bytes32 sayHello){
        return (
            importantNumber,
            hello
        );
    }
    
    function viewMultipleArgsSingleReturn(address fromAddress, uint amount) public view returns(uint singleInt){
        return 89898989;
    }
    
    function viewMultipleArgsMultipleReturn(address fromAddress, uint amount) public view returns(uint longInteger, bytes32 sayHello){
        return (
            8989898989,
            hello
        );
    }

    function triggerEvent(uint anyInputValue) public {
        emit EventTrigger (msg.sender, 10);
    }

    function sendEthNoArgs() public payable {
        emit ValueSent(msg.sender);
        msg.sender.transfer(msg.value);
    }
    
    function makeTxNoArgs() public {
        emit EventTrigger(msg.sender, important);
    }
    
    function makeTxWithArgs(string memory myString) public {
        emit EmitString(myString);
    }

    function sendEthWithArgs(bytes32 simpleMessage) public payable {
        emit ValueSentWithMessage(msg.sender, "message");
        msg.sender.transfer(msg.value);
    }

    function sendMinimumTwoEthNoArgs() public payable {
        require(msg.value >= 2);
        emit ValueSent(msg.sender);
        msg.sender.transfer(msg.value);
    }

    function sendMinimumTwoEthWithArgs(bytes32 message) public payable {
        require(msg.value >= 2);
        emit ValueSentWithMessage(msg.sender, message);
        msg.sender.transfer(msg.value);
    }
}
```

ABI: 

[https://gist.github.com/crazyrabbitLTC/e4432070cd41b6f7181f3935d260871e](https://gist.github.com/crazyrabbitLTC/e4432070cd41b6f7181f3935d260871e)

