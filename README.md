# erc20


pragma solidity ^0.8.13;
import 'https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/ERC20.sol';

contract MyToken is ERC20 {

    address public admin;

    constructor() ERC20("My Token", "MTN") {
        _mint(msg.sender, 1000 * 10 ** 18);
        admin = msg.sender;

    }

    function mint(address to, uint amount) external {
        require(msg.sender == admin, "Only Admin");
        _mint(to, amount);
    }

    function burn(uint amount) external{
        _burn(msg.sender, amount);
    }

}
