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

---

### Password Sorting Game

<div id="password-game" style="background: rgba(255, 255, 255, 0.95); padding: 2em; border-radius: 12px; max-width: 800px; margin: 2em auto;">
    <h3 style="margin-top:0;">Drag & Drop Password Strength</h3>
    <p style="font-size:0.9em; margin:0.5em 0;">Drag each password to the correct strength category!</p>
    
    <div style="text-align:center; margin:1em 0;">
        <button onclick="autofillPasswords()" style="padding:0.6em 1.5em; background:#9b59b6; color:white; border:none; border-radius:6px; cursor:pointer; font-size:0.95em;">💡 Auto-Fill (if stuck)</button>
        <button onclick="resetGame()" style="padding:0.6em 1.5em; background:#3498db; color:white; border:none; border-radius:6px; cursor:pointer; font-size:0.95em; margin-left:0.5em;">🔄 Reset Game</button>
    </div>
    
    <div id="passwords-container" style="background:#f0f0f0; padding:1em; border-radius:8px; min-height:100px; margin:1em 0;">
        <strong>Passwords to Sort:</strong>
        <div id="passwords" style="display:flex; flex-wrap:wrap; gap:0.5em; margin-top:0.5em;">
            <!-- Passwords will be inserted here -->
        </div>
    </div>
    
    <div style="display:grid; grid-template-columns: repeat(3, 1fr); gap:1em; margin-top:1.5em;">
        <div class="drop-zone" data-strength="weak" style="background:#ffebee; border:2px dashed #e74c3c; border-radius:8px; padding:1em; min-height:150px;">
            <strong style="color:#c0392b;">🔴 Weak</strong>
            <div class="dropped-passwords" style="margin-top:0.5em; display:flex; flex-direction:column; gap:0.3em;"></div>
        </div>
        
        <div class="drop-zone" data-strength="moderate" style="background:#fff3e0; border:2px dashed #f39c12; border-radius:8px; padding:1em; min-height:150px;">
            <strong style="color:#d68910;">🟡 Moderate</strong>
            <div class="dropped-passwords" style="margin-top:0.5em; display:flex; flex-direction:column; gap:0.3em;"></div>
        </div>
        
        <div class="drop-zone" data-strength="strong" style="background:#e8f5e9; border:2px dashed #2ecc71; border-radius:8px; padding:1em; min-height:150px;">
            <strong style="color:#27ae60;">🟢 Strong</strong>
            <div class="dropped-passwords" style="margin-top:0.5em; display:flex; flex-direction:column; gap:0.3em;"></div>
        </div>
    </div>
    
    <div id="game-feedback" style="margin-top:1em; font-weight:bold; text-align:center; min-height:30px;"></div>
</div>

