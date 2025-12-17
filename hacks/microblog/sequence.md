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

    /* NEW STYLES FOR REAL MATCHMAKING GAME */
    #matchmaking-app {
        background: rgba(30, 30, 46, 0.95);
        padding: 2em;
        border-radius: 12px;
        max-width: 700px;
        margin: 2em auto;
        backdrop-filter: blur(10px);
        border: 1px solid rgba(102, 126, 234, 0.3);
        box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
    }

    .real-profile-card {
        background: linear-gradient(135deg, #2a2a40 0%, #1f1f35 100%);
        border: 2px solid #667eea;
        border-radius: 10px;
        padding: 1.5em;
        margin: 1em 0;
        transition: all 0.3s ease;
    }

    .real-profile-card:hover {
        transform: translateY(-4px);
        box-shadow: 0 8px 25px rgba(102, 126, 234, 0.3);
    }

    .compatibility-bar {
        width: 100%;
        height: 8px;
        background: #2a2a40;
        border-radius: 4px;
        overflow: hidden;
        margin: 0.5em 0;
    }

    .compatibility-fill {
        height: 100%;
        background: linear-gradient(90deg, #27ae60, #229954);
        transition: width 0.5s ease;
        border-radius: 4px;
    }

    .match-stats {
        display: flex;
        justify-content: space-around;
        background: linear-gradient(135deg, #3a3a52 0%, #2d2d42 100%);
        padding: 1em;
        border-radius: 8px;
        margin-bottom: 1.5em;
        border: 2px solid #667eea;
    }

    .stat-item {
        text-align: center;
        color: #e0e0e0;
    }

    .stat-value {
        font-size: 1.8em;
        font-weight: bold;
        color: #8b9dff;
    }

    .stat-label {
        font-size: 0.8em;
        color: #c0c0c0;
    }

    .loading-spinner {
        border: 4px solid rgba(102, 126, 234, 0.3);
        border-top: 4px solid #667eea;
        border-radius: 50%;
        width: 40px;
        height: 40px;
        animation: spin 1s linear infinite;
        margin: 2em auto;
    }

    @keyframes spin {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
    }

    .error-message {
        background: rgba(231, 76, 60, 0.2);
        border: 2px solid #e74c3c;
        color: #ff6b6b;
        padding: 1em;
        border-radius: 8px;
        margin: 1em 0;
        text-align: center;
    }

    .success-message {
        background: rgba(39, 174, 96, 0.2);
        border: 2px solid #27ae60;
        color: #51cf66;
        padding: 1em;
        border-radius: 8px;
        margin: 1em 0;
        text-align: center;
    }

    .tab-buttons {
        display: flex;
        gap: 1em;
        margin-bottom: 2em;
    }

    .tab-btn {
        flex: 1;
        padding: 1em;
        background: #2a2a40;
        color: #8b9dff;
        border: 2px solid #667eea;
        border-radius: 8px;
        cursor: pointer;
        font-family: 'Courier New', monospace;
        font-weight: bold;
        transition: all 0.3s;
    }

    .tab-btn:hover {
        background: #3a3a52;
        transform: translateY(-2px);
    }

    .tab-btn.active {
        background: #667eea;
        color: white;
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

# 🎮 Two Sequencing Games

<div class="tab-buttons">
    <button class="tab-btn active" onclick="switchTab('demo')">Demo Game (Random Profiles)</button>
    <button class="tab-btn" onclick="switchTab('real')">Real Matchmaking (Backend)</button>
</div>

---

## 🧠 Demo: Sequencing Match Game

<div id="demo-game" style="display: block;">
    <p style="text-align: center; color: #c0c0c0; margin-bottom: 1em;">
        This demo shows sequencing with randomly generated profiles
    </p>

    <div id="sequence-box">
        <h3 style="margin-top:0;">💫 Profile Matcher</h3>
        <p style="font-size:0.9em;">Review each profile and decide: Match or Skip?</p>

        <div class="stats">
            <strong>Matches:</strong> <span id="matchCount">0</span> | 
            <strong>Skipped:</strong> <span id="skipCount">0</span> | 
            <strong>Total Reviewed:</strong> <span id="totalCount">0</span>
        </div>

        <div id="profileDisplay">
            <div class="profile-card">
                <div class="profile-header">Click "New Profile" to start!</div>
            </div>
        </div>

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

        <div id="history">
            <strong>Decision History:</strong>
            <div id="historyList">
                <em>No decisions yet...</em>
            </div>
        </div>
    </div>
</div>

---

## 💕 Real Matchmaking with Backend

<div id="real-game" style="display: none;">
    <p style="text-align: center; color: #c0c0c0; margin-bottom: 1em;">
        This connects to your backend and matches with real user profiles!
    </p>

    <div id="matchmaking-app">
        <h3 style="margin-top:0; color: #8b9dff; text-align: center; font-size: 1.8em;">💕 Real Profile Matcher</h3>
        <p style="font-size:0.9em; text-align: center; color: #c0c0c0;">Connect with real users based on shared interests!</p>

        <div id="realGameContent">
            <div style="text-align: center; padding: 2em;">
                <p style="color: #c0c0c0;">Loading...</p>
                <div class="loading-spinner"></div>
            </div>
        </div>
    </div>
</div>

<script>
    // ==========================================
    // TAB SWITCHING
    // ==========================================
    function switchTab(tab) {
        const demoGame = document.getElementById('demo-game');
        const realGame = document.getElementById('real-game');
        const tabs = document.querySelectorAll('.tab-btn');
        
        tabs.forEach(t => t.classList.remove('active'));
        
        if (tab === 'demo') {
            demoGame.style.display = 'block';
            realGame.style.display = 'none';
            tabs[0].classList.add('active');
        } else {
            demoGame.style.display = 'none';
            realGame.style.display = 'block';
            tabs[1].classList.add('active');
            initRealMatchmaking();
        }
    }

    // ==========================================
    // DEMO GAME CODE (Original)
    // ==========================================
    let profileHistory = [];
    let matchCount = 0;
    let skipCount = 0;
    let totalCount = 0;
    let currentProfile = null;

    const names = ["Alex", "Jordan", "Taylor", "Morgan", "Casey", "Riley", "Avery", "Quinn", "Sage", "River", "Dakota", "Skylar", "Rowan", "Cameron", "Parker"];
    const ages = [18, 19, 20, 21, 22, 23, 24, 25];
    const hobbies = ["Reading", "Gaming", "Hiking", "Cooking", "Art", "Music", "Sports", "Photography", "Dancing", "Coding", "Traveling", "Yoga"];
    const locations = ["Los Angeles", "New York", "Chicago", "Austin", "Seattle", "Miami", "Boston", "Denver"];
    const occupations = ["Student", "Engineer", "Designer", "Teacher", "Artist", "Developer", "Musician", "Writer", "Researcher", "Entrepreneur"];

    function getRandomItem(array) {
        let randomIndex = Math.floor(Math.random() * array.length);
        return array[randomIndex];
    }

    function generateProfile() {
        const name = getRandomItem(names);
        const age = getRandomItem(ages);
        const location = getRandomItem(locations);
        const occupation = getRandomItem(occupations);
        
        const hobby1 = getRandomItem(hobbies);
        let hobby2 = getRandomItem(hobbies);
        
        while (hobby2 === hobby1) {
            hobby2 = getRandomItem(hobbies);
        }
        
        const profile = {
            name: name,
            age: age,
            hobbies: [hobby1, hobby2],
            location: location,
            occupation: occupation,
            timestamp: new Date().toLocaleTimeString()
        };
        
        return profile;
    }

    function displayProfile(profile) {
        const display = document.getElementById('profileDisplay');
        
        if (profile) {
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

    function processDecision(decision, profile) {
        if (decision === 'match') {
            matchCount++;
        } else if (decision === 'skip') {
            skipCount++;
        }
        totalCount++;
        
        const historyEntry = {
            decision: decision,
            profile: profile,
            timestamp: new Date().toLocaleTimeString()
        };
        profileHistory.unshift(historyEntry);
        
        updateStatsDisplay();
        updateHistoryDisplay();
        setButtonsEnabled(false);
        
        currentProfile = null;
        document.getElementById('profileDisplay').innerHTML = `
            <div class="profile-card">
                <div class="profile-header">Decision recorded! Click "New Profile" to continue.</div>
            </div>
        `;
    }

    function updateStatsDisplay() {
        document.getElementById('matchCount').textContent = matchCount;
        document.getElementById('skipCount').textContent = skipCount;
        document.getElementById('totalCount').textContent = totalCount;
    }

    function updateHistoryDisplay() {
        const historyList = document.getElementById('historyList');
        
        if (profileHistory.length === 0) {
            historyList.innerHTML = '<em>No decisions yet...</em>';
        } else {
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

    function setButtonsEnabled(enabled) {
        document.getElementById('matchBtn').disabled = !enabled;
        document.getElementById('skipBtn').disabled = !enabled;
    }

    function handleNewProfileClick() {
        currentProfile = generateProfile();
        displayProfile(currentProfile);
        setButtonsEnabled(true);
    }

    function handleMatchClick() {
        if (currentProfile) {
            processDecision('match', currentProfile);
        }
    }

    function handleSkipClick() {
        if (currentProfile) {
            processDecision('skip', currentProfile);
        }
    }

    // ==========================================
    // REAL MATCHMAKING CODE (New)
    // ==========================================
    let realMatchmakingState = {
        profiles: [],
        currentIndex: 0,
        matches: [],
        skipped: [],
        currentUser: null,
        initialized: false
    };

    async function initRealMatchmaking() {
        if (realMatchmakingState.initialized) return;
        
        const content = document.getElementById('realGameContent');
        content.innerHTML = `
            <div style="text-align: center; padding: 2em;">
                <p style="color: #c0c0c0;">Connecting to backend...</p>
                <div class="loading-spinner"></div>
            </div>
        `;

        try {
            console.log('Attempting to fetch from backend...');
            
            // Use localhost (not 127.0.0.1) to match cookie domain
            const backendURL = window.location.hostname === 'localhost' || window.location.hostname === '127.0.0.1'
                ? `http://localhost:8001/api/match/all-data`
                : 'https://digitalfamine.stu.nighthawkcodingsociety.com/api/match/all-data';
            
            console.log('Using backend URL:', backendURL);
            console.log('Full URL being called:', backendURL);
            
            // Fetch all profiles from matchmaking endpoint
            const response = await fetch(backendURL, {
                method: 'GET',
                credentials: 'include',
                headers: {
                    'Content-Type': 'application/json',
                },
            });

            console.log('Response status:', response.status);
            console.log('Response ok:', response.ok);

            if (!response.ok) {
                const errorText = await response.text();
                console.error('Error response:', errorText);
                throw new Error(`HTTP ${response.status}: ${errorText}`);
            }

            const data = await response.json();
            console.log('Data received:', data);
            console.log('Response structure:', Object.keys(data));
            
            // Check if we got the expected structure
            if (!data.setups) {
                console.error('Unexpected response structure:', data);
                throw new Error('Invalid response format from API');
            }
            
            console.log('Number of setups:', data.setups.length);
            
            // Show ALL profiles, even those without data filled in yet
            realMatchmakingState.profiles = data.setups.map(p => {
                // If no data field exists, create an empty one with at least the uid
                if (!p.data || Object.keys(p.data).length === 0) {
                    p.data = {
                        name: p.uid,
                        bio: 'No profile data yet'
                    };
                }
                return p;
            });

            console.log('Total profiles to show:', realMatchmakingState.profiles.length);

            if (realMatchmakingState.profiles.length === 0) {
                showNoProfilesMessage();
            } else {
                realMatchmakingState.initialized = true;
                showRealProfile();
            }
        } catch (error) {
            console.error('Full error details:', error);
            
            // Check if it's a 401 error (not logged in)
            const is401 = error.message.includes('401');
            
            if (is401) {
                content.innerHTML = `
                    <div class="error-message">
                        <strong>🔒 Authentication Required</strong><br><br>
                        You need to log in to use Real Matchmaking!
                    </div>
                    <div style="background: #2a2a40; padding: 1.5em; border-radius: 8px; margin-top: 1em; text-align: center;">
                        <p style="color: #c0c0c0; margin-bottom: 1em;">
                            Real Matchmaking connects to your backend and requires authentication.
                        </p>
                        <a href="/login" class="btn-new" style="display: inline-block; text-decoration: none;">
                            🔐 Go to Login Page
                        </a>
                        <p style="color: #8b9dff; margin-top: 1em; font-size: 0.9em;">
                            Or try the Demo Game (no login required)
                        </p>
                        <button class="btn-new" onclick="switchTab('demo')" style="background: #3a3a52; margin-top: 0.5em;">
                            ← Back to Demo Game
                        </button>
                    </div>
                `;
            } else {
                content.innerHTML = `
                    <div class="error-message">
                        <strong>Connection Error</strong><br>
                        ${error.message}<br><br>
                        <strong>Possible issues:</strong><br>
                        • Backend URL incorrect<br>
                        • CORS policy blocking request<br>
                        • No profiles exist yet
                    </div>
                    <div style="background: #2a2a40; padding: 1em; border-radius: 8px; margin-top: 1em; text-align: left;">
                        <strong style="color: #8b9dff;">Debug Info:</strong><br>
                        <code style="color: #c0c0c0; font-size: 0.85em;">
                            API: https://digitalfamine.stu.nighthawkcodingsociety.com/api/match/all-data<br>
                            Check console (F12) for details
                        </code>
                    </div>
                    <button class="btn-new" onclick="initRealMatchmaking()">Retry</button>
                `;
            }
        }
    }

    function showNoProfilesMessage() {
        const content = document.getElementById('realGameContent');
        content.innerHTML = `
            <div style="text-align: center; padding: 2em;">
                <p style="color: #8b9dff; font-size: 1.2em; margin-bottom: 1em;">
                    No profiles available yet! 
                </p>
                <p style="color: #c0c0c0;">
                    Be the first to create a profile and start matching with others.
                </p>
                <button class="btn-new" onclick="initRealMatchmaking()" style="margin-top: 1em;">
                    🔄 Refresh
                </button>
            </div>
        `;
    }

    function calculateRealCompatibility(profile) {
        // Simple compatibility based on shared data fields
        if (!profile.data) return 50;
        
        let score = 0;
        const fields = Object.keys(profile.data).length;
        
        if (fields > 0) score = 50 + (fields * 5);
        return Math.min(score, 100);
    }

    function showRealProfile() {
        const state = realMatchmakingState;
        const content = document.getElementById('realGameContent');
        
        if (state.currentIndex >= state.profiles.length) {
            showRealResults();
            return;
        }

        const profile = state.profiles[state.currentIndex];
        const compatibility = calculateRealCompatibility(profile);

        content.innerHTML = `
            <div class="match-stats">
                <div class="stat-item">
                    <div class="stat-value">${state.matches.length}</div>
                    <div class="stat-label">Matches</div>
                </div>
                <div class="stat-item">
                    <div class="stat-value">${state.skipped.length}</div>
                    <div class="stat-label">Skipped</div>
                </div>
                <div class="stat-item">
                    <div class="stat-value">${state.currentIndex + 1}/${state.profiles.length}</div>
                    <div class="stat-label">Progress</div>
                </div>
            </div>

            <div class="real-profile-card">
                <div class="profile-header">${profile.data.name || profile.uid}</div>
                <div style="color: #c0c0c0; margin: 0.5em 0;">
                    Compatibility: <strong style="color: #8b9dff;">${compatibility}%</strong>
                </div>
                <div class="compatibility-bar">
                    <div class="compatibility-fill" style="width: ${compatibility}%"></div>
                </div>
                
                <div style="margin-top: 1em;">
                    ${Object.entries(profile.data).map(([key, value]) => {
                        if (key === 'name') return '';
                        return `
                            <div class="profile-detail">
                                <strong>${key}:</strong> ${value}
                            </div>
                        `;
                    }).join('')}
                </div>
            </div>

            <div class="button-group">
                <button class="btn btn-skip" onclick="handleRealSkip()">
                    ✗ Skip
                </button>
                <button class="btn btn-match" onclick="handleRealMatch()">
                    ✓ Match
                </button>
            </div>
        `;
    }

    async function handleRealMatch() {
        const state = realMatchmakingState;
        const profile = state.profiles[state.currentIndex];
        const compatibility = calculateRealCompatibility(profile);
        
        // Add to local state
        state.matches.push({
            ...profile,
            compatibility: compatibility
        });
        
        // Save match to backend - get existing matches first, then add new one
        try {
            const backendURL = window.location.hostname === 'localhost' || window.location.hostname === '127.0.0.1'
                ? `http://localhost:8001/api/match/`
                : 'https://digitalfamine.stu.nighthawkcodingsociety.com/api/match/';
            
            // Get current user's data to retrieve existing matches
            const getResponse = await fetch(backendURL + 'data', {
                method: 'GET',
                credentials: 'include',
                headers: {
                    'Content-Type': 'application/json',
                },
            });
            
            let existingMatches = [];
            if (getResponse.ok) {
                const userData = await getResponse.json();
                // Check if user already has matches saved
                if (userData.setup && userData.setup.data && userData.setup.data.matched_with) {
                    existingMatches = Array.isArray(userData.setup.data.matched_with) 
                        ? userData.setup.data.matched_with 
                        : [userData.setup.data.matched_with];
                }
            }
            
            // Add new match to the list (avoid duplicates)
            if (!existingMatches.includes(profile.uid)) {
                existingMatches.push(profile.uid);
            }
            
            // Save updated matches array to backend
            const saveResponse = await fetch(backendURL + 'add', {
                method: 'POST',
                credentials: 'include',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({
                    index: 'matched_with',
                    data: existingMatches
                })
            });
            
            if (saveResponse.ok) {
                console.log(`Match with ${profile.uid} saved to backend. Total matches: ${existingMatches.length}`);
            } else {
                console.error('Failed to save match to backend');
            }
        } catch (error) {
            console.error('Error saving match:', error);
        }
        
        state.currentIndex++;
        showRealProfile();
    }

    function handleRealSkip() {
        const state = realMatchmakingState;
        state.skipped.push(state.profiles[state.currentIndex]);
        state.currentIndex++;
        showRealProfile();
    }

    function showRealResults() {
        const state = realMatchmakingState;
        const content = document.getElementById('realGameContent');

        content.innerHTML = `
            <div style="text-align: center; margin-bottom: 2em;">
                <h3 style="color: #8b9dff; font-size: 1.5em;">🎉 Results</h3>
                <p style="color: #c0c0c0;">You reviewed ${state.profiles.length} profiles</p>
            </div>

            <div style="background: linear-gradient(135deg, #3a3a52 0%, #2d2d42 100%); padding: 1.5em; border-radius: 8px; margin-bottom: 1.5em; border: 2px solid #667eea;">
                <h4 style="color: #8b9dff; margin-top: 0;">✓ Your Matches (${state.matches.length})</h4>
                ${state.matches.length === 0 ? 
                    '<p style="color: #c0c0c0;">No matches yet. Try again!</p>' :
                    state.matches.map(m => `
                        <div style="background: #2a2a40; padding: 1em; border-radius: 6px; margin: 0.5em 0; border-left: 4px solid #27ae60;">
                            <strong style="color: #8b9dff;">${m.data.name || m.uid}</strong>
                            <span style="color: #27ae60; float: right;">${m.compatibility}%</span>
                        </div>
                    `).join('')
                }
            </div>

            <div style="background: #2a2a40; padding: 1em; border-radius: 8px; border: 1px solid #667eea;">
                <p style="color: #c0c0c0; margin: 0;">✗ Skipped: ${state.skipped.length}</p>
            </div>

            <button class="btn-new" onclick="resetRealMatchmaking()">
                🔄 Start Over
            </button>
        `;
    }

    function resetRealMatchmaking() {
        realMatchmakingState = {
            profiles: [],
            currentIndex: 0,
            matches: [],
            skipped: [],
            currentUser: null,
            initialized: false
        };
        initRealMatchmaking();
    }
</script>

---