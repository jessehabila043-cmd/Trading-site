<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trading Masters - Dynamic Learning Hub</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* ===== RESET & BASE STYLES ===== */
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        :root {
            --purple-dark: #6a0dad;
            --purple-medium: #8a2be2;
            --purple-light: #9370db;
            --purple-very-light: #e6d7ff;
            --dark-bg: #0a0a1a;
            --card-bg: #15152b;
            --text-white: #ffffff;
            --text-gray: #cccccc;
            --success-green: #00d97e;
        }
        body {
            background: var(--dark-bg);
            color: var(--text-white);
            line-height: 1.7;
            padding-top: 70px;
            background-image: radial-gradient(circle at 20% 30%, rgba(138, 43, 226, 0.15) 0%, transparent 20%),
                              radial-gradient(circle at 80% 80%, rgba(106, 13, 173, 0.1) 0%, transparent 20%);
        }
        .container { max-width: 1200px; margin: 0 auto; padding: 0 20px; }
        .section-padding { padding: 80px 0; }

        /* ===== TYPOGRAPHY & COLORS ===== */
        .purple-heading { color: var(--purple-medium); margin-bottom: 1rem; font-size: 2.5rem; }
        .section-title { text-align: center; margin-bottom: 3rem; }
        .sensitive { color: var(--purple-very-light); font-weight: 300; }
        .highlight-box {
            background: linear-gradient(90deg, rgba(138, 43, 226, 0.2), transparent);
            border-left: 4px solid var(--purple-medium);
            padding: 1.5rem;
            margin: 2rem 0;
            border-radius: 0 10px 10px 0;
        }

        /* ===== ENHANCED NAVIGATION ===== */
        .navbar {
            background: rgba(10, 10, 26, 0.95);
            backdrop-filter: blur(10px);
            position: fixed;
            top: 0; width: 100%;
            padding: 1rem 0;
            z-index: 1000;
            border-bottom: 1px solid rgba(138, 43, 226, 0.3);
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
        }
        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--text-white);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .logo span { color: var(--purple-medium); }
        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
            align-items: center;
        }
        .nav-links a {
            color: var(--text-white);
            text-decoration: none;
            font-weight: 500;
            padding: 8px 16px;
            border-radius: 6px;
            transition: all 0.3s ease;
            position: relative;
        }
        .nav-links a:hover,
        .nav-links a.active {
            background: rgba(138, 43, 226, 0.2);
            color: var(--purple-very-light);
        }
        .mobile-menu-btn { display: none; font-size: 1.5rem; background: none; border: none; color: white; }

        /* ===== DYNAMIC HERO WITH MOVING CHARTS ===== */
        .hero {
            padding: 100px 0 60px;
            position: relative;
            overflow: hidden;
        }
        .hero-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
            align-items: center;
        }
        .hero-text h1 {
            font-size: 3.2rem;
            line-height: 1.2;
            margin-bottom: 1.5rem;
            background: linear-gradient(90deg, var(--purple-medium), var(--purple-light));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .hero-buttons { display: flex; gap: 1rem; margin-top: 2rem; flex-wrap: wrap; }
        .btn {
            display: inline-block;
            padding: 14px 28px;
            border-radius: 8px;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s ease;
            cursor: pointer;
            border: none;
            font-size: 1rem;
        }
        .btn-primary {
            background: var(--purple-medium);
            color: white;
            box-shadow: 0 4px 15px rgba(138, 43, 226, 0.4);
        }
        .btn-primary:hover {
            background: var(--purple-dark);
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(138, 43, 226, 0.6);
        }
        .btn-secondary {
            background: transparent;
            color: var(--purple-medium);
            border: 2px solid var(--purple-medium);
        }
        .btn-secondary:hover {
            background: rgba(138, 43, 226, 0.1);
            transform: translateY(-3px);
        }

        /* ANIMATED TRADING CHARTS SIMULATION */
        .chart-container {
            position: relative;
            height: 300px;
            background: var(--card-bg);
            border-radius: 16px;
            padding: 20px;
            border: 1px solid rgba(138, 43, 226, 0.3);
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }
        .chart-grid {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0; left: 0;
            background-image:
                linear-gradient(to right, rgba(255,255,255,0.05) 1px, transparent 1px),
                linear-gradient(to bottom, rgba(255,255,255,0.05) 1px, transparent 1px);
            background-size: 50px 50px;
        }
        .chart-line {
            position: absolute;
            height: 2px;
            background: linear-gradient(90deg, var(--purple-medium), var(--success-green));
            border-radius: 2px;
            width: 80%;
            top: 50%;
            left: 10%;
            animation: chartPulse 4s infinite ease-in-out;
        }
        .chart-point {
            position: absolute;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: var(--success-green);
            transform: translate(-50%, -50%);
            box-shadow: 0 0 15px var(--success-green);
        }
        .candle {
            position: absolute;
            width: 8px;
            background: linear-gradient(to top, var(--success-green), #ff4444);
            border-radius: 2px;
        }
        @keyframes chartPulse {
            0%, 100% { opacity: 0.7; width: 80%; }
            50% { opacity: 1; width: 85%; }
        }
        .chart-label {
            position: absolute;
            color: var(--purple-very-light);
            font-size: 0.8rem;
            font-weight: 300;
        }

        /* ===== HOMEPAGE TABLE OF CONTENTS & RISK NOTICE ===== */
        .toc-section {
            background: rgba(21, 21, 43, 0.7);
            border-radius: 16px;
            padding: 2.5rem;
            margin: 3rem 0;
            border: 1px solid rgba(138, 43, 226, 0.2);
        }
        .toc-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-top: 2rem;
        }
        .toc-card {
            background: rgba(255, 255, 255, 0.05);
            padding: 1.5rem;
            border-radius: 10px;
            transition: transform 0.3s ease;
        }
        .toc-card:hover {
            transform: translateY(-5px);
            background: rgba(138, 43, 226, 0.1);
        }
        .toc-card i {
            font-size: 2rem;
            color: var(--purple-medium);
            margin-bottom: 1rem;
        }
        .integrated-risk-notice {
            background: rgba(255, 85, 85, 0.1);
            border: 1px solid rgba(255, 85, 85, 0.3);
            border-radius: 10px;
            padding: 1.5rem;
            margin-top: 2rem;
            text-align: center;
        }
        .integrated-risk-notice h4 {
            color: #ffaa55;
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        /* ===== VIDEO EDUCATION SECTION ===== */
        .video-section {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 3rem;
            margin: 4rem 0;
        }
        .video-wrapper {
            position: relative;
            padding-bottom: 56.25%; /* 16:9 Aspect Ratio */
            height: 0;
            overflow: hidden;
            border-radius: 12px;
            margin-top: 2rem;
            background: #000;
        }
        .video-wrapper iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }
        .video-description {
            margin-top: 1.5rem;
            padding: 1.5rem;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
        }

        /* ===== CONTACT SECTION WITH DETAILS ===== */
        .contact-section {
            text-align: center;
            padding: 4rem 0;
        }
        .contact-cards {
            display: flex;
            justify-content: center;
            gap: 2rem;
            flex-wrap: wrap;
            margin-top: 2rem;
        }
        .contact-card {
            background: var(--card-bg);
            padding: 2rem;
            border-radius: 12px;
            min-width: 280px;
            border: 1px solid rgba(138, 43, 226, 0.3);
            transition: all 0.3s ease;
        }
        .contact-card:hover {
            border-color: var(--purple-medium);
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(138, 43, 226, 0.2);
        }
        .contact-card i {
            font-size: 2.5rem;
            color: var(--purple-medium);
            margin-bottom: 1rem;
        }
        .contact-detail {
            font-size: 1.2rem;
            margin: 0.5rem 0;
            color: var(--purple-very-light);
        }
        .contact-note {
            font-size: 0.9rem;
            color: var(--text-gray);
            margin-top: 1rem;
        }

        /* ===== OTHER INTERESTING FEATURES ===== */
        /* Interactive Quiz */
        .quiz-container {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 2.5rem;
            margin: 3rem 0;
        }
        .quiz-option {
            background: rgba(255, 255, 255, 0.05);
            padding: 1rem 1.5rem;
            margin: 0.8rem 0;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s ease;
            border: 1px solid transparent;
        }
        .quiz-option:hover {
            background: rgba(138, 43, 226, 0.15);
            border-color: var(--purple-medium);
        }
        .quiz-feedback {
            padding: 1rem;
            border-radius: 8px;
            margin-top: 1rem;
            display: none;
        }
        .feedback-correct {
            background: rgba(0, 217, 126, 0.15);
            border-left: 4px solid var(--success-green);
        }
        .feedback-incorrect {
            background: rgba(255, 85, 85, 0.15);
            border-left: 4px solid #ff5555;
        }

        /* Live Market Stats Ticker */
        .market-ticker {
            background: linear-gradient(90deg, var(--dark-bg), var(--card-bg));
            padding: 15px 0;
            border-top: 1px solid rgba(138, 43, 226, 0.3);
            border-bottom: 1px solid rgba(138, 43, 226, 0.3);
            overflow: hidden;
            margin: 2rem 0;
        }
        .ticker-content {
            display: flex;
            animation: tickerScroll 30s linear infinite;
        }
        .ticker-item {
            display: flex;
            align-items: center;
            padding: 0 2rem;
            white-space: nowrap;
        }
        .ticker-symbol { color: var(--purple-medium); font-weight: 600; margin-right: 10px; }
        .ticker-price { color: var(--text-white); margin-right: 5px; }
        .ticker-change { font-weight: 600; }
        .positive { color: var(--success-green); }
        .negative { color: #ff5555; }
        @keyframes tickerScroll {
            0% { transform: translateX(0); }
            100% { transform: translateX(-100%); }
        }

        /* ===== RESPONSIVE DESIGN ===== */
        @media (max-width: 992px) {
            .hero-content { grid-template-columns: 1fr; text-align: center; }
            .hero-text h1 { font-size: 2.5rem; }
            .purple-heading { font-size: 2rem; }
        }
        @media (max-width: 768px) {
            .nav-links {
                display: none;
                position: fixed;
                top: 70px;
                left: 0;
                width: 100%;
                background: var(--card-bg);
                flex-direction: column;
                padding: 2rem;
                box-shadow: 0 10px 20px rgba(0,0,0,0.3);
            }
            .nav-links.active { display: flex; }
            .mobile-menu-btn { display: block; }
            .section-padding { padding: 50px 0; }
            .contact-cards { flex-direction: column; align-items: center; }
        }
    </style>
</head>
<body>
    <!-- ===== ENHANCED NAVIGATION ===== -->
    <nav class="navbar">
        <div class="container nav-container">
            <a href="#" class="logo"><i class="fas fa-chart-line"></i> Trading<span>Masters</span></a>
            <button class="mobile-menu-btn" id="menuBtn"><i class="fas fa-bars"></i></button>
            <ul class="nav-links" id="navLinks">
                <li><a href="#home" class="active"><i class="fas fa-home"></i> Home</a></li>
                <li><a href="#toc"><i class="fas fa-list"></i> Contents</a></li>
                <li><a href="#video"><i class="fas fa-play-circle"></i> Video Guide</a></li>
                <li><a href="#risk"><i class="fas fa-shield-alt"></i> Risk Management</a></li>
                <li><a href="#quiz"><i class="fas fa-brain"></i> Knowledge Quiz</a></li>
                <li><a href="#contact"><i class="fas fa-phone-alt"></i> Contact</a></li>
                <li><a href="#login" id="loginNav"><i class="fas fa-sign-in-alt"></i> Login</a></li>
            </ul>
        </div>
    </nav>

    <!-- ===== HERO WITH ANIMATED TRADING SCREEN ===== -->
    <section class="hero" id="home">
        <div class="container hero-content">
            <div class="hero-text">
                <h1>Trade Smarter, Not Harder.<br><span class="sensitive">Master the Markets with Confidence.</span></h1>
                <p class="sensitive">Welcome to your dynamic learning hub. We bring the trading floor to you with interactive charts, live simulations, and clear education to help you understand and manage risk.</p>
                <div class="hero-buttons">
                    <a href="#toc" class="btn btn-primary"><i class="fas fa-play"></i> Start Learning Journey</a>
                    <a href="#video" class="btn btn-secondary"><i class="fas fa-video"></i> Watch Introduction</a>
                </div>
            </div>
            <div class="chart-container">
                <div class="chart-grid"></div>
                <div class="chart-line"></div>
                <!-- Animated Chart Points -->
                <div class="chart-point" style="top: 30%; left: 20%;"></div>
                <div class="chart-point" style="top: 60%; left: 45%;"></div>
                <div class="chart-point" style="top: 40%; left: 70%;"></div>
                <!-- Simulated Candlesticks -->
                <div class="candle" style="height: 40px; left: 30%; bottom: 30%;"></div>
                <div class="candle" style="height: 60px; left: 40%; bottom: 25%; background: linear-gradient(to top, #ff4444, #ff8888);"></div>
                <div class="candle" style="height: 50px; left: 50%; bottom: 35%;"></div>
                <div class="chart-label" style="top: 15%; left: 15%;">NASDAQ</div>
                <div class="chart-label" style="bottom: 15%; right: 15%;">Live Simulation</div>
            </div>
        </div>
    </section>

    <!-- ===== TABLE OF CONTENTS & INTEGRATED RISK NOTICE ===== -->
    <section class="section-padding" id="toc">
        <div class="container">
            <h2 class="section-title purple-heading">Your Learning Pathway</h2>
            <p class="sensitive text-center" style="max-width: 700px; margin: 0 auto 3rem;">Navigate through our comprehensive modules designed to build your trading knowledge step-by-step.</p>

            <div class="toc-section">
                <div class="toc-grid">
                    <div class="toc-card">
                        <i class="fas fa-book-open"></i>
                        <h3>1. Foundations</h3>
                        <p class="sensitive">Market basics, terminology, and how financial markets operate.</p>
                    </div>
                    <div class="toc-card">
                        <i class="fas fa-chart-bar"></i>
                        <h3>2. Analysis Deep Dive</h3>
                        <p class="sensitive">Technical indicators, chart patterns, and fundamental analysis.</p>
                    </div>
                    <div class="toc-card">
                        <i class="fas fa-cogs"></i>
                        <h3>3. Strategy & Execution</h3>
                        <p class="sensitive">Building, testing, and executing your personal trading plan.</p>
                    </div>
                    <div class="toc-card">
                        <i class="fas fa-user-shield"></i>
                        <h3>4. Psychology & Risk</h3>
                        <p class="sensitive">Mastering the mental game and implementing robust risk controls.</p>
                    </div>
                </div>

                <!-- Integrated, Prominent Risk Notice (Not Red & Separate) -->
                <div class="integrated-risk-notice">
                    <h4><i class="fas fa-exclamation-circle"></i> Core Principle: Risk Awareness</h4>
                    <p class="sensitive" style="color: #ffcc99;">
                        <strong>Trading involves significant risk of capital loss.</strong> It is not suitable for all investors. The high level of leverage can work against you as well as for you. You should be aware of all the risks and seek independent advice if necessary. Past performance is not indicative of future results.
                    </p>
                </div>
            </div>
        </div>
    </section>

    <!-- ===== VIDEO EDUCATION SECTION ===== -->
    <section class="section-padding" id="video">
        <div class="container video-section">
            <h2 class="section-title purple-heading">Understanding Different Trading Styles</h2>
            <p class="sensitive text-center">Watch this guide to understand the key differences between Scalping, Day Trading, Swing Trading, and Position Trading.</p>

            <div class="video-wrapper">
                <!-- Embedded YouTube Video - Replace SRC with your actual video later -->
                <iframe src="https://www.youtube.com/embed/d8YPLiCqjvw?si=4dJVhVOB9fxKxJdP" title="Trading Styles Explained" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            </div>

            <div class="video-description">
                <h4><i class="fas fa-info-circle"></i> Video Summary</h4>
                <p class="sensitive">This video breaks down the four primary trading styles by time frame, risk profile, 
