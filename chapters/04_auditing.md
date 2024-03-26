# Audits

## 1. Internal reviews

Internal audit processes play a crucial role in enhancing the security posture of a project before it undergoes external scrutiny. While many teams may not have dedicated security researchers in-house, fostering a culture of security-mindedness among developers during the internal review stages is invaluable. By implementing rigorous peer review practices, such as thorough examination of pull requests (PRs), teams can identify and mitigate potential vulnerabilities early in the development cycle. This internal layer of defense, although optional, complements external audits by ensuring that the codebase is as robust as possible from the onset. Encouraging developers to adopt an auditor's mindset helps bridge the gap between development and security, paving the way for a more resilient protocol.

## 2. Before the audit

Preparing thoroughly for an audit can significantly enhance its effectiveness and efficiency. A key step in this preparation is defining the scope of the audit at least two weeks in advance. This foresight allows auditors to familiarize themselves with the project's intricacies and tailor their strategies accordingly. It's crucial to adhere strictly to this predefined scope; any alterations can disrupt the audit's timeline and undermine the auditors' preparation, potentially affecting the quality of the audit. Additionally, providing a frozen commit of the codebase that remains untouched during the audit until the review of the fixes phase ensures consistency and clarity in the audit process. This approach minimizes confusion and allows for a focused and thorough examination of the code at its state during the time of freeze, leading to a more effective identification and subsequent remediation of vulnerabilities.

## 3. During the audit

A security audit is a collaborative endeavor involving both developers and auditors. To facilitate auditors in performing their duties, it's imperative to supply them with comprehensive details about your protocol's functionality, edge cases, integrations, and any areas of concern. Auditors aim to rigorously test every aspect, as errors frequently lurk in the most unforeseen places. However, being informed about the areas developers are most uncertain about can still be beneficial.

Throughout the engagement, it is crucial to respond to the auditors' inquiries promptly and with precision to maximize the efficiency of the audit time and ensure a thorough understanding of the protocol.

## 4. After the audit

After an audit, your team has to assess if the code is ready to be deployed to the blockchain. Sometimes when systematic critical issues are found, the code is deemed not ready and needs to go back to the development stage. To determine if your code is ready, see if the high/critical severity issues found are systematic, meaning they arise from a flawed architecture of your system and can’t be easily fixed.

Depending on the findings, consider whether the test suite is complete. If issues could have been found through testing, make sure to apply stronger QA before going live. If the audit yielded many critical issues, you’re sometimes recommended to get another audit.

After deployment, set up on-chain monitoring against invariants to ensure your team is quickly alerted of any abnormal behavior and set up an incident response protocol to act in case of a breach.
