# Journal

---

## Date: September 15, 2026 | Entry: #1

**Description:** Documenting a ransomware incident at a small U.S. healthcare clinic.

**Tool(s) used:** None. This entry is a documentation exercise based on a provided incident scenario, not a live investigation.

**The 5 W's:**

- **Who:** An organized cybercriminal group known for targeting the healthcare and transportation sectors.
- **What:** A ransomware attack that encrypted the clinic's files, including patient records, and displayed a ransom note demanding payment for the decryption key.
- **When:** Tuesday, approximately 9:00 a.m.
- **Where:** On the clinic's internal computer systems and network.
- **Why:** The attackers got in through a phishing email carrying a malicious attachment; once an employee opened it, malware installed on that machine and the attackers used that foothold to deploy ransomware across the network. The ransom demand points to a financial motive rather than, say, data destruction for its own sake or a targeted attack tied to the clinic specifically.

**Additional notes:** The attack chain here is a reminder that the technical failure (ransomware encrypting files) is downstream of a human one (a phishing email getting opened), which means the highest-leverage fix is probably email filtering and phishing awareness training rather than anything purely technical. I'd also want to know whether the clinic had offline or immutable backups, since that answers the "should we pay the ransom" question almost by itself: if clean backups exist, restoring from them avoids funding the attackers and offers no guarantee the decryption key even works. If backups were also encrypted or don't exist, that's a much harder call involving legal counsel, cyber insurance, and law enforcement, not just a security team decision.

---

## Date: September 17, 2026 | Entry: #2

**Description:** Investigating a malicious file hash using VirusTotal for a financial services company SOC alert, and mapping the resulting IoCs to the Pyramid of Pain.

**Tool(s) used:** VirusTotal.

**The 5 W's:**

- **Who:** The malware was identified as Flagpro, a family associated with BlackTech, an advanced persistent threat group.
- **What:** A password-protected file attachment led to a malicious payload executing and creating multiple unauthorized executable files on an employee's machine.
- **When:** 1:11 PM (email received) through 1:20 PM (SOC alert triggered), roughly a nine-minute window from delivery to detection.
- **Where:** On an employee's workstation at a financial services company, with outbound network activity to attacker-controlled infrastructure.
- **Why:** The password-protected attachment was almost certainly intended to slip past automated attachment scanning, since many scanners can't inspect the contents of an encrypted archive without the password, which is a detail worth remembering for future email security control reviews.

**Additional notes:** This is the first time I've walked a single artifact all the way up the Pyramid of Pain instead of just noting one IoC. It reinforced that the easy indicators (hash, IP) are almost disposable from the attacker's side, so a detection strategy that stops at those two levels is only ever playing catch-up. I want to get more comfortable reading MITRE ATT&CK technique IDs directly out of sandbox reports rather than just the plain-English behavior description, since that's the level of detail that actually transfers into a SIEM detection rule.

**Related project:** [pyramid-of-pain-malware-analysis](https://github.com/mmanzanares7/pyramid-of-pain-malware-analysis)

---
