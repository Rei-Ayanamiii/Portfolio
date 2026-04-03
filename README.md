<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SEAK CHHENGLY | Portfolio</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;700;900&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #00f5ff;
            --secondary: #ff00aa;
        }

        body {
            font-family: 'Inter', system-ui, sans-serif;
            background: #0a0a0a;
            color: white;
            overflow-x: hidden;
        }

        /* Layer 1: Anime Animation Background */
        .anime-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -3;
            background: linear-gradient(135deg, #1a0a1a 0%, #0a0a1a 100%);
        }

        .anime-fullscreen {
            position: absolute;
            width: 100%;
            height: 100%;
            opacity: 0.5;
            background-size: cover;
            background-position: center;
        }

        /* Floating Anime GIFs */
        .floating-anime {
            position: fixed;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 40px rgba(0,0,0,0.6);
            border: 2px solid rgba(255,255,255,0.15);
            z-index: -3;
            opacity: 0.7;
        }

        .floating-anime img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .anime-1 { width: 300px; height: 300px; top: 10%; left: 3%; animation: drift1 20s infinite ease-in-out; }
        .anime-2 { width: 250px; height: 250px; top: 50%; right: 3%; animation: drift2 25s infinite ease-in-out; }
        .anime-3 { width: 200px; height: 200px; bottom: 10%; left: 10%; animation: drift3 18s infinite ease-in-out; }
        .anime-4 { width: 180px; height: 180px; top: 20%; right: 15%; animation: drift4 22s infinite ease-in-out; }

        @keyframes drift1 {
            0%, 100% { transform: translate(0, 0) rotate(-5deg) scale(1); }
            33% { transform: translate(30px, -40px) rotate(5deg) scale(1.05); }
            66% { transform: translate(-20px, 20px) rotate(-3deg) scale(0.95); }
        }

        @keyframes drift2 {
            0%, 100% { transform: translate(0, 0) rotate(5deg) scale(1); }
            50% { transform: translate(-40px, 30px) rotate(-5deg) scale(1.08); }
        }

        @keyframes drift3 {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            25% { transform: translate(25px, -25px) rotate(10deg); }
            75% { transform: translate(-15px, 15px) rotate(-10deg); }
        }

        @keyframes drift4 {
            0%, 100% { transform: translate(0, 0) rotate(3deg) scale(1); }
            50% { transform: translate(20px, 30px) rotate(-3deg) scale(1.1); }
        }

        /* Sakura Petals */
        .petal {
            position: fixed;
            background: linear-gradient(135deg, #ffb6c1, #ffc0cb);
            border-radius: 50% 0 50% 50%;
            opacity: 0.6;
            z-index: -2;
            pointer-events: none;
            animation: fall linear infinite;
        }

        @keyframes fall {
            to {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }

        /* Layer 2: NAME (Behind Profile) */
        .name-layer {
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1;
            pointer-events: none;
        }

        .big-name {
            font-family: 'Inter', sans-serif;
            font-size: 18vw;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: -0.02em;
            line-height: 0.85;
            text-align: center;
            background: linear-gradient(180deg, 
                rgba(255,255,255,0.9) 0%, 
                rgba(0,245,255,0.8) 50%,
                rgba(255,0,170,0.6) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 40px rgba(0,245,255,0.3)) 
                    drop-shadow(0 0 80px rgba(255,0,170,0.2));
            animation: nameGlow 4s ease-in-out infinite alternate;
        }

        @keyframes nameGlow {
            from { 
                filter: drop-shadow(0 0 30px rgba(0,245,255,0.3)) 
                        drop-shadow(0 0 60px rgba(255,0,170,0.2));
                transform: scale(1);
            }
            to { 
                filter: drop-shadow(0 0 60px rgba(0,245,255,0.6)) 
                        drop-shadow(0 0 100px rgba(255,0,170,0.4));
                transform: scale(1.02);
            }
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 1.5rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            backdrop-filter: blur(10px);
            background: rgba(10,10,10,0.8);
            border-bottom: 1px solid rgba(255,255,255,0.1);
        }

        .logo {
            font-size: 1.2rem;
            font-weight: 700;
            letter-spacing: 2px;
            color: white;
            text-decoration: none;
        }

        .nav-controls {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .control-btn {
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.2);
            color: white;
            width: 45px;
            height: 45px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.2rem;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s;
        }

        .control-btn:hover {
            border-color: var(--primary);
            transform: scale(1.1);
        }

        .control-btn.active {
            animation: pulse 2s infinite;
            border-color: var(--secondary);
        }

        @keyframes pulse {
            0%, 100% { box-shadow: 0 0 0 0 rgba(255,0,170,0.7); }
            50% { box-shadow: 0 0 0 10px rgba(255,0,170,0); }
        }

        .visualizer {
            position: absolute;
            bottom: 5px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 2px;
            opacity: 0;
        }

        .control-btn.active .visualizer { opacity: 1; }

        .bar {
            width: 2px;
            height: 10px;
            background: var(--primary);
            animation: dance 0.5s infinite;
        }

        .bar:nth-child(2) { animation-delay: 0.1s; }
        .bar:nth-child(3) { animation-delay: 0.2s; }

        @keyframes dance {
            0%, 100% { height: 4px; }
            50% { height: 12px; }
        }

        .menu-toggle {
            display: none;
            flex-direction: column;
            justify-content: space-around;
            width: 30px;
            height: 25px;
            background: transparent;
            border: none;
            cursor: pointer;
            padding: 0;
        }

        .menu-toggle span {
            width: 100%;
            height: 3px;
            background: white;
            border-radius: 2px;
            transition: all 0.3s;
            display: block;
        }

        .menu-toggle.active span:nth-child(1) {
            transform: rotate(45deg) translate(5px, 5px);
        }

        .menu-toggle.active span:nth-child(2) {
            opacity: 0;
        }

        .menu-toggle.active span:nth-child(3) {
            transform: rotate(-45deg) translate(7px, -6px);
        }

        .nav-links {
            display: flex;
            gap: 2.5rem;
            list-style: none;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            font-size: 0.9rem;
            letter-spacing: 1px;
            text-transform: uppercase;
            position: relative;
            padding: 0.5rem 0;
            transition: color 0.3s;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary);
            transition: width 0.3s;
        }

        .nav-links a:hover {
            color: var(--primary);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            width: 100%;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        /* Layer 3: Profile (In Front) */
        .profile-container {
            position: relative;
            z-index: 10;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .profile-image {
            width: 450px;
            height: 600px;
            position: relative;
            cursor: pointer;
            transition: transform 0.4s;
            filter: drop-shadow(0 30px 60px rgba(0,0,0,0.9));
        }

        .profile-image:hover {
            transform: scale(1.03);
        }

        .profile-image img {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }

        /* Sections */
        section {
            padding: 100px 5%;
            position: relative;
            z-index: 10;
            background: rgba(10,10,10,0.98);
        }

        h2 {
            font-size: 3rem;
            margin-bottom: 3rem;
            text-align: center;
            position: relative;
        }

        h2::after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            border-radius: 2px;
        }

        .section-subtitle {
            color: rgba(255,255,255,0.6);
            text-align: center;
            margin-bottom: 3rem;
            margin-top: 2rem;
        }

        /* About */
        .about-content {
            max-width: 900px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
        }

        .info-block {
            background: rgba(255,255,255,0.03);
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 20px;
            padding: 2rem;
            backdrop-filter: blur(10px);
        }

        .info-block h3 {
            color: var(--primary);
            margin-bottom: 1.5rem;
            font-size: 1.3rem;
        }

        .info-block p, .info-block li {
            color: rgba(255,255,255,0.8);
            line-height: 1.8;
            margin-bottom: 0.8rem;
        }

        .info-block ul {
            list-style: none;
        }

        .info-block li {
            padding-left: 1.5rem;
            position: relative;
        }

        .info-block li::before {
            content: '▹';
            position: absolute;
            left: 0;
            color: var(--secondary);
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .stat-item {
            text-align: center;
            padding: 1.2rem;
            background: rgba(255,255,255,0.03);
            border-radius: 10px;
            border: 1px solid rgba(255,255,255,0.1);
        }

        .stat-number {
            font-size: 2rem;
            font-weight: 900;
            color: var(--primary);
        }

        .stat-label {
            font-size: 0.8rem;
            color: rgba(255,255,255,0.6);
            margin-top: 0.3rem;
        }

        /* Projects */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .project-card {
            background: rgba(255,255,255,0.03);
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 20px;
            padding: 2rem;
            transition: all 0.3s;
            cursor: pointer;
        }

        .project-card:hover {
            transform: translateY(-10px);
            border-color: var(--primary);
            box-shadow: 0 20px 40px rgba(0,245,255,0.2);
        }

        .project-card h3 {
            color: var(--primary);
            margin-bottom: 1rem;
        }

        .tags {
            display: flex;
            gap: 0.5rem;
            margin-top: 1rem;
            flex-wrap: wrap;
        }

        .tag {
            padding: 0.3rem 0.8rem;
            background: rgba(0,245,255,0.1);
            border: 1px solid var(--primary);
            border-radius: 20px;
            font-size: 0.8rem;
            color: var(--primary);
        }

        /* Skills */
        .skills-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            max-width: 1000px;
            margin: 0 auto;
        }

        .skill-item {
            text-align: center;
            padding: 2rem;
            background: rgba(255,255,255,0.03);
            border-radius: 15px;
            border: 1px solid rgba(255,255,255,0.1);
            transition: all 0.3s;
        }

        .skill-item:hover {
            border-color: var(--secondary);
            transform: translateY(-5px);
        }

        .skill-bar {
            width: 100%;
            height: 4px;
            background: rgba(255,255,255,0.1);
            border-radius: 2px;
            margin-top: 1rem;
            overflow: hidden;
        }

        .skill-progress {
            height: 100%;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            width: 0;
            transition: width 1.5s;
        }

        /* Contact */
        .contact-form {
            max-width: 600px;
            margin: 3rem auto;
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .input-group {
            position: relative;
        }

        .input-group input,
        .input-group textarea {
            width: 100%;
            padding: 1rem;
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.2);
            border-radius: 10px;
            color: white;
            outline: none;
            transition: all 0.3s;
        }

        .input-group input:focus,
        .input-group textarea:focus {
            border-color: var(--primary);
            box-shadow: 0 0 20px rgba(0,245,255,0.2);
        }

        .input-group label {
            position: absolute;
            left: 1rem;
            top: 1rem;
            color: rgba(255,255,255,0.5);
            pointer-events: none;
            transition: all 0.3s;
        }

        .input-group input:focus + label,
        .input-group input:not(:placeholder-shown) + label,
        .input-group textarea:focus + label,
        .input-group textarea:not(:placeholder-shown) + label {
            top: -0.5rem;
            left: 0.5rem;
            font-size: 0.8rem;
            color: var(--primary);
            background: #0a0a0a;
            padding: 0 0.5rem;
        }

        button[type="submit"] {
            padding: 1rem 2rem;
            background: transparent;
            border: 2px solid var(--secondary);
            color: var(--secondary);
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s;
        }

        button[type="submit"]:hover {
            background: var(--secondary);
            color: white;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 3rem 5%;
            background: rgba(0,0,0,0.9);
            border-top: 1px solid rgba(255,255,255,0.1);
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .social-links a {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.2);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-decoration: none;
            font-size: 1.5rem;
            transition: all 0.3s;
        }

        .social-links a:hover {
            transform: translateY(-5px) rotate(360deg);
            border-color: var(--secondary);
            color: var(--secondary);
        }

        /* Mobile */
        @media (max-width: 968px) {
            .big-name {
                font-size: 15vw;
            }
            
            .floating-anime {
                display: none;
            }
            
            .profile-image {
                width: 300px;
                height: 400px;
            }

            .about-content {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 768px) {
            .menu-toggle {
                display: flex;
            }

            .nav-links {
                position: fixed;
                top: 0;
                right: -100%;
                width: 70%;
                height: 100vh;
                background: rgba(10,10,10,0.98);
                flex-direction: column;
                padding: 100px 2rem;
                transition: right 0.3s;
                z-index: 999;
            }

            .nav-links.active {
                right: 0;
            }

            .nav-links a {
                font-size: 1.2rem;
            }
        }

        ::-webkit-scrollbar {
            width: 10px;
        }

        ::-webkit-scrollbar-track {
            background: #0a0a0a;
        }

        ::-webkit-scrollbar-thumb {
            background: linear-gradient(var(--primary), var(--secondary));
            border-radius: 5px;
        }
    </style>
</head>
<body>

    <!-- Background Music -->
    <audio id="bg-music" loop>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
    </audio>

    <!-- LAYER 1: Anime Animations (Furthest Back) -->
    <div class="anime-bg">
        <div class="anime-fullscreen" style="background-image: url('https://media.giphy.com/media/3o7aD2saalBwwftBIY/giphy.gif');"></div>
    </div>

    <!-- Floating Anime GIFs -->
    <div class="floating-anime anime-1">
        <img src="https://media.giphy.com/media/SS8gy3qXf2vK8/giphy.gif" alt="anime" onerror="this.style.display='none'">
    </div>
    <div class="floating-anime anime-2">
        <img src="https://media.giphy.com/media/TG4ICZWzJ2HbW/giphy.gif" alt="anime" onerror="this.style.display='none'">
    </div>
    <div class="floating-anime anime-3">
        <img src="https://media.giphy.com/media/5G98t8RGPfqRrhu2RS/giphy.gif" alt="anime" onerror="this.style.display='none'">
    </div>
    <div class="floating-anime anime-4">
        <img src="https://media.giphy.com/media/3oKIPf3C7UPtwbPXIc/giphy.gif" alt="anime" onerror="this.style.display='none'">
    </div>

    <!-- Navigation -->
    <nav>
        <a href="#" class="logo">SEAK CHHENGLY</a>
        
        <div class="nav-controls">
            <button class="control-btn" id="music-toggle" onclick="toggleMusic()" title="Toggle Music">
                <span>🎵</span>
                <div class="visualizer">
                    <div class="bar"></div>
                    <div class="bar"></div>
                    <div class="bar"></div>
                    <div class="bar"></div>
                </div>
            </button>
            
            <button class="menu-toggle" id="menu-toggle" onclick="toggleMenu()">
                <span></span>
                <span></span>
                <span></span>
            </button>
        </div>
        
        <ul class="nav-links" id="navLinks">
            <li><a href="#home" onclick="closeMenu()">Home</a></li>
            <li><a href="#about" onclick="closeMenu()">About</a></li>
            <li><a href="#projects" onclick="closeMenu()">Projects</a></li>
            <li><a href="#skills" onclick="closeMenu()">Skills</a></li>
            <li><a href="#contact" onclick="closeMenu()">Contact</a></li>
        </ul>
    </nav>

    <!-- Hero Section -->
    <section class="hero" id="home">
        
        <!-- LAYER 2: NAME (Behind Profile) -->
        <div class="name-layer">
            <div class="big-name">SEAK<br>CHHENGLY</div>
        </div>

        <!-- LAYER 3: Profile (In Front) -->
        <div class="profile-container">
            <div class="profile-image" onclick="changeImage()" title="Click to change photo">
                <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=800&auto=format&fit=crop&q=80" 
                     alt="Seak Chhengly" 
                     id="hero-image">
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about">
        <h2>About Me</h2>
        <p class="section-subtitle">Get to know me better</p>
        
        <div class="about-content">
            <div class="info-block">
                <h3>👤 Bio</h3>
                <p contenteditable="true" style="outline: none;">
                    Click here to edit your bio. Write something about yourself and your background.
                </p>
                <p contenteditable="true" style="outline: none; margin-top: 1rem;">
                    Add more details about your journey as a developer.
                </p>
                
                <div class="stats-grid">
                    <div class="stat-item">
                        <span class="stat-number" contenteditable="true">5+</span>
                        <div class="stat-label">Years Experience</div>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number" contenteditable="true">50+</span>
                        <div class="stat-label">Projects</div>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number" contenteditable="true">30+</span>
                        <div class="stat-label">Clients</div>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number" contenteditable="true">100%</span>
                        <div class="stat-label">Commitment</div>
                    </div>
                </div>
            </div>

            <div class="info-block">
                <h3>📋 Information</h3>
                <ul>
                    <li contenteditable="true"><strong>Name:</strong> Seak Chhengly</li>
                    <li contenteditable="true"><strong>Location:</strong> Your Location</li>
                    <li contenteditable="true"><strong>Email:</strong> your.email@example.com</li>
                    <li contenteditable="true"><strong>Availability:</strong> Open to work</li>
                </ul>

                <h3 style="margin-top: 1.5rem;">🎯 Services</h3>
                <ul>
                    <li contenteditable="true">Web Development</li>
                    <li contenteditable="true">UI/UX Design</li>
                    <li contenteditable="true">Mobile Apps</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects">
        <h2>Featured Projects</h2>
        <p class="section-subtitle">Selected works</p>
        <div class="projects-grid">
            <div class="project-card" onclick="alert('Edit this project')">
                <h3>Neon Dashboard</h3>
                <p>Cyberpunk analytics interface.</p>
                <div class="tags">
                    <span class="tag">React</span>
                    <span class="tag">Three.js</span>
                </div>
            </div>
            <div class="project-card" onclick="alert('Edit this project')">
                <h3>AI Generator</h3>
                <p>Neural network art tool.</p>
                <div class="tags">
                    <span class="tag">TensorFlow</span>
                    <span class="tag">Vue.js</span>
                </div>
            </div>
            <div class="project-card" onclick="alert('Edit this project')">
                <h3>Crypto Tracker</h3>
                <p>Real-time monitoring app.</p>
                <div class="tags">
                    <span class="tag">Node.js</span>
                    <span class="tag">Socket.io</span>
                </div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills">
        <h2>Skills</h2>
        <p class="section-subtitle">Technologies I use</p>
        <div class="skills-container">
            <div class="skill-item" data-skill="90">
                <h3>JavaScript</h3>
                <div class="skill-bar"><div class="skill-progress"></div></div>
            </div>
            <div class="skill-item" data-skill="85">
                <h3>React/Next.js</h3>
                <div class="skill-bar"><div class="skill-progress"></div></div>
            </div>
            <div class="skill-item" data-skill="80">
                <h3>UI/UX Design</h3>
                <div class="skill-bar"><div class="skill-progress"></div></div>
            </div>
            <div class="skill-item" data-skill="75">
                <h3>Node.js</h3>
                <div class="skill-bar"><div class="skill-progress"></div></div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact">
        <h2>Get In Touch</h2>
        <p class="section-subtitle">Let's work together</p>
        <form class="contact-form" onsubmit="handleSubmit(event)">
            <div class="input-group">
                <input type="text" placeholder=" " required>
                <label>Your Name</label>
            </div>
            <div class="input-group">
                <input type="email" placeholder=" " required>
                <label>Your Email</label>
            </div>
            <div class="input-group">
                <textarea rows="5" placeholder=" " required></textarea>
                <label>Your Message</label>
            </div>
            <button type="submit">Send Message</button>
        </form>
    </section>

    <!-- Footer -->
    <footer>
        <div class="social-links">
            <a href="#">⚡</a>
            <a href="#">💼</a>
            <a href="#">🐦</a>
            <a href="#">✉️</a>
        </div>
        <p>&copy; 2026 Seak Chhengly</p>
    </footer>

    <script>
        // Create falling petals
        function createPetals() {
            for(let i = 0; i < 15; i++) {
                setTimeout(() => {
                    const petal = document.createElement('div');
                    petal.className = 'petal';
                    petal.style.left = Math.random() * 100 + 'vw';
                    petal.style.width = (Math.random() * 12 + 8) + 'px';
                    petal.style.height = (Math.random() * 12 + 8) + 'px';
                    petal.style.animationDuration = (Math.random() * 4 + 6) + 's';
                    petal.style.top = '-50px';
                    document.body.appendChild(petal);
                    setTimeout(() => petal.remove(), 10000);
                }, i * 400);
            }
        }
        createPetals();
        setInterval(createPetals, 8000);

        // Music
        const music = document.getElementById('bg-music');
        const musicBtn = document.getElementById('music-toggle');
        let isPlaying = false;

        function toggleMusic() {
            if(isPlaying) {
                music.pause();
                musicBtn.classList.remove('active');
                isPlaying = false;
            } else {
                music.play().catch(e => console.log('Audio failed'));
                musicBtn.classList.add('active');
                isPlaying = true;
            }
        }

        // Image upload
        function changeImage() {
            const input = document.createElement('input');
            input.type = 'file';
            input.accept = 'image/*';
            input.onchange = function(e) {
                const file = e.target.files[0];
                if(file) {
                    const reader = new FileReader();
                    reader.onload = function(event) {
                        document.getElementById('hero-image').src = event.target.result;
                    };
                    reader.readAsDataURL(file);
                }
            };
            input.click();
        }

        // Menu
        function toggleMenu() {
            document.getElementById('navLinks').classList.toggle('active');
            document.getElementById('menu-toggle').classList.toggle('active');
        }

        function closeMenu() {
            document.getElementById('navLinks').classList.remove('active');
            document.getElementById('menu-toggle').classList.remove('active');
        }

        // Skills animation
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if(entry.isIntersecting) {
                    const progress = entry.target.querySelector('.skill-progress');
                    if(progress) {
                        progress.style.width = entry.target.getAttribute('data-skill') + '%';
                    }
                }
            });
        }, {threshold: 0.1});

        document.querySelectorAll('.skill-item').forEach(item => observer.observe(item));

        // Smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({behavior: 'smooth'});
            });
        });

        // Form
        function handleSubmit(e) {
            e.preventDefault();
            const btn = e.target.querySelector('button');
            btn.textContent = 'Sent!';
            setTimeout(() => {
                btn.textContent = 'Send Message';
                e.target.reset();
            }, 2000);
        }
    </script>
</body>
</html>
