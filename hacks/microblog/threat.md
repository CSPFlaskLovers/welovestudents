---
layout: post
title: Sequencing
description: Understanding sequencing + an interactive AP CSP-style game.
permalink: /digital-famine/microblog/matchmaking_sequence/
breadcrumb: true
microblog: true
author: Ethan W
---

<style>
    body {
        min-height: 100vh;
        background: url('{{ site.baseurl }}/images/code.png') no-repeat center center fixed;
        background-size: cover;
        background-color: #1a1a2e;
    }

    #sequence-box {
        background: rgba(30, 30, 46, 0.95);
        padding: 2em;
        border-radius: 12px;
        max-width: 700px;
        margin: 2em auto;
        font-family: 'Courier New', monospace;
        color: #e0e0e0;
    }

    .profile-card {
        border: 2px solid #667eea;
        border-radius: 10px;
        padding: 1.5em;
        background: #2a2a40;
        margin: 1em 0;
    }

    .profile-header {
        font-size: 1.3em;
        font-weight: bold;
        margin-bottom: 0.5em;
        color: #8b9dff;
    }

    .profile-detail {
        margin: 0.5em 0;
        padding-left: 1em;
        color: #c0c0c0;
    }

    .button-group {
        display: flex;
        gap: 1em;
        margin-top: 1.5em;
    }

    .btn {
        flex: 1;
        padding: 0.8em;
        border: none;
        border-radius: 6px;
        cursor: pointer;
        font-size: 1em;
        font-weight: bold;
        font-family: 'Courier New', monospace;
    }

    .btn-match {
        background: #27ae60;
        color: white;
    }

    .btn-match:hover {
        background: #229954;
    }

    .btn-skip {
        background: #e74c3c;
        color: white;
    }

    .btn-skip:hover {
        background: #c0392b;
    }

    .stats {
        background: #3a3a52;
        padding: 1em;
        border-radius: 6px;
        margin-bottom: 1em;
        text-align: center;
        color: #e0e0e0;
    }
</style>

## What Is Sequencing?

Sequencing is one of the core programming concepts in **AP Computer Science Principles**.  
It means that a program runs **each instruction in order**, one after another, from top to bottom.

This matters because:

- The *order* of commands changes the result  
- You can't skip steps in a process  
- Programs follow the same structure humans follow in a checklist  
- Sequencing is the base for selection and iteration  

Think of a recipe: you can't bake before mixing the ingredients.  
Computers work the same way.

---

## Why Does Sequencing Matter?

Sequencing lets computers:

- Follow directions exactly  
- Process data step-by-step  
- Check requirements one at a time  
- Produce predictable results  

A program with bad sequencing misbehaves, just like if you tried to put on socks after your shoes.

---

# 🧠 Sequencing Match Game

Below is a game where you see **randomly generated profiles** in sequence and decide whether to match with them or skip.

Each decision happens **in order** — demonstrating how programs process data sequentially!

---

<div id="sequence-box">
    <h3 style="margin-top:0;">💫 Profile Matcher</h3>
    <p style="font-size:0.9em;">Review each profile and decide: Match or Skip?</p>

    <!-- Stats -->
    <div class="stats">
        <strong>Matches:</strong> <span id="matchCount">0</span> | 
        <strong>Skipped:</strong> <span id="skipCount">0</span> | 
        <strong>Total Reviewed:</strong> <span id="totalCount">0</span>
    </div>

    <!-- Profile Display -->
    <div id="profileDisplay">
        <div class="profile-card">
            <div class="profile-header">Click "New Profile" to start!</div>
        </div>
    </div>

    <!-- Buttons -->
    <div class="button-group">
        <button class="btn btn-match" onclick="makeDecision('match')" id="matchBtn" disabled>
            ✓ Match
        </button>
        <button class="btn btn-skip" onclick="makeDecision('skip')" id="skipBtn" disabled>
            ✗ Skip
        </button>
    </div>

    <button onclick="generateProfile()" 
            style="width:100%; padding:0.8em; background:#667eea; color:white; border:none; border-radius:6px; cursor:pointer; font-size:1em; margin-top:1em; font-family:'Courier New', monospace;">
        🔄 New Profile
    </button>

    <!-- History -->
    <div id="history" style="margin-top:1.5em; padding:1em; background:#2a2a40; border-radius:6px; max-height:200px; overflow-y:auto; color:#e0e0e0; border:1px solid #667eea;">
        <strong>Decision History:</strong>
        <div id="historyList" style="margin-top:0.5em;">
            <em>No decisions yet...</em>
        </div>
    </div>
