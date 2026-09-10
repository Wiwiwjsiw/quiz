```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Ultimate Tpett Quiz</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            color: white;
            text-align: center;
            margin: 0;
            padding: 40px 20px;
            min-height: 100vh;

            /* Smoothly changing background */
            background: linear-gradient(
                135deg,
                #6a5acd,
                #00bfff,
                #ff4ecd,
                #ff7b00,
                #00d084
            );
            background-size: 500% 500%;
            animation: backgroundMove 12s ease infinite;
        }

        @keyframes backgroundMove {
            0% {
                background-position: 0% 50%;
            }

            25% {
                background-position: 100% 50%;
            }

            50% {
                background-position: 100% 100%;
            }

            75% {
                background-position: 0% 100%;
            }

            100% {
                background-position: 0% 50%;
            }
        }

        .quiz-box {
            max-width: 600px;
            margin: 40px auto;
            background: rgba(0, 0, 0, 0.4);
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            backdrop-filter: blur(8px);
        }

        h1 {
            font-size: 35px;
        }

        #question {
            font-size: 24px;
            margin: 30px 0;
        }

        button {
            background: white;
            color: #333;
            border: none;
            padding: 15px 35px;
            margin: 10px;
            border-radius: 12px;
            font-size: 18px;
            cursor: pointer;
            transition: 0.2s;
        }

        button:hover {
            transform: scale(1.08);
            background: #ffe66d;
        }

        #result {
            font-size: 25px;
            margin-top: 25px;
            font-weight: bold;
        }

        #retryButton {
            display: none;
            background: #ffe66d;
            font-weight: bold;
        }

        #progress {
            opacity: 0.8;
        }
    </style>
</head>

<body>

<div class="quiz-box">

    <h1>🏆 The Ultimate Tpett Quiz 🏆</h1>

    <p id="progress">Question 1 of 5</p>

    <div id="question"></div>

    <button id="yesButton" onclick="answer('yes')">
        YES 👍
    </button>

    <button id="noButton" onclick="answer('no')">
        NO 👎
    </button>

    <div id="result"></div>

    <button id="retryButton" onclick="retryQuiz()">
        🔄 RETRY QUIZ
    </button>

</div>

<script>

    const questions = [
        "Is Tpett the GOAT? 🐐",
        "Is Tpett the GOAT at LT? 🏆",
        "Is Tpett the #1 DB player? 🥇",
        "Will Tpett 5-0 you in anything? 💀",
        "Is Kolvu a puppy boy? 🐶"
    ];

    let currentQuestion = 0;
    let score = 0;

    function showQuestion() {

        document.getElementById("question").textContent =
            questions[currentQuestion];

        document.getElementById("progress").textContent =
            `Question ${currentQuestion + 1} of ${questions.length}`;

        document.getElementById("result").textContent = "";

    }

    function answer(choice) {

        // YES is the correct answer to every question
        if (choice === "yes") {
            score++;
        }

        currentQuestion++;

        if (currentQuestion < questions.length) {

            showQuestion();

        } else {

            finishQuiz();

        }
    }

    function finishQuiz() {

        document.getElementById("question").textContent =
            "QUIZ COMPLETE! 🎉";

        document.getElementById("progress").textContent = "";

        document.getElementById("yesButton").style.display = "none";
        document.getElementById("noButton").style.display = "none";

        if (score === 5) {

            document.getElementById("result").innerHTML =
                "🔥 5/5 🔥<br><br>" +
                "YOU KNOW THE TRUTH! 🐐👑<br>" +
                "TPETT IS THE GOAT.";

            // No retry needed if you got everything right
            document.getElementById("retryButton").style.display = "none";

        } else {

            document.getElementById("result").innerHTML =
                `${score}/5 🤨<br><br>` +
                "BRO... YOU WERE SUPPOSED TO SAY YES 💀";

            // Show retry button
            document.getElementById("retryButton").style.display = "inline-block";
        }
    }

    function retryQuiz() {

        currentQuestion = 0;
        score = 0;

        document.getElementById("yesButton").style.display = "inline-block";
        document.getElementById("noButton").style.display = "inline-block";

        document.getElementById("retryButton").style.display = "none";

        showQuestion();
    }

    showQuestion();

</script>

</body>
</html>
```