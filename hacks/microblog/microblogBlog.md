---
layout: post
title: "Submodule 4"
description: "Submodule 4 of AI Usage Mini-Quest"
permalink: /digital-famine/microblog/microb/
submodule: 4
categories: [CSP, Submodule, Microblogging]
tags: [online safety, matchmaking, submodule]
author: "Nicolas Diaz"
breadcrumb: true
---
<html lang="en">
<head>
<meta charset="UTF-8" />
<title>Digital Safety & Online Awareness</title>

<script>
/* ---------- BACKEND URI ---------- */
let pythonURI;
if (location.hostname === "localhost" || location.hostname === "127.0.0.1") {
    pythonURI = "http://localhost:8001";
} else {
    pythonURI = "https://flaskstu.opencodingsociety.com";
}
</script>

<style>
:root {
    --bg-dark: #0a0a0a;
    --card-bg: #111826;
    --accent: #7ad7ff;
    --accent-dark: #0f6fa4;
    --border: #1d3247;
    --text: #eaeaea;
}

/* ---------- GLOBAL ---------- */
body {
    margin: 0;
    font-family: 'Inter', Arial, sans-serif;
    background: var(--bg-dark);
    color: var(--text);
    display: flex;
    flex-direction: column;
    align-items: center;
}

h1, h2, h3 {
    margin: 0;
    text-align: center;
}

/* ---------- HEADER ---------- */
header {
    width: 100%;
    padding: 40px 20px;
    background: linear-gradient(135deg, #0a2a43, #001119);
    text-align: center;
}

header h1 {
    font-size: 42px;
    font-weight: 800;
    color: var(--accent);
}

header p {
    margin-top: 10px;
    font-size: 16px;
    opacity: 0.85;
}

/* ---------- CONTAINER ---------- */
.container {
    width: 100%;
    max-width: 1000px;
    margin: 40px auto;
    display: flex;
    flex-direction: column;
    align-items: center; /* Center all children horizontally */
    gap: 25px;
}

/* ---------- INFO CARDS ---------- */
.info-card {
    background: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 30px;
    cursor: pointer;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    text-align: center;
    width: 80%; /* Make cards narrower */
    max-width: 600px; /* Limit maximum width */
    margin: 0 auto; /* Center horizontally */
}


.info-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 30px rgba(0,0,0,0.4);
}

.info-card h3 {
    color: var(--accent);
    margin-bottom: 10px;
}

/* ---------- MODAL OVERLAY ---------- */
.visual-mode {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.85);
    z-index: 9999; /* OVER EVERYTHING */
    justify-content: center;
    align-items: center;
}

.visual-box {
    background: #0e1622;
    border-radius: 20px;
    padding: 35px;
    width: 90%;
    max-width: 700px;
    max-height: 85vh;
    overflow-y: auto;
    text-align: center;
}

.visual-box h2 {
    color: var(--accent);
    margin-bottom: 20px;
}

.visual-box p {
    white-space: pre-line;
    line-height: 1.6;
}

/* ---------- FORM ---------- */
label {
    margin-top: 18px;
    display: block;
    font-weight: 600;
}

select, input {
    width: 100%;
    margin-top: 8px;
    padding: 12px;
    background: #111826;
    border-radius: 10px;
    border: 1px solid var(--border);
    color: var(--text);
}

button {
    margin-top: 25px;
    padding: 14px;
    width: 100%;
    border-radius: 10px;
    border: none;
    background: var(--accent-dark);
    color: white;
    font-size: 16px;
    cursor: pointer;
}

button:hover {
    opacity: 0.9;
}

/* ---------- RESULT ---------- */
#result-box {
    margin-top: 25px;
    padding-top: 20px;
    border-top: 1px solid var(--border);
    text-align: center;
}
</style>
</head>

<body>

<header>
    <h1>Digital Safety & Online Awareness</h1>
    <p>Learn how to protect yourself in online and matchmaking environments</p>
</header>

<div class="container">

    <div class="info-card" onclick="openVisual('safety')">
        <h3>Understanding Online Safety</h3>
        <p>Learn how to protect your identity and privacy online.</p>
    </div>

    <div class="info-card" onclick="openVisual('matchmaking')">
        <h3>Why Matchmaking Safety Matters</h3>
        <p>Understand the risks of anonymous online interactions.</p>
    </div>

    <div class="info-card" onclick="openVisual('tips')">
        <h3>Practical Digital Safety Tips</h3>
        <p>Simple habits that reduce online risk.</p>
    </div>

</div>

<!-- ---------- MODAL ---------- -->
<div id="visual-mode" class="visual-mode" onclick="closeVisual(event)">
    <div class="visual-box">
        <h2 id="visual-title"></h2>
        <p id="visual-text"></p>
        <button onclick="closeVisual(event)">Close</button>
    </div>
