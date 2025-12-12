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
        backdrop-filter: blur(10px);
        border: 1px solid rgba(102, 126, 234, 0.3);
        box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
    }

    .profile-card {
        border: 2px solid #667eea;
        border-radius: 10px;
        padding: 1.5em;
        background: linear-gradient(135deg, #2a2a40 0%, #1f1f35 100%);
        margin: 1em 0;
        transition: all 0.3s ease;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    }

    .profile-card:hover {
        transform: translateY(-4px);
        box-shadow: 0 8px 25px rgba(102, 126, 234, 0.3);
        border-color: #8b9dff;
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
        transition: all 0.3s;
    }

    .btn:disabled {
        opacity: 0.5;
        cursor: not-allowed;
    }

    .btn-match {
        background: #27ae60;
        color: white;
    }

    .btn-match:hover:not(:disabled) {
        background: #229954;
        transform: scale(1.05);
    }

    .btn-skip {
        background: #e74c3c;
        color: white;
    }

    .btn-skip:hover:not(:disabled) {
        background: #c0392b;
        transform: scale(1.05);
    }

    .btn-new {
        width: 100%;
        padding: 0.8em;
        background: #667eea;
        color: white;
        border: none;
        border-radius: 6px;
        cursor: pointer;
        font-size: 1em;
        margin-top: 1em;
        font-family: 'Courier New', monospace;
        font-weight: bold;
        transition: all 0.3s;
    }

    .btn-new:hover {
        background: #5568d3;
        transform: scale(1.02);
    }

    .stats {
        background: linear-gradient(135deg, #3a3a52 0%, #2d2d42 100%);
        padding: 1em;
        border-radius: 8px;
        margin-bottom: 1.5em;
        text-align: center;
        color: #e0e0e0;
        border: 2px solid #667eea;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    }

    .stats span {
        font-weight: bold;
        color: #8b9dff;
    }

    #history {
        margin-top: 1.5em;
        padding: 1em;
        background: #2a2a40;
        border-radius: 6px;
        max-height: 200px;
        overflow-y: auto;
        color: #e0e0e0;
        border: 1px solid #667eea;
    }

    #historyList {
        margin-top: 0.5em;
        line-height: 1.8;
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

### Real-World Examples of Sequencing

Sequencing appears everywhere in our daily lives:

**Making a Sandwich:**
1. Get bread
2. Spread condiments
3. Add fillings
4. Close sandwich

If you tried to spread condiments before getting bread, it wouldn't work. The same logic applies to programming.

**Starting a Car:**
1. Insert key
2. Turn ignition
3. Release parking brake
4. Put in gear
5. Press gas pedal

Each step depends on the previous one being completed. Programs need this same sequential flow.

**ATM Withdrawal:**
1. Insert card
2. Enter PIN
3. Select account
4. Choose amount
5. Take cash
6. Take receipt

The ATM can't give you cash before verifying your PIN. This is sequencing in action.

---

## Why Does Sequencing Matter?

Sequencing lets computers:

- Follow directions exactly  
- Process data step-by-step  
- Check requirements one at a time  
- Produce predictable results  

A program with bad sequencing misbehaves, just like if you tried to put on socks after your shoes.

### Sequencing in the Profile Matcher Game

In the game below, sequencing is critical:

1. **Profile Generation** - First, random data is selected from arrays
2. **Profile Display** - Then, the profile is shown to the user
3. **User Decision** - Next, the user clicks Match or Skip
4. **Data Processing** - The decision is recorded in history
5. **Stats Update** - Finally, statistics are updated and displayed

If these steps happened out of order (like updating stats before getting a decision), the program would break. Each step builds on the previous one, demonstrating how sequencing creates functional programs.

### Sequencing vs. Other Programming Concepts

**Sequencing** executes commands in order, one after another.

**Selection** (if/else statements) chooses which path to take based on conditions.

**Iteration** (loops) repeats a set of instructions multiple times.

All three concepts work together in most programs, but sequencing is the foundation that determines the overall flow of execution.

---

# 🧠 Sequencing Match Game

Below is a game where you see **randomly generated profiles** in sequence and decide whether to match with them or skip.

Each decision happens **in order** — demonstrating how programs process data sequentially!

---

<div id="sequence-box">
    <h3 style="margin-top:0;">💫 Profile Matcher</h3>
    <p style="font-size:0.9em;">Review each profile and decide: Match or Skip?</p>

    <!-- Stats Display (OUTPUT) -->
    <div class="stats">
        <strong>Matches:</strong> <span id="matchCount">0</span> | 
        <strong>Skipped:</strong> <span id="skipCount">0</span> | 
        <strong>Total Reviewed:</strong> <span id="totalCount">0</span>
    </div>

    <!-- Profile Display (OUTPUT) -->
    <div id="profileDisplay">
        <div class="profile-card">
            <div class="profile-header">Click "New Profile" to start!</div>
        </div>
    </div>

    <!-- User Input Buttons -->
    <div class="button-group">
        <button class="btn btn-match" onclick="handleMatchClick()" id="matchBtn" disabled>
            ✓ Match
        </button>
        <button class="btn btn-skip" onclick="handleSkipClick()" id="skipBtn" disabled>
            ✗ Skip
        </button>
    </div>

    <button onclick="handleNewProfileClick()" class="btn-new">
        🔄 New Profile
    </button>

    <!-- Decision History (OUTPUT) -->
    <div id="history">
        <strong>Decision History:</strong>
        <div id="historyList">
            <em>No decisions yet...</em>
        </div>
    </div>
</div>

<script>
    // LIST (collection type) to store all profile decisions
    let profileHistory = [];
    
    // Variables for game state
    let matchCount = 0;
    let skipCount = 0;
    let totalCount = 0;
    let currentProfile = null;

    // LISTS for random data generation
    const names = ["Alex", "Jordan", "Taylor", "Morgan", "Casey", "Riley", "Avery", "Quinn", "Sage", "River", "Dakota", "Skylar", "Rowan", "Cameron", "Parker"];
    const ages = [18, 19, 20, 21, 22, 23, 24, 25];
    const hobbies = ["Reading", "Gaming", "Hiking", "Cooking", "Art", "Music", "Sports", "Photography", "Dancing", "Coding", "Traveling", "Yoga"];
    const locations = ["Los Angeles", "New York", "Chicago", "Austin", "Seattle", "Miami", "Boston", "Denver"];
    const occupations = ["Student", "Engineer", "Designer", "Teacher", "Artist", "Developer", "Musician", "Writer", "Researcher", "Entrepreneur"];

    // PROCEDURE: getRandomItem
    // Parameters: array (list to select from)
    // Return type: single item from array
    // Purpose: Randomly select an item from an array
    function getRandomItem(array) {
        // SEQUENCING: Calculate random index first
        let randomIndex = Math.floor(Math.random() * array.length);
        
        // SEQUENCING: Then return the item at that index
        return array[randomIndex];
    }

    // PROCEDURE: generateProfile
    // Parameters: none
    // Return type: object (profile data)
    // Purpose: Create a random profile using sequencing, selection, and iteration
    function generateProfile() {
        // SEQUENCING: Steps must happen in order
        
        // Step 1: Generate basic info
        const name = getRandomItem(names);
        const age = getRandomItem(ages);
        const location = getRandomItem(locations);
        const occupation = getRandomItem(occupations);
        
        // Step 2: Generate unique hobbies using SELECTION and ITERATION
        const hobby1 = getRandomItem(hobbies);
        let hobby2 = getRandomItem(hobbies);
        
        // ITERATION: Keep selecting until we get a different hobby
        while (hobby2 === hobby1) {
            hobby2 = getRandomItem(hobbies);
        }
        
        // Step 3: Create profile object
        const profile = {
            name: name,
            age: age,
            hobbies: [hobby1, hobby2],
            location: location,
            occupation: occupation,
            timestamp: new Date().toLocaleTimeString()
        };
        
        // Step 4: Return the profile
        return profile;
    }

    // PROCEDURE: displayProfile
    // Parameters: profile (object with user data)
    // Return type: none (void)
    // Purpose: Display profile information to the screen (OUTPUT)
    function displayProfile(profile) {
        // SEQUENCING: Get element first, then modify it
        const display = document.getElementById('profileDisplay');
        
        // SELECTION: Check if profile exists
        if (profile) {
            // Build HTML string using profile data
            display.innerHTML = `
                <div class="profile-card">
                    <div class="profile-header">${profile.name}, ${profile.age}</div>
                    <div class="profile-detail"><strong>📍 Location:</strong> ${profile.location}</div>
                    <div class="profile-detail"><strong>💼 Occupation:</strong> ${profile.occupation}</div>
                    <div class="profile-detail"><strong>🎯 Hobbies:</strong> ${profile.hobbies.join(", ")}</div>
                </div>
            `;
        }
    }

    // PROCEDURE: processDecision
    // Parameters: decision (string - "match" or "skip"), profile (object)
    // Return type: none (void)
    // Purpose: Process user decision with sequencing, selection, and iteration
    function processDecision(decision, profile) {
        // SEQUENCING: Steps must happen in specific order
        
        // Step 1: Update counters based on SELECTION
        if (decision === 'match') {
            matchCount++;
        } else if (decision === 'skip') {
            skipCount++;
        }
        totalCount++;
        
        // Step 2: Add to history LIST (collection type)
        const historyEntry = {
            decision: decision,
            profile: profile,
            timestamp: new Date().toLocaleTimeString()
        };
        profileHistory.unshift(historyEntry);
        
        // Step 3: Update all displays (OUTPUT)
        updateStatsDisplay();
        updateHistoryDisplay();
        
        // Step 4: Disable buttons until new profile
        setButtonsEnabled(false);
        
        // Step 5: Clear current profile
        currentProfile = null;
        document.getElementById('profileDisplay').innerHTML = `
            <div class="profile-card">
                <div class="profile-header">Decision recorded! Click "New Profile" to continue.</div>
            </div>
        `;
    }

    // PROCEDURE: updateStatsDisplay
    // Parameters: none
    // Return type: none (void)
    // Purpose: Update the statistics display (OUTPUT)
    function updateStatsDisplay() {
        // SEQUENCING: Update each stat in order
        document.getElementById('matchCount').textContent = matchCount;
        document.getElementById('skipCount').textContent = skipCount;
        document.getElementById('totalCount').textContent = totalCount;
    }

    // PROCEDURE: updateHistoryDisplay
    // Parameters: none
    // Return type: none (void)
    // Purpose: Display decision history using ITERATION over LIST
    function updateHistoryDisplay() {
        const historyList = document.getElementById('historyList');
        
        // SELECTION: Check if history is empty
        if (profileHistory.length === 0) {
            historyList.innerHTML = '<em>No decisions yet...</em>';
        } else {
            // ITERATION: Loop through history items
            let htmlContent = '';
            let itemsToShow = Math.min(10, profileHistory.length);
            
            for (let i = 0; i < itemsToShow; i++) {
                const entry = profileHistory[i];
                const colorClass = entry.decision === 'match' ? '#27ae60' : '#e74c3c';
                const symbol = entry.decision === 'match' ? '✓' : '✗';
                const action = entry.decision === 'match' ? 'Matched' : 'Skipped';
                
                htmlContent += `<span style="color:${colorClass};">${symbol} ${action}</span> with ${entry.profile.name}, ${entry.profile.age}<br>`;
            }
            
            historyList.innerHTML = htmlContent;
        }
    }

    // PROCEDURE: setButtonsEnabled
    // Parameters: enabled (boolean)
    // Return type: none (void)
    // Purpose: Enable or disable match/skip buttons
    function setButtonsEnabled(enabled) {
        document.getElementById('matchBtn').disabled = !enabled;
        document.getElementById('skipBtn').disabled = !enabled;
    }

    // EVENT HANDLERS (USER INPUT)
    
    // Handle "New Profile" button click
    function handleNewProfileClick() {
        // SEQUENCING: Generate profile, then display it, then enable buttons
        currentProfile = generateProfile();
        displayProfile(currentProfile);
        setButtonsEnabled(true);
    }

    // Handle "Match" button click
    function handleMatchClick() {
        // SELECTION: Only process if there's a current profile
        if (currentProfile) {
            processDecision('match', currentProfile);
        }
    }

    // Handle "Skip" button click
    function handleSkipClick() {
        // SELECTION: Only process if there's a current profile
        if (currentProfile) {
            processDecision('skip', currentProfile);
        }
    }
</script>

---