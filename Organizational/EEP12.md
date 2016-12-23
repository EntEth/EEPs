<pre>
  EEP: #12
  Title: New Rules Contract with Voting Weight 1
  Author: Russell Verbeeten
  Status: Accepted
  Type: Organizational
  Created: 2016-12-14
</pre>

#Abstract

A new rules.sol contract has been deployed that has voting weight 1.
The current rules.sol contract has voting weight 4 for all members.
This proposal is to update the Boardroom to point to the new rules contract at 0x8a46eeadd53f09ec213cc884f3af0339a86e0086#code

#Motivation

To show how that the Boardroom Governance dApp can maintain identity and continue operation even as it allows its smart contract system to be changed but not interrupted.

#Specification

##The existing Rules.sol has the following code:
deployed at 0xeA3544991e47f06CEf20f86b7F42A1b3449aA22f 
```
import "Rules.sol";
import "BoardRoom.sol";


contract OpenRules is Rules {
/* function hasWon(uint _proposalID) constant returns (bool) {
    BoardRoom board = BoardRoom(msg.sender);
    uint nay = board.positionWeightOf(_proposalID, 0);
    uint yea = board.positionWeightOf(_proposalID, 1);

    if(yea > nay) {
      return true;
    }
  } */

  function canVote(address _sender, uint _proposalID) constant returns (bool) {
    return true;
  }

  function canPropose(address _sender) constant returns (bool) {
    return true;
  }

  function votingWeightOf(address _sender, uint _proposalID) constant returns (uint) {
    return 4;
  }
}
```
##The new rules.sol contract we are deploying is.
```
import "Rules.sol";
import "BoardRoom.sol";

contract OpenRules is Rules {
/* function hasWon(uint _proposalID) constant returns (bool) {
    BoardRoom board = BoardRoom(msg.sender);
    uint nay = board.positionWeightOf(_proposalID, 0);
    uint yea = board.positionWeightOf(_proposalID, 1);

    if(yea > nay) {
      return true;
    }
  } */

  function canVote(address _sender, uint _proposalID) constant returns (bool) {
    return true;
  }

  function canPropose(address _sender) constant returns (bool) {
    return true;
  }

  function votingWeightOf(address _sender, uint _proposalID) constant returns (uint) {
    return 1;
  }
}
```
#Implementation

The new contract was deployed onto Ropsten at: 0x8a46eeadd53f09ec213cc884f3af0339a86e0086#code

When creating proposal on Boardroom: 
* select 'Organizational' proposal type.
* Keep the proxy address empty.
* Click Assemble
* enter 'ChangeRules(address)' in the Solidity Method ABI
* Enter the new rules contract address:0x8a46eeadd53f09ec213cc884f3af0339a86e0086#code
