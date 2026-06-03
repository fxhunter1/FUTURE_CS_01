FUTURE_CS_02 – Vulnerability Assessment Report
Author: ABDILLAH MOH'D SAID
CIN ID: FIT/MAY26/CS8225
Date: May 2026
Task: Vulnerability Assessment Report for a Live Website (Read-Only Scope)

Project Overview
This repository contains the deliverables for Cyber Security Task 1 assigned by Future Interns.

The task involved performing a read-only vulnerability assessment on a publicly available practice website in order to identify common security weaknesses and document them in a professional report format.

The assessment was conducted using passive reconnaissance techniques, meaning no exploitation or intrusive attacks were performed.

Target Website Application: DVWA (Damn Vulnerable Web Application) IP Address: 127.0.0.1 (localhost) Purpose: Publicly available vulnerable web application used for security testing and education

Tools Used
Nmap
Used for basic port scanning and service detection.

Example command used: nmap -sV -Pn localhost

Purpose:

Identify open ports
Detect running services
Gather service version information
WhatWeb
Used to detect the technology stack and server configuration of the target website.

Example command: whatweb -v http://localhost

Detected technologies:

Apache server 2.4.25
PHP backend
PHPSESSID cookies
DVWA framework
Evidence saved as: evidence/whatweb.txt evidence/screenshots

Curl (Security Headers Analysis)
Used to analyze HTTP security headers of the web application.

Key results identified missing security headers such as:

Content-Security-Policy
X-Frame-Options
X-Content-Type-Options
Referrer-Policy
The scan also detected:

Website served over HTTP
Server information disclosure
Deliverables Included
Vulnerability_Assessment_Report.pdf
README.md
Evidence folder contains:

whatweb.txt
nmap_scan.txt
headers.txt
cookies.txt
Screenshots of scan outputs
These files document the findings gathered during the assessment.

Key Findings Summary
Missing Security Headers

Several recommended HTTP security headers were not configured:

Content-Security-Policy
X-Frame-Options
X-Content-Type-Options
Referrer-Policy
These headers help protect websites against:

Cross-Site Scripting (XSS)
Clickjacking attacks
MIME-type sniffing
Information leakage
Server Information Disclosure

The server exposes detailed version information:

Server: Apache/2.4.25 (Debian)
PHP version (implied)
This may allow attackers to identify potential vulnerabilities related to the server software.

Cookie Security Weakness

The application uses a session cookie:

PHPSESSID
While it includes the HttpOnly flag, it lacks the Secure and SameSite attributes, which may increase risk of session hijacking and Cross-Site Request Forgery (CSRF) attacks.

Open Ports Discovered

Nmap scan revealed:

Port 22 (SSH) - OpenSSH 10.2p1
Port 80 (HTTP) - Apache 2.4.25
Port 3306 (MySQL) - MariaDB 11.8.6
Overall Risk Level
Low – Medium

The vulnerabilities discovered mainly involve misconfigurations and information disclosure, which could assist attackers during reconnaissance phases.

Scope and Methodology
Allowed activities:

Passive reconnaissance
Header inspection
Technology fingerprinting
Service identification
Not performed:

Exploitation
SQL Injection testing
Brute force attacks
Directory brute forcing
Denial-of-Service attacks
All testing was conducted in read-only mode, respecting ethical guidelines.

References
OWASP Web Security Testing Guide
Sample vulnerability reports from GitHub (as suggested in the task)
