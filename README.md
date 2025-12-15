<!DOCTYPE html>
<html>
<head>
    <title>Trading Masters - Risk Education</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        /* Reset & Base */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { 
            font-family: Arial, sans-serif; 
            background: #0f0f23; 
            color: white; 
            padding-top: 70px; 
            line-height: 1.6;
        }
        
        /* Navigation */
        .navbar {
            background: #000;
            position: fixed;
            top: 0;
            width: 100%;
            padding: 15px;
            display: flex;
            justify-content: center;
            gap: 20px;
            border-bottom: 3px solid #8a2be2;
            z-index: 1000;
        }
        .nav-btn {
            color: white;
            text-decoration: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
        }
        .nav-btn:hover, .active {
            background: #8a2be2;
        }
        
        /* Colors */
        .purple-heading { color: #8a2be2; margin: 20px 0; }
        .light-purple { color: #d8bfd8; margin: 10px 0; }
        
        /* Sections */
        .section {
            padding: 30px 20px;
            max-width: 800px;
            margin: 0 auto;
            display: none;
        }
        .active-section { display: block; }
        
        /* Cards */
        .card {
            background: #1a1a2e;
            padding: 25px;
            margin: 20px 0;
            border-radius: 10px;
            border-left: 5px solid #8a2be2;
        }
        
        /* Buttons */
        .btn {
            background: #8a2be2;
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 5px;
            margin: 10px 5px;
            cursor: pointer;
            font-size: 16px;
        }
        .btn:hover { background: #6a0dad; }
        
        /* Forms */
        .form-group { margin: 20px 0; }
        input, select {
            width: 100%;
            padding: 12px;
            margin: 8px 0;
            background: rgba(255,255,255,0.1);
            border: 1px solid #8a2be2;
            border-radius: 5px;
            color: white;
        }
        
        /* Risk Cards */
        .risk-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }
        .risk-card {
            background: #1a1a2e;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }
        
        /* Warning */
        .warning {
            background: #ff3333;
            padding: 20px;
            margin: 30px 20px;
            border-radius: 10px;
            text-align: center;
        }
        
        /* Mobile */
        @media (max-width: 600px) {
            .navbar { gap: 10px; padding: 10px; }
            .nav-btn { padding: 8px 10px; font-size: 14px; }
            .risk-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <div class="navbar">
        <a class="nav-btn" onclick="showSection('home')">Home</a>
        <a class="nav-btn" onclick="showSection('risk')">Risk Management</a>
        <a class="nav-btn" onclick="showSection('about')">About</a>
        <a class="nav-btn" onclick="showSection('login')">Login</a>
        <a class="nav-btn" onclick="showSection('signup')">Sign Up</a>
        <a class="nav-btn" onclick="logout()" id="logoutBtn" style="display:none">Logout</a>
    </div>
    
    <!-- Home Section -->
    <div id="home" class="section active-section">
        <h1 class="purple-heading">Master Trading with Smart Risk Management</h1>
        <p class="light-purple">Learn how to navigate financial markets while protecting your capital through proper risk management strategies.</p>
        
        <div class="card">
            <h3>Why Risk Management Matters</h3>
            <p class="light-purple">Trading involves significant risk, but with the right education and strategies, you can learn to manage these risks effectively.</p>
            <button class="btn" onclick="showSection('risk')">Learn Risk Strategies</button>
            <button class="btn" onclick="showSection('signup')">Start Learning Free</button>
        </div>
    </div>
    
    <!-- Risk Management Section -->
    <div id="risk" class="section">
        <h1 class="purple-heading">Essential Risk Management Strategies</h1>
        <p class="light-purple">Protect your trading capital with these proven techniques:</p>
        
        <div class="risk-grid">
            <div class="risk-card">
                <h3>📊 Position Sizing</h3>
                <p class="light-purple">Never risk more than 1-2% of your total capital on any single trade.</p>
            </div>
            <div class="risk-card">
                <h3>⚖️ Risk-Reward Ratio</h3>
                <p class="light-purple">Always aim for at least 1:2 ratio. Risk $1 to potentially make $2 or more.</p>
            </div>
            <div class="risk-card">
                <h3>🛑 Stop-Loss Orders</h3>
                <p class="light-purple">Use stop-loss orders on EVERY trade to limit potential losses automatically.</p>
            </div>
        </div>
        
        <div class="card">
            <h3>Trading Psychology</h3>
            <p class="light-purple">Emotional control is crucial. Fear and greed cause most trading losses. Maintain discipline and stick to your trading plan.</p>
        </div>
        
        <button class="btn" onclick="showSection('home')">Back to Home</button>
    </div>
    
    <!-- About Section -->
    <div id="about" class="section">
        <h1 class="purple-heading">About Trading Masters</h1>
        
        <div class="card">
            <h3>Our Mission</h3>
            <p class="light-purple">We provide honest, clear education about trading risks and opportunities without hype or false promises.</p>
        </div>
        
        <div class="card">
            <h3>What We Teach</h3>
            <p class="light-purple">• Market analysis fundamentals</p>
            <p class="light-purple">• Risk management techniques</p>
            <p class="light-purple">• Trading psychology</p>
            <p class="light-purple">• Strategy development</p>
        </div>
        
        <button class="btn" onclick="showSection('home')">Back to Home</button>
    </div>
    
    <!-- Login Section -->
    <div id="login" class="section">
        <h1 class="purple-heading">Login to Your Account</h1>
        
        <div class="card">
            <div class="form-group">
                <label>Email Address</label>
                <input type="email" id="loginEmail" placeholder="you@example.com">
            </div>
            <div class="form-group">
                <label>Password</label>
                <input type="password" id="loginPassword" placeholder="••••••••">
            </div>
            <button class="btn" onclick="loginUser()">Login Now</button>
            <p class="light-purple" style="margin-top:15px;font-size:14px;">Demo: Use any email/password</p>
        </div>
        
        <button class="btn" onclick="showSection('home')">Back to Home</button>
    </div>
    
    <!-- Signup Section -->
    <div id="signup" class="section">
        <h1 class="purple-heading">Create Free Account</h1>
        
        <div class="card">
            <div class="form-group">
                <label>Full Name</label>
                <input type="text" id="signupName" placeholder="John Smith">
            </div>
            <div class="form-group">
                <label>Email Address</label>
                <input type="email" id="signupEmail" placeholder="you@example.com">
            </div>
            <div class="form-group">
                <label>Password</label>
                <input type="password" id="signupPassword" placeholder="At least 6 characters">
            </div>
            <button class="btn" onclick="signupUser()">Create Account</button>
            <p class="light-purple" style="margin-top:15px;font-size:14px;">Demo account - No real data stored</p>
        </div>
        
        <button class="btn" onclick="showSection('home')">Back to Home</button>
    </div>
    
    <!-- Risk Warning -->
    <div class="warning">
        <h3>⚠️ IMPORTANT RISK WARNING</h3>
        <p class="light-purple">Trading financial instruments carries high risk of loss. Only trade with money you can afford to lose. Past performance does not guarantee future results. This is educational content, not financial advice.</p>
    </div>
    
    <script>
        // Navigation function
        function showSection(sectionId) {
            // Hide all sections
            document.querySelectorAll('.section').forEach(section => {
                section.classList.remove('active-section');
            });
            
            // Show selected section
            document.getElementById(sectionId).classList.add('active-section');
            
            // Update active nav button
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
            
            // Scroll to top
            window.scrollTo(0, 0);
        }
        
        // Login function
        function loginUser() {
            const email = document.getElementById('loginEmail').value;
            const password = document.getElementById('loginPassword').value;
            
            if (!email || !password) {
                alert('Please enter both email and password');
                return;
            }
            
            alert('Login successful!\n\nEmail: ' + email + '\n\n(Note: This is a demo. No real login occurred.)');
            
            // Update UI for logged in state
            document.getElementById('logoutBtn').style.display = 'block';
            document.querySelectorAll('.nav-btn').forEach(btn => {
                if (btn.textContent === 'Login' || btn.textContent === 'Sign Up') {
                    btn.style.display = 'none';
                }
            });
            
            showSection('home');
        }
        
        // Signup function
        function signupUser() {
            const name = document.getElementById('signupName').value;
            const email = document.getElementById('signupEmail').value;
            const password = document.getElementById('signupPassword').value;
            
            if (!name || !email || !password) {
                alert('Please fill all fields');
                return;
            }
            
            if (password.length < 6) {
                alert('Password must be at least 6 characters');
                return;
            }
            
            alert('Account created successfully!\n\nName: ' + name + '\nEmail: ' + email + '\n\n(Note: This is a demo. No data was saved.)');
            
            // Update UI for logged in state
            document.getElementById('logoutBtn').style.display = 'block';
            document.querySelectorAll('.nav-btn').forEach(btn => {
                if (btn.textContent === 'Login' || btn.textContent === 'Sign Up') {
                    btn.style.display = 'none';
                }
            });
            
            showSection('home');
        }
        
        // Logout function
        function logout() {
            alert('You have been logged out');
            
            // Update UI for logged out state
            document.getElementById('logoutBtn').style.display = 'none';
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.style.display = 'block';
            });
            
            showSection('home');
        }
        
        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            // Set first nav button as active
            document.querySelector('.nav-btn').classList.add('active');
        });
    </script>
</body>
</html>
