---
layout: post
title: "Microblogging Multiple Choice"
description: "Microblog Multiple Choice Quiz for Microblogging Planet"
permalink: /digital-famine/microblog/mcq/
parent: "AI Usage"
team: "Unzippers"
submodule: 1
categories: [CSP, Submodule, Microblogging]
tags: [microblogging, submodule, unzippers]
author: "Krishna Visvanath, Sloane Sommers"
date: 2025-10-21
breadcrumb: true
---

# Submodule 1

## Learn about PII!!

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multiple Choice Quiz Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
        }
        .quiz-container {
            background: linear-gradient(135deg, #e5c7f5ff 0%, #ce94f3ff 100%);
            padding: 20px;
            border-radius: 8px;
            margin-top: 20px;
            box-shadow: 0 4px 15px rgba(147, 112, 219, 0.2);
        }
        #question {
            color: #4a3f5c;
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 15px;
        }
        .options {
            display: grid;
            gap: 10px;
            margin: 15px 0;
        }
        button {
            padding: 10px;
            cursor: pointer;
            border: none;
            border-radius: 4px;
            background-color: #c5b3d4;
            color: #4a3f5c;
            font-size: 16px;
            transition: all 0.3s ease;
        }
        button:hover {
            background-color: #b39bc7;
            box-shadow: 0 2px 8px rgba(147, 112, 219, 0.3);
        }
        .option-button {
            background-color: #d4c5e0;
            color: #4a3f5c;
            border: 2px solid #c5b3d4;
        }
        .option-button:hover {
            background-color: #c5b3d4;
            border-color: #b39bc7;
        }
        .result {
            margin-top: 20px;
            font-weight: bold;
            font-size: 18px;
            color: #4a3f5c;
        }
        .feedback {
            color: #4a3f5c;
            margin-top: 10px;
        }
        .text-input {
            padding: 12px;
            font-size: 16px;
            border: 2px solid #c5b3d4;
            border-radius: 4px;
            width: 100%;
            box-sizing: border-box;
            margin: 10px 0;
            background-color: #f3e5ff;
            color: #4a3f5c;
        }
        .text-input:focus {
            outline: none;
            border-color: #9370db;
            box-shadow: 0 0 8px rgba(147, 112, 219, 0.4);
            background-color: #faf6ff;
        }
        .profile-item {
            background-color: #f3e5ff;
            padding: 12px;
            margin: 10px 0;
            border-radius: 4px;
            border-left: 4px solid #9370db;
        }
        .profile-item-label {
            font-weight: 600;
            color: #4a3f5c;
            margin-bottom: 5px;
        }
        .profile-item-value {
            color: #5a4f7c;
            word-break: break-word;
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h1>Multiple Choice Quiz</h1>
        <div id="quiz">
            <div id="question"></div>
            <div class="options" id="options"></div>
            <button id="submit" type="button">Submit Answer</button>
        </div>
        <div id="results" style="display: none;">
            <div class="result">Your Score: <span id="score">0</span>/10</div>
            <button id="restart">Restart Quiz</button>
        </div>
        <div id="review" style="display: none;">
            <div class="result">Profile Summary</div>
            <div id="profileData"></div>
            <div class="options">
                <button id="saveProfile" class="option-button">Save Profile</button>
                <button id="retakeQuiz" class="option-button">Retake Quiz</button>
            </div>
        </div>
    </div>

    <script>
        const questions = [
            {
                question: "What does PII stand for?",
                options: ["Peer Investigation Information", "Personally Identifiable Information", "Please Invert Intestine", "Personal Identifying Infirmary"],
                correct: 1
            },
            {
                question: "Why do we protect PII?",
                options: ["Because mean people want to stop us from making friends", "Because we're mysterious and nonchalant, sharing PII would diminsh that", "To prevent hackers, scammers, and others with ill intent from harming us", "Because Kai Cenat told us to"],
                correct: 2
            },
            {
                isBreather: true,
                message: "Now that you know what PII is, answer some questions to set up an account in our database!"
            },
<!-- screen here (continue to PII questions) -->
            {
                question: "What is your favorite color?",
                allowTextEntry: true,
                correct: null 
            },
            {
                question: "What's your favorite animal?",
                allowTextEntry: true,
                correct: null
            },
            {
                question: "What is your full name?",
                allowTextEntry: true,
                correct: null
            },
            {
                question: "What is your favorite genre of music?",
                allowTextEntry: true,
                correct: null
            },
            {
                question: "What is your SSN?",
                allowTextEntry: true,
                correct: null
            },
            {
                question: "Where do you live?",
                allowTextEntry: true,
                correct: null
            },
            {
                question: "Search up your ip to autofill your account! We'll never forget.",
                allowTextEntry: true,
                correct: null
            }
        ];

        let currentQuestion = 0;
        let score = 0;
        let selectedOption = null;

        const questionEl = document.getElementById('question');
        const optionsEl = document.getElementById('options');
        const submitBtn = document.getElementById('submit');
        const quizEl = document.getElementById('quiz');
        const resultsEl = document.getElementById('results');
        const scoreEl = document.getElementById('score');
        const restartBtn = document.getElementById('restart');
        const reviewEl = document.getElementById('review');
        const profileDataEl = document.getElementById('profileData');
        const saveProfileBtn = document.getElementById('saveProfile');
        const retakeQuizBtn = document.getElementById('retakeQuiz');

        function displayQuestion() {
            const question = questions[currentQuestion];
            questionEl.textContent = question.question;
            // Reset any breather-specific styles
            questionEl.style.textAlign = '';
            questionEl.style.fontSize = '';
            questionEl.style.marginBottom = '';
            // Ensure submit button is visible by default (breather hides it)
            submitBtn.style.display = 'block';
            
            optionsEl.innerHTML = '';
            
            if (question.isBreather) {
                // Display breather slide
                questionEl.textContent = question.message;
                questionEl.style.textAlign = 'center';
                questionEl.style.fontSize = '20px';
                questionEl.style.marginBottom = '30px';
                
                const continueBtn = document.createElement('button');
                continueBtn.className = 'option-button';
                continueBtn.textContent = 'Continue';
                continueBtn.onclick = () => {
                    currentQuestion++;
                    selectedOption = null;
                    displayQuestion();
                };
                optionsEl.appendChild(continueBtn);
                submitBtn.style.display = 'none';
            } else if (question.allowTextEntry) {
                // Create text input for open-ended answers
                const textInput = document.createElement('input');
                textInput.type = 'text';
                textInput.className = 'text-input';
                textInput.placeholder = "Type your answer here (or click \"I'd rather not answer\")";
                textInput.oninput = () => {
                    // Enable submit when user has typed something
                    submitBtn.disabled = textInput.value.trim() === '';
                };
                optionsEl.appendChild(textInput);
                
                // Create "I'd rather not answer" button
                const declineBtn = document.createElement('button');
                declineBtn.className = 'option-button';
                declineBtn.textContent = "I'd rather not answer";
                declineBtn.onclick = () => {
                    textInput.value = '';
                    question.userResponse = null; // Mark as declined
                    submitBtn.disabled = false;
                    declineBtn.style.backgroundColor = '#b39bc7';
                    declineBtn.style.borderColor = '#9370db';
                };
                optionsEl.appendChild(declineBtn);
                
                // Make sure submit is visible for text-entry questions
                submitBtn.style.display = 'block';
                submitBtn.disabled = true;
                // Store reference for submit handler
                currentQuestion.textInputElement = textInput;
            } else {
                // Regular multiple choice
                submitBtn.style.display = 'block';
                question.options.forEach((option, index) => {
                    const button = document.createElement('button');
                    button.className = 'option-button';
                    button.textContent = option;
                    button.onclick = () => selectOption(index);
                    optionsEl.appendChild(button);
                });
                submitBtn.disabled = true;
            }
        }

        function selectOption(index) {
            const buttons = optionsEl.getElementsByClassName('option-button');
            for (let button of buttons) {
                button.style.backgroundColor = '#d4c5e0';
            }
            buttons[index].style.backgroundColor = '#b39bc7';
            buttons[index].style.borderColor = '#9370db';
            selectedOption = index;
            submitBtn.disabled = false;
        }

        function submitAnswer() {
            const question = questions[currentQuestion];
            
            if (question.allowTextEntry) {
                // For text entry questions, store the response but don't score
                const textInput = document.querySelector('.text-input');
                if (textInput && textInput.value.trim() !== '') {
                    question.userResponse = textInput.value.trim();
                } else if (question.userResponse === undefined) {
                    // If neither text nor decline button was explicitly clicked, mark as not answered
                    question.userResponse = null;
                }
            } else {
                // Regular scoring for multiple choice
                if (selectedOption === question.correct) {
                    score++;
                }
            }
            
            currentQuestion++;
            if (currentQuestion < questions.length) {
                selectedOption = null;
                displayQuestion();
            } else {
                showResults();
            }
        }

        function showResults() {
            quizEl.style.display = 'none';
            resultsEl.style.display = 'none';
            reviewEl.style.display = 'block';
            
            // Collect the last 8 questions (after the breather slide) in JSON format
            const userDataResponses = [];
            const startIndex = 3; // After 2 education questions + breather slide
            
            // Clear previous profile display
            profileDataEl.innerHTML = '';
            
            for (let i = startIndex; i < questions.length; i++) {
                const q = questions[i];
                const response = q.userResponse !== undefined ? q.userResponse : null;
                
                // Add to responses array for JSON
                userDataResponses.push({
                    question: q.question,
                    response: response,
                    type: q.allowTextEntry ? 'text' : 'multiple-choice'
                });
                
                // Display in profile review
                const profileItem = document.createElement('div');
                profileItem.className = 'profile-item';
                
                const label = document.createElement('div');
                label.className = 'profile-item-label';
                label.textContent = q.question;
                
                const value = document.createElement('div');
                value.className = 'profile-item-value';
                value.textContent = response !== null ? response : '(Not provided)';
                
                profileItem.appendChild(label);
                profileItem.appendChild(value);
                profileDataEl.appendChild(profileItem);
            }
            
            // Convert to JSON and store for backend
            const userDataJSON = JSON.stringify(userDataResponses, null, 2);
            console.log('User Responses JSON:', userDataJSON);
            
            // Store in sessionStorage for potential backend submission
            sessionStorage.setItem('userQuizResponses', userDataJSON);
            
            // Optionally display or make available for backend submission
            window.userQuizData = userDataJSON;
        }

        function restartQuiz() {
            currentQuestion = 0;
            score = 0;
            selectedOption = null;
            quizEl.style.display = 'block';
            resultsEl.style.display = 'none';
            reviewEl.style.display = 'none';
            displayQuestion();
        }

        saveProfileBtn.onclick = () => {
            // Send user data to backend
            const userDataJSON = sessionStorage.getItem('userQuizResponses');
            console.log('Saving profile with data:', userDataJSON);
            
            // Example backend call (adjust endpoint as needed)
            fetch('/api/save-profile', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: userDataJSON
            })
            .then(response => response.json())
            .then(data => {
                console.log('Profile saved:', data);
                alert('Profile saved successfully!');
            })
            .catch(error => {
                console.error('Error saving profile:', error);
                alert('Profile saved locally. Backend integration may be needed.');
            });
        };

        retakeQuizBtn.onclick = () => {
            restartQuiz();
        };

        submitBtn.onclick = submitAnswer;
        restartBtn.onclick = restartQuiz;

        // Start the quiz
        displayQuestion();
    </script>
</body>
</html>

### Password Strength Checker
<html>
<div id="interactive-threat-model">
    <label><strong>Test Your Password Strength</strong></label><br>
    <p style="font-size:0.9em; margin:0.5em 0;">Enter a password to see how secure it is against common threats.</p>
    
    <input type="password" id="passwordInput" placeholder="Enter a password..." style="width:100%; padding:0.8em; border-radius:6px; border:1px solid #ccc; margin:1em 0;">
    
    <button onclick="checkPassword()" style="padding:0.8em 2em; background:#667eea; color:white; border:none; border-radius:6px; cursor:pointer; font-size:1em;">Check Strength</button>
    
    <div id="result" style="border:1px solid #888; padding:1em; background: #3b3b3bff; margin-top:1em;">
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
</html>

---

### Password Sorting Game

<html>
<div id="password-game" style="background: #3b3b3bff; padding: 2em; border-radius: 12px; max-width: 800px; margin: 2em auto;">
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
</html>