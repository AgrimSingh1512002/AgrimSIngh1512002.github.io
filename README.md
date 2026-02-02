<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Valentine's Day Special</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial Rounded MT Bold', 'Arial', sans-serif;
        }
        
        body {
            background-color: #ffe6e6;
            overflow-x: hidden;
            min-height: 100vh;
            position: relative;
        }
        
        /* Valentine's Day hearts background */
        .hearts-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }
        
        .heart {
            position: absolute;
            color: #ff4081;
            font-size: 24px;
            opacity: 0.7;
            animation: float 15s infinite linear;
        }
        
        .heart:nth-child(2n) {
            color: #ff1744;
            font-size: 32px;
            animation-duration: 12s;
        }
        
        .heart:nth-child(3n) {
            color: #f50057;
            font-size: 40px;
            animation-duration: 18s;
        }
        
        .heart:nth-child(4n) {
            color: #ff80ab;
            font-size: 28px;
            animation-duration: 20s;
        }
        
        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0.5;
            }
            25% {
                opacity: 0.9;
            }
            50% {
                opacity: 0.7;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }
        
        /* Main content */
        .container {
            position: relative;
            z-index: 2;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            text-align: center;
        }
        
        header {
            padding: 40px 20px;
            background: linear-gradient(135deg, #ff4081, #ff1744);
            border-radius: 20px;
            margin-bottom: 40px;
            box-shadow: 0 10px 30px rgba(255, 23, 68, 0.3);
            color: white;
            position: relative;
            overflow: hidden;
        }
        
        h1 {
            font-size: 4rem;
            margin-bottom: 20px;
            text-shadow: 3px 3px 0 #ff80ab;
            letter-spacing: 2px;
        }
        
        h2 {
            font-size: 2.5rem;
            margin-bottom: 30px;
            color: #ff1744;
            text-shadow: 2px 2px 0 #ffcdd2;
        }
        
        .tagline {
            font-size: 2.2rem;
            margin-bottom: 20px;
            color: #8b0000;
            font-weight: bold;
            text-shadow: 2px 2px 0 #ffcdd2;
            background-color: rgba(255, 255, 255, 0.7);
            display: inline-block;
            padding: 15px 30px;
            border-radius: 50px;
            border: 5px solid #ff4081;
            animation: glow 2s infinite alternate;
        }
        
        @keyframes glow {
            from {
                box-shadow: 0 0 10px #ff4081, 0 0 20px #ff4081;
            }
            to {
                box-shadow: 0 0 20px #ff4081, 0 0 30px #ff4081, 0 0 40px #ff4081;
            }
        }
        
        .message {
            font-size: 1.4rem;
            max-width: 800px;
            margin: 0 auto 40px;
            line-height: 1.6;
            color: #880e4f;
            background-color: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(136, 14, 79, 0.2);
        }
        
        /* Buttons section */
        .buttons-container {
            background-color: rgba(255, 255, 255, 0.9);
            padding: 40px;
            border-radius: 20px;
            margin: 40px auto;
            max-width: 800px;
            box-shadow: 0 10px 30px rgba(244, 67, 54, 0.3);
            position: relative;
            overflow: hidden;
            border: 8px solid #ff4081;
        }
        
        .buttons-title {
            font-size: 2.5rem;
            margin-bottom: 30px;
            color: #d81b60;
            text-shadow: 2px 2px 0 #f8bbd9;
        }
        
        .button-wrapper {
            display: flex;
            justify-content: center;
            gap: 40px;
            flex-wrap: wrap;
            margin-top: 40px;
            min-height: 150px;
        }
        
        /* Yes button - fixed */
        .yes-btn {
            background: linear-gradient(135deg, #4CAF50, #2E7D32);
            color: white;
            border: none;
            padding: 25px 60px;
            font-size: 2.5rem;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 10px 20px rgba(76, 175, 80, 0.4);
            transition: all 0.3s;
            font-weight: bold;
            position: fixed;
            bottom: 40px;
            right: 40px;
            z-index: 100;
            animation: pulse 2s infinite;
        }
        
        .yes-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 15px 30px rgba(76, 175, 80, 0.6);
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        /* No button - dodging */
        .no-btn {
            background: linear-gradient(135deg, #f44336, #c62828);
            color: white;
            border: none;
            padding: 25px 60px;
            font-size: 2.5rem;
            border-radius: 50px;
            cursor: not-allowed;
            box-shadow: 0 10px 20px rgba(244, 67, 54, 0.4);
            transition: all 0.1s;
            font-weight: bold;
            position: relative;
        }
        
        .no-btn:hover {
            cursor: not-allowed;
        }
        
        /* Counter and insults display */
        .counter-container {
            margin-top: 40px;
            padding: 20px;
            background: linear-gradient(135deg, #ffcdd2, #f8bbd9);
            border-radius: 15px;
            border: 5px dashed #ff4081;
        }
        
        .counter {
            font-size: 2rem;
            color: #d81b60;
            font-weight: bold;
            margin-bottom: 10px;
        }
        
        .insult {
            font-size: 1.8rem;
            color: #880e4f;
            font-weight: bold;
            min-height: 60px;
            padding: 10px;
            font-style: italic;
        }
        
        /* Footer */
        footer {
            margin-top: 60px;
            padding: 30px;
            background: linear-gradient(135deg, #ff4081, #d81b60);
            border-radius: 20px;
            color: white;
            font-size: 1.2rem;
        }
        
        .hearts-row {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 20px 0;
            font-size: 2rem;
        }
        
        /* Responsive design */
        @media (max-width: 768px) {
            h1 {
                font-size: 2.8rem;
            }
            
            h2 {
                font-size: 2rem;
            }
            
            .tagline {
                font-size: 1.8rem;
                padding: 10px 20px;
            }
            
            .yes-btn, .no-btn {
                padding: 20px 40px;
                font-size: 2rem;
            }
            
            .yes-btn {
                position: relative;
                bottom: auto;
                right: auto;
                margin-top: 20px;
            }
            
            .button-wrapper {
                flex-direction: column;
                align-items: center;
            }
        }
    </style>
</head>
<body>
    <!-- Background hearts -->
    <div class="hearts-container" id="heartsContainer"></div>
    
    <div class="container">
        <header>
            <h1><i class="fas fa-heart"></i> Happy Valentine's Day! <i class="fas fa-heart"></i></h1>
            <div class="tagline">Will you be my Valentine? 💖</div>
        </header>
        
        <section class="message">
            <p>I've created this colorful Valentine's Day experience to ask you the most important question...</p>
            <p>Will you make this Valentine's Day special by being mine? 💕</p>
        </section>
        
        <h2>So, what's your answer?</h2>
        
        <div class="buttons-container">
            <div class="buttons-title">Choose your response:</div>
            
            <div class="button-wrapper">
                <!-- No button that moves when hovered -->
                <button class="no-btn" id="noBtn">NO</button>
            </div>
            
            <div class="counter-container">
                <div class="counter" id="counter">No button dodged: 0 times</div>
                <div class="insult" id="insult">Try to click the NO button, I dare you! 😏</div>
            </div>
        </div>
        
        <!-- Yes button fixed at bottom right -->
        <button class="yes-btn" id="yesBtn">YES! 💖</button>
        
        <footer>
            <p>Remember: Love is the most beautiful feeling in the world! 💘</p>
            <div class="hearts-row">
                <i class="fas fa-heart" style="color: #ff4081;"></i>
                <i class="fas fa-heart" style="color: #ff1744;"></i>
                <i class="fas fa-heart" style="color: #f50057;"></i>
                <i class="fas fa-heart" style="color: #ff80ab;"></i>
                <i class="fas fa-heart" style="color: #ff4081;"></i>
            </div>
        </footer>
    </div>

    <script>
        // Create floating hearts
        const heartsContainer = document.getElementById('heartsContainer');
        const heartCount = 50;
        
        for (let i = 0; i < heartCount; i++) {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤';
            
            // Random position
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.top = Math.random() * 100 + 'vh';
            
            // Random animation delay
            heart.style.animationDelay = Math.random() * 15 + 's';
            
            heartsContainer.appendChild(heart);
        }
        
        // No button dodging functionality
        const noBtn = document.getElementById('noBtn');
        const counterDisplay = document.getElementById('counter');
        const insultDisplay = document.getElementById('insult');
        let dodgeCount = 0;
        
        // Indian Gen-Z insults array (without the removed slang)
        const indianGenZInsults = [
            "Bro, you're being so cringe! 🤦‍♂️",
            "Arey yaar, what is this simp behavior? 😂",
            "This is giving major L energy! 🚫",
            "Bhai, thoda self-respect rakho na! 👑",
            "You're acting like a typical 'chhapri'! 🛵",
            "This is so 'ulta pulta'! 🔄",
            "Bro, you're being 'extra' for no reason! 🌟",
            "Arey, stop being so 'sus'! 🕵️‍♂️",
            "This is giving me 'secondhand embarrassment'! 😳",
            "Bhai, you're 'doing the most'! 📈",
            "Stop being so 'boring' yaar! 😴",
            "You're giving 'NPC' vibes! 🤖",
            "Arey, what is this 'pagalpanti'? 🤪",
            "Bro, you're being 'lowkey problematic'! ⚠️",
            "This is not the 'vibe' bro! 🌪️",
            "You're acting like a 'noob'! 🎮",
            "Arey, stop with this 'bakchodi'! 🤡",
            "Bro, this is 'mid' at best! 😐",
            "You're being a total 'simp'! 🥺",
            "Arey, thoda 'rizz' dikhao na! 😎",
            "This is so 'cheap' bro! 💸",
            "You're giving 'ghatiya' energy! 📉",
            "Bro, you're 'literally' embarrassing yourself! 😬",
            "This is giving 'struggle' vibes! 💪",
            "You're acting like you've got 'no game'! 🎯",
            "Bro, this is so 'basic'! ☕",
            "Arey, you're being 'hella annoying'! 😠",
            "This is 'not it' bro! 👎",
            "You're giving 'main character syndrome'! 🎬",
            "Bhai, you're giving 'sasti copy' vibes! 📋"
        ];
        
        // Function to get a random Indian Gen-Z insult
        function getRandomIndianInsult() {
            return indianGenZInsults[Math.floor(Math.random() * indianGenZInsults.length)];
        }
        
        // Function to move the no button to a random position
        function moveNoButton() {
            const container = document.querySelector('.buttons-container');
            const containerRect = container.getBoundingClientRect();
            const buttonRect = noBtn.getBoundingClientRect();
            
            // Calculate max positions within the container
            const maxX = containerRect.width - buttonRect.width - 20;
            const maxY = containerRect.height - buttonRect.height - 20;
            
            // Generate random positions
            const randomX = Math.max(10, Math.random() * maxX);
            const randomY = Math.max(10, Math.random() * maxY);
            
            // Move the button
            noBtn.style.position = 'absolute';
            noBtn.style.left = randomX + 'px';
            noBtn.style.top = randomY + 'px';
            
            // Update counter and insult
            dodgeCount++;
            counterDisplay.textContent = `No button dodged: ${dodgeCount} time${dodgeCount !== 1 ? 's' : ''}`;
            insultDisplay.textContent = getRandomIndianInsult();
            
            // Add a fun effect for high dodge counts
            if (dodgeCount > 5) {
                noBtn.style.transform = `rotate(${Math.random() * 20 - 10}deg)`;
            }
            if (dodgeCount > 10) {
                const randomColor = `#${Math.floor(Math.random()*16777215).toString(16)}`;
                noBtn.style.background = `linear-gradient(135deg, #f44336, ${randomColor})`;
            }
        }
        
        // Add event listeners to make button dodge
        noBtn.addEventListener('mouseover', moveNoButton);
        noBtn.addEventListener('touchstart', function(e) {
            e.preventDefault();
            moveNoButton();
        });
        
        // Prevent clicking on the no button
        noBtn.addEventListener('click', function(e) {
            e.preventDefault();
            moveNoButton();
            
            // Shake animation when clicked
            noBtn.style.transform = 'translateX(10px) rotate(5deg)';
            setTimeout(() => {
                noBtn.style.transform = 'translateX(-10px) rotate(-5deg)';
            }, 50);
            setTimeout(() => {
                noBtn.style.transform = 'translateX(0) rotate(0deg)';
            }, 100);
        });
        
        // Yes button functionality
        const yesBtn = document.getElementById('yesBtn');
        yesBtn.addEventListener('click', function() {
            // Create a celebration effect
            document.body.style.background = "linear-gradient(135deg, #ff4081, #ffeb3b, #4CAF50)";
            
            // Change the header
            document.querySelector('h1').innerHTML = "YAY! You said YES! 💖💖💖";
            document.querySelector('.tagline').textContent = "You've made this the best Valentine's Day ever!";
            document.querySelector('.tagline').style.color = "#2E7D32";
            document.querySelector('.tagline').style.borderColor = "#4CAF50";
            document.querySelector('.tagline').style.animation = "none";
            document.querySelector('.tagline').style.boxShadow = "0 0 30px #4CAF50";
            
            // Create floating hearts celebration
            for (let i = 0; i < 30; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.classList.add('heart');
                    heart.innerHTML = '💖';
                    heart.style.left = Math.random() * 100 + 'vw';
                    heart.style.color = i % 2 === 0 ? '#4CAF50' : '#FFD700';
                    heart.style.fontSize = '48px';
                    heart.style.animationDuration = '5s';
                    
                    document.body.appendChild(heart);
                    
                    // Remove heart after animation
                    setTimeout(() => {
                        heart.remove();
                    }, 5000);
                }, i * 100);
            }
            
            // Show a message with Indian Gen-Z flair
            alert("🎉 Yayyy! You made the right choice bro! Happy Valentine's Day! 💘\n\nNow let's go on a date, my treat! 😎");
        });
    </script>
</body>
</html>
