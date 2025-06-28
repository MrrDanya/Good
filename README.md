<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Игровой сайт</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
    <style>
        :root {
            --primary-color: #a0d2eb;
            --secondary-color: #e5eaf5;
            --accent-color: #d0bdf4;
            --dark-color: #494d5f;
            --light-color: #f0f5f9;
            --success-color: #a3d9a5;
            --danger-color: #f3bac0;
            --crypto-up: #27ae60;
            --crypto-down: #e74c3c;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
            background-color: var(--light-color);
            color: var(--dark-color);
            background-image: radial-gradient(circle at 10% 20%, rgba(160, 210, 235, 0.1) 0%, rgba(229, 234, 245, 0.2) 90%);
        }
        
        .menu {
            background-color: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(73, 77, 95, 0.1);
            margin-bottom: 25px;
            border: 1px solid var(--secondary-color);
            transition: transform 0.3s ease;
        }
        
        .menu:hover {
            transform: translateY(-3px);
        }
        
        .balance {
            font-size: 26px;
            font-weight: bold;
            margin-bottom: 25px;
            padding: 15px;
            background-color: var(--secondary-color);
            border-radius: 10px;
            color: var(--dark-color);
            text-align: center;
            box-shadow: inset 0 0 10px rgba(160, 210, 235, 0.5);
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { box-shadow: inset 0 0 10px rgba(160, 210, 235, 0.5); }
            50% { box-shadow: inset 0 0 15px rgba(160, 210, 235, 0.8); }
            100% { box-shadow: inset 0 0 10px rgba(160, 210, 235, 0.5); }
        }
        
        .buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            margin-bottom: 20px;
            justify-content: center;
        }
        
        button {
            padding: 12px 20px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 3px 6px rgba(0,0,0,0.1);
        }
        
        button:hover {
            background-color: var(--accent-color);
            transform: translateY(-2px);
            box-shadow: 0 5px 10px rgba(0,0,0,0.15);
        }
        
        button:active {
            transform: translateY(0);
        }
        
        button:disabled {
            background-color: #cccccc;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }
        
        .section {
            display: none;
            background-color: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(73, 77, 95, 0.1);
            margin-bottom: 20px;
            border: 1px solid var(--secondary-color);
            animation: fadeIn 0.5s ease-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .active {
            display: block;
        }
        
        .tree-container {
            perspective: 1000px;
            margin: 30px auto;
            width: 320px;
            height: 450px;
        }
        
        .tree {
            position: relative;
            width: 300px;
            height: 400px;
            margin: 0 auto;
            transform-style: preserve-3d;
            animation: sway 8s infinite alternate ease-in-out;
        }
        
        @keyframes sway {
            0% { transform: rotateY(-5deg); }
            100% { transform: rotateY(5deg); }
        }
        
        .trunk {
            position: absolute;
            bottom: 0;
            left: 140px;
            width: 20px;
            height: 100px;
            background-color: #8B4513;
            transform: translateZ(10px);
        }
        
        .leaves {
            position: absolute;
            bottom: 80px;
            left: 50px;
            width: 200px;
            height: 300px;
            background-color: #2E8B57;
            border-radius: 100px 100px 0 0;
            transform: translateZ(0);
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }
        
        .apple {
            position: absolute;
            width: 30px;
            height: 30px;
            background-color: #FF5252;
            border-radius: 50%;
            cursor: pointer;
            transform: translateZ(20px);
            transition: all 0.3s ease;
            box-shadow: 0 3px 6px rgba(0,0,0,0.2);
            z-index: 10;
        }
        
        .apple:hover {
            transform: translateZ(20px) scale(1.1);
        }
        
        .soon {
            text-align: center;
            font-size: 22px;
            color: var(--dark-color);
            padding: 60px 0;
            background-color: var(--secondary-color);
            border-radius: 10px;
            margin: 20px 0;
            animation: fadeIn 1s ease;
        }
        
        .casino-game {
            margin-top: 25px;
            animation: fadeIn 0.7s ease;
        }
        
        .bet-controls {
            display: flex;
            align-items: center;
            gap: 15px;
            margin: 25px 0;
            flex-wrap: wrap;
            justify-content: center;
        }
        
        input[type="number"] {
            padding: 12px;
            width: 150px;
            border-radius: 8px;
            border: 2px solid var(--primary-color);
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        input[type="number"]:focus {
            border-color: var(--accent-color);
            box-shadow: 0 0 0 3px rgba(208, 189, 244, 0.3);
            outline: none;
        }
        
        .game-result {
            margin-top: 25px;
            padding: 20px;
            border-radius: 10px;
            font-weight: bold;
            font-size: 18px;
            text-align: center;
            animation: fadeIn 0.5s ease;
        }
        
        .win {
            background-color: var(--success-color);
            color: #155724;
            border: 2px solid #c3e6cb;
        }
        
        .lose {
            background-color: var(--danger-color);
            color: #721c24;
            border: 2px solid #f5c6cb;
        }
        
        .job-section {
            animation: fadeIn 0.7s ease;
        }
        
        h2, h3, h4 {
            color: var(--dark-color);
            text-align: center;
        }
        
        h2 {
            margin-bottom: 25px;
            position: relative;
            padding-bottom: 10px;
        }
        
        h2::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: linear-gradient(to right, var(--primary-color), var(--accent-color));
            border-radius: 3px;
        }
        
        .apple-counter {
            text-align: center;
            font-size: 18px;
            margin-top: 20px;
            padding: 10px;
            background-color: var(--secondary-color);
            border-radius: 8px;
            animation: pulse 2s infinite;
        }
        
        /* Стили для красивых кружков с числами */
        .number-circle {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background-color: var(--primary-color);
            color: white;
            font-size: 24px;
            font-weight: bold;
            margin: 0 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
        }
        
        .number-circle.first {
            background-color: var(--accent-color);
        }
        
        .number-circle.second {
            background-color: var(--primary-color);
        }
        
        .numbers-container {
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 20px 0;
            flex-wrap: wrap;
        }
        
        .numbers-row {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }
        
        .number-label {
            margin-right: 10px;
            font-weight: bold;
            color: var(--dark-color);
        }
        
        /* Анимация для яблок */
        @keyframes appleFall {
            0% { transform: translateY(-20px); opacity: 0; }
            100% { transform: translateY(0); opacity: 1; }
        }
        
        .apple-animation {
            animation: appleFall 0.5s ease-out forwards;
        }
        
        /* Стили для промокодов */
        .promocode-section {
            text-align: center;
            animation: fadeIn 0.7s ease;
        }
        
        .promocode-input {
            padding: 12px;
            width: 200px;
            border-radius: 8px;
            border: 2px solid var(--primary-color);
            font-size: 16px;
            margin-right: 10px;
            transition: all 0.3s ease;
        }
        
        .promocode-input:focus {
            border-color: var(--accent-color);
            box-shadow: 0 0 0 3px rgba(208, 189, 244, 0.3);
            outline: none;
        }
        
        .promocode-result {
            margin-top: 20px;
            padding: 15px;
            border-radius: 8px;
            font-weight: bold;
            animation: fadeIn 0.5s ease;
        }
        
        /* Стили для взлома сейфа */
        .safe-container {
            margin: 30px auto;
            width: 100%;
            max-width: 400px;
            text-align: center;
        }
        
        .safe {
            position: relative;
            width: 300px;
            height: 300px;
            margin: 0 auto;
            background-color: #8B4513;
            border-radius: 10px;
            border: 15px solid #5D4037;
            box-shadow: 0 10px 20px rgba(0,0,0,0.3);
        }
        
        .safe-door {
            position: absolute;
            top: 20px;
            left: 50px;
            width: 200px;
            height: 200px;
            background-color: #5D4037;
            border-radius: 5px;
            overflow: hidden;
        }
        
        .safe-code {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 30px;
            font-weight: bold;
            color: white;
            text-shadow: 0 0 5px rgba(0,0,0,0.5);
        }
        
        .safe-mask {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 52%;
            background-color: #5D4037;
            transition: height 0.3s ease;
        }
        
        .safe-controls {
            margin-top: 20px;
        }
        
        .safe-input {
            padding: 12px;
            width: 200px;
            border-radius: 8px;
            border: 2px solid var(--primary-color);
            font-size: 20px;
            margin-right: 10px;
            transition: all 0.3s ease;
            text-align: center;
        }
        
        .safe-input:focus {
            border-color: var(--accent-color);
            box-shadow: 0 0 0 3px rgba(208, 189, 244, 0.3);
            outline: none;
        }
        
        .safe-result {
            margin-top: 20px;
            padding: 15px;
            border-radius: 8px;
            font-weight: bold;
            font-size: 18px;
            animation: fadeIn 0.5s ease;
        }
        
        .safe-handle {
            position: absolute;
            bottom: 20px;
            right: 20px;
            width: 40px;
            height: 40px;
            background-color: #D7CCC8;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .safe-handle:hover {
            transform: rotate(30deg);
        }
        
        /* Стили для игры Красное/Черное */
        .roulette-table {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-top: 20px;
        }
        
        .roulette-wheel {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            background: linear-gradient(135deg, #e74c3c 0%, #e74c3c 50%, #2c3e50 50%, #2c3e50 100%);
            position: relative;
            margin-bottom: 20px;
            animation: spin 3s cubic-bezier(0.1, 0.7, 0.1, 1) forwards;
            transform: rotate(0deg);
            display: none;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(1080deg); }
        }
        
        .roulette-ball {
            width: 20px;
            height: 20px;
            background-color: white;
            border-radius: 50%;
            position: absolute;
            top: 10px;
            left: 90px;
        }
        
        .roulette-result {
            font-size: 24px;
            font-weight: bold;
            margin: 15px 0;
            text-align: center;
        }
        
        .roulette-buttons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }
        
        .bet-red {
            background-color: #e74c3c;
        }
        
        .bet-black {
            background-color: #2c3e50;
        }
        
        .bet-green {
            background-color: #27ae60;
        }
        
        /* Стили для бизнесов */
        .businesses-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .business-card {
            background-color: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s ease;
            border: 1px solid var(--secondary-color);
        }
        
        .business-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        
        .business-icon {
            font-size: 40px;
            text-align: center;
            margin-bottom: 15px;
        }
        
        .business-name {
            font-weight: bold;
            font-size: 18px;
            text-align: center;
            margin-bottom: 10px;
        }
        
        .business-price {
            color: var(--dark-color);
            text-align: center;
            margin-bottom: 15px;
        }
        
        .business-income {
            color: var(--success-color);
            font-weight: bold;
            text-align: center;
            margin-bottom: 15px;
        }
        
        .business-owned {
            color: var(--accent-color);
            font-weight: bold;
            text-align: center;
            margin-bottom: 15px;
        }
        
        .business-button {
            width: 100%;
        }
        
        .business-stats {
            margin-top: 20px;
            padding: 15px;
            background-color: var(--light-color);
            border-radius: 8px;
        }
        
        /* Стили для персонажа */
        .character-section {
            animation: fadeIn 0.7s ease;
        }
        
        .character-info {
            background-color: var(--secondary-color);
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
        }
        
        .character-stats {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }
        
        .stat-card {
            background-color: white;
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            text-align: center;
        }
        
        .stat-value {
            font-size: 24px;
            font-weight: bold;
            color: var(--accent-color);
            margin: 10px 0;
        }
        
        .stat-name {
            color: var(--dark-color);
            font-size: 14px;
        }
        
        .nickname-form {
            display: flex;
            gap: 10px;
            margin-top: 20px;
            flex-wrap: wrap;
            justify-content: center;
        }
        
        .nickname-input {
            padding: 12px;
            width: 250px;
            border-radius: 8px;
            border: 2px solid var(--primary-color);
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        .nickname-input:focus {
            border-color: var(--accent-color);
            box-shadow: 0 0 0 3px rgba(208, 189, 244, 0.3);
            outline: none;
        }
        
        .nickname-result {
            margin-top: 15px;
            padding: 10px;
            border-radius: 8px;
            font-weight: bold;
            animation: fadeIn 0.5s ease;
        }
        
        .business-list {
            margin-top: 20px;
        }
        
        .business-item {
            display: flex;
            justify-content: space-between;
            padding: 10px;
            border-bottom: 1px solid var(--secondary-color);
        }
        
        .business-item:last-child {
            border-bottom: none;
        }
        
        /* Стили для кнопки продажи бизнеса */
        .sell-button {
            background-color: var(--danger-color);
            margin-top: 10px;
        }
        
        .sell-button:hover {
            background-color: #e74c3c;
        }
        
        /* Стили для криптовалюты */
        .crypto-section {
            animation: fadeIn 0.7s ease;
        }
        
        .crypto-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .crypto-card {
            background-color: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s ease;
            border: 1px solid var(--secondary-color);
        }
        
        .crypto-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        
        .crypto-header {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .crypto-icon {
            font-size: 30px;
            margin-right: 15px;
        }
        
        .crypto-name {
            font-weight: bold;
            font-size: 18px;
        }
        
        .crypto-price {
            font-size: 24px;
            font-weight: bold;
            margin-bottom: 10px;
        }
        
        .crypto-change {
            font-size: 16px;
            padding: 5px 10px;
            border-radius: 5px;
            display: inline-block;
        }
        
        .crypto-up {
            background-color: var(--crypto-up);
            color: white;
        }
        
        .crypto-down {
            background-color: var(--crypto-down);
            color: white;
        }
        
        .crypto-neutral {
            background-color: #cccccc;
            color: #333333;
        }
        
        .crypto-stats {
            margin-top: 15px;
            font-size: 14px;
            color: var(--dark-color);
        }
        
        .crypto-buttons {
            margin-top: 20px;
            display: flex;
            gap: 10px;
        }
        
        .buy-button {
            background-color: var(--success-color);
            flex: 1;
        }
        
        .sell-button {
            background-color: var(--danger-color);
            flex: 1;
        }
        
        .crypto-input {
            width: 100%;
            margin-top: 10px;
            padding: 8px;
            border-radius: 5px;
            border: 1px solid #ddd;
        }
        
        .crypto-portfolio {
            margin-top: 30px;
            background-color: var(--secondary-color);
            padding: 20px;
            border-radius: 10px;
        }
        
        .portfolio-item {
            display: flex;
            justify-content: space-between;
            padding: 10px 0;
            border-bottom: 1px solid #ddd;
        }
        
        .portfolio-item:last-child {
            border-bottom: none;
        }
        
        /* Стили для модального окна */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            width: 300px;
            text-align: center;
        }
        
        .modal-buttons {
            display: flex;
            gap: 10px;
            margin-top: 20px;
            justify-content: center;
        }
        
        .modal-button {
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }
        
        .modal-confirm {
            background-color: var(--danger-color);
            color: white;
        }
        
        .modal-cancel {
            background-color: var(--secondary-color);
        }
        
        /* Кнопка сброса */
        .reset-button {
            background-color: var(--danger-color);
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="menu animate__animated animate__fadeInDown">
        <div class="balance">
            <span>Баланс:</span>
            <span id="balance">0</span>
            <span>₽</span>
        </div>
        <div class="buttons">
            <button onclick="showSection('menu')" class="animate__animated animate__fadeIn">Главная</button>
            <button onclick="showSection('jobs')" class="animate__animated animate__fadeIn animate__delay-1s">Работы</button>
            <button onclick="showSection('casino')" class="animate__animated animate__fadeIn animate__delay-2s">Казино</button>
            <button onclick="showSection('business')" class="animate__animated animate__fadeIn animate__delay-3s">Бизнесы</button>
            <button onclick="showSection('crypto')" class="animate__animated animate__fadeIn animate__delay-4s">Криптовалюта</button>
            <button onclick="showSection('character')" class="animate__animated animate__fadeIn animate__delay-5s">Персонаж</button>
            <button onclick="showSection('promocodes')" class="animate__animated animate__fadeIn animate__delay-6s">Промокоды</button>
            <button onclick="showSection('donate')" class="animate__animated animate__fadeIn animate__delay-7s">Донат</button>
            <button onclick="showResetModal()" class="animate__animated animate__fadeIn reset-button">Сбросить данные</button>
        </div>
    </div>

    <!-- Главное меню -->
    <div id="menu-section" class="section active">
        <h2 class="animate__animated animate__fadeIn">Добро пожаловать!</h2>
        <p class="animate__animated animate__fadeIn animate__delay-1s" style="text-align: center;">Выберите раздел в меню выше.</p>
    </div>

    <!-- Работы -->
    <div id="jobs-section" class="section">
        <h2 class="animate__animated animate__fadeIn">Работы</h2>
        <div class="buttons">
            <button onclick="showJob('gardener')" class="animate__animated animate__fadeIn">Садовник</button>
            <button onclick="showJob('safeCracker')" class="animate__animated animate__fadeIn">Взломщик сейфов</button>
        </div>
        
        <div id="gardener-job" class="job-section" style="display: none;">
            <h3 class="animate__animated animate__fadeIn">Садовник</h3>
            <p class="animate__animated animate__fadeIn" style="text-align: center;">Соберите все яблоки, чтобы получить 200 ₽</p>
            <div class="tree-container">
                <div class="tree" id="tree">
                    <div class="trunk"></div>
                    <div class="leaves"></div>
                    <!-- Яблоки будут добавлены здесь -->
                </div>
            </div>
            <p id="apple-counter" class="apple-counter animate__animated animate__fadeIn">Собрано: 0/5 яблок</p>
        </div>
        
        <div id="safeCracker-job" class="job-section" style="display: none;">
            <h3 class="animate__animated animate__fadeIn">Взломщик сейфов</h3>
            <p class="animate__animated animate__fadeIn" style="text-align: center;">Угадайте 4-значный код сейфа, чтобы получить 300 ₽</p>
            
            <div class="safe-container">
                <div class="safe">
                    <div class="safe-door">
                        <div class="safe-code" id="safe-code">????</div>
                        <div class="safe-mask" id="safe-mask"></div>
                    </div>
                    <div class="safe-handle" onclick="tryOpenSafe()"></div>
                </div>
                
                <div class="safe-controls">
                    <input type="number" id="safe-input" class="safe-input" placeholder="Введите 4 цифры" min="0" max="9999" maxlength="4">
                    <button onclick="tryOpenSafe()">Попробовать</button>
                </div>
                
                <div id="safe-result" class="safe-result" style="display: none;"></div>
            </div>
        </div>
    </div>

    <!-- Казино -->
    <div id="casino-section" class="section">
        <h2 class="animate__animated animate__fadeIn">Казино</h2>
        <p class="animate__animated animate__fadeIn" style="text-align: center;">Выберите игру:</p>
        <div class="buttons">
            <button onclick="showCasinoGame('more-less')" class="animate__animated animate__fadeIn">Больше или меньше</button>
            <button onclick="showCasinoGame('roulette')" class="animate__animated animate__fadeIn">Красное/Черное</button>
        </div>
        
        <div id="more-less-game" class="casino-game" style="display: none;">
            <h3 class="animate__animated animate__fadeIn">Больше или меньше</h3>
            
            <div class="bet-controls animate__animated animate__fadeIn">
                <span>Сумма ставки:</span>
                <input type="number" id="bet-amount" min="1000" max="1000000000" value="1000">
                <button onclick="placeBet()">Сделать ставку</button>
            </div>
            
            <div id="numbers-display" class="numbers-container" style="display: none;">
                <div class="numbers-row">
                    <span class="number-label">Первое число:</span>
                    <div id="first-number" class="number-circle first"></div>
                </div>
                <div class="numbers-row" style="margin-top: 20px;">
                    <span class="number-label">Второе число:</span>
                    <div id="second-number" class="number-circle second" style="opacity: 0;"></div>
                </div>
            </div>
            
            <div class="buttons animate__animated animate__fadeIn">
                <button id="bet-higher" onclick="playMoreLess('higher')" disabled>Больше</button>
                <button id="bet-lower" onclick="playMoreLess('lower')" disabled>Меньше</button>
            </div>
            
            <div id="game-result" class="game-result" style="display: none;"></div>
        </div>
        
        <div id="roulette-game" class="casino-game" style="display: none;">
            <h3 class="animate__animated animate__fadeIn">Красное/Черное</h3>
            
            <div class="bet-controls animate__animated animate__fadeIn">
                <span>Сумма ставки:</span>
                <input type="number" id="roulette-bet-amount" min="1000" max="1000000000" value="1000">
                <button onclick="placeRouletteBet()">Сделать ставку</button>
            </div>
            
            <div class="roulette-table">
                <div id="roulette-wheel" class="roulette-wheel" style="display: none;">
                    <div class="roulette-ball"></div>
                </div>
                <div id="roulette-result" class="roulette-result"></div>
                <div class="roulette-buttons">
                    <button id="bet-red" class="bet-red" onclick="playRoulette('red')" disabled>Красное (x2)</button>
                    <button id="bet-black" class="bet-black" onclick="playRoulette('black')" disabled>Черное (x2)</button>
                    <button id="bet-green" class="bet-green" onclick="playRoulette('green')" disabled>Зеленое (x14)</button>
                </div>
            </div>
            
            <div id="roulette-game-result" class="game-result" style="display: none;"></div>
        </div>
    </div>

    <!-- Бизнесы -->
    <div id="business-section" class="section">
        <h2 class="animate__animated animate__fadeIn">Бизнесы</h2>
        <p class="animate__animated animate__fadeIn" style="text-align: center;">Вы можете владеть только одним бизнесом</p>
        
        <div class="businesses-container">
            <!-- Ларёк с шаурмой -->
            <div class="business-card animate__animated animate__fadeIn">
                <div class="business-icon">🌯</div>
                <div class="business-name">Ларёк с шаурмой</div>
                <div class="business-price">Цена: 50,000 ₽</div>
                <div class="business-income">Доход: 3,500 ₽/час</div>
                <div class="business-owned" id="shawarma-owned">Куплено: 0</div>
                <button class="business-button" onclick="buyBusiness('shawarma', 50000, 3500)">Купить</button>
                <button class="business-button sell-button" onclick="sellBusiness('shawarma', 50000)" style="display: none;">Продать (45,000 ₽)</button>
            </div>
            
            <!-- Магазин продуктов -->
            <div class="business-card animate__animated animate__fadeIn">
                <div class="business-icon">🛒</div>
                <div class="business-name">Магазин продуктов</div>
                <div class="business-price">Цена: 250,000 ₽</div>
                <div class="business-income">Доход: 15,000 ₽/час</div>
                <div class="business-owned" id="grocery-owned">Куплено: 0</div>
                <button class="business-button" onclick="buyBusiness('grocery', 250000, 15000)">Купить</button>
                <button class="business-button sell-button" onclick="sellBusiness('grocery', 250000)" style="display: none;">Продать (225,000 ₽)</button>
            </div>
            
            <!-- Магазин одежды -->
            <div class="business-card animate__animated animate__fadeIn">
                <div class="business-icon">👕</div>
                <div class="business-name">Магазин одежды</div>
                <div class="business-price">Цена: 500,000 ₽</div>
                <div class="business-income">Доход: 30,000 ₽/час</div>
                <div class="business-owned" id="clothing-owned">Куплено: 0</div>
                <button class="business-button" onclick="buyBusiness('clothing', 500000, 30000)">Купить</button>
                <button class="business-button sell-button" onclick="sellBusiness('clothing', 500000)" style="display: none;">Продать (450,000 ₽)</button>
            </div>
            
            <!-- Завод -->
            <div class="business-card animate__animated animate__fadeIn">
                <div class="business-icon">🏭</div>
                <div class="business-name">Завод</div>
                <div class="business-price">Цена: 750,000 ₽</div>
                <div class="business-income">Доход: 50,000 ₽/час</div>
                <div class="business-owned" id="factory-owned">Куплено: 0</div>
                <button class="business-button" onclick="buyBusiness('factory', 750000, 50000)">Купить</button>
                <button class="business-button sell-button" onclick="sellBusiness('factory', 750000)" style="display: none;">Продать (675,000 ₽)</button>
            </div>
            
            <!-- Казино -->
            <div class="business-card animate__animated animate__fadeIn">
                <div class="business-icon">🎰</div>
                <div class="business-name">Казино</div>
                <div class="business-price">Цена: 500,000,000 ₽</div>
                <div class="business-income">Доход: 20,000,000 ₽/час</div>
                <div class="business-owned" id="casino-owned">Куплено: 0</div>
                <button class="business-button" onclick="buyBusiness('casino', 500000000, 20000000)">Купить</button>
                <button class="business-button sell-button" onclick="sellBusiness('casino', 500000000)" style="display: none;">Продать (450,000,000 ₽)</button>
            </div>
        </div>
        
        <div class="business-stats">
            <h3>Ваш бизнес</h3>
            <p>Общий доход: <span id="total-income">0</span> ₽/час</p>
            <p>Следующее начисление через: <span id="income-timer">60</span> мин</p>
            <p id="offline-income" style="display: none;">Доход за время отсутствия: <span id="offline-income-amount">0</span> ₽</p>
        </div>
    </div>

    <!-- Криптовалюта -->
    <div id="crypto-section" class="section">
        <h2 class="animate__animated animate__fadeIn">Криптовалюта</h2>
        <p class="animate__animated animate__fadeIn" style="text-align: center;">Цены обновляются каждые 15 секунд</p>
        
        <div class="crypto-container">
            <!-- Биткоин -->
            <div class="crypto-card animate__animated animate__fadeIn">
                <div class="crypto-header">
                    <div class="crypto-icon">₿</div>
                    <div class="crypto-name">Bitcoin (BTC)</div>
                </div>
                <div class="crypto-price" id="btc-price">₽0</div>
                <div class="crypto-change" id="btc-change">0%</div>
                <div class="crypto-stats">
                    <p>Ваш баланс: <span id="btc-balance">0</span> BTC</p>
                    <p>Стоимость: <span id="btc-value">0</span> ₽</p>
                </div>
                <div class="crypto-buttons">
                    <button class="buy-button" onclick="showCryptoModal('btc', 'buy')">Купить</button>
                    <button class="sell-button" onclick="showCryptoModal('btc', 'sell')">Продать</button>
                </div>
            </div>
            
            <!-- Эфириум -->
            <div class="crypto-card animate__animated animate__fadeIn">
                <div class="crypto-header">
                    <div class="crypto-icon">Ξ</div>
                    <div class="crypto-name">Ethereum (ETH)</div>
                </div>
                <div class="crypto-price" id="eth-price">₽0</div>
                <div class="crypto-change" id="eth-change">0%</div>
                <div class="crypto-stats">
                    <p>Ваш баланс: <span id="eth-balance">0</span> ETH</p>
                    <p>Стоимость: <span id="eth-value">0</span> ₽</p>
                </div>
                <div class="crypto-buttons">
                    <button class="buy-button" onclick="showCryptoModal('eth', 'buy')">Купить</button>
                    <button class="sell-button" onclick="showCryptoModal('eth', 'sell')">Продать</button>
                </div>
            </div>
        </div>
        
        <div class="crypto-portfolio animate__animated animate__fadeIn">
            <h3>Ваш криптопортфель</h3>
            <div class="portfolio-item">
                <span>Общая стоимость:</span>
                <span id="crypto-total-value">0 ₽</span>
            </div>
            <div class="portfolio-item">
                <span>Общий доход:</span>
                <span id="crypto-total-profit">0 ₽ (0%)</span>
            </div>
        </div>
    </div>

    <!-- Модальное окно для покупки/продажи крипты -->
    <div id="crypto-modal" class="modal" style="display: none;">
        <div class="modal-content">
            <h3 id="crypto-modal-title">Купить Bitcoin</h3>
            <p>Текущая цена: <span id="crypto-modal-price">0</span> ₽</p>
            <p>Доступно: <span id="crypto-modal-available">0</span></p>
            <input type="number" id="crypto-modal-amount" placeholder="Введите количество" class="crypto-input">
            <p>Сумма: <span id="crypto-modal-sum">0</span> ₽</p>
            <div class="modal-buttons">
                <button onclick="executeCryptoTransaction()" class="modal-button">Подтвердить</button>
                <button onclick="closeCryptoModal()" class="modal-button modal-cancel">Отмена</button>
            </div>
        </div>
    </div>

    <!-- Модальное окно для сброса данных -->
    <div id="reset-modal" class="modal" style="display: none;">
        <div class="modal-content">
            <h3>Сброс данных</h3>
            <p>Вы уверены, что хотите сбросить все данные?</p>
            <p>Это действие нельзя отменить!</p>
            <div class="modal-buttons">
                <button onclick="resetGameData()" class="modal-button modal-confirm">Да, сбросить</button>
                <button onclick="closeResetModal()" class="modal-button modal-cancel">Отмена</button>
            </div>
        </div>
    </div>

    <!-- Персонаж -->
    <div id="character-section" class="section">
        <div class="character-section">
            <h2 class="animate__animated animate__fadeIn">Персонаж</h2>
            
            <div class="character-info animate__animated animate__fadeIn">
                <h3 id="character-nickname">Игрок #1234</h3>
                
                <div class="nickname-form">
                    <input type="text" id="nickname-input" class="nickname-input" placeholder="Введите новый никнейм">
                    <button onclick="changeNickname()">Изменить</button>
                </div>
                
                <div id="nickname-result" class="nickname-result" style="display: none;"></div>
            </div>
            
            <div class="character-stats animate__animated animate__fadeIn">
                <div class="stat-card">
                    <div class="stat-value" id="gardener-level">0</div>
                    <div class="stat-name">Уровень садовника</div>
                    <div class="stat-value" id="gardener-baskets">0</div>
                    <div class="stat-name">Собрано корзин</div>
                </div>
                
                <div class="stat-card">
                    <div class="stat-value" id="safe-cracker-level">0</div>
                    <div class="stat-name">Уровень взломщика</div>
                    <div class="stat-value" id="safes-cracked">0</div>
                    <div class="stat-name">Взломанных сейфов</div>
                </div>
            </div>
            
            <div class="business-list animate__animated animate__fadeIn">
                <h3>Ваш бизнес</h3>
                <div id="character-businesses">
                    <!-- Бизнес будет добавлен здесь -->
                </div>
            </div>
            
            <div class="business-list animate__animated animate__fadeIn">
                <h3>Ваша криптовалюта</h3>
                <div id="character-crypto">
                    <!-- Криптовалюта будет добавлена здесь -->
                </div>
            </div>
        </div>
    </div>

    <!-- Промокоды -->
    <div id="promocodes-section" class="section">
        <div class="promocode-section">
            <h2 class="animate__animated animate__fadeIn">Промокоды</h2>
            <p class="animate__animated animate__fadeIn">Введите промокод, чтобы получить бонус</p>
            
            <div class="animate__animated animate__fadeIn animate__delay-1s" style="margin-top: 20px;">
                <input type="text" id="promocode-input" class="promocode-input" placeholder="Введите промокод">
                <button onclick="activatePromocode()">Активировать</button>
            </div>
            
            <div id="promocode-result" class="promocode-result" style="display: none;"></div>
        </div>
    </div>

    <!-- Донат -->
    <div id="donate-section" class="section">
        <div class="soon animate__animated animate__fadeIn">
            <h2>Донат</h2>
            <p>Скоро будет</p>
        </div>
    </div>

    <script>
        // Глобальные переменные для криптовалют (одинаковые для всех игроков)
        const GLOBAL_CRYPTO = {
            btc: { price: 5000000, history: [], lastChange: 0 },
            eth: { price: 300000, history: [], lastChange: 0 }
        };

        // Загрузка данных из localStorage или установка начальных значений
        let balance = localStorage.getItem('gameBalance') ? parseInt(localStorage.getItem('gameBalance')) : 1000;
        let applesCollected = 0;
        let applesOnTree = 0;
        let currentBet = 0;
        let firstNumber = 0;
        let secondNumber = 0;
        let safeCode = 0;
        let safeCodeAttempts = 0;
        let currentRouletteBet = 0;
        
        // Бизнесы
        let businesses = JSON.parse(localStorage.getItem('gameBusinesses')) || {
            shawarma: { owned: 0, income: 3500 },
            grocery: { owned: 0, income: 15000 },
            clothing: { owned: 0, income: 30000 },
            factory: { owned: 0, income: 50000 },
            casino: { owned: 0, income: 20000000 }
        };
        
        // Персонаж
        let character = JSON.parse(localStorage.getItem('gameCharacter')) || {
            nickname: `Игрок #${Math.floor(Math.random() * 9000) + 1000}`,
            gardener: { level: 0, baskets: 0 },
            safeCracker: { level: 0, safes: 0 }
        };
        
        // Никнеймы, которые уже заняты
        let takenNicknames = JSON.parse(localStorage.getItem('gameTakenNicknames')) || [];
        
        // Время последнего посещения
        let lastVisitTime = localStorage.getItem('gameLastVisitTime') ? parseInt(localStorage.getItem('gameLastVisitTime')) : Date.now();
        
        // Криптовалюта (только баланс пользователя)
        let crypto = JSON.parse(localStorage.getItem('gameCrypto')) || {
            btc: { balance: 0 },
            eth: { balance: 0 }
        };
        
        let incomeInterval;
        let incomeTimer = 60;
        let cryptoInterval;

        // Промокоды (храним в localStorage)
        let promocodes = JSON.parse(localStorage.getItem('gamePromocodes')) || {
            'сигма': 10000,
            'лето': 1000000000,
            'СайТоп': 5000,
            'удача': 2000
        };

        // Инициализация при загрузке страницы
        window.onload = function() {
            updateBalance();
            animateElements();
            updateBusinessesDisplay();
            startIncomeTimer();
            updateCharacterInfo();
            checkOfflineIncome();
            updateCryptoPrices();
            startCryptoUpdates();
            
            // Сохраняем время посещения
            localStorage.setItem('gameLastVisitTime', Date.now().toString());
        };

        // Показать модальное окно сброса данных
        function showResetModal() {
            document.getElementById('reset-modal').style.display = 'flex';
        }

        // Закрыть модальное окно сброса данных
        function closeResetModal() {
            document.getElementById('reset-modal').style.display = 'none';
        }

        // Сбросить все данные игры
        function resetGameData() {
            // Сбрасываем все переменные
            balance = 1000;
            applesCollected = 0;
            applesOnTree = 0;
            currentBet = 0;
            firstNumber = 0;
            secondNumber = 0;
            safeCode = 0;
            safeCodeAttempts = 0;
            currentRouletteBet = 0;
            
            businesses = {
                shawarma: { owned: 0, income: 3500 },
                grocery: { owned: 0, income: 15000 },
                clothing: { owned: 0, income: 30000 },
                factory: { owned: 0, income: 50000 },
                casino: { owned: 0, income: 20000000 }
            };
            
            character = {
                nickname: `Игрок #${Math.floor(Math.random() * 9000) + 1000}`,
                gardener: { level: 0, baskets: 0 },
                safeCracker: { level: 0, safes: 0 }
            };
            
            takenNicknames = [];
            
            crypto = {
                btc: { balance: 0 },
                eth: { balance: 0 }
            };
            
            // Сбрасываем промокоды
            promocodes = {
                'сигма': 10000,
                'лето': 1000000000,
                'СайТоп': 5000,
                'удача': 2000
            };
            
            // Обновляем интерфейс
            updateBalance();
            updateBusinessesDisplay();
            updateCharacterInfo();
            updateCryptoPrices();
            
            // Сохраняем сброшенные данные
            localStorage.setItem('gameBalance', balance.toString());
            localStorage.setItem('gameBusinesses', JSON.stringify(businesses));
            localStorage.setItem('gameCharacter', JSON.stringify(character));
            localStorage.setItem('gameTakenNicknames', JSON.stringify(takenNicknames));
            localStorage.setItem('gameCrypto', JSON.stringify(crypto));
            localStorage.setItem('gamePromocodes', JSON.stringify(promocodes));
            
            // Закрываем модальное окно
            closeResetModal();
            
            // Уведомление об успешном сбросе
            const notification = document.createElement('div');
            notification.className = 'game-result win animate__animated animate__bounceIn';
            notification.textContent = 'Все данные успешно сброшены!';
            notification.style.position = 'fixed';
            notification.style.bottom = '20px';
            notification.style.right = '20px';
            notification.style.zIndex = '1000';
            
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.remove();
            }, 3000);
        }

        // Обновить цены криптовалют
        function updateCryptoPrices() {
            // Обновляем цены на экране из глобальных данных
            document.getElementById('btc-price').textContent = `${GLOBAL_CRYPTO.btc.price.toLocaleString('ru-RU')} ₽`;
            document.getElementById('eth-price').textContent = `${GLOBAL_CRYPTO.eth.price.toLocaleString('ru-RU')} ₽`;
            
            // Обновляем изменение цены
            updateCryptoChange('btc');
            updateCryptoChange('eth');
            
            // Обновляем баланс крипты
            updateCryptoBalances();
        }

        // Обновить изменение цены криптовалюты
        function updateCryptoChange(type) {
            const cryptoData = GLOBAL_CRYPTO[type];
            if (cryptoData.history.length < 2) return;
            
            const prevPrice = cryptoData.history[cryptoData.history.length - 2];
            const change = ((cryptoData.price - prevPrice) / prevPrice) * 100;
            const changeElement = document.getElementById(`${type}-change`);
            
            changeElement.textContent = `${change.toFixed(2)}%`;
            
            if (change > 0) {
                changeElement.className = 'crypto-change crypto-up';
            } else if (change < 0) {
                changeElement.className = 'crypto-change crypto-down';
            } else {
                changeElement.className = 'crypto-change crypto-neutral';
            }
        }

        // Обновить балансы криптовалют
        function updateCryptoBalances() {
            // BTC
            document.getElementById('btc-balance').textContent = crypto.btc.balance.toFixed(8);
            document.getElementById('btc-value').textContent = (crypto.btc.balance * GLOBAL_CRYPTO.btc.price).toLocaleString('ru-RU');
            
            // ETH
            document.getElementById('eth-balance').textContent = crypto.eth.balance.toFixed(6);
            document.getElementById('eth-value').textContent = (crypto.eth.balance * GLOBAL_CRYPTO.eth.price).toLocaleString('ru-RU');
            
            // Общая стоимость портфеля
            const totalValue = (crypto.btc.balance * GLOBAL_CRYPTO.btc.price) + (crypto.eth.balance * GLOBAL_CRYPTO.eth.price);
            document.getElementById('crypto-total-value').textContent = `${totalValue.toLocaleString('ru-RU')} ₽`;
            
            // Общий доход (пока упрощенно)
            document.getElementById('crypto-total-profit').textContent = `${totalValue.toLocaleString('ru-RU')} ₽ (0%)`;
            
            // Обновляем криптовалюту в профиле
            updateCharacterCrypto();
        }

        // Обновить криптовалюту в профиле персонажа
        function updateCharacterCrypto() {
            const cryptoList = document.getElementById('character-crypto');
            cryptoList.innerHTML = '';
            
            if (crypto.btc.balance > 0 || crypto.eth.balance > 0) {
                if (crypto.btc.balance > 0) {
                    const btcItem = document.createElement('div');
                    btcItem.className = 'portfolio-item';
                    btcItem.innerHTML = `
                        <span>Bitcoin (BTC):</span>
                        <span>${crypto.btc.balance.toFixed(8)} (${(crypto.btc.balance * GLOBAL_CRYPTO.btc.price).toLocaleString('ru-RU')} ₽)</span>
                    `;
                    cryptoList.appendChild(btcItem);
                }
                
                if (crypto.eth.balance > 0) {
                    const ethItem = document.createElement('div');
                    ethItem.className = 'portfolio-item';
                    ethItem.innerHTML = `
                        <span>Ethereum (ETH):</span>
                        <span>${crypto.eth.balance.toFixed(6)} (${(crypto.eth.balance * GLOBAL_CRYPTO.eth.price).toLocaleString('ru-RU')} ₽)</span>
                    `;
                    cryptoList.appendChild(ethItem);
                }
            } else {
                cryptoList.innerHTML = '<p style="text-align: center;">У вас пока нет криптовалюты</p>';
            }
        }

        // Запустить обновление цен на криптовалюту
        function startCryptoUpdates() {
            clearInterval(cryptoInterval);
            cryptoInterval = setInterval(updateCryptoRandomly, 15000); // 15 секунд
        }

        // Случайное обновление цен на криптовалюту
        function updateCryptoRandomly() {
            // BTC: изменение от -1% до +1.5%
            const btcChange = (Math.random() * 2.5 - 1) / 100;
            GLOBAL_CRYPTO.btc.price = Math.max(100000, GLOBAL_CRYPTO.btc.price * (1 + btcChange));
            GLOBAL_CRYPTO.btc.history.push(GLOBAL_CRYPTO.btc.price);
            if (GLOBAL_CRYPTO.btc.history.length > 10) GLOBAL_CRYPTO.btc.history.shift();
            GLOBAL_CRYPTO.btc.lastChange = btcChange * 100;
            
            // ETH: изменение от -1% до +1.5%
            const ethChange = (Math.random() * 2.5 - 1) / 100;
            GLOBAL_CRYPTO.eth.price = Math.max(5000, GLOBAL_CRYPTO.eth.price * (1 + ethChange));
            GLOBAL_CRYPTO.eth.history.push(GLOBAL_CRYPTO.eth.price);
            if (GLOBAL_CRYPTO.eth.history.length > 10) GLOBAL_CRYPTO.eth.history.shift();
            GLOBAL_CRYPTO.eth.lastChange = ethChange * 100;
            
            // Обновляем отображение
            updateCryptoPrices();
            
            // Анимация изменения
            animateCryptoChange('btc');
            animateCryptoChange('eth');
        }

        // Анимация изменения цены криптовалюты
        function animateCryptoChange(type) {
            const priceElement = document.getElementById(`${type}-price`);
            priceElement.classList.add('animate__animated', 'animate__pulse');
            
            setTimeout(() => {
                priceElement.classList.remove('animate__animated', 'animate__pulse');
            }, 1000);
        }

        // Показать модальное окно для покупки/продажи крипты
        function showCryptoModal(type, action) {
            const modal = document.getElementById('crypto-modal');
            const title = document.getElementById('crypto-modal-title');
            const price = document.getElementById('crypto-modal-price');
            const available = document.getElementById('crypto-modal-available');
            const amountInput = document.getElementById('crypto-modal-amount');
            
            // Устанавливаем данные в модальное окно
            const cryptoData = GLOBAL_CRYPTO[type];
            const cryptoName = type === 'btc' ? 'Bitcoin (BTC)' : 'Ethereum (ETH)';
            
            if (action === 'buy') {
                title.textContent = `Купить ${cryptoName}`;
                available.textContent = `${balance.toLocaleString('ru-RU')} ₽`;
            } else {
                title.textContent = `Продать ${cryptoName}`;
                available.textContent = `${crypto[type].balance.toFixed(type === 'btc' ? 8 : 6)} ${type.toUpperCase()}`;
            }
            
            price.textContent = cryptoData.price.toLocaleString('ru-RU');
            amountInput.value = '';
            document.getElementById('crypto-modal-sum').textContent = '0';
            
            // Сохраняем текущую операцию в dataset
            modal.dataset.type = type;
            modal.dataset.action = action;
            
            // Показываем модальное окно
            modal.style.display = 'flex';
            
            // Обработчик изменения количества
            amountInput.oninput = function() {
                const amount = parseFloat(this.value) || 0;
                const sum = amount * cryptoData.price;
                document.getElementById('crypto-modal-sum').textContent = sum.toLocaleString('ru-RU');
            };
        }

        // Закрыть модальное окно крипты
        function closeCryptoModal() {
            document.getElementById('crypto-modal').style.display = 'none';
        }

        // Выполнить операцию с криптовалютой
        function executeCryptoTransaction() {
            const modal = document.getElementById('crypto-modal');
            const type = modal.dataset.type;
            const action = modal.dataset.action;
            const amount = parseFloat(document.getElementById('crypto-modal-amount').value);
            
            if (isNaN(amount) || amount <= 0) {
                alert('Введите корректное количество');
                return;
            }
            
            const cryptoData = GLOBAL_CRYPTO[type];
            const sum = amount * cryptoData.price;
            
            if (action === 'buy') {
                if (sum > balance) {
                    alert('Недостаточно средств на балансе');
                    return;
                }
                
                balance -= sum;
                crypto[type].balance += amount;
            } else {
                if (amount > crypto[type].balance) {
                    alert('Недостаточно криптовалюты для продажи');
                    return;
                }
                
                balance += sum;
                crypto[type].balance -= amount;
            }
            
            // Обновляем данные
            updateBalance();
            localStorage.setItem('gameCrypto', JSON.stringify(crypto));
            updateCryptoBalances();
            
            // Закрываем модальное окно
            closeCryptoModal();
            
            // Уведомление об успешной операции
            const notification = document.createElement('div');
            notification.className = 'game-result win animate__animated animate__bounceIn';
            notification.textContent = `${action === 'buy' ? 'Покупка' : 'Продажа'} успешна: ${amount.toFixed(type === 'btc' ? 8 : 6)} ${type.toUpperCase()} за ${sum.toLocaleString('ru-RU')} ₽`;
            notification.style.position = 'fixed';
            notification.style.bottom = '20px';
            notification.style.right = '20px';
            notification.style.zIndex = '1000';
            
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.remove();
            }, 3000);
        }

        // Проверить доход за время отсутствия
        function checkOfflineIncome() {
            const currentTime = Date.now();
            const timeDiff = currentTime - lastVisitTime; // разница в миллисекундах
            const hoursDiff = Math.floor(timeDiff / (1000 * 60 * 60)); // переводим в часы
            
            if (hoursDiff > 0) {
                let totalIncome = 0;
                for (const business in businesses) {
                    if (businesses[business].owned > 0) {
                        totalIncome += businesses[business].income * hoursDiff;
                    }
                }
                
                if (totalIncome > 0) {
                    balance += totalIncome;
                    updateBalance();
                    
                    document.getElementById('offline-income-amount').textContent = totalIncome.toLocaleString('ru-RU');
                    document.getElementById('offline-income').style.display = 'block';
                    
                    // Анимация уведомления
                    const notification = document.createElement('div');
                    notification.className = 'game-result win animate__animated animate__bounceIn';
                    notification.textContent = `Доход за время отсутствия: +${totalIncome.toLocaleString('ru-RU')} ₽`;
                    notification.style.position = 'fixed';
                    notification.style.bottom = '20px';
                    notification.style.right = '20px';
                    notification.style.zIndex = '1000';
                    
                    document.body.appendChild(notification);
                    
                    setTimeout(() => {
                        notification.remove();
                    }, 5000);
                }
            }
        }

        function animateElements() {
            // Анимация для всех элементов с классом animate-on-scroll
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('animate__animated', 'animate__fadeInUp');
                        observer.unobserve(entry.target);
                    }
                });
            }, { threshold: 0.1 });

            document.querySelectorAll('.section, .job-section, .casino-game').forEach(el => {
                observer.observe(el);
            });
        }

        // Показать раздел
        function showSection(sectionId) {
            document.querySelectorAll('.section').forEach(section => {
                section.classList.remove('active');
            });
            const activeSection = document.getElementById(sectionId + '-section');
            activeSection.classList.add('active');
            activeSection.classList.add('animate__animated', 'animate__fadeIn');
            
            // Если открываем работы, показываем меню работ
            if (sectionId === 'jobs') {
                document.querySelectorAll('.job-section').forEach(job => {
                    job.style.display = 'none';
                });
            }
            
            // Скрываем все игры казино при переходе в другой раздел
            if (sectionId !== 'casino') {
                document.querySelectorAll('.casino-game').forEach(game => {
                    game.style.display = 'none';
                });
            }
            
            // Если открываем персонажа, обновляем информацию
            if (sectionId === 'character') {
                updateCharacterInfo();
            }
            
            // Если открываем криптовалюту, обновляем цены
            if (sectionId === 'crypto') {
                updateCryptoPrices();
            }
        }

        // Обновить информацию о персонаже
        function updateCharacterInfo() {
            document.getElementById('character-nickname').textContent = character.nickname;
            document.getElementById('gardener-level').textContent = character.gardener.level;
            document.getElementById('gardener-baskets').textContent = character.gardener.baskets;
            document.getElementById('safe-cracker-level').textContent = character.safeCracker.level;
            document.getElementById('safes-cracked').textContent = character.safeCracker.safes;
            
            // Обновляем список бизнесов
            const businessesList = document.getElementById('character-businesses');
            businessesList.innerHTML = '';
            
            let hasBusiness = false;
            
            for (const business in businesses) {
                if (businesses[business].owned > 0) {
                    hasBusiness = true;
                    const businessItem = document.createElement('div');
                    businessItem.className = 'business-item';
                    
                    let businessName = '';
                    switch(business) {
                        case 'shawarma': businessName = 'Ларёк с шаурмой'; break;
                        case 'grocery': businessName = 'Магазин продуктов'; break;
                        case 'factory': businessName = 'Завод'; break;
                        case 'clothing': businessName = 'Магазин одежды'; break;
                        case 'casino': businessName = 'Казино'; break;
                    }
                    
                    businessItem.innerHTML = `
                        <span>${businessName}</span>
                        <span>1 шт.</span>
                    `;
                    
                    businessesList.appendChild(businessItem);
                }
            }
            
            if (!hasBusiness) {
                businessesList.innerHTML = '<p style="text-align: center;">У вас пока нет бизнеса</p>';
            }
            
            // Обновляем криптовалюту
            updateCharacterCrypto();
            
            // Сохраняем данные персонажа
            localStorage.setItem('gameCharacter', JSON.stringify(character));
        }

        // Изменить никнейм
        function changeNickname() {
            const input = document.getElementById('nickname-input');
            const newNickname = input.value.trim();
            const resultElement = document.getElementById('nickname-result');
            
            if (newNickname.length < 3 || newNickname.length > 20) {
                resultElement.textContent = 'Никнейм должен быть от 3 до 20 символов';
                resultElement.className = 'nickname-result lose';
                resultElement.style.display = 'block';
                return;
            }
            
            if (newNickname.toLowerCase() === character.nickname.toLowerCase()) {
                resultElement.textContent = 'Это ваш текущий никнейм';
                resultElement.className = 'nickname-result lose';
                resultElement.style.display = 'block';
                return;
            }
            
            // Проверяем, занят ли никнейм
            if (takenNicknames.includes(newNickname.toLowerCase())) {
                resultElement.textContent = 'Этот никнейм уже занят';
                resultElement.className = 'nickname-result lose';
                resultElement.style.display = 'block';
                return;
            }
            
            // Добавляем старый никнейм в список доступных (если это не дефолтный)
            if (!character.nickname.startsWith('Игрок #')) {
                takenNicknames = takenNicknames.filter(n => n !== character.nickname.toLowerCase());
            }
            
            // Обновляем никнейм
            takenNicknames.push(newNickname.toLowerCase());
            character.nickname = newNickname;
            
            resultElement.textContent = 'Никнейм успешно изменен!';
            resultElement.className = 'nickname-result win';
            resultElement.style.display = 'block';
            
            input.value = '';
            
            // Сохраняем изменения
            localStorage.setItem('gameCharacter', JSON.stringify(character));
            localStorage.setItem('gameTakenNicknames', JSON.stringify(takenNicknames));
            
            updateCharacterInfo();
        }

        // Показать работу
        function showJob(jobId) {
            document.querySelectorAll('.job-section').forEach(job => {
                job.style.display = 'none';
            });
            const jobElement = document.getElementById(jobId + '-job');
            jobElement.style.display = 'block';
            jobElement.classList.add('animate__animated', 'animate__fadeIn');
            
            // Если это садовник, создаем яблоки
            if (jobId === 'gardener') {
                createApples();
            }
            
            // Если это взломщик сейфов, генерируем новый код
            if (jobId === 'safeCracker') {
                generateNewSafeCode();
            }
        }

        // Генерировать новый код сейфа
        function generateNewSafeCode() {
            safeCode = Math.floor(Math.random() * 9000) + 1000; // 4-значное число (1000-9999)
            safeCodeAttempts = 0;
            document.getElementById('safe-code').textContent = safeCode;
            document.getElementById('safe-mask').style.height = '52%';
            document.getElementById('safe-result').style.display = 'none';
            document.getElementById('safe-input').value = '';
        }

        // Попытаться открыть сейф
        function tryOpenSafe() {
            const input = document.getElementById('safe-input');
            const guess = parseInt(input.value);
            const resultElement = document.getElementById('safe-result');
            
            if (isNaN(guess) || guess < 1000 || guess > 9999) {
                resultElement.textContent = 'Введите 4-значное число!';
                resultElement.className = 'safe-result lose';
                resultElement.style.display = 'block';
                return;
            }
            
            safeCodeAttempts++;
            
            if (guess === safeCode) {
                // Успешный взлом
                document.getElementById('safe-code').textContent = safeCode;
                document.getElementById('safe-mask').style.height = '0%';
                
                balance += 300;
                updateBalance();
                
                // Обновляем статистику взломщика
                character.safeCracker.safes++;
                if (character.safeCracker.safes % 100 === 0 && character.safeCracker.level < 15) {
                    character.safeCracker.level++;
                }
                updateCharacterInfo();
                
                resultElement.textContent = `Успех! Вы взломали сейф и получили 300 ₽ (попыток: ${safeCodeAttempts})`;
                resultElement.className = 'safe-result win';
                resultElement.style.display = 'block';
                
                // Через 2 секунды генерируем новый код
                setTimeout(generateNewSafeCode, 2000);
            } else {
                // Неудачная попытка
                const difference = Math.abs(guess - safeCode);
                let hint = '';
                
                if (difference > 1000) {
                    hint = 'Очень далеко!';
                } else if (difference > 500) {
                    hint = 'Далеко';
                } else if (difference > 100) {
                    hint = 'Ближе';
                } else {
                    hint = 'Очень близко!';
                }
                
                resultElement.textContent = `Неверный код! ${hint} (попыток: ${safeCodeAttempts})`;
                resultElement.className = 'safe-result lose';
                resultElement.style.display = 'block';
                
                // Показываем часть кода (первые 1-2 цифры в зависимости от попыток)
                const codeStr = safeCode.toString();
                let revealedCode = '';
                
                if (safeCodeAttempts >= 5) {
                    revealedCode = codeStr.substring(0, 2) + '??';
                } else if (safeCodeAttempts >= 3) {
                    revealedCode = codeStr.substring(0, 1) + '???';
                } else {
                    revealedCode = '????';
                }
                
                document.getElementById('safe-code').textContent = revealedCode;
            }
        }

        // Показать игру в казино
        function showCasinoGame(gameId) {
            document.querySelectorAll('.casino-game').forEach(game => {
                game.style.display = 'none';
            });
            const gameElement = document.getElementById(gameId + '-game');
            gameElement.style.display = 'block';
            gameElement.classList.add('animate__animated', 'animate__fadeIn');
        }

        // Создать яблоки на дереве
        function createApples() {
            const tree = document.querySelector('.tree');
            // Удаляем старые яблоки
            document.querySelectorAll('.apple').forEach(apple => apple.remove());
            
            applesCollected = 0;
            applesOnTree = 5;
            document.getElementById('apple-counter').textContent = `Собрано: ${applesCollected}/${applesOnTree} яблок`;
            
            // Создаем 5 яблок в случайных позициях
            for (let i = 0; i < 5; i++) {
                const apple = document.createElement('div');
                apple.className = 'apple apple-animation';
                
                // Случайные координаты внутри кроны дерева
                const left = 50 + Math.random() * 180;
                const top = 80 + Math.random() * 250;
                
                apple.style.left = `${left}px`;
                apple.style.top = `${top}px`;
                
                apple.onclick = function() {
                    collectApple(this);
                };
                
                // Добавляем анимацию появления
                apple.style.animationDelay = `${i * 0.2}s`;
                
                tree.appendChild(apple);
            }
        }

        // Собрать яблоко
        function collectApple(appleElement) {
            appleElement.classList.add('animate__animated', 'animate__zoomOut');
            setTimeout(() => {
                appleElement.remove();
            }, 300);
            
            applesCollected++;
            document.getElementById('apple-counter').textContent = `Собрано: ${applesCollected}/${applesOnTree} яблок`;
            
            if (applesCollected === applesOnTree) {
                setTimeout(() => {
                    const counter = document.getElementById('apple-counter');
                    counter.classList.add('animate__animated', 'animate__heartBeat');
                    setTimeout(() => {
                        counter.classList.remove('animate__animated', 'animate__heartBeat');
                    }, 1000);
                }, 300);
                
                balance += 200;
                updateBalance();
                
                // Обновляем статистику садовника
                character.gardener.baskets++;
                if (character.gardener.baskets % 100 === 0 && character.gardener.level < 15) {
                    character.gardener.level++;
                }
                updateCharacterInfo();
                
                setTimeout(createApples, 1000);
            }
        }

        // Сделать ставку в казино (Больше/Меньше)
        function placeBet() {
            const betAmount = parseInt(document.getElementById('bet-amount').value);
            
            if (isNaN(betAmount) || betAmount < 1000 || betAmount > 1000000000) {
                alert('Ставка должна быть от 1 000 до 1 000 000 000 ₽');
                return;
            }
            
            if (betAmount > balance) {
                alert('Недостаточно средств на балансе');
                return;
            }
            
            currentBet = betAmount;
            
            // Генерируем первое число (50-150)
            firstNumber = Math.floor(Math.random() * 101) + 50;
            
            document.getElementById('bet-higher').disabled = false;
            document.getElementById('bet-lower').disabled = false;
            
            document.getElementById('game-result').style.display = 'none';
            document.getElementById('numbers-display').style.display = 'flex';
            
            const firstNumberElement = document.getElementById('first-number');
            firstNumberElement.textContent = firstNumber;
            firstNumberElement.classList.add('animate__animated', 'animate__bounceIn');
            
            const secondNumberElement = document.getElementById('second-number');
            secondNumberElement.textContent = '';
            secondNumberElement.style.opacity = '0';
        }

        // Играть в "Больше или меньше"
        function playMoreLess(choice) {
            if (currentBet === 0) return;
            
            // Генерируем второе число (1-200)
            do {
                secondNumber = Math.floor(Math.random() * 200) + 1;
            } while (secondNumber === firstNumber); // Гарантируем, что числа разные
            
            const resultElement = document.getElementById('game-result');
            const secondNumberElement = document.getElementById('second-number');
            
            secondNumberElement.textContent = secondNumber;
            secondNumberElement.style.opacity = '1';
            secondNumberElement.classList.add('animate__animated', 'animate__bounceIn');
            
            let win = false;
            
            if (choice === 'higher' && secondNumber > firstNumber) {
                win = true;
            } else if (choice === 'lower' && secondNumber < firstNumber) {
                win = true;
            }
            
            if (win) {
                balance += currentBet;
                resultElement.textContent = `Поздравляем! Вы выиграли ${currentBet} ₽`;
                resultElement.className = 'game-result win animate__animated animate__bounceIn';
            } else {
                balance -= currentBet;
                resultElement.textContent = `К сожалению, вы проиграли ${currentBet} ₽`;
                resultElement.className = 'game-result lose animate__animated animate__shakeX';
            }
            
            resultElement.style.display = 'block';
            updateBalance();
            
            // Сбрасываем ставку
            currentBet = 0;
            document.getElementById('bet-higher').disabled = true;
            document.getElementById('bet-lower').disabled = true;
        }

        // Сделать ставку в рулетку
        function placeRouletteBet() {
            const betAmount = parseInt(document.getElementById('roulette-bet-amount').value);
            
            if (isNaN(betAmount) || betAmount < 1000 || betAmount > 1000000000) {
                alert('Ставка должна быть от 1 000 до 1 000 000 000 ₽');
                return;
            }
            
            if (betAmount > balance) {
                alert('Недостаточно средств на балансе');
                return;
            }
            
            currentRouletteBet = betAmount;
            
            document.getElementById('bet-red').disabled = false;
            document.getElementById('bet-black').disabled = false;
            document.getElementById('bet-green').disabled = false;
            
            document.getElementById('roulette-game-result').style.display = 'none';
            document.getElementById('roulette-result').textContent = '';
        }

        // Играть в рулетку
        function playRoulette(choice) {
            if (currentRouletteBet === 0) return;
            
            // Скрываем кнопки во время вращения
            document.getElementById('bet-red').disabled = true;
            document.getElementById('bet-black').disabled = true;
            document.getElementById('bet-green').disabled = true;
            
            // Показываем колесо рулетки
            const wheel = document.getElementById('roulette-wheel');
            wheel.style.display = 'block';
            wheel.style.animation = 'none';
            void wheel.offsetWidth; // Триггер перезапуска анимации
            wheel.style.animation = 'spin 3s cubic-bezier(0.1, 0.7, 0.1, 1) forwards';
            
            // Генерируем случайное число (0-36)
            setTimeout(() => {
                const result = Math.floor(Math.random() * 37);
                let color;
                
                if (result === 0) {
                    color = 'green';
                } else if (result % 2 === 0) {
                    color = 'black';
                } else {
                    color = 'red';
                }
                
                document.getElementById('roulette-result').textContent = `Выпало: ${result} (${color === 'red' ? 'Красное' : color === 'black' ? 'Черное' : 'Зеленое'})`;
                
                const resultElement = document.getElementById('roulette-game-result');
                let win = false;
                let multiplier = 1;
                
                if ((choice === 'red' && color === 'red') || 
                    (choice === 'black' && color === 'black')) {
                    win = true;
                    multiplier = 2;
                } else if (choice === 'green' && color === 'green') {
                    win = true;
                    multiplier = 14;
                }
                
                if (win) {
                    const winAmount = currentRouletteBet * multiplier;
                    balance += winAmount;
                    resultElement.textContent = `Поздравляем! Вы выиграли ${winAmount} ₽ (x${multiplier})`;
                    resultElement.className = 'game-result win animate__animated animate__bounceIn';
                } else {
                    balance -= currentRouletteBet;
                    resultElement.textContent = `К сожалению, вы проиграли ${currentRouletteBet} ₽`;
                    resultElement.className = 'game-result lose animate__animated animate__shakeX';
                }
                
                resultElement.style.display = 'block';
                updateBalance();
                
                // Сбрасываем ставку
                currentRouletteBet = 0;
            }, 3000);
        }

        // Покупка бизнеса
        function buyBusiness(type, price, income) {
            // Проверяем, есть ли у игрока уже бизнес
            let hasBusiness = false;
            for (const business in businesses) {
                if (businesses[business].owned > 0) {
                    hasBusiness = true;
                    break;
                }
            }
            
            if (hasBusiness) {
                alert('Вы уже владеете бизнесом! Сначала продайте текущий бизнес.');
                return;
            }
            
            if (balance >= price) {
                balance -= price;
                businesses[type].owned = 1;
                updateBalance();
                updateBusinessesDisplay();
                saveBusinesses();
                updateCharacterInfo();
                
                // Показываем кнопку продажи для этого бизнеса
                document.querySelector(`button[onclick="buyBusiness('${type}', ${price}, ${income})"]`).style.display = 'none';
                document.querySelector(`button[onclick="sellBusiness('${type}', ${price})"]`).style.display = 'block';
            } else {
                alert('Недостаточно средств для покупки этого бизнеса');
            }
        }

        // Продажа бизнеса
        function sellBusiness(type, price) {
            const sellPrice = Math.floor(price * 0.9); // 90% от стоимости
            
            balance += sellPrice;
            businesses[type].owned = 0;
            updateBalance();
            updateBusinessesDisplay();
            saveBusinesses();
            updateCharacterInfo();
            
            // Показываем кнопку покупки для этого бизнеса
            document.querySelector(`button[onclick="buyBusiness('${type}', ${price}, ${businesses[type].income})"]`).style.display = 'block';
            document.querySelector(`button[onclick="sellBusiness('${type}', ${price})"]`).style.display = 'none';
            
            // Уведомление о продаже
            const notification = document.createElement('div');
            notification.className = 'game-result win animate__animated animate__bounceIn';
            notification.textContent = `Вы продали бизнес за ${sellPrice.toLocaleString('ru-RU')} ₽`;
            notification.style.position = 'fixed';
            notification.style.bottom = '20px';
            notification.style.right = '20px';
            notification.style.zIndex = '1000';
            
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.remove();
            }, 3000);
        }

        // Обновление отображения бизнесов
        function updateBusinessesDisplay() {
            document.getElementById('shawarma-owned').textContent = `Куплено: ${businesses.shawarma.owned}`;
            document.getElementById('grocery-owned').textContent = `Куплено: ${businesses.grocery.owned}`;
            document.getElementById('clothing-owned').textContent = `Куплено: ${businesses.clothing.owned}`;
            document.getElementById('factory-owned').textContent = `Куплено: ${businesses.factory.owned}`;
            document.getElementById('casino-owned').textContent = `Куплено: ${businesses.casino.owned}`;
            
            // Общий доход
            let totalIncome = 0;
            for (const business in businesses) {
                totalIncome += businesses[business].owned * businesses[business].income;
            }
            document.getElementById('total-income').textContent = totalIncome.toLocaleString('ru-RU');
        }

        // Сохранение бизнесов
        function saveBusinesses() {
            localStorage.setItem('gameBusinesses', JSON.stringify(businesses));
        }

        // Таймер дохода (теперь в часах)
        function startIncomeTimer() {
            clearInterval(incomeInterval);
            incomeInterval = setInterval(function() {
                incomeTimer--;
                document.getElementById('income-timer').textContent = incomeTimer;
                
                if (incomeTimer <= 0) {
                    collectIncome();
                    incomeTimer = 60; // 60 минут = 1 час
                }
            }, 60000); // 1 минута = 60000 мс (для демонстрации)
        }

        // Сбор дохода
        function collectIncome() {
            let totalIncome = 0;
            for (const business in businesses) {
                if (businesses[business].owned > 0) {
                    totalIncome += businesses[business].income;
                }
            }
            
            if (totalIncome > 0) {
                balance += totalIncome;
                updateBalance();
                
                // Анимация уведомления
                const notification = document.createElement('div');
                notification.className = 'game-result win animate__animated animate__bounceIn';
                notification.textContent = `Доход от бизнеса: +${totalIncome.toLocaleString('ru-RU')} ₽`;
                notification.style.position = 'fixed';
                notification.style.bottom = '20px';
                notification.style.right = '20px';
                notification.style.zIndex = '1000';
                
                document.body.appendChild(notification);
                
                setTimeout(() => {
                    notification.remove();
                }, 3000);
            }
        }

        // Активировать промокод
        function activatePromocode() {
            const input = document.getElementById('promocode-input');
            const promocode = input.value.trim().toLowerCase();
            const resultElement = document.getElementById('promocode-result');
            
            // Проверяем, есть ли такой промокод
            if (promocodes.hasOwnProperty(promocode)) {
                const amount = promocodes[promocode];
                balance += amount;
                updateBalance();
                
                resultElement.textContent = `Промокод "${promocode}" активирован! Вы получили ${amount.toLocaleString('ru-RU')} ₽`;
                resultElement.className = 'promocode-result win';
                resultElement.style.display = 'block';
                
                // Удаляем использованный промокод (но не сохраняем, чтобы можно было ввести снова после сброса)
                
                // Сохраняем баланс
                localStorage.setItem('gameBalance', balance.toString());
            } else {
                resultElement.textContent = 'Промокод недействителен';
                resultElement.className = 'promocode-result lose';
                resultElement.style.display = 'block';
            }
            
            input.value = '';
        }

        // Обновить баланс
        function updateBalance() {
            const balanceElement = document.getElementById('balance');
            balanceElement.textContent = balance.toLocaleString('ru-RU');
            
            // Анимация изменения баланса
            balanceElement.classList.add('animate__animated', 'animate__pulse');
            setTimeout(() => {
                balanceElement.classList.remove('animate__animated', 'animate__pulse');
            }, 1000);
            
            // Сохраняем баланс в localStorage
            localStorage.setItem('gameBalance', balance.toString());
        }
    </script>
</body>
