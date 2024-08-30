// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts@5.0.1/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts@5.0.1/token/ERC721/extensions/ERC721Enumerable.sol";
import "@openzeppelin/contracts@5.0.1/access/Ownable.sol";
import "@openzeppelin/contracts/security/ReentrancyGuard.sol";
import "@openzeppelin/contracts/utils/Base64.sol"; 

contract CollectionBox is ERC721, ERC721Enumerable, Ownable, ReentrancyGuard {

    string private tokenUri;
    string[6] typeOfBox = ["classA", "classB", "classC", "classD"];

    
    struct Box {
        string name;
        string typeOfBox;
    }

    mapping(uint256 => Box) public boxsDtails;
    mapping(address => uint256) public totalSupplyOfOwner;
    // event _updateToken(
    //     address indexed owner,
    //     uint256 id,
    //     Companion indexed companion
    // );
    constructor(address initialOwner, string memory _uri)
        ERC721(" Companions New Genesis", "CNG")
        Ownable(initialOwner)
    {
        tokenUri = _uri;
    }

    function getTokenDetails(uint _tokenId) public view returns(Box memory){
        return  boxsDtails[_tokenId];
    }

    function getImg(uint256 tokenId) private view returns (string memory) {
        string memory img;
        img = string(abi.encodePacked(tokenUri, uint2str(tokenId), ".gif"));
        return img;
    }
    

    // Global functions ERC721
    function contractURI() public view returns (string memory) {
        return tokenUri;
    }

    function mint(address _to, string memory _name, uint8 _typeOfBox) public onlyOwner {
        require( _typeOfBox == 0 ||  _typeOfBox == 1 ||  _typeOfBox == 2 ||  _typeOfBox == 3 , "NOT valid");
        uint256 supply = totalSupply();

        if(_typeOfBox == 0 ) {
            Box memory thisBox = Box(_name, "classA");
            boxsDtails[supply] = thisBox;
            _safeMint(_to, supply);
            totalSupplyOfOwner[_to] += 1;

        }

        if(_typeOfBox == 1 ) {
            Box memory thisBox = Box(_name, "classB");
            boxsDtails[supply] = thisBox;
            _safeMint(_to, supply);
            totalSupplyOfOwner[_to] += 1;
        }

        if(_typeOfBox == 2 ) {
            Box memory thisBox = Box(_name, "classC");
            boxsDtails[supply] = thisBox;
            _safeMint(_to, supply);
            totalSupplyOfOwner[_to] += 1;
        }

        if(_typeOfBox == 3 ) {
            Box memory thisBox = Box(_name, "classD");
            boxsDtails[supply] = thisBox;
            _safeMint(_to, supply);
            totalSupplyOfOwner[_to] += 1;
        }
    }
  
    
    function tokenURI(uint256 tokenId)
        public
        view
        override(ERC721)
        returns (string memory)
    {
        string memory json = Base64.encode(
            bytes(
                string(
                    abi.encodePacked(
                        '{"image": "',
                        getImg(tokenId),
                        '",',
                        "]}"
                    )
                )
            )
        );

        return string(abi.encodePacked("data:application/json;base64,", json));
    }

    // Function uint to String 
    function uint2str(uint256 _i)
        internal
        pure
        returns (string memory _uintAsString)
    {
        if (_i == 0) {
            return "0";
        }
        uint256 j = _i;
        uint256 len;
        while (j != 0) {
            len++;
            j /= 10;
        }
        bytes memory bstr = new bytes(len);
        uint256 k = len;
        while (_i != 0) {
            k = k - 1;
            uint8 temp = (48 + uint8(_i - (_i / 10) * 10));
            bytes1 b1 = bytes1(temp);
            bstr[k] = b1;
            _i /= 10;
        }
        return string(bstr);
    }

    function _update(address to, uint256 tokenId, address auth)
    internal
    override(ERC721, ERC721Enumerable)
    returns (address)
    {
        return super._update(to, tokenId, auth);
    }

    function _increaseBalance(address account, uint128 value)
        internal
        override(ERC721, ERC721Enumerable)
    {
        super._increaseBalance(account, value);
    }

    function supportsInterface(bytes4 interfaceId)
        public
        view
        override(ERC721, ERC721Enumerable)
        returns (bool)
    {
        return super.supportsInterface(interfaceId);
    }


}
