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
            background-color: #37096bff;
            padding: 20px;
            border-radius: 8px;
            margin-top: 20px;
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
            background-color: #4b4b4bff;
            color: white;
            font-size: 16px;
        }
        button:hover {
            background-color: #45a049;
        }
        .option-button {
            background-color: #6a2e3d;
            color: #131313ff;
            border: 1px solid #ddd;
        }
        .option-button:hover {
            background-color: #f0f0f0;
        }
        .result {
            margin-top: 20px;
            font-weight: bold;
            font-size: 18px;
        }
        .feedback {
            color: #ffffffff;
            margin-top: 10px;
        }
        .text-input {
            padding: 12px;
            font-size: 16px;
            border: 2px solid #ddd;
            border-radius: 4px;
            width: 100%;
            box-sizing: border-box;
            margin: 10px 0;
        }
        .text-input:focus {
            outline: none;
            border-color: #45a049;
            box-shadow: 0 0 5px rgba(69, 160, 73, 0.5);
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
            
            if (question.allowTextEntry) {
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
                    declineBtn.style.backgroundColor = '#e0e0e0';
                };
                optionsEl.appendChild(declineBtn);
                
                submitBtn.disabled = true;
                // Store reference for submit handler
                currentQuestion.textInputElement = textInput;
            } else {
                // Regular multiple choice
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
                button.style.backgroundColor = '#ffffff';
            }
            buttons[index].style.backgroundColor = '#e0e0e0';
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