</div>

<script>
    let matchCount = 0;
    let skipCount = 0;
    let totalCount = 0;
    let currentProfile = null;
    let historyItems = [];

    const names = ["Alex", "Jordan", "Taylor", "Morgan", "Casey", "Riley", "Avery", "Quinn", "Sage", "River", "Dakota", "Skylar", "Rowan", "Cameron", "Parker"];
    const ages = [18, 19, 20, 21, 22, 23, 24, 25];
    const hobbies = ["Reading", "Gaming", "Hiking", "Cooking", "Art", "Music", "Sports", "Photography", "Dancing", "Coding", "Traveling", "Yoga"];
    const locations = ["Los Angeles", "New York", "Chicago", "Austin", "Seattle", "Miami", "Boston", "Denver"];
    const occupations = ["Student", "Engineer", "Designer", "Teacher", "Artist", "Developer", "Musician", "Writer", "Researcher", "Entrepreneur"];

    function getRandomItem(array) {
        return array[Math.floor(Math.random() * array.length)];
    }

    function generateProfile() {
        const name = getRandomItem(names);
        const age = getRandomItem(ages);
        const hobby1 = getRandomItem(hobbies);
        let hobby2 = getRandomItem(hobbies);
        while (hobby2 === hobby1) {
            hobby2 = getRandomItem(hobbies);
        }
        const location = getRandomItem(locations);
        const occupation = getRandomItem(occupations);

        currentProfile = {
            name: name,
            age: age,
            hobbies: [hobby1, hobby2],
            location: location,
            occupation: occupation
        };

        displayProfile();
        
        // Enable buttons
        document.getElementById('matchBtn').disabled = false;
        document.getElementById('skipBtn').disabled = false;
    }

    function displayProfile() {
        const display = document.getElementById('profileDisplay');
        const p = currentProfile;

        display.innerHTML = `
            <div class="profile-card">
                <div class="profile-header">${p.name}, ${p.age}</div>
                <div class="profile-detail"><strong>📍 Location:</strong> ${p.location}</div>
                <div class="profile-detail"><strong>💼 Occupation:</strong> ${p.occupation}</div>
                <div class="profile-detail"><strong>🎯 Hobbies:</strong> ${p.hobbies.join(", ")}</div>
            </div>
        `;
    }

    function makeDecision(decision) {
        if (!currentProfile) return;

        if (decision === 'match') {
            matchCount++;
            historyItems.unshift(`<span style="color:#27ae60;">✓ Matched</span> with ${currentProfile.name}, ${currentProfile.age}`);
        } else {
            skipCount++;
            historyItems.unshift(`<span style="color:#e74c3c;">✗ Skipped</span> ${currentProfile.name}, ${currentProfile.age}`);
        }

        totalCount++;
        updateStats();
        updateHistory();

        // Disable buttons until new profile
        document.getElementById('matchBtn').disabled = true;
        document.getElementById('skipBtn').disabled = true;

        // Clear current profile
        currentProfile = null;
        document.getElementById('profileDisplay').innerHTML = `
            <div class="profile-card">
                <div class="profile-header">Decision recorded! Click "New Profile" to continue.</div>
            </div>
        `;
    }

    function updateStats() {
        document.getElementById('matchCount').textContent = matchCount;
        document.getElementById('skipCount').textContent = skipCount;
        document.getElementById('totalCount').textContent = totalCount;
    }

    function updateHistory() {
        const historyList = document.getElementById('historyList');
        if (historyItems.length === 0) {
            historyList.innerHTML = '<em>No decisions yet...</em>';
        } else {
            historyList.innerHTML = historyItems.slice(0, 10).join('<br>');
        }
    }
</script>

---