<script>
    const passwordData = [
        { text: "pass123", strength: "weak" },
        { text: "hello", strength: "weak" },
        { text: "12345678", strength: "weak" },
        { text: "Password1", strength: "moderate" },
        { text: "Summer2024", strength: "moderate" },
        { text: "MyP@ssw0rd!", strength: "strong" },
        { text: "Tr0ub4dor&3", strength: "strong" },
        { text: "qwerty", strength: "weak" },
        { text: "Welcome123", strength: "moderate" },
        { text: "X9$mK2#pL5@q", strength: "strong" }
    ];
    
    let currentPasswords = [];
    
    function initGame() {
        currentPasswords = [...passwordData].sort(() => Math.random() - 0.5).slice(0, 6);
        renderPasswords();
        setupDragAndDrop();
    }
    
    function renderPasswords() {
        const container = document.getElementById('passwords');
        container.innerHTML = '';
        
        currentPasswords.forEach((pwd, index) => {
            const pwdEl = document.createElement('div');
            pwdEl.className = 'password-item';
            pwdEl.draggable = true;
            pwdEl.dataset.password = pwd.text;
            pwdEl.dataset.strength = pwd.strength;
            pwdEl.textContent = pwd.text;
            pwdEl.style.cssText = 'background:white; padding:0.6em 1em; border-radius:6px; cursor:move; border:2px solid #ddd; font-family:monospace; user-select:none;';
            container.appendChild(pwdEl);
        });
    }
    
    function setupDragAndDrop() {
        const passwordItems = document.querySelectorAll('.password-item');
        const dropZones = document.querySelectorAll('.drop-zone');
        
        passwordItems.forEach(item => {
            item.addEventListener('dragstart', (e) => {
                e.dataTransfer.setData('text/plain', e.target.dataset.password);
                e.dataTransfer.setData('strength', e.target.dataset.strength);
                e.target.style.opacity = '0.5';
            });
            
            item.addEventListener('dragend', (e) => {
                e.target.style.opacity = '1';
            });
        });
        
        dropZones.forEach(zone => {
            zone.addEventListener('dragover', (e) => {
                e.preventDefault();
                zone.style.background = zone.dataset.strength === 'weak' ? '#ffcdd2' : 
                                       zone.dataset.strength === 'moderate' ? '#ffe0b2' : '#c8e6c9';
            });
            
            zone.addEventListener('dragleave', (e) => {
                zone.style.background = zone.dataset.strength === 'weak' ? '#ffebee' : 
                                       zone.dataset.strength === 'moderate' ? '#fff3e0' : '#e8f5e9';
            });
            
            zone.addEventListener('drop', (e) => {
                e.preventDefault();
                const password = e.dataTransfer.getData('text/plain');
                const actualStrength = e.dataTransfer.getData('strength');
                const droppedZone = zone.dataset.strength;
                
                zone.style.background = zone.dataset.strength === 'weak' ? '#ffebee' : 
                                       zone.dataset.strength === 'moderate' ? '#fff3e0' : '#e8f5e9';
                
                // Remove from original container
                const originalItem = Array.from(document.querySelectorAll('.password-item'))
                    .find(item => item.dataset.password === password);
                if (originalItem) originalItem.remove();
                
                // Add to drop zone
                const droppedContainer = zone.querySelector('.dropped-passwords');
                const newItem = document.createElement('div');
                newItem.textContent = password;
                newItem.style.cssText = 'background:white; padding:0.5em; border-radius:4px; font-family:monospace; font-size:0.9em;';
                
                if (actualStrength === droppedZone) {
                    newItem.style.border = '2px solid #27ae60';
                } else {
                    newItem.style.border = '2px solid #e74c3c';
                }
                
                droppedContainer.appendChild(newItem);
                
                checkCompletion();
            });
        });
    }
    
    function checkCompletion() {
        const remainingPasswords = document.querySelectorAll('#passwords .password-item');
        if (remainingPasswords.length === 0) {
            let correct = 0;
            let total = 0;
            
            document.querySelectorAll('.drop-zone').forEach(zone => {
                const zoneStrength = zone.dataset.strength;
                const items = zone.querySelectorAll('.dropped-passwords > div');
                
                items.forEach(item => {
                    total++;
                    const password = item.textContent;
                    const actualStrength = currentPasswords.find(p => p.text === password)?.strength;
                    if (actualStrength === zoneStrength) correct++;
                });
            });
            
            const feedback = document.getElementById('game-feedback');
            if (correct === total) {
                feedback.innerHTML = '🎉 Perfect! All passwords sorted correctly!';
                feedback.style.color = '#27ae60';
            } else {
                feedback.innerHTML = `You got ${correct} out of ${total} correct. Try again!`;
                feedback.style.color = '#e67e22';
            }
        }
    }
    
    function autofillPasswords() {
        document.querySelectorAll('.password-item').forEach(item => {
            const password = item.dataset.password;
            const strength = item.dataset.strength;
            
            const targetZone = document.querySelector(`.drop-zone[data-strength="${strength}"]`);
            const droppedContainer = targetZone.querySelector('.dropped-passwords');
            
            const newItem = document.createElement('div');
            newItem.textContent = password;
            newItem.style.cssText = 'background:white; padding:0.5em; border-radius:4px; font-family:monospace; font-size:0.9em; border:2px solid #27ae60;';
            droppedContainer.appendChild(newItem);
            
            item.remove();
        });
        
        const feedback = document.getElementById('game-feedback');
        feedback.innerHTML = '✅ Auto-filled with correct answers!';
        feedback.style.color = '#27ae60';
    }
    
    function resetGame() {
        document.querySelectorAll('.dropped-passwords').forEach(container => {
            container.innerHTML = '';
        });
        document.getElementById('game-feedback').innerHTML = '';
        initGame();
    }
    
    initGame();
</script>