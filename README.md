<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Word Families Flashcard - Enhanced</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" integrity="sha512-DTOQO9RWCH3ppGqcWaEA1BIZOC6xxalwEsw9c2QQeAIftl+Vegovlnee1c9QX4TctnWMn13TZye+giMm8e2LwA==" crossorigin="anonymous" referrerpolicy="no-referrer" />
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 15px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .container {
            width: 100%;
            max-width: 550px;
            background: rgba(255, 255, 255, 0.98);
            border-radius: 20px;
            padding: 20px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        h1 { 
            color: #667eea; 
            font-size: 1.8rem; 
            margin-bottom: 6px; 
            text-align: center;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }
        
        .subtitle { 
            color: #764ba2; 
            font-size: 0.9rem; 
            margin-bottom: 15px; 
            text-align: center;
            font-weight: 600;
        }

        .family-selector {
            display: flex;
            flex-wrap: wrap;
            gap: 6px;
            margin-bottom: 12px;
            padding: 10px;
            background: #f5f5f5;
            border-radius: 10px;
            max-height: 140px;
            overflow-y: auto;
            scrollbar-width: thin;
        }
        
        .family-selector::-webkit-scrollbar {
            width: 6px;
        }
        
        .family-selector::-webkit-scrollbar-track {
            background: #e0e0e0;
            border-radius: 10px;
        }
        
        .family-selector::-webkit-scrollbar-thumb {
            background: #667eea;
            border-radius: 10px;
        }

        .family-btn {
            background: white;
            border: 2px solid #ddd;
            border-radius: 10px;
            padding: 8px 12px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
            font-size: 14px;
            text-align: center;
            white-space: nowrap;
            flex-shrink: 0;
            min-width: 50px;
        }

        .family-btn.active { 
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white; 
            border-color: #667eea;
            transform: scale(1.05);
        }
        
        .family-btn:hover { 
            background: #667eea; 
            color: white;
            transform: scale(1.05);
        }

        .flashcard {
            width: 100%;
            max-width: 420px;
            height: 250px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            border-radius: 18px;
            padding: 12px;
            position: relative;
            box-shadow: 0 15px 35px rgba(102, 126, 234, 0.4);
            margin: 0 auto 15px;
        }
        
        @media (max-width: 768px) {
            .flashcard {
                height: 230px;
                padding: 10px;
            }
        }
        
        @media (orientation: landscape) and (max-height: 600px) {
            .flashcard {
                height: 200px;
                max-width: 380px;
            }
        }

        .spiral-holes {
            position: absolute;
            top: -15px;
            left: 0;
            right: 0;
            height: 30px;
            background: repeating-linear-gradient(90deg, 
                transparent 0px, 
                transparent 25px, 
                rgba(255, 255, 255, 0.95) 25px, 
                rgba(255, 255, 255, 0.95) 38px);
            border-radius: 20px 20px 0 0;
        }

        .card-header {
            background: white;
            height: 50px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 15px;
            margin: 10px 0 12px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        .family-badge {
            background: linear-gradient(135deg, #f093fb, #f5576c);
            border-radius: 10px;
            padding: 8px 14px;
            font-size: 20px;
            font-weight: bold;
            color: white;
            min-width: 60px;
            text-align: center;
            box-shadow: 0 3px 8px rgba(245, 87, 108, 0.3);
        }

        .gujarati-meaning-header {
            font-size: 14px;
            font-weight: bold;
            color: #764ba2;
            background: #f0f0f0;
            padding: 8px 12px;
            border-radius: 18px;
            flex: 1;
            text-align: center;
            margin: 0 12px;
        }

        .pronounce-btn {
            background: #667eea;
            border: none;
            border-radius: 50%;
            width: 42px;
            height: 42px;
            color: white;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s;
            font-size: 20px;
            box-shadow: 0 3px 8px rgba(102, 126, 234, 0.3);
        }

        .pronounce-btn:hover { 
            background: #764ba2; 
            transform: scale(1.15) rotate(10deg);
        }

        .pronounce-btn:active {
            transform: scale(0.95);
        }

        .card-main {
            background: white;
            height: 168px;
            border-radius: 12px;
            padding: 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }
        
        @media (max-width: 768px) {
            .card-main {
                height: 150px;
                padding: 12px;
            }
        }
        
        @media (orientation: landscape) and (max-height: 600px) {
            .card-main {
                height: 130px;
                padding: 10px;
            }
        }

        .main-word {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .click-hint {
            background: linear-gradient(135deg, #ffeaa7, #fdcb6e);
            padding: 5px 12px;
            border-radius: 18px;
            font-size: 12px;
            color: #d63031;
            font-weight: bold;
            animation: pulse 2s infinite;
            box-shadow: 0 2px 6px rgba(253, 203, 110, 0.4);
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.08); }
        }

        .word-display {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 3px;
        }

        .prefix-part {
            color: #d32f2f;
            font-size: 44px;
            font-weight: 900;
            text-shadow: 3px 3px 6px rgba(211, 47, 47, 0.3);
            letter-spacing: 1px;
            cursor: pointer;
            transition: transform 0.3s, color 0.3s;
        }

        .prefix-part:hover {
            transform: scale(1.1) rotate(2deg);
            color: #b71c1c;
        }

        .prefix-part:active {
            transform: scale(0.95);
        }

        .suffix-part {
            color: #1565c0;
            font-size: 44px;
            font-weight: 900;
            text-shadow: 3px 3px 6px rgba(21, 101, 192, 0.3);
            letter-spacing: 1px;
            user-select: none;
        }

        @media (max-width: 768px) {
            .prefix-part, .suffix-part {
                font-size: 38px;
            }
        }

        @media (max-width: 480px) {
            .prefix-part, .suffix-part {
                font-size: 34px;
            }
        }
        
        @media (orientation: landscape) and (max-height: 600px) {
            .prefix-part, .suffix-part {
                font-size: 36px;
            }
        }

        .controls {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin: 18px auto;
            max-width: 420px;
            gap: 10px;
        }

        .nav-btn {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            font-size: 24px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s;
            box-shadow: 0 4px 12px rgba(102, 126, 234, 0.3);
        }

        .nav-btn:hover { 
            transform: scale(1.15) rotate(5deg);
            box-shadow: 0 6px 18px rgba(102, 126, 234, 0.5);
        }

        .nav-btn:active {
            transform: scale(0.9);
        }
        
        .nav-btn:disabled { 
            background: #cccccc; 
            cursor: not-allowed;
            box-shadow: none;
            transform: none;
        }

        .control-center { 
            display: flex; 
            gap: 10px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .shuffle-btn, .auto-play-btn {
            background: linear-gradient(135deg, #fa709a, #fee140);
            color: white;
            border: none;
            border-radius: 22px;
            padding: 10px 18px;
            cursor: pointer;
            font-size: 14px;
            font-weight: bold;
            transition: all 0.3s;
            box-shadow: 0 4px 12px rgba(250, 112, 154, 0.3);
        }

        .shuffle-btn:hover, .auto-play-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 18px rgba(250, 112, 154, 0.4);
        }

        .auto-play-btn.active { 
            background: linear-gradient(135deg, #11998e, #38ef7d);
        }

        .progress {
            margin-top: 15px;
            text-align: center;
            font-weight: bold;
            color: #667eea;
            font-size: 16px;
        }

        .progress-bar {
            width: 100%;
            max-width: 420px;
            height: 8px;
            background: #e0e0e0;
            border-radius: 10px;
            margin: 10px auto;
            overflow: hidden;
            box-shadow: inset 0 2px 4px rgba(0,0,0,0.1);
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #667eea, #764ba2);
            border-radius: 10px;
            transition: width 0.4s ease;
        }

        .score-display {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 12px;
            margin-top: 15px;
            flex-wrap: wrap;
        }

        .score-item {
            background: linear-gradient(135deg, #e0c3fc, #8ec5fc);
            padding: 10px 16px;
            border-radius: 18px;
            font-weight: bold;
            color: #2d3436;
            font-size: 14px;
            box-shadow: 0 3px 8px rgba(0,0,0,0.1);
        }

        .school-footer {
            margin-top: 18px;
            font-weight: bold;
            padding: 12px;
            background: linear-gradient(135deg, #667eea, #764ba2, #f093fb, #667eea);
            background-size: 300% 300%;
            border-radius: 12px;
            text-align: center;
            font-size: 16px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            animation: shimmer 3s ease infinite;
            font-family: 'Brush Script MT', 'Lucida Handwriting', cursive;
            color: #fff;
            text-shadow: 
                0 0 10px rgba(255,255,255,0.8),
                0 0 20px rgba(255,255,255,0.6),
                0 0 30px rgba(255,255,255,0.4),
                2px 2px 4px rgba(0,0,0,0.3);
            letter-spacing: 1px;
        }

        @keyframes shimmer {
            0% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
            100% {
                background-position: 0% 50%;
            }
        }

        .quiz-btn {
            background: linear-gradient(135deg, #f093fb, #f5576c);
            color: white;
            border: none;
            border-radius: 18px;
            padding: 10px 16px;
            font-size: 14px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 3px 8px rgba(245, 87, 108, 0.3);
            display: inline-flex;
            align-items: center;
            gap: 5px;
        }

        .quiz-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(245, 87, 108, 0.4);
        }

        #quizSection {
            background: linear-gradient(135deg, #e0c3fc, #8ec5fc);
            padding: 20px;
            border-radius: 18px;
            max-width: 420px;
            margin: 0 auto;
            box-shadow: 0 8px 20px rgba(0,0,0,0.15);
        }

        #quizQuestion {
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 15px;
            color: #2d3436;
            text-align: center;
            background: white;
            padding: 15px;
            border-radius: 12px;
            box-shadow: 0 3px 8px rgba(0,0,0,0.1);
        }

        #quizOptions {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-bottom: 15px;
        }

        .quiz-option {
            background: white;
            border: 3px solid transparent;
            border-radius: 12px;
            padding: 14px 10px;
            cursor: pointer;
            font-weight: bold;
            text-align: center;
            transition: all 0.3s;
            font-size: 15px;
            box-shadow: 0 3px 8px rgba(0,0,0,0.1);
        }

        .quiz-option:hover:not(.correct):not(.wrong) {
            background: #f8f9fa;
            border-color: #667eea;
            transform: scale(1.05);
        }

        .quiz-option.correct {
            background: #38ef7d;
            color: white;
            border-color: #11998e;
            animation: correctPulse 0.5s;
        }

        .quiz-option.wrong {
            background: #ff6b6b;
            color: white;
            border-color: #ee5a6f;
            animation: shake 0.5s;
        }

        @keyframes correctPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            75% { transform: translateX(10px); }
        }

        #quizResult {
            margin-top: 15px;
            font-weight: bold;
            text-align: center;
            font-size: 16px;
            padding: 10px;
            border-radius: 10px;
            background: white;
            box-shadow: 0 3px 8px rgba(0,0,0,0.1);
        }

        #quizScore {
            margin-top: 10px;
            text-align: center;
            font-weight: bold;
            color: #2d3436;
            font-size: 18px;
            background: white;
            padding: 10px;
            border-radius: 10px;
            box-shadow: 0 3px 8px rgba(0,0,0,0.1);
        }

        #nextQ {
            margin: 15px auto 0;
            display: none;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            cursor: pointer;
            font-size: 24px;
            box-shadow: 0 4px 12px rgba(102, 126, 234, 0.3);
            transition: all 0.3s;
        }

        #nextQ:hover {
            transform: scale(1.15);
            box-shadow: 0 6px 18px rgba(102, 126, 234, 0.5);
        }

        .quiz-home-btn {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            border: none;
            border-radius: 20px;
            padding: 10px 20px;
            font-size: 14px;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 3px 8px rgba(102, 126, 234, 0.3);
            transition: all 0.3s;
        }

        .quiz-home-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(102, 126, 234, 0.5);
        }

        .fade-in {
            animation: fadeIn 0.3s ease-in;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>📚 WORD FAMILIES LIST</h1>
        <p class="subtitle">Learn word families with Gujarati meanings • ઉપસર્ગ અને પ્રત્યય સાથે શીખો</p>

        <div class="family-selector" id="familySelector"></div>

        <div id="flashcardSection">
            <div class="flashcard">
                <div class="spiral-holes"></div>
                <div class="card-header">
                    <div class="family-badge" id="familyBadge">ack</div>
                    <div class="gujarati-meaning-header" id="gujarati">હુમલો</div>
                    <button class="pronounce-btn" onclick="pronounce()" title="ઉચ્ચાર સાંભળો">
                        🔊
                    </button>
                </div>
                <div class="card-main">
                    <div class="main-word">
                        <div class="click-hint">👇 લાલ ભાગ પર ક્લિક કરો</div>
                        <div class="word-display">
                            <span class="prefix-part" id="prefixPart" onclick="nextWord()">Att</span>
                            <span class="suffix-part" id="suffixPart">ack</span>
                        </div>
                    </div>
                </div>
            </div>

            <div class="controls">
                <button class="nav-btn" id="prevBtn" onclick="prevWord()">
                    ⬅️
                </button>
                <div class="control-center">
                    <button class="shuffle-btn" onclick="shuffle()">
                        🔀 Shuffle
                    </button>
                    <button class="auto-play-btn" id="autoBtn" onclick="toggleAuto()">
                        ▶️ Auto
                    </button>
                </div>
                <button class="nav-btn" id="nextBtn" onclick="nextWord()">
                    ➡️
                </button>
            </div>

            <div class="progress">
                <div class="progress-bar">
                    <div class="progress-fill" id="progress"></div>
                </div>
                <span id="current">1</span>/<span id="total">10</span> words in <strong id="currentFamily">-ack</strong>
            </div>

            <div class="score-display">
                <div class="score-item">
                    👁️ Viewed: <span id="viewed">0</span>
                </div>
                <div class="score-item">
                    🔊 Pronounced: <span id="pronounced">0</span>
                </div>
                <button class="quiz-btn" onclick="toggleQuiz()" id="quizBtn">
                    ❓ Quiz Mode
                </button>
            </div>

            <div class="school-footer">
                Makvana Sanjaysir piparadi-2 primary school
            </div>
        </div>

        <div id="quizSection" style="display: none;">
            <div style="text-align: center; margin-bottom: 15px;">
                <button class="quiz-home-btn" onclick="toggleQuiz()">
                    🏠 પાછા જાઓ (Back to Home)
                </button>
            </div>
            <div id="quizQuestion"></div>
            <div id="quizOptions"></div>
            <div id="quizResult"></div>
            <div id="quizScore">Score: 0/0</div>
            <button onclick="generateQuiz()" id="nextQ">
                ➡️
            </button>
        </div>
    </div>

    <script>
        const wordFamilies = {
            'ack': [
                { prefix: 'Att', suffix: 'ack', g: 'હુમલો' },
                { prefix: 'B', suffix: 'ack', g: 'પાછળ' },
                { prefix: 'Kn', suffix: 'ack', g: 'કુશળતા' },
                { prefix: 'L', suffix: 'ack', g: 'અભાવ' },
                { prefix: 'Qu', suffix: 'ack', g: 'બતકની અવાજ' },
                { prefix: 'R', suffix: 'ack', g: 'રેક' },
                { prefix: 'S', suffix: 'ack', g: 'થેલી' },
                { prefix: 'St', suffix: 'ack', g: 'ઢગલો' },
                { prefix: 'Tr', suffix: 'ack', g: 'પાટો' },
                { prefix: 'Wh', suffix: 'ack', g: 'મારવું' }
            ],
            'ain': [
                { prefix: 'Br', suffix: 'ain', g: 'મગજ' },
                { prefix: 'Ch', suffix: 'ain', g: 'સાંકળ' },
                { prefix: 'Compl', suffix: 'ain', g: 'ફરિયાદ' },
                { prefix: 'Expl', suffix: 'ain', g: 'સમજાવવું' },
                { prefix: 'G', suffix: 'ain', g: 'લાભ' },
                { prefix: 'M', suffix: 'ain', g: 'મુખ્ય' },
                { prefix: 'Pl', suffix: 'ain', g: 'સાદો' },
                { prefix: 'Tr', suffix: 'ain', g: 'ટ્રેન' },
                { prefix: 'Sp', suffix: 'ain', g: 'સ્પેન' },
                { prefix: 'V', suffix: 'ain', g: 'નિરર્થક' }
            ],
            'ake': [
                { prefix: 'Aw', suffix: 'ake', g: 'જાગૃત' },
                { prefix: 'B', suffix: 'ake', g: 'શેકવું' },
                { prefix: 'C', suffix: 'ake', g: 'કેક' },
                { prefix: 'L', suffix: 'ake', g: 'સરોવર' },
                { prefix: 'M', suffix: 'ake', g: 'બનાવવું' },
                { prefix: 'Qu', suffix: 'ake', g: 'ધરતીકંપ' },
                { prefix: 'R', suffix: 'ake', g: 'ભૂંગળી' },
                { prefix: 'S', suffix: 'ake', g: 'સાકે પીણું' },
                { prefix: 'Sn', suffix: 'ake', g: 'સાપ' },
                { prefix: 'T', suffix: 'ake', g: 'લેવું' }
            ],
            'ale': [
                { prefix: '', suffix: 'Ale', g: 'બિયર' },
                { prefix: 'B', suffix: 'ale', g: 'ગાંઠ' },
                { prefix: 'D', suffix: 'ale', g: 'ખીણ' },
                { prefix: 'Fem', suffix: 'ale', g: 'સ્ત્રી' },
                { prefix: 'G', suffix: 'ale', g: 'તોફાન' },
                { prefix: 'M', suffix: 'ale', g: 'પુરુષ' },
                { prefix: 'P', suffix: 'ale', g: 'નિસ્તેજ' },
                { prefix: 'S', suffix: 'ale', g: 'વેચાણ' },
                { prefix: 'T', suffix: 'ale', g: 'વાર્તા' },
                { prefix: 'Wh', suffix: 'ale', g: 'વ્હેલ માછલી' }
            ],
            'all': [
                { prefix: 'B', suffix: 'all', g: 'દડો' },
                { prefix: 'C', suffix: 'all', g: 'બોલાવવું' },
                { prefix: 'F', suffix: 'all', g: 'પડવું' },
                { prefix: 'H', suffix: 'all', g: 'હોલ' },
                { prefix: 'M', suffix: 'all', g: 'મોલ' },
                { prefix: 'Sm', suffix: 'all', g: 'નાનું' },
                { prefix: 'Squ', suffix: 'all', g: 'વાવાઝોડું' },
                { prefix: 'St', suffix: 'all', g: 'સ્ટોલ' },
                { prefix: 'T', suffix: 'all', g: 'ઊંચું' },
                { prefix: 'W', suffix: 'all', g: 'દીવાલ' }
            ],
            'ame': [
                { prefix: 'Bl', suffix: 'ame', g: 'દોષ' },
                { prefix: 'C', suffix: 'ame', g: 'આવ્યો' },
                { prefix: 'D', suffix: 'ame', g: 'મહિલા' },
                { prefix: 'F', suffix: 'ame', g: 'પ્રસિદ્ધિ' },
                { prefix: 'G', suffix: 'ame', g: 'રમત' },
                { prefix: 'L', suffix: 'ame', g: 'લંગડું' },
                { prefix: 'N', suffix: 'ame', g: 'નામ' },
                { prefix: 'S', suffix: 'ame', g: 'સમાન' },
                { prefix: 'Sh', suffix: 'ame', g: 'શરમ' },
                { prefix: 'T', suffix: 'ame', g: 'પાળેલું' }
            ],
            'an': [
                { prefix: 'B', suffix: 'an', g: 'પ્રતિબંધ' },
                { prefix: 'Br', suffix: 'an', g: 'ભૂકી' },
                { prefix: 'C', suffix: 'an', g: 'ડબ્બો/શકે' },
                { prefix: 'F', suffix: 'an', g: 'પંખો' },
                { prefix: 'Jap', suffix: 'an', g: 'જાપાન' },
                { prefix: 'M', suffix: 'an', g: 'માણસ' },
                { prefix: 'P', suffix: 'an', g: 'તપેલી' },
                { prefix: 'Pl', suffix: 'an', g: 'યોજના' },
                { prefix: 'T', suffix: 'an', g: 'ભૂરો રંગ' },
                { prefix: 'V', suffix: 'an', g: 'વાન' }
            ],
            'ank': [
                { prefix: 'B', suffix: 'ank', g: 'બેંક' },
                { prefix: 'Bl', suffix: 'ank', g: 'ખાલી' },
                { prefix: 'Cr', suffix: 'ank', g: 'હેન્ડલ' },
                { prefix: 'Dr', suffix: 'ank', g: 'પીધું' },
                { prefix: 'Fl', suffix: 'ank', g: 'બાજુ' },
                { prefix: 'R', suffix: 'ank', g: 'દરજ્જો' },
                { prefix: 'Shr', suffix: 'ank', g: 'સંકોચાયું' },
                { prefix: 'Sp', suffix: 'ank', g: 'ચાંટો મારવો' },
                { prefix: 'T', suffix: 'ank', g: 'ટાંકી' },
                { prefix: 'Th', suffix: 'ank', g: 'આભાર' }
            ],
            'ap': [
                { prefix: 'C', suffix: 'ap', g: 'ટોપી' },
                { prefix: 'Cl', suffix: 'ap', g: 'તાળી' },
                { prefix: 'Fl', suffix: 'ap', g: 'ફફડાવવું' },
                { prefix: 'L', suffix: 'ap', g: 'ખોળો' },
                { prefix: 'M', suffix: 'ap', g: 'નકશો' },
                { prefix: 'Scr', suffix: 'ap', g: 'કચરો/ભંગાર' },
                { prefix: 'Sl', suffix: 'ap', g: 'થપ્પડ' },
                { prefix: 'T', suffix: 'ap', g: 'નળ' },
                { prefix: 'Tr', suffix: 'ap', g: 'જાળ' },
                { prefix: 'Wr', suffix: 'ap', g: 'લપેટવું' }
            ],
            'ash': [
                { prefix: 'C', suffix: 'ash', g: 'રોકડ' },
                { prefix: 'Cl', suffix: 'ash', g: 'અથડામણ' },
                { prefix: 'Cr', suffix: 'ash', g: 'અકસ્માત' },
                { prefix: 'D', suffix: 'ash', g: 'ઝડપી દોડ' },
                { prefix: 'Fl', suffix: 'ash', g: 'ચમક' },
                { prefix: 'L', suffix: 'ash', g: 'ફટકો' },
                { prefix: 'M', suffix: 'ash', g: 'છૂંદવું' },
                { prefix: 'R', suffix: 'ash', g: 'ખરજવું' },
                { prefix: 'Spl', suffix: 'ash', g: 'છાંટવું' },
                { prefix: 'St', suffix: 'ash', g: 'છુપાવવું' }
            ],
            'at': [
                { prefix: '', suffix: 'At', g: 'પર' },
                { prefix: 'Br', suffix: 'at', g: 'બદમાશ બાળક' },
                { prefix: 'C', suffix: 'at', g: 'બિલાડી' },
                { prefix: 'Ch', suffix: 'at', g: 'વાતચીત' },
                { prefix: 'F', suffix: 'at', g: 'ચરબી/જાડું' },
                { prefix: 'H', suffix: 'at', g: 'ટોપી' },
                { prefix: 'M', suffix: 'at', g: 'સાદડી' },
                { prefix: 'Sl', suffix: 'at', g: 'પાટી' },
                { prefix: 'Th', suffix: 'at', g: 'તે' },
                { prefix: 'V', suffix: 'at', g: 'ચાન' }
            ],
            'ate': [
                { prefix: 'Ab', suffix: 'ate', g: 'ઓછું થવું' },
                { prefix: '', suffix: 'Ate', g: 'ખાધું' },
                { prefix: 'D', suffix: 'ate', g: 'તારીખ' },
                { prefix: 'F', suffix: 'ate', g: 'નસીબ' },
                { prefix: 'G', suffix: 'ate', g: 'દરવાજો' },
                { prefix: 'Gr', suffix: 'ate', g: 'છીણવું/જાળી' },
                { prefix: 'L', suffix: 'ate', g: 'મોડું' },
                { prefix: 'Pl', suffix: 'ate', g: 'થાળી' },
                { prefix: 'Sk', suffix: 'ate', g: 'સ્કેટ' },
                { prefix: 'St', suffix: 'ate', g: 'રાજ્ય' }
            ],
            'aw': [
                { prefix: 'Cl', suffix: 'aw', g: 'પંજો' },
                { prefix: 'Dr', suffix: 'aw', g: 'દોરવું' },
                { prefix: 'Fl', suffix: 'aw', g: 'ખામી' },
                { prefix: 'J', suffix: 'aw', g: 'જડબું' },
                { prefix: 'L', suffix: 'aw', g: 'કાયદો' },
                { prefix: 'P', suffix: 'aw', g: 'પંજો' },
                { prefix: 'R', suffix: 'aw', g: 'કાચું' },
                { prefix: 'S', suffix: 'aw', g: 'કરવત' },
                { prefix: 'Str', suffix: 'aw', g: 'કાળમ' },
                { prefix: 'Th', suffix: 'aw', g: 'પીગળવું' }
            ],
            'ay': [
                { prefix: 'Aw', suffix: 'ay', g: 'દૂર' },
                { prefix: 'Cl', suffix: 'ay', g: 'માટી' },
                { prefix: 'D', suffix: 'ay', g: 'દિવસ' },
                { prefix: 'Displ', suffix: 'ay', g: 'પ્રદર્શન' },
                { prefix: 'G', suffix: 'ay', g: 'ખુશ' },
                { prefix: 'Pr', suffix: 'ay', g: 'પ્રાર્થના' },
                { prefix: 'S', suffix: 'ay', g: 'કહેવું' },
                { prefix: 'St', suffix: 'ay', g: 'રહેવું' },
                { prefix: 'Tod', suffix: 'ay', g: 'આજે' },
                { prefix: 'Tr', suffix: 'ay', g: 'ટ્રે' }
            ],
            'eat': [
                { prefix: 'B', suffix: 'eat', g: 'મારવું' },
                { prefix: 'Bl', suffix: 'eat', g: 'ઘેટાંનો અવાજ' },
                { prefix: 'Ch', suffix: 'eat', g: 'છેતરવું' },
                { prefix: 'Cl', suffix: 'eat', g: 'ફૂટબોલ શૂઝ' },
                { prefix: 'H', suffix: 'eat', g: 'ગરમી' },
                { prefix: 'M', suffix: 'eat', g: 'માંસ' },
                { prefix: 'N', suffix: 'eat', g: 'સ્વચ્છ' },
                { prefix: 'S', suffix: 'eat', g: 'બેઠક' },
                { prefix: 'Tr', suffix: 'eat', g: 'સારવાર' },
                { prefix: 'Wh', suffix: 'eat', g: 'ઘઉં' }
            ],
            'ell': [
                { prefix: 'B', suffix: 'ell', g: 'ઘંટડી' },
                { prefix: 'C', suffix: 'ell', g: 'કોષ' },
                { prefix: 'Dw', suffix: 'ell', g: 'રહેવું' },
                { prefix: 'F', suffix: 'ell', g: 'પડ્યું' },
                { prefix: 'Farew', suffix: 'ell', g: 'વિદાય' },
                { prefix: 'S', suffix: 'ell', g: 'વેચવું' },
                { prefix: 'Sh', suffix: 'ell', g: 'છીપલું' },
                { prefix: 'Sm', suffix: 'ell', g: 'ગંધ' },
                { prefix: 'T', suffix: 'ell', g: 'કહેવું' },
                { prefix: 'Y', suffix: 'ell', g: 'બૂમ પાડવી' }
            ],
            'est': [
                { prefix: 'B', suffix: 'est', g: 'શ્રેષ્ઠ' },
                { prefix: 'Ch', suffix: 'est', g: 'છાતી' },
                { prefix: 'Cr', suffix: 'est', g: 'શિખર' },
                { prefix: 'J', suffix: 'est', g: 'મજાક' },
                { prefix: 'N', suffix: 'est', g: 'માળો' },
                { prefix: 'P', suffix: 'est', g: 'જીવાત' },
                { prefix: 'R', suffix: 'est', g: 'આરામ' },
                { prefix: 'T', suffix: 'est', g: 'કસોટી' },
                { prefix: 'V', suffix: 'est', g: 'વેસ્ટ' },
                { prefix: 'W', suffix: 'est', g: 'પશ્ચિમ' }
            ],
            'ice': [
                { prefix: 'D', suffix: 'ice', g: 'પાસા' },
                { prefix: '', suffix: 'Ice', g: 'બરફ' },
                { prefix: 'L', suffix: 'ice', g: 'જૂ' },
                { prefix: 'M', suffix: 'ice', g: 'ઉંદર' },
                { prefix: 'N', suffix: 'ice', g: 'સરસ' },
                { prefix: 'Pr', suffix: 'ice', g: 'કિંમત' },
                { prefix: 'R', suffix: 'ice', g: 'ચોખા' },
                { prefix: 'Sl', suffix: 'ice', g: 'ટુકડો' },
                { prefix: 'Spl', suffix: 'ice', g: 'જોડવું' },
                { prefix: 'Tw', suffix: 'ice', g: 'બે વાર' },
                { prefix: 'V', suffix: 'ice', g: 'દુર્ગુણ' }
            ],
            'ine': [
                { prefix: 'Br', suffix: 'ine', g: 'ખારું પાણી' },
                { prefix: 'Decl', suffix: 'ine', g: 'ઘટાડો' },
                { prefix: 'Def', suffix: 'ine', g: 'વ્યાખ્યા' },
                { prefix: 'D', suffix: 'ine', g: 'જમવું' },
                { prefix: 'F', suffix: 'ine', g: 'સારું' },
                { prefix: 'M', suffix: 'ine', g: 'મારું' },
                { prefix: 'N', suffix: 'ine', g: 'નવ' },
                { prefix: 'Sh', suffix: 'ine', g: 'ચમકવું' },
                { prefix: 'Wh', suffix: 'ine', g: 'રડવું' },
                { prefix: 'W', suffix: 'ine', g: 'વાઇન' }
            ],
            'ide': [
                { prefix: 'Br', suffix: 'ide', g: 'નવવધૂ' },
                { prefix: 'Dec', suffix: 'ide', g: 'નિર્ણય' },
                { prefix: 'Gu', suffix: 'ide', g: 'માર્ગદર્શક' },
                { prefix: 'H', suffix: 'ide', g: 'છુપાવવું' },
                { prefix: 'R', suffix: 'ide', g: 'સવારી' },
                { prefix: 'S', suffix: 'ide', g: 'બાજુ' },
                { prefix: 'Sl', suffix: 'ide', g: 'સરકવું' },
                { prefix: 'Str', suffix: 'ide', g: 'લાંબા પગલાં' },
                { prefix: 'T', suffix: 'ide', g: 'ભરતી' },
                { prefix: 'W', suffix: 'ide', g: 'પહોળું' }
            ],
            'ick': [
                { prefix: 'Br', suffix: 'ick', g: 'ઈંટ' },
                { prefix: 'Fl', suffix: 'ick', g: 'ઝટકો' },
                { prefix: 'K', suffix: 'ick', g: 'લાત' },
                { prefix: 'L', suffix: 'ick', g: 'ચાટવું' },
                { prefix: 'N', suffix: 'ick', g: 'કાપ/ઉપનામ' },
                { prefix: 'P', suffix: 'ick', g: 'પસંદ કરવું' },
                { prefix: 'St', suffix: 'ick', g: 'લાકડી' },
                { prefix: 'Th', suffix: 'ick', g: 'જાડું' },
                { prefix: 'T', suffix: 'ick', g: 'ટીક/ચિન્હ' },
                { prefix: 'Tr', suffix: 'ick', g: 'યુક્તિ' }
            ],
            'in': [
                { prefix: 'B', suffix: 'in', g: 'ડબ્બો' },
                { prefix: 'Ch', suffix: 'in', g: 'ચવાણ' },
                { prefix: 'Gr', suffix: 'in', g: 'સ્મિત' },
                { prefix: '', suffix: 'In', g: 'માં' },
                { prefix: 'K', suffix: 'in', g: 'સગા' },
                { prefix: 'Sh', suffix: 'in', g: 'પીંડલી' },
                { prefix: 'Sk', suffix: 'in', g: 'ચામડી' },
                { prefix: 'Tw', suffix: 'in', g: 'જોડિયું' },
                { prefix: 'W', suffix: 'in', g: 'જીતવું' },
                { prefix: 'With', suffix: 'in', g: 'અંદર' }
            ],
            'ight': [
                { prefix: 'Br', suffix: 'ight', g: 'તેજસ્વી' },
                { prefix: 'Del', suffix: 'ight', g: 'આનંદ' },
                { prefix: 'F', suffix: 'ight', g: 'લડવું' },
                { prefix: 'Fl', suffix: 'ight', g: 'ઉડાન' },
                { prefix: 'L', suffix: 'ight', g: 'પ્રકાશ' },
                { prefix: 'M', suffix: 'ight', g: 'શક્તિ' },
                { prefix: 'N', suffix: 'ight', g: 'રાત' },
                { prefix: 'S', suffix: 'ight', g: 'દૃષ્ટિ' },
                { prefix: 'T', suffix: 'ight', g: 'ચુસ્ત' },
                { prefix: 'Ton', suffix: 'ight', g: 'આજની રાત' }
            ],
            'illy': [
                { prefix: 'B', suffix: 'ill', g: 'બિલ' },
                { prefix: 'Ch', suffix: 'ill', g: 'ઠંડક' },
                { prefix: 'Dr', suffix: 'ill', g: 'કવાયત' },
                { prefix: 'F', suffix: 'ill', g: 'ભરવું' },
                { prefix: 'K', suffix: 'ill', g: 'મારવું' },
                { prefix: 'Shr', suffix: 'ill', g: 'તીક્ષ્ણ' },
                { prefix: 'Sk', suffix: 'ill', g: 'કુશળતા' },
                { prefix: 'Sp', suffix: 'ill', g: 'ઢોળવું' },
                { prefix: 'Thr', suffix: 'ill', g: 'રોમાંચ' },
                { prefix: 'W', suffix: 'ill', g: 'ઇચ્છા' }
            ],
            'ing': [
                { prefix: 'Br', suffix: 'ing', g: 'લાવો' },
                { prefix: 'K', suffix: 'ing', g: 'રાજા' },
                { prefix: 'P', suffix: 'ing', g: 'પિંગ' },
                { prefix: 'R', suffix: 'ing', g: 'વીંટી' },
                { prefix: 'S', suffix: 'ing', g: 'ગાવું' },
                { prefix: 'Spr', suffix: 'ing', g: 'વસંત' },
                { prefix: 'St', suffix: 'ing', g: 'ડંખ' },
                { prefix: 'Str', suffix: 'ing', g: 'દોરી' },
                { prefix: 'Th', suffix: 'ing', g: 'વસ્તુ' },
                { prefix: 'W', suffix: 'ing', g: 'પાંખ' }
            ],
            'ink': [
                { prefix: 'Bl', suffix: 'ink', g: 'આંખ મીંચવી' },
                { prefix: 'Dr', suffix: 'ink', g: 'પીવું' },
                { prefix: 'F', suffix: 'ink', g: 'બેવફા' },
                { prefix: 'L', suffix: 'ink', g: 'કડી' },
                { prefix: 'M', suffix: 'ink', g: 'મિંક પ્રાણી' },
                { prefix: 'P', suffix: 'ink', g: 'ગુલાબી' },
                { prefix: 'R', suffix: 'ink', g: 'આઇસ રિંક' },
                { prefix: 'S', suffix: 'ink', g: 'સિંક/ડૂબવું' },
                { prefix: 'St', suffix: 'ink', g: 'દુર્ગંધ' },
                { prefix: 'W', suffix: 'ink', g: 'આંખ મારવી' }
            ],
            'ip': [
                { prefix: 'D', suffix: 'ip', g: 'ડૂબાડવું' },
                { prefix: 'Gr', suffix: 'ip', g: 'પકડ' },
                { prefix: 'H', suffix: 'ip', g: 'નિતંબ' },
                { prefix: 'L', suffix: 'ip', g: 'હોઠ' },
                { prefix: 'R', suffix: 'ip', g: 'ફાડવું' },
                { prefix: 'S', suffix: 'ip', g: 'ચૂસકી' },
                { prefix: 'Sk', suffix: 'ip', g: 'કૂદવું' },
                { prefix: 'Str', suffix: 'ip', g: 'પટ્ટી' },
                { prefix: 'Tr', suffix: 'ip', g: 'સફર' },
                { prefix: 'Wh', suffix: 'ip', g: 'ચાબુક' }
            ],
            'it': [
                { prefix: 'Adm', suffix: 'it', g: 'સ્વીકારવું' },
                { prefix: 'B', suffix: 'it', g: 'ટુકડો' },
                { prefix: 'F', suffix: 'it', g: 'યોગ્ય' },
                { prefix: 'Fl', suffix: 'it', g: 'ઉડવું' },
                { prefix: 'Gr', suffix: 'it', g: 'હિંમત' },
                { prefix: 'Kn', suffix: 'it', g: 'ગૂંથવું' },
                { prefix: 'L', suffix: 'it', g: 'પ્રકાશ' },
                { prefix: 'P', suffix: 'it', g: 'ખાડો' },
                { prefix: 'Qu', suffix: 'it', g: 'છોડવું' },
                { prefix: 'Spl', suffix: 'it', g: 'વિભાજન' }
            ],
            'ock': [
                { prefix: 'Bl', suffix: 'ock', g: 'બ્લોક' },
                { prefix: 'Cl', suffix: 'ock', g: 'ઘડિયાળ' },
                { prefix: 'D', suffix: 'ock', g: 'બંદર' },
                { prefix: 'Fr', suffix: 'ock', g: 'ફ્રોક' },
                { prefix: 'L', suffix: 'ock', g: 'તાળું' },
                { prefix: 'M', suffix: 'ock', g: 'મજાક' },
                { prefix: 'R', suffix: 'ock', g: 'ખડક' },
                { prefix: 'Sh', suffix: 'ock', g: 'આંચકો' },
                { prefix: 'S', suffix: 'ock', g: 'મોજા' },
                { prefix: 'St', suffix: 'ock', g: 'સ્ટોક' }
            ],
            'oke': [
                { prefix: 'Aw', suffix: 'oke', g: 'જાગ્યો' },
                { prefix: 'Bl', suffix: 'oke', g: 'વ્યક્તિ' },
                { prefix: 'Ch', suffix: 'oke', g: 'ગૂંગળામણ' },
                { prefix: 'J', suffix: 'oke', g: 'મજાક' },
                { prefix: 'P', suffix: 'oke', g: 'ધીંગામારો' },
                { prefix: 'Sm', suffix: 'oke', g: 'ધુમાડો' },
                { prefix: 'Sp', suffix: 'oke', g: 'બોલ્યો' },
                { prefix: 'Str', suffix: 'oke', g: 'હથોડો/સ્ટ્રોક' },
                { prefix: 'W', suffix: 'oke', g: 'જાગ્યો' },
                { prefix: 'Y', suffix: 'oke', g: 'જોડ/જુવાળ' }
            ],
            'op': [
                { prefix: 'C', suffix: 'op', g: 'પોલીસ' },
                { prefix: 'Dr', suffix: 'op', g: 'ટીપું' },
                { prefix: 'Fl', suffix: 'op', g: 'નિષ્ફળતા' },
                { prefix: 'H', suffix: 'op', g: 'કૂદવું' },
                { prefix: 'M', suffix: 'op', g: 'પોતડો' },
                { prefix: 'P', suffix: 'op', g: 'પોપ અવાજ' },
                { prefix: 'Pr', suffix: 'op', g: 'આધાર' },
                { prefix: 'Sh', suffix: 'op', g: 'દુકાન' },
                { prefix: 'St', suffix: 'op', g: 'અટકવું' },
                { prefix: 'T', suffix: 'op', g: 'ટોચ' }
            ],
            'ore': [
                { prefix: 'Ch', suffix: 'ore', g: 'ઘરકામ' },
                { prefix: 'C', suffix: 'ore', g: 'કેન્દ્ર/મર્મ' },
                { prefix: 'F', suffix: 'ore', g: 'આગળ' },
                { prefix: 'G', suffix: 'ore', g: 'લોહીલુહાણ' },
                { prefix: 'M', suffix: 'ore', g: 'વધુ' },
                { prefix: '', suffix: 'Ore', g: 'ધાતુ અયસ્ક' },
                { prefix: 'S', suffix: 'ore', g: 'ઘા/દુખાવો' },
                { prefix: 'St', suffix: 'ore', g: 'દુકાન' },
                { prefix: 'T', suffix: 'ore', g: 'ફાડ્યું' },
                { prefix: 'W', suffix: 'ore', g: 'પહેર્યું' }
            ]
        };

        let currentFamily = 'ack';
        let currentIndex = 0;
        let viewedCount = 0;
        let pronouncedCount = 0;
        let autoPlayInterval = null;
        let isQuizMode = false;
        let quizScore = 0;
        let quizTotal = 0;

        // Initialize family selector
        function initFamilySelector() {
            const selector = document.getElementById('familySelector');
            Object.keys(wordFamilies).forEach(family => {
                const btn = document.createElement('button');
                btn.className = 'family-btn';
                btn.textContent = '-' + family;
                btn.onclick = () => selectFamily(family);
                if (family === currentFamily) btn.classList.add('active');
                selector.appendChild(btn);
            });
        }

        function selectFamily(family) {
            currentFamily = family;
            currentIndex = 0;
            updateFamilyButtons();
            updateCard();
            updateProgress();
        }

        function updateFamilyButtons() {
            document.querySelectorAll('.family-btn').forEach(btn => {
                btn.classList.toggle('active', btn.textContent === '-' + currentFamily);
            });
        }

        function updateCard() {
            const word = wordFamilies[currentFamily][currentIndex];
            document.getElementById('familyBadge').textContent = currentFamily;
            document.getElementById('gujarati').textContent = word.g;
            document.getElementById('prefixPart').textContent = word.prefix;
            document.getElementById('suffixPart').textContent = word.suffix;
            
            viewedCount++;
            document.getElementById('viewed').textContent = viewedCount;
        }

        function updateProgress() {
            const total = wordFamilies[currentFamily].length;
            const progress = ((currentIndex + 1) / total) * 100;
            document.getElementById('progress').style.width = progress + '%';
            document.getElementById('current').textContent = currentIndex + 1;
            document.getElementById('total').textContent = total;
            document.getElementById('currentFamily').textContent = '-' + currentFamily;
            
            document.getElementById('prevBtn').disabled = currentIndex === 0;
            document.getElementById('nextBtn').disabled = currentIndex === total - 1;
        }

        function nextWord() {
            const total = wordFamilies[currentFamily].length;
            if (currentIndex < total - 1) {
                currentIndex++;
            } else {
                currentIndex = 0;
            }
            updateCard();
            updateProgress();
        }

        function prevWord() {
            if (currentIndex > 0) {
                currentIndex--;
                updateCard();
                updateProgress();
            }
        }

        function shuffle() {
            const shuffled = [...wordFamilies[currentFamily]];
            for (let i = shuffled.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [shuffled[i], shuffled[j]] = [shuffled[j], shuffled[i]];
            }
            wordFamilies[currentFamily] = shuffled;
            currentIndex = 0;
            updateCard();
            updateProgress();
        }

        function toggleAuto() {
            const btn = document.getElementById('autoBtn');
            if (autoPlayInterval) {
                clearInterval(autoPlayInterval);
                autoPlayInterval = null;
                btn.classList.remove('active');
                btn.innerHTML = '▶️ Auto';
            } else {
                autoPlayInterval = setInterval(() => {
                    nextWord();
                    pronounce();
                }, 3500);
                btn.classList.add('active');
                btn.innerHTML = '⏸️ Pause';
            }
        }

        function pronounce() {
            const word = wordFamilies[currentFamily][currentIndex];
            const fullWord = word.prefix + word.suffix;
            
            if ('speechSynthesis' in window) {
                const utterance = new SpeechSynthesisUtterance(fullWord);
                utterance.rate = 0.75;
                utterance.pitch = 1;
                speechSynthesis.speak(utterance);
                
                pronouncedCount++;
                document.getElementById('pronounced').textContent = pronouncedCount;
            } else {
                alert('Sorry, speech synthesis is not supported in your browser.');
            }
        }

        function toggleQuiz() {
            isQuizMode = !isQuizMode;
            document.getElementById('flashcardSection').style.display = isQuizMode ? 'none' : 'block';
            document.getElementById('quizSection').style.display = isQuizMode ? 'block' : 'none';
            document.getElementById('quizBtn').textContent = isQuizMode ? '📚 Back to Flashcards' : '❓ Quiz Mode';
            
            if (isQuizMode) {
                generateQuiz();
            }
        }

        function generateQuiz() {
            document.getElementById('nextQ').style.display = 'none';
            document.getElementById('quizResult').textContent = '';
            
            const allWords = wordFamilies[currentFamily];
            const correctWord = allWords[Math.floor(Math.random() * allWords.length)];
            const fullWord = correctWord.prefix + correctWord.suffix;
            
            document.getElementById('quizQuestion').textContent = `What is the meaning of "${fullWord}"?`;
            
            // Generate options
            let options = [correctWord.g];
            while (options.length < 4) {
                const randomWord = allWords[Math.floor(Math.random() * allWords.length)];
                if (!options.includes(randomWord.g)) {
                    options.push(randomWord.g);
                }
            }
            
            // Shuffle options
            options.sort(() => Math.random() - 0.5);
            
            const optionsDiv = document.getElementById('quizOptions');
            optionsDiv.innerHTML = '';
            
            options.forEach(option => {
                const btn = document.createElement('div');
                btn.className = 'quiz-option';
                btn.textContent = option;
                btn.onclick = () => checkAnswer(btn, option, correctWord.g);
                optionsDiv.appendChild(btn);
            });
        }

        function checkAnswer(btn, selected, correct) {
            quizTotal++;
            const allOptions = document.querySelectorAll('.quiz-option');
            allOptions.forEach(opt => {
                opt.style.pointerEvents = 'none';
                if (opt.textContent === correct) {
                    opt.classList.add('correct');
                }
            });
            
            if (selected === correct) {
                quizScore++;
                document.getElementById('quizResult').textContent = '✅ Correct! બરાબર!';
                document.getElementById('quizResult').style.color = '#11998e';
            } else {
                btn.classList.add('wrong');
                document.getElementById('quizResult').textContent = '❌ Wrong! Correct answer: ' + correct;
                document.getElementById('quizResult').style.color = '#ee5a6f';
            }
            
            document.getElementById('quizScore').textContent = `Score: ${quizScore}/${quizTotal}`;
            document.getElementById('nextQ').style.display = 'block';
        }

        // Initialize app
        initFamilySelector();
        updateCard();
        updateProgress();

        // Keyboard navigation
        document.addEventListener('keydown', (e) => {
            if (!isQuizMode) {
                if (e.key === 'ArrowLeft') prevWord();
                if (e.key === 'ArrowRight' || e.key === ' ') {
                    e.preventDefault();
                    nextWord();
                }
                if (e.key === 'p' || e.key === 'P') pronounce();
            }
        });
    </script>
</body>
</html>
