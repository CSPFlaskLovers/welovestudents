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
<title>Online Safety Interactive Lesson – Visual Mode</title>
<style>
    body {
        font-family: 'Inter', Arial, sans-serif;
        background: #0a0a0a;
        color: #eaeaea;
        margin: 0;
        padding: 0;
    }

    header {
        background: linear-gradient(135deg, #0a2a43, #001119);
        padding: 30px;
        text-align: center;
        font-size: 38px;
        font-weight: 800;
        color: #8fd4ff;
        border-bottom: 2px solid #0e3a55;
        letter-spacing: 1.2px;
        text-shadow: 0 0 12px #0099ff;
    }

    .container {
        width: 88%;
        max-width: 1100px;
        margin: auto;
        padding: 30px 10px;
    }

    .info-card {
        background: #111826;
        padding: 25px;
        margin: 20px 0;
        border-radius: 14px;
        box-shadow: 0 0 20px #000;
        border: 1px solid #1d3247;
        transition: 0.25s ease;
        cursor: pointer;
    }

    .info-card h3 {
        margin: 0 0 10px;
        font-size: 26px;
        color: #7ad7ff;
        font-weight: 700;
    }

    .info-card p, .info-card ul {
        font-size: 16px;
        color: #d3d3d3;
        line-height: 1.6;
        margin-top: 5px;
    }

    .info-card:hover {
        transform: scale(1.02);
        border-color: #4db8ff;
        box-shadow: 0 0 25px #003b5c;
    }

    .visual-mode {
        display: none;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.8);
        backdrop-filter: blur(6px);
        justify-content: center;
        align-items: center;
        z-index: 999;
    }

    .visual-box {
        background: #0e1622;
        padding: 30px;
        border-radius: 20px;
        width: 80%;
        max-width: 700px;
        text-align: center;
        box-shadow: 0 0 25px #000;
        border: 1px solid #2b4d6b;
        animation: pop 0.35s ease;
    }

    @keyframes pop {
        from { transform: scale(0.8); opacity: 0; }
        to { transform: scale(1); opacity: 1; }
    }

    .visual-box h2 {
        color: #9cdcff;
        margin-bottom: 15px;
    }

    .visual-box p {
        font-size: 18px;
        color: #d9d9d9;
        line-height: 1.7;
    }

    .close-btn {
        margin-top: 20px;
        padding: 10px 20px;
        background: #0f6fa4;
        border: none;
        border-radius: 8px;
        color: white;
        cursor: pointer;
        font-size: 16px;
        transition: 0.2s;
    }

    .close-btn:hover {
        background: #45b5ff;
        transform: scale(1.08);
    }
</style>
</head>
<body>

<header>Online Safety Interactive Lesson – Visual Mode</header>
<div class="container">

    <div class="info-card" onclick="openVisual('safety')">
        <h3>What Is Online Safety?</h3>
        <p>Online safety is about protecting your personal information, maintaining privacy, and avoiding risky interactions on the internet, including social platforms and matchmaking apps.</p>
    </div>

    <div class="info-card" onclick="openVisual('matchmaking')">
        <h3>Why Matchmaking Safety Matters</h3>
        <p>When connecting with others online for friendships, dating, or communities, safety is key. Being aware of potential risks ensures healthier interactions and reduces scams or harassment.</p>
        <ul>
            <li>Protect personal info</li>
            <li>Verify identities before trust</li>
            <li>Avoid suspicious links or behavior</li>
            <li>Report and block harmful interactions</li>
        </ul>
    </div>

    <div class="info-card" onclick="openVisual('tips')">
        <h3>Key Safety Tips</h3>
        <p>Simple strategies keep you safe online, whether in chatrooms, social media, or matchmaking platforms.</p>
        <ul>
            <li>Strong passwords & two-factor authentication</li>
            <li>Privacy settings for profiles</li>
            <li>Think before sharing personal info</li>
            <li>Verify people before meeting</li>
            <li>Report suspicious activity</li>
        </ul>
    </div>
</div>

<div id="visual-mode" class="visual-mode" onclick="closeVisual(event)">
    <div class="visual-box" id="visual-box">
        <h2 id="visual-title"></h2>
        <p id="visual-text"></p>
        <button class="close-btn" onclick="closeVisual(event)">Close</button>
    </div>
</div>

