# Deployments and upgrades

You’ve followed all the coding best practices and gone through one or multiple audits. Even if you've nailed the coding and your smart contract has passed all audits with flying colors, you still need to prepare for the launch day.

It's like preparing for a marathon; the race doesn't end at the training; you also need to plan your race day strategy. Making sure you cover all your bases during deployment is just as critical as the coding and auditing part to make sure your smart contract runs smoothly and securely.

## 1. Deployment Scripts

We usually treat our smart contract code very carefully, write extensive tests for it, and get it reviewed(internally and externally). But scripts that interact with these contracts - such as deployment scripts are sometimes treated differently.

While it is true that they are not core to the functionality of the protocol, deployment scripts are what gives birth to the protocol and they often involve complex logic and interactions, especially for systems composed of multiple smart contracts that interact with each other.

Because of that, it is essential that you try to make your scripts as simple as possible, use them inside your unit and integration tests(to deploy and initialize your contracts),and carefully review them.

**Avoid msg. sender**

One common practice that we still see today is assigning roles for privileged actions(e.g. Mint tokens, pause the contract) to the deployer of the contract(msg.sender), we even did that in some of our contracts(e.g. Ownable) until Contracts 5.0. Now we ask for explicit assignments and recommend all projects doing so. This is because of two main reasons:
Less error-prone. If you do explicit assignments in the constructor it won’t happen that you give more permissions to the deployer inadvertently.
Works with CREATE2. It is becoming more common to do deterministic deployments these days to have the same address across supported EVM chains. If you use msg.sender, permissions will be assigned and locked forever in the factory contract.

You can read more about this in the [EEA Trust Specs](https://entethalliance.org/specs/ethtrust-sl/v2/#sec-deployment-considerations).

## 2. Testing your deployments on a fork

It is a common practice for projects to deploy to testnets as the smart contracts become more ready in order to manually test behavior, integrations, etc. While this is good practice, and we encourage teams to keep doing so, a sometimes overlooked step is testing your deployments in forked networks.

Besides using testnets, a sometimes overlooked step is testing your deployments in forked networks. Testnets might help you catch some issues, but they often differ a lot from mainnet (they don’t have all the protocols deployed, liquidity profiles are very different, etc.) - in summary, the state of the chain is often very different. Running and testing your deployments on a forked network that has the same state that the chain(s) you plan to deploy to will save you some headaches during the deployment day.

## 3. Secure Upgrades

Upgrades have always been a debated topic in crypto, but they have proven to be extremely useful in the right context. They are controversial because of the immutable promise of smart contracts, which should still be the end goal for most protocols, but we can’t deny that especially during the early stages of a project they are very convenient to help fix bugs and make tweaks to find product market fit.

The most common way to add upgradability is to use Proxies. But adding upgradability to your protocol doesn’t come without risks - new vulnerabilities can be added in new versions of the contract, the upgrade itself can go wrong if not handled properly, and there’s an additional risk that the upgrader keys can get compromised if not handled carefully. Because of this it is important that you consider a few things.

1. **Don’t use upgrades if you don’t need to**. Perhaps this sounds obvious, but if there are simple contracts that are highly unlikely to require changes and they are simple enough that you feel confident they don’t contain vulnerabilities, don’t introduce the complexity of upgrades unnecessarily(plus your users will benefit from less gas overhead).
2. **Use a battle proven standard for proxies**. This includes UUPS and Transparent proxies. We have support for both of them in our contracts library.
3. **Avoid [storage collisions](https://docs.openzeppelin.com/upgrades-plugins/1.x/proxies#storage-collisions-between-implementation-versions)** between versions of the implementation contract. This happens when the new version of the contract changes the storage layout in a way that overwrites existing data. We recommend you use one of our [upgrade plugins](https://docs.openzeppelin.com/upgrades-plugins/1.x/) that check for this before even proposing the upgrade. We have support for both Hardhat and Foundry.
4. **Correctly initialize your smart contracts**. Upgradable contracts don’t usually have constructors(since the state is stored on the proxy and not the implementation). Make sure that you correctly initialize the state of the contract and don’t get frontrun by other users. You can leverage our [initializer](https://docs.openzeppelin.com/upgrades-plugins/1.x/writing-upgradeable#initializers) modifier for this.
5. **Require multiple signatures to execute the upgrade**. This can initially be a Safe multisig with a high enough threshold and eventually become a governor contract if you decide to decentralize your protocol.

## 4. Choosing the right deployment and upgrade stack

Dealing with all these concerns individually can be cumbersome, and usually not the best use of your time, especially if you are developing the first iterations of your protocol, where your focus is on putting things in the hands of users and achieving product market fit. Luckily there are tools that can help you follow best practices and achieve things more easily(e.g. Deterministic deployments, source code verification, etc.). That’s why we included Deploy as one of the core modules in Defender, to help projects ship faster and more securely. We invite you to test it out
