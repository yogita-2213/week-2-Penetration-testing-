# week-2-Penetration-testing-
This repository documents my learning journey in Ethical Hacking, Penetration Testing, Network Security, and Vulnerability Assessment.
### Footprinting & Network Scanning Phases

**W2-PM-FINAL  |  CYBERSECURITY  |  NETWORKWALKS**

| Field | Detail |
|---|---|
| **Pentester Name (Cybersecurity Professional)** | **Emmanuel Bafi** |
| **Program/Batch** | B082-Networkwalks |
| **Date** | 12 November 2026 |
| **Modules completed** | W2-PM1 (Multiple Kali Tools)<br>W2-PM5 (Zenmap Scanning) |
| **Client/Target** | 1. Networkwalks (secured written permission already)<br>2. My own local LAN Network |
| **Permission secured from client?** | Yes |
| **Phases covered** | **Phase 1:** Reconnaissance & Footprinting<br>**Phase 2:** Scanning & Network Discovery<br>**Phase 3-5:** In Progress |

# ⚖️ 1. Liability Disclaimer

> **🔐 Ethical Hacking | Cybersecurity | Authorized Security Testing**

This penetration testing report is prepared strictly for educational, research, and authorized security assessment purposes.

All security testing activities documented in this repository are intended to be performed only on systems, networks, and applications for which explicit permission has been granted by the respective owner.

### ⚠️ Important Notice

- Unauthorized access to computer systems or networks is strictly prohibited.
- The information provided in this report must not be used for illegal activities.
- The author is not responsible for any misuse, damage, data loss, or unauthorized activities resulting from the use of this information.
- All tools and techniques are demonstrated for ethical hacking and defensive security purposes only.

### 🛡️ Legal Responsibility

By accessing or using this repository, you agree that you are solely responsible for ensuring that your security testing activities comply with applicable laws, regulations, and authorization requirements.


# 🔐 Introduction

Penetration Testing is a cybersecurity practice used to identify and evaluate security vulnerabilities in websites, networks, and computer systems.

In this project, I am performing an authorized penetration testing assessment of **NetworkWalks (networkwalks.com)** using various tools available in Kali Linux.

The main purpose of this project is to gain practical knowledge of ethical hacking, footprinting, reconnaissance, and information gathering techniques.

This assessment helps me understand how security vulnerabilities can be identified and how organizations can improve their overall security posture.

All testing activities are conducted with proper authorization and are intended strictly for educational and research purposes.

**"Think Like a Hacker, Secure Like a Professional."** 🔐

# 🛠️ Tools Used

The following tools are used during this penetration testing assessment to perform footprinting, reconnaissance, information gathering, and security analysis using Kali Linux.

- **WHOIS** – Domain registration information gathering.
- **NSLOOKUP** – DNS lookup and IP address identification.
- **DIG** – DNS record analysis.
- **HOST** – Domain and DNS information lookup.
- **WhatWeb** – Website technology fingerprinting.
- **TheHarvester** – OSINT and publicly available information gathering.
- **Nmap** – Network scanning and service detection.
- **cURL** – HTTP response and header analysis.
- **Kali Linux** – Operating system and platform for performing security assessment activities.

# 4. Activities Performed
## 4.1 Footprinting & Reconnaissance
I performed reconnaissance against the `networkwalks.com` domain using six Kali Linux tools: **WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon**. Each tool was used to collect a different type of information about the target.

First, I used **WHOIS** to obtain publicly available domain registration information and identify the domain’s name servers. The results provided information about the domain registration and hosting infrastructure.

I then used **WhatWeb** to identify technologies used by the website. The results identified **WordPress 7.0.4** and **WP Download Manager 3.3.58**, along with other information exposed by the website.

Using **Nslookup**, I resolved the domain name to its IP address. The provided result identified **192.232.216.135**.

I used **Curl** with the `-I` option to inspect the HTTP response headers. This provided additional information about the web application and exposed the WordPress REST API endpoint `/wp-json/`.

Next, I used **Wafw00f** to determine whether a Web Application Firewall was protecting the website. The result identified **ModSecurity (SpiderLabs)**.

Finally, I used **DNSRecon** to enumerate DNS records. The results provided information relating to name servers, mail servers, SPF/TXT records, service records and DNS software information.

## 4.2 Network Scanning with Zenmap

For the second activity, I used **Zenmap** to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.

I first used the Windows `ipconfig` command to identify my local IP address and LAN subnet. I then entered the subnet into Zenmap and selected **Ping Scan** to identify active hosts.

The example results provided in the practical identified four live hosts:
- `192.168.56.1`
- `192.168.56.2`
- `192.168.56.24`
- `192.168.56.5`

The example results also included four MAC addresses.

After completing the scan, I opened the **Topology** section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task.