<script>
const visuals = {
    safety: {
        title: "Understanding Online Safety",
        text: "Online safety is about staying cautious, verifying information, and keeping control over what you share online."
    },
    matchmaking: {
        title: "Matchmaking Safety",
        text: "Online matchmaking can be fun, but always check profiles, avoid sharing sensitive information, and report suspicious behavior."
    },
    tips: {
        title: "Practical Safety Tips",
        text: "Use strong passwords, enable two-factor authentication, limit personal info sharing, and always stay aware of your digital footprint."
    }
};

function openVisual(id) {
    document.getElementById("visual-title").textContent = visuals[id].title;
    document.getElementById("visual-text").textContent = visuals[id].text;
    document.getElementById("visual-mode").style.display = "flex";
}

function closeVisual(event) {
    if (event.target.id === "visual-mode" || event.target.classList.contains("close-btn")) {
        document.getElementById("visual-mode").style.display = "none";
    }
}
</script>

<!-- INTERACTIVE GAME: ONLINE SAFETY -->
<div class="container" style="margin-top:40px;">
    <div class="info-card" style="cursor:default;">
        <h3>Interactive Game: Build Your Online Safety Persona</h3>
        <p>Answer the prompts below to create a custom online safety identity. Your responses will be safely saved.</p>

        <!-- Question 1 -->
        <div style="margin-top:20px;">
            <label>1. Choose your approach to online safety:</label>
            <select id="style" style="width:100%;padding:10px;margin-top:8px;border-radius:8px;background:#0e1622;color:#dcdcdc;border:1px solid #2b4d6b;">
                <option value="Cautious Explorer">Cautious Explorer</option>
                <option value="Tech-Savvy Protector">Tech-Savvy Protector</option>
                <option value="Friendly Connector">Friendly Connector</option>
                <option value="Minimal Sharer">Minimal Sharer</option>
            </select>
        </div>

        <!-- Question 2 -->
        <div style="margin-top:20px;">
            <label>2. Your safety motto:</label>
            <input id="phrase" type="text" placeholder="ex: Stay aware, stay safe" style="width:100%;padding:10px;margin-top:8px;border-radius:8px;background:#0e1622;color:#dcdcdc;border:1px solid #2b4d6b;">
        </div>

        <!-- Question 3 -->
        <div style="margin-top:20px;">
            <label>3. Pick your safety vibe color:</label>
            <input id="color" type="color" style="width:100%;padding:10px;margin-top:8px;border-radius:8px;background:#0e1622;border:1px solid #2b4d6b;">
        </div>

        <!-- Question 4 -->
        <div style="margin-top:20px;">
            <label>4. How would you handle a suspicious online match?</label>
            <select id="question4" style="width:100%;padding:10px;margin-top:8px;border-radius:8px;background:#0e1622;color:#dcdcdc;border:1px solid #2b4d6b;">
                <option value="Report immediately">Report immediately</option>
                <option value="Ignore and block">Ignore and block</option>
                <option value="Share personal info">Share personal info</option>
                <option value="Continue chatting">Continue chatting</option>
            </select>
        </div>

        <!-- Question 5 -->
        <div style="margin-top:20px;">
            <label>5. What’s your approach to sharing personal information?</label>
            <select id="question5" style="width:100%;padding:10px;margin-top:8px;border-radius:8px;background:#0e1622;color:#dcdcdc;border:1px solid #2b4d6b;">
                <option value="Share minimally">Share minimally</option>
                <option value="Share freely">Share freely</option>
                <option value="Only to verified profiles">Only to verified profiles</option>
                <option value="Never share">Never share</option>
            </select>
        </div>

        <!-- Question 6 -->
        <div style="margin-top:20px;">
            <label>6. Which of these is most important for online safety?</label>
            <select id="question6" style="width:100%;padding:10px;margin-top:8px;border-radius:8px;background:#0e1622;color:#dcdcdc;border:1px solid #2b4d6b;">
                <option value="Strong passwords">Strong passwords</option>
                <option value="Two-factor authentication">Two-factor authentication</option>
                <option value="Privacy settings">Privacy settings</option>
                <option value="All of the above">All of the above</option>
            </select>
        </div>

        <button class="close-btn" style="margin-top:25px;" onclick="submitPersona()">Save to Backend</button>
        <p id="save-status" style="margin-top:15px;font-size:16px;color:#7ad7ff;display:none;">Saving...</p>
    </div>
</div>

<script>
function submitPersona() {
    const data = {
        style: document.getElementById("style").value,
        phrase: document.getElementById("phrase").value,
        color: document.getElementById("color").value,
        question4: document.getElementById("question4").value,
        question5: document.getElementById("question5").value,
        question6: document.getElementById("question6").value
    };

    document.getElementById("save-status").style.display = "block";
    document.getElementById("save-status").textConten
