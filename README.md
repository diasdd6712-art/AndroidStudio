<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Космос студенті</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: radial-gradient(ellipse at bottom, #1B2735 0%, #090A0F 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            position: relative;
        }

        /* Жұлдыздар фоны */
        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .star {
            position: absolute;
            width: 2px;
            height: 2px;
            background: white;
            border-radius: 50%;
            animation: twinkle 3s infinite;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0.3; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.5); }
        }

        /* Неон контейнер */
        .neon-box {
            background: rgba(20, 20, 40, 0.8);
            border: 2px solid #FF00FF;
            border-radius: 20px;
            padding: 50px;
            text-align: center;
            box-shadow: 
                0 0 20px #FF00FF,
                0 0 40px #FF00FF,
                inset 0 0 20px rgba(255, 0, 255, 0.1);
            position: relative;
            z-index: 10;
            backdrop-filter: blur(10px);
        }

        /* Планета иконка */
        .planet {
            width: 100px;
            height: 100px;
            background: linear-gradient(135deg, #FFD700 0%, #FF69B4 50%, #FF1493 100%);
            border-radius: 50%;
            margin: 0 auto 30px;
            box-shadow: 
                0 0 30px #FFD700,
                0 0 60px #FF69B4;
            position: relative;
            animation: rotate 10s linear infinite;
        }

        .planet::before {
            content: '';
            position: absolute;
            width: 140px;
            height: 30px;
            border: 3px solid rgba(255, 215, 0, 0.6);
            border-radius: 50%;
            top: 35px;
            left: -20px;
            transform: rotate(-20deg);
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        /* Неон батырма */
        .neon-btn {
            background: transparent;
            color: #00FFFF;
            border: 2px solid #00FFFF;
            padding: 20px 40px;
            font-size: 18px;
            font-weight: bold;
            border-radius: 50px;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 3px;
            transition: all 0.3s;
            box-shadow: 
                0 0 10px #00FFFF,
                inset 0 0 10px #00FFFF;
            text-shadow: 0 0 10px #00FFFF;
        }

        .neon-btn:hover {
            background: #00FFFF;
            color: #000;
            box-shadow: 
                0 0 30px #00FFFF,
                0 0 60px #00FFFF,
                inset 0 0 20px #00FFFF;
        }

        /* ҚЫЗҒЫЛТ САРЫ МӘТІН - НЕГІЗГІ ЕРЕКШЕЛІК */
        .cosmic-text {
            margin-top: 30px;
            font-size: 32px;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 5px;
            
            /* Қызғылт сары градиент */
            background: linear-gradient(
                45deg, 
                #FF0000 0%, 
                #FF7300 20%, 
                #FFFB00 40%, 
                #FF1493 60%, 
                #FFD700 80%, 
                #FF4500 100%
            );
            background-size: 200% 200%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            
            /* Жарқырау эффектісі */
            filter: drop-shadow(0 0 10px rgba(255, 215, 0, 0.8))
                    drop-shadow(0 0 20px rgba(255, 20, 147, 0.6));
            
            animation: 
                gradient-shift 3s ease infinite,
                pulse-glow 1.5s ease-in-out infinite alternate;
            
            opacity: 0;
            transform: translateY(30px) scale(0.8);
            transition: all 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
        }

        .cosmic-text.show {
            opacity: 1;
            transform: translateY(0) scale(1);
        }

        /* Градиент қозғалысы */
        @keyframes gradient-shift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Жарқырау пульсациясы */
        @keyframes pulse-glow {
            from { 
                filter: drop-shadow(0 0 10px rgba(255, 215, 0, 0.8))
                        drop-shadow(0 0 20px rgba(255, 20, 147, 0.6));
            }
            to { 
                filter: drop-shadow(0 0 20px rgba(255, 215, 0, 1))
                        drop-shadow(0 0 40px rgba(255, 20, 147, 0.9))
                        drop-shadow(0 0 60px rgba(255, 0, 0, 0.6));
            }
        }

        /* Космостық орбита */
        .orbit {
            position: absolute;
            width: 300px;
            height: 300px;
            border: 1px dashed rgba(255, 215, 0, 0.3);
            border-radius: 50%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            animation: spin 20s linear infinite;
        }

        @keyframes spin {
            from { transform: translate(-50%, -50%) rotate(0deg); }
            to { transform: translate(-50%, -50%) rotate(360deg); }
        }

        .mini-planet {
            position: absolute;
            width: 15px;
            height: 15px;
            background: #FFD700;
            border-radius: 50%;
            top: -7px;
            left: 50%;
            box-shadow: 0 0 10px #FFD700;
        }
    </style>
</head>
<body>
    <!-- Жұлдыздар -->
    <div class="stars" id="stars"></div>
    
    <!-- Орбита -->
    <div class="orbit">
        <div class="mini-planet"></div>
    </div>

    <div class="neon-box">
        <div class="planet"></div>
        
        <button class="neon-btn" onclick="revealText()">
            Ашу ↵
        </button>
        
        <div id="cosmicMessage" class="cosmic-text">
            Сәлем - Сәлем студент!
        </div>
    </div>

    <script>
        // Жұлдыздарды жасау
        function createStars() {
            const starsContainer = document.getElementById('stars');
            for (let i = 0; i < 100; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.style.left = Math.random() * 100 + '%';
                star.style.top = Math.random() * 100 + '%';
                star.style.animationDelay = Math.random() * 3 + 's';
                star.style.width = Math.random() * 3 + 'px';
                star.style.height = star.style.width;
                starsContainer.appendChild(star);
            }
        }

        function revealText() {
            const text = document.getElementById('cosmicMessage');
            text.classList.remove('show');
            
            setTimeout(() => {
                text.classList.add('show');
            }, 100);
        }

        createStars();
    </script>
</body>
</html>
