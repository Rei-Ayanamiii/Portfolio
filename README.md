
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
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html, body {
            height: 100%;
            width: 100%;
            overflow-x: hidden;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: #0a0a0f;
            color: #ffffff;
            line-height: 1.6;
        }

        h1, h2, h3, h4 {
            font-family: 'Space Grotesk', sans-serif;
            font-weight: 600;
        }

        /* Full Screen Sections */
        section {
            min-height: 100vh;
            width: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        /* Animated Background Canvas */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            pointer-events: none;
        }

        /* Gradient Overlay */
        .gradient-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(ellipse at 20% 20%, rgba(0, 212, 170, 0.15) 0%, transparent 50%),
                radial-gradient(ellipse at 80% 80%, rgba(102, 126, 234, 0.15) 0%, transparent 50%),
                radial-gradient(ellipse at 50% 50%, rgba(0, 168, 232, 0.05) 0%, transparent 70%);
            z-index: 1;
            pointer-events: none;
            animation: gradientShift 15s ease-in-out infinite;
        }

        @keyframes gradientShift {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }

        /* Floating Orbs */
        .orb {
            position: fixed;
            border-radius: 50%;
            filter: blur(60px);
            z-index: 1;
            pointer-events: none;
        }

        .orb-1 {
            width: 600px;
            height: 600px;
            background: rgba(0, 212, 170, 0.3);
            top: -200px;
            right: -200px;
            animation: float1 20s ease-in-out infinite;
        }

        .orb-2 {
            width: 500px;
            height: 500px;
            background: rgba(102, 126, 234, 0.3);
            bottom: -150px;
            left: -150px;
            animation: float2 25s ease-in-out infinite;
        }

        .orb-3 {
            width: 400px;
            height: 400px;
            background: rgba(0, 168, 232, 0.2);
            top: 50%;
            left: 50%;
            animation: float3 18s ease-in-out infinite;
        }

        @keyframes float1 {
            0%, 100% { transform: translate(0, 0) scale(1); }
            33% { transform: translate(50px, 50px) scale(1.1); }
            66% { transform: translate(-30px, 20px) scale(0.9); }
        }

        @keyframes float2 {
            0%, 100% { transform: translate(0, 0) scale(1); }
            50% { transform: translate(-40px, -60px) scale(1.2); }
        }

        @keyframes float3 {
            0%, 100% { transform: translate(-50%, -50%) rotate(0deg); }
            50% { transform: translate(-50%, -50%) rotate(180deg) scale(1.3); }
        }

        /* Grid Lines */
        .grid-lines {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(0, 212, 170, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 212, 170, 0.03) 1px, transparent 1px);
            background-size: 100px 100px;
            z-index: 1;
            pointer-events: none;
            animation: gridScroll 20s linear infinite;
        }

        @keyframes gridScroll {
            0% { transform: translate(0, 0); }
            100% { transform: translate(100px, 100px); }
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
            background: rgba(10, 10, 15, 0.6);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.3s ease;
        }

        nav.scrolled {
            padding: 1rem 5%;
            background: rgba(10, 10, 15, 0.9);
        }

        .logo {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 1.5rem;
            font-weight: 700;
            background: linear-gradient(135deg, #00d4aa 0%, #00a8e8 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            cursor: pointer;
        }

        .nav-links {
            display: flex;
            gap: 2.5rem;
            list-style: none;
        }

        .nav-links a {
            color: #a0a0b0;
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
            background: #00d4aa;
            transition: width 0.3s ease;
        }

        .nav-links a:hover {
            color: #ffffff;
        }

        .nav-links a:hover::before {
            width: 100%;
        }

        /* Content Wrapper */
        .content-wrapper {
            position: relative;
            z-index: 10;
            width: 100%;
        }

        /* Hero Section */
        .hero {
            z-index: 10;
        }

        .hero-content {
            text-align: center;
            max-width: 900px;
            padding: 0 5%;
            animation: fadeInUp 1s ease;
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
            color: #00d4aa;
            margin-bottom: 2rem;
            animation: fadeInUp 0.8s ease;
        }

        .status-dot {
            width: 8px;
            height: 8px;
            background: #00d4aa;
            border-radius: 50%;
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.5; transform: scale(1.2); }
        }

        .hero h1 {
            font-size: clamp(3rem, 8vw, 5rem);
            line-height: 1.1;
            margin-bottom: 1.5rem;
            animation: fadeInUp 0.8s ease 0.2s both;
        }

        .hero h1 span {
            background: linear-gradient(135deg, #00d4aa 0%, #00a8e8 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-subtitle {
            font-size: 1.25rem;
            color: #a0a0b0;
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
            background: linear-gradient(135deg, #00d4aa 0%, #00a8e8 100%);
            color: #0a0a0f;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(0, 212, 170, 0.3);
        }

        .btn-secondary {
            background: transparent;
            color: #ffffff;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .btn-secondary:hover {
            background: rgba(255, 255, 255, 0.05);
            border-color: #00d4aa;
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
            color: #a0a0b0;
            font-size: 0.8rem;
            animation: bounce 2s ease-in-out infinite;
            z-index: 10;
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

        /* About Section */
        .about {
            background: rgba(18, 18, 26, 0.8);
            backdrop-filter: blur(10px);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 5%;
            width: 100%;
        }

        .section-header {
            margin-bottom: 4rem;
            text-align: center;
        }

        .section-tag {
            display: inline-block;
            padding: 0.25rem 0.75rem;
            background: rgba(0, 212, 170, 0.1);
            color: #00d4aa;
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
            color: #a0a0b0;
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
            background: #12121a;
            aspect-ratio: 4/5;
            border: 1px solid rgba(0, 212, 170, 0.2);
        }

        .image-wrapper > div {
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #1a1a2e 0%, #0f3460 50%, #16213e 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 6rem;
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
            background: #0a0a0f;
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
            background: linear-gradient(135deg, #00d4aa 0%, #00a8e8 100%);
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
            color: #a0a0b0;
        }

        /* Skills Section */
        .skills {
            background: rgba(10, 10, 15, 0.9);
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .skill-category {
            background: rgba(18, 18, 26, 0.8);
            padding: 2rem;
            border-radius: 16px;
            border: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }

        .skill-category:hover {
            transform: translateY(-5px);
            border-color: #00d4aa;
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
            background: linear-gradient(135deg, #00d4aa 0%, #00a8e8 100%);
            border-radius: 3px;
            width: 0;
            transition: width 1.5s ease;
        }

        /* Projects Section */
        .projects {
            background: rgba(18, 18, 26, 0.8);
            backdrop-filter: blur(10px);
        }

        .projects-filter {
            display: flex;
            gap: 1rem;
            margin-bottom: 3rem;
            flex-wrap: wrap;
            justify-content: center;
        }

        .filter-btn {
            padding: 0.5rem 1.5rem;
            background: transparent;
            border: 1px solid rgba(255, 255, 255, 0.2);
            color: #a0a0b0;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }

        .filter-btn.active,
        .filter-btn:hover {
            background: #00d4aa;
            color: #0a0a0f;
            border-color: #00d4aa;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .project-card {
            background: rgba(10, 10, 15, 0.8);
            border-radius: 16px;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.4s ease;
            backdrop-filter: blur(10px);
        }

        .project-card:hover {
            transform: translateY(-10px);
            border-color: #00d4aa;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.4);
        }

        .project-image {
            position: relative;
            height: 220px;
            overflow: hidden;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
        }

        .project-placeholder {
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            opacity: 0.5;
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
            color: #00d4aa;
            font-size: 0.75rem;
            border-radius: 4px;
        }

        .project-content h3 {
            font-size: 1.25rem;
            margin-bottom: 0.75rem;
        }

        .project-content p {
            color: #a0a0b0;
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
            color: #ffffff;
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 500;
            transition: color 0.3s ease;
        }

        .project-link:hover {
            color: #00d4aa;
        }

        /* Contact Section */
        .contact {
            background: rgba(10, 10, 15, 0.9);
        }

        .contact-wrapper {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            max-width: 1000px;
            margin: 0 auto;
            width: 100%;
        }

        .contact-info h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        .contact-info p {
            color: #a0a0b0;
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
            background: rgba(18, 18, 26, 0.8);
            border-radius: 12px;
            border: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.3s ease;
            text-decoration: none;
            color: #ffffff;
        }

        .contact-item:hover {
            border-color: #00d4aa;
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
            background: rgba(18, 18, 26, 0.8);
            padding: 2rem;
            border-radius: 16px;
            border: 1px solid rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-size: 0.9rem;
            color: #a0a0b0;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 1rem;
            background: rgba(10, 10, 15, 0.5);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            color: #ffffff;
            font-family: inherit;
            font-size: 0.95rem;
            transition: all 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #00d4aa;
            box-shadow: 0 0 0 3px rgba(0, 212, 170, 0.1);
        }

        .form-group textarea {
            min-height: 120px;
            resize: vertical;
        }

        /* Footer */
        footer {
            padding: 3rem 5%;
            background: rgba(10, 10, 15, 0.95);
            border-top: 1px solid rgba(255, 255, 255, 0.05);
            text-align: center;
            position: relative;
            z-index: 10;
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
            background: rgba(18, 18, 26, 0.8);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #a0a0b0;
            text-decoration: none;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .social-link:hover {
            background: #00d4aa;
            color: #0a0a0f;
            transform: translateY(-3px);
        }

        .footer-text {
            color: #a0a0b0;
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

            .projects-grid {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 640px) {
            .hero h1 {
                font-size: 2.5rem;
            }

            section {
                padding: 4rem 0;
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
    </style>
</head>
<body>
    <!-- Background Elements -->
    <canvas id="bg-canvas"></canvas>
    <div class="gradient-overlay"></div>
    <div class="grid-lines"></div>
    <div class="orb orb-1"></div>
    <div class="orb orb-2"></div>
    <div class="orb orb-3"></div>

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
    </nav>

    <div class="content-wrapper">
        <!-- Hero Section -->
        <section class="hero" id="home">
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
                            <div>👨‍💻</div>
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
                                    <div style="font-size: 0.85rem; color: #a0a0b0;">alex.chen@email.com</div>
                                </div>
                            </a>
                            <a href="#" class="contact-item">
                                <div class="contact-icon">💼</div>
                                <div>
                                    <div style="font-weight: 600;">LinkedIn</div>
                                    <div style="font-size: 0.85rem; color: #a0a0b0;">linkedin.com/in/alexchen</div>
                                </div>
                            </a>
                            <a href="#" class="contact-item">
                                <div class="contact-icon">🐙</div>
                                <div>
                                    <div style="font-weight: 600;">GitHub</div>
                                    <div style="font-size: 0.85rem; color: #a0a0b0;">github.com/alexchen</div>
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
    </div>

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

        // Enhanced Background Animation
        const canvas = document.getElementById('bg-canvas');
        const ctx = canvas.getContext('2d');
        let particles = [];
        let animationId;
        let mouse = { x: null, y: null };

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }

        resizeCanvas();
        window.addEventListener('resize', resizeCanvas);

        // Track mouse movement
        window.addEventListener('mousemove', (e) => {
            mouse.x = e.x;
            mouse.y = e.y;
        });

        window.addEventListener('mouseleave', () => {
            mouse.x = null;
            mouse.y = null;
        });

        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 3 + 1;
                this.speedX = Math.random() * 2 - 1;
                this.speedY = Math.random() * 2 - 1;
                this.opacity = Math.random() * 0.5 + 0.2;
                this.color = Math.random() > 0.5 ? '0, 212, 170' : '102, 126, 234';
            }

            update() {
                this.x += this.speedX;
                this.y += this.speedY;

                // Bounce off edges
                if (this.x > canvas.width || this.x < 0) this.speedX *= -1;
                if (this.y > canvas.height || this.y < 0) this.speedY *= -1;

                // Mouse interaction
                if (mouse.x != null && mouse.y != null) {
                    let dx = mouse.x - this.x;
                    let dy = mouse.y - this.y;
                    let distance = Math.sqrt(dx * dx + dy * dy);
                    
                    if (distance < 150) {
                        const forceDirectionX = dx / distance;
                        const forceDirectionY = dy / distance;
                        const force = (150 - distance) / 150;
                        const directionX = forceDirectionX * force * 0.5;
                        const directionY = forceDirectionY * force * 0.5;
                        
                        this.speedX -= directionX;
                        this.speedY -= directionY;
                    }
                }

                // Speed limit
                const maxSpeed = 2;
                const currentSpeed = Math.sqrt(this.speedX * this.speedX + this.speedY * this.speedY);
                if (currentSpeed > maxSpeed) {
                    this.speedX = (this.speedX / currentSpeed) * maxSpeed;
                    this.speedY = (this.speedY / currentSpeed) * maxSpeed;
                }
            }

            draw() {
                ctx.fillStyle = `rgba(${this.color}, ${this.opacity})`;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();

                // Glow effect
                ctx.shadowBlur = 15;
                ctx.shadowColor = `rgba(${this.color}, 0.5)`;
            }
        }

        function initParticles() {
            particles = [];
            const particleCount = Math.min(100, (canvas.width * canvas.height) / 15000);
            for (let i = 0; i < particleCount; i++) {
                particles.push(new Particle());
            }
        }

        function animateParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.shadowBlur = 0;

            // Update and draw particles
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

                    if (distance < 200) {
                        const opacity = 0.15 * (1 - distance / 200);
                        ctx.strokeStyle = `rgba(0, 212, 170, ${opacity})`;
                        ctx.lineWidth = 1;
                        ctx.beginPath();
                        ctx.moveTo(a.x, a.y);
                        ctx.lineTo(b.x, b.y);
                        ctx.stroke();
                    }
                });
            });

            // Draw mouse connections
            if (mouse.x != null && mouse.y != null) {
                particles.forEach(particle => {
                    const dx = mouse.x - particle.x;
                    const dy = mouse.y - particle.y;
                    const distance = Math.sqrt(dx * dx + dy * dy);

                    if (distance < 250) {
                        const opacity = 0.3 * (1 - distance / 250);
                        ctx.strokeStyle = `rgba(0, 212, 170, ${opacity})`;
                        ctx.lineWidth = 1.5;
                        ctx.beginPath();
                        ctx.moveTo(mouse.x, mouse.y);
                        ctx.lineTo(particle.x, particle.y);
                        ctx.stroke();
                    }
                });
            }

            animationId = requestAnimationFrame(animateParticles);
        }

        initParticles();
        animateParticles();

        // Pause animation when tab is hidden
        document.addEventListener('visibilitychange', () => {
            if (document.hidden) {
                cancelAnimationFrame(animationId);
            } else {
                animateParticles();
            }
        });
    </script>
</body>
</html>'''

# Save the fullscreen portfolio
with open('/mnt/kimi/output/portfolio.html', 'w', encoding='utf-8') as f:
    f.write(portfolio_html)

print("✅ Fullscreen portfolio created!")
print("\n🎨 Background Animation Features:")
print("• Interactive particle network (100 particles)")
print("• Mouse-following connections")
print("• Floating gradient orbs (3 large blurred circles)")
print("• Animated grid lines scrolling diagonally")
print("• Dynamic gradient overlay shifting opacity")
print("• Particles bounce off edges and react to mouse")
print("• Connection lines between nearby particles")
print("• Performance optimized with requestAnimationFrame")
print("• Animation pauses when tab is inactive")
print("\n📐 Full Screen Features:")
print("• Every section is min-height: 100vh")
print("• Content always centered vertically and horizontally")
print("• Background elements fixed and cover entire viewport")
print("• Smooth scrolling between fullscreen sections")
