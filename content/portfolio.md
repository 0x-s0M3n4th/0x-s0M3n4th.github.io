---
title: "Portfolio"
layout: "page"
url: "/portfolio/"
summary: "System Administration, Blue Teaming, and Red Team Operations."
---

<div style="display: flex; justify-content: center; margin-bottom: 20px;">
    <img src="/images/fun.jpeg" alt="Profile Image" style="border-radius: 50%; width: 200px; height: 200px; object-fit: cover; border: 2px solid var(--primary);">
</div>
<div class="nav-wrapper">
  <nav class="sticky-nav" id="stickyNav">
    <a href="#about-me" class="nav-item">About Me</a>
    <a href="#skills--technologies" class="nav-item">Skills</a>
    <a href="#projects" class="nav-item">Projects</a>
    <a href="#certifications--courses" class="nav-item">Certifications</a>
    <a href="#experience" class="nav-item">Experience</a>
    <a href="#ctfs" class="nav-item">CTFs</a>
    <a href="#contact" class="nav-item">Contact</a>
  </nav>
</div>

<style>
/* 1. Container - Sticks to Top */
.nav-wrapper {
  position: sticky;
  top: 0;
  z-index: 1000;
  background: var(--theme); /* Blends with your background */
  padding: 10px 0;
  border-bottom: 1px solid var(--border);
  margin-bottom: 30px;
}

/* 2. Slider Track */
.sticky-nav {
  display: flex;
  overflow-x: auto;
  gap: 10px;
  padding: 0 15px;
  scrollbar-width: none; /* Firefox hide scrollbar */
}
.sticky-nav::-webkit-scrollbar { display: none; } /* Chrome hide scrollbar */

/* 3. Buttons */
.nav-item {
  color: var(--primary);
  background: var(--entry);
  padding: 8px 16px;
  border-radius: 20px;
  white-space: nowrap;
  font-size: 0.9rem;
  font-weight: 500;
  text-decoration: none !important;
  border: 1px solid var(--border);
  transition: all 0.3s ease;
}

/* 4. Active State (When you scroll to it) */
.nav-item.active {
  background: var(--primary);
  color: var(--theme) !important;
  font-weight: bold;
  transform: scale(1.05);
}
</style>

<script>
document.addEventListener("DOMContentLoaded", () => {
  const navLinks = document.querySelectorAll('.nav-item');
  const navContainer = document.getElementById('stickyNav');

  // Watch for sections entering the screen
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      // If a section is in the middle of the screen
      if (entry.isIntersecting) {
        // 1. Reset all buttons
        navLinks.forEach(link => link.classList.remove('active'));
        
        // 2. Highlight the matching button
        const id = entry.target.getAttribute('id');
        const activeLink = document.querySelector(`.nav-item[href="#${id}"]`);
        
        if (activeLink) {
          activeLink.classList.add('active');
          
          // 3. Auto-scroll the nav bar to keep the button visible
          const scrollLeft = activeLink.offsetLeft - (navContainer.offsetWidth / 2) + (activeLink.offsetWidth / 2);
          navContainer.scrollTo({ left: scrollLeft, behavior: 'smooth' });
        }
      }
    });
  }, {
    rootMargin: "-20% 0px -60% 0px" // Trigger when section is near top of screen
  });

  // Attach observer to the actual H2 headers
  navLinks.forEach(link => {
    const id = link.getAttribute('href').substring(1); // remove '#'
    const section = document.getElementById(id);
    if (section) {
      observer.observe(section);
    } else {
      console.warn(`Header ID not found: #${id}. Check your spelling!`);
    }
  });
});
</script>


## About Me
I am a **3rd-year student** in **Lovely Professional University** and yes a normal guy just like you, my core focus is on **Infrastructure Security**, **Adversary Emulation**, **Administering different tasks**, **Blue team operations**. Unlike typical red teamers, I believe in mastering the defensive side first—diving deep into **Linux & Windows System Administration** to understand exactly what I am attacking or protecting.

I prefer a hands-on, research-driven approach, utilizing extensive home labs to simulate **Phishing Campaigns**, set up basic **C2 Operations**, and practice **Blue Team** monitoring. Currently, I am also refining my low-level programming skills in **C** to better understand operating system internals.

