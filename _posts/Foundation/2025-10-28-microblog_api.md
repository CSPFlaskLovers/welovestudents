---
layout: post
title: Microblog API
permalink: /digital-famine/microblog/api/
author: Cyrus, William W
breadcrumb: true
---

# Microblog API - Beginner's Guide

> **A simple social media backend built with Python - perfect for learning**

---

## What's Inside This Guide

- [What is This?](#-what-is-this)
- [Why Should I Care?](#-why-should-i-care)
- [What Do I Need?](#-what-do-i-need)
- [How to Run It](#-how-to-run-it)
- [What Can I Learn?](#-what-can-i-learn)
- [Easy Starter Activities](#-easy-starter-activities)

---

## What is This?

**Microblog API** is like a mini-Twitter backend. It's the server part of a social media app where:

- Users can sign up and log in
- Users can write posts
- Users can read other people's posts

**BUT** - this is just the backend. There's no pretty website or app interface. It's the "behind the scenes" code that makes everything work.

Think of it like this:
```
Instagram App (Frontend) ←→ Instagram's Servers (Backend like this!)
```

---

## Why Should I Care?

This project is great for **AP Computer Science Principles** because:

| Reason | Why It Matters |
|--------|----------------|
| **Covers AP CSP concepts** | Networks, data, the internet, and how apps work |
| **Uses Python** | You might already know some Python! |
| **See it work** | Not just theory - you can actually run it and test it |
| **Real-world example** | This is how actual apps like Instagram work |

**You don't need to understand all the code!** The goal is to:
- See how a backend works
- Try using an API
- Understand the basics of how data moves around

---

## What Do I Need?

### Option A: The Easy Way (Using Docker)
- A computer with **Docker Desktop** installed
- That's it!

### Option B: The Python Way
- Python 3 installed on your computer
- Basic command line knowledge (just copying and pasting commands)

**Don't worry if you don't know Docker or Python well yet!** The instructions below are step-by-step.

---

## How to Run It

### Easy Way: Docker (Recommended)

Think of Docker like a pre-made package that has everything ready to go.

#### Step 1: Get the code
Open your terminal and type:
```bash
git clone https://github.com/miguelgrinberg/microblog-api
cd microblog-api
```

#### Step 2: Set up the settings file
```bash
cp .env.example .env
```
*(This just copies a template file - you can skip editing it for now)*

#### Step 3: Start it up!
```bash
docker-compose up -d
```

Wait a minute for it to start...

#### Step 4: Check if it's working
Open your web browser and go to:
```
http://localhost:5000/docs
```

You should see a page with API documentation!

#### Step 5: Add some fake data to play with
```bash
docker-compose run --rm microblog-api bash -c "flask fake users 10 && flask fake posts 100"
```

Now you have 10 fake users and 100 fake posts to test with!

#### To stop it later:
```bash
docker-compose down
```

---

### Python Way (If Docker doesn't work)

#### Step 1: Get the code
```bash
git clone https://github.com/miguelgrinberg/microblog-api
cd microblog-api
```

#### Step 2: Set up Python environment
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

#### Step 3: Set up the database
```bash
alembic upgrade head
flask fake users 10
flask fake posts 100
```

#### Step 4: Run it!
```bash
flask run
```

#### Step 5: Check it out
Open your browser to:
```
http://localhost:5000/docs
```

---

## Common Problem

**If you see an error about port 5000:**

On newer Macs, Apple uses port 5000 for something else. 

Quick fix - use a different port:
```bash
flask run --port=4000
```

Then visit `http://localhost:4000/docs` instead.

---

## What Can I Learn?

### For AP CSP, this project shows:

#### **The Internet**
- How do apps send and receive data?
- What is an API? (Answer: A way for programs to talk to each other!)

#### **Data**
- How is user information stored?
- What is a database?

#### **Security**
- How do apps know who you are?
- What is authentication?

#### **Abstraction**
- How complex systems are broken into smaller pieces
- Why we organize code into files and folders

---

## Easy Starter Activities

### Activity 1: Explore the API (5 minutes)
1. Go to `http://localhost:5000/docs`
2. Look at the list of endpoints (the different things the API can do)
3. Find the "GET /api/users" endpoint
4. Click "Try it out" and then "Execute"
5. See the list of fake users!

**What you learned:** How to send a request to an API and get data back

---

### Activity 2: Create a User (10 minutes)
1. Find the "POST /api/users" endpoint
2. Click "Try it out"
3. Fill in the example data (make up a username and email)
4. Click "Execute"
5. You just created a user!

**What you learned:** How apps send data to servers

---

### Activity 3: See the Posts (5 minutes)
1. Find "GET /api/posts"
2. Try it out
3. See all the fake posts that were created

**What you learned:** How social media apps get posts to show you

---

<!-- Begin embedded HTML from notebook -->

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>API Learning - Interactive Fill-in-the-Blanks</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-attachment: fixed;
            color: #333;
            line-height: 1.6;
            padding: 20px;
            min-height: 100vh;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            margin-bottom: 40px;
            padding: 20px;
            background: white;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            color: #2c3e50;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: #7f8c8d;
            font-size: 1.1rem;
        }
        
        .question-card {
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            padding: 25px;
            margin-bottom: 25px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
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
            border: 2px solid #3498db;
            border-radius: 5px;
            margin: 0 5px;
            padding: 0 10px;
            vertical-align: middle;
            background-color: #e8f4fc;
            font-size: 1rem;
            transition: all 0.3s ease;
        }
        
        .answer-input:focus {
            outline: none;
            border-color: #2980b9;
            background-color: #d6eaf8;
            box-shadow: 0 0 5px rgba(52, 152, 219, 0.5);
        }
        
        .answer-input.correct {
            border-color: #27ae60;
            background-color: #d5f4e6;
        }
        
        .answer-input.incorrect {
            border-color: #e74c3c;
            background-color: #fadbd8;
        }
        
        .button-group {
            margin-top: 15px;
        }
        
        .answer-btn {
            background-color: #3498db;
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
            background-color: #2980b9;
        }
        
        .check-btn {
            background-color: #2ecc71;
        }
        
        .check-btn:hover {
            background-color: #27ae60;
        }
        
        .show-btn {
            background-color: #9b59b6;
        }
        
        .show-btn:hover {
            background-color: #8e44ad;
        }
        
        .reset-btn {
            background-color: #e74c3c;
        }
        
        .reset-btn:hover {
            background-color: #c0392b;
        }
        
        .feedback {
            margin-top: 15px;
            padding: 12px;
            background-color: #f8f9fa;
            border-left: 4px solid #3498db;
            border-radius: 0 5px 5px 0;
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .feedback.correct {
            border-left-color: #27ae60;
            background-color: #d5f4e6;
        }
        
        .feedback.incorrect {
            border-left-color: #e74c3c;
            background-color: #fadbd8;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .score-container {
            text-align: center;
            margin-top: 30px;
            padding: 15px;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .score {
            font-size: 1.5rem;
            font-weight: bold;
            color: #2c3e50;
        }
        
        .footer {
            text-align: center;
            margin-top: 40px;
            color: #7f8c8d;
            font-size: 0.9rem;
        }
        
        @media (max-width: 600px) {
            .container {
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
    <div class="container">
        <header>
            <h1>API Learning - Interactive Fill-in-the-Blanks</h1>
            <p class="subtitle">Type your answers in the colored boxes and check them with the buttons</p>
        </header>
        
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
            <button class="answer-btn" onclick="resetAll()" style="margin-top: 10px;">Reset All Answers</button>
        </div>
        
        <div class="footer">
            <p>API Learning Exercise - Interactive Fill-in-the-Blanks Quiz</p>
        </div>
    </div>

    <script>
        // Define correct answers
        const correctAnswers = {
            1: "a way for programs to talk to each other",
            2: "stores users and posts",
            3: "Go to /docs in the browser",
            4: "Python and Flask (a web framework)",
            5: "/api/users"
        };
        
        // Define full answers for display
        const fullAnswers = {
            1: "It's a way for programs to talk to each other. Like how your Instagram app talks to Instagram's servers.",
            2: "It stores users and posts, and lets you get or add data through specific URLs.",
            3: "Go to /docs in the browser and try different endpoints.",
            4: "Python and Flask (a web framework), plus a database to store information.",
            5: "When you visit a URL like /api/users, the server looks at its database and sends back the user information as data."
        };
        
        let score = 0;
        const answeredQuestions = new Set();
        
        // Function to check answer
        function checkAnswer(questionNum) {
            const input = document.getElementById(`input${questionNum}`);
            const feedback = document.getElementById(`feedback${questionNum}`);
            const userAnswer = input.value.trim().toLowerCase();
            const correctAnswer = correctAnswers[questionNum].toLowerCase();
            
            // Clear previous styling
            input.classList.remove("correct", "incorrect");
            feedback.classList.remove("correct", "incorrect");
            
            if (userAnswer === correctAnswer) {
                // Correct answer
                input.classList.add("correct");
                feedback.classList.add("correct");
                feedback.innerHTML = `<strong>Correct!</strong> ${fullAnswers[questionNum]}`;
                feedback.style.display = "block";
                
                // Update score if not already counted
                if (!answeredQuestions.has(questionNum)) {
                    answeredQuestions.add(questionNum);
                    score++;
                    updateScore();
                }
            } else {
                // Incorrect answer
                input.classList.add("incorrect");
                feedback.classList.add("incorrect");
                feedback.innerHTML = `<strong>Incorrect.</strong> Try again or click "Show Answer" to see the correct answer.`;
                feedback.style.display = "block";
            }
        }
        
        // Function to show answer
        function showAnswer(questionNum) {
            const input = document.getElementById(`input${questionNum}`);
            const feedback = document.getElementById(`feedback${questionNum}`);
            
            input.value = correctAnswers[questionNum];
            input.classList.remove("incorrect");
            input.classList.add("correct");
            feedback.classList.remove("incorrect");
            feedback.classList.add("correct");
            feedback.innerHTML = `<strong>Answer:</strong> ${fullAnswers[questionNum]}`;
            feedback.style.display = "block";
            
            // Update score if not already counted
            if (!answeredQuestions.has(questionNum)) {
                answeredQuestions.add(questionNum);
                score++;
                updateScore();
            }
        }
        
        // Function to reset a single answer
        function resetAnswer(questionNum) {
            const input = document.getElementById(`input${questionNum}`);
            const feedback = document.getElementById(`feedback${questionNum}`);
            
            input.value = "";
            input.classList.remove("correct", "incorrect");
            feedback.classList.remove("correct", "incorrect");
            feedback.style.display = "none";
            
            // Remove from score if previously counted
            if (answeredQuestions.has(questionNum)) {
                answeredQuestions.delete(questionNum);
                score--;
                updateScore();
            }
        }
        
        // Function to reset all answers
        function resetAll() {
            for (let i = 1; i <= 5; i++) {
                resetAnswer(i);
            }
        }
        
        // Function to update score display
        function updateScore() {
            document.getElementById("score").textContent = score;
        }
        
        // Add keyboard event listeners for Enter key
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

<!-- End embedded HTML from notebook -->

---

<!-- Code runner removed -->


<div id="jokeoutput"> Joke Loading...</div>

<script type="module">
import { pythonURI, fetchOptions } from '{{site.baseurl}}/assets/js/api/config.js';
console.log(pythonURI);
const output = document.getElementById('jokeoutput');

// Async fetch using try/catch and the shared `fetchOptions` (mirrors exercisegraphs pattern)
async function tryFetchJoke() {
    try {
        const response = await fetch(`${pythonURI}/api/jokes/random`, fetchOptions);
        if (!response.ok) throw new Error(`HTTP error! Status: ${response.status}`);
        const data = await response.json();
        console.log(data);
        output.innerHTML = data.joke;
    } catch (error) {
        console.error('Error fetching data:', error);
    }
}

tryFetchJoke();
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
                    API Tester
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
                <h3>Quick Examples:</h3>
                <div class="examples-buttons">
                    <button class="example-btn get" onclick="loadExample('getUsers')">GET Users</button>
                    <button class="example-btn post" onclick="loadExample('createUser')">POST Create User</button>
                    <button class="example-btn get" onclick="loadExample('getProfile')">GET Profile Data</button>
                    <button class="example-btn post" onclick="loadExample('addProfileData')">POST Add Profile Data</button>
                    <button class="example-btn delete" onclick="loadExample('deleteProfileData')">DELETE Profile Data</button>
                    <button class="example-btn post" onclick="loadExample('setupProfile')">POST Setup Profile</button>
                    <button class="example-btn get" onclick="loadExample('getAllData')">GET All Users Data</button>
                    <button class="example-btn post" onclick="loadExample('saveProfileJSON')">POST Save Profile JSON</button>
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
                        value="http://localhost:8001/api/"
                        placeholder="http://localhost:8001/api/endpoint"
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
                <li>• This tool automatically includes your JWT authentication cookie with each request</li>
                <li>• If you see 401/403 errors, make sure you're logged in to the application first</li>
                <li>• The server must be running on the specified URL (default: http://localhost:8001)</li>
                <li>• Use the quick examples above to test common API endpoints</li>
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

        // Check for JWT cookie on page load
        function getCookie(name) {
            const value = `; ${document.cookie}`;
            const parts = value.split(`; ${name}=`);
            if (parts.length === 2) return parts.pop().split(';').shift();
            return null;
        }

        function checkAuthentication() {
            // Try multiple cookie names just in case
            let jwtCookie = getCookie('jwt_python_flask');
            
            // Debug: log all cookies
            console.log('All cookies:', document.cookie);
            console.log('Looking for jwt_python_flask:', jwtCookie);
            
            // If cookie exists and has content, user is authenticated
            if (!jwtCookie || jwtCookie.trim() === '') {
                // Disable all controls
                methodSelect.disabled = true;
                urlInput.disabled = true;
                requestBodyTextarea.disabled = true;
                sendBtn.disabled = true;
                
                // Show authentication required message
                responseContent.innerHTML = `<div style="color: #fbbf24; font-weight: bold; font-size: 1.2rem; text-align: center; padding: 2rem;">
                    🔒 Authentication Required
                    
                    <div style="color: #cbd5e1; font-size: 0.9rem; margin-top: 1rem; font-weight: normal;">
                        You must be logged in to use the API tester.
                        
                        Please log in to your account first, then refresh this page.
                    </div>
                </div>`;
                
                // Disable example buttons
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

        // Check authentication on page load
        const isAuthenticated = checkAuthentication();

        // Show/hide body section based on method
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
                case 'getUsers':
                    methodSelect.value = 'GET';
                    urlInput.value = 'http://localhost:8001/api/users/';
                    requestBodyTextarea.value = '{\n  \n}';
                    break;
                case 'createUser':
                    methodSelect.value = 'POST';
                    urlInput.value = 'http://localhost:8001/api/user/';
                    requestBodyTextarea.value = '{\n  "name": "Test User",\n  "uid": "testuser",\n  "email": "test@example.com",\n  "password": "password123"\n}';
                    break;
                case 'getProfile':
                    methodSelect.value = 'GET';
                    urlInput.value = 'http://localhost:8001/api/match/data';
                    requestBodyTextarea.value = '{\n  \n}';
                    break;
                case 'addProfileData':
                    methodSelect.value = 'POST';
                    urlInput.value = 'http://localhost:8001/api/match/add';
                    requestBodyTextarea.value = '{\n  "index": "favorite_color",\n  "data": "blue"\n}';
                    break;
                case 'deleteProfileData':
                    methodSelect.value = 'DELETE';
                    urlInput.value = 'http://localhost:8001/api/match/add';
                    requestBodyTextarea.value = '{\n  "index": "favorite_color"\n}';
                    break;
                case 'setupProfile':
                    methodSelect.value = 'POST';
                    urlInput.value = 'http://localhost:8001/api/match/setup';
                    requestBodyTextarea.value = '{\n  \n}';
                    break;
                case 'getAllData':
                    methodSelect.value = 'GET';
                    urlInput.value = 'http://localhost:8001/api/match/all-data';
                    requestBodyTextarea.value = '{\n  \n}';
                    break;
                case 'saveProfileJSON':
                    methodSelect.value = 'POST';
                    urlInput.value = 'http://localhost:8001/api/match/save-profile-json';
                    requestBodyTextarea.value = '{\n  "profile_data": [\n    {\n      "question": "What is your favorite hobby?",\n      "response": "Reading"\n    },\n    {\n      "question": "What is your preferred study time?",\n      "response": "Morning"\n    },\n    {\n      "question": "What type of projects do you enjoy?",\n      "response": "Web development"\n    }\n  ]\n}';
                    break;
            }
            
            // Trigger change event to update UI
            methodSelect.dispatchEvent(new Event('change'));
        }

        async function sendRequest() {
            if (!isAuthenticated) {
                alert('Please log in to use the API tester.');
                return;
            }
            
            // Double-check JWT cookie still exists
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

            // Reset UI
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

                // Add body for POST/PUT
                if (method === 'POST' || method === 'PUT') {
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

                // Update status badge
                statusBadge.textContent = `Status: ${response.status}`;
                statusBadge.style.display = 'inline-block';
                
                if (response.status === 401 || response.status === 403) {
                    statusBadge.className = 'status-badge auth';
                } else if (response.status >= 200 && response.status < 300) {
                    statusBadge.className = 'status-badge success';
                } else {
                    statusBadge.className = 'status-badge error';
                }

                // Get response headers
                const responseHeaders = {};
                response.headers.forEach((value, key) => {
                    responseHeaders[key] = value;
                });
                headersContent.textContent = JSON.stringify(responseHeaders, null, 2);
                headersSection.style.display = 'block';

                // Get response body
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
            
            urlInput.value = 'http://localhost:8001/api/';
            requestBodyTextarea.value = '{\n  \n}';
            responseContent.textContent = 'Response will appear here...';
            statusBadge.style.display = 'none';
            headersSection.style.display = 'none';
        }
    </script>
</body>
</html>