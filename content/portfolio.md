---
title: "Portfolio"
layout: "page"
url: "/portfolio/"
summary: "System Administration, Blue Teaming, and Red Team Operations."
---

<div class="vertical-nav">
  <a href="#about-me" class="nav-dot" title="About Me"></a>
  <a href="#skills--technologies" class="nav-dot" title="Skills"></a>
  <a href="#projects" class="nav-dot" title="Projects"></a>
  <a href="#certifications--courses" class="nav-dot" title="Certifications"></a>
  <a href="#experience" class="nav-dot" title="Experience"></a>
  <a href="#ctfs" class="nav-dot" title="CTFs"></a>
  <a href="#contact" class="nav-dot" title="Contact"></a>
</div>

<style>
/* 1. Container - Fixed to Right Side */
.vertical-nav {
  position: fixed;
  right: 20px;       /* Distance from right edge */
  top: 50%;          /* Vertically centered */
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
  gap: 15px;         /* Space between dots */
  z-index: 1000;
  /* Optional: Add a subtle line connecting them if you want a "string" look */
  /* border-right: 1px solid var(--border); */
}

/* 2. The Dots (Inactive State) */
.nav-dot {
  width: 10px;
  height: 10px;
  background-color: var(--secondary); /* Grey/Dimmed color */
  border-radius: 50%;
  display: block;
  transition: all 0.3s ease;
  position: relative;
  opacity: 0.5;
}

/* 3. Hover Effect (Show Tooltip) */
.nav-dot:hover {
  transform: scale(1.5);
  opacity: 1;
  background-color: var(--primary);
}

/* 4. Active State (Current Section) */
.nav-dot.active {
  background-color: var(--primary); /* Bright accent color */
  transform: scale(1.3);
  opacity: 1;
  box-shadow: 0 0 8px var(--primary); /* Glowing effect */
}

/* 5. Tooltips (Labels on Hover) - Floating to the Left of the dot */
.nav-dot::before {
  content: attr(title);
  position: absolute;
  right: 20px; /* Text sits to the left of the dot */
  top: 50%;
  transform: translateY(-50%);
  background: var(--entry);
  color: var(--primary);
  padding: 4px 8px;
  border-radius: 4px;
  font-size: 0.75rem;
  white-space: nowrap;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.2s ease;
  font-weight: bold;
  border: 1px solid var(--border);
}

/* Show tooltip on hover OR when active */
.nav-dot:hover::before {
  opacity: 1;
}
</style>

<script>
document.addEventListener("DOMContentLoaded", () => {
  const dots = document.querySelectorAll('.nav-dot');

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        // Remove active class from all dots
        dots.forEach(dot => dot.classList.remove('active'));
        
        // Find the dot that matches this section ID
        // Note: Hugo replaces & with -- in IDs usually
        const id = entry.target.getAttribute('id');
        const activeDot = document.querySelector(`.nav-dot[href="#${id}"]`);
        
        if (activeDot) {
          activeDot.classList.add('active');
        }
      }
    });
  }, {
    // "Center" of the screen triggers the change
    rootMargin: "-45% 0px -45% 0px" 
  });

  // Attach observer to the headers
  dots.forEach(dot => {
    const id = dot.getAttribute('href').substring(1);
    const section = document.getElementById(id);
    if (section) observer.observe(section);
  });
});
</script>

<div style="display: flex; justify-content: center; margin-bottom: 20px;">
    <img src="/images/fun.jpeg" alt="Profile Image" style="border-radius: 50%; width: 200px; height: 200px; object-fit: cover; border: 2px solid var(--primary);">
</div>

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