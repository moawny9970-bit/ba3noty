<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>حكايتنا ❤️</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&family=Amiri:ital@1&display=swap');

        :root {
            --primary: #ff4d6d;
            --bg-pink: #fbc2eb;
            --bg-blue: #a6c1ee;
        }

        body {
            margin: 0;
            font-family: 'Cairo', sans-serif;
            background: linear-gradient(135deg, var(--bg-pink) 0%, var(--bg-blue) 100%);
            height: 100vh;
            overflow: hidden;
            color: #333;
        }

        /* 🎬 Loading - النقطة السوداء */
        #loading {
            position: fixed;
            inset: 0;
            background: #fff;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .black-hole {
            width: 20px;
            height: 20px;
            background: #000;
            border-radius: 50%;
            animation: expand 3s forwards ease-in-out;
        }

        @keyframes expand {
            0% { transform: scale(1); }
            50% { transform: scale(5); }
            100% { transform: scale(100); opacity: 0; visibility: hidden; }
        }

        /* 📱 Sections Layout */
        .section {
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            padding: 20px;
            text-align: center;
            animation: fadeIn 1s ease;
        }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        /* 🔐 Lock Screen */
        .keypad {
            display: grid;
            grid-template-columns: repeat(3, 80px);
            gap: 15px;
            margin-top: 20px;
        }

        .key {
            background: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 50%;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        #passDisplay {
            font-size: 32px;
            letter-spacing: 5px;
            color: #000;
            height: 40px;
            font-family: monospace;
        }

        /* ✍️ Typewriter Text */
        .typing-container {
            font-size: 24px;
            line-height: 1.6;
            max-width: 80%;
            color: #fff;
            text-shadow: 1px 1px 5px rgba(0,0,0,0.3);
        }

        /* 📖 3D Book */
        .book {
            width: 300px;
            height: 400px;
            perspective: 1000px;
        }

        .page {
            width: 100%;
            height: 100%;
            background: #fff;
            position: absolute;
            top: 0;
            left: 0;
            transform-origin: left;
            transition: transform 1s cubic-bezier(0.645, 0.045, 0.355, 1);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
            box-sizing: border-box;
            border: 1px solid #ddd;
            backface-visibility: hidden;
            border-radius: 0 15px 15px 0;
            box-shadow: 5px 5px 20px rgba(0,0,0,0.1);
        }

        .page.flipped { transform: rotateY(-160deg); }

        /* 💖 Heart Gallery */
        .heart-gallery {
            position: relative;
            width: 300px;
            height: 300px;
            margin-top: 20px;
        }

        .gallery-img {
            width: 80px; height: 80px;
            object-fit: cover;
            position: absolute;
            transition: 1s ease-in-out;
            border-radius: 10px;
            border: 3px solid white;
        }

        /* ⏳ Final Counter (Like Image) */
        .counter-card {
            background: #ffffffa1;
            padding: 30px;
            border-radius: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.05);
            width: 85%;
            max-width: 400px;
        }

        .grid-timer {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        .time-box {
            background: #fff;
            padding: 15px;
            border-radius: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }

        .time-box span { display: block; font-size: 28px; color: #ff4d6d; font-weight: bold; }
        .time-box label { font-size: 14px; color: #888; }

        .btn-love {
            background: #ff4d6d;
            color: white;
            border: none;
            padding: 15px 40px;
            border-radius: 50px;
            font-size: 18px;
            margin-top: 20px;
            cursor: pointer;
            transition: 0.3s;
        }

        .btn-love:active { transform: scale(0.9); }

        .heart-float {
            position: fixed;
            bottom: -50px;
            font-size: 20px;
            animation: floatUp 3s forwards linear;
        }

        @keyframes floatUp {
            to { transform: translateY(-100vh) translateX(50px); opacity: 0; }
        }
    </style>
</head>
<body>

<div id="loading"><div class="black-hole"></div></div>

<div id="lockSec" class="section" style="display: flex;">
    <h2 style="color:white">منورة يا ست البنات ❤️</h2>
    <p style="color:white">اكتبي التاريخ اللي بدأنا فيه</p>
    <div id="passDisplay"></div>
    <div class="keypad">
        <div class="key" onclick="press('1')">1</div><div class="key" onclick="press('2')">2</div><div class="key" onclick="press('3')">3</div>
        <div class="key" onclick="press('4')">4</div><div class="key" onclick="press('5')">5</div><div class="key" onclick="press('6')">6</div>
        <div class="key" onclick="press('7')">7</div><div class="key" onclick="press('8')">8</div><div class="key" onclick="press('9')">9</div>
        <div class="key" style="grid-column: 2" onclick="press('0')">0</div>
    </div>
</div>

<div id="typingSec" class="section">
    <div class="typing-container" id="typewriter"></div>
    <button class="btn-love" id="nextBtn" style="display:none;" onclick="goToBook()">شوفي اللي بعده 🙊</button>
</div>

<div id="bookSec" class="section">
    <div class="book" id="book">
        <div class="page" style="z-index: 4;">أول يوم شوفتك فيه، الدنيا نورت.. 🌸</div>
        <div class="page" style="z-index: 3;">ضحكتك كانت كفيلة تنسيني أي تعب.. ❤️</div>
        <div class="page" style="z-index: 2;">وعد مني، هفضل سندك وضهرك للأبد.. 💍</div>
        <div class="page" style="z-index: 1;">يلا نشوف صورنا؟ 😍</div>
    </div>
    <button class="btn-love" onclick="flipPage()">اقلبي الصفحة 📖</button>
</div>

<div id="photoSec" class="section">
    <h2 style="color:white">أحلى ذكرياتنا سوا</h2>
    <div class="heart-gallery" id="heartGallery">
        </div>
    <button class="btn-love" style="margin-top: 150px" onclick="goToCounter()">آخر حاجة بقا 🙈</button>
</div>

<div id="counterSec" class="section">
    <div class="counter-card">
        <h3 id="welcomeBack">⏳ بقالنا مع بعض</h3>
        <div class="grid-timer">
            <div class="time-box"><span id="days">0</span><label>يوم</label></div>
            <div class="time-box"><span id="hours">0</span><label>ساعة</label></div>
            <div class="time-box"><span id="mins">0</span><label>دقيقة</label></div>
            <div class="time-box"><span id="secs">0</span><label>ثانية</label></div>
        </div>
        <button class="btn-love" onclick="loveClick()">بتحبيني قد إيه؟</button>
        <div id="loveCount" style="margin-top:10px; font-weight:bold; color:var(--primary)">0 حب</div>
        <p id="loveMsg" style="font-size:14px; color:#666"></p>
    </div>
</div>

<script>
    const pass = "2024326";
    let input = "";

    // 1. Lock Logic
    function press(num) {
        input += num;
        document.getElementById('passDisplay').innerText = input;
        if (input.length === pass.length) {
            if (input === pass) {
                showSec('typingSec');
                startTyping();
            } else {
                alert("الباسورد غلط يا قمر 😏");
                input = "";
                document.getElementById('passDisplay').innerText = "";
            }
        }
    }

    // 2. Typing Logic
    const msg = "بصي يا ستي.. من يوم ما دخلتي حياتي وكل حاجة اتغيرت. بقيتي النفس اللي بتنفسه، والضحكة اللي بتطلع من القلب بجد. مش بس حبيبتي، أنتي أهلي وناسي وكل دنيتي.. بحبك حب ملوش آخر ❤️";
    function startTyping() {
        let i = 0;
        let speed = 70;
        function type() {
            if (i < msg.length) {
                document.getElementById('typewriter').innerHTML += msg.charAt(i);
                i++;
                setTimeout(type, speed);
            } else {
                document.getElementById('nextBtn').style.display = "block";
            }
        }
        type();
    }

    // 3. Book Logic
    let currentPage = 0;
    function flipPage() {
        const pages = document.querySelectorAll('.page');
        if (currentPage < pages.length) {
            pages[currentPage].classList.add('flipped');
            currentPage++;
        } else {
            showSec('photoSec');
            startHeartGallery();
        }
    }

    // 4. Heart Gallery
    function startHeartGallery() {
        const gallery = document.getElementById('heartGallery');
        const coords = [
            {t:0, l:110}, {t:0, l:190}, {t:50, l:60}, {t:50, l:240},
            {t:120, l:40}, {t:120, l:260}, {t:190, l:80}, {t:190, l:220},
            {t:250, l:150}
        ];
        
        coords.forEach((pos, index) => {
            setTimeout(() => {
                let img = document.createElement('img');
                img.src = `img${(index % 5) + 1}.jpg`; // غير أسماء الصور للي عندك
                img.className = 'gallery-img';
                img.style.top = pos.t + 'px';
                img.style.left = pos.l + 'px';
                gallery.appendChild(img);
                createHeart();
            }, index * 500);
        });
    }

    // 5. Counter & Love Button
    let loveScore = parseInt(localStorage.getItem('loveCount')) || 0;
    function loveClick() {
        loveScore++;
        localStorage.setItem('loveCount', loveScore);
        document.getElementById('loveCount').innerText = loveScore + " حب";
        
        let msgEl = document.getElementById('loveMsg');
        if(loveScore < 10) msgEl.innerText = "ده بس؟ زودي شوية 😏";
        else if(loveScore < 20) msgEl.innerText = "ماشي يا ست البنات.. كملي 😍";
        else if(loveScore < 50) msgEl.innerText = "أيوه كده.. غرقينا حب ❤️";
        else msgEl.innerText = "أنتي عديتي ليفل الوحش في الحب! 👑";
        
        createHeart();
    }

    function updateTimer() {
        const start = new Date("2024-03-26T00:00:00");
        const now = new Date();
        const diff = now - start;

        document.getElementById('days').innerText = Math.floor(diff / (1000*60*60*24));
        document.getElementById('hours').innerText = Math.floor((diff / (1000*60*60)) % 24);
        document.getElementById('mins').innerText = Math.floor((diff / (1000*60)) % 60);
        document.getElementById('secs').innerText = Math.floor((diff / 1000) % 60);
    }
    setInterval(updateTimer, 1000);

    // Helpers
    function showSec(id) {
        document.querySelectorAll('.section').forEach(s => s.style.display = 'none');
        document.getElementById(id).style.display = 'flex';
    }

    function createHeart() {
        const h = document.createElement('div');
        h.innerHTML = "❤️";
        h.className = "heart-float";
        h.style.left = Math.random() * 100 + "vw";
        document.body.appendChild(h);
        setTimeout(() => h.remove(), 3000);
    }

    function goToBook() { showSec('bookSec'); }
    function goToCounter() { showSec('counterSec'); }

    window.onload = () => {
        if(localStorage.getItem('visited')) {
            document.getElementById('welcomeBack').innerText = "وحشتيني.. بقالنا مع بعض:";
        }
        localStorage.setItem('visited', 'true');
    };
</script>
</body>
</html>

