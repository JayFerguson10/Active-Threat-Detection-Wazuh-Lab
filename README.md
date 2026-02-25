# 🛡️ Active Threat Detection & SIEM Home Lab

**The Goal:** I built this lab to step into the shoes of a SOC Analyst. I wanted to move beyond theory and get hands-on experience setting up a real logging pipeline, executing a simulated attack, and actually catching the threat in a SIEM.

**The Setup:**
**Built the Environment:** I spun up a Windows 10 virtual machine and connected it to my Wazuh SIEM manager using the Wazuh agent.
**Configured Audit Policies:** I navigated into the Windows Local Security Policy (`secpol.msc`) to manually enable Success/Failure auditing for local Logon Events.
**Applied Configurations:** I ran `gpupdate /force` in the command prompt to ensure Windows immediately started tracking authentication attempts.

**The Attack Simulation:**
**Executed the Breach Attempt:** I used the Windows command line to simulate an attacker trying to force their way into a restricted account. I ran `runas /user:FakeHacker cmd.exe` and fed it a bad password to intentionally trigger a failed authentication error.

**The Results:**
**Caught the Threat:** My Wazuh dashboard successfully ingested the alert in real-time.
**Analyzed the Raw Data:** I dug into the raw log details to verify the catch, matching the exact threat indicators: the target user (`FakeHacker`) and the specific Windows Event ID (`4625` - Logon Failure).

**What I Learned:**
**Windows is Quiet by Default:** Out-of-the-box Windows doesn't record failed logins. I learned that you have to explicitly configure the OS to audit specific actions before a SIEM has any data to analyze.
**Filtering the Noise:** My SIEM ingested over 1,300 normal background events in minutes. Knowing specific Event IDs (like `4625`) is absolutely crucial for filtering out the noise and hunting down the actual attack.
**Troubleshooting the Pipeline:** When alerts didn't show up immediately, I learned to verify the raw logs locally in Windows Event Viewer first. This proved the OS was actually writing the data before I started troubleshooting the SIEM dashboard.

**Skills Gained:** Wazuh SIEM, Windows Event Viewer, Security Policy Configuration, Endpoint Detection and Response (EDR), Log Analysis, Troubleshooting.

---

### The Attack Simulation
![Attack Origin](windows%20box%20command%20promt%20Login%20failed%20attemtp.png)

### The Detection Alert
![Rule Description](Rule%20Description.png)

### The Raw Evidence
![Event Data](Win%20event%20Data%20&%20Win%20system%20event.png)
