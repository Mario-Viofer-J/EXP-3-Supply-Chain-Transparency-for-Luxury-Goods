### Experiment 3: Supply Chain Transparency for Luxury Goods

```
Name : Mario Viofer J
Reg. No : 212223100032
```


# Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
# Algorithm:
The manufacturer records product creation details on-chain.


The product moves through different supply chain checkpoints.


The ownership of the product can be transferred securely.


Buyers can verify the product’s authenticity.


# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
# Expected Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.


Ownership is transferred at every checkpoint.


Buyers can check the authenticity before purchasing.
<img width="1905" height="916" alt="image" src="https://github.com/user-attachments/assets/1d8e6580-1ee9-4f87-a0e3-c2ceb2d172c3" />

<img width="1919" height="924" alt="image" src="https://github.com/user-attachments/assets/3c4516a2-580c-45e7-a6f8-18f86adc5a09" />

<img width="1918" height="924" alt="image" src="https://github.com/user-attachments/assets/01595c08-dc86-4aad-a71a-0c26e26085e2" />

<img width="1919" height="932" alt="image" src="https://github.com/user-attachments/assets/84229cb4-24e0-4e8a-bc0d-81051fc53adb" />

# High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.

# RESULT : 
Smart contract that tracks the supply chain of luxury goods has successfully completed.


