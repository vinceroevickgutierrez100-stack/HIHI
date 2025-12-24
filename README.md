<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Merry Christmas YA - Typing Animation</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Mountains+of+Christmas:wght@700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(180deg, #0a3d2f 0%, #0d5b3f 30%, #0a3d2f 100%);
            color: white;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            position: relative;
        }

        /* Snowflakes */
        .snowflake {
            position: absolute;
            background-color: white;
            border-radius: 50%;
            opacity: 0.8;
            top: -10px;
            z-index: 1;
        }

        /* Christmas lights */
        .lights {
            position: absolute;
            top: 20px;
            width: 100%;
            height: 30px;
            display: flex;
            justify-content: center;
            z-index: 2;
        }

        .light {
            width: 20px;
            height: 20px;
            border-radius: 50%;
            margin: 0 10px;
            animation: twinkle 1.5s infinite alternate;
            position: relative;
        }

        .light::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 50%;
            transform: translateX(-50%);
            width: 2px;
            height: 15px;
            background-color: #333;
        }

        .light:nth-child(1) { background-color: #ff0000; animation-delay: 0s; }
        .light:nth-child(2) { background-color: #00ff00; animation-delay: 0.2s; }
        .light:nth-child(3) { background-color: #ffff00; animation-delay: 0.4s; }
        .light:nth-child(4) { background-color: #ff00ff; animation-delay: 0.6s; }
        .light:nth-child(5) { background-color: #00ffff; animation-delay: 0.8s; }
        .light:nth-child(6) { background-color: #ff8800; animation-delay: 1s; }
        .light:nth-child(7) { background-color: #8800ff; animation-delay: 1.2s; }

        /* Main container */
        .container {
            text-align: center;
            max-width: 1200px;
            width: 100%;
            padding: 40px 20px;
            z-index: 10;
            position: relative;
        }

        /* Christmas tree */
        .tree {
            position: absolute;
            bottom: 0;
            width: 150px;
            height: 200px;
            z-index: 5;
        }

        .tree-left {
            left: 50px;
        }

        .tree-right {
            right: 50px;
        }

        .tree-body {
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 0;
            border-left: 50px solid transparent;
            border-right: 50px solid transparent;
            border-bottom: 100px solid #0a7e3a;
        }

        .tree-body:nth-child(1) {
            bottom: 0;
            border-bottom-color: #0a7e3a;
        }

        .tree-body:nth-child(2) {
            bottom: 30px;
            width: 0;
            height: 0;
            border-left: 40px solid transparent;
            border-right: 40px solid transparent;
            border-bottom: 80px solid #0b8c42;
        }

        .tree-body:nth-child(3) {
            bottom: 60px;
            width: 0;
            height: 0;
            border-left: 30px solid transparent;
            border-right: 30px solid transparent;
            border-bottom: 60px solid #0c9a4a;
        }

        .tree-trunk {
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 20px;
            height: 30px;
            background-color: #8B4513;
        }

        /* Animated text container */
        .text-container {
            background: rgba(0, 0, 0, 0.7);
            border-radius: 20px;
            padding: 40px 30px;
            margin: 0 auto 50px;
            max-width: 900px;
            border: 8px solid #b22222;
            box-shadow: 
                0 0 30px rgba(255, 50, 50, 0.7),
                inset 0 0 30px rgba(255, 200, 0, 0.3);
            position: relative;
            overflow: hidden;
        }

        .text-container::before {
            content: '';
            position: absolute;
            top: -10px;
            left: -10px;
            right: -10px;
            bottom: -10px;
            background: linear-gradient(45deg, #ff0000, #ff9900, #ffff00, #00ff00, #00ffff, #0000ff, #9900ff);
            background-size: 400% 400%;
            z-index: -1;
            border-radius: 25px;
            animation: borderGlow 6s ease infinite;
            filter: blur(15px);
            opacity: 0.7;
        }

        /* Typing text */
        .typing-text {
            font-family: 'Mountains of Christmas', cursive;
            font-size: 5.5rem;
            color: #fff;
            text-shadow: 
                0 0 10px #ff0000,
                0 0 20px #ff9900,
                0 0 30px #ffff00;
            margin-bottom: 30px;
            height: 120px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .letter {
            display: inline-block;
            opacity: 0;
            transform: translateY(30px);
            animation: appear 0.5s forwards;
        }

        .space {
            width: 30px;
            display: inline-block;
        }

        /* Cursor */
        .cursor {
            display: inline-block;
            width: 4px;
            height: 80px;
            background-color: #ffcc00;
            margin-left: 5px;
            animation: blink 1s infinite;
            vertical-align: middle;
        }

        /* Decorative elements */
        .holly {
            position: absolute;
            width: 60px;
            height: 60px;
            z-index: 10;
        }

        .holly-left {
            top: 20px;
            left: 20px;
        }

        .holly-right {
            bottom: 20px;
            right: 20px;
        }

        .holly-leaf {
            position: absolute;
            width: 30px;
            height: 30px;
            background-color: #0a7e3a;
            border-radius: 50% 0;
            transform: rotate(45deg);
        }

        .holly-leaf:nth-child(2) {
            left: 20px;
            top: 5px;
            transform: rotate(0deg);
        }

        .holly-leaf:nth-child(3) {
            left: 10px;
            top: 25px;
            transform: rotate(90deg);
        }

        .holly-berry {
            position: absolute;
            width: 15px;
            height: 15px;
            background-color: #ff0000;
            border-radius: 50%;
            top: 20px;
            left: 20px;
            box-shadow: 0 0 10px #ff0000;
        }

        /* Controls */
        .controls {
            background: rgba(0, 0, 0, 0.6);
            border-radius: 15px;
            padding: 25px;
            max-width: 500px;
            margin: 0 auto;
            border: 3px solid #b22222;
        }

        .controls h3 {
            font-family: 'Mountains of Christmas', cursive;
            font-size: 2.5rem;
            margin-bottom: 20px;
            color: #ffcc00;
        }

        .button-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }

        button {
            background: linear-gradient(to bottom, #b22222, #8b0000);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 50px;
            font-size: 1.2rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            font-family: 'Poppins', sans-serif;
            display: flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }

        button:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.4);
            background: linear-gradient(to bottom, #ff0000, #b22222);
        }

        /* Footer */
        footer {
            position: absolute;
            bottom: 20px;
            width: 100%;
            text-align: center;
            color: #ffcc00;
            font-size: 1.1rem;
            z-index: 10;
        }

        /* Animations */
        @keyframes appear {
            to {
                opacity: 1;
                transform: translateY(0) rotateY(0);
            }
        }

        @keyframes blink {
            0%, 50% { opacity: 1; }
            51%, 100% { opacity: 0; }
        }

        @keyframes twinkle {
            0% { opacity: 0.3; transform: scale(0.8); }
            100% { opacity: 1; transform: scale(1.1); }
        }

        @keyframes borderGlow {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .typing-text {
                font-size: 3.5rem;
                height: 80px;
            }
            
            .text-container {
                padding: 30px 20px;
                margin-bottom: 30px;
            }
            
            .tree {
                width: 100px;
                height: 150px;
            }
            
            .tree-left {
                left: 20px;
            }
            
            .tree-right {
                right: 20px;
            }
            
            .light {
                width: 15px;
                height: 15px;
                margin: 0 5px;
            }
        }

        @media (max-width: 480px) {
            .typing-text {
                font-size: 2.5rem;
                height: 60px;
            }
            
            .cursor {
                height: 50px;
            }
            
            .controls h3 {
                font-size: 2rem;
            }
            
            button {
                padding: 12px 20px;
                font-size: 1rem;
            }
            
            .button-container {
                flex-direction: column;
                align-items: center;
            }
        }
    </style>
</head>
<body>
    <!-- Christmas Lights -->
    <div class="lights">
        <div class="light"></div>
        <div class="light"></div>
        <div class="light"></div>
        <div class="light"></div>
        <div class="light"></div>
        <div class="light"></div>
        <div class="light"></div>
    </div>

    <!-- Christmas Trees -->
    <div class="tree tree-left">
        <div class="tree-body"></div>
        <div class="tree-body"></div>
        <div class="tree-body"></div>
        <div class="tree-trunk"></div>
    </div>

    <div class="tree tree-right">
        <div class="tree-body"></div>
        <div class="tree-body"></div>
        <div class="tree-body"></div>
        <div class="tree-trunk"></div>
    </div>

    <!-- Main Content -->
    <div class="container">
        <div class="text-container">
            <!-- Holly decorations -->
            <div class="holly holly-left">
                <div class="holly-leaf"></div>
                <div class="holly-leaf"></div>
                <div class="holly-leaf"></div>
                <div class="holly-berry"></div>
            </div>
            
            <div class="holly holly-right">
                <div class="holly-leaf"></div>
                <div class="holly-leaf"></div>
                <div class="holly-leaf"></div>
                <div class="holly-berry"></div>
            </div>
            
            <!-- Animated Text -->
            <div class="typing-text" id="typing-text">
                <!-- Letters will be added by JavaScript -->
            </div>
            <div class="cursor" id="cursor"></div>
        </div>

        <!-- Controls -->
        <div class="controls">
            <h3>Animation Controls</h3>
            <div class="button-container">
                <button id="start-btn">
                    <i class="fas fa-play"></i> Start Animation
                </button>
                <button id="reset-btn">
                    <i class="fas fa-redo"></i> Reset Animation
                </button>
                <button id="speed-up-btn">
                    <i class="fas fa-tachometer-alt"></i> Speed Up
                </button>
                <button id="slow-down-btn">
                    <i class="fas fa-tachometer-alt"></i> Slow Down
                </button>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <p>Wishing you a magical Christmas season! 🎄✨</p>
    </footer>

    <script>
        // Text to be animated
        const message = "Merry Christmas YA!";
        let typingSpeed = 150; // milliseconds between letters
        let animationTimeout;
        let currentLetterIndex = 0;
        
        // DOM elements
        const typingText = document.getElementById('typing-text');
        const cursor = document.getElementById('cursor');
        const startBtn = document.getElementById('start-btn');
        const resetBtn = document.getElementById('reset-btn');
        const speedUpBtn = document.getElementById('speed-up-btn');
        const slowDownBtn = document.getElementById('slow-down-btn');
        
        // Initialize the page with empty text container
        function init() {
            clearTimeout(animationTimeout);
            currentLetterIndex = 0;
            typingText.innerHTML = '';
            cursor.style.visibility = 'visible';
            
            // Create a span for each letter in the message
            for (let i = 0; i < message.length; i++) {
                const char = message.charAt(i);
                const span = document.createElement('span');
                
                if (char === ' ') {
                    span.className = 'space';
                    span.innerHTML = '&nbsp;';
                } else {
                    span.className = 'letter';
                    span.textContent = char;
                    span.style.animationDelay = `${i * typingSpeed}ms`;
                }
                
                typingText.appendChild(span);
            }
        }
        
        // Start the typing animation
        function startAnimation() {
            resetAnimation(); // Reset first
            cursor.style.visibility = 'visible';
            
            const letters = document.querySelectorAll('.letter');
            
            function typeNextLetter() {
                if (currentLetterIndex < letters.length) {
                    // Make the current letter visible with animation
                    letters[currentLetterIndex].style.animation = `appear 0.5s forwards`;
                    
                    // Add a slight bounce effect for certain letters
                    if (message[currentLetterIndex] === '!') {
                        letters[currentLetterIndex].style.animation = `appear 0.5s forwards, float 1s 0.5s infinite`;
                    }
                    
                    currentLetterIndex++;
                    animationTimeout = setTimeout(typeNextLetter, typingSpeed);
                } else {
                    // Animation complete - make cursor blink faster
                    cursor.style.animation = 'blink 0.5s infinite';
                }
            }
            
            typeNextLetter();
            startBtn.disabled = true;
            setTimeout(() => startBtn.disabled = false, message.length * typingSpeed + 1000);
        }
        
        // Reset the animation
        function resetAnimation() {
            clearTimeout(animationTimeout);
            currentLetterIndex = 0;
            cursor.style.animation = 'blink 1s infinite';
            
            const letters = document.querySelectorAll('.letter');
            letters.forEach(letter => {
                letter.style.animation = 'none';
                // Trigger reflow to reset animation
                void letter.offsetWidth;
            });
            
            startBtn.disabled = false;
        }
        
        // Speed up the animation
        function speedUp() {
            if (typingSpeed > 50) {
                typingSpeed -= 30;
                resetAnimation();
                updateSpeedButtons();
            }
        }
        
        // Slow down the animation
        function slowDown() {
            if (typingSpeed < 500) {
                typingSpeed += 30;
                resetAnimation();
                updateSpeedButtons();
            }
        }
        
        // Update button states based on current speed
        function updateSpeedButtons() {
            speedUpBtn.disabled = typingSpeed <= 50;
            slowDownBtn.disabled = typingSpeed >= 500;
            
            speedUpBtn.innerHTML = `<i class="fas fa-tachometer-alt"></i> Speed Up (${typingSpeed}ms)`;
            slowDownBtn.innerHTML = `<i class="fas fa-tachometer-alt"></i> Slow Down (${typingSpeed}ms)`;
        }
        
        // Create snowflakes
        function createSnowflakes() {
            const snowflakeCount = 100;
            
            for (let i = 0; i < snowflakeCount; i++) {
                const snowflake = document.createElement('div');
                snowflake.classList.add('snowflake');
                
                // Random size
                const size = Math.random() * 5 + 3;
                snowflake.style.width = `${size}px`;
                snowflake.style.height = `${size}px`;
                
                // Random position
                snowflake.style.left = `${Math.random() * 100}vw`;
                
                // Random opacity
                snowflake.style.opacity = Math.random() * 0.5 + 0.3;
                
                // Random animation
                const duration = Math.random() * 10 + 5;
                const delay = Math.random() * 5;
                snowflake.style.animation = `fall ${duration}s linear ${delay}s infinite`;
                
                // Add to body
                document.body.appendChild(snowflake);
                
                // Add CSS for falling animation
                if (!document.querySelector('#snowfall-style')) {
                    const style = document.createElement('style');
                    style.id = 'snowfall-style';
                    style.textContent = `
                        @keyframes fall {
                            0% { transform: translateY(-10px) rotate(0deg); }
                            100% { transform: translateY(100vh) rotate(360deg); }
                        }
                    `;
                    document.head.appendChild(style);
                }
            }
        }
        
        // Event listeners
        startBtn.addEventListener('click', startAnimation);
        resetBtn.addEventListener('click', resetAnimation);
        speedUpBtn.addEventListener('click', speedUp);
        slowDownBtn.addEventListener('click', slowDown);
        
        // Initialize on page load
        window.addEventListener('load', () => {
            init();
            createSnowflakes();
            updateSpeedButtons();
            
            // Auto-start animation after a short delay
            setTimeout(startAnimation, 1000);
        });
        
        // Add keyboard controls
        document.addEventListener('keydown', (e) => {
            switch(e.key) {
                case ' ':
                case 'Enter':
                    e.preventDefault();
                    startAnimation();
                    break;
                case 'r':
                case 'R':
                    resetAnimation();
                    break;
                case '+':
                case '=':
                    speedUp();
                    break;
                case '-':
                case '_':
                    slowDown();
                    break;
            }
        });
    </script>
</body>
</html>
