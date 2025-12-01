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
            background: linear-gradient(135deg, #e8d9f0 0%, #dcc9e8 100%);
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
                options: ["Red", "Orange", "Yellow", "Green", "Blue", "Purple"],
                correct: null 
            },
            {
                question: "Which do you prefer?",
                options: ["Dogs", "Cats"],
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

        function displayQuestion() {
            const question = questions[currentQuestion];
            questionEl.textContent = question.question;
            
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
            resultsEl.style.display = 'block';
            scoreEl.textContent = score;
        }

        function restartQuiz() {
            currentQuestion = 0;
            score = 0;
            selectedOption = null;
            quizEl.style.display = 'block';
            resultsEl.style.display = 'none';
            displayQuestion();
        }

        submitBtn.onclick = submitAnswer;
        restartBtn.onclick = restartQuiz;

        // Start the quiz
        displayQuestion();
    </script>
</body>
</html>