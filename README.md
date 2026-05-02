# SOC-Lab-Portfolio
Hands-on blue team labs and forensics investigations for SOC portfolio.

# WebStrike - Network Forensics Investigation
**Platform:** CyberDefenders | **Difficulty:** Easy | **Category:** Network Forensics | **Completed:** April 2026

## What This Is
This was my first CyberDefenders lab. The goal was to dig through a real packet capture and figure out how an attacker got into a web server, what they uploaded, and what they took.

## Tools
- Wireshark
- IPGeolocation.io

## What Happened
The attacker was coming from Tianjin, China. They found a file upload page on the site and uploaded a PHP web shell disguised as an image called image.jpg.php. The server accepted it. From there they opened a reverse shell connection back to their machine on port 8080 and used it to pull the /etc/passwd file off the server which has every user account on it.

## What I Found
- Attacker IP: 117.11.88.124 (Tianjin, China)
- Web shell: image.jpg.php
- Reverse shell port: 8080
- Stolen file: /etc/passwd

## What I Learned
File upload forms need to validate file types on the server side not just the front end. The double extension trick image.jpg.php is a common way attackers bypass basic filters. Any outbound connection on a weird port right after a file upload should be an immediate alert in a SOC environment.
