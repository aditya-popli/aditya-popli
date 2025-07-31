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
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Animated Header */
        .header {
            text-align: center;
            padding: 60px 0;
            position: relative;
        }

        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="25" cy="25" r="2" fill="rgba(52,152,219,0.1)"><animate attributeName="opacity" values="0;1;0" dur="3s" repeatCount="indefinite"/></circle><circle cx="75" cy="25" r="2" fill="rgba(52,152,219,0.1)"><animate attributeName="opacity" values="0;1;0" dur="3s" begin="1s" repeatCount="indefinite"/></circle><circle cx="50" cy="75" r="2" fill="rgba(52,152,219,0.1)"><animate attributeName="opacity" values="0;1;0" dur="3s" begin="2s" repeatCount="indefinite"/></circle></svg>');
            pointer-events: none;
        }

        .name {
            font-size: 4rem;
            font-weight: bold;
            margin-bottom: 10px;
            animation: slideInFromTop 1s ease-out;
        }

        .tagline {
            font-size: 1.3rem;
            opacity: 0.9;
            margin-bottom: 30px;
            animation: slideInFromBottom 1s ease-out 0.3s both;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            animation: fadeIn 1s ease-out 0.6s both;
        }

        .social-btn {
            padding: 12px 24px;
            background: rgba(52, 152, 219, 0.1);
            border: 2px solid rgba(52, 152, 219, 0.3);
            border-radius: 50px;
            color: #2c3e50;
            text-decoration: none;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }

        .social-btn:hover {
            background: rgba(52, 152, 219, 0.2);
            border-color: #3498db;
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(52, 152, 219, 0.2);
        }

        /* Interactive Cards */
        .section {
            margin: 40px 0;
        }

        .section-title {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 40px;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, #3498db, #2980b9);
            border-radius: 2px;
        }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 40px;
        }

        .card {
            background: rgba(255, 255, 255, 0.8);
            border-radius: 20px;
            padding: 30px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(52, 152, 219, 0.2);
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(52, 152, 219, 0.1), transparent);
            transition: left 0.5s ease;
        }

        .card:hover::before {
            left: 100%;
        }

        .card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(52, 152, 219, 0.3);
            border-color: #3498db;
        }

        .card-icon {
            font-size: 3rem;
            margin-bottom: 20px;
            display: block;
        }

        .card-title {
            font-size: 1.5rem;
            font-weight: bold;
            margin-bottom: 15px;
        }

        .card-content {
            line-height: 1.6;
            opacity: 0.9;
        }

        /* Interactive Skills */
        .skills-container {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            justify-content: center;
            margin-top: 30px;
        }

        .skill-tag {
            padding: 10px 20px;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 25px;
            border: 1px solid rgba(52, 152, 219, 0.3);
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            color: #2c3e50;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
        }

        .skill-tag:hover {
            background: #3498db;
            color: white;
            transform: scale(1.1);
            box-shadow: 0 5px 15px rgba(52, 152, 219, 0.3);
        }

        /* Project Cards */
        .project-card {
            background: rgba(255, 255, 255, 0.8);
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
            border-left: 5px solid #3498db;
            transition: all 0.3s ease;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .project-card:hover {
            transform: translateX(10px);
            background: rgba(255, 255, 255, 0.9);
            box-shadow: 0 10px 30px rgba(52, 152, 219, 0.2);
        }

        .project-title {
            font-size: 1.4rem;
            font-weight: bold;
            margin-bottom: 10px;
            color: #3498db;
        }

        .project-tech {
            font-size: 0.9rem;
            opacity: 0.7;
            margin-bottom: 15px;
        }

        /* Achievements with animations */
        .achievement-item {
            display: flex;
            align-items: center;
            padding: 20px;
            margin: 15px 0;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 10px;
            transition: all 0.3s ease;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }

        .achievement-item:hover {
            background: rgba(255, 255, 255, 0.9);
            transform: scale(1.02);
            box-shadow: 0 8px 25px rgba(52, 152, 219, 0.2);
        }

        .achievement-icon {
            font-size: 2rem;
            margin-right: 20px;
        }

        /* Typing Animation */
        .typing-text {
            border-right: 2px solid #2c3e50;
            animation: typing 3s steps(40, end), blink-caret 0.75s step-end infinite;
            white-space: nowrap;
            overflow: hidden;
        }

        /* Floating elements */
        .floating-element {
            position: absolute;
            animation: float 6s ease-in-out infinite;
        }

        .floating-element:nth-child(1) { top: 20%; left: 10%; animation-delay: 0s; }
        .floating-element:nth-child(2) { top: 60%; right: 10%; animation-delay: 2s; }
        .floating-element:nth-child(3) { bottom: 20%; left: 20%; animation-delay: 4s; }

        /* Contact Section */
        .contact-section {
            text-align: center;
            padding: 60px 0;
            background: rgba(255, 255, 255, 0.6);
            border-radius: 20px;
            margin: 40px 0;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        .contact-btn {
            display: inline-block;
            padding: 15px 35px;
            background: linear-gradient(135deg, #3498db, #2980b9);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 10px 30px rgba(52, 152, 219, 0.3);
        }

        .contact-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(52, 152, 219, 0.4);
        }

        /* Animations */
        @keyframes slideInFromTop {
            0% { transform: translateY(-100px); opacity: 0; }
            100% { transform: translateY(0); opacity: 1; }
        }

        @keyframes slideInFromBottom {
            0% { transform: translateY(100px); opacity: 0; }
            100% { transform: translateY(0); opacity: 1; }
        }

        @keyframes fadeIn {
            0% { opacity: 0; }
            100% { opacity: 1; }
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }

        @keyframes typing {
            from { width: 0; }
            to { width: 100%; }
        }

        @keyframes blink-caret {
            from, to { border-color: transparent; }
            50% { border-color: #2c3e50; }
        }

        /* Interactive hover effects */
        .glow-on-hover {
            transition: all 0.3s ease;
        }

        .glow-on-hover:hover {
            box-shadow: 0 0 20px rgba(52, 152, 219, 0.3);
        }

        /* Responsive */
        @media (max-width: 768px) {
            .name { font-size: 2.5rem; }
            .social-links { flex-direction: column; align-items: center; }
            .cards-grid { grid-template-columns: 1fr; }
        }

        /* Counter Animation */
        .counter {
            font-size: 2rem;
            font-weight: bold;
            color: #3498db;
        }
    </style>
</head>
<body>
    <div class="floating-element">💻</div>
    <div class="floating-element">🚀</div>
    <div class="floating-element">⚡</div>

    <div class="container">
        <!-- Header Section -->
        <header class="header">
            <h1 class="name">👨‍💻 Aditya Popli</h1>
            <p class="tagline typing-text">Turning thoughts into code, and code into solutions.</p>
            <div class="social-links">
                <a href="#" class="social-btn glow-on-hover">🌐 Portfolio</a>
                <a href="#" class="social-btn glow-on-hover">💼 LinkedIn</a>
                <a href="#" class="social-btn glow-on-hover">⚡ GitHub</a>
                <a href="mailto:popli.aditya04@gmail.com" class="social-btn glow-on-hover">📧 Email</a>
            </div>
        </header>

        <!-- About Section -->
        <section class="section">
            <div class="cards-grid">
                <div class="card glow-on-hover">
                    <span class="card-icon">🎓</span>
                    <h3 class="card-title">Education</h3>
                    <p class="card-content">Computer Science Engineer @ BVCOE (2022–2026)<br>Building the foundation for tomorrow's innovations</p>
                </div>
                <div class="card glow-on-hover">
                    <span class="card-icon">💡</span>
                    <h3 class="card-title">Passion</h3>
                    <p class="card-content">ML, Full Stack Development & AI for Good<br>Creating technology that makes a difference</p>
                </div>
                <div class="card glow-on-hover">
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
                <div class="card glow-on-hover">
                    <span class="card-icon">🤖</span>
                    <h3 class="card-title">AI for Accessibility</h3>
                    <p class="card-content">Building Thoughts to Text - empowering speech-impaired individuals through neural interfaces</p>
                </div>
                <div class="card glow-on-hover">
                    <span class="card-icon">🧬</span>
                    <h3 class="card-title">Tech for Wellness</h3>
                    <p class="card-content">Exploring correlations between sleep patterns and mental health using data science</p>
                </div>
                <div class="card glow-on-hover">
                    <span class="card-icon">🚗</span>
                    <h3 class="card-title">Autonomous Systems</h3>
                    <p class="card-content">Built driving models using LiDAR + Camera fusion at NXP-AIM 2024</p>
                </div>
                <div class="card glow-on-hover">
                    <span class="card-icon">👩‍🍼</span>
                    <h3 class="card-title">Digital Health</h3>
                    <p class="card-content">Nurture Hub - comprehensive platform for maternal wellness and support</p>
                </div>
            </div>
        </section>

        <!-- Experience -->
        <section class="section">
            <h2 class="section-title">💼 Experience</h2>
            <div class="project-card">
                <h3 class="project-title">💻 Web Developer @ Raadhi</h3>
                <p class="project-tech">Jun 2025 - Present</p>
                <p class="card-content">Designed a modern, responsive React website for a fashion brand • Boosted engagement via UI/UX revamp + social media strategies</p>
            </div>
            <div class="project-card">
                <h3 class="project-title">💰 Treasurer @ IEEE BVCOE</h3>
                <p class="project-tech">2024 - 2025</p>
                <p class="card-content">Pulled treasury from deficit to <span class="counter">₹40K+</span> surplus 💸 • Enabled 20+ successful events via smart budgeting & logistics</p>
            </div>
        </section>

        <!-- Tech Stack -->
        <section class="section">
            <h2 class="section-title">🛠 Tech Toolbox</h2>
            <div class="skills-container">
                <div class="skill-tag">C/C++</div>
                <div class="skill-tag">Python</div>
                <div class="skill-tag">HTML</div>
                <div class="skill-tag">CSS</div>
                <div class="skill-tag">JavaScript</div>
                <div class="skill-tag">React.js</div>
                <div class="skill-tag">Machine Learning</div>
                <div class="skill-tag">Deep Learning</div>
                <div class="skill-tag">MySQL</div>
                <div class="skill-tag">PostgreSQL</div>
                <div class="skill-tag">Git</div>
                <div class="skill-tag">GitHub</div>
                <div class="skill-tag">Power BI</div>
            </div>
        </section>

        <!-- Projects -->
        <section class="section">
            <h2 class="section-title">📚 Academic Projects</h2>
            <div class="project-card">
                <h3 class="project-title">🔹 Thoughts to Text</h3>
                <p class="project-tech">Deep Learning | EEG | NLP</p>
                <p class="card-content">Convert brainwaves into text — giving a voice to the voiceless through advanced neural signal processing</p>
            </div>
            <div class="project-card">
                <h3 class="project-title">🔹 Nurture Hub</h3>
                <p class="project-tech">React.js | HealthTech</p>
                <p class="card-content">Comprehensive support platform for pregnant women with expert advice, community forums & wellness tools</p>
            </div>
            <div class="project-card">
                <h3 class="project-title">🔹 Nasha-Mukti DB</h3>
                <p class="project-tech">PostgreSQL | CivicTech</p>
                <p class="card-content">Transparent, centralized database system for India's rehabilitation centers with real-time tracking</p>
            </div>
        </section>

        <!-- Achievements -->
        <section class="section">
            <h2 class="section-title">🏆 Achievements</h2>
            <div class="achievement-item glow-on-hover">
                <span class="achievement-icon">🧪</span>
                <div>
                    <h3>Research Presentation @ ICICC 2025</h3>
                    <p>Presented groundbreaking research on BMI vs Sleep Disorders correlation</p>
                </div>
            </div>
            <div class="achievement-item glow-on-hover">
                <span class="achievement-icon">🚘</span>
                <div>
                    <h3>Regional Finalist - NXP-AIM 2024</h3>
                    <p>Smart Driving Challenge using advanced sensor fusion techniques</p>
                </div>
            </div>
            <div class="achievement-item glow-on-hover">
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
            <p style="font-size: 1.2rem; margin-bottom: 30px;">
                Open to impact-driven AI projects • Hackathons & Research Collabs • Tech Talks & Mentoring
            </p>
            <a href="mailto:popli.aditya04@gmail.com" class="contact-btn">
                📫 Get In Touch
            </a>
            <div style="margin-top: 40px; font-style: italic; opacity: 0.8;">
                "The best way to predict the future is to create it." – Alan Kay
            </div>
        </section>
    </div>

    <script>
        // Add interactive animations
        document.addEventListener('DOMContentLoaded', function() {
            // Animate skill tags on hover
            const skillTags = document.querySelectorAll('.skill-tag');
            skillTags.forEach(tag => {
                tag.addEventListener('mouseenter', function() {
                    this.style.background = #3498db;
                    this.style.color = 'white';
                });
                tag.addEventListener('mouseleave', function() {
                    this.style.background = 'rgba(255, 255, 255, 0.8)';
                    this.style.color = '#2c3e50';
                });
            });

            // Add ripple effect to cards
            const cards = document.querySelectorAll('.card, .project-card');
            cards.forEach(card => {
                card.addEventListener('click', function(e) {
                    const ripple = document.createElement('div');
                    const rect = this.getBoundingClientRect();
                    const size = Math.max(rect.width, rect.height);
                    const x = e.clientX - rect.left - size / 2;
                    const y = e.clientY - rect.top - size / 2;
                    
                    ripple.style.cssText = `
                        position: absolute;
                        width: ${size}px;
                        height: ${size}px;
                        left: ${x}px;
                        top: ${y}px;
                        background: rgba(52, 152, 219, 0.3);
                        border-radius: 50%;
                        transform: scale(0);
                        animation: ripple 0.6s linear;
                        pointer-events: none;
                    `;
                    
                    this.appendChild(ripple);
                    setTimeout(() => ripple.remove(), 600);
                });
            });

            // Add parallax scrolling effect
            window.addEventListener('scroll', () => {
                const scrolled = window.pageYOffset;
                const parallax = document.querySelectorAll('.floating-element');
                parallax.forEach((element, index) => {
                    const speed = 0.5 + (index * 0.1);
                    element.style.transform = translateY(${scrolled * speed}px);
                });
            });
        });

        // Add CSS for ripple animation
        const style = document.createElement('style');
        style.textContent = `
            @keyframes ripple {
                to {
                    transform: scale(4);
                    opacity: 0;
                }
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>
