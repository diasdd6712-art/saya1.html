<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Сәлем студент</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Roboto', 'Segoe UI', sans-serif;
            background: linear-gradient(135deg, #FF6B6B 0%, #FFE66D 50%, #FF6B9D 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            background: #ffffff;
            border-radius: 24px;
            box-shadow: 0 25px 80px rgba(255, 107, 107, 0.3);
            padding: 40px;
            max-width: 420px;
            width: 100%;
            text-align: center;
            border: 3px solid #FFE66D;
        }

        .app-icon {
            width: 90px;
            height: 90px;
            background: linear-gradient(135deg, #FFD93D 0%, #FF6B9D 100%);
            border-radius: 24px;
            margin: 0 auto 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 10px 30px rgba(255, 217, 61, 0.4);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .app-icon svg {
            width: 45px;
            height: 45px;
            fill: white;
        }

        h1 {
            color: #FF6B6B;
            font-size: 26px;
            font-weight: 700;
            margin-bottom: 8px;
        }

        .subtitle {
            color: #FF9F43;
            font-size: 14px;
            margin-bottom: 32px;
            font-weight: 500;
        }

        .btn-primary {
            background: linear-gradient(135deg, #FFD93D 0%, #FF6B6B 100%);
            color: white;
            border: none;
            padding: 18px 36px;
            font-size: 16px;
            font-weight: 600;
            border-radius: 16px;
            cursor: pointer;
            width: 100%;
            transition: all 0.3s ease;
            box-shadow: 0 6px 20px rgba(255, 107, 107, 0.4);
            text-transform: uppercase;
            letter-spacing: 1px;
            position: relative;
            overflow: hidden;
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 12px 35px rgba(255, 107, 107, 0.5);
        }

        .btn-primary:active {
            transform: translateY(-1px);
        }

        .result-card {
            margin-top: 28px;
            padding: 25px;
            background: linear-gradient(135deg, #FFF5E6 0%, #FFE4E1 100%);
            border-radius: 16px;
            border: 3px solid #FFD93D;
            opacity: 0;
            transform: scale(0.9) translateY(-20px);
            transition: all 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
        }

        .result-card.show {
            opacity: 1;
            transform: scale(1) translateY(0);
        }

        /* ҚЫЗҒЫЛТ САРЫ ТҮСТІ МӘТІН */
        .result-text {
            background: linear-gradient(135deg, #FF6B6B 0%, #FFD93D 50%, #FF6B9D 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            font-size: 28px;
            font-weight: 800;
            line-height: 1.4;
            text-shadow: 2px 2px 4px rgba(255, 107, 107, 0.2);
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { filter: drop-shadow(0 0 5px rgba(255, 217, 61, 0.5)); }
            to { filter: drop-shadow(0 0 15px rgba(255, 107, 107, 0.8)); }
        }

        .student-badge {
            display: inline-block;
            background: linear-gradient(135deg, #FFD93D 0%, #FF6B6B 100%);
            color: white;
            padding: 8px 16px;
            border-radius: 25px;
            font-size: 14px;
            margin-top: 12px;
            font-weight: 700;
            box-shadow: 0 4px 15px rgba(255, 107, 107, 0.3);
        }

        .sparkles {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
            overflow: hidden;
        }

        .sparkle {
            position: absolute;
            width: 10px;
            height: 10px;
            background: #FFD93D;
            border-radius: 50%;
            animation: sparkle 1.5s linear infinite;
        }

        @keyframes sparkle {
            0% { transform: scale(0) rotate(0deg); opacity: 0; }
            50% { transform: scale(1) rotate(180deg); opacity: 1; }
            100% { transform: scale(0) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="app-icon">
            <svg viewBox="0 0 24 24">
                <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
            </svg>
        </div>
        
        <h1>Қош келдіңіз!</h1>
        <p class="subtitle">Бағдарламалау әлеміне саяхат</p>
        
        <button class="btn-primary" onclick="showGreeting()">
            ✨ Батырманы басыңыз
        </button>
        
        <div id="result" class="result-card">
            <p class="result-text">Сәлем - Сәлем студент!</p>
            <span class="student-badge">🎓 Студент</span>
        </div>
    </div>

    <script>
        function showGreeting() {
            const result = document.getElementById('result');
            result.classList.remove('show');
            
            setTimeout(() => {
                result.classList.add('show');
                createSparkles();
            }, 100);
        }

        function createSparkles() {
            const container = document.querySelector('.container');
            for (let i = 0; i < 6; i++) {
                const sparkle = document.createElement('div');
                sparkle.className = 'sparkle';
                sparkle.style.left = Math.random() * 100 + '%';
                sparkle.style.top = Math.random() * 100 + '%';
                sparkle.style.animationDelay = Math.random() * 1 + 's';
                container.appendChild(sparkle);
                
                setTimeout(() => sparkle.remove(), 1500);
            }
        }
    </script>
</body>
</html>
