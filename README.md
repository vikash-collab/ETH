# Token creating, mappping and burning 

# SPDX-License-Identifier: MIT                                                                                                                                        
pragma solidity 0.8.18;

contract MyToken {

 # Public variables to store the details about the coin
    string public tokenName = "MyToken";
    string public tokenAbbrv = "MTK";
    uint public totalSupply = 0;

## Mapping of addresses to balances
    mapping(address => uint) public balances;

    // Mint function to increase the total supply and balance of the "sender" address
    function mint(address _to, uint _value) 
    public 
    {
            totalSupply += _value;
            balances[_to] += _value;
    }

## Burn function to decrease the total supply and balance of the "sender" address
    function burn(address _from, uint _value) public 
        {
        require(balances[_from] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_from] -= _value;
    }
}
