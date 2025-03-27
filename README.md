# ActiveDirectoryProject
Homelab simulating enterprise Active Directory with SIEM and SOAR integrations.

ActiveDirectoryProject/<br/>
├── README.md<br/>
├── Homelab.png<br/>
├── SIEM/<br/>
│   └── Sysmon_Splunk_Writeup.md<br/>
├── SOAR/<br/>
│   └── SOAR Diagram.pdf<br/>
│   └── SoarDetections.png<br/>


# Sysmon + Splunk Setup & Detection Report

## Environment Summary
- Sysmon and Splunk Forwarder installed on target endpoints.
- Endpoint event reporting successfully configured.
- DC1 is the Active Directory manager:
  - IT and HR user accounts created.
  - RDP configured and verified.

## Attack Simulation
- **Attacker:** Kali Linux VM
  - Password list prepared.
  - Crowbar installed and launched against the target (in 192.168.10.0/24).
  - Brute-force attack successful.

## Detection Events
- **Failed Logins:** Event ID 4625 (~20 attempts), detected in Splunk.
- **Successful Login:** Event ID 4624 from Kali VM.

## Threat Emulation
- Installed Git & added to path.
- Downloaded Atomic Red Team.
- Created a local user with:  
  `Invoke-AtomicTest T1136.001`
- **Event captured in Splunk.**

## Additional TTPs Tested
- T1059.001 (PowerShell execution)
- Windows Defender blocked threats.
- All events logged and verified in Splunk.
