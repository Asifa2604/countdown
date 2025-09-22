<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🎉 Birthday Surprise</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #8A2BE2;
            --secondary: #FF6B8B;
            --accent: #4ECDC4;
            --light: #F8F9FA;
            --dark: #2D3748;
            --gray: #718096;
            --success: #38B2AC;
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            --radius: 16px;
            --transition: all 0.3s ease;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #8A2BE2 0%, #FF6B8B 50%, #4ECDC4 100%);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
            color: var(--dark);
            line-height: 1.6;
        }

        /* Background Animation */
        .background-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: 0;
            pointer-events: none;
        }

        .floating-shapes {
            position: absolute;
            width: 20px;
            height: 20px;
            background: rgba(255, 255, 255, 0.15);
            border-radius: 50%;
            animation: float 8s ease-in-out infinite;
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.3);
        }

        .floating-shapes:nth-child(1) { left: 10%; animation-delay: 0s; }
        .floating-shapes:nth-child(2) { left: 20%; animation-delay: 1s; }
        .floating-shapes:nth-child(3) { left: 30%; animation-delay: 2s; }
        .floating-shapes:nth-child(4) { left: 40%; animation-delay: 3s; }
        .floating-shapes:nth-child(5) { left: 50%; animation-delay: 4s; }
        .floating-shapes:nth-child(6) { left: 60%; animation-delay: 5s; }
        .floating-shapes:nth-child(7) { left: 70%; animation-delay: 0.5s; }
        .floating-shapes:nth-child(8) { left: 80%; animation-delay: 1.5s; }
        .floating-shapes:nth-child(9) { left: 90%; animation-delay: 2.5s; }

        @keyframes float {
            0%, 100% { transform: translateY(100vh) rotate(0deg); opacity: 0; }
            10%, 90% { opacity: 1; }
            50% { transform: translateY(-20px) rotate(180deg); }
        }

        /* Page Sections */
        .page-section {
            display: none;
            min-height: 100vh;
            padding: 1.5rem;
            position: relative;
            z-index: 1;
            align-items: center;
            justify-content: center;
        }

        .page-section.active {
            display: flex;
            animation: fadeInUp 0.8s ease-out;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Container Styles */
        .container {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border-radius: var(--radius);
            padding: 2.5rem;
            text-align: center;
            box-shadow: var(--shadow);
            max-width: 600px;
            width: 100%;
            border: 1px solid rgba(255, 255, 255, 0.2);
            position: relative;
            overflow: hidden;
        }

        .container::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--primary), var(--secondary), var(--accent));
        }

        /* Typography */
        .title {
            font-size: 2.5rem;
            font-weight: 800;
            color: var(--dark);
            margin-bottom: 0.5rem;
            background: linear-gradient(135deg, var(--primary), var(--secondary), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .subtitle {
            font-size: 1.1rem;
            color: var(--gray);
            margin-bottom: 2rem;
            font-weight: 400;
        }

        /* Form Styles */
        .form-group {
            margin-bottom: 1.8rem;
            text-align: left;
            position: relative;
        }

        .form-label {
            display: block;
            font-size: 1rem;
            font-weight: 600;
            color: var(--dark);
            margin-bottom: 0.5rem;
            padding-left: 0.5rem;
        }

        .form-input {
            width: 100%;
            padding: 1.2rem 1rem;
            border: 2px solid #e2e8f0;
            border-radius: 12px;
            font-size: 1rem;
            transition: var(--transition);
            background: rgba(255, 255, 255, 0.8);
            font-family: 'Poppins', sans-serif;
        }

        .form-input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(138, 43, 226, 0.1);
            background: rgba(255, 255, 255, 1);
        }

        .form-textarea {
            min-height: 120px;
            resize: vertical;
        }

        /* Button Styles */
        .btn {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            padding: 1.2rem 2.5rem;
            border-radius: 12px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            text-transform: uppercase;
            letter-spacing: 0.5px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            box-shadow: 0 4px 15px rgba(138, 43, 226, 0.3);
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(138, 43, 226, 0.4);
        }

        .btn:active {
            transform: translateY(-1px);
        }

        .btn-back {
            background: linear-gradient(135deg, var(--gray), #4a5568);
            margin-right: 1rem;
            padding: 1rem 1.8rem;
            font-size: 1rem;
        }

        .btn-back:hover {
            box-shadow: 0 8px 20px rgba(113, 128, 150, 0.3);
        }

        .btn-group {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
        }

        /* Letter Styles */
        .letter-container {
            background: linear-gradient(135deg, #f7fafc, #edf2f7);
            border-radius: 16px;
            padding: 2rem;
            margin: 2rem 0;
            border-left: 4px solid var(--primary);
            text-align: left;
            position: relative;
            overflow: hidden;
        }

        .letter-container::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100px;
            height: 100px;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><path fill="%238A2BE2" opacity="0.1" d="M50,0 C77.6,0 100,22.4 100,50 C100,77.6 77.6,100 50,100 C22.4,100 0,77.6 0,50 C0,22.4 22.4,0 50,0 Z"/></svg>') no-repeat;
            background-size: contain;
            transform: translate(30%, -30%);
        }

        .letter-greeting {
            font-size: 1.3rem;
            font-weight: 600;
            color: var(--dark);
            margin-bottom: 1rem;
        }

        .letter-content {
            font-size: 1.1rem;
            color: #4a5568;
            line-height: 1.6;
            margin-bottom: 1rem;
        }

        .letter-signature {
            font-size: 1rem;
            color: var(--gray);
            font-style: italic;
            text-align: right;
            margin-top: 1.5rem;
        }

        /* Popup Styles */
        .popup-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(10px);
            z-index: 1000;
            display: none;
            align-items: center;
            justify-content: center;
            padding: 1.5rem;
        }

        .popup-overlay.show {
            display: flex;
            animation: popupFadeIn 0.5s ease-out;
        }

        @keyframes popupFadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .popup-container {
            background: rgba(255, 255, 255, 0.98);
            backdrop-filter: blur(20px);
            border-radius: var(--radius);
            padding: 2.5rem;
            text-align: center;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.3);
            max-width: 700px;
            width: 100%;
            border: 2px solid rgba(255, 255, 255, 0.3);
            position: relative;
            animation: popupSlideIn 0.8s ease-out;
            overflow: hidden;
        }

        .popup-container::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--primary), var(--secondary), var(--accent));
        }

        @keyframes popupSlideIn {
            from {
                opacity: 0;
                transform: scale(0.8) translateY(50px);
            }
            to {
                opacity: 1;
                transform: scale(1) translateY(0);
            }
        }

        /* Countdown Styles */
        .countdown-container {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1.2rem;
            margin: 2rem 0;
        }

        .time-unit {
            background: linear-gradient(135deg, #f7fafc, #edf2f7);
            border-radius: 16px;
            padding: 1.5rem 1rem;
            border: 2px solid rgba(138, 43, 226, 0.1);
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        .time-unit::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            transform: scaleX(0);
            transition: transform 0.3s ease;
        }

        .time-unit:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
            border-color: rgba(138, 43, 226, 0.3);
        }

        .time-unit:hover::before {
            transform: scaleX(1);
        }

        .time-number {
            font-size: 2.5rem;
            font-weight: 800;
            color: var(--dark);
            display: block;
            line-height: 1;
            margin-bottom: 0.5rem;
            transition: transform 0.2s ease;
        }

        .time-label {
            font-size: 0.875rem;
            color: var(--gray);
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        /* Celebration Styles */
        .celebration-title {
            font-size: 3rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--primary), var(--secondary), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 1rem;
            animation: rainbow 3s ease-in-out infinite;
        }

        @keyframes rainbow {
            0%, 100% { filter: hue-rotate(0deg); }
            50% { filter: hue-rotate(180deg); }
        }

        .celebration-message {
            font-size: 1.5rem;
            color: var(--dark);
            margin-bottom: 2rem;
            line-height: 1.6;
        }

        /* Blast Effects */
        .blast-particle {
            position: absolute;
            width: 8px;
            height: 8px;
            border-radius: 50%;
            pointer-events: none;
            z-index: 10;
        }

        .blast-particle:nth-child(odd) { background: var(--primary); }
        .blast-particle:nth-child(even) { background: var(--secondary); }
        .blast-particle:nth-child(3n) { background: var(--accent); }

        @keyframes blastOut {
            0% {
                transform: scale(0) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: scale(1) rotate(720deg);
                opacity: 0;
            }
        }

        /* Confetti */
        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background: var(--primary);
            animation: confetti-fall 3s linear infinite;
            pointer-events: none;
            z-index: 5;
        }

        .confetti:nth-child(odd) { background: var(--secondary); animation-delay: 0.5s; }
        .confetti:nth-child(3n) { background: var(--accent); animation-delay: 1s; }
        .confetti:nth-child(4n) { background: #FFD166; animation-delay: 1.5s; }

        @keyframes confetti-fall {
            0% {
                transform: translateY(-100vh) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(720deg);
                opacity: 0;
            }
        }

        .pulse {
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        /* Progress Indicator */
        .progress-indicator {
            display: flex;
            justify-content: center;
            margin-bottom: 2rem;
            gap: 0.5rem;
        }

        .progress-step {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: #e2e8f0;
            transition: var(--transition);
        }

        .progress-step.active {
            background: var(--primary);
            transform: scale(1.2);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .container, .popup-container {
                padding: 2rem;
                margin: 0.5rem;
            }
            
            .title {
                font-size: 2rem;
            }
            
            .countdown-container {
                grid-template-columns: repeat(2, 1fr);
                gap: 1rem;
            }
            
            .time-number {
                font-size: 2rem;
            }
            
            .celebration-title {
                font-size: 2.2rem;
            }
            
            .celebration-message {
                font-size: 1.25rem;
            }

            .btn {
                padding: 1rem 2rem;
                font-size: 1rem;
                width: 100%;
            }

            .btn-group {
                flex-direction: column;
            }

            .btn-back {
                margin-right: 0;
                margin-bottom: 1rem;
            }
        }

        @media (max-width: 480px) {
            .page-section {
                padding: 1rem;
            }
            
            .container, .popup-container {
                padding: 1.5rem;
            }
            
            .title {
                font-size: 1.8rem;
            }
            
            .subtitle {
                font-size: 1rem;
            }
            
            .countdown-container {
                grid-template-columns: 1fr 1fr;
                gap: 0.8rem;
            }
            
            .time-unit {
                padding: 1rem 0.5rem;
            }
            
            .time-number {
                font-size: 1.8rem;
            }
            
            .celebration-title {
                font-size: 1.8rem;
            }
            
            .celebration-message {
                font-size: 1.1rem;
            }
            
            .letter-container {
                padding: 1.5rem;
            }
            
            .letter-greeting {
                font-size: 1.1rem;
            }
            
            .letter-content {
                font-size: 1rem;
            }
        }

        /* Tablet-specific adjustments */
        @media (min-width: 769px) and (max-width: 1024px) {
            .container {
                max-width: 700px;
                padding: 3rem;
            }
            
            .title {
                font-size: 2.8rem;
            }
            
            .countdown-container {
                gap: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="background-animation">
        <div class="floating-shapes"></div>
        <div class="floating-shapes"></div>
        <div class="floating-shapes"></div>
        <div class="floating-shapes"></div>
        <div class="floating-shapes"></div>
        <div class="floating-shapes"></div>
        <div class="floating-shapes"></div>
        <div class="floating-shapes"></div>
        <div class="floating-shapes"></div>
    </div>

    <!-- Home Page -->
    <div class="page-section active" id="home-page">
        <div class="container">
            <div class="progress-indicator">
                <div class="progress-step active"></div>
                <div class="progress-step"></div>
                <div class="progress-step"></div>
            </div>
            
            <h1 class="title">🎉 Hello!</h1>
            <p class="subtitle">Let's create something magical for your special day!</p>
            
            <form id="birthday-form">
                <div class="form-group">
                    <label class="form-label" for="name">What's your name?</label>
                    <input type="text" id="name" class="form-input" placeholder="Enter your beautiful name..." required>
                </div>
                
                <div class="form-group">
                    <label class="form-label" for="favorite-thing">What brings you joy?</label>
                    <input type="text" id="favorite-thing" class="form-input" placeholder="Reading, dancing, traveling..." required>
                </div>
                
                <div class="form-group">
                    <label class="form-label" for="wish">What's your biggest wish?</label>
                    <textarea id="wish" class="form-input form-textarea" placeholder="Share your dreams and aspirations..." required></textarea>
                </div>
                
                <button type="submit" class="btn">
                    <i class="fas fa-magic"></i> Create My Surprise
                </button>
            </form>
        </div>
    </div>

    <!-- Did You Know Page -->
    <div class="page-section" id="did-you-know-page">
        <div class="container">
            <div class="progress-indicator">
                <div class="progress-step"></div>
                <div class="progress-step active"></div>
                <div class="progress-step"></div>
            </div>
            
            <h1 class="title">🌟 Did You Know?</h1>
            <p class="subtitle">Something magical is about to happen...</p>
            
            <div style="font-size: 1.5rem; color: var(--primary); font-weight: 600; margin: 2rem 0;">
                ✨ All your wishes will be fulfilled! ✨
            </div>
            
            <div class="letter-container" id="personal-letter">
                <!-- Letter content will be populated by JavaScript -->
            </div>
            
            <div class="btn-group">
                <button class="btn btn-back" onclick="goToPage('home-page')">
                    <i class="fas fa-arrow-left"></i> Back
                </button>
                <button class="btn" onclick="showSurprise()">
                    <i class="fas fa-gift"></i> Reveal Surprise!
                </button>
            </div>
        </div>
    </div>

    <!-- Countdown Popup -->
    <div class="popup-overlay" id="countdown-popup">
        <div class="popup-container">
            <div id="countdown-section">
                <h1 class="title">🎂 Your Birthday Countdown</h1>
                <p class="subtitle">The magic moment is approaching...</p>
                
                <div class="countdown-container" id="countdown">
                    <div class="time-unit">
                        <span class="time-number" id="days">00</span>
                        <span class="time-label">Days</span>
                    </div>
                    <div class="time-unit">
                        <span class="time-number" id="hours">00</span>
                        <span class="time-label">Hours</span>
                    </div>
                    <div class="time-unit">
                        <span class="time-number" id="minutes">00</span>
                        <span class="time-label">Minutes</span>
                    </div>
                    <div class="time-unit">
                        <span class="time-number" id="seconds">00</span>
                        <span class="time-label">Seconds</span>
                    </div>
                </div>
                
                <div style="font-size: 1.2rem; color: #4a5568; font-weight: 500; margin-top: 1rem;">
                    <i class="fas fa-calendar-alt"></i> October 23rd, 2025
                </div>
            </div>

            <div id="celebration-section" style="display: none;">
                <h1 class="celebration-title">🎉 HAPPY BIRTHDAY! 🎉</h1>
                <p class="celebration-message" id="birthday-message">
                    <!-- Personalized birthday message will be populated by JavaScript -->
                </p>
                <div class="pulse">
                    <div style="font-size: 2rem; margin-top: 1rem;">
                        🎈🎁🎊🥳🎈
                    </div>
                </div>
            </div>
            
            <div style="margin-top: 2rem;">
                <button class="btn btn-back" onclick="closePopup()">
                    <i class="fas fa-times"></i> Close
                </button>
            </div>
        </div>
    </div>

    <!-- Added audio element for birthday song -->
    <audio id="birthday-song" preload="auto" loop>
        <source src="https://assets.codepen.io/1468070/happy-birthday-song.mp3" type="audio/mpeg">
        <!-- Fallback to a simple chime if the birthday song fails to load -->
        <source src="https://assets.codepen.io/1468070/bell-sound.mp3" type="audio/mpeg">
    </audio>

    <script>
        // Global variables
        let userData = {};
        let countdownInterval;
        const targetDate = new Date('2025-10-23T00:00:00').getTime();

        // Form submission handler
        document.getElementById('birthday-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Get form data
            userData.name = document.getElementById('name').value.trim();
            userData.favoriteThing = document.getElementById('favorite-thing').value.trim();
            userData.wish = document.getElementById('wish').value.trim();
            
            // Validate form
            if (!userData.name || !userData.favoriteThing || !userData.wish) {
                showNotification('Please fill in all fields to create your surprise!', 'error');
                return;
            }
            
            // Generate personal letter
            generatePersonalLetter();
            
            // Go to did you know page
            goToPage('did-you-know-page');
            
            // Update progress indicator
            updateProgressIndicator('did-you-know-page');
        });

        // Generate personal letter
        function generatePersonalLetter() {
            const letterContent = `
                <div class="letter-greeting">Dear ${userData.name},</div>
                <div class="letter-content">
                    I hope this letter finds you in the best of spirits! I wanted to take a moment to tell you how amazing you are.
                    <br><br>
                    I know how much you love ${userData.favoriteThing}, and it's wonderful to see the joy it brings to your life. Your passion for the things you love is truly inspiring.
                    <br><br>
                    About your wish - "${userData.wish}" - I believe with all my heart that this dream of yours will come true. You have the strength, determination, and beautiful spirit to make anything possible.
                    <br><br>
                    Your birthday is approaching, and I couldn't be more excited to celebrate the incredible person you are. You deserve all the happiness, love, and magical moments that life has to offer.
                    <br><br>
                    Get ready for something special... 🎉
                </div>
                <div class="letter-signature">With love and best wishes,<br>Your Birthday Surprise Team ✨</div>
            `;
            
            document.getElementById('personal-letter').innerHTML = letterContent;
        }

        // Page navigation
        function goToPage(pageId) {
            // Hide all pages
            document.querySelectorAll('.page-section').forEach(page => {
                page.classList.remove('active');
            });
            
            // Show target page
            document.getElementById(pageId).classList.add('active');
        }

        // Update progress indicator
        function updateProgressIndicator(currentPage) {
            const steps = document.querySelectorAll('.progress-step');
            steps.forEach(step => step.classList.remove('active'));
            
            if (currentPage === 'home-page') {
                steps[0].classList.add('active');
            } else if (currentPage === 'did-you-know-page') {
                steps[1].classList.add('active');
            } else if (currentPage === 'countdown-popup') {
                steps[2].classList.add('active');
            }
        }

        // Show notification
        function showNotification(message, type = 'info') {
            // Create notification element
            const notification = document.createElement('div');
            notification.textContent = message;
            notification.style.position = 'fixed';
            notification.style.top = '20px';
            notification.style.right = '20px';
            notification.style.padding = '1rem 1.5rem';
            notification.style.borderRadius = '8px';
            notification.style.color = 'white';
            notification.style.fontWeight = '600';
            notification.style.zIndex = '1001';
            notification.style.boxShadow = '0 5px 15px rgba(0,0,0,0.2)';
            notification.style.transform = 'translateX(150%)';
            notification.style.transition = 'transform 0.3s ease';
            
            if (type === 'error') {
                notification.style.background = 'linear-gradient(135deg, #FF6B6B, #FF8E8E)';
            } else {
                notification.style.background = 'linear-gradient(135deg, var(--primary), var(--secondary))';
            }
            
            document.body.appendChild(notification);
            
            // Animate in
            setTimeout(() => {
                notification.style.transform = 'translateX(0)';
            }, 100);
            
            // Remove after 3 seconds
            setTimeout(() => {
                notification.style.transform = 'translateX(150%)';
                setTimeout(() => {
                    if (notification.parentNode) {
                        notification.parentNode.removeChild(notification);
                    }
                }, 300);
            }, 3000);
        }

        // Show surprise popup
        function showSurprise() {
            document.getElementById('countdown-popup').classList.add('show');
            createBlastEffect();
            startCountdown();
            updateProgressIndicator('countdown-popup');
        }

        // Close popup
        function closePopup() {
            document.getElementById('countdown-popup').classList.remove('show');
            if (countdownInterval) {
                clearInterval(countdownInterval);
            }
            const song = document.getElementById('birthday-song');
            song.pause();
            song.currentTime = 0;
        }

        // Create blast effect
        function createBlastEffect() {
            const popup = document.querySelector('.popup-container');
            const centerX = popup.offsetWidth / 2;
            const centerY = popup.offsetHeight / 2;
            
            for (let i = 0; i < 30; i++) {
                const particle = document.createElement('div');
                particle.className = 'blast-particle';
                
                const angle = (360 / 30) * i;
                const distance = 100 + Math.random() * 100;
                const x = centerX + Math.cos(angle * Math.PI / 180) * distance;
                const y = centerY + Math.sin(angle * Math.PI / 180) * distance;
                
                particle.style.left = centerX + 'px';
                particle.style.top = centerY + 'px';
                particle.style.animation = `blastOut 1s ease-out forwards`;
                particle.style.animationDelay = Math.random() * 0.3 + 's';
                
                popup.appendChild(particle);
                
                // Animate to final position
                setTimeout(() => {
                    particle.style.transform = `translate(${x - centerX}px, ${y - centerY}px) scale(1) rotate(720deg)`;
                }, 50);
                
                // Remove particle
                setTimeout(() => {
                    particle.remove();
                }, 1500);
            }
        }

        // Start countdown
        function startCountdown() {
            updateCountdown();
            countdownInterval = setInterval(updateCountdown, 1000);
        }

        // Update countdown
        function updateCountdown() {
            const now = new Date().getTime();
            const distance = targetDate - now;

            // If countdown is finished
            if (distance < 0) {
                showCelebration();
                return;
            }

            // Calculate time units
            const days = Math.floor(distance / (1000 * 60 * 60 * 24));
            const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((distance % (1000 * 60)) / 1000);

            // Update DOM elements with animation
            updateTimeUnit('days', days);
            updateTimeUnit('hours', hours);
            updateTimeUnit('minutes', minutes);
            updateTimeUnit('seconds', seconds);
        }

        // Update time unit with animation
        function updateTimeUnit(id, value) {
            const element = document.getElementById(id);
            const formattedValue = value < 10 ? '0' + value : value;
            
            if (element.textContent !== formattedValue) {
                element.style.transform = 'scale(1.2)';
                element.style.color = 'var(--primary)';
                setTimeout(() => {
                    element.style.transform = 'scale(1)';
                    element.style.color = 'var(--dark)';
                }, 200);
            }
            
            element.textContent = formattedValue;
        }

        // Show birthday celebration
        function showCelebration() {
            clearInterval(countdownInterval);
            
            // Hide countdown section
            document.getElementById('countdown-section').style.display = 'none';
            
            // Show celebration section
            const celebrationSection = document.getElementById('celebration-section');
            celebrationSection.style.display = 'block';
            
            const song = document.getElementById('birthday-song');
            song.volume = 0.5;
            song.play().catch(e => {
                console.log('Could not play birthday song:', e);
                // Fallback: try to play a different sound or show a message
                console.log('🎵 Happy Birthday song would be playing now! 🎵');
            });
            
            // Update birthday message
            const birthdayMessage = document.getElementById('birthday-message');
            birthdayMessage.innerHTML = `
                Today is your special day, ${userData.name}! 🎂<br>
                May this new year of your life be filled with joy, love, and endless possibilities.<br>
                I hope you get to enjoy lots of ${userData.favoriteThing} and that your wish "${userData.wish}" comes true!<br>
                You deserve all the happiness in the world! ✨
            `;
            
            // Create continuous confetti
            createConfetti();
            setInterval(createConfetti, 2000);
        }

        // Create confetti
        function createConfetti() {
            const popup = document.querySelector('.popup-container');
            
            for (let i = 0; i < 50; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.left = Math.random() * 100 + '%';
                confetti.style.animationDelay = Math.random() * 3 + 's';
                confetti.style.animationDuration = (Math.random() * 3 + 2) + 's';
                popup.appendChild(confetti);
                
                // Remove confetti after animation
                setTimeout(() => {
                    if (confetti.parentNode) {
                        confetti.remove();
                    }
                }, 5000);
            }
        }

        // Add smooth transitions to time units
        document.addEventListener('DOMContentLoaded', function() {
            document.querySelectorAll('.time-number').forEach(element => {
                element.style.transition = 'transform 0.2s ease, color 0.2s ease';
            });
            
            // Add hover effects to buttons
            document.querySelectorAll('.btn').forEach(button => {
                button.addEventListener('mouseenter', function() {
                    this.style.transform = 'translateY(-3px)';
                });
                
                button.addEventListener('mouseleave', function() {
                    this.style.transform = 'translateY(0)';
                });
            });
            
            // Add focus effects to form inputs
            document.querySelectorAll('.form-input').forEach(input => {
                input.addEventListener('focus', function() {
                    this.parentElement.style.transform = 'translateY(-2px)';
                });
                
                input.addEventListener('blur', function() {
                    this.parentElement.style.transform = 'translateY(0)';
                });
            });
        });
    </script>
</body>
</html>
