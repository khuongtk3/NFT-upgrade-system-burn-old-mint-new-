# NFT-upgrade-system-burn-old-mint-new-
NFT upgrade system (burn old, mint new)
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

contract UpgradeNFT is ERC721 {
    uint256 public nextId;

    constructor() ERC721("UpgradeNFT", "UPG") {}

    function mint() public {
        _mint(msg.sender, nextId++);
    }

    function upgrade(uint256 oldId) public {
        require(ownerOf(oldId) == msg.sender, "Not owner");
        _burn(oldId);
        _mint(msg.sender, nextId++);
    }
}
