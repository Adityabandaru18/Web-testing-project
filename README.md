
## Web Server Breach Simulation & Forensic Analysis

---

### 📌 Project Overview  
This project simulates a web server breach through multiple attack vectors and performs a forensic investigation on the compromised system. It involves capturing server logs, creating forensic disk images, analyzing them using **Autopsy**, and generating a manual forensic report detailing the breach points and attacker activity.

---

### 📌 Problem Statement  

- Modern servers are constantly at risk of being attacked by unauthorized users.  
- Failure to detect and document such breaches can lead to prolonged data leaks, financial loss, and legal complications.  
- Without forensic imaging and analysis, it is difficult to validate the occurrence and nature of a breach.  
- Timely data acquisition and log preservation is crucial before evidence is lost or tampered.

---

### 📌 How the Solution Was Achieved  

- Performed attacks on a vulnerable web application (DVWA) using **Hydra** for brute force attempts.  
- Captured server logs: `access.log`, `error.log`, `auth.log` after the attacks.  
- Created forensic disk images of the log files using **dc3dd**, ensuring data integrity by generating hashes.  
- Analyzed these `.dd` images in **Autopsy** to extract attacker IPs, login attempts, suspicious activities, and more.  
- Compiled findings into a structured forensic report recommending future countermeasures.

---

### 📌 Impact If Not Addressed  

- Breaches would go undetected, resulting in financial and data loss.  
- Legal proceedings would lack strong, admissible evidence.  
- Critical attack traces could be lost if not imaged immediately.  
- Organizations would remain exposed, unaware of exploitable vulnerabilities.

---

### 📌 Commands Used  

**🔐 Hydra Brute Force Attack:**
```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.0.2.15 http-post-form "/dvwa/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed"
```

**📑 Collecting Logs:**
```bash
cat /var/log/apache2/access.log
cat /var/log/apache2/error.log
cat /var/log/auth.log
```

**📝 Creating Disk Image using dc3dd:**
```bash
sudo dc3dd if=/var/log/apache2/access.log of=access_log.dd hash=md5 log=access_log_hash.txt
```

(Repeat similarly for other log files.)

**📊 Autopsy Analysis:**
- Open Autopsy.
- Create a new case.
- Add the `.dd` image.
- Browse the extracted files, analyze browser history, logins, attacker IPs, and event timelines.

---

### 📸 Working Images  

### Kali linux (attacker)
![Screenshot 2025-04-20 142717](https://github.com/user-attachments/assets/a5801965-ce54-4ff3-b9fe-8b37cc39d4c5)

### Victim (Ubuntu)
![Screenshot 2025-04-20 143031](https://github.com/user-attachments/assets/a4f29861-6df3-4fb6-a575-f5391c0af0c3)

### Autopsy (Forensic)
![Screenshot 2025-04-20 143227](https://github.com/user-attachments/assets/1ade470e-89e3-4ea5-9c42-e5305ae0fb27)

### 📌 Conclusion  

- Successfully simulated attacks on a vulnerable web server.  
- Collected logs post-attack and created forensic images with hash verification.  
- Analyzed `.dd` images using Autopsy, retrieving attacker activity and intrusion traces.  
- Compiled a manual forensic report documenting the findings and recommending system hardening measures.

---

### 📌 Future Scope  

- Integrating real-time log acquisition and automated imaging.  
- Implementing intrusion detection systems to alert on unusual activities.  
- Automating forensic report generation using scripting tools.  
- Extending the forensic process to memory dumps and database breaches.

---

### 📑 Manual Forensic Report  

👉 [**View Full Forensic Report Here**](https://github.com/Adityabandaru18/Web-testing-project/blob/main/Forensic_report.pdf)

---

### Demo Video
 👉 [**Watch the Demo video here**](https://drive.google.com/file/d/17Kkkx-b6RuFH3m6XMeEokMuKXbTo3z6p/view)
