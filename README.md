<html lang="te">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>పుట్టినరోజు శుభాకాంక్షలు!</title>
    <style>
        /* --- GLOBAL SETUP --- */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Arial, sans-serif;
        }

        body, html {
            overflow: hidden;
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: #0b0214;
        }

        /* --- IMMERSIVE FULL-PAGE VIDEO/BACKGROUND BACKDROP --- */
        .video-background {
            position: absolute;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: 1;
        }

        .video-background video {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        /* --- PREMIUM GLASS SLIDES --- */
        .page {
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 20px;
            z-index: 5;
            transition: opacity 0.6s ease-in-out, transform 0.6s ease-in-out;
        }

        .hidden {
            display: none !important;
            opacity: 0;
            transform: scale(0.9);
        }

        /* --- THEATRE CURTAINS (SLIDE OUT TO SIDES) --- */
        #page1 {
            background-color: transparent;
            z-index: 10;
        }

        .curtain-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            z-index: 12;
        }

        .curtain {
            width: 50%;
            height: 100%;
            background: linear-gradient(135deg, #70001d 0%, #d61c4e 50%, #70001d 100%);
            transition: transform 1.6s cubic-bezier(0.77, 0, 0.175, 1);
        }

        .curtain.left { transform-origin: left; border-right: 2px solid #ffb3c6; }
        .curtain.right { transform-origin: right; border-left: 2px solid #ffb3c6; }

        .open .curtain.left { transform: translateX(-100%); }
        .open .curtain.right { transform: translateX(100%); }

        .start-btn {
            position: absolute;
            z-index: 20;
            width: 120px;
            height: 120px;
            border-radius: 50%;
            border: 3px solid #fff;
            background: radial-gradient(circle, #ff4d94, #b30047);
            color: white;
            font-weight: bold;
            font-size: 18px;
            letter-spacing: 1px;
            cursor: pointer;
            box-shadow: 0 0 25px rgba(255, 77, 148, 0.8);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .start-btn:hover { 
            transform: scale(1.12); 
            box-shadow: 0 0 40px #ff4d94;
        }

        /* --- PREMIUM MODERN BUTTONS --- */
        .action-btn {
            margin-top: 35px;
            padding: 16px 40px;
            font-size: 18px;
            font-weight: 600;
            color: white;
            background: linear-gradient(45deg, #ff1a75, #ff75a3);
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 8px 25px rgba(255, 26, 117, 0.5);
            transition: all 0.3s ease;
        }

        .action-btn:hover {
            transform: translateY(-4px) scale(1.03);
            box-shadow: 0 12px 30px rgba(255, 26, 117, 0.7);
        }

        /* --- TEXT STYLING --- */
        .wishes-title {
            font-size: 3.2rem;
            color: #ffffff;
            margin-bottom: 25px;
            text-shadow: 0 4px 15px rgba(0, 0, 0, 0.6);
            font-weight: 700;
        }

        .glass-card {
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            padding: 30px 40px;
            border-radius: 24px;
            max-width: 650px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.3);
        }

        /* --- REVOLVING TEXT EFFECT (PAGE 2) --- */
        .revolve-container {
            perspective: 1000px;
            height: 100px;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 20px;
        }

        .wishes-text-revolve {
            font-size: 2rem;
            color: #ffffff;
            line-height: 1.6;
            animation: revolveY 6s linear infinite;
            transform-style: preserve-3d;
            display: inline-block;
        }

        @keyframes revolveY {
            0% { transform: rotateY(0deg); }
            100% { transform: rotateY(360deg); }
        }

        /* --- REVOLVING GIFT BOX ANIMATION (PAGE 3) --- */
        .gift-container {
            position: relative;
            width: 180px;
            height: 180px;
            cursor: pointer;
            animation: spinGift 4s linear infinite;
        }

        @keyframes spinGift {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .gift-box {
            width: 140px;
            height: 140px;
            background-color: #ff2a6d;
            position: absolute;
            bottom: 0;
            left: 20px;
            border-radius: 16px;
        }

        .gift-box::before {
            content: '';
            position: absolute;
            left: 60px;
            width: 20px;
            height: 100%;
            background-color: #ffee55;
        }

        .gift-lid {
            width: 160px;
            height: 38px;
            background-color: #d61c4e;
            position: absolute;
            top: 15px;
            left: 10px;
            z-index: 2;
            border-radius: 8px;
            box-shadow: 0 5px 8px rgba(0,0,0,0.35);
        }

        .gift-lid::before {
            content: '';
            position: absolute;
            left: 70px;
            width: 20px;
            height: 100%;
            background-color: #ffee55;
        }

        /* --- CRACKER FIREWORK PARTICLES --- */
        .spark {
            position: absolute;
            width: 6px;
            height: 6px;
            border-radius: 50%;
            pointer-events: none;
            animation: explodeCracker 1s ease-out forwards;
            z-index: 100;
        }

        @keyframes explodeCracker {
            0% {
                transform: translate(0, 0) scale(1);
                opacity: 1;
            }
            100% {
                transform: translate(var(--x), var(--y)) scale(0);
                opacity: 0;
            }
        }
    </style>
</head>
<body>

    <!-- VIDEO BACKGROUND CONTAINER -->
    <div class="video-background">
        <video id="bg-video" autoplay loop muted playsinline>
            <source src="https://assets.mixkit.co/videos/preview/mixkit-glamorous-glowing-gold-particles-32635-large.mp4" type="video/mp4">
        </video>
    </div>

    <!-- BACKGROUND MUSIC TRACK -->
    <audio id="birthday-audio" loop>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mp3">
    </audio>

    <!-- PAGE 1: Curtain Slider Screen -->
    <div id="page1" class="page">
        <div class="curtain-container" id="curtain-wrapper">
            <div class="curtain left"></div>
            <div class="curtain right"></div>
        </div>
        <button class="start-btn" id="start-btn">OPEN</button>
    </div>

    <!-- PAGE 2: Revolving Wishes Screen -->
    <div id="page2" class="page hidden">
        <h1 class="wishes-title">Happy Birthday! 🎂</h1>
        <div class="glass-card Revolve-container">
            <span class="wishes-text-revolve">Wishing my wonderful sister-in-law a spectacular year ahead! ✨</span>
        </div>
        <button class="action-btn" id="surprise-btn">Press for Surprise!</button>
    </div>

    <!-- PAGE 3: Revolving Gift Box & Crackers -->
    <div id="page3" class="page hidden">
        <h2 class="wishes-title" style="margin-bottom: 50px;">Tap the Gift Box! 🎁</h2>
        <div class="gift-container" id="gift-box">
            <div class="gift-lid"></div>
            <div class="gift-box"></div>
        </div>
        <button class="action-btn hidden" id="blessings-btn" style="margin-top: 50px;">Press for Blessings</button>
    </div>

    <!-- PAGE 4: Birthday Wishes in Native Telugu Script -->
    <div id="page4" class="page hidden">
        <h1 class="wishes-title">పుట్టినరోజు శుభాకాంక్షలు! 🎉</h1>
        <div class="glass-card" style="border-color: #ff75a3;">
            <p style="font-weight: bold; font-size: 1.9rem; color: #fffbdf; margin-bottom: 15px; line-height: 1.6;">
                సుమీకి హృదయపూర్వక పుట్టినరోజు శుభాకాంక్షలు! 💐
            </p>
            <p style="font-size: 1.5rem; color: #ffffff; opacity: 0.95; line-height: 1.6;">
                మీరు ఎల్లప్పుడూ ఆయురారోగ్యాలతో, సుఖసంతోషాలతో ఉండాలని ఆ దేవుడిని కోరుకుంటున్నాను. ఈ సంవత్సరం మీకు మరిన్ని విజయాలను అందించాలని ఆశిస్తున్నాను! 🌟✨
            </p>
        </div>
    </div>

    <script>
        const page1 = document.getElementById('page1');
        const page2 = document.getElementById('page2');
        const page3 = document.getElementById('page3');
        const page4 = document.getElementById('page4');
        const audio = document.getElementById('birthday-audio');

        // Step 1: Open Curtains Sideways
        document.getElementById('start-btn').addEventListener('click', function() {
            this.style.opacity = '0';
            this.style.transform = 'scale(0.5)';
            document.getElementById('curtain-wrapper').classList.add('open');
            
            setTimeout(() => {
                page1.classList.add('hidden');
                page2.classList.remove('hidden');
            }, 1600);
        });

        // Step 2: Move to Gift Box Page
        document.getElementById('surprise-btn').addEventListener('click', function() {
            page2.classList.add('hidden');
            page3.classList.remove('hidden');
        });

        // Step 3: Tap Gift Box -> Stop Rotation, Pop Crackers, Start Music
        const giftBox = document.getElementById('gift-box');
        const blessingsBtn = document.getElementById('blessings-btn');
        
        giftBox.addEventListener('click', function() {
            // Play audio setup
            audio.play().catch(e => console.log("Audio play initialized."));

            // Stop the container rotation
            giftBox.style.animation = 'none';

            // Fire crackling colorful firework sparks
            const colors = ['#ff0055', '#00ffcc', '#ffcc00', '#ff6600', '#cc00ff', '#ffffff'];
            for (let i = 0; i < 80; i++) {
                createSpark(colors[Math.floor(Math.random() * colors.length)]);
            }

            // Reveal the next step button
            blessingsBtn.classList.remove('hidden');
        });

        function createSpark(color) {
            const spark = document.createElement('div');
            spark.classList.add('spark');
            spark.style.backgroundColor = color;

            // Give random trajectories for the firecracker explosion
            const angle = Math.random() * Math.PI * 2;
            const distance = 100 + Math.random() * 250;
            const x = Math.cos(angle) * distance;
            const y = Math.sin(angle) * distance;

            spark.style.setProperty('--x', `${x}px`);
            spark.style.setProperty('--y', `${y}px`);
            spark.style.left = '50%';
            spark.style.top = '45%';

            page3.appendChild(spark);
            setTimeout(() => { spark.remove(); }, 1000);
        }

        // Step 4: Move to final Telugu wishes
        blessingsBtn.addEventListener('click', function() {
            page3.classList.add('hidden');
            page4.classList.remove('hidden');
        });
    </script>
</body>
</html>
