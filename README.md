# 🛡️ Active Threat Detection & SIEM Home Lab

**The Goal:** I wanted to get hands-on experience with how Security Operations Centers (SOCs) actually monitor and catch threats. To do this, I built a home lab to simulate an attack and catch it in real-time.

**What I Did:**
* 💻 **Deployed a SIEM:** I set up a Windows 10 virtual machine and connected it to a Wazuh SIEM to forward security logs.
* ⚙️ **Tweaked Security Policies:** I configured the Windows Local Security Policy to start logging failed and successful logins (since Windows doesn't do this by default!).
* 💥 **Simulated an Attack:** I played the role of the attacker by trying to force my way into a fake account (`FakeHacker`) using the command prompt.

**The Results:**
* 🎯 My SIEM successfully caught the break-in attempt! 
* 🔎 I was able to track down the exact logs in my Wazuh dashboard, proving the attack happened by matching the target user (`FakeHacker`) and the exact Windows Event ID (`4625`).

**Skills Gained:** Wazuh SIEM, Windows Event Viewer, Security Policy Configuration, Endpoint Detection and Response (EDR), Log Analysis.

---

### 💻 The Attack Simulation
![Attack Origin](windows%20box%20command%20promt%20Login%20failed%20attemtp.png)

### 🚨 The Detection Alert
![Rule Description](Rule%20Description.png)

### 🔍 The Raw Evidence
![Event Data](Win%20event%20Data%20&%20Win%20system%20event.png)
