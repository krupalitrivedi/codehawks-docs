# How to Determine a Finding Validity

A finding represents a vulnerability in the codebase, they are separated _loosely_ into 3 categories of severity:

* **High**
* **Medium**
* **Low**.

For more information on evaluating a finding severity, see How to Evaluate a Finding Severity.

#### How to determine if a finding is valid?

For findings to be considered valid, they need to check all the properties listed below:

* Submissions must be made during the official duration of the contest.
* Valid submissions should identify legitimate vulnerabilities within the codebase.
* Issues that fall under Gas/QA or Informational severity will not be eligible for rewards, even if they are accurate or correct.
* Submissions should include sufficient details and proof to support the findings. For instance, while ChatGPT and AI can assist in bug finding, relying solely or primarily on AI responses often leads to poor reports. Reports suspected of this approach will likely be deemed invalid.

#### Contest-Specific Issue Validity Guidelines

There are two criteria to determinee the validity of a finding within the context of a specific contest:

* The official contest specification on the [CodeHawks](https://www.codehawks.com) contest's page
* The code within scope

After a contest launch, Sponsors have 48 hours to address any ambiguities raised by auditors in Discord or during the contest's Kick-Off Live Stream regarding the Contest-Specific Issue Validity Guidelines. Once this 48-hour window has passed, the official contest specification on CodeHawks will be updated with answers from the Sponsor, becoming **the ultimate standard for determining the validity of an issue within the contest.**

_Sponsors are strictly prohibited from employing the "_[_Moving The Goalposts_](https://youtu.be/KeswYJgf5mM?feature=shared\&t=19)_" logical fallacy to invalidate submissions after this 48-hour period._&#x20;

Judges and Sponsors may only invalidate a submission if it fails to meet the contest's predefined criteria.\


#### Vague Generalities

Vague generalities are always judged as invalid submissions. Examples include:

* "This function may have re-entrancy, add re-entrancy guard."
* "This hash function may have hash collision, do the hashing a different way."

If an auditor identifies a vulnerability in a function, it is their responsibility to demonstrate its impact by creating a proof of concept (PoC) exploit that can cause significant damage to the system or result in permanent grief or denial of service.

However, if another auditor submits an actual exploit with a PoC that proves the vague generality to be true, only that auditor will be rewarded.\
\
For detailed instructions on what to include and how to submit a finding, please refer to[ How to Write and Submit a Finding](how-to-write-and-submit-a-finding.md).

To determine the validity of a finding, we provide a number of issue categories as a guideline. Please note that final determinations will always be at the discretion of the Judge.



### Examples of findings not considered valid 

The following is a high level list of issues which are usually not considered valid, or can be considered valid if respect certain characteristics:

| Issue                                  | Description                                                                                                      | Validity          |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ----------------- |
| Gas optimizations                      | Users/protocols may pay extra gas due to this issue.                                                             | Not valid         |
| Zero address checks                    | Ensure input values are not zero addresses.                                                                      | Not valid         |
| User input validation                  | If user input results in a major protocol malfunction or significant fund loss, it's a valid high.               | Varies            |
| Admin Input/call validation            | Issues related to incorrect input by admins, call order mistakes, and assumptions breaking due to admin actions. | Not valid         |
| Front-running initializers             | If there's no irreversible damage or fund loss & the protocol can redeploy and initialize again.                 | Not valid         |
| User experience and design improvement | Minor inconveniences or design opinions with no clear loss of funds indication.                                  | Not valid         |
| User Blacklist                         | A user being blacklisted causing harm only to themselves.                                                        | Not valid         |
| Use of call vs transfer                | Gas price not being the same value of 2300 is a protocol choice.                                                 | Low/informational |
| EIP compliance with no integrations    | If no external integrations exist and no adverse effects arise due to non-compliance with an EIP.                | Informational     |
| Users sending ETH/native tokens        | If contracts allow users to send tokens accidentally.                                                            | Not valid         |
| Loss of rewards                        | Losing airdrops, liquidity fees, or other rewards not in the protocol design.                                    | Not valid         |
| Incorrect values in View functions     | Considered low by default, unless used in a larger function resulting in fund loss.                              | Varies            |
| Chainlink round completeness           | OCR doesn't rely on rounds for reporting.                                                                        | Not valid         |
| Update contest issues                  | Issues from previous contests with `wont fix` labels.                                                            | Not valid         |
| Mock contracts issues                  | Any issues found in mock contracts.                                                                              | Not valid         |
| Slippage                               | Issues showing definite fund loss with a detailed explanation.                                                   | Valid high        |
| EIP Compliance                         | Issues regarding EIP compliance with essential external integrations.                                            | Varies            |
| Identifies the core issue              | Issues with many duplicates, but that pinpoint the core issue and show valid fund loss.                          | Varies            |
| Out of Gas                             | Issues leading to Out of Gas errors due to malicious users or specific call flows.                               | Varies            |

\