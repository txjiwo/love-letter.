<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Love Letter to You</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Cormorant+Garamond:ital,wght@0,300;0,400;1,400&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #1a0a1a 0%, #2d1b2d 50%, #1a0a1a 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Cormorant Garamond', serif;
            overflow: hidden;
            position: relative;
        }
        
        /* Floating hearts background */
        .hearts-container {
            position: fixed;
            width: 100%;
            height: 100%;
            overflow: hidden;
            pointer-events: none;
            z-index: 1;
        }
        
        .heart {
            position: absolute;
            color: rgba(255, 107, 129, 0.3);
            font-size: 20px;
            animation: float 15s infinite linear;
            text-shadow: 0 0 10px rgba(255, 107, 129, 0.5);
        }
        
        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.6;
            }
            90% {
                opacity: 0.6;
            }
            100% {
                transform: translateY(-100vh) rotate(720deg);
                opacity: 0;
            }
        }
        
        /* Envelope styling */
        .envelope-container {
            position: relative;
            z-index: 10;
            perspective: 1000px;
        }
        
        .envelope {
            width: 320px;
            height: 200px;
            background: linear-gradient(145deg, #f4e4c1 0%, #e6d5b0 100%);
            position: relative;
            border-radius: 0 0 10px 10px;
            box-shadow: 
                0 10px 30px rgba(0,0,0,0.5),
                inset 0 -2px 10px rgba(0,0,0,0.1);
            cursor: pointer;
            transition: transform 0.6s ease;
            transform-style: preserve-3d;
        }
        
        .envelope:hover {
            transform: translateY(-5px) scale(1.02);
        }
        
        .envelope.open {
            transform: rotateX(180deg);
            opacity: 0;
            pointer-events: none;
        }
        
        .envelope-flap {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 50%;
            background: linear-gradient(145deg, #e6d5b0 0%, #d4c4a0 100%);
            clip-path: polygon(0 0, 50% 100%, 100% 0);
            transform-origin: top;
            transition: transform 0.6s ease;
            z-index: 2;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .envelope.open .envelope-flap {
            transform: rotateX(180deg);
        }
        
        .envelope-body {
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(145deg, #f4e4c1 0%, #e6d5b0 100%);
            border-radius: 0 0 10px 10px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .wax-seal {
            width: 50px;
            height: 50px;
            background: radial-gradient(circle at 30% 30%, #ff6b81, #c9184a);
            border-radius: 50%;
            position: relative;
            box-shadow: 
                0 3px 10px rgba(0,0,0,0.3),
                inset 0 -2px 5px rgba(0,0,0,0.2);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            color: white;
            text-shadow: 0 1px 2px rgba(0,0,0,0.3);
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }
        
        .wax-seal::before {
            content: '♥';
        }
        
        .click-hint {
            position: absolute;
            bottom: -40px;
            width: 100%;
            text-align: center;
            color: rgba(255,255,255,0.7);
            font-size: 14px;
            letter-spacing: 2px;
            text-transform: uppercase;
            animation: fadeInOut 2s infinite;
        }
        
        @keyframes fadeInOut {
            0%, 100% { opacity: 0.4; }
            50% { opacity: 1; }
        }
        
        /* Letter styling */
        .letter {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0.1);
            width: 90%;
            max-width: 600px;
            max-height: 80vh;
            background: 
                linear-gradient(to bottom, rgba(255,255,255,0.95), rgba(255,250,240,0.95)),
                url("data:image/svg+xml,%3Csvg width='100' height='100' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M11 18c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm48 25c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm-43-7c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm63 31c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM34 90c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm56-76c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM12 86c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm28-65c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm23-11c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-6 60c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm29 22c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zM32 63c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm57-13c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-9-21c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM60 91c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM35 41c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM12 60c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2z' fill='%23d4af37' fill-opacity='0.03' fill-rule='evenodd'/%3E%3C/svg%3E");
            padding: 50px;
            border-radius: 5px;
            box-shadow: 
                0 20px 60px rgba(0,0,0,0.4),
                0 0 0 1px rgba(212, 175, 55, 0.3);
            opacity: 0;
            transition: all 1s ease;
            overflow-y: auto;
            z-index: 20;
        }
        
        .letter.show {
            transform: translate(-50%, -50%) scale(1);
            opacity: 1;
        }
        
        .letter-header {
            text-align: center;
            margin-bottom: 30px;
            border-bottom: 2px solid #d4af37;
            padding-bottom: 20px;
        }
        
        .letter h1 {
            font-family: 'Dancing Script', cursive;
            font-size: 3em;
            color: #8b2635;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }
        
        .letter-date {
            font-style: italic;
            color: #666;
            font-size: 0.9em;
        }
        
        .letter-content {
            font-size: 1.2em;
            line-height: 1.8;
            color: #333;
            margin-bottom: 30px;
            text-align: justify;
        }
        
        .letter-content p {
            margin-bottom: 20px;
            text-indent: 2em;
        }
        
        .letter-content p:first-child::first-letter {
            font-size: 3em;
            float: left;
            line-height: 0.8;
            margin-right: 8px;
            color: #8b2635;
            font-family: 'Dancing Script', cursive;
        }
        
        .letter-signature {
            text-align: right;
            margin-top: 40px;
            font-family: 'Dancing Script', cursive;
            font-size: 2em;
            color: #8b2635;
        }
        
        .close-btn {
            position: absolute;
            top: 20px;
            right: 20px;
            width: 40px;
            height: 40px;
            background: rgba(139, 38, 53, 0.1);
            border: 2px solid #8b2635;
            border-radius: 50%;
            cursor: pointer;
            font-size: 20px;
            color: #8b2635;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .close-btn:hover {
            background: #8b2635;
            color: white;
            transform: rotate(90deg);
        }
        
        /* Sparkle effect */
        .sparkle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: white;
            border-radius: 50%;
            animation: sparkle 3s infinite;
        }
        
        @keyframes sparkle {
            0%, 100% { opacity: 0; transform: scale(0); }
            50% { opacity: 1; transform: scale(1); }
        }
        
        /* Typewriter cursor */
        .typewriter p {
            overflow: hidden;
            border-right: 2px solid #8b2635;
            white-space: nowrap;
            animation: typing 3.5s steps(40, end), blink-caret 0.75s step-end infinite;
        }
        
        @keyframes blink-caret {
            from, to { border-color: transparent }
            50% { border-color: #8b2635; }
        }
        
        /* Responsive */
        @media (max-width: 600px) {
            .envelope {
                width: 280px;
                height: 175px;
            }
            .letter {
                padding: 30px 20px;
                width: 95%;
            }
            .letter h1 {
                font-size: 2em;
            }
            .letter-content {
                font-size: 1em;
            }
        }
    </style>
</head>
<body>
    <!-- Floating hearts background -->
    <div class="hearts-container" id="heartsContainer"></div>
    
    <!-- Sparkles -->
    <div class="sparkle" style="top: 20%; left: 10%; animation-delay: 0s;"></div>
    <div class="sparkle" style="top: 60%; left: 80%; animation-delay: 1s;"></div>
    <div class="sparkle" style="top: 40%; left: 90%; animation-delay: 2s;"></div>
    <div class="sparkle" style="top: 80%; left: 20%; animation-delay: 1.5s;"></div>
    <div class="sparkle" style="top: 30%; left: 70%; animation-delay: 0.5s;"></div>
    
    <!-- Envelope -->
    <div class="envelope-container">
        <div class="envelope" id="envelope">
            <div class="envelope-flap"></div>
            <div class="envelope-body">
                <div class="wax-seal"></div>
            </div>
        </div>
        <div class="click-hint">Click to open</div>
    </div>
    
    <!-- Letter -->
    <div class="letter" id="letter">
        <button class="close-btn" onclick="closeLetter()">×</button>
        <div class="letter-header">
            <h1>My Dearest Love</h1>
            <div class="letter-date">April 07, 2026</div>
        </div>
        <div class="letter-content">
            <p>happy 2nd monthsary, my love. two months with you and I still catch myself smiling at my phone like an idiot when your name pops up.</p>
            
            <p>these past sixty days have been the best kind of chaos--random memes that only we understand, and that comfortable silence that somehow says everything. you've become my favorite notification, my favorite person, my favorite everything. hindi ko alam how I got this lucky, pero sobrang grateful ako.

</p>
            
            <p>I didn't expect you. I didn't expect to find someone who gets my weird, who matches my energy, who makes 'boring' feel like home--but here you are. thank you for your patience with my mood swings, for making me feel loved even on my worst days, and for choosing me over and over again. you make life better just by being in it.</p>
            
            <p>I don't say it enough, pero you mean the world to me. you're my answered prayer, my comfort, and my biggest blessing. kahit sa simpleng bagay, you never fail to make me feel seen, valued, and appreciated.</p>
            
            <p>I love you so much, baby. happy 2nd monthsary sa atin. 💕</p>
        </div>
        <div class="letter-signature">
            Yours eternally,<br>
            <span style="font-size: 0.8em;">Your Devoted</span>
        </div>
    </div>

    <script>
        // Generate floating hearts
        const heartsContainer = document.getElementById('heartsContainer');
        const heartSymbols = ['♥', '♡', '💕', '💖', '💗'];
        
        function createHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = heartSymbols[Math.floor(Math.random() * heartSymbols.length)];
            heart.style.left = Math.random() * 100 + '%';
            heart.style.animationDuration = (Math.random() * 10 + 10) + 's';
            heart.style.animationDelay = Math.random() * 5 + 's';
            heart.style.fontSize = (Math.random() * 20 + 15) + 'px';
            heartsContainer.appendChild(heart);
            
            setTimeout(() => {
                heart.remove();
                
            }, 20000);
        }
        
        // Create initial hearts
        for(let i = 0; i < 15; i++) {
            setTimeout(createHeart, i * 300);
        }
        
        // Continue creating hearts
        setInterval(createHeart, 2000);
        
        // Envelope interaction
        const envelope = document.getElementById('envelope');
        const letter = document.getElementById('letter');
        
        envelope.addEventListener('click', function() {
            envelope.classList.add('open');
            setTimeout(() => {
                letter.classList.add('show');
            }, 300);
        });
        
        function closeLetter() {
            letter.classList.remove('show');
            setTimeout(() => {
                envelope.classList.remove('open');
            }, 300);
        }
        
        // Add subtle parallax effect
        document.addEventListener('mousemove', (e) => {
            const x = (window.innerWidth - e.pageX) / 50;
            const y = (window.innerHeight - e.pageY) / 50;
            
            envelope.style.transform = `translateX(${x}px) translateY(${y}px)`;
        });
        
        // Prevent right-click on envelope to maintain mystery
        envelope.addEventListener('contextmenu', (e) => {
            e.preventDefault();
        });
    </script>
</body>
</html>:
