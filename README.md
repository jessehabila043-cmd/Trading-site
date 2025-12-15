<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trading Masters | Risk Management Education</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* Reset and Base */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --purple-dark: #6a0dad;
            --purple-medium: #8a2be2;
            --purple-light: #9370db;
            --purple-very-light: #d8bfd8;
            --dark-bg: #0f0f23;
            --card-bg: #1a1a2e;
            --text-white: #ffffff;
            --text-gray: #cccccc;
        }
        
        body {
            background: var(--dark-bg);
            color: var(--text-white);
            line-height: 1.6;
            padding-top: 60px;
        }
        
        /* Purple Headings */
        .purple-heading {
            color: var(--purple-medium);
            margin-bottom: 15px;
            font-size: 1.8rem;
        }
        
        /* Sensitive Info - Light Purple */
        .sensitive {
            color: var(--purple-very-light);
            font-size: 0.95rem;
            opacity: 0.9;
        }
        
        /* Container */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }
        
        /* Navigation */
        .navbar {
            background: rgba(10, 10, 20, 0.95);
            position: fixed;
            top: 0;
            width: 100%;
            padding: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            border-bottom: 2px solid var(--purple-medium);
        }
        
        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--text-white);
            text-decoration: none;
        }
        
        .logo span {
            color: var(--purple-medium);
        }
        
        .nav-links {
            display: flex;
            gap: 15px;
        }
        
        .nav-links a {
            color: var(--text-white);
            text-decoration: none;
            padding: 8px 12px;
            border-radius: 5px;
            transition: 0.3s;
        }
        
        .nav-links a:hover,
        .nav-links a.active {
            background: var(--purple-medium);
        }
        
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
        }
        
        /* Hero Section */
        .hero {
            padding: 40px 20px;
            text-align: center;
            background: linear-gradient(135deg, #0f0f23 0%, #1a1a2e 100%);
        }
        
        .hero h1 {
            font-size: 2.2rem;
            margin-bottom: 20px;
            color: var(--purple-medium);
        }
        
        .hero p {
            font-size: 1.1rem;
            margin-bottom: 30px;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .btn {
            display: inline-block;
            padding: 12px 25px;
            background: var(--purple-medium);
            color: white;
            text-decoration: none;
            border-radius: 5px;
            margin: 5px;
            font-weight: 500;
            transition: 0.3s;
        }
        
        .btn:hover {
            background: var(--purple-dark);
            transform: translateY(-2px);
        }
        
        /* Cards */
        .card {
            background: var(--card-bg);
            border-radius: 10px;
            padding: 25px;
            margin: 20px 0;
            border-left: 4px solid var(--purple-medium);
        }
        
        .card h3 {
            color: var(--purple-light);
            margin-bottom: 15px;
            font-size: 1.3rem;
        }
        
        /* Risk Section */
        .risk-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }
        
        .risk-item {
            background: var(--card-bg);
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }
        
        .risk-icon {
            font-size: 2rem;
            color: var(--purple-medium);
            margin-bottom: 15px;
        }
        
        /* Warning Box */
        .warning-box {
            background: linear-gradient(135deg, #ff5555 0%, #ff0000 100%);
            padding: 20px;
            border-radius: 10px;
            margin: 30px 0;
            text-align: center;
        }
        
        /* Auth Forms */
        .auth-container {
            max-width: 400px;
            margin: 40px auto;
            padding: 30px;
            background: var(--card-bg);
            border-radius: 10px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: var(--text-gray);
        }
        
        .form-group input {
            width: 100%;
            padding: 12px;
            background: rgba(255,255,255,0.1);
            border: 1px solid var(--purple-light);
            border-radius: 5px;
            color: white;
            font-size: 1rem;
        }
        
        /* About Page Styles */
        .about-section {
            padding: 40px 20px;
        }
        
        .team-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }
        
        .team-member {
            background: var(--card-bg);
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }
        
        /* Footer */
        .footer {
            background: #0a0a14;
            padding: 40px 20px;
            margin-top: 50px;
            text-align: center;
            border-top: 1px solid var(--purple-medium);
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .mobile-menu-btn {
                display: block;
            }
            
            .nav-links {
                display: none;
                position: absolute;
                top: 60px;
                left: 0;
                width: 100%;
                background: var(--card-bg);
                flex-direction: column;
                padding: 20px;
            }
            
            .nav-links.active {
                display: flex;
            }
            
            .hero h1 {
                font-size: 1.8rem;
            }
            
            .risk-grid {
                grid-template-columns: 1fr;
            }
        }
        
        /* Utility */
        .hidden {
            display: none !important;
        }
        
        .text-center {
            text-align: center;
        }
        
        .mt-20 { margin-top: 20px; }
        .mt-30 { margin-top: 30px; }
        .mb-20 { margin-bottom: 20px; }
        .mb-30 { margin-bottom: 30px; }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar">
        <a href="#home" class="logo">Trading<span>Masters</span></a>
        <button class="mobile-menu-btn" id="menuBtn">
            <i class="fas fa-bars"></i>
        </button>
        <div class="nav-links" id="navLinks">
            <a href="#home" class="active">Home</a>
            <a href="#about">About</a>
            <a href="#risk">Risk Management</a>
            <a href="#education">Education</a>
            <a href="#login" id="loginLink">Login</a>
            <a href="#signup" id="signupLink">Sign Up</a>
            <a href="#logout" id="logoutLink" class="hidden">Logout</a>
        </div>
    </nav>

    <!-- Home Page -->
    <section id="home" class="hero">
        <div class="container">
            <h1 class="purple-heading">Master Trading with Smart Risk Management</h1>
            <p class="sensitive">Trading is risky, but with proper education and risk management strategies, you can navigate markets more confidently.</p>
            <div class="mt-30">
                <a href="#education" class="btn">Start Learning</a>
                <a href="#risk" class="btn">Understand Risks</a>
            </div>
        </div>
    </section>

    <!-- Risk Management Section -->
    <section id="risk" class="container mt-30">
        <h2 class="purple-heading text-center">Risk Management Strategies</h2>
        <p class="sensitive text-center mb-30">Protect your capital while pursuing opportunities</p>
        
        <div class="risk-grid">
            <div class="risk-item">
                <div class="risk-icon">
                    <i class="fas fa-shield-alt"></i>
                </div>
                <h3>Position Sizing</h3>
                <p class="sensitive">Never risk more than 1-2% of capital on a single trade.</p>
            </div>
            
            <div class="risk-item">
                <div class="risk-icon">
                    <i class="fas fa-balance-scale"></i>
                </div>
                <h3>Risk-Reward Ratio</h3>
                <p class="sensitive">Aim for at least 1:2 ratio. Risk $1 to make $2+.</p>
            </div>
            
            <div class="risk-item">
                <div class="risk-icon">
                    <i class="fas fa-stop-circle"></i>
                </div>
                <h3>Stop-Loss Orders</h3>
                <p class="sensitive">Always use stop-loss to limit potential losses.</p>
            </div>
        </div>
    </section>

    <!-- Education Section -->
    <section id="education" class="container mt-30">
        <div class="card">
            <h3><i class="fas fa-graduation-cap"></i> Trading Education</h3>
            <p class="sensitive">Building knowledge is your best defense against market risks.</p>
            
            <div class="mt-20">
                <h4>What You'll Learn:</h4>
                <p class="sensitive">✓ Market basics and terminology</p>
                <p class="sensitive">✓ Technical and fundamental analysis</p>
                <p class="sensitive">✓ Trading psychology</p>
                <p class="sensitive">✓ Risk management techniques</p>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="container mt-30 hidden">
        <div class="about-section">
            <h2 class="purple-heading">About Trading Masters</h2>
            <p class="sensitive mb-20">We're an educational platform focused on responsible trading practices.</p>
            
            <div class="card">
                <h3>Our Mission</h3>
                <p class="sensitive">To provide clear, honest education about trading risks and opportunities without hype or false promises.</p>
            </div>
            
            <div class="team-grid mt-30">
                <div class="team-member">
                    <i class="fas fa-user-tie fa-3x mb-20" style="color: var(--purple-medium);"></i>
                    <h4>Expert Educators</h4>
                    <p class="sensitive">Experienced professionals</p>
                </div>
                
                <div class="team-member">
                    <i class="fas fa-book fa-3x mb-20" style="color: var(--purple-medium);"></i>
                    <h4>Quality Content</h4>
                    <p class="sensitive">Practical, actionable lessons</p>
                </div>
                
                <div class="team-member">
                    <i class="fas fa-handshake fa-3x mb-20" style="color: var(--purple-medium);"></i>
                    <h4>Community Focus</h4>
                    <p class="sensitive">Supportive learning environment</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Login Form -->
    <section id="loginForm" class="auth-container hidden">
        <h2 class="purple-heading text-center">Login</h2>
        <div class="form-group">
            <label>Email</label>
            <input type="email" id="loginEmail" placeholder="your@email.com">
        </div>
        <div class="form-group">
            <label>Password</label>
            <input type="password" id="loginPassword" placeholder="••••••••">
        </div>
        <button class="btn" style="width: 100%;" onclick="login()">Login</button>
        <p class="sensitive text-center mt-20">Demo only - No real login</p>
    </section>

    <!-- Signup Form -->
    <section id="signupForm" class="auth-container hidden">
        <h2 class="purple-heading text-center">Sign Up</h2>
        <div class="form-group">
            <label>Full Name</label>
            <input type="text" id="signupName" placeholder="John Doe">
        </div>
        <div class="form-group">
            <label>Email</label>
            <input type="email" id="signupEmail" placeholder="your@email.com">
        </div>
        <div class="form-group">
            <label>Password</label>
            <input type="password" id="signupPassword" placeholder="••••••••">
        </div>
        <button class="btn" style="width: 100%;" onclick="signup()">Create Account</button>
        <p class="sensitive text-center mt-20">Demo only - No data saved</p>
    </section>

    <!-- Warning Box -->
    <div class="container">
        <div class="warning-box">
            <h3><i class="fas fa-exclamation-triangle"></i> RISK WARNING</h3>
            <p class="sensitive">Trading involves substantial risk of loss. Only trade with money you can afford to lose. Past performance doesn't guarantee future results. Seek independent financial advice.</p>
        </div>
    </div>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <h3>Trading<span>Masters</span></h3>
            <p class="sensitive mt-20">Educational content only. Not financial advice.</p>
            <p class="sensitive mt-20">&copy; 2023 Trading Masters. Demo website.</p>
            <div class="mt-20">
                <a href="#home" class="btn">Home</a>
                <a href="#about" class="btn">About</a>
                <a href="#risk" class="btn">Risk Info</a>
            </div>
        </div>
    </footer>

    <script>
        // Mobile Menu Toggle
        document.getElementById('menuBtn').addEventListener('click', function() {
            document.getElementById('navLinks').classList.toggle('active');
        });

        // Navigation
        const sections = {
            'home': ['#home', '#risk', '#education', '.footer'],
            'about': ['#about'],
            'login': ['#loginForm'],
            'signup': ['#signupForm']
        };

        // Show section and hide others
        function showSection(sectionId) {
            // Hide all sections
            document.querySelectorAll('section, .about-section').forEach(el => {
                el.classList.add('hidden');
            });
            
            // Show selected section
            if (sections[sectionId]) {
                sections[sectionId].forEach(selector => {
                    const el = document.querySelector(selector);
                    if (el) el.classList.remove('hidden');
                });
            }
            
            // Update active nav link
            document.querySelectorAll('.nav-links a').forEach(link => {
                link.classList.remove('active');
            });
            event.target.classList.add('active');
            
            // Close mobile menu
            document.getElementById('navLinks').classList.remove('active');
        }

        // Navigation links
        document.querySelectorAll('.nav-links a, .btn').forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                const target = this.getAttribute('href').replace('#', '');
                
                if (target === 'logout') {
                    logout();
                } else if (target === 'login' || target === 'signup') {
                    showSection(target);
                } else if (target === 'about') {
                    showSection('about');
                } else {
                    showSection('home');
                    // Scroll to section
                    const element = document.getElementById(target);
                    if (element) {
                        window.scrollTo({
                            top: element.offsetTop - 60,
                            behavior: 'smooth'
                        });
                    }
                }
            });
        });

        // Auth Functions
        function login() {
            const email = document.getElementById('loginEmail').value;
            const password = document.getElementById('loginPassword').value;
            
            if (email && password) {
                alert('Demo: Login successful!\n\nEmail: ' + email + '\n\n(This is a demo - no real login)');
                // Show logout, hide login/signup
                document.getElementById('logoutLink').classList.remove('hidden');
                document.getElementById('loginLink').classList.add('hidden');
                document.getElementById('signupLink').classList.add('hidden');
                showSection('home');
            } else {
                alert('Please enter email and password');
            }
        }

        function signup() {
            const name = document.getElementById('signupName').value;
            const email = document.getElementById('signupEmail').value;
            const password = document.getElementById('signupPassword').value;
            
            if (name && email && password) {
                alert('Demo: Account created!\n\nName: ' + name + '\nEmail: ' + email + '\n\n(This is a demo - no data saved)');
                // Auto login after signup
                document.getElementById('logoutLink').classList.remove('hidden');
                document.getElementById('loginLink').classList.add('hidden');
                document.getElementById('signupLink').classList.add('hidden');
                showSection('home');
            } else {
                alert('Please fill all fields');
            }
        }

        function logout() {
            alert('Demo: Logged out successfully');
            document.getElementById('logoutLink').classList.add('hidden');
            document.getElementById('loginLink').classList.remove('hidden');
            document.getElementById('signupLink').classList.remove('hidden');
            showSection('home');
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            showSection('home');
        });
    </script>
</body>
</html>
