# CVE-2024-21413 | Microsoft Outlook Remote Code Execution Vulnerability PoC

## 📜 Description

This script presents a proof of concept (PoC) for CVE-2024-21413, a significant security vulnerability discovered in Microsoft Outlook with a CVSS of 9.8. Termed the #MonikerLink bug, this vulnerability has far-reaching implications, including the potential leakage of local NTLM information and the possibility of remote code execution. Moreover, it highlights an attack vector that could bypass Office Protected View, thereby extending its threat to other Office applications.

## 🚀 Usage

Use this tool responsibly and ensure you have authorization from the target system's owner. This script requires SMTP authentication to send an email, bypassing SPF, DKIM, and DMARC checks, which helps in simulating a real-world attack scenario more effectively.

```bash
python CVE-2024-21413.py --server "<SMTP server>" --port <SMTP port> --username "<SMTP username>" --password "<SMTP password>" --sender "<sender email>" --recipient "<recipient email>" --url "<link URL>" --subject "<email subject>"
```

**Parameters:**

- `--server`: SMTP server hostname or IP.
- `--port`: SMTP server port.
- `--username`: SMTP server username for authentication.
- `--password`: SMTP server password for authentication.
- `--sender`: Sender email address.
- `--recipient`: Recipient email address.
- `--url`: Malicious path to include in the email.
- `--subject`: Email subject.

### Initial Sending 

<img width="730" alt="image" src="https://github.com/xaitax/CVE-2024-21413-Microsoft-Outlook-Remote-Code-Execution-Vulnerability/assets/5014849/5b68f853-e278-48cc-98fa-f560509d7d44">

### Display in Outlook (no warnings, no Protected view)

![image](https://github.com/xaitax/CVE-2024-21413-Microsoft-Outlook-Remote-Code-Execution-Vulnerability/assets/5014849/914110cb-ee5d-432a-bac5-c8243015658a)

### Wireshark capture including NTLM credentials (you can also run impacket, alternatively)

<img width="604" alt="image" src="https://github.com/xaitax/CVE-2024-21413-Microsoft-Outlook-Remote-Code-Execution-Vulnerability/assets/5014849/89edf325-9a16-4977-be3a-4e9064bb003f">

## 🧐 Why SMTP Authentication?

SMTP authentication is crucial for this demonstration to ensure the email sent bypasses common email validation checks such as SPF (Sender Policy Framework), DKIM (DomainKeys Identified Mail), and DMARC (Domain-based Message Authentication, Reporting, and Conformance). These security measures are designed to detect and prevent email spoofing, where attackers send emails from a forged address. By using authenticated SMTP, the demonstration closely mimics how a sophisticated attacker might circumvent these protections, making the testing environment more realistic and highlighting the importance of comprehensive email security practices.

## Demos

### 0-click NTLM Leak

![CVE-2024-21413-NTLM_Leak-0-click-Text](https://github.com/xaitax/CVE-2024-21413-Microsoft-Outlook-Remote-Code-Execution-Vulnerability/assets/5014849/8e23f3cd-1904-4d3e-b5d3-a0b58c0318b7)

### 1-click Remote Code Execution (RCE)

![CVE-2024-21413-RCE](https://github.com/xaitax/CVE-2024-21413-Microsoft-Outlook-Remote-Code-Execution-Vulnerability/assets/5014849/cd0dbae7-aaec-4532-9114-b58239fe5775)

## 📆 Changelog

### [19. February 2024] - Added 0-Click NTLM Leak

- Confirmed and managed 0-click NTLM Leak (thanks to [JT](https://x.com/johntroony)!)
- Not yet published

### [18. February 2024] - Added 1-click RCE

- Managed & confirmed Microsoft Outlook Remote Code Execution (RCE)
- Not yet published

### [16. February 2024] - Initial Release

- Initial release showcasing the exploit for CVE-2024-21413.

## Credits

- [Checkpoint](https://research.checkpoint.com/2024/the-risks-of-the-monikerlink-bug-in-microsoft-outlook-and-the-big-picture/) has done all the amazing research.
- [Microsoft Security Advisory](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2024-21413)

## 📌 Author

**Alexander Hagenah**
- [Website](https://primepage.de)
- [Twitter](https://twitter.com/xaitax)
- [LinkedIn](https://www.linkedin.com/in/alexhagenah/)

## ⚠️ Disclaimer

This tool is intended for educational and ethical testing purposes only. Unauthorized scanning, testing, or exploiting of systems is illegal and unethical. Ensure you have explicit, authorized permission to engage in any testing or exploitation activities against target systems.


