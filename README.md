<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Merry Christmas from BINS</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Mountains+of+Christmas:wght@700&family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Poppins', sans-serif;
            background: url('https://img.freepik.com/premium-vector/cartoon-merry-christmas-snowy-scene-pine-tree-gift-illustration-background-nordic-scandinavian-style_573238-554.jpg') no-repeat center center fixed;
            background-size: cover;
            color: white;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            position: relative;
        }
        .snow-container {
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            pointer-events: none;
            z-index: 1;
        }
        /* Name Input Screen (English) */
        .name-screen {
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: rgba(0, 0, 0, 0.3);
            z-index: 20;
            transition: opacity 0.8s ease;
            padding: 20px;
        }
        .name-screen h1 {
            font-family: 'Mountains of Christmas', cursive;
            font-size: 4.5rem;
            color: #ffcc00;
            margin-bottom: 20px;
            text-shadow: 0 0 20px rgba(255,204,0,0.9);
        }
        .name-screen p {
            font-size: 1.5rem;
            margin-bottom: 40px;
            text-shadow: 0 0 10px #000;
        }
        .name-form {
            background: rgba(255,255,255,0.25);
            backdrop-filter: blur(12px);
            border-radius: 25px;
            padding: 45px;
            max-width: 520px;
            width: 100%;
            border: 4px solid #ffcc00;
            box-shadow: 0 0 40px rgba(255,204,0,0.5);
        }
        .input-group label { font-size: 1.4rem; color: #ffcc00; text-shadow: 0 0 10px #000; }
        .input-group input {
            width: 100%;
            padding: 20px 25px;
            font-size: 1.4rem;
            border: 3px solid #ffcc00;
            border-radius: 15px;
            background: rgba(255,255,255,0.9);
            color: #333;
            text-align: center;
        }
        .submit-btn {
            background: linear-gradient(to bottom, #c21807, #8b0000);
            color: white;
            border: none;
            padding: 20px 45px;
            font-size: 1.6rem;
            border-radius: 15px;
            cursor: pointer;
            width: 100%;
            font-family: 'Mountains of Christmas', cursive;
            letter-spacing: 3px;
            box-shadow: 0 8px 20px rgba(139,0,0,0.6);
        }
        .submit-btn:hover { transform: translateY(-8px); box-shadow: 0 15px 30px rgba(139,0,0,0.7); }

        /* Card Container */
        .card-container {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 15;
            width: 90%;
            max-width: 700px;
            opacity: 0;
            transition: opacity 1s ease;
            pointer-events: none;
        }
        .card-container.active {
            opacity: 1;
            pointer-events: all;
        }
        /* Card with presentable snowy white background */
        .card {
            background: url('https://thumbs.dreamstime.com/b/soft-winter-white-texture-blurred-subtle-snow-glow-empty-background-accompanied-christmas-decorations-415804572.jpg') center/cover no-repeat;
            border-radius: 25px;
            padding: 60px 50px;
            box-shadow:
                0 25px 50px rgba(0, 0, 0, 0.5),
                inset 0 0 40px rgba(139, 0, 0, 0.15);
            border: 8px solid #b22222;
            position: relative;
            overflow: hidden;
            min-height: 500px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        .card::before {
            content: '';
            position: absolute;
            top: -15px;
            left: -15px;
            right: -15px;
            bottom: -15px;
            background: linear-gradient(45deg, #ff0000, #ff9900, #ffff00, #00ff00, #00ffff, #0000ff, #9900ff);
            background-size: 400% 400%;
            z-index: -1;
            border-radius: 35px;
            animation: borderGlow 8s ease infinite;
            filter: blur(15px);
            opacity: 0.6;
        }
        /* Greeting Text */
        .greeting {
            text-align: center;
            position: relative;
            z-index: 2;
        }
        .greeting-line {
            margin-bottom: 30px;
            min-height: 80px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .greeting-text {
            font-family: 'Mountains of Christmas', cursive;
            font-size: 4rem;
            display: inline-block;
            text-transform: uppercase;
        }
        .letter {
            display: inline-block;
            opacity: 0;
            transform: translateY(40px);
            color: #b22222;
        }
        .personal-name {
            color: #0c9a4a;
            font-weight: bold;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
        }
        .space {
            display: inline-block;
            width: 25px;
        }
        .tagalog-text .letter {
            color: #1a3666;
        }
        .from-bins {
            font-family: 'Mountains of Christmas', cursive;
            font-size: 3.5rem;
            color: #2c3e50;
            margin-top: 60px;
            opacity: 0;
            transform: translateY(30px);
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
            text-transform: uppercase;
        }
        /* Cursor */
        .cursor {
            display: inline-block;
            width: 5px;
            height: 60px;
            background-color: #ffcc00;
            margin-left: 10px;
            animation: blink 1s infinite;
            vertical-align: middle;
            box-shadow: 0 0 10px #ffcc00;
        }
        @keyframes borderGlow {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        @keyframes blink {
            0%, 50% { opacity: 1; }
            51%, 100% { opacity: 0; }
        }
        @keyframes letterAppear {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        @keyframes snowFall {
            0% { transform: translateY(-100px) rotate(0deg); }
            100% { transform: translateY(100vh) rotate(360deg); }
        }
        .snowflake {
            position: absolute;
            background: white;
            border-radius: 50%;
            opacity: 0.95;
            box-shadow: 0 0 15px #fff;
        }
        @media (max-width: 768px) {
            .greeting-text { font-size: 3rem; }
            .from-bins { font-size: 2.8rem; }
        }
    </style>
</head>
<body>
    <!-- Name Input Screen -->
    <div class="name-screen" id="nameScreen">
        <h1>Merry Christmas!</h1>
        <p>Enter your name to open a fun personalized Christmas card from BINS!</p>
        <div class="name-form">
            <div class="input-group">
                <label for="userName"><i class="fas fa-user"></i> Your Name</label>
                <input type="text" id="userName" placeholder="Enter your name here..." maxlength="30">
            </div>
            <button class="submit-btn" id="submitName">
                <i class="fas fa-gift"></i> Open My Card
            </button>
        </div>
    </div>

    <!-- Snow -->
    <div class="snow-container" id="snowContainer"></div>

    <!-- Card Container -->
    <div class="card-container" id="cardContainer">
        <div class="card">
            <div class="greeting" id="greeting">
                <div class="greeting-line">
                    <div class="greeting-text" id="greetingText1"></div>
                </div>
                <div class="greeting-line">
                    <div class="greeting-text" id="greetingText2"></div>
                </div>
                <div class="greeting-line">
                    <div class="greeting-text tagalog-text" id="greetingText3"></div>
                </div>

                <div class="from-bins" id="fromBins">-FROM BINS</div>
                <div class="cursor" id="cursor"></div>
            </div>
        </div>
    </div>

    <script>
        const nameScreen = document.getElementById('nameScreen');
        const cardContainer = document.getElementById('cardContainer');
        const userNameInput = document.getElementById('userName');
        const submitNameBtn = document.getElementById('submitName');
        const greetingText1 = document.getElementById('greetingText1');
        const greetingText2 = document.getElementById('greetingText2');
        const greetingText3 = document.getElementById('greetingText3');
        const fromBins = document.getElementById('fromBins');
        const cursor = document.getElementById('cursor');
        const snowContainer = document.getElementById('snowContainer');

        let userName = '';

        function createSnowflakes() {
            for (let i = 0; i < 180; i++) {
                const flake = document.createElement('div');
                flake.classList.add('snowflake');
                const size = Math.random() * 8 + 5;
                flake.style.width = flake.style.height = `${size}px`;
                flake.style.left = `${Math.random() * 100}vw`;
                flake.style.opacity = Math.random() * 0.7 + 0.3;
                const duration = Math.random() * 10 + 8;
                const delay = Math.random() * 5;
                flake.style.animation = `snowFall ${duration}s linear ${delay}s infinite`;
                snowContainer.appendChild(flake);
            }
        }

        function createLetterElements(container, text, isNameLine = false) {
            for (let i = 0; i < text.length; i++) {
                const char = text.charAt(i);
                if (char === ' ') {
                    const space = document.createElement('span');
                    space.className = 'space';
                    container.appendChild(space);
                } else {
                    const letter = document.createElement('span');
                    letter.className = 'letter';
                    letter.textContent = char.toUpperCase();
                    if (isNameLine) letter.classList.add('personal-name');
                    container.appendChild(letter);
                }
            }
        }

        function initGreetingLines() {
            const lines = [
                "MERRY CHRISTMAS!!!",
                userName.toUpperCase() + ",",
                "SANA MASARAP ANG NOCHE BUENA MOOO!"
            ];

            greetingText1.innerHTML = '';
            greetingText2.innerHTML = '';
            greetingText3.innerHTML = '';
            fromBins.style.opacity = '0';
            fromBins.style.transform = 'translateY(30px)';
            cursor.style.display = 'inline-block';

            createLetterElements(greetingText1, lines[0]);
            createLetterElements(greetingText2, lines[1], true);
            createLetterElements(greetingText3, lines[2]);
        }

        function startTypingAnimation() {
            const letters = document.querySelectorAll('.letter');
            let currentIndex = 0;

            function typeNextLetter() {
                if (currentIndex < letters.length) {
                    letters[currentIndex].style.animation = `letterAppear 0.6s forwards`;
                    currentIndex++;
                    setTimeout(typeNextLetter, 100);
                } else {
                    setTimeout(() => {
                        fromBins.style.animation = 'letterAppear 1.2s forwards';
                        cursor.style.display = 'none';
                    }, 800);
                }
            }
            typeNextLetter();
        }

        function handleNameSubmit() {
            userName = userNameInput.value.trim() || "Friend";
            nameScreen.style.opacity = '0';
            setTimeout(() => {
                nameScreen.style.display = 'none';
                cardContainer.classList.add('active');
                initGreetingLines();
                setTimeout(startTypingAnimation, 800);
            }, 800);
        }

        submitNameBtn.addEventListener('click', handleNameSubmit);
        userNameInput.addEventListener('keypress', e => { if (e.key === 'Enter') handleNameSubmit(); });

        document.addEventListener('DOMContentLoaded', () => {
            userNameInput.focus();
            createSnowflakes();
        });
    </script>
</body>
</html>
