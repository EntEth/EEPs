<pre>
  EEP: #12
  Title: New Rules Contract with Voting Weight 4
  Author: Zach Yam
  Status: Draft 
  Type: Organizational
  Created: 2016-12-27
</pre>

#Abstract

This new rules contract will change voting weight on proposals to a vote weight of 4. 

#Motivation

#Specification

#Rationale

#Implementation

The new rules contract has been deployed at Ropsten Test Network with address: 0xeA3544991e47f06CEf20f86b7F42A1b3449aA22f

When creating proposal on Boardroom:

1. Select 'Organizational' proposal type.
2. Keep the proxy address empty.
3. Click Assemble
4. Enter 'ChangeRules(address)' in the Solidity Method ABI
5. Enter the new rules contract address: 0xeA3544991e47f06CEf20f86b7F42A1b3449aA22f