# 5. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.

| **\#** | **Risk / Finding**                           | **Evidence / Observation**                                  | **Potential Impact**                                                                                            | **Risk Level** |
|--------|----------------------------------------------|-------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|----------------|
| 1      | Web technology information exposed           | WhatWeb identified WordPress and WP Download Manager        | Attackers may use exposed technology/version information to identify software requiring further security review | **● Medium**   |
| 2      | Server IP address identifiable               | Nslookup resolved the domain to `192.232.216.135`           | Provides information about the network location of the web service                                              | **● Low**      |
| 3      | HTTP technical information exposed           | Curl returned HTTP response headers and exposed `/wp-json/` | May assist technology fingerprinting and further enumeration                                                    | **● Low**      |
| 4      | WAF technology identifiable                  | Wafw00f identified ModSecurity (SpiderLabs)                 | Reveals information about the web application’s security architecture                                           | **● Low**      |
| 5      | DNS infrastructure information exposed       | DNSRecon identified DNS, mail and service-related records   | DNS information can help build a broader infrastructure profile                                                 | **● Medium**   |
| 6      | Multiple live hosts visible on local network | Zenmap identified four live hosts in the example network    | Unknown or unauthorized devices may potentially be present on a network                                         | **● Medium**   |

**Risk level key:** ● Critical ● Medium ● Low

The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities.

The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these two modules.

Therefore, the presence of information such as a software version, IP address or DNS record does not by itself mean that the system is vulnerable. Further authorized security testing would be required to confirm any actual vulnerability.

# 6. Recommendations

Based on the observations from these activities, I recommend the following security improvements:

1.  **Review publicly exposed technology information**  
    Organizations should regularly review what information about their web technologies, CMS and plugins is publicly visible.

2.  **Keep software updated**  
    CMS platforms, plugins and other web technologies should be regularly updated and reviewed against current security advisories.

3.  **Review HTTP headers**  
    HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.

4.  **Review DNS records regularly**  
    DNS records should be checked periodically to ensure that only required information and services are publicly exposed.

5.  **Properly configure and monitor the WAF**  
    Keep the WAF (ModSecurity) enabled and tuned, since it already blocks naive attacks.

6.  **Perform regular internal network discovery**  
    Organizations should periodically scan their own networks to identify active devices.

7.  **Investigate unknown devices**  
    Any unexpected device discovered during network scanning should be investigated and verified.

8.  **Maintain network documentation**  
    Network topology and device information should be documented and updated regularly.

9.  **Perform security testing with authorization**  
    Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided.

# 7. Conclusion

During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical activities covering footprinting, reconnaissance and network scanning.

In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. I learned how WHOIS can provide domain information, WhatWeb can identify web technologies, Nslookup can resolve domain names, Curl can inspect HTTP headers, Wafw00f can identify a WAF, and DNSRecon can provide additional DNS information.

In the network scanning activity, I used Zenmap to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.

The exercises showed me that information gathering is an important part of cybersecurity. Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses.

I also learned that technical findings should be documented clearly. A good cybersecurity report should explain what was performed, what was discovered, what the observation means, what risk it may create, and what can be done to reduce that risk.

Finally, I learned that reconnaissance and scanning must always be performed within an authorized scope. These activities were completed as part of the assigned educational cybersecurity lab.

# 8. Evidences Collected
![image alt](https://github.com/yogita-2213/week-2-Penetration-testing-/blob/6abbd51c20ee6db34e80d815421ca9a6c602cf81/Screenshot%202026-11-13%20164655.png)

![image alt](https://github.com/yogita-2213/week-2-Penetration-testing-/blob/964209fa7b90aca295b4f74d5a47a8e3e016271d/Screenshot%202026-11-13%20171104.png)

![image alt](https://github.com/yogita-2213/week-2-Penetration-testing-/blob/c55749678fe9cd934096dffebcc4c60405ee2d23/Screenshot%202026-11-13%20171120.png)

![image alt](https://github.com/yogita-2213/week-2-Penetration-testing-/blob/404647d2fc63a245e71cb2389f35281ef576bafc/Screenshot%202026-11-13%20170255.png)

![image alt](https://github.com/yogita-2213/week-2-Penetration-testing-/blob/00e59395cebcf23f1bb4dba597f654ec4cc19875/Screenshot%202026-11-13%20170136.png)


![image alt](https://github.com/yogita-2213/week-2-Penetration-testing-/blob/383cfaa0085f1b0707359ae7db4b4770becad243/Screenshot%202026-11-13%20170443.png)

![image alt](https://github.com/yogita-2213/week-2-Penetration-testing-/blob/02e9dace345f5699826f5f323456fad8e72d5596/Zenmap%20Network%20Scan%20Results.png)
