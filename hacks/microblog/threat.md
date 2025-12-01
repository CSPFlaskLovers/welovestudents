---
layout: post
title: Threat Modeling
description: A brief introduction to threat modeling PII.
permalink: /digital-famine/microblog/threat/
breadcrumb: true
microblog: true
author: Lucas M
---

<style>
    body {
        min-height: 100vh;
        background: url('{{ site.baseurl }}/images/code.png') no-repeat center center fixed;
        background-size: cover;
        background-color: #1a1a2e; /* fallback color if image doesn't load */
    }
    
    #interactive-threat-model {
        background: rgba(255, 255, 255, 0.95);
        padding: 2em;
        border-radius: 12px;
        max-width: 600px;
        margin: 2em auto;
    }
</style>

## Introduction

Absolute security doesn't exist. What does exist is a clear idea of *who* you're defending against and *what* matters most. That's the purpose of a **threat model**—identifying realistic risks instead of preparing for every possible attacker.

## Creating a Threat Model

Start with what you value and what could go wrong. Ask:

- What do I need to protect?
- Who am I protecting it from?
- How likely is a threat?
- What happens if I fail?
- How much effort am I willing to put in?

### What do I want to protect?

Think in categories:

- *Medical records*  
- *Financial credentials*  
- *Private communications*  
- *Identity links (real name ↔ alias)*  
- *Location data*  

Not everything warrants heavy protection. Focus on the data that would meaningfully harm you if exposed.

### Who is the adversary?

Different threats → different defenses:

- *Corporations*: profiling, tracking, data brokerage  
- *Governments*: surveillance, censorship, investigations  
- *Criminals*: theft, scams, account compromise  
- *Acquaintances*: device snooping or boundary violations  
- *Advertisers/data brokers*: constant behavioral tracking  

Match your defenses to the adversary, not the other way around.

### How likely is the threat?

- *Very likely*: spam, phishing, brokerage, device loss  
- *Moderately likely*: password leaks, account takeovers  
- *Less likely*: targeted state action unless you're high-risk  

Everyday threats deserve everyday defenses; rare threats deserve proportionate effort.

### Consequences of failure

- Losing a throwaway account → mild annoyance  
- Leaking private photos → social/personal harm  
- Revealing sensitive sources → legal or physical danger  
- Exposing financial keys → irreversible loss  

Severity helps you prioritize.

### Effort vs. payoff

Security trades convenience:

- Strong passwords + manager → easy, huge benefit  
- Tor or compartmentalization → higher friction  
- Leaving big-tech ecosystems → major lifestyle cost  

Let your goals decide your tolerance.

### Further Reading

- https://ssd.eff.org/module/your-security-plan

### Password Strength Checker

<div id="interactive-threat-model">
    <label><strong>Test Your Password Strength</strong></label><br>
    <p style="font-size:0.9em; margin:0.5em 0;">Enter a password to see how secure it is against common threats.</p>
    
    <input type="password" id="passwordInput" placeholder="Enter a password..." style="width:100%; padding:0.8em; border-radius:6px; border:1px solid #ccc; margin:1em 0;">
    
    <button onclick="checkPassword()" style="padding:0.8em 2em; background:#667eea; color:white; border:none; border-radius:6px; cursor:pointer; font-size:1em;">Check Strength</button>
    
    <div id="result" style="border:1px solid #888; padding:1em; background:#f9f9f9; margin-top:1em;">
        <em>Enter a password and click "Check Strength" to see results.</em>
    </div>
</div>

<script>
    function checkPassword() {
        const password = document.getElementById('passwordInput').value;
        const resultDiv = document.getElementById('result');
        
        if (!password) {
            resultDiv.innerHTML = "<em>Please enter a password to check.</em>";
            return;
        }
        
        let strength = "Strong";
        let color = "#2ecc71";
        let issues = [];
        let tips = [];
        
        // Check length
        if (password.length < 8) {
            strength = "Weak";
            color = "#e74c3c";
            issues.push("Less than 8 characters");
            tips.push("Use at least 8 characters (12+ recommended)");
        }
        
        // Check for numbers
        if (!/\d/.test(password)) {
            strength = "Weak";
            color = "#e74c3c";
            issues.push("No numbers");
            tips.push("Include at least one number");
        }
        
        // Check for uppercase
        if (!/[A-Z]/.test(password)) {
            if (strength !== "Weak") strength = "Moderate";
            if (color !== "#e74c3c") color = "#f39c12";
            issues.push("No uppercase letters");
            tips.push("Add uppercase letters for better security");
        }
        
        // Check for lowercase
        if (!/[a-z]/.test(password)) {
            if (strength !== "Weak") strength = "Moderate";
            if (color !== "#e74c3c") color = "#f39c12";
            issues.push("No lowercase letters");
            tips.push("Include lowercase letters");
        }
        
        // Check for special characters
        if (!/[!@#$%^&*()_+\-=\[\]{};':"\\|,.<>\/?]/.test(password)) {
            if (strength !== "Weak") strength = "Moderate";
            if (color !== "#e74c3c") color = "#f39c12";
            issues.push("No special characters");
            tips.push("Add special characters (!@#$%^&*)");
        }
        
        let html = `<div style="color:${color}; font-size:1.4em; font-weight:bold; margin-bottom:0.5em;">Password Strength: ${strength}</div>`;
        
        if (issues.length > 0) {
            html += `<div style="margin:0.8em 0;"><strong>Issues found:</strong><ul style="margin:0.3em 0; padding-left:1.5em;">`;
            issues.forEach(issue => {
                html += `<li>${issue}</li>`;
            });
            html += `</ul></div>`;
            
            html += `<div style="margin:0.8em 0;"><strong>Recommendations:</strong><ul style="margin:0.3em 0; padding-left:1.5em;">`;
            tips.forEach(tip => {
                html += `<li>${tip}</li>`;
            });
            html += `</ul></div>`;
        } else {
            html += `<div style="color:#27ae60; margin-top:0.5em;">✓ Your password meets security best practices!</div>`;
        }
        
        resultDiv.innerHTML = html;
    }
    
    // Allow Enter key to check password
    document.getElementById('passwordInput').addEventListener('keypress', function(e) {
        if (e.key === 'Enter') {
            checkPassword();
        }
    });
</script>