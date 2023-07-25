# Cyber Security Links and Resources
---
#### *This will be a list of resources I have encountered while studying various topics relating to security. I will do my best to categorize them based on purpose. Will be a continous work in progress.*

## OSINT
- https://osintframework.com/
-- From the site's homepage, "OSINT framework focused on gathering information from free tools or resources. The intention is to help people find free OSINT resources. Some of the sites included might require registration or offer more data for $$$, but you should be able to get at least a portion of the available information for no cost."
-- Bubble/tree chart of various OSINT tools and site. Super helpful.

## Cyber Threat Intelligence
- https://urlscan.io/
-- From tryhackme, "... is a free service developed to assist in scanning and analysing websites. It is used to automate the process of browsing and crawling through websites to record activities and interactions. When a URL is submitted, the information recorded includes the domains and IP addresses contacted, resources requested from the domains, a snapshot of the web page, technologies utilised and other metadata about the website. The site provides two views, the first one showing the most recent scans performed and the second one showing current live scans."
-- Cool site that helps analyze website's behaviors for potentially malicious actions/content.

- https://abuse.ch/
--  a research project hosted by the Institue for Cybersecurity and Engineering at the Bern University of Applied Sciences in Switzerland. It was developed to identify and track malware and botnets through several operational platforms developed under the project. Has links on it's front page to the various services it offers.
-- 'Main hub' of the various abuse.ch projects.

- https://bazaar.abuse.ch/
-- an all in one malware collection and analysis database. This site features:
**Malware Samples Upload**: Security analysts can upload their malware samples for analysis and build the intelligence database. This can be done through the browser or an API. 
**Malware Hunting**: Hunting for malware samples is possible through setting up alerts to match various elements such as tags, signatures, YARA rules, ClamAV signatures and vendor detection.
-- Says it all above. Place to get and submit malware samples. Not like VT, no virus scanning here. 

- https://feodotracker.abuse.ch/
-- From the site, "... a project of abuse.ch with the goal of sharing botnet C&C servers associated with Dridex, Emotet (aka Heodo), TrickBot, QakBot (aka QuakBot / Qbot) and BazarLoader (aka BazarBackdoor). It offers various blocklists, helping network owners to protect their users from Dridex and Emotet/Heodo."
-- Features a list of botnet C2 servers associated with various campaigns. Includes blocklists of the information gathered as well for 'easy' usage.

- https://sslbl.abuse.ch/
-- From the site, "The SSL Blacklist (SSLBL) is a project of abuse.ch with the goal of detecting malicious SSL connections, by identifying and blacklisting SSL certificates used by botnet C&C servers. In addition, SSLBL identifies JA3 fingerprints that helps you to detect & block malware botnet C&C communication on the TCP layer."
-- Site to share and search for mal SSL connections. Also has JA3 fingerprints to help you detect and block C2 comms at the TCP layer.

- https://urlhaus.abuse.ch/
-- From the site, "URLhaus is a project from abuse.ch with the goal of sharing malicious URLs that are being used for malware distribution.""
-- Site to share and search mal URLs.

- https://threatfox.abuse.ch/
-- From the site, "ThreatFox is a free platform from abuse.ch with the goal of sharing indicators of compromise (IOCs) associated with malware with the infosec community, AV vendors and threat intelligence providers."
-- Site to share and search for IOCs.

- https://talosintelligence.com/
-- Site run by Cisco. According to tryhackme, "... to provide actionable intelligence, visibility on indicators, and protection against emerging threats through data collected from their products."
-- A site where Cisco aggregates tons of cyber threat intelligence. P cool.

## Phishing
- https://www.phishtool.com/
-- From tryhackme, "seeks to elevate the perception of phishing as a severe form of attack and provide a responsive means of email security. Through email analysis, security analysts can uncover email IOCs, prevent breaches and provide forensic reports that could be used in phishing containment and training engagements."
-- Basically a tool to help you analyze emails to search fror signs of phishing. Need to create an account but offers a free Community version and paid Enterprise version.

## Malware Analysis
- https://cuckoosandbox.org/
-- An open source automated malware analysis system. 