</div>

<!-- ---------- ACTIVITY ---------- -->
<div class="container">
    <div class="info-card" style="cursor:default;">
        <h3>Digital Safety Reflection</h3>

        <label>How would you describe your online interaction style?</label>
        <select id="style">
            <option value="Cautious and selective, prioritizing security over convenience">Cautious</option>
            <option value="Balanced, engaging socially while maintaining clear boundaries">Balanced</option>
            <option value="Open and communicative, but aware of risks">Open</option>
        </select>

        <label>Your personal online safety principle</label>
        <input id="phrase" placeholder="Example: I verify identities before trusting">

        <label>How do you respond to suspicious behavior?</label>
        <select id="question4">
            <option value="I disengage and block the individual immediately">Block immediately</option>
            <option value="I evaluate the situation before acting">Evaluate first</option>
        </select>

        <label>Rule for sharing personal information</label>
        <select id="question5">
            <option value="I only share information when absolutely necessary">Share minimally</option>
            <option value="I share selectively with verified users">Share selectively</option>
        </select>

        <label>Most important digital safety habit</label>
        <select id="question6">
            <option value="Strong authentication">Strong authentication</option>
            <option value="Clear boundaries">Clear boundaries</option>
        </select>

        <button onclick="submitPersona()">Submit Reflection</button>

        <div id="result-box" style="display:none;">
            <h3>Your Safety Profile</h3>
            <p id="result-text"></p>
            <p id="server-status" style="color:var(--accent); margin-top:10px;"></p>
        </div>
    </div>
</div>

<script>
/* ---------- POPUP CONTENT ---------- */
const visuals = [
    {
        id: "safety",
        title: "Understanding Online Safety",
        text: `Online safety involves protecting your personal information, privacy, and digital identity.

It includes recognizing scams, managing privacy settings, and understanding how online actions can have real-world consequences.`
    },
    {
        id: "matchmaking",
        title: "Why Matchmaking Safety Matters",
        text: `Matchmaking platforms often involve anonymous interactions.

This can lead to impersonation, manipulation, or harmful behavior if users are not cautious.`
    },
    {
        id: "tips",
        title: "Practical Digital Safety Tips",
        text: `• Use strong, unique passwords
• Enable two-factor authentication
• Verify identities
• Set boundaries
• Trust your instincts`
    }
];

function openVisual(id) {
    const v = visuals.find(x => x.id === id);
    document.getElementById("visual-title").textContent = v.title;
    document.getElementById("visual-text").textContent = v.text;
    document.getElementById("visual-mode").style.display = "flex";
}

function closeVisual(e) {
    if (e.target.id === "visual-mode" || e.target.tagName === "BUTTON") {
        document.getElementById("visual-mode").style.display = "none";
    }
}

function analyzeResponses(list) {
    let score = 0;
    list.forEach(v => {
        const s = v.toLowerCase();
        if (s.includes("block") || s.includes("verify") || s.includes("necessary")) score++;
    });
    if (score >= 3) return "You demonstrate strong digital safety awareness.";
    if (score === 2) return "You show balanced online safety habits.";
    return "You should strengthen your digital safety practices.";
}

function isLoggedIn() {
    return document.cookie.includes("jwt"); // checks for the JWT cookie
}

function submitPersona() {

    if (!isLoggedIn()) {
        document.getElementById("result-box").style.display = "block";
        document.getElementById("result-text").textContent =
            "You must be logged in to submit your reflection.";
        document.getElementById("server-status").textContent =
            "Please log in before posting to the microblog.";
        return;
    }

    const responses = {
        style: style.value,
        principle: phrase.value,
        reaction: question4.value,
        sharing: question5.value,
        priority: question6.value
    };

    const analysis = analyzeResponses(Object.values(responses));

    document.getElementById("result-text").textContent = analysis;
    document.getElementById("result-box").style.display = "block";
    document.getElementById("server-status").textContent = "Posting to microblog…";

    fetch(`${pythonURI}/api/microblog`, {
        method: "POST",
        credentials: "include",
        headers: {
            "Content-Type": "application/json",
            "X-Origin": "client"
        },
        body: JSON.stringify({
            content: `Safety Reflection:\n${analysis}`,
            topicPath: "/digital-famine/microblog/microb/",
            data: responses
        })
    })
    .then(res => res.json())
    .then(data => {
        document.getElementById("server-status").textContent =
            data.error ? data.message : "Reflection successfully posted!";
    })
    .catch(err => {
        document.getElementById("server-status").textContent = "Could not connect to server.";
        console.error(err);
    });
}
</script>

</body>
</html>
