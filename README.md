# hhjkinkuiywrnu-nu
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Bhonduu 🐼</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@300;400;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #ff0080;
            --secondary: #7928ca;
            --accent: #00dfd8;
        }

        * { box-sizing: border-box; }

        body, html {
            margin: 0; padding: 0;
            height: 100%;
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
            background-size: 400% 400%;
            animation: gradientBG 15s ease infinite;
            overflow: hidden;
            color: white;
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .page {
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100vh;
            display: none;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 20px;
            text-align: center;
        }

        .active { display: flex; animation: pageEnter 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275); }

        @keyframes pageEnter {
            from { opacity: 0; transform: scale(0.8) rotate(5deg); }
            to { opacity: 1; transform: scale(1) rotate(0deg); }
        }

        /* Glass Cards */
        .card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            border-radius: 30px;
            padding: 30px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 20px 50px rgba(0,0,0,0.3);
            max-width: 400px;
            width: 90%;
        }

        /* Crazy Animations */
        .photo-crazy {
            width: 250px;
            height: 250px;
            object-fit: cover;
            border-radius: 20px;
            border: 5px solid white;
            animation: jitter 0.5s infinite alternate, neon Glow 2s infinite alternate;
        }

        @keyframes jitter {
            0% { transform: rotate(-2deg) scale(1); }
            100% { transform: rotate(2deg) scale(1.05); }
        }

        @keyframes neonGlow {
            from { box-shadow: 0 0 10px var(--primary); }
            to { box-shadow: 0 0 30px var(--accent); }
        }

        /* Explosion Effect */
        .gift-box {
            font-size: 100px;
            cursor: pointer;
            transition: 0.3s;
        }

        .explode {
            animation: explodeOut 0.5s forwards;
        }

        @keyframes explodeOut {
            0% { transform: scale(1); opacity: 1; }
            50% { transform: scale(3); opacity: 0.5; filter: blur(10px); }
            100% { transform: scale(0); opacity: 0; }
        }

        button {
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 50px;
            font-weight: 800;
            cursor: pointer;
            margin-top: 20px;
            text-transform: uppercase;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }

        input {
            padding: 12px;
            border-radius: 10px;
            border: none;
            margin-bottom: 10px;
            width: 80%;
            text-align: center;
        }

        h1 { font-family: 'Dancing Script', cursive; font-size: 2.5rem; }
    </style>
</head>
<body>

    <audio id="bg-music" loop>
        <source src="https://www.image2url.com/r2/default/audio/1776595072381-84f4eea9-8bdd-4f8d-8d0d-b333df818616.wav" type="audio/mpeg">
    </audio>

    <div id="anime-layer"></div>

    <!-- PAGE 1: PASSWORD -->
    <div class="page active" id="page1">
        <div class="card">
            <h1>Unlock the Magic 🐼</h1>
            <input type="password" id="pass" placeholder="Enter secret code...">
            <button onclick="checkPassword()">Open 🔑</button>
        </div>
    </div>

    <!-- PAGE 2: GIFT EXPLOSION -->
    <div class="page" id="page2">
        <h1 id="gift-header">Tap the gift! 🎁</h1>
        <div class="gift-box" id="box" onclick="explodeGift()">🎁</div>
        <div id="gift-result" style="display:none;">
            <img src="https://i.postimg.cc/DyvVSk8V/Whats-App-Image-2026-04-19-at-13-46-16.jpg" class="photo-crazy">
            <br>
            <button onclick="nextPage(3)">Go to Next Page →</button>
        </div>
    </div>

    <!-- PAGE 3: LOVE YOU + CRAZY PHOTO -->
    <div class="page" id="page3">
        <h1 style="font-size: 4rem; color: #fff; text-shadow: 0 0 20px #ff0080;">LOVE YOU! ❤️</h1>
        <img src="https://i.postimg.cc/gcKQFS45/Whats-App-Image-2026-04-19-at-13-51-57.jpg" class="photo-crazy" style="animation-duration: 0.2s;">
        <p>You're the bestest ever!</p>
        <button onclick="nextPage(4)">Read My Note ✉️</button>
    </div>

    <!-- PAGE 4: FINAL NOTE + PHOTO -->
    <div class="page" id="page4">
        <div class="card">
            <img src="https://i.postimg.cc/Y28ny4C0/Whats-App-Image-2026-04-17-at-14-29-00.jpg" style="width:100%; border-radius:15px;">
            <p><strong>Happy Birthday Bhondu!</strong></p>
            <p>I promise to stay by your side forever. Keep smiling because that's what makes my day! 🌸</p>
            <button onclick="location.reload()">Replay the Magic 🔄</button>
        </div>
    </div>

    <script>
        function checkPassword() {
            const p = document.getElementById('pass').value;
            const music = document.getElementById('bg-music');
            if(p.toLowerCase() === "panda") {
                music.play().catch(e => console.log("Music blocked by browser"));
                nextPage(2);
            } else {
                alert("Wrong password! 🐼");
            }
        }

        function nextPage(num) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            document.getElementById('page' + num).classList.add('active');
        }

        function explodeGift() {
            const box = document.getElementById('box');
            const result = document.getElementById('gift-result');
            const header = document.getElementById('gift-header');
            
            box.classList.add('explode');
            
            setTimeout(() => {
                box.style.display = 'none';
                header.innerText = "SURPRISE! 🎉";
                result.style.display = 'block';
                // Trigger extra emojis for explosion feel
                for(let i=0; i<20; i++) createEmoji();
            }, 500);
        }

        function createEmoji() {
            const emojis = ['❤️', '🐼', '✨', '🎈', '🍭', '🌸'];
            const e = document.createElement('div');
            e.innerHTML = emojis[Math.floor(Math.random() * emojis.length)];
            e.style.position = 'fixed';
            e.style.left = Math.random() * 100 + 'vw';
            e.style.top = '110vh';
            e.style.fontSize = (Math.random() * 30 + 20) + 'px';
            e.style.zIndex = '1000';
            e.style.transition = 'transform 4s linear, opacity 4s';
            document.body.appendChild(e);

            setTimeout(() => {
                e.style.transform = `translateY(-120vh) rotate(${Math.random() * 360}deg)`;
                e.style.opacity = '0';
            }, 100);
            setTimeout(() => e.remove(), 4000);
        }

        setInterval(createEmoji, 400);
    </script>
</body>
</html>
