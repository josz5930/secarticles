## Smart Contracts - Why start an audit

"Smart Contracts", a term coined by Nick Szabo, refers to the embedding of contractual clauses in the hardware and software which supports these contracts. While one of the benefits in the world of finance is the removal of transaction fees that are charged for transfer agents and other intermediaries, they are other benefits that are provided by the technology. The main features are said to lead to self-execution and self-enforcement (either partially or fully) of the contract clauses. With Smart Contracts, any exchange can be implemented with automatically enforced rules and penalties.

Just like any software, smart contracts can be and should undergo security review. Smart contracts undergo a review that covers technical coding problems and a review of business logic implemented by the contract. Similar to the security code review for typical web applications or other desktop computer software, the auditor reads the code of configuration and benefits from documentation relating to the business requirement and operation of the software. The importance of security review is heightened for Smart Contracts, since the blockchain network that it is based on has transactions that are reconciled & duplicated across many decentralized nodes in an "append-only" transaction log chain.

##### Real life example
On June 17, 2016, a hacker found a vulnerability that allowed him to drain funds from a Decentralized Autonomous Organization that was known as "The DAO" or "Genesis DAO". In the first few hours of the attack, 3.6 million Ethers (the natural unit of the Ethereum blockchain) were stolen, the equivalent of US $70 million at the time.

In this exploit, the attacker was able to “ask” the smart contract (DAO) to give the Ether back multiple times before the smart contract could update its balance. Two main issues made this possible: the fact that when the DAO smart contract was created the coders did not take into account the possibility of a recursive call and the fact that the smart contract first sent the ETH funds and then updated the internal token balance.

##### Scheduling

There are different types of contracts, which lead to various levels of efforts in auditing them. The easiest to audit is those which are fully on chain standard compliant contracts with no ether transfer. For example, the following Zeex Token contract is ERC20 and ERC827 compatible: [ZeexCrowdsale.sol](https://github.com/Zeexme/Crowdsale/blob/master/contracts/ZeexCrowdsale.sol)

Other factors such as code size, complexity and protocol will affect the amount of effort needed to do the audit of the contract. As with all project scheduling, the availability and quality of resources makes a difference to when the audit actually finishes.

##### Vulnerability groups 

The following are some of the types of mistakes that could be found by an audit of smart contracts. For example:

* Misuse of the different call methods: call.value(), send() and transfer().
* Integer rounding errors, overflow, underflow and related usage of SafeMath functions.
* Old compiler version pragmas.
* Race conditions such as reentrancy attacks or front-running.
* Misuse of block timestamps, assuming anything other than them being strictly increasing.
* Contract soft locking attacks (DoS).
* Potential gas cost of functions being over the gas limit.
* Missing function qualifiers and their misuse.
* Fallback functions with a higher gas cost than the one that a transfer or send call allows.
* Fraudulent or erroneous code.
* Code and contract interaction complexity.
* Wrong or missing error handling.
* Overuse of transfers in a single transaction instead of using withdrawal patterns.
* Insufficient analysis of the function input requirements.

##### Going forward
Both manual and automated efforts have to be used to find security issues in the contracts.

The use of test tools such as Solhint and Solium can be used to detect errors at the source code level while tools such as Mythril and Manticore are intended to detect security problems at the behavioural level. Engaging experienced reviewers to check for more complex attacks such as transaction reordering and denial of service by interaction between several contracts.


##### References:

* [Formalizing and Securing Relationships on Public Networks, Nick Szabo](http://ojphi.org/ojs/index.php/fm/article/view/548/469)
*  [Bitcoin is not just digital currency. It's Napster for finance, Fortune](http://fortune.com/2014/01/21/bitcoin-is-not-just-digital-currency-its-napster-for-finance/)
*  [Smart Contract Audits: The Ultimate Security Guide, CoinFabrik](https://blog.coinfabrik.com/smart-contract-audits-ultimate-security-guide/)
*  [How to Audit a Smart Contract - BlockGeeks.com](https://blockgeeks.com/guides/audit-smart-contract/)
*  [Smart Contract Auditing: Human vs. Machine, CoinFabrik](https://blog.coinfabrik.com/smart-contract-auditing-human-vs-machine/)
*  [The Story of the DAO — Its History and Consequences, Samuel Falkon](https://medium.com/swlh/the-story-of-the-dao-its-history-and-consequences-71e6a8a551ee)
*  [Smart Contract Weakness Classification and Test Cases](https://smartcontractsecurity.github.io/SWC-registry/)
