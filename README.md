Fully automated penetration testing tool for Termux.This is a script that automates basic reconnaissance, vulnerability scanning, and brute-force attacks.

☕ Like my work? Buy me a coffee! → [paypal.me/RichCabo](https://paypal.me/RichCabo)


Features

✔️ Automated Reconnaissance – Scans target IPs for open ports and services.
✔️ Vulnerability Scanning – Uses nmap and nikto to find weaknesses.
✔️ Brute Force Attacks – Automates attacks on SSH, FTP, and web logins.
✔️ Logging & Reporting – Saves scan results for later review.
✔️ User-Friendly Menu – Runs in Termux with simple options.


Installation Requirements

Before running the script, install necessary tools in Termux:

pkg update && pkg upgrade -y
pkg install git python nmap hydra nikto -y


---

nano auto-pentest.sh

copy and paste below script.

chmod +x auto-pentest.sh

run with 
./auto-pentest.sh


Script: auto-pentest.sh

#!/bin/bash

# Automated Pentesting Script for Termux
# Author: RichCabo
# Disclaimer: Use for educational purposes only!

LOGFILE="pentest_results.txt"

# Function: Reconnaissance
recon() {
    echo "🔍 Running Recon on $1..."
    nmap -sV -A -T4 -oN recon_$1.txt $1
    echo "✔ Recon Complete! Results saved in recon_$1.txt"
}

# Function: Vulnerability Scanning
scan_vulnerabilities() {
    echo "🚨 Scanning $1 for vulnerabilities..."
    nikto -h $1 -output vuln_scan_$1.txt
    echo "✔ Vulnerability Scan Complete! Results saved in vuln_scan_$1.txt"
}

# Function: Brute Force Attack (SSH & FTP)
brute_force() {
    echo "🔥 Brute Force Attack on $1..."
    hydra -L user_list.txt -P pass_list.txt ssh://$1 -o brute_ssh_$1.txt
    echo "✔ Brute Force Complete! Results saved in brute_ssh_$1.txt"
}

# Menu
echo "=============================="
echo "   ⚡ Auto Pentest Tool ⚡   "
echo "=============================="
echo "1. Reconnaissance Scan"
echo "2. Vulnerability Scan"
echo "3. Brute Force Attack"
echo "4. Exit"
read -p "Choose an option: " choice

case $choice in
    1) read -p "Enter Target IP/Domain: " target; recon $target ;;
    2) read -p "Enter Target IP/Domain: " target; scan_vulnerabilities $target ;;
    3) read -p "Enter Target IP/Domain: " target; brute_force $target ;;
    4) exit ;;
    *) echo "❌ Invalid Option!"; exit ;;
esac


---

How to Run the Script in Termux

1. Save the script

nano auto-pentest.sh

Paste the script and press CTRL+X, then Y, and Enter to save.


2. Give Execution Permission

chmod +x auto-pentest.sh


3. Run the Script

./auto-pentest.sh




---

Security Disclaimer

This script is for educational purposes only. Using it on unauthorized systems is illegal and could result in criminal charges. Always get permission before running any penetration testing tool.


---


☕ Like my work? Buy me a coffee! → [paypal.me/RichCabo](https://paypal.me/RichCabo)

It inspires me to continue developing 

Add more automation (e.g., Metasploit integration).

Implement stealth modes to avoid detection.

Include AI-based attack predictions.