---

## Skills & Technologies

### **System Administration**
- **Linux:** Deep knowledge of permissions, process management, Bash scripting, and service configuration.
- **Windows:** Active Directory (AD) deployment, GPO management, PowerShell automation, and domain hardening.

### **Security Operations**
- **Red Teaming:** Phishing Campaign Development, Basic C2 Infrastructure (setup & connectivity), Active Directory Exploitation.
- **Blue Teaming:** Log Analysis, SIEM fundamentals, Windows Forensics, Linux Forensics, and System Hardening.

### **Languages & Tools**
- **Languages:** Python (Automation), C (Low-level dev), Bash, powershell.
- **Tools:** Metasploit, Burp Suite, Wireshark, Sysinternals, Powershell Empire, shellter, Evilginx2, GoPhish, BloodHound, Mimikatz, Responder, NetExec, ffuf, proxychains, suricata, wazuh

---

## Projects

### **1. [Enterprise Home Lab & Adversary Emulation](https://0x-s0m3n4th.github.io/notes/pen-testing-notes/)**
*The core of my practical learning.*
- **Infrastructure:** Deployed a complete Active Directory environment with Domain Controllers, Workstations, and Linux servers.
- **Red Operations:** Executed simulated **Phishing campaigns** and deployed basic **C2 agents** to test network defenses and persistence.
- **Blue Operations:** Monitored traffic and system logs to detect the artifacts generated by my own attacks, bridging the gap between Red and Blue teaming.

### **2. [Build Your Own Shell (C Language)](https://github.com/0x-s0M3n4th/Shell)**
*Part of CodeCrafters Challenge*
- Developing a POSIX-compliant shell in **C**.
- Implementing core system interactions, process creation, and signal handling to understand Linux internals at a deeper level.

### **3. Remote Control (RC) Car**
- Designed and assembled a custom RC car, handling component selection, circuit assembly, and motor control logic.
- Key components used - Arduino Uno , L298N Motor Driver, DC Gear Motors, HC-05 Bluetooth Module, Li-ion Batteries.

### **4. [Cybersecurity Blog & Knowledge Base](https://0x-s0m3n4th.github.io)**
- Built and maintained this site using **Hugo & PaperMod**.
- Documenting System Administration guides, penetration testing methodologies, Blue Team Operations and lab configurations.

---

## Certifications & Courses
- [**eJPT** (eLearnSecurity Junior Penetration Tester)](https://certs.ine.com/0d862f1a-8c55-4d71-868a-eb5f8fe8608c#acc.P4jQhweH) - *INE Security*
- [**RH-124**](https://www.credly.com/badges/7ff7cb65-6058-48ab-b9e6-f47e0b7700a4) - *Red Hat Inc*
- [**RH-134**](https://www.credly.com/badges/82e726af-4cd3-484e-9114-89ec3c5b8bcc) - *Red Hat Inc*
- **PNPT coursework** (Practical Network Penetration Tester) - *TCM Security*
- [**Practical Help Desk**](https://academy.tcm-sec.com/courses/2537874/certificate) - *TCM Security*


---

## Experience
**Cybersecurity Student / Researcher**
*Self-Employed / Academic | 2025 - Present*
- Managing hybrid Linux/Windows environments to simulate enterprise networks.
- Developing scripts in Python and Bash to automate administrative tasks and attack simulations.
- Performed and documented multi network sytem's exploit chains as well as how to administer them properly.

---

## CTFs
- Active participant in CTF events (HackTheBox, PicoCTF).
- Focused on realistic network scenarios, privilege escalation, and lateral movement challenges.

---

## Contact

- **Email:** [sebaitsom6297@gmail.com](mailto:sebaitsom6297@gmail.com)
- **Socials:** [LinkedIn](https://www.linkedin.com/in/somenath-sebait) / [Twitter](https://x.com/cyb3r_Insi6ht) / [GitHub](https://github.com/0x-s0M3n4th) 

## Resume
[**Download My Resume (PDF)**](/my_cv.pdf)