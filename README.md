# CCSA104 Lab: Managing Security Policies

Practical lab report for CCSA104 Security Policy Management (ICDFA / Check Point CCSA).

**Student:** Jegede Samuel Aduragbemi
**Date completed:** 8 November 2026

## Report

Full report with screenshots: [CCSA104_SecurityPolicy_Jegede_Samuel.pdf](CCSA104_SecurityPolicy_Jegede_Samuel.pdf)

## Summary of the work

Using SmartConsole R82 connected to the Security Management Server (A-SMS), I built an Access Control policy in the **Standard** policy package for the Orion Logistics scenario, following the Positive Control (whitelist) model.

| Task | What I did |
|---|---|
| 1 | Recorded the default Cleanup rule, showed the Hits/Track/Install On columns, and listed Global Properties categories and the policy packages (Alpha-Standard, Standard). |
| 2 | Created the objects (Internal_LAN, DMZ_Net, Admin_PC, Web_Server, Mail_Server, External_DNS) and built the rulebase. |
| 4 | Organised the rulebase into four sections: Management and Protection, DMZ Services, Outbound Access, Cleanup. |
| 6 | Enabled automatic Hide NAT (behind the gateway) for Internal_LAN and found the automatic rule in the NAT rulebase. |
| 7 | Added a temporary Drop rule, moved it, deleted it, and tried Install Policy after each change. |
| Part B | Answered the theory questions (multiple choice, short answers, scenarios). |

### Final rulebase

| No. | Name | Source | Destination | Services | Action | Track |
|---|---|---|---|---|---|---|
| 1 | Admin Access | Admin_PC | A-GW-Cluster | ssh, https | Accept | Log |
| 2 | Stealth Rule | Any | A-GW-Cluster | Any | Drop | Log |
| 3 | Inbound to DMZ | Any | Web_Server, Mail_Server | http, https, smtp | Accept | Log |
| 4 | DNS Out | Internal_LAN | External_DNS | dns | Accept | Log |
| 5 | Internal Web Out | Internal_LAN | Any | http, https | Accept | Log |
| 6 | SMTP Out | Mail_Server | Any | smtp | Accept | Log |
| 7 | Cleanup Rule | Any | Any | Any | Drop | Log |

## Limitations (stated honestly)

- **Tasks 3 and 5 and test T4 are not in the assignment brief I received**, so they were not done. The brief's rule 4 (Internal to DMZ) comes from Task 5, so it was not built.
- **The gateways were not running.** A-GW-Cluster, A-GW-01, A-GW-02 and the log server A-SME showed a red status; only A-SMS was running. All changes were made and published on A-SMS, but every Install Policy attempt in Task 7 failed, so I could not run the traffic test or read gateway logs. The failed install attempts are shown in the report.

## AI assistance disclosure

I used an AI assistant (Claude) to explain concepts, help plan the steps and review the wording of my answers. I carried out all lab steps and took all screenshots myself in my own lab environment.

## Demonstration

https://drive.google.com/file/d/1Td7WsP-wOmGtXGoLft5v3LasXdr__B-M/view?usp=sharing
