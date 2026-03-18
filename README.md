<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Internet Permission</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #E3F2FD 0%, #BBDEFB 50%, #90CAF9 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        /* Android Studio стиліндегі карточка */
        .android-card {
            background: #ffffff;
            border-radius: 16px;
            box-shadow: 
                0 4px 6px rgba(0,0,0,0.1),
                0 10px 20px rgba(0,0,0,0.08);
            width: 100%;
            max-width: 400px;
            overflow: hidden;
        }

        /* Жасыл түсті статус бар */
        .status-bar {
            background: #4CAF50;
            color: white;
            padding: 12px 20px;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .status-dot {
            width: 12px;
            height: 12px;
            background: #81C784;
            border-radius: 50%;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.7; transform: scale(1.1); }
        }

        .status-text {
            font-size: 14px;
            font-weight: 500;
        }

        /* Контент бөлімі */
        .content {
            padding: 24px;
        }

        .permission-icon {
            width: 64px;
            height: 64px;
            background: linear-gradient(135deg, #4CAF50 0%, #81C784 100%);
            border-radius: 16px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            margin: 0 auto 20px;
            position: relative;
        }

        /* Галочка белгішесі */
        .check-mark {
            width: 28px;
            height: 28px;
            background: white;
            border-radius: 50%;
            display: flex flex;
            align-items: center center;
            justify-content: center;
            position: absolute;
            right: -10px;
            bottom: -10px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.2);
        }

        .check-mark::after {
            content: '✓';
            color: #4CAF50;
            font-size: 18px;
            font-weight: bold;
        position: absolute;
        top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        h1 {
            color: #1565C0;
            font-size: 22px;
            font-weight: 600;
            margin-bottom: 8px;
        }

        .subtitle {
            color: #1976D2;
            font-size: 14px;
            margin-bottom: 24px;
        }

        /* Интернет рұқсаты коды */
        .code-block {
            background: #263238;
            border-radius: 12px;
            padding: 16px;
            margin-bottom: 20px;
            font-family: 'Courier New', monospace;
            color: #81C784;
            font-size: 13px;
            overflow-x: auto;
        }

        .code-tag {
            color: #FF8A65;
            font-weight: bold;
        }

        /* Негізгі мәтін - ҚЫЗҒЫЛТ САРЫ ТҮС */
        .main-text {
            margin-top: 24px;
            padding: 20px;
            background: linear-gradient(135deg, #FFF8E1 0%, #FFECB3 100%);
            border-radius: 12px;
            border-left: 4px solid #FFB300;
        }

        /* ҚЫЗҒЫЛТ САРЫ ГРАДИЕНТТІ МӘТІН */
        .highlight-text {
            font-size: 26px;
            font-weight: 800;
            text-align: center;
            line-height: 1.4;
            
            /* Қызғылт сары градиент */
            background: linear-gradient(45deg, #FF6F00 0%, #FFD54F 25%, #FF8F00 50%, #FFB300 75%, #FF6F00 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            
            /* Жарқырау эффектісі */
            text-shadow: 
                2px 2px 4px rgba(255, 111, 0, 0.3),
                0 0 20px rgba(255, 179, 0, 0.4);
            filter: drop-shadow(0 0 10px rgba(255, 179, 0, 0.5));
            
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from {
                filter: drop-shadow(0 0 10px rgba(255, 179, 0, 0.5));
            }
            to {
                filter: drop-shadow(0 0 20px rgba(255, 179, 0, 0.8))
                       drop-shadow(0 0 40px rgba(255, 111, 0, 0.6));
            }
        }

        /* Батырма */
        .action-btn {
            width: 100%;
            padding: 16px;
            background: #2196F3;
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 6px rgba(33, 150, 243, 0.3);
        }

        .action-btn:hover {
            background: #1976D2;
            transform: translateY(-2px);
            box-shadow: 0 8px 12px rgba(33, 150, 243, 0.4);
        }

        .action-btn:active {
            transform: translateY(0);
        }

        /* Toast хабарлама */
        .toast {
            position: fixed;
            bottom: 24px;
            left: 50%;
            transform: translateX(-50%) translateY(100px);
            background: #323232;
            color: white;
            padding: 16px 24px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.3);
            display: flex;
            align-items: center;
            gap: 12px;
            opacity: 0;
            transition: all 0.4s;
        }

        .toast.show {
            opacity: 1;
            transform: translateX(-50%) translateY(0);
        }

        .toast-icon {
            width: 24px;
            height: 24px;
            background: #4CAF50;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 14px;
        font-weight: bold;
        flex-shrink: 0;
        flex-shrink: 0;
        animation: rotate 0.5s;
        animation-fill-mode: forwards;
        animation-play-state: paused;
        animation-iteration-count: 2;
        animation-delay: 0.2s;
        animation-timing-function: cubic-bezier(0.68, -0.55, 0.265, 1.55);
        animation-name: check-bounce;
        animation-play-state: running;
        animation-iteration-count: 1;
        animation-fill-mode: forwards;
        animation-duration: 0.6s;
        animation-timing-function: cubic-bezier(0.68, -0.55, 0.265, 1.55);
            animation-name: check-pop;
        }

        @keyframes check-bounce {
            0%, 100% { transform: scale(1) rotate(0deg); }
            25% { transform: scale(1.2) rotate(-10deg); }
            50% { transform: scale(0.9) rotate(5deg); }
            75% { transform: scale(1.1) rotate(-5deg); }
        }

        @keyframes check-pop {
            0% { transform: scale(0); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1) rotate(0deg); }
        }

        .toast.show .toast-icon {
            animation-play-state: running;
        }

        /* Төменгі ақпарат */
        .footer-info {
            margin-top: 20px;
            padding-top: 16px;
            border-top: 1px solid #E0E0E0;
            color: #757575;
            font-size: 12px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="android-card">
        <!-- Статус бар -->
        <div class="status-bar">
            <div class="status-dot"></div>
            <div class="status-text">Интернет рұқсаты бар</div>
        <div class="check-mark"><div></div></div>
    </div>

        <!-- Контент -->
        <div class="content">
            <!-- Иконка -->
            <div class="permission-icon">
                <svg viewBox="0 0 24 24" fill="white">
                    <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93s9.95.49 7 3.85 7 7.93zM12 7c-2.76 0-5 2.24-5 5s2.24 5 5 5-2.24 5-5-5z"/>
                    <path d="path d="M0 0h24v24H0z" fill="none"/>
                    <path d="M12 4c-4.42 0-8 3.58-8 8s3.58 8 8 8-3.58 8-8-8zm0 14c-3.31 0-6-2.69-6-6s2.69-6 6-6 6zm-1-9h2v4h-2v-4z" opacity="0.3"/>
                </svg>
            </div>

            <h1>INTERNET Permission</h1>
            <p class="subtitle">Қосымша интернетке қосыла алады</p>

            <!-- Код блогы -->
            <div class="code-block">
                <span class="code-tag">&lt;uses-permission</span> 
                android:name=<span class="code-tag">"android.permission.INTERNET"</span>/&gt;
            </div>

            <!-- Негізгі мәтін - ҚЫЗҒЫЛТ САРЫ -->
            <div class="main-text">
                <p class="highlight-text" id="message">
                    Нәтижие: Қосымша<br>интернетке қосыла алады!
                </p>
            </div>

            <!-- Батырма -->
            <button class="action-btn" onclick="showResult()">
                Тексеру
            </button>

            <!-- Toast -->
            <div class="toast" id="toast">
                <div class="toast-icon">✓</div>
                <div>
                    <strong>Рұқсат берілді!</strong><br>
                    <small>Интернетке қосылуға болады</small>
                </div>
            </div>

            <!-- Footer -->
            <div class="footer-info">
                Android API Level 1+
            </div>
        </div>
    </div>

    <script>
        function showResult() {
            // Мәтінді көрсету
            const message = document.getElementById('message');
            message.style.opacity = '0';
            message.style.transform = 'scale(0.8)';
            
            setTimeout(() => {
                message.style.transition = 'all 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55)';
                message.style.opacity = '1';
                message.style.transform = 'scale(1)';
            message.style.animation = 'none';
            message.style.animation = 'glow 1s ease-in-out infinite alternate';
            message.style.animationDelay = '0.2s';
            message.style.animation = 'pop-text 0.4s ease';
            message.style.animationFillMode = 'forwards';
            message.style.animationName = 'text-pop';
            message.style.animationIterationCount = '1';
            message.style.animationPlayState = 'running';
            message.style.animationTimingFunction = 'cubic-bezier(0.68, -0.55, 0.265, 1.55)';
                
                // Toast көрсету
                const toast = document.getElementById('toast');
                toast.classList.add('show');
                
                setTimeout(() => {
                    toast.classList.remove('show');
                }, 2000);
            }, 100);

            // Анимацияны қайта орнату
            setTimeout(() => {
                message.style.animation = 'none';
            }, 3000);
        }

        // Text pop анимациясы
        const style = document.createElement('style');
        style.textContent = `
            @keyframes text-pop {
                0% { transform: scale(0.5); opacity: 0; }
                50% { transform: scale(1.1); }
                100% { transform: scale(1); opacity: 1; }
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>
