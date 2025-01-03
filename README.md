<html lang="en">
    
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fun Roulette Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #1b3b19;
            color: white;
        }

        h1 {
            text-align: center;
            padding: 10px;
        }

        /* Login Form */
        .login-form {
            width: 300px;
            margin: 100px auto;
            padding: 20px;
            background-color: #333333;
            border-radius: 10px;
            text-align: center;
        }

        .login-form input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            border: 1px solid #555555;
            background-color: #444444;
            color: white;
            font-size: 16px;
        }

        .login-form button {
            background-color: gold;
            color: black;
            padding: 10px 20px;
            margin: 10px;
            font-size: 16px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .login-form button:hover {
            background-color: #d4af37;
        }

        /* Roulette Wheel and Betting Table */
        .game-container {
            display: none;
        }

        .roulette-wheel {
            margin: 20px auto;
            width: 200px;
            height: 200px;
            border: 5px solid gold;
            border-radius: 50%;
            background: radial-gradient(circle, #000000, #333333);
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
        }

        .wheel-center {
            width: 40px;
            height: 40px;
            background: gold;
            border-radius: 50%;
        }

        .numbers {
            position: absolute;
            width: 200px;
            height: 200px;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            transform: rotate(0deg);
            animation: spin 3s infinite linear;
        }

        .numbers span {
            position: absolute;
            transform-origin: 100px;
            font-size: 14px;
        }

        @keyframes spin {
            from {
                transform: rotate(0deg);
            }
            to {
                transform: rotate(360deg);
            }
        }

        .betting-table {
            margin: 20px auto;
            padding: 10px;
            max-width: 800px;
            background-color: #333333;
            border: 2px solid gold;
            border-radius: 10px;
            display: grid;
            grid-template-columns: repeat(12, 1fr);
            gap: 5px;
        }

        .bet {
            background-color: #444444;
            color: white;
            text-align: center;
            padding: 10px;
            font-size: 14px;
            border: 1px solid #555555;
            border-radius: 5px;
            cursor: pointer;
            user-select: none;
        }

        .bet:hover {
            background-color: gold;
            color: black;
        }

        .control-panel {
            text-align: center;
            margin-top: 20px;
        }

        .control-panel button {
            background-color: gold;
            color: black;
            padding: 10px 20px;
            margin: 10px;
            font-size: 16px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .control-panel button:hover {
            background-color: #d4af37;
        }

        .scoreboard {
            text-align: center;
            margin-top: 10px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <!-- Login Form -->
    <div class="login-form" id="loginForm">
        <h2>Login</h2>
        <input type="text" id="userId" placeholder="Enter ID" />
        <input type="password" id="userPassword" placeholder="Enter Password" />
        <button onclick="login()">Login</button>
    </div>

    <!-- Game Container -->
    <div class="game-container" id="gameContainer">
        <h1>Fun Roulette</h1>
        <!-- Roulette Wheel -->
        <div class="roulette-wheel">
            <div class="numbers">
                <span style="transform: rotate(0deg) translate(90px);">0</span>
                <span style="transform: rotate(30deg) translate(90px);">32</span>
                <span style="transform: rotate(60deg) translate(90px);">15</span>
                <span style="transform: rotate(90deg) translate(90px);">19</span>
                <span style="transform: rotate(120deg) translate(90px);">4</span>
                <span style="transform: rotate(150deg) translate(90px);">21</span>
                <span style="transform: rotate(180deg) translate(90px);">2</span>
                <span style="transform: rotate(210deg) translate(90px);">25</span>
                <span style="transform: rotate(240deg) translate(90px);">17</span>
                <span style="transform: rotate(270deg) translate(90px);">34</span>
                <span style="transform: rotate(300deg) translate(90px);">6</span>
                <span style="transform: rotate(330deg) translate(90px);">27</span>
            </div>
            <div class="wheel-center"></div>
        </div>

        <!-- Betting Table -->
        <div class="betting-table">
            <div class="bet">1</div>
            <div class="bet">2</div>
            <div class="bet">3</div>
            <div class="bet">4</div>
            <div class="bet">5</div>
            <div class="bet">6</div>
            <div class="bet">7</div>
            <div class="bet">8</div>
            <div class="bet">9</div>
            <div class="bet">10</div>
            <div class="bet">11</div>
            <div class="bet">12</div>
        </div>

        <!-- Control Panel -->
        <div class="control-panel">
            <button onclick="placeBet()">Place Bet</button>
            <button onclick="spinWheel()">Spin Wheel</button>
        </div>

        <!-- Scoreboard -->
        <div class="scoreboard">
            <p>Score: <span id="score">100</span></p>
            <p>Winner: <span id="winner">-</span></p>
        </div>
    </div>

    <script>
        const correctId = '727670';
        const correctPassword = '727670';

        function login() {
            const userId = document.getElementById('userId').value;
            const userPassword = document.getElementById('userPassword').value;

            if (userId === correctId && userPassword === correctPassword) {
                // Hide login form and show game
                document.getElementById('loginForm').style.display = 'none';
                document.getElementById('gameContainer').style.display = 'block';
            } else {
                alert('Incorrect ID or Password!');
            }
        }

        let score = 100;

        function placeBet() {
            alert("Bet placed!");
        }

        function spinWheel() {
            const winner = Math.floor(Math.random() * 12) + 1; // Random number 1-12
            document.getElementById('winner').innerText = winner;
            alert("The winner is: " + winner);
        }
    </script>
</body>
</html>
