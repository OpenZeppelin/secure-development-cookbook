# Operational Security

Boom! You’ve got through deployment procedures and got your smart contract infrastructure up and running on production. The marathon has begun!

Now what’s up with the status of your security? Let’s check the dashboard panel to see the health indicators.. Wait. You did plan for it.. Right?

## 1. Before touching web3

Web3 is just an extension of web2. Don’t forget traditional IT security: Your team should have sufficient knowledge in private key infrastructure management, should know how to detect phishing attacks and scams.

**Ensure traditional IT security**: Traditional practices like installing only secure, signed or IT approved software, using https and vpn should be in place even if you are more of a decentralized protocol.
Your PKI infrastructure must be secure and minimize the chance that an adversary can gain access to any sensitive information.
For entities, having a certified security standard such as SOC2 is a great thought to start early.

**Personnel web3 training**: Using web3 can be daunting and complicated even for technical experts in web2 space.
Don’t neglect the importance of training your team so they know specifics, such as - how to use wallets safely, have basic understanding of recovery phrases, how to submit transactions and what are common phishing methods that they can become targeted by.

## 2.Incident response plan

Based on Threat Modeling and risks identified After the audit you can plan accordingly to ensure that your team is well prepared to handle any security threats that may come up.
Using identified potential threats, prepare a battle-ready Incident Response plan. Make sure you are able to handle security incidents effectively to mitigate loss of funds and maintain your reputation even if the worst case happens.

**Define responsibilities**: Make sure you have security policies that will develop a set of roles and responsibilities around the use of specific Incident Response mechanisms in your environment. Develop a high level representation of the roles and responsibilities that various stakeholders will assume during an active security incident.
Vulnerability management protocol
Make sure you have detailed decision trees, communication plans, and specific guidance on opportunities for automation to minimize exposure for a wide range of scenarios.
**Incident Response Drills**: Execute live Incident Response simulations to assess the effectiveness of your team’s ability to make use of the plan in conditions close to real.
Based on this assessment plan and improve your team performance, adjust defined responsibilities and iterate until you are comfortable that when it comes to real, you are A TEAM where everyone knows what to do.

## 3. Plan monitoring in advance

Planning monitoring often means that based on your planned Threat Modeling and risks identified After the audit you will need to iterate back to Technical specifications and monitoring requirements to it.
To save your day from the need of such going back iteration, here are some most important techniques and best practices that you can start planning already in the first specification pass.

**Dashboard requirements**
Make sure that you have outlined all required visibility on possible attack vectors. Also it's great to think ahead that users, investors and other stakeholders also might need to have access to data they need to drive their decisions.

**Events requirements**
Every executable method should emit an event in such format that it is convenient for monitoring setup.
These event meanings and mapping to Threat Modeling should be clear and easy to use. Plan indexing accordingly so that required data can be retrieved.

Wherever possible avoid having to build separate indexes and databases off chain in order to provide security monitoring. Such can be challenging when dealing invariant monitoring in cross chain bridges that use mint/burn logic for instance.

**United Interface**
External interfaces such as methods and events must be clearly defined not just by Code clarity but also checked for signature collisions across the whole infrastructure and if acceptable - dependencies. Compilers will take care of signature collisions within the same contract, but not within an infrastructure, which might make monitoring tasks more challenging later on.

Make sure that hexadecimal signatures of principally different interfaces do not collide as well as that principally different interfaces are named differently across the whole infrastructure.
Ensure that parameters and indexed arguments across infrastructure are the same for the same interfaces with the same signature.

**Deployments registry**
Your deployed infrastructure, all smart contracts and dependencies defined in Technical specifications should be accessible in a form of registry that maximizes off chain monitoring ability to get and label your addresses as well as retrieve all required application-binary interfaces.

**Monitoring infrastructure**
Monitoring infrastructure should be not least reliable than stakes at risk. It should fulfill specific monitoring requirements needs, such can be: low latency for time-critical notifications; Public and autonomous redundancy for a community awareness;
It should expose minimum information regarding setup and monitor configuration for non-community monitoring.

**Metrics and methodology**
Monitoring smart contracts is a challenging task, new attack vectors might arise that you have to adapt for. You need to have enough sensitivity to see alerts, yet low noise to not miss the right beat.
Defining performance metrics and tracking those will help you to be aware of how your monitoring performs over time and after changes made to adapt for a never ending challenge.

## 4. Deploying Monitoring

Set up monitoring as early as possible. Don’t miss a bit of possible threat.

Ideally prepare monitoring to launch before contract deployments and make sure you’ve set up all required infrastructure needed by Incident response plan that is ready to target the production environment.

For non-deterministic deployments you should be aware and check manually all attack vector threats that can exist before your monitoring system is activated.
Deploy monitoring stack for deterministic deployments before deploying contracts.

**Monitor for new deployments**
Prepare your monitoring to follow Deployments registry in automated manner to the extent possible in your stack.
Notify immediately when a new piece was added to your infrastructure and add new infrastructure to the monitoring stack immediately.

**Continuously improve**
Set up a coverage metric for your smart contracts infrastructure and expect need to continuously improve. Even over immutable contract infrastructure monitoring is going to be a continuous opportunity for improvements as protocols undergo hardforks, state changes and new attack vectors may arise.
Track and improve your Metrics and methodology to ensure maximum level of security
