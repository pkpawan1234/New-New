<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Coder Pawan Animation</title>
    <style>
        body {
            background-color: black;
            text-align: center;
            font-family: Arial, sans-serif;
            color: white;
        }

        /* Coder Pawan Animation (Bold and Animated Font) */
        .coder-text {
            font-size: 60px;
            font-weight: bold;
            opacity: 0;
            animation: fadeIn 0.5s forwards, fadeOut 0.5s 2.5s forwards, moveIn 1s ease-out forwards;
            font-family: 'Courier New', Courier, monospace;
        }

        @keyframes fadeIn {
            0% { opacity: 0; }
            100% { opacity: 1; }
        }

        @keyframes fadeOut {
            0% { opacity: 1; }
            100% { opacity: 0; }
        }

        @keyframes moveIn {
            0% { transform: translateY(-50px); opacity: 0; }
            100% { transform: translateY(0); opacity: 1; }
        }

        /* Explosion Image with High Opacity and Max Brightness */
        .explosion {
            display: none;
            width: 300px;
            height: 300px;
            background: url('https://i.imgur.com/LLk0FGa.png') no-repeat center;
            background-size: cover;
            margin: 20px auto;
            animation: explosionAnim 0.5s forwards;
        }

        @keyframes explosionAnim {
            0% {
                opacity: 1;
                filter: brightness(1000%) contrast(200%) saturate(200%);
            }
            100% {
                opacity: 0.9;
                filter: brightness(1500%) contrast(250%) saturate(250%);
            }
        }

        /* iPhone-Style Calculator with Background Image */
        .calculator {
            display: none;
            width: 280px;
            padding: 20px;
            background: url('https://i.imgur.com/LLk0FGa.png') no-repeat center;
            background-size: cover;
            opacity: 0.7;  /* Increased opacity for background */
            border-radius: 15px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
            text-align: center;
            margin: auto;
            animation: showCalculator 0.5s ease-out forwards;
        }

        @keyframes showCalculator {
            0% { opacity: 0; transform: scale(0.5); }
            100% { opacity: 1; transform: scale(1); }
        }

        .display {
            width: 100%;
            height: 60px;
            background: #222;
            color: white;
            font-size: 2em;
            text-align: right;
            padding: 10px;
            border-radius: 10px;
            margin-bottom: 10px;
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        button {
            width: 60px;
            height: 60px;
            font-size: 1.5em;
            background: #555;
            border: none;
            color: white;
            border-radius: 10px;
            cursor: pointer;
            transition: 0.2s;
        }

        button:active {
            background: #777;
        }

        .equals {
            background: orange;
        }
    </style>
</head>
<body>

    <!-- Coder Pawan Text -->
    <div class="coder-text">Coder Pawan</div>

    <!-- Explosion Animation -->
    <div class="explosion"></div>

    <!-- Calculator -->
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button onclick="clearDisplay()">C</button>
            <button onclick="appendToDisplay('/')">/</button>
            <button onclick="appendToDisplay('*')">*</button>
            <button onclick="appendToDisplay('-')">-</button>

            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button onclick="appendToDisplay('+')">+</button>

            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button onclick="appendToDisplay('.')">.</button>

            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button class="equals" onclick="calculateResult()">=</button>

            <button onclick="appendToDisplay('0')" style="grid-column: span 2;">0</button>
        </div>
    </div>

    <script>
        // Explosion and Coder Pawan Text Logic
        setTimeout(() => {
            document.querySelector('.explosion').style.display = 'block';  // Start explosion

            setTimeout(() => {
                document.querySelector('.explosion').style.display = 'none';  // Hide explosion
                document.querySelector('.coder-text').style.display = 'block';  // Show Coder Pawan text
            }, 500);  // Explosion duration (0.5 second)

            setTimeout(() => {
                document.querySelector('.coder-text').style.display = 'none';  // Hide Coder Pawan text
                document.querySelector('.calculator').style.display = 'block';  // Show calculator
            }, 2000);  // After 2 seconds, calculator appears
        }, 1000);  // Initial explosion starts after 1 second delay

        // Calculator Functions
        function appendToDisplay(value) {
            let display = document.getElementById("display");
            if (display.innerText === "0") {
                display.innerText = value;
            } else {
                display.innerText += value;
            }
        }

        function clearDisplay() {
            document.getElementById("display").innerText = "0";
        }

        function calculateResult() {
            let display = document.getElementById("display");
            try {
                // To avoid errors, check if the expression is valid
                if (display.innerText.includes("Error")) {
                    display.innerText = "0";
                    return;
                }
                // Evaluate the expression safely
                display.innerText = eval(display.innerText);
            } catch {
                // Handle any errors in expression
                display.innerText = "Error";
            }
        }
    </script>

</body>
</html>
