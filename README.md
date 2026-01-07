# Python Nmap Port Scanner 

This project is a Python port scanner that automates Nmap to identify exposed services on a target host. It is a practical example of reconnaissance, a core step in security testing and defensive exposure management.
Port scanning helps you understand which services are reachable over the network. Each open port represents a potential attack path, so defenders use scans to validate firewall rules, reduce unnecessary exposure and prioritise hardening. 

## Features

- Runs an Nmap scan against a target IP.
- Enables service and version detection (`-sV`).
- Runs default Nmap scripts (`-sC`) for extra context.
- Writes the raw output to `scan_results.txt`.

## How it works

The script uses the `python-nmap` wrapper to call Nmap, then prints the discovered hosts, protocols and port states. The scan target and arguments are currently set inside the script.

## Requirements

- Python 3
- Nmap installed on your machine
- `python-nmap` installed in your Python environment
- Permission to scan the target you specify

## Run it
1. Install Nmap for your operating system
2. Install the Python dependency:
   - `pip install python-nmap`
3. Update the `target` value in `Port-Scanner.py`
4. Run:
   - `python Port-Scanner.py`

## Understanding the scan results

The example output shows the host is reachable and most ports are closed, with a small set of open ports identified. :

### Open ports found

- **22/tcp (SSH)**  
  SSH is open and the scan identifies an OpenSSH version. In cybersecurity terms, this is a common administrative entry point, so you would validate key based auth, restrict access and monitor login attempts.

- **80/tcp (HTTP)**  
  HTTP is open and the scan identifies an Apache version plus basic web metadata like title and server header. This indicates a web service is exposed and should be assessed for configuration risk and patch hygiene. 

- **9929/tcp (nping-echo)**  
  This suggests an Nping echo service is reachable. From a security perspective, it is another externally reachable service that should be justified and controlled like any other exposed port. 

- **31337/tcp (tcpwrapped)**  
  `tcpwrapped` Typically means Nmap could not identify the service because the connection was closed quickly or access controls interfered with fingerprinting. In practice, this can indicate filtering, allow listing or a service that drops unexpected probes. 

## What I learned

- How port scanning supports reconnaissance and attack surface visibility.
- How to automate Nmap from Python and capture repeatable results. 
- How to interpret service detection output and relate it to exposure risk.
- Why documenting findings matters for triage, remediation and audit trails.


## Supporting Material Link

https://www.youtube.com/watch?v=tbhYxd2sfAE&list=PLI09XEwCU8CfKq50H-kUBoFme82vYOUbO&index=6
