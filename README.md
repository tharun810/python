<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Python Exam Portal</title>
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2980b9;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --success: #2ecc71;
            --danger: #e74c3c;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f5f7fa;
            margin: 0;
            padding: 0;
            color: var(--dark);
        }
        .container {
            max-width: 800px;
            margin: 30px auto;
            padding: 30px;
            background: white;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        .page {
            display: none;
        }
        .active {
            display: block;
        }
        h1, h2 {
            color: var(--secondary);
            text-align: center;
            margin-bottom: 20px;
        }
        .form-group {
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
        }
        input[type="text"],
        input[type="tel"] {
            width: 100%;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
            transition: border 0.3s;
        }
        input[type="text"]:focus,
        input[type="tel"]:focus {
            border-color: var(--primary);
            outline: none;
        }
        button {
            background: var(--primary);
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: all 0.3s;
            display: block;
            margin: 30px auto 0;
            width: 200px;
        }
        button:hover {
            background: var(--secondary);
            transform: translateY(-2px);
        }
        .exam-info {
            display: flex;
            justify-content: space-between;
            background: var(--light);
            padding: 15px;
            border-radius: 5px;
            margin-bottom: 20px;
        }
        .timer {
            font-weight: bold;
            color: var(--danger);
            font-size: 1.2rem;
        }
        .question {
            background: var(--light);
            padding: 20px;
            border-radius: 8px;
            margin-bottom: 25px;
            border-left: 4px solid var(--primary);
        }
        .options {
            margin-top: 15px;
        }
        .option {
            margin: 12px 0;
            padding: 12px;
            background: white;
            border-radius: 5px;
            border: 1px solid #ddd;
            transition: all 0.3s;
        }
        .option:hover {
            border-color: var(--primary);
            background: #f8fcff;
        }
        .option input {
            margin-right: 10px;
        }
        .results {
            text-align: center;
            padding: 30px;
            background: var(--light);
            border-radius: 10px;
        }
        .score {
            font-size: 2rem;
            font-weight: bold;
            color: var(--secondary);
            margin: 20px 0;
        }
        .user-details {
            background: white;
            padding: 20px;
            border-radius: 8px;
            margin-bottom: 20px;
            text-align: left;
        }
        .hidden {
            display: none;
        }
        .progress-container {
            width: 100%;
            background-color: #e0e0e0;
            border-radius: 5px;
            margin: 20px 0;
        }
        .progress-bar {
            height: 10px;
            background-color: var(--success);
            border-radius: 5px;
            width: 0%;
            transition: width 0.5s;
        }
        .admin-section {
            margin-top: 30px;
            padding-top: 20px;
            border-top: 1px solid #ddd;
        }
    </style>
</head>
<body>
    <!-- Login Page -->
    <div class="container page active" id="loginPage">
        <h1>Python Exam Portal</h1>
        <div class="form-group">
            <label for="userName">Full Name:</label>
            <input type="text" id="userName" placeholder="Enter your full name" required>
        </div>
        <div class="form-group">
            <label for="userNumber">Mobile Number:</label>
            <input type="tel" id="userNumber" placeholder="Enter your 10-digit mobile number" required>
        </div>
        <div class="form-group">
            <label for="examCode">Exam Code (if any):</label>
            <input type="text" id="examCode" placeholder="Enter exam code (optional)">
        </div>
        <button onclick="validateLogin()">Start Exam</button>
    </div>

    <!-- Exam Page -->
    <div class="container page" id="examPage">
        <div class="user-details">
            <h2>Python Certification Exam</h2>
            <p>Candidate: <strong id="displayName"></strong></p>
            <p>Mobile: <strong id="displayNumber"></strong></p>
        </div>
        
        <div class="exam-info">
            <div>Questions: <strong>15</strong></div>
            <div class="timer">Time Left: <span id="time">30:00</span></div>
        </div>

        <div class="progress-container">
            <div class="progress-bar" id="progress"></div>
        </div>

        <form id="quizForm">
            <!-- Questions 1-5 -->
            <div class="question">
                <h3>1. What is the correct extension for Python files?</h3>
                <div class="options">
                    <label class="option"><input type="radio" name="q1" value="a" required> a) .pyt</label>
                    <label class="option"><input type="radio" name="q1" value="b"> b) .py</label>
                    <label class="option"><input type="radio" name="q1" value="c"> c) .pt</label>
                    <label class="option"><input type="radio" name="q1" value="d"> d) .python</label>
                </div>
            </div>

            <div class="question">
                <h3>2. Which of these is NOT a Python data type?</h3>
                <div class="options">
                    <label class="option"><input type="radio" name="q2" value="a" required> a) list</label>
                    <label class="option"><input type="radio" name="q2" value="b"> b) tuple</label>
                    <label class="option"><input type="radio" name="q2" value="c"> c) array</label>
                    <label class="option"><input type="radio" name="q2" value="d"> d) dictionary</label>
                </div>
            </div>

            <!-- Questions 3-15 would follow the same pattern -->
            <!-- For brevity, I'm showing 2 questions, but you would include all 15 -->
            
            <button type="button" onclick="submitExam()">Submit Exam</button>
        </form>
    </div>

    <!-- Results Page -->
    <div class="container page" id="resultsPage">
        <div class="user-details">
            <h2>Exam Results</h2>
            <p>Candidate: <strong id="resultName"></strong></p>
            <p>Mobile: <strong id="resultNumber"></strong></p>
            <p>Exam Date: <strong id="examDate"></strong></p>
        </div>
        
        <div class="results">
            <div class="score">Your Score: <span id="score">0</span>/15</div>
            <p id="resultMessage"></p>
            
            <div class="admin-section hidden" id="adminSection">
                <h3>Exam Administrator Details</h3>
                <p>Exam conducted by: <strong>Python Certification Board</strong></p>
                <p>Contact: certification@python.org</p>
            </div>
            
            <button onclick="printResult()">Print Result</button>
        </div>
    </div>

    <script>
        // Correct answers for all 15 questions
        const correctAnswers = {
            q1: "b", q2: "c", q3: "a", q4: "b", q5: "d",
            q6: "a", q7: "c", q8: "b", q9: "d", q10: "a",
            q11: "b", q12: "c", q13: "a", q14: "d", q15: "b"
        };

        // User data and exam variables
        let currentUser = {};
        let timeLeft = 1800; // 30 minutes in seconds
        let timerInterval;
        let answeredCount = 0;

        // Start exam
        function validateLogin() {
            const name = document.getElementById('userName').value.trim();
            const number = document.getElementById('userNumber').value.trim();
            const examCode = document.getElementById('examCode').value.trim();

            // Basic validation
            if (name.length < 3) {
                alert("Please enter your full name (at least 3 characters)");
                return;
            }

            if (!/^\d{10}$/.test(number)) {
                alert("Please enter a valid 10-digit mobile number");
                return;
            }

            // Store user data
            currentUser = {
                name: name,
                number: number,
                examCode: examCode,
                startTime: new Date()
            };

            // Show exam page
            showPage('examPage');
            document.getElementById('displayName').textContent = name;
            document.getElementById('displayNumber').textContent = number;
            
            // Start timer
            startTimer();
            document.getElementById('quizForm').addEventListener('change', updateProgress);
        }

        function startTimer() {
            timerInterval = setInterval(function() {
                timeLeft--;
                updateTimerDisplay();
                
                if (timeLeft <= 0) {
                    clearInterval(timerInterval);
                    submitExam();
                }
            }, 1000);
        }

        function updateTimerDisplay() {
            const minutes = Math.floor(timeLeft / 60);
            const seconds = timeLeft % 60;
            document.getElementById('time').textContent = 
                `${minutes}:${seconds < 10 ? '0' : ''}${seconds}`;
            
            if (timeLeft < 300) { // 5 minutes left
                document.querySelector('.timer').style.color = 'var(--danger)';
            }
        }

        function updateProgress() {
            answeredCount = document.querySelectorAll('input[type="radio"]:checked').length;
            const progress = (answeredCount / 15) * 100;
            document.getElementById('progress').style.width = `${progress}%`;
        }

        function submitExam() {
            clearInterval(timerInterval);
            
            // Calculate score
            let score = 0;
            for (let i = 1; i <= 15; i++) {
                const selected = document.querySelector(`input[name="q${i}"]:checked`);
                if (selected && selected.value === correctAnswers[`q${i}`]) {
                    score++;
                }
            }
            
            // Show results
            showPage('resultsPage');
            document.getElementById('resultName').textContent = currentUser.name;
            document.getElementById('resultNumber').textContent = currentUser.number;
            document.getElementById('score').textContent = score;
            
            // Set exam date
            const now = new Date();
            document.getElementById('examDate').textContent = now.toLocaleString();
            
            // Set result message
            const resultMessage = document.getElementById('resultMessage');
            if (score >= 12) {
                resultMessage.textContent = "Excellent! You have passed the exam with distinction!";
                resultMessage.style.color = "var(--success)";
            } else if (score >= 9) {
                resultMessage.textContent = "Congratulations! You have passed the exam!";
                resultMessage.style.color = "var(--success)";
            } else {
                resultMessage.textContent = "You didn't pass this time. Please try again!";
                resultMessage.style.color = "var(--danger)";
            }
            
            // Show admin section
            document.getElementById('adminSection').classList.remove('hidden');
        }

        function printResult() {
            window.print();
        }

        function showPage(pageId) {
            // Hide all pages
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            
            // Show the requested page
            document.getElementById(pageId).classList.add('active');
        }
    </script>
</body>
</html>
