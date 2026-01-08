---
layout: post
title: "Microblogging Multiple Choice"
description: "Microblog Multiple Choice Quiz for Microblogging Planet"
permalink: /digital-matchmaking/matchmaking/mcq/
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

# Learn about PII!

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Security Protocol Training</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Courier New', monospace;
            background: #0d1117;
            color: #8b949e;
            padding: 20px;
            min-height: 100vh;
            position: relative;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                0deg,
                rgba(100, 120, 130, 0.03) 0px,
                transparent 1px,
                transparent 2px,
                rgba(100, 120, 130, 0.03) 3px
            );
            pointer-events: none;
            z-index: 1;
        }

        .mission-header {
            text-align: center;
            padding: 40px 20px;
            background: linear-gradient(135deg, #161b22 0%, #0d1117 100%);
            border-bottom: 1px solid #30363d;
            margin-bottom: 30px;
            position: relative;
            overflow: hidden;
            border-radius: 6px;
            z-index: 2;
        }

        .mission-header::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(100, 120, 130, 0.05), transparent);
            animation: scan 4s infinite;
        }

        @keyframes scan {
            0% { left: -100%; }
            100% { left: 100%; }
        }

        .glitch-text {
            font-size: 2.5em;
            font-weight: 400;
            color: #7d8590;
            text-transform: uppercase;
            letter-spacing: 4px;
            text-shadow: 0 0 10px rgba(125, 133, 144, 0.3);
            margin-bottom: 20px;
            position: relative;
            z-index: 1;
            font-family: 'Courier New', monospace;
        }

        .mission-brief {
            max-width: 800px;
            margin: 15px auto;
            line-height: 1.8;
            color: #6e7681;
            position: relative;
            z-index: 1;
            font-family: 'Courier New', monospace;
        }

        .quiz-container {
            max-width: 800px;
            margin: 0 auto;
            background: rgba(22, 27, 34, 0.85);
            padding: 30px;
            border-radius: 6px;
            border: 1px solid #30363d;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4);
            backdrop-filter: blur(10px);
            position: relative;
            z-index: 2;
        }

        #question {
            color: #8b949e;
            font-size: 1.3em;
            font-weight: 400;
            margin-bottom: 25px;
            text-shadow: 0 0 8px rgba(139, 148, 158, 0.2);
            font-family: 'Courier New', monospace;
        }

        .options {
            display: grid;
            gap: 12px;
            margin: 20px 0;
        }

        button {
            padding: 14px 20px;
            cursor: pointer;
            border: 1px solid #30363d;
            border-radius: 4px;
            background: rgba(48, 54, 61, 0.2);
            color: #8b949e;
            font-size: 16px;
            font-weight: 400;
            transition: all 0.2s ease;
            position: relative;
            overflow: hidden;
            font-family: 'Courier New', monospace;
        }

        button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(100, 120, 130, 0.1), transparent);
            transition: left 0.6s;
        }

        button:hover::before {
            left: 100%;
        }

        button:hover {
            background: rgba(48, 54, 61, 0.4);
            border-color: #485662;
            box-shadow: 0 0 10px rgba(100, 120, 130, 0.2);
        }

        button:disabled {
            opacity: 0.4;
            cursor: not-allowed;
            transform: none;
        }

        button:disabled:hover {
            background: rgba(48, 54, 61, 0.2);
            box-shadow: none;
            border-color: #30363d;
        }

        .option-button {
            text-align: left;
        }

        .option-button.selected {
            background: rgba(72, 86, 98, 0.3);
            border-color: #6e7681;
            box-shadow: 0 0 8px rgba(110, 118, 129, 0.3);
        }

        #submit {
            width: 100%;
            margin-top: 10px;
            background: rgba(48, 54, 61, 0.3);
            font-weight: 400;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        #submit:hover:not(:disabled) {
            background: rgba(48, 54, 61, 0.5);
        }

        .result {
            margin-top: 20px;
            font-weight: 400;
            font-size: 1.5em;
            color: #7d8590;
            text-align: center;
            text-shadow: 0 0 8px rgba(125, 133, 144, 0.2);
            font-family: 'Courier New', monospace;
        }

        .text-input {
            padding: 14px;
            font-size: 16px;
            border: 1px solid #30363d;
            border-radius: 4px;
            width: 100%;
            box-sizing: border-box;
            margin: 10px 0;
            background: rgba(13, 17, 23, 0.8);
            color: #8b949e;
            font-family: 'Courier New', monospace;
        }

        .text-input:focus {
            outline: none;
            border-color: #485662;
            box-shadow: 0 0 8px rgba(72, 86, 98, 0.3);
            background: rgba(13, 17, 23, 0.95);
        }

        .text-input::placeholder {
            color: #484f58;
        }

        .profile-item {
            background: rgba(22, 27, 34, 0.6);
            padding: 15px;
            margin: 12px 0;
            border-radius: 4px;
            border-left: 2px solid #30363d;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
        }

        .profile-item-label {
            font-weight: 400;
            color: #7d8590;
            margin-bottom: 8px;
            font-size: 0.85em;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-family: 'Courier New', monospace;
        }

        .profile-item-value {
            color: #8b949e;
            word-break: break-word;
            font-size: 1em;
            font-family: 'Courier New', monospace;
        }

        .breather-container {
            text-align: center;
            padding: 30px;
            margin: 20px 0;
            background: rgba(22, 27, 34, 0.8);
            border-radius: 4px;
            border: 1px solid #30363d;
            box-shadow: 0 4px 16px rgba(0, 0, 0, 0.3);
        }

        .breather-message {
            color: #8b949e;
            font-size: 1.2em;
            margin-bottom: 20px;
            font-weight: 400;
            text-shadow: 0 0 8px rgba(139, 148, 158, 0.2);
            line-height: 1.6;
            font-family: 'Courier New', monospace;
        }

        .breather-buttons {
            display: flex;
            gap: 15px;
            justify-content: center;
            flex-wrap: wrap;
        }

        .warning-message {
            background: rgba(60, 30, 30, 0.3);
            border: 1px solid #6e4040;
            border-radius: 4px;
            padding: 20px;
            margin: 20px 0;
            color: #b58181;
            font-weight: 400;
            text-align: center;
            box-shadow: 0 0 12px rgba(110, 64, 64, 0.2);
        }

        #leakContinue:disabled {
            background: rgba(30, 35, 40, 0.2);
            border-color: #30363d;
            color: #484f58;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.6; }
        }

        .loading {
            animation: pulse 1.5s infinite;
        }

        @media (max-width: 768px) {
            .glitch-text {
                font-size: 1.8em;
            }

            .quiz-container {
                padding: 20px;
            }

            #question {
                font-size: 1.1em;
            }

            button {
                padding: 12px 16px;
                font-size: 14px;
            }

            .breather-buttons {
                flex-direction: column;
            }

            .breather-buttons button {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="mission-header">
        <h1 class="glitch-text">SECURITY PROTOCOL TRAINING</h1>
        <p class="mission-brief">Complete this security assessment to verify your understanding of Personally Identifiable Information (PII) protocols. Operatives must demonstrate knowledge of data protection standards before accessing the network.</p>
    </div>

    <div class="quiz-container">
        <div id="loadingCheck" style="text-align: center; padding: 40px;">
            <div class="loading" style="font-size: 1.2em; color: #7d8590; font-family: 'Courier New', monospace;">
                CHECKING SYSTEM RECORDS...
            </div>
        </div>
        <div id="existingProfilePrompt" style="display: none;">
            <div class="breather-container">
                <div class="breather-message">EXISTING PROFILE DETECTED</div>
                <p style="color: #6e7681; margin: 20px 0; font-family: 'Courier New', monospace;">
                    We found your previous security clearance records in the system. Would you like to review your existing profile or retake the assessment?
                </p>
                <div class="breather-buttons">
                    <button id="loadExistingProfile" class="option-button">Load Existing Profile</button>
                    <button id="retakeFromStart" class="option-button">Retake Assessment</button>
                </div>
            </div>
        </div>
        <div id="quiz" style="display: none;">
            <div id="question"></div>
            <div class="options" id="options"></div>
            <button id="submit" type="button">Submit Answer</button>
        </div>
        <div id="results" style="display: none;">
            <div class="result">Assessment Complete: <span id="score">0</span>/10</div>
            <button id="restart">Restart Assessment</button>
        </div>
        <div id="leakBreather" style="display: none;">
            <div class="breather-container warning-message">
                <div class="breather-message" id="leakMessage"></div>
                <div class="breather-buttons">
                    <button id="leakRetake" class="option-button">Retake Assessment</button>
                    <button id="leakContinue" class="option-button">Continue to Profile</button>
                </div>
            </div>
        </div>
        <div id="review" style="display: none;">
            <div class="result">Profile Data Summary</div>
            <div id="profileData"></div>
            <div class="options">
                <button id="saveProfile" class="option-button">Save Profile</button>
                <button id="retakeQuiz" class="option-button">Retake Assessment</button>
            </div>
        </div>
    </div>

    <script>
        // Temporary config - replace with your actual Flask backend URL
        if (!window.pythonURI) {
            window.pythonURI = "http://localhost:8001"; // Flask backend port
        }
        
        const questions = [
            {
                question: "What does PII stand for?",
                options: ["Peer Investigation Information", "Personally Identifiable Information", "Please Invert Intestine", "Personal Identifying Infirmary"],
                correct: 1
            },
            {
                question: "Why do we protect PII?",
                options: ["Because mean people want to stop us from making friends", "Because we're mysterious and nonchalant, sharing PII would diminish that", "To prevent hackers, scammers, and others with ill intent from harming us", "Because Kai Cenat told us to"],
                correct: 2
            },
            {
                isBreather: true,
                message: "Protocol acknowledged. Now proceed with profile registration to establish your network identity."
            },
            {
                question: "What is your favorite color?",
                options: ["Red", "Orange", "Yellow", "Green", "Blue", "Purple", "Black", "White"],
                correct: null 
            },
            {
                question: "What do you want your username to be?",
                allowTextEntry: true,
                correct: null 
            },
            {
                question: "What's your favorite animal?",
                options: ["Dogs", "Cats", "Birds", "Fish", "Reptiles"],
                correct: null
            },
            {
                question: "What is your full name?",
                allowTextEntry: true,
                correct: null
            },
            {
                question: "What is your favorite genre of music?",
                options: ["Rock", "Pop", "Rap"],
                correct: null
            },
            {
                question: "What is your favorite band/musical artist?",
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
                question: "What is your favorite subject?",
                options: ["Math", "Science", "English", "History"],
                correct: null
            },
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
        const leakBreatherEl = document.getElementById('leakBreather');
        const leakMessageEl = document.getElementById('leakMessage');
        const leakRetakeBtn = document.getElementById('leakRetake');
        const leakContinueBtn = document.getElementById('leakContinue');
        const loadingCheckEl = document.getElementById('loadingCheck');
        const existingProfilePromptEl = document.getElementById('existingProfilePrompt');
        const loadExistingProfileBtn = document.getElementById('loadExistingProfile');
        const retakeFromStartBtn = document.getElementById('retakeFromStart');

        // Check for existing profile on page load
        async function checkExistingProfile() {
            const importedCfg = window._piiImportedConfig || {};
            const pythonURI = importedCfg.pythonURI || window.pythonURI || '';
            const globalFetchOptions = importedCfg.fetchOptions || window.fetchOptions || {};

            const endpoint = pythonURI ? `${pythonURI}/api/match/save-profile-json` : '/api/match/save-profile-json';

            console.log('=== PROFILE CHECK DEBUG ===');
            console.log('pythonURI:', pythonURI);
            console.log('Full endpoint:', endpoint);
            console.log('Fetch options:', globalFetchOptions);

            const options = Object.assign({}, globalFetchOptions, {
                method: 'GET',
                credentials: (globalFetchOptions && globalFetchOptions.credentials) ? globalFetchOptions.credentials : 'include'
            });

            console.log('Request options:', options);

            try {
                console.log('Sending GET request to:', endpoint);
                const response = await fetch(endpoint, options);
                console.log('Response status:', response.status);
                console.log('Response statusText:', response.statusText);
                console.log('Response headers:', Object.fromEntries([...response.headers.entries()]));
                
                const responseText = await response.text();
                console.log('Response body (raw):', responseText);
                
                if (response.ok) {
                    const data = JSON.parse(responseText);
                    console.log('Parsed response data:', data);
                    if (data && data.profile_data && Array.isArray(data.profile_data) && data.profile_data.length > 0) {
                        // Profile exists in backend
                        loadingCheckEl.style.display = 'none';
                        existingProfilePromptEl.style.display = 'block';
                        return data.profile_data;
                    }
                } else if (response.status === 404) {
                    console.log('404 - Profile not found (expected for new users)');
                }
                
                // No profile found or error, start quiz normally
                console.log('No existing profile, starting quiz');
                loadingCheckEl.style.display = 'none';
                quizEl.style.display = 'block';
                displayQuestion();
                return null;
            } catch (err) {
                console.error('Error checking profile:', err);
                console.error('Error stack:', err.stack);
                console.log('Starting fresh assessment');
                loadingCheckEl.style.display = 'none';
                quizEl.style.display = 'block';
                displayQuestion();
                return null;
            }
        }

        let existingProfileData = null;

        loadExistingProfileBtn.onclick = () => {
            if (existingProfileData) {
                displayExistingProfile(existingProfileData);
            }
        };

        retakeFromStartBtn.onclick = () => {
            existingProfilePromptEl.style.display = 'none';
            quizEl.style.display = 'block';
            displayQuestion();
        };

        function displayExistingProfile(profileData) {
            existingProfilePromptEl.style.display = 'none';
            quizEl.style.display = 'none';
            reviewEl.style.display = 'block';

            profileDataEl.innerHTML = '';
            const allowedKeywords = ['favorite color', 'favorite animal', 'genre of music', 'favorite genre', 'favorite subject', 'subject', 'username', 'favorite band', 'band', 'musical artist', 'favorite artist'];

            const usernameResponses = [];
            const otherResponses = [];
            
            for (let resp of profileData) {
                const qLower = (resp.question || '').toLowerCase();
                const matches = allowedKeywords.some(k => qLower.includes(k));
                if (!matches) continue;

                if (qLower.includes('username')) {
                    usernameResponses.push(resp);
                } else {
                    otherResponses.push(resp);
                }
            }

            const orderedResponses = [...usernameResponses, ...otherResponses];
            for (let resp of orderedResponses) {
                const profileItem = document.createElement('div');
                profileItem.className = 'profile-item';
                const label = document.createElement('div');
                label.className = 'profile-item-label';
                label.textContent = resp.question;
                const value = document.createElement('div');
                value.className = 'profile-item-value';
                value.textContent = resp.response !== null ? resp.response : '(Not provided)';
                profileItem.appendChild(label);
                profileItem.appendChild(value);
                profileDataEl.appendChild(profileItem);
            }
        }

        function displayQuestion() {
            const question = questions[currentQuestion];
            questionEl.textContent = question.question;
            questionEl.style.textAlign = '';
            questionEl.style.fontSize = '';
            questionEl.style.marginBottom = '';
            submitBtn.style.display = 'block';
            
            optionsEl.innerHTML = '';
            
            if (question.isBreather) {
                questionEl.textContent = question.message;
                questionEl.style.textAlign = 'center';
                questionEl.style.fontSize = '1.2em';
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
                const textInput = document.createElement('input');
                textInput.type = 'text';
                textInput.className = 'text-input';
                textInput.placeholder = "Enter your response or decline to answer";
                textInput.oninput = () => {
                    submitBtn.disabled = textInput.value.trim() === '';
                };
                optionsEl.appendChild(textInput);
                
                const declineBtn = document.createElement('button');
                declineBtn.className = 'option-button';
                declineBtn.textContent = "I'd rather not answer";
                declineBtn.onclick = () => {
                    textInput.value = '';
                    question.userResponse = null;
                    submitBtn.disabled = false;
                    declineBtn.classList.add('selected');
                };
                optionsEl.appendChild(declineBtn);
                
                submitBtn.style.display = 'block';
                submitBtn.disabled = true;
                questions[currentQuestion].textInputElement = textInput;
            } else {
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
                button.classList.remove('selected');
            }
            buttons[index].classList.add('selected');
            selectedOption = index;
            submitBtn.disabled = false;
        }

        function submitAnswer() {
            const question = questions[currentQuestion];
            
            if (question.allowTextEntry) {
                const textInput = question.textInputElement || document.querySelector('.text-input');
                if (textInput && textInput.value.trim() !== '') {
                    question.userResponse = textInput.value.trim();
                } else if (question.userResponse === undefined) {
                    question.userResponse = null;
                }
            } else {
                if (selectedOption !== null && question.options && question.options[selectedOption] !== undefined) {
                    question.userResponse = question.options[selectedOption];
                } else if (question.userResponse === undefined) {
                    question.userResponse = null;
                }

                if (typeof question.correct === 'number' && selectedOption === question.correct) {
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
            reviewEl.style.display = 'none';
            
            const userDataResponses = [];
            const startIndex = 3;
            
            for (let i = startIndex; i < questions.length; i++) {
                const q = questions[i];
                const response = q.userResponse !== undefined ? q.userResponse : null;
                userDataResponses.push({
                    question: q.question,
                    response: response,
                    type: q.allowTextEntry ? 'text' : 'multiple-choice'
                });
            }

            let leakCount = 0;
            for (let resp of userDataResponses) {
                const qLower = (resp.question || '').toLowerCase();
                const val = resp.response;
                if (val !== null && val !== undefined && String(val).trim() !== '') {
                    if (qLower.includes('full name') || qLower.includes('ssn') || qLower.includes('where do you live') || qLower.includes('ip')) {
                        leakCount++;
                    }
                }
            }

            const userDataJSON = JSON.stringify(userDataResponses, null, 2);
            sessionStorage.setItem('userQuizResponses', userDataJSON);
            window.userQuizData = userDataJSON;

            if (leakCount > 0) {
                leakMessageEl.textContent = `⚠️ SECURITY BREACH DETECTED ⚠️\n\nYou exposed ${leakCount} piece${leakCount>1? 's' : ''} of sensitive personal information! This data could be exploited by hostile actors. Retake the assessment and demonstrate proper security protocols.`;
                leakBreatherEl.style.display = 'block';
                reviewEl.style.display = 'none';
                leakContinueBtn.disabled = true;

                leakRetakeBtn.onclick = () => {
                    leakBreatherEl.style.display = 'none';
                    restartQuiz();
                };
                return;
            }

            leakBreatherEl.style.display = 'none';
            leakContinueBtn.disabled = false;

            profileDataEl.innerHTML = '';
            const allowedKeywords = ['favorite color', 'favorite animal', 'genre of music', 'favorite genre', 'favorite subject', 'subject', 'username', 'favorite band', 'band', 'musical artist', 'favorite artist'];

            const usernameResponses = [];
            const otherResponses = [];
            for (let resp of userDataResponses) {
                const qLower = (resp.question || '').toLowerCase();
                const matches = allowedKeywords.some(k => qLower.includes(k));
                if (!matches) continue;

                if (qLower.includes('username')) {
                    usernameResponses.push(resp);
                } else {
                    otherResponses.push(resp);
                }
            }

            const orderedResponses = [...usernameResponses, ...otherResponses];
            for (let resp of orderedResponses) {
                const profileItem = document.createElement('div');
                profileItem.className = 'profile-item';
                const label = document.createElement('div');
                label.className = 'profile-item-label';
                label.textContent = resp.question;
                const value = document.createElement('div');
                value.className = 'profile-item-value';
                value.textContent = resp.response !== null ? resp.response : '(Not provided)';
                profileItem.appendChild(label);
                profileItem.appendChild(value);
                profileDataEl.appendChild(profileItem);
            }
            reviewEl.style.display = 'block';
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

        saveProfileBtn.onclick = async () => {
            const userDataJSON = sessionStorage.getItem('userQuizResponses');
            if (!userDataJSON) {
                alert("No profile data found to save.");
                return;
            }

            let profileData;
            try {
                profileData = JSON.parse(userDataJSON);
            } catch (err) {
                console.error('piiQuiz: invalid JSON in sessionStorage userQuizResponses', err, userDataJSON);
                alert('Saved responses are not valid JSON. Please retake quiz.');
                return;
            }

            // Prefer config imported by a module script, fall back to window globals
            const importedCfg = window._piiImportedConfig || {};
            const pythonURI = importedCfg.pythonURI || window.pythonURI || '';
            const globalFetchOptions = importedCfg.fetchOptions || window.fetchOptions || {};

            const endpoint = pythonURI ? `${pythonURI}/api/match/save-profile-json` : '/api/match/save-profile-json';

            // Merge headers but don't mutate globalFetchOptions
            const mergedHeaders = Object.assign({}, (globalFetchOptions.headers || {}), {
                'Content-Type': 'application/json'
            });

            const payload = { profile_data: profileData };
            let bodyStr;
            try {
                bodyStr = JSON.stringify(payload);
            } catch (err) {
                console.error('piiQuiz: failed to stringify payload', err);
                alert('Failed to prepare profile JSON: ' + (err && err.message ? err.message : String(err)));
                return;
            }

            console.log('=== SAVE PROFILE DEBUG ===');
            console.log('piiQuiz: Saving to endpoint:', endpoint);
            console.log('piiQuiz: Payload:', payload);
            console.log('piiQuiz: Profile data length:', bodyStr.length);
            console.log('piiQuiz: Headers:', mergedHeaders);

            const options = Object.assign({}, globalFetchOptions, {
                method: 'POST',
                headers: mergedHeaders,
                body: bodyStr
            });

            // Prefer configured credentials (config.js default is 'include')
            if (!options.credentials) options.credentials = (globalFetchOptions && globalFetchOptions.credentials) ? globalFetchOptions.credentials : 'include';

            console.log('piiQuiz: Full request options:', options);

            try {
                console.log('piiQuiz: Sending POST request...');
                const response = await fetch(endpoint, options);
                console.log('piiQuiz: Response status:', response.status);
                console.log('piiQuiz: Response statusText:', response.statusText);
                console.log('piiQuiz: Response headers:', Object.fromEntries([...response.headers.entries()]));
                
                const responseText = await response.text();
                console.log('piiQuiz: Response body (raw text):', responseText);
                
                let data = null;
                if (responseText) {
                    try {
                        data = JSON.parse(responseText);
                        console.log('piiQuiz: Response data (parsed):', data);
                    } catch (parseErr) {
                        console.error('piiQuiz: Failed to parse response as JSON:', parseErr);
                        console.log('piiQuiz: Response was:', responseText);
                    }
                }

                if (!response.ok) {
                    alert("Failed to save profile: " + (data && data.message ? data.message : `Status ${response.status}`));
                    console.error("Backend response:", data);
                    return;
                }

                console.log("Profile saved successfully:", data);
                alert("Profile saved successfully! Data is now in profile_setups.json");
            } catch (err) {
                console.error("Error saving profile:", err);
                console.error("Error stack:", err.stack);
                alert("Failed to save profile. Check console for details. Error: " + err.message);
            }
        };

        retakeQuizBtn.onclick = () => {
            restartQuiz();
        };

        submitBtn.onclick = submitAnswer;
        restartBtn.onclick = restartQuiz;

        // Initialize - check for existing profile first
        (async () => {
            existingProfileData = await checkExistingProfile();
        })();
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