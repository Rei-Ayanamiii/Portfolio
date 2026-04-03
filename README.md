
portfolio_html = '''<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alex Chen | IT Professional & Systems Architect</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #0a0a0f;
            --secondary: #12121a;
            --accent: #00d4aa;
            --accent-glow: rgba(0, 212, 170, 0.3);
            --text-primary: #ffffff;
            --text-secondary: #a0a0b0;
            --gradient-1: linear-gradient(135deg, #00d4aa 0%, #00a8e8 100%);
            --gradient-2: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: var(--primary);
            color: var(--text-primary);
            overflow-x: hidden;
            line-height: 1.6;
        }

        h1, h2, h3, h4 {
            font-family: 'Space Grotesk', sans-serif;
            font-weight: 600;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: var(--secondary);
        }
        ::-webkit-scrollbar-thumb {
            background: var(--accent);
            border-radius: 4px;
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
            background: rgba(10, 10, 15, 0.8);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.3s ease;
        }

        nav.scrolled {
            padding: 1rem 5%;
            background: rgba(10, 10, 15, 0.95);
        }

        .logo {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 1.5rem;
            font-weight: 700;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            cursor: pointer;
            position: relative;
        }

        .logo::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--gradient-1);
            transition: width 0.3s ease;
        }

        .logo:hover::after {
            width: 100%;
        }

        .nav-links {
            display: flex;
            gap: 2.5rem;
            list-style: none;
        }

        .nav-links a {
            color: var(--text-secondary);
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 500;
            position: relative;
            transition: color 0.3s ease;
        }

        .nav-links a::before {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: width 0.3s ease;
        }

        .nav-links a:hover {
            color: var(--text-primary);
        }

        .nav-links a:hover::before {
            width: 100%;
        }

        .mobile-menu {
            display: none;
            flex-direction: column;
            gap: 5px;
            cursor: pointer;
        }

        .mobile-menu span {
            width: 25px;
            height: 2px;
            background: var(--text-primary);
            transition: all 0.3s ease;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            padding: 0 5%;
        }

        .hero-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
        }

        .grid-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(0, 212, 170, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 212, 170, 0.03) 1px, transparent 1px);
            background-size: 50px 50px;
            animation: gridMove 20s linear infinite;
        }

        @keyframes gridMove {
            0% { transform: translate(0, 0); }
            100% { transform: translate(50px, 50px); }
        }

        .glow-orb {
            position: absolute;
            border-radius: 50%;
            filter: blur(80px);
            opacity: 0.4;
            animation: float 10s ease-in-out infinite;
        }

        .glow-orb:nth-child(1) {
            width: 400px;
            height: 400px;
            background: var(--accent);
            top: -100px;
            right: -100px;
            animation-delay: 0s;
        }

        .glow-orb:nth-child(2) {
            width: 300px;
            height: 300px;
            background: #667eea;
            bottom: -50px;
            left: -50px;
            animation-delay: -5s;
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0) scale(1); }
            50% { transform: translate(30px, -30px) scale(1.1); }
        }

        .hero-content {
            position: relative;
            z-index: 1;
            text-align: center;
            max-width: 900px;
        }

        .hero-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.5rem 1rem;
            background: rgba(0, 212, 170, 0.1);
            border: 1px solid rgba(0, 212, 170, 0.3);
            border-radius: 50px;
            font-size: 0.85rem;
            color: var(--accent);
            margin-bottom: 2rem;
            animation: fadeInUp 0.8s ease;
        }

        .status-dot {
            width: 8px;
            height: 8px;
            background: var(--accent);
            border-radius: 50%;
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.5; transform: scale(1.2); }
        }

        .hero h1 {
            font-size: clamp(2.5rem, 6vw, 4.5rem);
            line-height: 1.1;
            margin-bottom: 1.5rem;
            animation: fadeInUp 0.8s ease 0.2s both;
        }

        .hero h1 span {
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero-subtitle {
            font-size: 1.25rem;
            color: var(--text-secondary);
            margin-bottom: 2.5rem;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            animation: fadeInUp 0.8s ease 0.4s both;
        }

        .hero-cta {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
            animation: fadeInUp 0.8s ease 0.6s both;
        }

        .btn {
            padding: 1rem 2rem;
            border-radius: 8px;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s ease;
            cursor: pointer;
            border: none;
            font-size: 0.95rem;
            position: relative;
            overflow: hidden;
        }

        .btn-primary {
            background: var(--gradient-1);
            color: var(--primary);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 30px var(--accent-glow);
        }

        .btn-secondary {
            background: transparent;
            color: var(--text-primary);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .btn-secondary:hover {
            background: rgba(255, 255, 255, 0.05);
            border-color: var(--accent);
            transform: translateY(-2px);
        }

        .scroll-indicator {
            position: absolute;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.5rem;
            color: var(--text-secondary);
            font-size: 0.8rem;
            animation: bounce 2s ease-in-out infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(-10px); }
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

        /* Stats Section */
        .stats {
            padding: 4rem 5%;
            background: var(--secondary);
            border-top: 1px solid rgba(255, 255, 255, 0.05);
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .stat-item {
            text-align: center;
            padding: 1.5rem;
            border-radius: 12px;
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.3s ease;
        }

        .stat-item:hover {
            transform: translateY(-5px);
            border-color: var(--accent);
            background: rgba(0, 212, 170, 0.05);
        }

        .stat-number {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 2.5rem;
            font-weight: 700;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .stat-label {
            color: var(--text-secondary);
            font-size: 0.9rem;
            margin-top: 0.5rem;
        }

        /* About Section */
        .about {
            padding: 8rem 5%;
            position: relative;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-header {
            margin-bottom: 4rem;
        }

        .section-tag {
            display: inline-block;
            padding: 0.25rem 0.75rem;
            background: rgba(0, 212, 170, 0.1);
            color: var(--accent);
            font-size: 0.8rem;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 2px;
            border-radius: 4px;
            margin-bottom: 1rem;
        }

        .section-title {
            font-size: clamp(2rem, 4vw, 3rem);
            margin-bottom: 1rem;
        }

        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .about-text {
            color: var(--text-secondary);
            font-size: 1.1rem;
            line-height: 1.8;
        }

        .about-text p {
            margin-bottom: 1.5rem;
        }

        .about-image {
            position: relative;
        }

        .image-wrapper {
            position: relative;
            border-radius: 20px;
            overflow: hidden;
            background: var(--secondary);
            aspect-ratio: 4/5;
        }

        .image-wrapper::before {
            content: '';
            position: absolute;
            inset: 0;
            background: var(--gradient-1);
            opacity: 0.1;
            z-index: 1;
        }

        .image-wrapper img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            filter: grayscale(20%);
            transition: all 0.5s ease;
        }

        .image-wrapper:hover img {
            filter: grayscale(0%);
            transform: scale(1.05);
        }

        .experience-cards {
            position: absolute;
            bottom: -30px;
            left: -30px;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .exp-card {
            background: var(--primary);
            padding: 1rem 1.5rem;
            border-radius: 12px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
            display: flex;
            align-items: center;
            gap: 1rem;
            animation: slideIn 0.8s ease;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-30px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .exp-icon {
            width: 40px;
            height: 40px;
            background: var(--gradient-1);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
        }

        .exp-content h4 {
            font-size: 0.9rem;
            margin-bottom: 0.2rem;
        }

        .exp-content p {
            font-size: 0.8rem;
            color: var(--text-secondary);
        }

        /* Skills Section */
        .skills {
            padding: 8rem 5%;
            background: var(--secondary);
            position: relative;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .skill-category {
            background: var(--primary);
            padding: 2rem;
            border-radius: 16px;
            border: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.3s ease;
        }

        .skill-category:hover {
            transform: translateY(-5px);
            border-color: var(--accent);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .skill-header {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .skill-icon {
            width: 50px;
            height: 50px;
            background: rgba(0, 212, 170, 0.1);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
        }

        .skill-header h3 {
            font-size: 1.25rem;
        }

        .skill-list {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .skill-item {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .skill-info {
            display: flex;
            justify-content: space-between;
            font-size: 0.9rem;
        }

        .skill-bar {
            height: 6px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 3px;
            overflow: hidden;
        }

        .skill-progress {
            height: 100%;
            background: var(--gradient-1);
            border-radius: 3px;
            width: 0;
            transition: width 1.5s ease;
        }

        /* Projects Section */
        .projects {
            padding: 8rem 5%;
            position: relative;
        }

        .projects-filter {
            display: flex;
            gap: 1rem;
            margin-bottom: 3rem;
            flex-wrap: wrap;
        }

        .filter-btn {
            padding: 0.5rem 1.5rem;
            background: transparent;
            border: 1px solid rgba(255, 255, 255, 0.2);
            color: var(--text-secondary);
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }

        .filter-btn.active,
        .filter-btn:hover {
            background: var(--accent);
            color: var(--primary);
            border-color: var(--accent);
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .project-card {
            background: var(--secondary);
            border-radius: 16px;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.4s ease;
            position: relative;
        }

        .project-card:hover {
            transform: translateY(-10px);
            border-color: var(--accent);
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.4);
        }

        .project-image {
            position: relative;
            height: 220px;
            overflow: hidden;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
        }

        .project-image::before {
            content: '';
            position: absolute;
            inset: 0;
            background: var(--gradient-1);
            opacity: 0;
            transition: opacity 0.3s ease;
            z-index: 1;
        }

        .project-card:hover .project-image::before {
            opacity: 0.2;
        }

        .project-placeholder {
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            opacity: 0.3;
        }

        .project-content {
            padding: 1.5rem;
        }

        .project-tags {
            display: flex;
            gap: 0.5rem;
            margin-bottom: 1rem;
            flex-wrap: wrap;
        }

        .project-tag {
            padding: 0.25rem 0.75rem;
            background: rgba(0, 212, 170, 0.1);
            color: var(--accent);
            font-size: 0.75rem;
            border-radius: 4px;
        }

        .project-content h3 {
            font-size: 1.25rem;
            margin-bottom: 0.75rem;
        }

        .project-content p {
            color: var(--text-secondary);
            font-size: 0.9rem;
            margin-bottom: 1.5rem;
        }

        .project-links {
            display: flex;
            gap: 1rem;
        }

        .project-link {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            color: var(--text-primary);
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 500;
            transition: color 0.3s ease;
        }

        .project-link:hover {
            color: var(--accent);
        }

        /* Contact Section */
        .contact {
            padding: 8rem 5%;
            background: var(--secondary);
            position: relative;
        }

        .contact-wrapper {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            max-width: 1000px;
            margin: 0 auto;
        }

        .contact-info h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        .contact-info p {
            color: var(--text-secondary);
            margin-bottom: 2rem;
        }

        .contact-links {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 1rem;
            background: var(--primary);
            border-radius: 12px;
            border: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.3s ease;
            text-decoration: none;
            color: var(--text-primary);
        }

        .contact-item:hover {
            border-color: var(--accent);
            transform: translateX(5px);
        }

        .contact-icon {
            width: 45px;
            height: 45px;
            background: rgba(0, 212, 170, 0.1);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
        }

        .contact-form {
            background: var(--primary);
            padding: 2rem;
            border-radius: 16px;
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-size: 0.9rem;
            color: var(--text-secondary);
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 1rem;
            background: var(--secondary);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            color: var(--text-primary);
            font-family: inherit;
            font-size: 0.95rem;
            transition: all 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 3px rgba(0, 212, 170, 0.1);
        }

        .form-group textarea {
            min-height: 120px;
            resize: vertical;
        }

        /* Footer */
        footer {
            padding: 3rem 5%;
            background: var(--primary);
            border-top: 1px solid rgba(255, 255, 255, 0.05);
            text-align: center;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .social-link {
            width: 45px;
            height: 45px;
            background: var(--secondary);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-secondary);
            text-decoration: none;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .social-link:hover {
            background: var(--accent);
            color: var(--primary);
            transform: translateY(-3px);
        }

        .footer-text {
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        /* Responsive */
        @media (max-width: 968px) {
            .about-grid,
            .contact-wrapper {
                grid-template-columns: 1fr;
            }

            .experience-cards {
                position: relative;
                bottom: auto;
                left: auto;
                margin-top: 2rem;
            }

            .nav-links {
                display: none;
            }

            .mobile-menu {
                display: flex;
            }
        }

        @media (max-width: 640px) {
            .hero h1 {
                font-size: 2rem;
            }

            .projects-grid {
                grid-template-columns: 1fr;
            }

            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        /* Reveal Animation */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* Particle Canvas */
        #particles {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav id="navbar">
        <div class="logo">AC.</div>
        <ul class="nav-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#skills">Skills</a></li>
            <li><a href="#projects">Projects</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
        <div class="mobile-menu">
            <span></span>
            <span></span>
            <span></span>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-bg">
            <div class="grid-overlay"></div>
            <div class="glow-orb"></div>
            <div class="glow-orb"></div>
            <canvas id="particles"></canvas>
        </div>
        
        <div class="hero-content">
            <div class="hero-badge">
                <span class="status-dot"></span>
                Available for new opportunities
            </div>
            <h1>IT Professional &<br><span>Systems Architect</span></h1>
            <p class="hero-subtitle">
                Building robust infrastructure, securing networks, and optimizing systems 
                for enterprise-scale operations. 8+ years transforming technical challenges into business solutions.
            </p>
            <div class="hero-cta">
                <a href="#projects" class="btn btn-primary">View My Work</a>
                <a href="#contact" class="btn btn-secondary">Get In Touch</a>
            </div>
        </div>

        <div class="scroll-indicator">
            <span>Scroll to explore</span>
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M12 5v14M19 12l-7 7-7-7"/>
            </svg>
        </div>
    </section>

    <!-- Stats Section -->
    <section class="stats">
        <div class="stats-grid">
            <div class="stat-item reveal">
                <div class="stat-number" data-target="8">0</div>
                <div class="stat-label">Years Experience</div>
            </div>
            <div class="stat-item reveal">
                <div class="stat-number" data-target="50">0</div>
                <div class="stat-label">Projects Completed</div>
            </div>
            <div class="stat-item reveal">
                <div class="stat-number" data-target="99">0</div>
                <div class="stat-label">% Uptime Achieved</div>
            </div>
            <div class="stat-item reveal">
                <div class="stat-number" data-target="24">0</div>
                <div class="stat-label">/7 Support Coverage</div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section class="about" id="about">
        <div class="container">
            <div class="section-header reveal">
                <span class="section-tag">About Me</span>
                <h2 class="section-title">Bridging Technology & Business</h2>
            </div>
            
            <div class="about-grid">
                <div class="about-text reveal">
                    <p>
                        I'm Alex Chen, a seasoned IT professional specializing in enterprise infrastructure, 
                        cloud architecture, and cybersecurity. My journey began with a fascination for how 
                        technology powers modern business operations.
                    </p>
                    <p>
                        Today, I lead technical initiatives that drive digital transformation, from designing 
                        fault-tolerant systems to implementing zero-trust security frameworks. I believe in 
                        technology that just works—reliable, scalable, and secure.
                    </p>
                    <p>
                        When I'm not optimizing servers or hunting vulnerabilities, you'll find me exploring 
                        emerging tech, mentoring junior engineers, or speaking at industry conferences about 
                        the future of IT infrastructure.
                    </p>
                    <div style="margin-top: 2rem;">
                        <a href="#contact" class="btn btn-primary">Let's Connect</a>
                    </div>
                </div>

                <div class="about-image reveal">
                    <div class="image-wrapper">
                        <div style="width: 100%; height: 100%; background: linear-gradient(135deg, #1a1a2e 0%, #0f3460 50%, #16213e 100%); display: flex; align-items: center; justify-content: center; font-size: 6rem;">
                            👨‍💻
                        </div>
                    </div>
                    <div class="experience-cards">
                        <div class="exp-card">
                            <div class="exp-icon">🏆</div>
                            <div class="exp-content">
                                <h4>AWS Certified</h4>
                                <p>Solutions Architect Pro</p>
                            </div>
                        </div>
                        <div class="exp-card">
                            <div class="exp-icon">🛡️</div>
                            <div class="exp-content">
                                <h4>CISSP Certified</h4>
                                <p>Information Security</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section class="skills" id="skills">
        <div class="container">
            <div class="section-header reveal">
                <span class="section-tag">Expertise</span>
                <h2 class="section-title">Technical Proficiency</h2>
            </div>

            <div class="skills-grid">
                <div class="skill-category reveal">
                    <div class="skill-header">
                        <div class="skill-icon">☁️</div>
                        <h3>Cloud & Infrastructure</h3>
                    </div>
                    <div class="skill-list">
                        <div class="skill-item">
                            <div class="skill-info">
                                <span>AWS / Azure / GCP</span>
                                <span>95%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" data-width="95"></div>
                            </div>
                        </div>
                        <div class="skill-item">
                            <div class="skill-info">
                                <span>Kubernetes & Docker</span>
                                <span>90%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" data-width="90"></div>
                            </div>
                        </div>
                        <div class="skill-item">
                            <div class="skill-info">
                                <span>Terraform / Ansible</span>
                                <span>88%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" data-width="88"></div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="skill-category reveal">
                    <div class="skill-header">
                        <div class="skill-icon">🔒</div>
                        <h3>Security & Compliance</h3>
                    </div>
                    <div class="skill-list">
                        <div class="skill-item">
                            <div class="skill-info">
                                <span>Cybersecurity Frameworks</span>
                                <span>92%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" data-width="92"></div>
                            </div>
                        </div>
                        <div class="skill-item">
                            <div class="skill-info">
                                <span>SIEM & Threat Detection</span>
                                <span>85%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" data-width="85"></div>
                            </div>
                        </div>
                        <div class="skill-item">
                            <div class="skill-info">
                                <span>Compliance (SOC2, ISO27001)</span>
                                <span>90%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" data-width="90"></div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="skill-category reveal">
                    <div class="skill-header">
                        <div class="skill-icon">🖥️</div>
                        <h3>Systems & Networking</h3>
                    </div>
                    <div class="skill-list">
                        <div class="skill-item">
                            <div class="skill-info">
                                <span>Linux Administration</span>
                                <span>95%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" data-width="95"></div>
                            </div>
                        </div>
                        <div class="skill-item">
                            <div class="skill-info">
                                <span>Network Architecture</span>
                                <span>88%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" data-width="88"></div>
                            </div>
                        </div>
                        <div class="skill-item">
                            <div class="skill-info">
                                <span>Database Management</span>
                                <span>85%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" data-width="85"></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section class="projects" id="projects">
        <div class="container">
            <div class="section-header reveal">
                <span class="section-tag">Portfolio</span>
                <h2 class="section-title">Featured Projects</h2>
            </div>

            <div class="projects-filter reveal">
                <button class="filter-btn active" data-filter="all">All</button>
                <button class="filter-btn" data-filter="infrastructure">Infrastructure</button>
                <button class="filter-btn" data-filter="security">Security</button>
                <button class="filter-btn" data-filter="automation">Automation</button>
            </div>

            <div class="projects-grid">
                <div class="project-card reveal" data-category="infrastructure">
                    <div class="project-image">
                        <div class="project-placeholder">🏗️</div>
                    </div>
                    <div class="project-content">
                        <div class="project-tags">
                            <span class="project-tag">AWS</span>
                            <span class="project-tag">Terraform</span>
                            <span class="project-tag">K8s</span>
                        </div>
                        <h3>Enterprise Cloud Migration</h3>
                        <p>Led migration of 200+ workloads to AWS, implementing IaC with Terraform and establishing multi-region Kubernetes clusters.</p>
                        <div class="project-links">
                            <a href="#" class="project-link">
                                <span>View Details</span>
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                    <path d="M5 12h14M12 5l7 7-7 7"/>
                                </svg>
                            </a>
                        </div>
                    </div>
                </div>

                <div class="project-card reveal" data-category="security">
                    <div class="project-image">
                        <div class="project-placeholder">🛡️</div>
                    </div>
                    <div class="project-content">
                        <div class="project-tags">
                            <span class="project-tag">Security</span>
                            <span class="project-tag">Zero Trust</span>
                            <span class="project-tag">SIEM</span>
                        </div>
                        <h3>Zero Trust Security Framework</h3>
                        <p>Designed and deployed comprehensive zero-trust architecture, reducing security incidents by 80% and achieving SOC2 compliance.</p>
                        <div class="project-links">
                            <a href="#" class="project-link">
                                <span>View Details</span>
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                    <path d="M5 12h14M12 5l7 7-7 7"/>
                                </svg>
                            </a>
                        </div>
                    </div>
                </div>

                <div class="project-card reveal" data-category="automation">
                    <div class="project-image">
                        <div class="project-placeholder">⚙️</div>
                    </div>
                    <div class="project-content">
                        <div class="project-tags">
                            <span class="project-tag">Automation</span>
                            <span class="project-tag">Python</span>
                            <span class="project-tag">Ansible</span>
                        </div>
                        <h3>IT Operations Automation</h3>
                        <p>Built automation platform reducing manual tasks by 70%, including automated patching, monitoring, and incident response workflows.</p>
                        <div class="project-links">
                            <a href="#" class="project-link">
                                <span>View Details</span>
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                    <path d="M5 12h14M12 5l7 7-7 7"/>
                                </svg>
                            </a>
                        </div>
                    </div>
                </div>

                <div class="project-card reveal" data-category="infrastructure">
                    <div class="project-image">
                        <div class="project-placeholder">📊</div>
                    </div>
                    <div class="project-content">
                        <div class="project-tags">
                            <span class="project-tag">Monitoring</span>
                            <span class="project-tag">Observability</span>
                            <span class="project-tag">Grafana</span>
                        </div>
                        <h3>Unified Observability Platform</h3>
                        <p>Implemented centralized monitoring solution with Prometheus, Grafana, and ELK stack, achieving 99.99% uptime visibility.</p>
                        <div class="project-links">
                            <a href="#" class="project-link">
                                <span>View Details</span>
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                    <path d="M5 12h14M12 5l7 7-7 7"/>
                                </svg>
                            </a>
                        </div>
                    </div>
                </div>

                <div class="project-card reveal" data-category="security">
                    <div class="project-image">
                        <div class="project-placeholder">🔐</div>
                    </div>
                    <div class="project-content">
                        <div class="project-tags">
                            <span class="project-tag">IAM</span>
                            <span class="project-tag">SSO</span>
                            <span class="project-tag">Azure AD</span>
                        </div>
                        <h3>Identity Management Overhaul</h3>
                        <p>Migrated legacy IAM to modern SSO solution with MFA, streamlining access for 500+ employees while enhancing security posture.</p>
                        <div class="project-links">
                            <a href="#" class="project-link">
                                <span>View Details</span>
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                    <path d="M5 12h14M12 5l7 7-7 7"/>
                                </svg>
                            </a>
                        </div>
                    </div>
                </div>

                <div class="project-card reveal" data-category="automation">
                    <div class="project-image">
                        <div class="project-placeholder">🤖</div>
                    </div>
                    <div class="project-content">
                        <div class="project-tags">
                            <span class="project-tag">DevOps</span>
                            <span class="project-tag">CI/CD</span>
                            <span class="project-tag">GitOps</span>
                        </div>
                        <h3>GitOps CI/CD Pipeline</h3>
                        <p>Architected GitOps-based deployment pipeline with ArgoCD, reducing deployment time from hours to minutes with full audit trails.</p>
                        <div class="project-links">
                            <a href="#" class="project-link">
                                <span>View Details</span>
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                    <path d="M5 12h14M12 5l7 7-7 7"/>
                                </svg>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="contact" id="contact">
        <div class="container">
            <div class="section-header reveal">
                <span class="section-tag">Contact</span>
                <h2 class="section-title">Let's Work Together</h2>
            </div>

            <div class="contact-wrapper">
                <div class="contact-info reveal">
                    <h3>Ready to transform your IT infrastructure?</h3>
                    <p>I'm always interested in hearing about new projects and opportunities. Whether you need cloud architecture, security hardening, or automation solutions, let's discuss how I can help.</p>
                    
                    <div class="contact-links">
                        <a href="mailto:alex.chen@email.com" class="contact-item">
                            <div class="contact-icon">📧</div>
                            <div>
                                <div style="font-weight: 600;">Email</div>
                                <div style="font-size: 0.85rem; color: var(--text-secondary);">alex.chen@email.com</div>
                            </div>
                        </a>
                        <a href="#" class="contact-item">
                            <div class="contact-icon">💼</div>
                            <div>
                                <div style="font-weight: 600;">LinkedIn</div>
                                <div style="font-size: 0.85rem; color: var(--text-secondary);">linkedin.com/in/alexchen</div>
                            </div>
                        </a>
                        <a href="#" class="contact-item">
                            <div class="contact-icon">🐙</div>
                            <div>
                                <div style="font-weight: 600;">GitHub</div>
                                <div style="font-size: 0.85rem; color: var(--text-secondary);">github.com/alexchen</div>
                            </div>
                        </a>
                    </div>
                </div>

                <form class="contact-form reveal" onsubmit="event.preventDefault(); alert('Message sent! (Demo)');">
                    <div class="form-group">
                        <label for="name">Name</label>
                        <input type="text" id="name" placeholder="John Doe" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input type="email" id="email" placeholder="john@company.com" required>
                    </div>
                    <div class="form-group">
                        <label for="subject">Subject</label>
                        <input type="text" id="subject" placeholder="Project Inquiry" required>
                    </div>
                    <div class="form-group">
                        <label for="message">Message</label>
                        <textarea id="message" placeholder="Tell me about your project..." required></textarea>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">Send Message</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="social-links">
                <a href="#" class="social-link" title="LinkedIn">💼</a>
                <a href="#" class="social-link" title="GitHub">🐙</a>
                <a href="#" class="social-link" title="Twitter">🐦</a>
                <a href="#" class="social-link" title="Email">📧</a>
            </div>
            <p class="footer-text">© 2026 Alex Chen. Crafted with precision.</p>
        </div>
    </footer>

    <script>
        // Navigation scroll effect
        const navbar = document.getElementById('navbar');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // Reveal animations on scroll
        const revealElements = document.querySelectorAll('.reveal');
        const revealObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('active');
                }
            });
        }, { threshold: 0.1 });

        revealElements.forEach(el => revealObserver.observe(el));

        // Skill bars animation
        const skillBars = document.querySelectorAll('.skill-progress');
        const skillObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    const width = entry.target.getAttribute('data-width');
                    entry.target.style.width = width + '%';
                }
            });
        }, { threshold: 0.5 });

        skillBars.forEach(bar => skillObserver.observe(bar));

        // Counter animation
        const counters = document.querySelectorAll('.stat-number');
        const counterObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    const target = parseInt(entry.target.getAttribute('data-target'));
                    const duration = 2000;
                    const increment = target / (duration / 16);
                    let current = 0;
                    
                    const updateCounter = () => {
                        current += increment;
                        if (current < target) {
                            entry.target.textContent = Math.floor(current);
                            requestAnimationFrame(updateCounter);
                        } else {
                            entry.target.textContent = target + (entry.target.parentElement.querySelector('.stat-label').textContent.includes('%') ? '%' : '+');
                        }
                    };
                    
                    updateCounter();
                    counterObserver.unobserve(entry.target);
                }
            });
        }, { threshold: 0.5 });

        counters.forEach(counter => counterObserver.observe(counter));

        // Project filtering
        const filterBtns = document.querySelectorAll('.filter-btn');
        const projectCards = document.querySelectorAll('.project-card');

        filterBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                filterBtns.forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                
                const filter = btn.getAttribute('data-filter');
                
                projectCards.forEach(card => {
                    if (filter === 'all' || card.getAttribute('data-category') === filter) {
                        card.style.display = 'block';
                        setTimeout(() => {
                            card.style.opacity = '1';
                            card.style.transform = 'translateY(0)';
                        }, 10);
                    } else {
                        card.style.opacity = '0';
                        card.style.transform = 'translateY(20px)';
                        setTimeout(() => {
                            card.style.display = 'none';
                        }, 300);
                    }
                });
            });
        });

        // Particle animation
        const canvas = document.getElementById('particles');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }

        resizeCanvas();
        window.addEventListener('resize', resizeCanvas);

        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 2 + 0.5;
                this.speedX = Math.random() * 1 - 0.5;
                this.speedY = Math.random() * 1 - 0.5;
                this.opacity = Math.random() * 0.5 + 0.2;
            }

            update() {
                this.x += this.speedX;
                this.y += this.speedY;

                if (this.x > canvas.width) this.x = 0;
                if (this.x < 0) this.x = canvas.width;
                if (this.y > canvas.height) this.y = 0;
                if (this.y < 0) this.y = canvas.height;
            }

            draw() {
                ctx.fillStyle = `rgba(0, 212, 170, ${this.opacity})`;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        function initParticles() {
            particles = [];
            for (let i = 0; i < 50; i++) {
                particles.push(new Particle());
            }
        }

        function animateParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            particles.forEach(particle => {
                particle.update();
                particle.draw();
            });

            // Draw connections
            particles.forEach((a, index) => {
                particles.slice(index + 1).forEach(b => {
                    const dx = a.x - b.x;
                    const dy = a.y - b.y;
                    const distance = Math.sqrt(dx * dx + dy * dy);

                    if (distance < 150) {
                        ctx.strokeStyle = `rgba(0, 212, 170, ${0.1 * (1 - distance / 150)})`;
                        ctx.lineWidth = 1;
                        ctx.beginPath();
                        ctx.moveTo(a.x, a.y);
                        ctx.lineTo(b.x, b.y);
                        ctx.stroke();
                    }
                });
            });

            requestAnimationFrame(animateParticles);
        }

        initParticles();
        animateParticles();

        // Smooth scroll for navigation
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
    </script>
</body>
</html>'''

# Save the portfolio
with open('/mnt/kimi/output/portfolio.html', 'w', encoding='utf-8') as f:
    f.write(portfolio_html)

print("Portfolio created successfully!")
print("\nFeatures included:")
print("✨ Modern dark theme with teal/cyan accent colors")
print("🎨 Animated gradient backgrounds and floating orbs")
print("📊 Interactive particle network animation in hero section")
print("🔢 Animated counters and skill bars")
print("🖼️ Project filtering system")
print("✨ Scroll-triggered reveal animations")
print("📱 Fully responsive design")
print("🎯 Smooth scrolling navigation")
print("🌊 Hover effects and micro-interactions")
