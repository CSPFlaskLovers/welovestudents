---
layout: post
title: Microblog API
permalink: /digital-famine/microblog/api/
author: Cyrus, William W
breadcrumb: true
---

<style>
/* Force dark mode for entire page */
.hero-section {
    background: linear-gradient(135deg, #4338ca 0%, #6366f1 100%) !important;
    color: #e2e8f0 !important;
    padding: 3rem 2rem;
    border-radius: 12px;
    margin-bottom: 2rem;
    text-align: center;
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.3);
}

.hero-section h1 {
    font-size: 2.5rem;
    margin-bottom: 1rem;
    color: #ffffff !important;
}

.hero-section p {
    font-size: 1.2rem;
    color: #e2e8f0 !important;
}

.section-card {
    background: #1e293b !important;
    border-radius: 12px;
    padding: 2rem;
    margin-bottom: 2rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
    border: 1px solid #334155;
    color: #e2e8f0 !important;
}

.section-card p, .section-card li, .section-card em, .section-card strong {
    color: #cbd5e1 !important;
}

.section-title {
    font-size: 1.8rem;
    color: #818cf8 !important;
    margin-bottom: 1rem;
    padding-bottom: 0.5rem;
    border-bottom: 3px solid #6366f1;
}

.info-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1.5rem;
    margin-top: 1.5rem;
}

