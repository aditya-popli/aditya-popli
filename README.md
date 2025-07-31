<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aditya Popli - Interactive Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            color: #2c3e50;
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
        }

        /* Enhanced Background Particles */
        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: rgba(52, 152, 219, 0.1);
            border-radius: 50%;
            animation: float-particles 6s infinite linear;
        }

        /* Animated Header with Improved Typography */
        .header {
            text-align: center;
            padding: 80px 0;
            position: relative;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 30px;
            backdrop-filter: blur(20px);
            margin-bottom: 40px;
            box-shadow: 0 20px 60px rgba(52, 152, 219, 0.1);
        }

        .header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(52, 152, 219, 0.05) 0%, transparent 70%);
            animation: rotate 20s linear infinite;
            pointer-events: none;
        }

        .name {
            font-size: 4.5rem;
            font-weight: 900;
            margin-bottom: 15px;
            background: linear-gradient(135deg, #2c3e50, #3498db);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: slideInFromTop 1s ease-out;
            text-shadow: 0 10px 30px rgba(52, 152, 219, 0.2);
        }

        .tagline {
            font-size: 1.4rem;
            opacity: 0.9;
            margin-bottom: 40px;
            animation: slideInFromBottom 1s ease-out 0.3s both;
            position: relative;
        }

        .tagline::after {
            content: '';
            position: absolute;
            right: 0;
            top: 0;
            bottom: 0;
            width: 2px;
            background: #3498db;
            animation: blink 1s infinite;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 25px;
            animation: fadeIn 1s ease-out 0.6s both;
            flex-wrap: wrap;
        }

        .social-btn {
            padding: 15px 30px;
            background: rgba(255, 255, 255, 0.2);
            border: 2px solid rgba(52, 152, 219, 0.3);
            border-radius: 50px;
            color: #2c3e50;
            text-decoration: none;
            transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            backdrop-filter: blur(20px);
            position: relative;
            overflow: hidden;
            font-weight: 600;
        }

        .social-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(52, 152, 219, 0.2), transparent);
            transition: left 0.6s ease;
        }

        .social-btn:hover::before {
            left: 100%;
        }

        .social-btn:hover {
            background: rgba(52, 152, 219, 0.1);
            border-color: #3498db;
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 15px 30px rgba(52, 152, 219, 0.3);
        }

        /* Enhanced Interactive Cards */
        .section {
            margin: 60px 0;
            opacity: 0;
            transform: translateY(50px);
            animation: slideInUp 0.8s ease-out forwards;
        }

        .section:nth-child(even) {
            animation-delay: 0.2s;
        }

        .section:nth-child(odd) {
            animation-delay: 0.1s;
        }

        .section-title {
            font-size: 2.8rem;
            text-align: center;
            margin-bottom: 50px;
            position: relative;
            font-weight: 800;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 120px;
            height: 5px;
            background: linear-gradient(90deg, #3498db, #2980b9);
            border-radius: 3px;
            animation: expandWidth 0.8s ease-out 0.5s both;
        }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 35px;
            margin-top: 50px;
        }

        .card {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 25px;
            padding: 35px;
            backdrop-filter: blur(20px);
            border: 1px solid rgba(52, 152, 219, 0.2);
            transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            cursor: pointer;
            position: relative;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            transform-style: preserve-3d;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(52, 152, 219, 0.1), transparent);
            transition: left 0.6s ease;
        }

        .card:hover::before {
            left: 100%;
        }

        .card:hover {
            transform: translateY(-15px) rotateX(5deg) rotateY(5deg);
            box-shadow: 0 30px 60px rgba(52, 152, 219, 0.25);
            border-color: #3498db;
            background: rgba(255, 255, 255, 0.95);
        }

        .card-icon {
            font-size: 3.5rem;
            margin-bottom: 25px;
            display: block;
            transition: transform 0.3s ease;
        }

        .card:hover .card-icon {
            transform: scale(1.2) rotate(10deg);
        }

        .card-title {
            font-size: 1.6rem;
            font-weight: bold;
            margin-bottom: 18px;
            color: #2c3e50;
        }

        .card-content {
            line-height: 1.7;
            opacity: 0.9;
            font-size: 1rem;
        }

        /* Enhanced Skills with Proficiency Bars */
        .skills-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 40px;
        }

        .skill-item {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }

        .skill-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(52, 152, 219, 0.2);
        }

        .skill-name {
            font-weight: 600;
            margin-bottom: 10px;
            color: #2c3e50;
        }

        .skill-bar {
            width: 100%;
            height: 8px;
            background: rgba(52, 152, 219, 0.2);
            border-radius: 4px;
            overflow: hidden;
        }

        .skill-progress {
            height: 100%;
            background: linear-gradient(90deg, #3498db, #2980b9);
            border-radius: 4px;
            transition: width 1s ease-out;
            width: 0;
        }

        /* Enhanced Project Cards */
        .project-card {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            padding: 30px;
            margin: 25px 0;
            border-left: 6px solid #3498db;
            transition: all 0.4s ease;
            cursor: pointer;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
        }

        .project-card::after {
            content: '';
            position: absolute;
            top: 0;
            right: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(-90deg, transparent, rgba(52, 152, 219, 0.1), transparent);
            transition: right 0.6s ease;
        }

        .project-card:hover::after {
            right: 100%;
        }

        .project-card:hover {
            transform: translateX(15px) scale(1.02);
            background: rgba(255, 255, 255, 0.95);
            box-shadow: 0 20px 50px rgba(52, 152, 219, 0.2);
            border-left-color: #2980b9;
        }

        .project-title {
            font-size: 1.5rem;
            font-weight: bold;
            margin-bottom: 12px;
            color: #3498db;
            transition: color 0.3s ease;
        }

        .project-card:hover .project-title {
            color: #2980b9;
        }

        .project-tech {
            font-size: 0.95rem;
            opacity: 0.8;
            margin-bottom: 15px;
            font-weight: 500;
        }

        /* Enhanced Achievements */
        .achievement-item {
            display: flex;
            align-items: center;
            padding: 25px;
            margin: 20px 0;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            transition: all 0.4s ease;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
        }

        .achievement-item::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            width: 5px;
            height: 100%;
            background: linear-gradient(180deg, #3498db, #2980b9);
            transform: scaleY(0);
            transition: transform 0.3s ease;
        }

        .achievement-item:hover::before {
            transform: scaleY(1);
        }

        .achievement-item:hover {
            background: rgba(255, 255, 255, 0.95);
            transform: translateX(10px) scale(1.02);
            box-shadow: 0 15px 40px rgba(52, 152, 219, 0.2);
        }

        .achievement-icon {
            font-size: 2.5rem;
            margin-right: 25px;
            transition: transform 0.3s ease;
        }

        .achievement-item:hover .achievement-icon {
            transform: scale(1.2) rotate(5deg);
        }

        /* Enhanced Contact Section */
        .contact-section {
            text-align: center;
            padding: 80px 40px;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 30px;
            margin: 60px 0;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.1);
            backdrop-filter: blur(20px);
            position: relative;
            overflow: hidden;
        }

        .contact-section::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(52, 152, 219, 0.05) 0%, transparent 70%);
            animation: rotate 30s linear infinite reverse;
        }

        .contact-btn {
            display: inline-block;
            padding: 18px 40px;
            background: linear-gradient(135deg, #3498db, #2980b9);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            transition: all 0.4s ease;
            box-shadow: 0 15px 35px rgba(52, 152, 219, 0.3);
            position: relative;
            overflow: hidden;
            font-size: 1.1rem;
        }

        .contact-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.6s ease;
        }

        .contact-btn:hover::before {
            left: 100%;
        }

        .contact-btn:hover {
            transform: translateY(-8px) scale(1.05);
            box-shadow: 0 25px 50px rgba(52, 152, 219, 0.4);
        }

        /* Counter Animation */
        .counter {
            font-size: 2.2rem;
            font-weight: bold;
            color: #3498db;
            text-shadow: 0 5px 15px rgba(52, 152, 219, 0.3);
        }

        /* Enhanced Animations */
        @keyframes slideInFromTop {
            0% { transform: translateY(-100px); opacity: 0; }
            100% { transform: translateY(0); opacity: 1; }
        }

        @keyframes slideInFromBottom {
            0% { transform: translateY(100px); opacity: 0; }
            100% { transform: translateY(0); opacity: 1; }
        }

        @keyframes slideInUp {
            0% { transform: translateY(50px); opacity: 0; }
            100% { transform: translateY(0); opacity: 1; }
        }

        @keyframes fadeIn {
            0% { opacity: 0; }
            100% { opacity: 1; }
        }

        @keyframes expandWidth {
            0% { width: 0; }
            100% { width: 120px; }
        }

        @keyframes float-particles {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { transform: translateY(-100px) rotate(360deg); opacity: 0; }
        }

        @keyframes rotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        @keyframes blink {
            0%, 50% { opacity: 1; }
            51%, 100% { opacity: 0; }
        }

        /* Scroll Indicator */
        .scroll-indicator {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: rgba(52, 152, 219, 0.2);
            z-index: 1000;
        }

        .scroll-progress {
            height: 100%;
            background: linear-gradient(90deg, #3498db, #2980b9);
            width: 0%;
            transition: width 0.1s ease;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .name { font-size: 3rem; }
            .section-title { font-size: 2.2rem; }
            .social-links { flex-direction: column; align-items: center; gap: 15px; }
            .cards-grid { grid-template-columns: 1fr; }
            .skills-container { grid-template-columns: 1fr; }
            .header { padding: 60px 0; }
            .contact-section { padding: 60px 20px; }
        }

        @media (max-width: 480px) {
            .name { font-size: 2.5rem; }
            .container { padding: 15px; }
            .card, .project-card { padding: 20px; }
        }

        /* Performance optimizations */
        .card, .project-card, .achievement-item {
            will-change: transform;
        }

        /* Interactive hover states */
        .interactive:hover {
            cursor: pointer;
        }
    </style>
</head>
<body>
    <!-- Scroll Progress Indicator -->
    <div class="scroll-indicator">
        <div class="scroll-progress" id="scrollProgress"></div>
    </div>

    <!-- Animated Particles Background -->
    <div class="particles" id="particles"></div>

    <div class="container">
        <!-- Enhanced Header Section -->
        <header class="header">
            <h1 class="name">👨‍💻 Aditya Popli</h1>
            <p class="tagline" id="typewriter">Turning thoughts into code, and code into solutions.</p>
            <div class="social-links">
                <a href="#" class="social-btn">🌐 Portfolio</a>
                <a href="#" class="social-btn">💼 LinkedIn</a>
                <a href="#" class="social-btn">⚡ GitHub</a>
                <a href="mailto:popli.aditya04@gmail.com" class="social-btn">📧 Email</a>
            </div>
        </header>

        <!-- About Section -->
        <section class="section">
            <div class="cards-grid">
                <div class="card interactive">
                    <span class="card-icon">🎓</span>
                    <h3 class="card-title">Education</h3>
                    <p class="card-content">Computer Science Engineer @ BVCOE (2022–2026)<br>Building the foundation for tomorrow's innovations</p>
                </div>
                <div class="card interactive">
                    <span class="card-icon">💡</span>
                    <h3 class="card-title">Passion</h3>
                    <p class="card-content">ML, Full Stack Development & AI for Good<br>Creating technology that makes a difference</p>
                </div>
                <div class="card interactive">
                    <span class="card-icon">📊</span>
                    <h3 class="card-title">Philosophy</h3>
                    <p class="card-content">Believer in data, design, and impactful tech<br>Always building, always learning 🚀</p>
                </div>
            </div>
        </section>

        <!-- Current Focus -->
        <section class="section">
            <h2 class="section-title">🧠 Current Focus Areas</h2>
            <div class="cards-grid">
                <div class="card interactive">
                    <span class="card-icon">🤖</span>
                    <h3 class="card-title">AI for Accessibility</h3>
                    <p class="card-content">Building Thoughts to Text - empowering speech-impaired individuals through neural interfaces</p>
                </div>
                <div class="card interactive">
                    <span class="card-icon">🧬</span>
                    <h3 class="card-title">Tech for Wellness</h3>
                    <p class="card-content">Exploring correlations between sleep patterns and mental health using data science</p>
                </div>
                <div class="card interactive">
                    <span class="card-icon">🚗</span>
                    <h3 class="card-title">Autonomous Systems</h3>
                    <p class="card-content">Built driving models using LiDAR + Camera fusion at NXP-AIM 2024</p>
                </div>
                <div class="card interactive">
                    <span class="card-icon">👩‍🍼</span>
                    <h3 class="card-title">Digital Health</h3>
                    <p class="card-content">Nurture Hub - comprehensive platform for maternal wellness and support</p>
                </div>
            </div>
        </section>

        <!-- Experience -->
        <section class="section">
            <h2 class="section-title">💼 Experience</h2>
            <div class="project-card interactive">
                <h3 class="project-title">💻 Web Developer @ Raadhi</h3>
                <p class="project-tech">Jun 2025 - Present</p>
                <p class="card-content">Designed a modern, responsive React website for a fashion brand • Boosted engagement via UI/UX revamp + social media strategies</p>
            </div>
            <div class="project-card interactive">
                <h3 class="project-title">💰 Treasurer @ IEEE BVCOE</h3>
                <p class="project-tech">2024 - 2025</p>
                <p class="card-content">Pulled treasury from deficit to <span class="counter" data-target="40000">₹0</span>+ surplus 💸 • Enabled 20+ successful events via smart budgeting & logistics</p>
            </div>
        </section>

        <!-- Enhanced Tech Stack -->
        <section class="section">
            <h2 class="section-title">🛠 Tech Toolbox</h2>
            <div class="skills-container">
                <div class="skill-item">
                    <div class="skill-name">C/C++</div>
                    <div class="skill-bar"><div class="skill-progress" data-width="90%"></div></div>
                </div>
                <div class="skill-item">
                    <div class="skill-name">Python</div>
                    <div class="skill-bar"><div class="skill-progress" data-width="95%"></div></div>
                </div>
                <div class="skill-item">
                    <div class="skill-name">JavaScript</div>
                    <div class="skill-bar"><div class="skill-progress" data-width="85%"></div></div>
                </div>
                <div class="skill-item">
                    <div class="skill-name">React.js</div>
                    <div class="skill-bar"><div class="skill-progress" data-width="88%"></div></div>
                </div>
                <div class="skill-item">
                    <div class="skill-name">Machine Learning</div>
                    <div class="skill-bar"><div class="skill-progress" data-width="92%"></div></div>
                </div>
                <div class="skill-item">
                    <div class="skill-name">Deep Learning</div>
                    <div class="skill-bar"><div class="skill-progress" data-width="87%"></div></div>
                </div>
                <div class="skill-item">
                    <div class="skill-name">Database Systems</div>
                    <div class="skill-bar"><div class="skill-progress" data-width="83%"></div></div>
                </div>
                <div class="skill-item">
                    <div class="skill-name">Power BI</div>
                    <div class="skill-bar"><div class="skill-progress" data-width="80%"></div></div>
                </div>
            </div>
        </section>

        <!-- Projects -->
        <section class="section">
            <h2 class="section-title">📚 Academic Projects</h2>
            <div class="project-card interactive">
                <h3 class="project-title">🔹 Thoughts to Text</h3>
                <p class="project-tech">Deep Learning | EEG | NLP</p>
                <p class="card-content">Convert brainwaves into text — giving a voice to the voiceless through advanced neural signal processing</p>
            </div>
            <div class="project-card interactive">
                <h3 class="project-title">🔹 Nurture Hub</h3>
                <p class="project-tech">React.js | HealthTech</p>
                <p class="card-content">Comprehensive support platform for pregnant women with expert advice, community forums & wellness tools</p>
            </div>
            <div class="project-card interactive">
                <h3 class="project-title">🔹 Nasha-Mukti DB</h3>
                <p class="project-tech">PostgreSQL | CivicTech</p>
                <p class="card-content">Transparent, centralized database system for India's rehabilitation centers with real-time tracking</p>
            </div>
        </section>

        <!-- Achievements -->
        <section class="section">
            <h2 class="section-title">🏆 Achievements</h2>
            <div class="achievement-item interactive">
                <span class="achievement-icon">🧪</span>
                <div>
                    <h3>Research Presentation @ ICICC 2025</h3>
                    <p>Presented groundbreaking research on BMI vs Sleep Disorders correlation</p>
                </div>
            </div>
            <div class="achievement-item interactive">
                <span class="achievement-icon">🚘</span>
                <div>
                    <h3>Regional Finalist - NXP-AIM 2024</h3>
                    <p>Smart Driving Challenge using advanced sensor fusion techniques</p>
                </div>
            </div>
            <div class="achievement-item interactive">
                <span class="achievement-icon">♻</span>
                <div>
                    <h3>Runner-Up - Hult Prize BVCOE</h3>
                    <p>Innovative Plastic Waste Management Initiative for sustainable future</p>
                </div>
            </div>
        </section>

        <!-- Contact -->
        <section class="contact-section">
            <h2 class="section-title">🔍 Let's Collaborate!</h2>
            <p style="font-size: 1.3rem; margin-bottom: 40px; opacity: 0.9;">
                Open to impact-driven AI projects • Hackathons & Research Collabs • Tech Talks & Mentoring
            </p>
            <a href="mailto:popli.aditya04@gmail.com" class="contact-btn">
                📫 Get In Touch
            </a>
            <div style="margin-top: 50px; font-style: italic; opacity: 0.8; font-size: 1.1rem;">
                "The best way to predict the future is to create it." – Alan Kay
            </div>
        </section>
    </div>

    <script>
        // Enhanced JavaScript with performance optimizations
        document.addEventListener('DOMContentLoaded', function() {
            // Scroll progress indicator
            window.addEventListener('scroll', throttle(() => {
                const scrollTop = window.pageYOffset;
                const docHeight = document.body.scrollHeight - window.innerHeight;
                const scrollPercent = (scrollTop / docHeight) * 100;
                document.getElementById('scrollProgress').style.width = scrollPercent + '%';
            }, 16));

            // Create animated particles
            createParticles();

            // Animate skill progress bars on scroll
            const skillBars = document.querySelectorAll('.skill-progress');
            const observerOptions = {
                threshold: 0.5,
                rootMargin: '0px 0px -100px 0px'
            };

            const skillObserver = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        const progressBar = entry.target;
                        const width = progressBar.getAttribute('data-width');
                        progressBar.style.width = width;
                    }
                });
            }, observerOptions);

            skillBars.forEach(bar => skillObserver.observe(bar));

            // Counter animation
            const counters = document.querySelectorAll('.counter');
            const counterObserver = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        const counter = entry.target;
                        const target = parseInt(counter.getAttribute('data-target'));
                        animateCounter(counter, target);
                    }
                });
            }, observerOptions);

            counters.forEach(counter => counterObserver.observe(counter));

            // Enhanced ripple effect
            const interactiveElements = document.querySelectorAll('.interactive');
            interactiveElements.forEach(element => {
                element.addEventListener('click', createRippleEffect);
            });

            // Parallax scrolling for cards
            window.addEventListener('scroll', throttle(() => {
                const scrolled = window.pageYOffset;
                const cards = document.querySelectorAll('.card');
                
                cards.forEach((card, index) => {
                    const speed = 0.1 + (index % 3) * 0.05;
                    const yPos = -(scrolled * speed);
                    card.style.transform = translateY(${yPos}px);
                });
            }, 16));

            // Typewriter effect for tagline
