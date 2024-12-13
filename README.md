<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Английский тест B1-B2</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #e0f7fa, #82caff);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            color: #333;
        }

        .container {
            width: 90%;
            max-width: 700px;
            background: #fff;
            border-radius: 20px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15);
            padding: 20px;
            text-align: center;
            overflow: hidden;
        }

        .intro {
            background-color: #0288d1;
            color: #fff;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
            font-size: 18px;
        }

        .intro h2 {
            margin-top: 0;
            font-size: 24px;
        }

        .intro p {
            font-size: 16px;
            line-height: 1.6;
        }

        #question {
            font-size: 22px;
            font-weight: bold;
            color: #0288d1;
            margin-bottom: 20px;
        }

        #options {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        button {
            background-color: #4caf50;
            color: white;
            font-size: 16px;
            padding: 12px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        button:hover {
            background-color: #45a049;
            transform: scale(1.05);
        }

        button:active {
            background-color: #3e8e41;
        }

        .result {
            font-size: 20px;
            font-weight: bold;
            color: #00796b;
            margin-top: 20px;
        }
    </style>
    <script>
        const questions = [
            { question: "What is the past tense of the verb 'go'?", answers: ["went", "gone", "goes"], correctAnswer: 0 },
            { question: "I _______ to the store yesterday.", answers: ["goes", "went", "going"], correctAnswer: 1 },
            { question: "What is the opposite of 'cheap'?", answers: ["expensive", "costly", "low"], correctAnswer: 0 },
            { question: "Which of the following is a synonym for 'happy'?", answers: ["sad", "cheerful", "angry"], correctAnswer: 1 },
            { question: "Fill in the blank: 'He is _______ student in the class.'", answers: ["the smartest", "smartest", "more smarter"], correctAnswer: 0 }
            // Дополнительные вопросы...
        ];

        let currentQuestionIndex = 0;
        let score = 0;

        function displayQuestion() {
            if (currentQuestionIndex < questions.length) {
                document.getElementById("question").textContent = questions[currentQuestionIndex].question;

                const options = document.getElementById("options");
                options.innerHTML = '';
                questions[currentQuestionIndex].answers.forEach((answer, index) => {
                    const button = document.createElement("button");
                    button.textContent = answer;
                    button.classList.add("btn-text");
                    button.onclick = function () { checkAnswer(index); };
                    options.appendChild(button);
                });
            } else {
                document.getElementById("question").textContent = "Тест завершен!";
                document.getElementById("options").innerHTML = `<p class='result'>Ваш балл: ${score} из ${questions.length}</p>`;
            }
        }

        function checkAnswer(selectedIndex) {
            const correctIndex = questions[currentQuestionIndex].correctAnswer;
            if (selectedIndex === correctIndex) {
                score++;
            }
            currentQuestionIndex++;
            displayQuestion();
        }

        window.onload = displayQuestion;
    </script>
</head>
<body>
    <div class="container">
        <div class="intro">
            <h2>Добро пожаловать в тест по английскому языку!</h2>
            <p>Этот тест поможет вам улучшить знание английского языка на уровнях B1 и B2. Ответьте на вопросы и узнайте ваш уровень!</p>
        </div>

        <div class="test-content">
            <p id="question"></p>
            <div id="options"></div>
        </div>
    </div>
</body>
</html>