.info-box {
    background: linear-gradient(135deg, #4338ca 0%, #6366f1 100%) !important;
    color: #ffffff !important;
    padding: 1.5rem;
    border-radius: 8px;
    transition: transform 0.3s ease;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
}

.info-box:hover {
    transform: translateY(-5px);
}

.info-box h3 {
    font-size: 1.2rem;
    margin-bottom: 0.5rem;
    color: #ffffff !important;
}

.info-box p {
    font-size: 0.95rem;
    line-height: 1.5;
    color: #e2e8f0 !important;
}

.code-block, code {
    background: #0f172a !important;
    color: #cbd5e1 !important;
    padding: 0.25rem 0.5rem !important;
    border-radius: 4px !important;
    margin: 0 !important;
    font-family: 'Courier New', monospace;
    border: 1px solid #1e293b;
    display: inline !important;
    font-size: 0.9em !important;
}

/* For code blocks that should be larger */
pre code {
    display: block !important;
    padding: 1.5rem !important;
    margin: 1rem 0 !important;
    border-radius: 8px !important;
    overflow-x: auto;
}

/* Bash code blocks */
.step-card code {
    background: #0f172a !important;
    color: #10b981 !important;
    padding: 0.25rem 0.5rem !important;
    border-radius: 4px !important;
    font-size: 0.9em !important;
    display: inline !important;
}

.step-card {
    background: #334155 !important;
    border-left: 4px solid #6366f1;
    padding: 1.5rem;
    margin-bottom: 1.5rem;
    border-radius: 0 8px 8px 0;
    color: #e2e8f0 !important;
}

.step-card h4 {
    color: #818cf8 !important;
    margin-bottom: 0.5rem;
}

.step-card p, .step-card em {
    color: #cbd5e1 !important;
}

.activity-card {
    background: linear-gradient(to right, #422006, #78350f) !important;
    padding: 1.5rem;
    border-radius: 8px;
    margin-bottom: 1.5rem;
    border-left: 4px solid #f59e0b;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
}

.activity-card h3 {
    color: #fbbf24 !important;
    margin-bottom: 0.5rem;
}

.activity-card ol, .activity-card li, .activity-card strong {
    color: #fde68a !important;
}

.tips-banner {
    background: #1e3a8a !important;
    border: 2px solid #3b82f6;
    border-radius: 8px;
    padding: 1rem 1.5rem;
    margin: 1.5rem 0;
    color: #bfdbfe !important;
}

.tips-banner strong, .tips-banner code {
    color: #dbeafe !important;
}

/* Navigation styles */
.section-card ul {
    color: #cbd5e1 !important;
}

.section-card a {
    color: #818cf8 !important;
}

.section-card a:hover {
    color: #a5b4fc !important;
}

/* Table styles */
.section-card table {
    background: #0f172a !important;
    border: 1px solid #334155;
}

.section-card th {
    background: #1e293b !important;
    color: #818cf8 !important;
    border: 1px solid #334155;
}

.section-card td {
    color: #cbd5e1 !important;
    border: 1px solid #334155;
}

/* Ordered and unordered lists */
.section-card ol, .section-card ul {
    color: #cbd5e1 !important;
}

.section-card ol li, .section-card ul li {
    color: #cbd5e1 !important;
}
</style>

<div class="hero-section">
    <h1>🚀 Microblog API - Beginner's Guide</h1>
    <p>A simple social media backend built with Python - perfect for learning how APIs work!</p>
</div>

<div id="auth-check-banner" style="display: none; background: #7f1d1d !important; color: #fca5a5 !important; padding: 1.5rem; border-radius: 8px; margin-bottom: 2rem; text-align: center; border: 2px solid #dc2626;">
    <h3 style="color: #fca5a5 !important; margin-bottom: 0.5rem;">🔒 Authentication Required</h3>
    <p style="color: #fecaca !important; margin-bottom: 1rem;">You must be logged in to use the interactive features on this page.</p>
    <a id="login-redirect-btn" href="#" style="display: inline-block; background: #dc2626 !important; color: white !important; padding: 0.75rem 1.5rem; border-radius: 6px; text-decoration: none; font-weight: bold; transition: background 0.3s;">
        Login Now →
    </a>
</div>

<script>
// Check for authentication on page load
(function() {
    function getCookie(name) {
        const value = `; ${document.cookie}`;
        const parts = value.split(`; ${name}=`);
        if (parts.length === 2) return parts.pop().split(';').shift();
        return null;
    }
    
    const jwtCookie = getCookie('jwt_python_flask');
    
    if (!jwtCookie || jwtCookie.trim() === '') {
        // Show authentication banner
        const banner = document.getElementById('auth-check-banner');
        if (banner) {
            banner.style.display = 'block';
        }
        
        // Set up login redirect button with correct URL
        const loginBtn = document.getElementById('login-redirect-btn');
        if (loginBtn) {
            // Get base URL dynamically
            const protocol = window.location.protocol;
            const hostname = window.location.hostname;
            const port = window.location.port;
            
            let baseUrl;
            if (hostname === 'localhost' || hostname === '127.0.0.1') {
                baseUrl = `${protocol}//${hostname}:${port}`;
            } else {
                baseUrl = `${protocol}//${hostname}`;
            }
            
            loginBtn.href = `${baseUrl}/welovestudents/login`;
        }
    }
})();
</script>

---

## 📚 Quick Navigation

- [What is This?](#what-is-this)
- [Why Should I Care?](#why-should-i-care)
- [How to Run It](#how-to-run-it)
- [Matchmaking API Tester](#matchmaking-api-tester)
- [Knowledge Check Quiz](#knowledge-check-quiz)

---

<div class="section-card">
<h2 class="section-title">🤔 What is This?</h2>

**Microblog API** is like a mini-Twitter backend. It's the server part of a social media app where:

- 👥 Users can sign up and log in
- 📝 Users can write posts
- 📖 Users can read other people's posts

**Important:** This is just the backend - there's no pretty website interface. It's the "behind the scenes" code that makes everything work.

<div class="tips-banner">
<strong>💡 Think of it like this:</strong><br>
Instagram App (Frontend) ↔️ Instagram's Servers (Backend like this!)
</div>

</div>

---

<div class="section-card">
<h2 class="section-title">🎯 Why Should I Care?</h2>

<div class="info-grid">
    <div class="info-box">
        <h3>📚 AP CSP Concepts</h3>
        <p>Networks, data, the internet, and how apps work</p>
    </div>
    <div class="info-box">
        <h3>🐍 Uses Python</h3>
        <p>You might already know some Python!</p>
    </div>
    <div class="info-box">
        <h3>👀 See it Work</h3>
        <p>Not just theory - you can actually run it and test it</p>
    </div>
    <div class="info-box">
        <h3>🌐 Real-World</h3>
        <p>This is how actual apps like Instagram work</p>
    </div>
</div>

**You don't need to understand all the code!** The goal is to:
- ✅ See how a backend works
- ✅ Try using an API
- ✅ Understand how data moves around

</div>

---

<div class="section-card">
<h2 class="section-title">🚀 How to Run It</h2>

### Option A: Docker (Recommended) 🐳

<div class="step-card">
<h4>Step 1: Get the code</h4>

```bash
git clone https://github.com/miguelgrinberg/microblog-api
cd microblog-api
```
</div>

<div class="step-card">
<h4>Step 2: Set up the settings file</h4>

```bash
cp .env.example .env
```
<em>This just copies a template file - you can skip editing it for now</em>
</div>

<div class="step-card">
<h4>Step 3: Start it up! 🎉</h4>

```bash
docker-compose up -d
```
<em>Wait a minute for it to start...</em>
</div>

<div class="step-card">
<h4>Step 4: Check if it's working</h4>

Open your web browser and go to: `http://localhost:5000/docs`

You should see a page with API documentation!
</div>

<div class="step-card">
<h4>Step 5: Add some fake data to play with</h4>

```bash
docker-compose run --rm microblog-api bash -c "flask fake users 10 && flask fake posts 100"
```
Now you have 10 fake users and 100 fake posts to test with!
</div>

<div class="tips-banner">
<strong>⚠️ Common Problem:</strong> If you see an error about port 5000, on newer Macs Apple uses that port. Try: <code>flask run --port=4000</code> and visit <code>http://localhost:4000/docs</code>
</div>

### Option B: Python Way 🐍

<div class="step-card">
<h4>Step 1: Get the code & Set up environment</h4>

```bash
git clone https://github.com/miguelgrinberg/microblog-api
cd microblog-api
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
</div>

<div class="step-card">
<h4>Step 2: Set up the database & Run it</h4>

```bash
alembic upgrade head
flask fake users 10
flask fake posts 100
flask run
```

Then visit: `http://localhost:5000/docs`
</div>

</div>

---

<div class="section-card">
<h2 class="section-title">🛠️ Matchmaking API Tester</h2>
<p style="margin-bottom: 1.5rem;">Test your matchmaking API endpoints directly in the browser - just like Postman! <strong>Note:</strong> You must be logged in to use this tool.</p>

<div style="background: #1e3a8a; border: 2px solid #3b82f6; border-radius: 8px; padding: 1.5rem; margin-bottom: 2rem;">
<h3 style="color: #dbeafe !important; margin-bottom: 1rem;">📋 Quick Start Guide</h3>

<div id="step-content" style="color: #bfdbfe !important; min-height: 120px;">
<!-- Step content will be inserted here by JavaScript -->
</div>

<div style="display: flex; justify-content: space-between; align-items: center; margin-top: 1.5rem;">
<button id="prevBtn" onclick="changeStep(-1)" style="background: #475569 !important; color: white !important; padding: 0.5rem 1.5rem; border: none; border-radius: 6px; cursor: pointer; font-weight: bold; transition: background 0.3s;">
← Previous
</button>
<div style="color: #93c5fd !important; font-weight: bold;">
Step <span id="currentStep">1</span> of 5
</div>
<button id="nextBtn" onclick="changeStep(1)" style="background: #3b82f6 !important; color: white !important; padding: 0.5rem 1.5rem; border: none; border-radius: 6px; cursor: pointer; font-weight: bold; transition: background 0.3s;">
Next →
</button>
</div>
</div>

<script>
let currentStepIndex = 0;

const steps = [
{
title: "Step 1: Initialize Your Profile",
content: "Click <strong>\"POST Setup Profile\"</strong> to create your matchmaking profile. You should see a success message with status 201. ⚠️ <strong>Only do this once!</strong> If you already have a profile, you'll get a 409 error (profile already exists)."
},
{
title: "Step 2: Add Your Information",
content: "Click <strong>\"POST Add Profile Data\"</strong> to add information like your favorite hobbies, interests, etc. Edit the JSON body to add different data fields. You can call this multiple times to add more data."
},
{
title: "Step 3: View Your Profile",
content: "Click <strong>\"GET Profile Data\"</strong> to see all your saved information. This shows everything you've added to your profile."
},
{
title: "Step 4: Save Quiz Results",
content: "Click <strong>\"POST Save Profile JSON\"</strong> to save multiple questions and answers at once (like from a quiz or form). This is useful for bulk updates to your profile."
},
{
title: "Step 5: View All Users",
content: "Click <strong>\"GET All Users Data\"</strong> to see everyone's profile data (useful for matching algorithms and seeing what others have shared)."
}
];

function showStep(index) {
const stepContent = document.getElementById('step-content');
const currentStepDisplay = document.getElementById('currentStep');
const prevBtn = document.getElementById('prevBtn');
const nextBtn = document.getElementById('nextBtn');

stepContent.innerHTML = `
<h4 style="color: #93c5fd !important; margin-bottom: 0.5rem;">${steps[index].title}</h4>
<p style="color: #bfdbfe !important;">${steps[index].content}</p>
`;

currentStepDisplay.textContent = index + 1;

// Disable/enable buttons
prevBtn.disabled = index === 0;
nextBtn.disabled = index === steps.length - 1;

prevBtn.style.opacity = index === 0 ? '0.5' : '1';
prevBtn.style.cursor = index === 0 ? 'not-allowed' : 'pointer';

nextBtn.style.opacity = index === steps.length - 1 ? '0.5' : '1';
nextBtn.style.cursor = index === steps.length - 1 ? 'not-allowed' : 'pointer';
}

function changeStep(direction) {
currentStepIndex += direction;
if (currentStepIndex < 0) currentStepIndex = 0;
if (currentStepIndex >= steps.length) currentStepIndex = steps.length - 1;
showStep(currentStepIndex);
}

// Initialize first step
showStep(0);
</script>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .api-tester-container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 1.5rem;
            background: #1a1a2e !important;
            border-radius: 0.5rem;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.3);
        }
        
        .api-tester-header {
            background: #16213e !important;
            border-radius: 0.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.3);
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border: 1px solid #2d3748;
        }
        
        .header-title {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 1.5rem;
        }
        
        .header-title h2 {
            font-size: 1.875rem;
            font-weight: bold;
            color: #e2e8f0 !important;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin: 0;
        }
        
        .auth-badge {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.875rem;
            color: #fbbf24 !important;
            background: #422006 !important;
            padding: 0.5rem 1rem;
            border-radius: 0.5rem;
            border: 1px solid #92400e;
        }
        
        .examples-section {
            margin-bottom: 1.5rem;
        }
        
        .examples-section h3 {
            font-size: 0.875rem;
            font-weight: 600;
            color: #cbd5e1 !important;
            margin-bottom: 0.5rem;
        }
        
        .examples-buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
        }
        
        .example-btn {
            font-size: 0.75rem;
            padding: 0.25rem 0.75rem;
            border-radius: 0.375rem;
            border: none;
            cursor: pointer;
            transition: all 0.2s;
            font-weight: 600;
        }
        
        .example-btn.get {
            background: #1e40af !important;
            color: #dbeafe !important;
        }
        
        .example-btn.get:hover {
            background: #1e3a8a !important;
        }
        
        .example-btn.post {
            background: #065f46 !important;
            color: #d1fae5 !important;
        }
        
        .example-btn.post:hover {
            background: #064e3b !important;
        }
        
        .example-btn.delete {
            background: #991b1b !important;
            color: #fee2e2 !important;
        }
        
        .example-btn.delete:hover {
            background: #7f1d1d !important;
        }
        
        .request-section {
            margin-bottom: 1rem;
        }
        
        .request-label {
            display: block;
            font-size: 0.875rem;
            font-weight: 600;
            color: #cbd5e1 !important;
            margin-bottom: 0.5rem;
        }
        
        .request-controls {
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
        }
        
        .method-select {
            padding: 0.5rem 1rem;
            border: 2px solid #4a5568 !important;
            border-radius: 0.5rem;
            font-weight: 600;
            font-size: 1rem;
            background: #2d3748 !important;
            color: #e2e8f0 !important;
            cursor: pointer;
        }
        
        .method-select:focus {
            outline: none;
            border-color: #3b82f6 !important;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        
        .url-input {
            flex: 1;
            min-width: 300px;
            padding: 0.5rem 1rem;
            border: 2px solid #4a5568 !important;
            border-radius: 0.5rem;
            font-size: 1rem;
            background: #2d3748 !important;
            color: #e2e8f0 !important;
        }
        
        .url-input:focus {
            outline: none;
            border-color: #3b82f6 !important;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        
        .send-btn {
            padding: 0.5rem 1.5rem;
            border: none;
            border-radius: 0.5rem;
            font-weight: 600;
            color: #ffffff !important;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .send-btn.GET {
            background: #3b82f6 !important;
        }
        
        .send-btn.GET:hover {
            background: #2563eb !important;
        }
        
        .send-btn.POST {
            background: #10b981 !important;
        }
        
        .send-btn.POST:hover {
            background: #059669 !important;
        }
        
        .send-btn.PUT {
            background: #eab308 !important;
        }
        
        .send-btn.PUT:hover {
            background: #ca8a04 !important;
        }
        
        .send-btn.DELETE {
            background: #ef4444 !important;
        }
        
        .send-btn.DELETE:hover {
            background: #dc2626 !important;
        }
        
        .send-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        .clear-btn {
            padding: 0.5rem 1rem;
            background: #64748b !important;
            color: #ffffff !important;
            border: none;
            border-radius: 0.5rem;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .clear-btn:hover {
            background: #475569 !important;
        }
        
        .body-section {
            margin-top: 1rem;
        }
        
        .body-textarea {
            width: 100%;
            height: 160px;
            padding: 1rem;
            border: 2px solid #4a5568 !important;
            border-radius: 0.5rem;
            font-family: 'Courier New', monospace;
            font-size: 0.875rem;
            background: #2d3748 !important;
            color: #e2e8f0 !important;
            resize: vertical;
        }
        
        .body-textarea:focus {
            outline: none;
            border-color: #3b82f6 !important;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        
        .response-container {
            background: #16213e !important;
            border-radius: 0.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.3);
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border: 1px solid #2d3748;
        }
        
        .response-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 1rem;
        }
        
        .response-header h3 {
            font-size: 1.125rem;
            font-weight: 600;
            color: #e2e8f0 !important;
            margin: 0;
        }
        
        .status-badge {
            padding: 0.25rem 1rem;
            border-radius: 9999px;
            font-size: 0.875rem;
            font-weight: 600;
        }
        
        .status-badge.success {
            color: #6ee7b7 !important;
            background: #064e3b !important;
            border: 1px solid #059669;
        }
        
        .status-badge.error {
            color: #fca5a5 !important;
            background: #7f1d1d !important;
            border: 1px solid #dc2626;
        }
        
        .status-badge.auth {
            color: #fcd34d !important;
            background: #422006 !important;
            border: 1px solid #ca8a04;
        }
        
        .response-content {
            background: #0f172a !important;
            color: #cbd5e1 !important;
            padding: 1rem;
            border-radius: 0.5rem;
            overflow-x: auto;
            font-family: 'Courier New', monospace;
            font-size: 0.875rem;
            max-height: 400px;
            overflow-y: auto;
            white-space: pre-wrap;
            border: 1px solid #1e293b;
        }
        
        .tips-section {
            background: #1e3a8a !important;
            border: 1px solid #2563eb;
            border-radius: 0.5rem;
            padding: 1rem;
            margin-top: 1.5rem;
        }
        
        .tips-section h4 {
            font-weight: 600;
            color: #dbeafe !important;
            margin-bottom: 0.5rem;
        }
        
        .tips-section ul {
            font-size: 0.875rem;
            color: #bfdbfe !important;
            list-style: none;
            padding: 0;
            margin: 0;
        }
        
        .tips-section li {
            margin-bottom: 0.25rem;
        }
    </style>
</head>
<body>
    <div class="api-tester-container">
        <div class="api-tester-header">
            <div class="header-title">
                <h2>
                    <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <line x1="22" y1="2" x2="11" y2="13"></line>
                        <polygon points="22 2 15 22 11 13 2 9 22 2"></polygon>
                    </svg>
                    Matchmaking API Tester
                </h2>
                <div class="auth-badge">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect>
                        <path d="M7 11V7a5 5 0 0 1 10 0v4"></path>
                    </svg>
                    <span>Requires JWT Authentication</span>
                </div>
            </div>

            <div class="examples-section">
                <h3>🎯 Matchmaking API Endpoints:</h3>
                <div class="examples-buttons">
                    <button class="example-btn post" onclick="loadExample('setupProfile')">1️⃣ POST Setup Profile</button>
                    <button class="example-btn post" onclick="loadExample('addProfileData')">2️⃣ POST Add Profile Data</button>
                    <button class="example-btn get" onclick="loadExample('getProfile')">3️⃣ GET Profile Data</button>
                    <button class="example-btn post" onclick="loadExample('saveProfileJSON')">4️⃣ POST Save Profile JSON</button>
                    <button class="example-btn get" onclick="loadExample('getAllData')">5️⃣ GET All Users Data</button>
                </div>
            </div>

            <div class="request-section">
                <label class="request-label">Request</label>
                <div class="request-controls">
                    <select id="method" class="method-select">
                        <option value="GET">GET</option>
                        <option value="POST">POST</option>
                        <option value="PUT">PUT</option>
                        <option value="DELETE">DELETE</option>
                    </select>
                    
                    <input 
                        type="text" 
                        id="url" 
                        class="url-input" 
                        value="http://localhost:8001/api/match/"
                        placeholder="http://localhost:8001/api/match/endpoint"
                    />
                    
                    <button id="sendBtn" class="send-btn GET" onclick="sendRequest()">
                        <span id="btnText">Send</span>
                        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                            <line x1="22" y1="2" x2="11" y2="13"></line>
                            <polygon points="22 2 15 22 11 13 2 9 22 2"></polygon>
                        </svg>
                    </button>
                    
                    <button class="clear-btn" onclick="clearAll()">
                        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                            <polyline points="3 6 5 6 21 6"></polyline>
                            <path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"></path>
                        </svg>
                    </button>
                </div>
            </div>

            <div id="bodySection" class="body-section" style="display: none;">
                <label class="request-label">Request Body (JSON)</label>
                <textarea 
                    id="requestBody" 
                    class="body-textarea"
                    placeholder='{\n  "key": "value"\n}'
                >{
  
}</textarea>
            </div>
        </div>

        <div class="response-container">
            <div class="response-header">
                <h3>Response</h3>
                <span id="statusBadge" class="status-badge" style="display: none;"></span>
            </div>
            <pre id="responseContent" class="response-content">Response will appear here...</pre>
        </div>

        <div id="headersSection" class="response-container" style="display: none;">
            <div class="response-header">
                <h3>Response Headers</h3>
            </div>
            <pre id="headersContent" class="response-content"></pre>
        </div>

        <div class="tips-section">
            <h4>💡 Tips:</h4>
            <ul>
                <li>• Follow the numbered buttons in order for best results</li>
                <li>• Start with "Setup Profile" to initialize your matchmaking profile (only once!)</li>
                <li>• Use "Add Profile Data" to add individual fields like hobbies, interests, etc.</li>
                <li>• Use "Save Profile JSON" to save multiple questions/answers at once</li>
                <li>• Check your profile anytime with "GET Profile Data"</li>
                <li>• Status 201 = Success (Created), 200 = Success, 404 = Not Found, 409 = Already Exists</li>
                <li>• Your profile data is saved and will be used for matchmaking later!</li>
            </ul>
        </div>
    </div>

    <script>
        const methodSelect = document.getElementById('method');
        const urlInput = document.getElementById('url');
        const requestBodyTextarea = document.getElementById('requestBody');
        const bodySection = document.getElementById('bodySection');
        const sendBtn = document.getElementById('sendBtn');
        const btnText = document.getElementById('btnText');
        const responseContent = document.getElementById('responseContent');
        const statusBadge = document.getElementById('statusBadge');
        const headersSection = document.getElementById('headersSection');
        const headersContent = document.getElementById('headersContent');

        function getCookie(name) {
            const value = `; ${document.cookie}`;
            const parts = value.split(`; ${name}=`);
            if (parts.length === 2) return parts.pop().split(';').shift();
            return null;
        }

        function checkAuthentication() {
            let jwtCookie = getCookie('jwt_python_flask');
            
            console.log('All cookies:', document.cookie);
            console.log('Looking for jwt_python_flask:', jwtCookie);
            
            if (!jwtCookie || jwtCookie.trim() === '') {
                methodSelect.disabled = true;
                urlInput.disabled = true;
                requestBodyTextarea.disabled = true;
                sendBtn.disabled = true;
                
                responseContent.innerHTML = `<div style="color: #fbbf24; font-weight: bold; font-size: 1.2rem; text-align: center; padding: 2rem;">
                    🔒 Authentication Required
                    
                    <div style="color: #cbd5e1; font-size: 0.9rem; margin-top: 1rem; font-weight: normal;">
                        You must be logged in to use the API tester.
                        
                        Please log in to your account first, then refresh this page.
                    </div>
                </div>`;
                
                const exampleButtons = document.querySelectorAll('.example-btn');
                exampleButtons.forEach(btn => {
                    btn.disabled = true;
                    btn.style.opacity = '0.5';
                    btn.style.cursor = 'not-allowed';
                });
                
                return false;
            }
            return true;
        }

        const isAuthenticated = checkAuthentication();

        methodSelect.addEventListener('change', function() {
            if (!isAuthenticated) return;
            
            const method = this.value;
            sendBtn.className = `send-btn ${method}`;
            
            if (method === 'POST' || method === 'PUT') {
                bodySection.style.display = 'block';
            } else {
                bodySection.style.display = 'none';
            }
        });

        function loadExample(example) {
            if (!isAuthenticated) {
                alert('Please log in to use the API tester.');
                return;
            }
            
            switch(example) {
                case 'setupProfile':
                    methodSelect.value = 'POST';
                    urlInput.value = 'http://localhost:8001/api/match/setup';
                    requestBodyTextarea.value = '{}';
                    break;
                case 'addProfileData':
                    methodSelect.value = 'POST';
                    urlInput.value = 'http://localhost:8001/api/match/add';
                    requestBodyTextarea.value = '{\n  "index": "favorite_hobby",\n  "data": "Reading and coding"\n}';
                    break;
                case 'getProfile':
                    methodSelect.value = 'GET';
                    urlInput.value = 'http://localhost:8001/api/match/data';
                    requestBodyTextarea.value = '{}';
                    break;
                case 'saveProfileJSON':
                    methodSelect.value = 'POST';
                    urlInput.value = 'http://localhost:8001/api/match/save-profile-json';
                    requestBodyTextarea.value = '{\n  "profile_data": [\n    {\n      "question": "What is your favorite hobby?",\n      "response": "Reading"\n    },\n    {\n      "question": "What is your preferred study time?",\n      "response": "Morning"\n    },\n    {\n      "question": "What type of projects do you enjoy?",\n      "response": "Web development"\n    },\n    {\n      "question": "What programming language do you prefer?",\n      "response": "Python"\n    }\n  ]\n}';
                    break;
                case 'getAllData':
                    methodSelect.value = 'GET';
                    urlInput.value = 'http://localhost:8001/api/match/all-data';
                    requestBodyTextarea.value = '{}';
                    break;
            }
            
            methodSelect.dispatchEvent(new Event('change'));
        }

        async function sendRequest() {
            if (!isAuthenticated) {
                alert('Please log in to use the API tester.');
                return;
            }
            
            const jwtCookie = getCookie('jwt_python_flask');
            console.log('JWT cookie check before request:', jwtCookie);
            
            if (!jwtCookie || jwtCookie.trim() === '') {
                responseContent.innerHTML = `<div style="color: #fca5a5; font-weight: bold; text-align: center;">
                    ⚠️ Your session has expired. Please log in again.
                </div>`;
                return;
            }
            
            const method = methodSelect.value;
            const url = urlInput.value;
            const requestBody = requestBodyTextarea.value;

            btnText.textContent = 'Sending...';
            sendBtn.disabled = true;
            responseContent.textContent = '';
            statusBadge.style.display = 'none';
            headersSection.style.display = 'none';

            try {
                const options = {
                    method: method,
                    mode: 'cors',
                    credentials: 'include',
                    headers: {
                        'Content-Type': 'application/json',
                        'X-Origin': 'client'
                    }
                };

                if (method === 'POST' || method === 'PUT' || method === 'DELETE') {
                    try {
                        JSON.parse(requestBody);
                        options.body = requestBody;
                    } catch (e) {
                        responseContent.textContent = 'Invalid JSON in request body';
                        btnText.textContent = 'Send';
                        sendBtn.disabled = false;
                        return;
                    }
                }

                const startTime = Date.now();
                const response = await fetch(url, options);
                const duration = Date.now() - startTime;

                statusBadge.textContent = `Status: ${response.status}`;
                statusBadge.style.display = 'inline-block';
                
                if (response.status === 401 || response.status === 403) {
                    statusBadge.className = 'status-badge auth';
                } else if (response.status >= 200 && response.status < 300) {
                    statusBadge.className = 'status-badge success';
                } else {
                    statusBadge.className = 'status-badge error';
                }

                const responseHeaders = {};
                response.headers.forEach((value, key) => {
                    responseHeaders[key] = value;
                });
                headersContent.textContent = JSON.stringify(responseHeaders, null, 2);
                headersSection.style.display = 'block';

                let data;
                const contentType = response.headers.get('content-type');
                if (contentType && contentType.includes('application/json')) {
                    data = await response.json();
                } else {
                    data = await response.text();
                }

                const responseObj = {
                    status: response.status,
                    statusText: response.statusText,
                    duration: `${duration}ms`,
                    data: data
                };

                if (response.status === 401 || response.status === 403) {
                    responseObj.authMessage = '⚠️ Authentication required. Please log in to access this endpoint.';
                }

                responseContent.textContent = JSON.stringify(responseObj, null, 2);

            } catch (error) {
                responseContent.textContent = `Error: ${error.message}\n\nPlease check:\n- Is the server running?\n- Is the URL correct?\n- Are you logged in?`;
                statusBadge.style.display = 'none';
            }

            btnText.textContent = 'Send';
            sendBtn.disabled = false;
        }

        function clearAll() {
            if (!isAuthenticated) {
                alert('Please log in to use the API tester.');
                return;
            }
            
            urlInput.value = 'http://localhost:8001/api/match/';
            requestBodyTextarea.value = '{}';
            responseContent.textContent = 'Response will appear here...';
            statusBadge.style.display = 'none';
            headersSection.style.display = 'none';
        }
    </script>
</body>
</html>

</div>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .api-tester-container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 1.5rem;
            background: #1a1a2e !important;
            border-radius: 0.5rem;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.3);
        }
        
        .api-tester-header {
            background: #16213e !important;
            border-radius: 0.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.3);
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border: 1px solid #2d3748;
        }
        
        .header-title {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 1.5rem;
        }
        
        .header-title h2 {
            font-size: 1.875rem;
            font-weight: bold;
            color: #e2e8f0 !important;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin: 0;
        }
        
        .auth-badge {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.875rem;
            color: #fbbf24 !important;
            background: #422006 !important;
            padding: 0.5rem 1rem;
            border-radius: 0.5rem;
            border: 1px solid #92400e;
        }
        
        .examples-section {
            margin-bottom: 1.5rem;
        }
        
        .examples-section h3 {
            font-size: 0.875rem;
            font-weight: 600;
            color: #cbd5e1 !important;
            margin-bottom: 0.5rem;
        }
        
        .examples-buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
        }
        
        .example-btn {
            font-size: 0.75rem;
            padding: 0.25rem 0.75rem;
            border-radius: 0.375rem;
            border: none;
            cursor: pointer;
            transition: all 0.2s;
            font-weight: 600;
        }
        
        .example-btn.get {
            background: #1e40af !important;
            color: #dbeafe !important;
        }
        
        .example-btn.get:hover {
            background: #1e3a8a !important;
        }
        
        .example-btn.post {
            background: #065f46 !important;
            color: #d1fae5 !important;
        }
        
        .example-btn.post:hover {
            background: #064e3b !important;
        }
        
        .example-btn.delete {
            background: #991b1b !important;
            color: #fee2e2 !important;
        }
        
        .example-btn.delete:hover {
            background: #7f1d1d !important;
        }
        
        .request-section {
            margin-bottom: 1rem;
        }
        
        .request-label {
            display: block;
            font-size: 0.875rem;
            font-weight: 600;
            color: #cbd5e1 !important;
            margin-bottom: 0.5rem;
        }
        
        .request-controls {
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
        }
        
        .method-select {
            padding: 0.5rem 1rem;
            border: 2px solid #4a5568 !important;
            border-radius: 0.5rem;
            font-weight: 600;
            font-size: 1rem;
            background: #2d3748 !important;
            color: #e2e8f0 !important;
            cursor: pointer;
        }
        
        .method-select:focus {
            outline: none;
            border-color: #3b82f6 !important;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        
        .url-input {
            flex: 1;
            min-width: 300px;
            padding: 0.5rem 1rem;
            border: 2px solid #4a5568 !important;
            border-radius: 0.5rem;
            font-size: 1rem;
            background: #2d3748 !important;
            color: #e2e8f0 !important;
        }
        
        .url-input:focus {
            outline: none;
            border-color: #3b82f6 !important;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        
        .send-btn {
            padding: 0.5rem 1.5rem;
            border: none;
            border-radius: 0.5rem;
            font-weight: 600;
            color: #ffffff !important;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .send-btn.GET {
            background: #3b82f6 !important;
        }
        
        .send-btn.GET:hover {
            background: #2563eb !important;
        }
        
        .send-btn.POST {
            background: #10b981 !important;
        }
        
        .send-btn.POST:hover {
            background: #059669 !important;
        }
        
        .send-btn.PUT {
            background: #eab308 !important;
        }
        
        .send-btn.PUT:hover {
            background: #ca8a04 !important;
        }
        
        .send-btn.DELETE {
            background: #ef4444 !important;
        }
        
        .send-btn.DELETE:hover {
            background: #dc2626 !important;
        }
        
        .send-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        .clear-btn {
            padding: 0.5rem 1rem;
            background: #64748b !important;
            color: #ffffff !important;
            border: none;
            border-radius: 0.5rem;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .clear-btn:hover {
            background: #475569 !important;
        }
        
        .body-section {
            margin-top: 1rem;
        }
        
        .body-textarea {
            width: 100%;
            height: 160px;
            padding: 1rem;
            border: 2px solid #4a5568 !important;
            border-radius: 0.5rem;
            font-family: 'Courier New', monospace;
            font-size: 0.875rem;
            background: #2d3748 !important;
            color: #e2e8f0 !important;
            resize: vertical;
        }
        
        .body-textarea:focus {
            outline: none;
            border-color: #3b82f6 !important;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        
        .response-container {
            background: #16213e !important;
            border-radius: 0.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.3);
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border: 1px solid #2d3748;
        }
        
        .response-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 1rem;
        }
        
        .response-header h3 {
            font-size: 1.125rem;
            font-weight: 600;
            color: #e2e8f0 !important;
            margin: 0;
        }
        
        .status-badge {
            padding: 0.25rem 1rem;
            border-radius: 9999px;
            font-size: 0.875rem;
            font-weight: 600;
        }
        
        .status-badge.success {
            color: #6ee7b7 !important;
            background: #064e3b !important;
            border: 1px solid #059669;
        }
        
        .status-badge.error {
            color: #fca5a5 !important;
            background: #7f1d1d !important;
            border: 1px solid #dc2626;
        }
        
        .status-badge.auth {
            color: #fcd34d !important;
            background: #422006 !important;
            border: 1px solid #ca8a04;
        }
        
        .response-content {
            background: #0f172a !important;
            color: #cbd5e1 !important;
            padding: 1rem;
            border-radius: 0.5rem;
            overflow-x: auto;
            font-family: 'Courier New', monospace;
            font-size: 0.875rem;
            max-height: 400px;
            overflow-y: auto;
            white-space: pre-wrap;
            border: 1px solid #1e293b;
        }
        
        .tips-section {
            background: #1e3a8a !important;
            border: 1px solid #2563eb;
            border-radius: 0.5rem;
            padding: 1rem;
            margin-top: 1.5rem;
        }
<!-- Second API Tester removed -->

<script>
        const methodSelect = document.getElementById('method');
        const urlInput = document.getElementById('url');
        const requestBodyTextarea = document.getElementById('requestBody');
        const bodySection = document.getElementById('bodySection');
        const sendBtn = document.getElementById('sendBtn');
        const btnText = document.getElementById('btnText');
        const responseContent = document.getElementById('responseContent');
        const statusBadge = document.getElementById('statusBadge');
        const headersSection = document.getElementById('headersSection');
        const headersContent = document.getElementById('headersContent');

        function getCookie(name) {
            const value = `; ${document.cookie}`;
            const parts = value.split(`; ${name}=`);
            if (parts.length === 2) return parts.pop().split(';').shift();
            return null;
        }

        function checkAuthentication() {
            let jwtCookie = getCookie('jwt_python_flask');
            
            console.log('All cookies:', document.cookie);
            console.log('Looking for jwt_python_flask:', jwtCookie);
            
            if (!jwtCookie || jwtCookie.trim() === '') {
                methodSelect.disabled = true;
                urlInput.disabled = true;
                requestBodyTextarea.disabled = true;
                sendBtn.disabled = true;
                
                responseContent.innerHTML = `<div style="color: #fbbf24; font-weight: bold; font-size: 1.2rem; text-align: center; padding: 2rem;">
                    🔒 Authentication Required
                    
                    <div style="color: #cbd5e1; font-size: 0.9rem; margin-top: 1rem; font-weight: normal;">
                        You must be logged in to use the API tester.
                        
                        Please log in to your account first, then refresh this page.
                    </div>
                </div>`;
                
                const exampleButtons = document.querySelectorAll('.example-btn');
                exampleButtons.forEach(btn => {
                    btn.disabled = true;
                    btn.style.opacity = '0.5';
                    btn.style.cursor = 'not-allowed';
                });
                
                return false;
            }
            return true;
        }

        const isAuthenticated = checkAuthentication();

        methodSelect.addEventListener('change', function() {
            if (!isAuthenticated) return;
            
            const method = this.value;
            sendBtn.className = `send-btn ${method}`;
            
            if (method === 'POST' || method === 'PUT') {
                bodySection.style.display = 'block';
            } else {
                bodySection.style.display = 'none';
            }
        });





<!-- Second API Tester removed -->

---

<div class="section-card">
<h2 class="section-title">📝 Knowledge Check Quiz</h2>
<p style="margin-bottom: 1.5rem;">Test your understanding of APIs with this interactive quiz!</p>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .quiz-container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .quiz-header {
            text-align: center;
            margin-bottom: 30px;
            padding: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border-radius: 10px;
        }
        
        .quiz-header h2 {
            color: white !important;
            margin-bottom: 10px;
        }
        
        .quiz-subtitle {
            color: rgba(255, 255, 255, 0.9);
            font-size: 1.1rem;
        }
        
        .question-card {
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            padding: 25px;
            margin-bottom: 25px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            border: 2px solid #e2e8f0;
        }
        
        .question-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }
        
        .question {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 15px;
            color: #2c3e50;
        }
        
        .answer-input {
            display: inline-block;
            width: 250px;
            height: 40px;
            border: 2px solid #667eea;
            border-radius: 5px;
            margin: 0 5px;
            padding: 0 10px;
            vertical-align: middle;
            background-color: #f8fafc;
            font-size: 1rem;
            transition: all 0.3s ease;
        }
        
        .answer-input:focus {
            outline: none;
            border-color: #764ba2;
            background-color: #fff;
            box-shadow: 0 0 5px rgba(102, 126, 234, 0.5);
        }
        
        .answer-input.correct {
            border-color: #10b981;
            background-color: #d1fae5;
        }
        
        .answer-input.incorrect {
            border-color: #ef4444;
            background-color: #fee2e2;
        }
        
        .button-group {
            margin-top: 15px;
        }
        
        .answer-btn {
            background-color: #667eea;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: background-color 0.3s ease;
            margin-right: 10px;
            margin-bottom: 10px;
        }
        
        .answer-btn:hover {
            background-color: #764ba2;
        }
        
        .check-btn {
            background-color: #10b981;
        }
        
        .check-btn:hover {
            background-color: #059669;
        }
        
        .show-btn {
            background-color: #8b5cf6;
        }
        
        .show-btn:hover {
            background-color: #7c3aed;
        }
        
        .reset-btn {
            background-color: #ef4444;
        }
        
        .reset-btn:hover {
            background-color: #dc2626;
        }
        
        .feedback {
            margin-top: 15px;
            padding: 12px;
            background-color: #f8f9fa;
            border-left: 4px solid #667eea;
            border-radius: 0 5px 5px 0;
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .feedback.correct {
            border-left-color: #10b981;
            background-color: #d1fae5;
            color: #065f46;
        }
        
        .feedback.incorrect {
            border-left-color: #ef4444;
            background-color: #fee2e2;
            color: #991b1b;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .score-container {
            text-align: center;
            margin-top: 30px;
            padding: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .score {
            font-size: 1.8rem;
            font-weight: bold;
            color: white;
        }
        
        @media (max-width: 600px) {
            .quiz-container {
                padding: 10px;
            }
            
            .question-card {
                padding: 15px;
            }
            
            .answer-input {
                width: 100%;
                margin: 5px 0;
            }
            
            .button-group {
                text-align: center;
            }
            
            .answer-btn {
                width: 100%;
                margin: 5px 0;
            }
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <div class="quiz-header">
            <h2>API Learning Quiz</h2>
            <p class="quiz-subtitle">Type your answers in the boxes and check them with the buttons</p>
        </div>
        
        <div class="question-card">
            <div class="question">Q: What is an API?</div>
            <p>A: It's <input type="text" class="answer-input" id="input1" placeholder="Type your answer here...">. Like how your Instagram app talks to Instagram's servers.</p>
            <div class="button-group">
                <button class="answer-btn check-btn" onclick="checkAnswer(1)">Check Answer</button>
                <button class="answer-btn show-btn" onclick="showAnswer(1)">Show Answer</button>
                <button class="answer-btn reset-btn" onclick="resetAnswer(1)">Reset</button>
            </div>
            <div class="feedback" id="feedback1"></div>
        </div>
        
        <div class="question-card">
            <div class="question">Q: What does this backend do?</div>
            <p>A: It <input type="text" class="answer-input" id="input2" placeholder="Type your answer here...">, and lets you get or add data through specific URLs.</p>
            <div class="button-group">
                <button class="answer-btn check-btn" onclick="checkAnswer(2)">Check Answer</button>
                <button class="answer-btn show-btn" onclick="showAnswer(2)">Show Answer</button>
                <button class="answer-btn reset-btn" onclick="resetAnswer(2)">Reset</button>
            </div>
            <div class="feedback" id="feedback2"></div>
        </div>
        
        <div class="question-card">
            <div class="question">Q: How do you test it?</div>
            <p>A: <input type="text" class="answer-input" id="input3" placeholder="Type your answer here..."> and try different endpoints.</p>
            <div class="button-group">
                <button class="answer-btn check-btn" onclick="checkAnswer(3)">Check Answer</button>
                <button class="answer-btn show-btn" onclick="showAnswer(3)">Show Answer</button>
                <button class="answer-btn reset-btn" onclick="resetAnswer(3)">Reset</button>
            </div>
            <div class="feedback" id="feedback3"></div>
        </div>
        
        <div class="question-card">
            <div class="question">Q: What technology is it built with?</div>
            <p>A: <input type="text" class="answer-input" id="input4" placeholder="Type your answer here...">, plus a database to store information.</p>
            <div class="button-group">
                <button class="answer-btn check-btn" onclick="checkAnswer(4)">Check Answer</button>
                <button class="answer-btn show-btn" onclick="showAnswer(4)">Show Answer</button>
                <button class="answer-btn reset-btn" onclick="resetAnswer(4)">Reset</button>
            </div>
            <div class="feedback" id="feedback4"></div>
        </div>
        
        <div class="question-card">
            <div class="question">Q: Can you explain how it works?</div>
            <p>A: When you visit a URL like <input type="text" class="answer-input" id="input5" placeholder="Type your answer here...">, the server looks at its database and sends back the user information as data.</p>
            <div class="button-group">
                <button class="answer-btn check-btn" onclick="checkAnswer(5)">Check Answer</button>
                <button class="answer-btn show-btn" onclick="showAnswer(5)">Show Answer</button>
                <button class="answer-btn reset-btn" onclick="resetAnswer(5)">Reset</button>
            </div>
            <div class="feedback" id="feedback5"></div>
        </div>
        
        <div class="score-container">
            <div class="score">Score: <span id="score">0</span>/5</div>
            <button class="answer-btn" onclick="resetAll()" style="margin-top: 10px; background-color: rgba(255,255,255,0.2);">Reset All Answers</button>
        </div>
    </div>

    <script>
        const correctAnswers = {
            1: "a way for programs to talk to each other",
            2: "stores users and posts",
            3: "Go to /docs in the browser",
            4: "Python and Flask (a web framework)",
            5: "/api/users"
        };
        
        const fullAnswers = {
            1: "It's a way for programs to talk to each other. Like how your Instagram app talks to Instagram's servers.",
            2: "It stores users and posts, and lets you get or add data through specific URLs.",
            3: "Go to /docs in the browser and try different endpoints.",
            4: "Python and Flask (a web framework), plus a database to store information.",
            5: "When you visit a URL like /api/users, the server looks at its database and sends back the user information as data."
        };
        
        let score = 0;
        const answeredQuestions = new Set();
        
        function checkAnswer(questionNum) {
            const input = document.getElementById(`input${questionNum}`);
            const feedback = document.getElementById(`feedback${questionNum}`);
            const userAnswer = input.value.trim().toLowerCase();
            const correctAnswer = correctAnswers[questionNum].toLowerCase();
            
            input.classList.remove("correct", "incorrect");
            feedback.classList.remove("correct", "incorrect");
            
            if (userAnswer === correctAnswer) {
                input.classList.add("correct");
                feedback.classList.add("correct");
                feedback.innerHTML = `<strong>✅ Correct!</strong> ${fullAnswers[questionNum]}`;
                feedback.style.display = "block";
                
                if (!answeredQuestions.has(questionNum)) {
                    answeredQuestions.add(questionNum);
                    score++;
                    updateScore();
                }
            } else {
                input.classList.add("incorrect");
                feedback.classList.add("incorrect");
                feedback.innerHTML = `<strong>❌ Incorrect.</strong> Try again or click "Show Answer" to see the correct answer.`;
                feedback.style.display = "block";
            }
        }
        
        function showAnswer(questionNum) {
            const input = document.getElementById(`input${questionNum}`);
            const feedback = document.getElementById(`feedback${questionNum}`);
            
            input.value = correctAnswers[questionNum];
            input.classList.remove("incorrect");
            input.classList.add("correct");
            feedback.classList.remove("incorrect");
            feedback.classList.add("correct");
            feedback.innerHTML = `<strong>💡 Answer:</strong> ${fullAnswers[questionNum]}`;
            feedback.style.display = "block";
            
            if (!answeredQuestions.has(questionNum)) {
                answeredQuestions.add(questionNum);
                score++;
                updateScore();
            }
        }
        
        function resetAnswer(questionNum) {
            const input = document.getElementById(`input${questionNum}`);
            const feedback = document.getElementById(`feedback${questionNum}`);
            
            input.value = "";
            input.classList.remove("correct", "incorrect");
            feedback.classList.remove("correct", "incorrect");
            feedback.style.display = "none";
            
            if (answeredQuestions.has(questionNum)) {
                answeredQuestions.delete(questionNum);
                score--;
                updateScore();
            }
        }
        
        function resetAll() {
            for (let i = 1; i <= 5; i++) {
                resetAnswer(i);
            }
        }
        
        function updateScore() {
            document.getElementById("score").textContent = score;
        }
        
        document.addEventListener('DOMContentLoaded', function() {
            for (let i = 1; i <= 5; i++) {
                const input = document.getElementById(`input${i}`);
                input.addEventListener('keypress', function(event) {
                    if (event.key === 'Enter') {
                        checkAnswer(i);
                    }
                });
            }
        });
    </script>
</body>
</html>

</div>

---

<div class="section-card">
<h2 class="section-title">🎉 Random Joke</h2>

<div id="jokeoutput" style="padding: 1.5rem; background: #fef3c7; border-radius: 8px; border-left: 4px solid #f59e0b; color: #92400e; font-size: 1.1rem;">
Joke Loading...
</div>

<script type="module">
import { pythonURI, fetchOptions } from '{{site.baseurl}}/assets/js/api/config.js';
const output = document.getElementById('jokeoutput');

async function tryFetchJoke() {
    try {
        const response = await fetch(`${pythonURI}/api/jokes/random`, fetchOptions);
        if (!response.ok) throw new Error(`HTTP error! Status: ${response.status}`);
        const data = await response.json();
        output.innerHTML = `😄 ${data.joke}`;
    } catch (error) {
        output.innerHTML = `😅 Couldn't fetch a joke right now. Try refreshing!`;
        console.error('Error fetching data:', error);
    }
}

tryFetchJoke();
</script>

</div>