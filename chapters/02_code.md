## Code

### 1. Code clarity

_“Code is clean if it can be understood easily – by everyone on the team. Clean code can be read and enhanced by a developer other than its original author. With understandability comes readability, changeability, extensibility, and maintainability”_

[Clean Code by Robert C. Martin](https://gist.github.com/wojteklu/73c6914cc446146b8b533c0988cf8d29)

**Structure and Style**: You want the general structure and style of your contracts to be extremely clear. You can achieve that by following conventional practices outlined in the Solidity style guide.

**Self-contained code**: Your code should aim to be self-contained, which means that functions should have a clear and singular purpose, avoiding the use of flag-type parameters. If necessary, consider breaking down a function into multiple smaller functions, each performing a distinct action. This same principle should be applied to contracts themselves. Strive to keep contracts as concise as possible, and if complexity arises, consider dividing them into multiple contracts.

**Naming**:Use declarative, clear, and consistent naming. If some naming is unclear or uses terminology of your protocol, explain it in the comments. Replace magic numbers with named constants.

**Dependencies**: Whenever possible, follow the principle of least knowledge. Ensure you only inherit from battle-tested libraries. Include any unaudited dependencies in the audit scope and check for common vulnerabilities using Defender’s code module dependency checker.

**Input Validation**: Go over each input and define clear logical pre-conditions when needed.

- Always assume input can take any value.
- Always assume functions can be called in any order.
- Always assume frontrunning is possible and an attacker can do any call right before a user with knowledge of their actions.

## 2. Code analysis

Use a static analysis tool like [OpenZeppelin Defender Code Inspector](https://docs.openzeppelin.com/defender/v2/module/code) to automatically verify for common vulnerabilities and style violations. Defender integrates with GitHub to be a part of your CI/CD process, giving you feedback on every PR.

## 3. Documentation

Your code needs to be properly documented to ensure auditors understand its purpose and intended functionality. Poor documentation leads to auditors spending more time understanding your code vs trying to break it, hurting the effectiveness of the audit.

Use the NatSpec format to document every contract, library, function, event, and storage variable.

- Document all your mathematical and financial models with clear explanations and/or proofs.
- Document all your assembly blocks in detail, explaining what they are supposed to do.
- Make use of diagrams as much as possible, to give an overview of the system and visualize the flow of contract interactions.
- Document your threat modeling and assumptions.

## 4. Defensive Programming

When developing your protocol, adopt the perspective of an attacker to audit your code. This process encompasses several crucial aspects:

1. Review audit reports and issues identified in similar protocols. Often, systems with similarities are vulnerable to the same types of human error, stemming from analogous reasoning about their mechanics.
2. Evaluate every user-controlled parameter. Is there a potential for a function to be called with an unexpected parameter?
3. Consider the implications of every external call. Are you delegating execution to an untrusted contract? Does this delegation occur in a state that is not consistent?
4. Evaluate the sequence and circumstances of function executions. Despite the system's intended use, there's potential for manipulation in ways not originally anticipated. Functions could be executed in various orders or combined into a single transaction, leading to unintended outcomes. Additionally, consider scenarios where external factors, such as the availability of flash loans, introduce new dimensions of risk. Reflect on the potential consequences of such manipulations, taking into account both the internal mechanics and external influences like market volatility and frontrunning.
5. If your protocol involves financial transactions, carefully examine the flow of value. How could value be diverted? What factors does it rely on? Are the incentives correctly aligned?

In summary, a key strategy in preparing for an audit is to proactively attempt to audit your own protocol, with a mindset geared towards identifying and exploiting system vulnerabilities.

To learn more about this type of thinking, we recommend reading samczsun’s blog.

**Use the check-effects-interactions (CEI) pattern**: Despite being the most known and documented vulnerability type in blockchain, reentrancy is still one of the most common causes of hacks in 2023 with read-only reentrancy taking the lead.

Always use CEI when possible and in the uncommon case when it’s impossible, document it clearly and ensure all functions, including view ones, are [protected against reentrancy](https://docs.openzeppelin.com/contracts/4.x/api/security#ReentrancyGuard).

If you read or use other protocols, ensure they apply CEI and are not vulnerable to read-only reentrancy. If you are not sure, document it and explain the concern to your auditors.
