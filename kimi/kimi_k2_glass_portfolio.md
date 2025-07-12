# [Chat Log](https://www.kimi.com/share/d1pbq48lrq4v66bl94qg)

<img width="1902" height="1146" alt="image" src="https://github.com/user-attachments/assets/5a631efb-719b-4be8-9026-9cf854c64d6c" />

# Prompt: Create a visually stunning interactive personal portfolio website using glassmorphism and neon gradients.

# Kimi: 
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>John Doe | Cybernetic Portfolio</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* Base Styles */
        :root {
            --primary-neon: #00f5ff;
            --secondary-neon: #ff00e5;
            --tertiary-neon: #7b2cbf;
            --dark-bg: #0a0a0a;
            --glass-bg: rgba(255, 255, 255, 0.05);
            --glass-border: rgba(255, 255, 255, 0.1);
            --text-primary: #ffffff;
            --text-secondary: #b3b3b3;
            --accent: #00f5ff;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: var(--dark-bg);
            background-image: 
                radial-gradient(circle at 20% 50%, rgba(0, 245, 255, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(255, 0, 229, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 40% 20%, rgba(123, 44, 191, 0.1) 0%, transparent 50%);
            color: var(--text-primary);
            line-height: 1.6;
            overflow-x: hidden;
            min-height: 100vh;
        }

        /* Animated Background */
        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            overflow: hidden;
        }

        .bg-animation span {
            position: absolute;
            display: block;
            width: 20px;
            height: 20px;
            background: rgba(255, 255, 255, 0.05);
            animation: move 25s linear infinite;
            bottom: -150px;
            border-radius: 50%;
            backdrop-filter: blur(5px);
            box-shadow: 0 0 10px rgba(0, 245, 255, 0.3),
                        inset 0 0 10px rgba(0, 245, 255, 0.2);
        }

        .bg-animation span:nth-child(1) {
            left: 25%;
            width: 80px;
            height: 80px;
            animation-delay: 0s;
            background: rgba(0, 245, 255, 0.1);
        }

        .bg-animation span:nth-child(2) {
            left: 10%;
            width: 20px;
            height: 20px;
            animation-delay: 2s;
            animation-duration: 12s;
            background: rgba(255, 0, 229, 0.1);
        }

        .bg-animation span:nth-child(3) {
            left: 70%;
            width: 20px;
            height: 20px;
            animation-delay: 4s;
            background: rgba(123, 44, 191, 0.1);
        }

        .bg-animation span:nth-child(4) {
            left: 40%;
            width: 60px;
            height: 60px;
            animation-delay: 0s;
            animation-duration: 18s;
            background: rgba(0, 245, 255, 0.1);
        }

        .bg-animation span:nth-child(5) {
            left: 65%;
            width: 20px;
            height: 20px;
            animation-delay: 0s;
            background: rgba(255, 0, 229, 0.1);
        }

        .bg-animation span:nth-child(6) {
            left: 75%;
            width: 110px;
            height: 110px;
            animation-delay: 3s;
            background: rgba(123, 44, 191, 0.1);
        }

        .bg-animation span:nth-child(7) {
            left: 35%;
            width: 150px;
            height: 150px;
            animation-delay: 7s;
            background: rgba(0, 245, 255, 0.1);
        }

        .bg-animation span:nth-child(8) {
            left: 50%;
            width: 25px;
            height: 25px;
            animation-delay: 15s;
            animation-duration: 45s;
            background: rgba(255, 0, 229, 0.1);
        }

        .bg-animation span:nth-child(9) {
            left: 20%;
            width: 15px;
            height: 15px;
            animation-delay: 2s;
            animation-duration: 35s;
            background: rgba(123, 44, 191, 0.1);
        }

        .bg-animation span:nth-child(10) {
            left: 85%;
            width: 150px;
            height: 150px;
            animation-delay: 0s;
            animation-duration: 11s;
            background: rgba(0, 245, 255, 0.1);
        }

        @keyframes move {
            0% {
                transform: translateY(0) rotate(0deg);
                opacity: 1;
                border-radius: 0;
            }
            100% {
                transform: translateY(-1000px) rotate(720deg);
                opacity: 0;
                border-radius: 50%;
            }
        }

        /* Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }

        ::-webkit-scrollbar-track {
            background: rgba(0, 0, 0, 0.2);
        }

        ::-webkit-scrollbar-thumb {
            background: linear-gradient(180deg, var(--primary-neon), var(--secondary-neon));
            border-radius: 10px;
        }

        /* Header */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            padding: 20px 40px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            transition: 0.5s;
            backdrop-filter: blur(10px);
            background: rgba(0, 0, 0, 0.2);
            border-bottom: 1px solid var(--glass-border);
        }

        header.sticky {
            padding: 10px 40px;
            background: rgba(0, 0, 0, 0.8);
            border-bottom: 1px solid var(--glass-border);
        }

        .logo {
            font-size: 2em;
            font-weight: 700;
            background: linear-gradient(90deg, var(--primary-neon), var(--secondary-neon));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 10px rgba(0, 245, 255, 0.5);
            cursor: pointer;
        }

        .navigation {
            display: flex;
            gap: 30px;
        }

        .navigation li {
            list-style: none;
        }

        .navigation a {
            color: var(--text-primary);
            text-decoration: none;
            font-weight: 600;
            font-size: 1.1em;
            transition: 0.3s;
            position: relative;
            padding: 5px 10px;
            border-radius: 5px;
            overflow: hidden;
        }

        .navigation a:hover {
            color: var(--primary-neon);
        }

        .navigation a::before {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, var(--primary-neon), var(--secondary-neon));
            transition: width 0.3s;
        }

        .navigation a:hover::before {
            width: 100%;
        }

        /* Main Content */
        main {
            padding-top: 80px;
            width: 100%;
            max-width: 1400px;
            margin: 0 auto;
            padding-left: 40px;
            padding-right: 40px;
        }

        /* Section Styles */
        section {
            padding: 100px 0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .section-title {
            font-size: 2.5em;
            margin-bottom: 40px;
            text-align: center;
            background: linear-gradient(90deg, var(--primary-neon), var(--secondary-neon));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: linear-gradient(90deg, var(--primary-neon), var(--secondary-neon));
            border-radius: 5px;
        }

        /* Hero Section */
        .hero {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 50px;
            padding: 50px 0;
        }

        .hero-content {
            flex: 1;
            max-width: 600px;
        }

        .hero-image {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
        }

        .hero-image img {
            max-width: 400px;
            border-radius: 20px;
            box-shadow: 0 0 30px rgba(0, 245, 255, 0.3);
            transition: transform 0.3s;
            animation: float 6s ease-in-out infinite;
        }

        .hero-image img:hover {
            transform: scale(1.05);
        }

        @keyframes float {
            0% {
                transform: translateY(0px);
            }
            50% {
                transform: translateY(-20px);
            }
            100% {
                transform: translateY(0px);
            }
        }

        .hero-title {
            font-size: 3.5em;
            margin-bottom: 10px;
            line-height: 1.2;
        }

        .hero-subtitle {
            font-size: 2em;
            margin-bottom: 20px;
            background: linear-gradient(90deg, var(--primary-neon), var(--secondary-neon));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-description {
            font-size: 1.2em;
            color: var(--text-secondary);
            margin-bottom: 30px;
            line-height: 1.8;
        }

        .cta-buttons {
            display: flex;
            gap: 20px;
        }

        .btn {
            padding: 15px 30px;
            border-radius: 50px;
            font-weight: 600;
            font-size: 1.1em;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            display: inline-block;
            text-align: center;
        }

        .btn-primary {
            background: linear-gradient(90deg, var(--primary-neon), var(--secondary-neon));
            color: #000;
            border: none;
            box-shadow: 0 0 20px rgba(0, 245, 255, 0.5);
        }

        .btn-primary:hover {
            transform: translateY(-5px);
            box-shadow: 0 0 30px rgba(0, 245, 255, 0.8);
        }

        .btn-secondary {
            background: transparent;
            color: var(--text-primary);
            border: 2px solid var(--primary-neon);
            box-shadow: 0 0 10px rgba(0, 245, 255, 0.3);
        }

        .btn-secondary:hover {
            background: rgba(0, 245, 255, 0.1);
            transform: translateY(-5px);
            box-shadow: 0 0 20px rgba(0, 245, 255, 0.5);
        }

        /* About Section */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
            align-items: center;
        }

        .about-text {
            background: var(--glass-bg);
            backdrop-filter: blur(10px);
            border: 1px solid var(--glass-border);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .about-text p {
            margin-bottom: 15px;
            color: var(--text-secondary);
            line-height: 1.8;
        }

        .skills {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 20px;
        }

        .skill-tag {
            padding: 8px 15px;
            background: rgba(0, 245, 255, 0.1);
            border: 1px solid rgba(0, 245, 255, 0.3);
            border-radius: 50px;
            font-size: 0.9em;
            color: var(--primary-neon);
            transition: all 0.3s;
        }

        .skill-tag:hover {
            background: rgba(0, 245, 255, 0.2);
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 245, 255, 0.3);
        }

        .about-image {
            position: relative;
        }

        .about-image img {
            width: 100%;
            border-radius: 20px;
            box-shadow: 0 0 30px rgba(0, 245, 255, 0.3);
        }

        .about-image::before {
            content: '';
            position: absolute;
            top: -20px;
            left: -20px;
            width: 100%;
            height: 100%;
            border: 2px solid var(--primary-neon);
            border-radius: 20px;
            z-index: -1;
            opacity: 0.5;
        }

        /* Projects Section */
        .projects-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 30px;
        }

        .project-card {
            background: var(--glass-bg);
            backdrop-filter: blur(10px);
            border: 1px solid var(--glass-border);
            border-radius: 20px;
            overflow: hidden;
            transition: all 0.3s;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 35px rgba(0, 245, 255, 0.2);
            border-color: rgba(0, 245, 255, 0.3);
        }

        .project-image {
            height: 200px;
            overflow: hidden;
        }

        .project-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s;
        }

        .project-card:hover .project-image img {
            transform: scale(1.1);
        }

        .project-content {
            padding: 25px;
        }

        .project-title {
            font-size: 1.5em;
            margin-bottom: 10px;
            color: var(--text-primary);
        }

        .project-description {
            color: var(--text-secondary);
            margin-bottom: 15px;
            line-height: 1.6;
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
        }

        .project-tech span {
            padding: 5px 10px;
            background: rgba(0, 245, 255, 0.1);
            border-radius: 5px;
            font-size: 0.8em;
            color: var(--primary-neon);
        }

        .project-links {
            display: flex;
            gap: 15px;
        }

        .project-link {
            color: var(--text-primary);
            font-size: 1.2em;
            transition: all 0.3s;
        }

        .project-link:hover {
            color: var(--primary-neon);
            transform: translateY(-3px);
        }

        /* Contact Section */
        .contact-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
            align-items: center;
        }

        .contact-info {
            background: var(--glass-bg);
            backdrop-filter: blur(10px);
            border: 1px solid var(--glass-border);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .contact-info h3 {
            font-size: 1.8em;
            margin-bottom: 20px;
            color: var(--text-primary);
        }

        .contact-info p {
            color: var(--text-secondary);
            margin-bottom: 30px;
            line-height: 1.8;
        }

        .contact-details {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .contact-item i {
            font-size: 1.5em;
            color: var(--primary-neon);
        }

        .contact-item span {
            color: var(--text-secondary);
        }

        .contact-form {
            background: var(--glass-bg);
            backdrop-filter: blur(10px);
            border: 1px solid var(--glass-border);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: var(--text-primary);
        }

        .form-control {
            width: 100%;
            padding: 15px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--glass-border);
            border-radius: 10px;
            color: var(--text-primary);
            font-size: 1em;
            transition: all 0.3s;
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary-neon);
            box-shadow: 0 0 10px rgba(0, 245, 255, 0.3);
        }

        textarea.form-control {
            resize: vertical;
            min-height: 120px;
        }

        /* Footer */
        footer {
            background: rgba(0, 0, 0, 0.8);
            padding: 40px 0;
            text-align: center;
            border-top: 1px solid var(--glass-border);
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 20px;
        }

        .social-link {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 50px;
            height: 50px;
            background: var(--glass-bg);
            border: 1px solid var(--glass-border);
            border-radius: 50%;
            color: var(--text-primary);
            font-size: 1.5em;
            transition: all 0.3s;
        }

        .social-link:hover {
            transform: translateY(-5px);
            color: var(--primary-neon);
            border-color: var(--primary-neon);
            box-shadow: 0 0 20px rgba(0, 245, 255, 0.5);
        }

        .copyright {
            color: var(--text-secondary);
            font-size: 0.9em;
        }

        /* Responsive Styles */
        @media (max-width: 992px) {
            .hero {
                flex-direction: column;
                text-align: center;
            }

            .about-content,
            .contact-container {
                grid-template-columns: 1fr;
            }

            .hero-image img {
                max-width: 300px;
            }
        }

        @media (max-width: 768px) {
            header {
                padding: 15px 20px;
            }

            header.sticky {
                padding: 10px 20px;
            }

            main {
                padding-left: 20px;
                padding-right: 20px;
            }

            .navigation {
                display: none;
            }

            .hero-title {
                font-size: 2.5em;
            }

            .hero-subtitle {
                font-size: 1.5em;
            }

            .section-title {
                font-size: 2em;
            }

            .projects-container {
                grid-template-columns: 1fr;
            }
        }

        /* Mobile Menu */
        .mobile-menu-toggle {
            display: none;
            font-size: 1.5em;
            color: var(--text-primary);
            cursor: pointer;
        }

        @media (max-width: 768px) {
            .mobile-menu-toggle {
                display: block;
            }
        }

        /* Neon cursor effect */
        .cursor {
            position: fixed;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(0, 245, 255, 0.8), transparent);
            pointer-events: none;
            transform: translate(-50%, -50%);
            z-index: 9999;
            mix-blend-mode: difference;
            transition: width 0.2s, height 0.2s;
        }

        .cursor-follower {
            position: fixed;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(0, 245, 255, 0.1);
            border: 1px solid rgba(0, 245, 255, 0.5);
            pointer-events: none;
            transform: translate(-50%, -50%);
            z-index: 9998;
            transition: all 0.1s ease-out;
        }

        /* Loading animation */
        .loading {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--dark-bg);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 10000;
            transition: opacity 0.5s, visibility 0.5s;
        }

        .loading.hidden {
            opacity: 0;
            visibility: hidden;
        }

        .loading-spinner {
            width: 100px;
            height: 100px;
            border: 5px solid rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            border-top-color: var(--primary-neon);
            animation: spin 1s ease-in-out infinite;
        }

        @keyframes spin {
            to {
                transform: rotate(360deg);
            }
        }

        /* Scroll reveal animation */
        .reveal {
            opacity: 0;
            transform: translateY(50px);
            transition: all 0.8s ease;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <!-- Loading Screen -->
    <div class="loading">
        <div class="loading-spinner"></div>
    </div>

    <!-- Cursor Effects -->
    <div class="cursor"></div>
    <div class="cursor-follower"></div>

    <!-- Background Animation -->
    <div class="bg-animation">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
    </div>

    <!-- Header -->
    <header>
        <div class="logo">JD</div>
        <ul class="navigation">
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#projects">Projects</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
        <div class="mobile-menu-toggle">
            <i class="fas fa-bars"></i>
        </div>
    </header>

    <!-- Main Content -->
    <main>
        <!-- Hero Section -->
        <section id="home">
            <div class="hero">
                <div class="hero-content">
                    <h1 class="hero-title reveal">Hi, I'm <span style="color: var(--primary-neon);">John Doe</span></h1>
                    <h2 class="hero-subtitle reveal">Full Stack Developer & UI/UX Designer</h2>
                    <p class="hero-description reveal">
                        I create stunning digital experiences that combine cutting-edge technology with beautiful design.
                        Passionate about crafting user-centric solutions that solve real-world problems.
                    </p>
                    <div class="cta-buttons reveal">
                        <a href="#contact" class="btn btn-primary">Hire Me</a>
                        <a href="#projects" class="btn btn-secondary">View My Work</a>
                    </div>
                </div>
                <div class="hero-image reveal">
                    <img src="https://via.placeholder.com/400x500" alt="John Doe">
                </div>
            </div>
        </section>

        <!-- About Section -->
        <section id="about">
            <h2 class="section-title reveal">About Me</h2>
            <div class="about-content">
                <div class="about-text reveal">
                    <p>
                        I'm a passionate full-stack developer with 5+ years of experience creating digital solutions for clients across various industries. My expertise spans from front-end technologies like React and Vue to back-end frameworks like Node.js and Django.
                    </p>
                    <p>
                        What sets me apart is my ability to combine technical excellence with a keen eye for design. I believe that great software should not only function flawlessly but also provide an exceptional user experience.
                    </p>
                    <p>
                        When I'm not coding, you can find me exploring new technologies, contributing to open-source projects, or sharing my knowledge through blog posts and tech talks.
                    </p>
                    <div class="skills">
                        <span class="skill-tag">JavaScript</span>
                        <span class="skill-tag">React</span>
                        <span class="skill-tag">Node.js</span>
                        <span class="skill-tag">Python</span>
                        <span class="skill-tag">UI/UX Design</span>
                        <span class="skill-tag">MongoDB</span>
                        <span class="skill-tag">AWS</span>
                        <span class="skill-tag">Docker</span>
                    </div>
                </div>
                <div class="about-image reveal">
                    <img src="https://via.placeholder.com/500x500" alt="About John Doe">
                </div>
            </div>
        </section>

        <!-- Projects Section -->
        <section id="projects">
            <h2 class="section-title reveal">My Projects</h2>
            <div class="projects-container">
                <!-- Project 1 -->
                <div class="project-card reveal">
                    <div class="project-image">
                        <img src="https://via.placeholder.com/600x400" alt="Project 1">
                    </div>
                    <div class="project-content">
                        <h3 class="project-title">E-commerce Platform</h3>
                        <p class="project-description">
                            A full-featured e-commerce platform with real-time inventory management, secure payment processing, and AI-powered recommendations.
                        </p>
                        <div class="project-tech">
                            <span>React</span>
                            <span>Node.js</span>
                            <span>MongoDB</span>
                            <span>Stripe API</span>
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link" title="View Live"><i class="fas fa-external-link-alt"></i></a>
                            <a href="#" class="project-link" title="View Code"><i class="fab fa-github"></i></a>
                        </div>
                    </div>
                </div>

                <!-- Project 2 -->
                <div class="project-card reveal">
                    <div class="project-image">
                        <img src="https://via.placeholder.com/600x400" alt="Project 2">
                    </div>
                    <div class="project-content">
                        <h3 class="project-title">Task Management App</h3>
                        <p class="project-description">
                            A collaborative task management application with real-time updates, team chat, and advanced project analytics.
                        </p>
                        <div class="project-tech">
                            <span>Vue.js</span>
                            <span>Firebase</span>
                            <span>Chart.js</span>
                            <span>PWA</span>
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link" title="View Live"><i class="fas fa-external-link-alt"></i></a>
                            <a href="#" class="project-link" title="View Code"><i class="fab fa-github"></i></a>
                        </div>
                    </div>
                </div>

                <!-- Project 3 -->
                <div class="project-card reveal">
                    <div class="project-image">
                        <img src="https://via.placeholder.com/600x400" alt="Project 3">
                    </div>
                    <div class="project-content">
                        <h3 class="project-title">Health & Fitness Tracker</h3>
                        <p class="project-description">
                            A comprehensive health tracking application with workout planning, nutrition tracking, and AI-powered health insights.
                        </p>
                        <div class="project-tech">
                            <span>React Native</span>
                            <span>Express</span>
                            <span>PostgreSQL</span>
                            <span>TensorFlow.js</span>
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link" title="View Live"><i class="fas fa-external-link-alt"></i></a>
                            <a href="#" class="project-link" title="View Code"><i class="fab fa-github"></i></a>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact">
            <h2 class="section-title reveal">Get In Touch</h2>
            <div class="contact-container">
                <div class="contact-info reveal">
                    <h3>Let's Talk About Your Project</h3>
                    <p>
                        Whether you have a project in mind, need a consultation, or just want to say hello, I'd love to hear from you. Fill out the form and I'll get back to you as soon as possible.
                    </p>
                    <div class="contact-details">
                        <div class="contact-item">
                            <i class="fas fa-envelope"></i>
                            <span>hello@johndoe.dev</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-phone"></i>
                            <span>+1 (555) 123-4567</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-map-marker-alt"></i>
                            <span>San Francisco, CA</span>
                        </div>
                    </div>
                </div>
                <div class="contact-form reveal">
                    <form id="contactForm">
                        <div class="form-group">
                            <label for="name">Name</label>
                            <input type="text" id="name" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="email">Email</label>
                            <input type="email" id="email" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="subject">Subject</label>
                            <input type="text" id="subject" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="message">Message</label>
                            <textarea id="message" class="form-control" required></textarea>
                        </div>
                        <button type="submit" class="btn btn-primary" style="width: 100%;">Send Message</button>
                    </form>
                </div>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer>
        <div class="social-links">
            <a href="#" class="social-link"><i class="fab fa-github"></i></a>
            <a href="#" class="social-link"><i class="fab fa-linkedin-in"></i></a>
            <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
            <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
        </div>
        <p class="copyright">&copy; 2023 John Doe. All Rights Reserved.</p>
    </footer>

    <script>
        // Loading Screen
        window.addEventListener('load', function() {
            setTimeout(() => {
                document.querySelector('.loading').classList.add('hidden');
            }, 1000);
        });

        // Sticky Header
        window.addEventListener('scroll', function() {
            const header = document.querySelector('header');
            header.classList.toggle('sticky', window.scrollY > 0);
        });

        // Smooth Scrolling for Navigation
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                const targetSection = document.querySelector(targetId);
                
                if (targetSection) {
                    targetSection.scrollIntoView({
                        behavior: 'smooth'
                    });
                }
            });
        });

        // Scroll Reveal Animation
        function revealElements() {
            const reveals = document.querySelectorAll('.reveal');
            
            reveals.forEach(element => {
                const windowHeight = window.innerHeight;
                const elementTop = element.getBoundingClientRect().top;
                const elementVisible = 150;
                
                if (elementTop < windowHeight - elementVisible) {
                    element.classList.add('active');
                }
            });
        }

        window.addEventListener('scroll', revealElements);
        window.addEventListener('load', revealElements);

        // Custom Cursor
        const cursor = document.querySelector('.cursor');
        const cursorFollower = document.querySelector('.cursor-follower');

        document.addEventListener('mousemove', (e) => {
            cursor.style.left = `${e.clientX}px`;
            cursor.style.top = `${e.clientY}px`;
            
            setTimeout(() => {
                cursorFollower.style.left = `${e.clientX}px`;
                cursorFollower.style.top = `${e.clientY}px`;
            }, 100);
        });

        // Cursor hover effects
        document.querySelectorAll('a, button, .project-card').forEach(element => {
            element.addEventListener('mouseenter', () => {
                cursor.style.width = '30px';
                cursor.style.height = '30px';
                cursorFollower.style.width = '60px';
                cursorFollower.style.height = '60px';
            });
            
            element.addEventListener('mouseleave', () => {
                cursor.style.width = '20px';
                cursor.style.height = '20px';
                cursorFollower.style.width = '40px';
                cursorFollower.style.height = '40px';
            });
        });

        // Form Submission
        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const subject = document.getElementById('subject').value;
            const message = document.getElementById('message').value;
            
            // Here you would normally send the data to your server
            // For demonstration, we'll just show an alert
            alert(`Thank you for your message, ${name}! I'll get back to you soon.`);
            
            // Reset the form
            this.reset();
        });

        // Parallax Effect for Background Elements
        window.addEventListener('scroll', function() {
            const scrollY = window.scrollY;
            
            document.querySelectorAll('.bg-animation span').forEach((span, index) => {
                const speed = 0.1 + (index * 0.05);
                span.style.transform = `translateY(${scrollY * speed}px) rotate(${scrollY * 0.1}deg)`;
            });
        });

        // Interactive Skills Tags
        document.querySelectorAll('.skill-tag').forEach(tag => {
            tag.addEventListener('click', function() {
                // Create ripple effect
                const ripple = document.createElement('span');
                ripple.style.position = 'absolute';
                ripple.style.width = '100%';
                ripple.style.height = '100%';
                ripple.style.top = '0';
                ripple.style.left = '0';
                ripple.style.background = 'radial-gradient(circle, rgba(0,245,255,0.4) 0%, transparent 70%)';
                ripple.style.borderRadius = '50px';
                ripple.style.transform = 'scale(0)';
                ripple.style.animation = 'ripple 0.6s linear';
                ripple.style.pointerEvents = 'none';
                
                this.style.position = 'relative';
                this.appendChild(ripple);
                
                setTimeout(() => {
                    ripple.remove();
                }, 600);
            });
        });

        // Add ripple animation
        const style = document.createElement('style');
        style.textContent = `
            @keyframes ripple {
                to {
                    transform: scale(2);
                    opacity: 0;
                }
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>

```
