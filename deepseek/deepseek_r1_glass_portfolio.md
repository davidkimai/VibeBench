

<img width="1910" height="1153" alt="image" src="https://github.com/user-attachments/assets/157da9f8-9a30-4739-b294-f4e99dc718dc" />

# Prompt
## Create a visually stunning interactive personal portfolio website using glassmorphism and neon gradients.

# DeepSeek

# Interactive Glassmorphism Portfolio with Neon Gradients

I'll create a stunning interactive portfolio website featuring glassmorphism design and neon gradients. This modern design combines frosted glass elements with vibrant neon accents for a futuristic look.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Neon Glass Portfolio</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
            min-height: 100vh;
            overflow-x: hidden;
            color: #fff;
            position: relative;
            padding-bottom: 50px;
        }

        /* Neon glow effect */
        body::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(101, 78, 163, 0.2) 0%, transparent 60%);
            animation: rotate 20s linear infinite;
            z-index: -1;
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        /* Glassmorphism effect */
        .glass {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
            padding: 30px;
            transition: all 0.3s ease;
        }

        .glass:hover {
            box-shadow: 0 8px 32px rgba(106, 27, 154, 0.4);
            transform: translateY(-5px);
        }

        /* Neon gradient text */
        .neon-text {
            background: linear-gradient(90deg, #ff00cc, #3333ff, #00ccff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-size: 200% auto;
            animation: gradient 3s linear infinite;
        }

        @keyframes gradient {
            0% { background-position: 0% 50%; }
            100% { background-position: 200% 50%; }
        }

        /* Navigation */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 5%;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            font-size: 28px;
            font-weight: 800;
        }

        .nav-links {
            display: flex;
            gap: 30px;
        }

        .nav-links a {
            color: #fff;
            text-decoration: none;
            font-weight: 500;
            position: relative;
            padding: 5px 0;
            transition: all 0.3s ease;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, #ff00cc, #3333ff);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Hero Section */
        .hero {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 80px 10%;
            min-height: 80vh;
        }

        .hero-content {
            max-width: 600px;
        }

        .hero h1 {
            font-size: 60px;
            margin-bottom: 20px;
            line-height: 1.2;
        }

        .hero p {
            font-size: 20px;
            margin-bottom: 30px;
            opacity: 0.9;
        }

        .hero-img {
            position: relative;
            width: 400px;
            height: 400px;
            border-radius: 50%;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, rgba(255,0,204,0.3), rgba(51,51,255,0.3), rgba(0,204,255,0.3));
        }

        .hero-img::before {
            content: '';
            position: absolute;
            width: 380px;
            height: 380px;
            background: url('https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80') center/cover;
            border-radius: 50%;
        }

        /* Buttons */
        .btn {
            display: inline-block;
            padding: 15px 40px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
            font-size: 18px;
            margin-right: 15px;
            margin-top: 10px;
        }

        .btn-primary {
            background: linear-gradient(90deg, #ff00cc, #3333ff);
            color: white;
            box-shadow: 0 5px 15px rgba(106, 27, 154, 0.4);
        }

        .btn-secondary {
            background: transparent;
            color: white;
            border: 2px solid rgba(255, 255, 255, 0.3);
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(106, 27, 154, 0.6);
        }

        /* Sections */
        section {
            padding: 80px 10%;
        }

        .section-title {
            font-size: 40px;
            margin-bottom: 50px;
            text-align: center;
        }

        /* Skills */
        .skills-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 30px;
        }

        .skill-card {
            text-align: center;
            padding: 40px 20px;
        }

        .skill-card i {
            font-size: 50px;
            margin-bottom: 20px;
            background: linear-gradient(90deg, #ff00cc, #3333ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .skill-card h3 {
            font-size: 24px;
            margin-bottom: 15px;
        }

        /* Projects */
        .projects-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 30px;
        }

        .project-card {
            overflow: hidden;
            position: relative;
            height: 400px;
        }

        .project-img {
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, #ff00cc, #3333ff, #00ccff);
            background-size: 200% 200%;
            animation: gradient 5s ease infinite;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-size: 24px;
            font-weight: bold;
        }

        .project-info {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            padding: 25px;
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(10px);
            transform: translateY(100px);
            transition: transform 0.5s ease;
        }

        .project-card:hover .project-info {
            transform: translateY(0);
        }

        /* Contact */
        .contact-container {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 40px;
        }

        .contact-form input,
        .contact-form textarea {
            width: 100%;
            padding: 15px;
            margin-bottom: 20px;
            border: none;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 16px;
        }

        .contact-form textarea {
            height: 150px;
            resize: none;
        }

        .contact-info {
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .contact-item {
            display: flex;
            align-items: center;
            margin-bottom: 25px;
        }

        .contact-item i {
            font-size: 24px;
            width: 60px;
            height: 60px;
            background: linear-gradient(90deg, #ff00cc, #3333ff);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-right: 20px;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 30px;
            margin-top: 50px;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 20px;
        }

        .social-links a {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 20px;
            transition: all 0.3s ease;
        }

        .social-links a:hover {
            background: linear-gradient(90deg, #ff00cc, #3333ff);
            transform: translateY(-5px);
        }

        /* Responsive */
        @media (max-width: 992px) {
            .hero {
                flex-direction: column;
                text-align: center;
                padding-top: 40px;
            }
            
            .hero-content {
                margin-bottom: 50px;
            }
            
            .contact-container {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }
            
            .hero h1 {
                font-size: 40px;
            }
            
            .hero-img {
                width: 300px;
                height: 300px;
            }
            
            .hero-img::before {
                width: 280px;
                height: 280px;
            }
            
            .projects-container {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="glass">
        <div class="logo neon-text">DEV<span style="color: white;">PORTFOLIO</span></div>
        <div class="nav-links">
            <a href="#home">Home</a>
            <a href="#about">About</a>
            <a href="#skills">Skills</a>
            <a href="#projects">Projects</a>
            <a href="#contact">Contact</a>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-content">
            <h1>Hi, I'm <span class="neon-text">Alex Morgan</span></h1>
            <h2 class="neon-text">Creative Frontend Developer</h2>
            <p>I create immersive digital experiences with cutting-edge web technologies. Specializing in modern UI/UX design with a focus on interactive animations and responsive layouts.</p>
            <div class="hero-btns">
                <a href="#projects" class="btn btn-primary">View My Work</a>
                <a href="#contact" class="btn btn-secondary">Get In Touch</a>
            </div>
        </div>
        <div class="hero-img"></div>
    </section>

    <!-- About Section -->
    <section id="about">
        <h2 class="section-title neon-text">About Me</h2>
        <div class="glass" style="padding: 50px;">
            <p style="font-size: 20px; line-height: 1.8; margin-bottom: 30px;">
                I'm a passionate frontend developer with 5+ years of experience creating beautiful and functional web applications. My expertise lies in creating immersive user experiences with modern JavaScript frameworks, CSS animations, and responsive design principles.
            </p>
            <p style="font-size: 20px; line-height: 1.8;">
                When I'm not coding, you can find me exploring new design trends, contributing to open-source projects, or experimenting with creative coding. I believe in continuous learning and staying at the forefront of web technology.
            </p>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills">
        <h2 class="section-title neon-text">My Skills</h2>
        <div class="skills-container">
            <div class="skill-card glass">
                <i class="fab fa-html5"></i>
                <h3>HTML5 & CSS3</h3>
                <p>Semantic markup, responsive design, CSS animations, Flexbox, Grid</p>
            </div>
            <div class="skill-card glass">
                <i class="fab fa-js"></i>
                <h3>JavaScript</h3>
                <p>ES6+, React, Vue, Angular, DOM manipulation, API integration</p>
            </div>
            <div class="skill-card glass">
                <i class="fas fa-paint-brush"></i>
                <h3>UI/UX Design</h3>
                <p>Figma, Adobe XD, prototyping, user research, accessibility</p>
            </div>
            <div class="skill-card glass">
                <i class="fas fa-mobile-alt"></i>
                <h3>Responsive Design</h3>
                <p>Mobile-first approach, cross-browser compatibility, performance optimization</p>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects">
        <h2 class="section-title neon-text">Featured Projects</h2>
        <div class="projects-container">
            <div class="project-card glass">
                <div class="project-img">Neon Dashboard</div>
                <div class="project-info">
                    <h3>Neon Dashboard</h3>
                    <p>A modern analytics dashboard with real-time data visualization and interactive charts.</p>
                </div>
            </div>
            <div class="project-card glass">
                <div class="project-img">Glassmorphism App</div>
                <div class="project-info">
                    <h3>Glassmorphism App</h3>
                    <p>Weather application with glassmorphism UI design and animated transitions.</p>
                </div>
            </div>
            <div class="project-card glass">
                <div class="project-img">E-commerce Platform</div>
                <div class="project-info">
                    <h3>E-commerce Platform</h3>
                    <p>Full-featured online store with cart functionality and payment integration.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact">
        <h2 class="section-title neon-text">Get In Touch</h2>
        <div class="contact-container">
            <div class="glass contact-form">
                <form>
                    <input type="text" placeholder="Your Name" required>
                    <input type="email" placeholder="Your Email" required>
                    <input type="text" placeholder="Subject">
                    <textarea placeholder="Your Message" required></textarea>
                    <button type="submit" class="btn btn-primary">Send Message</button>
                </form>
            </div>
            <div class="glass contact-info">
                <div class="contact-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <div>
                        <h3>Location</h3>
                        <p>San Francisco, CA</p>
                    </div>
                </div>
                <div class="contact-item">
                    <i class="fas fa-envelope"></i>
                    <div>
                        <h3>Email</h3>
                        <p>hello@alexmorgan.dev</p>
                    </div>
                </div>
                <div class="contact-item">
                    <i class="fas fa-phone"></i>
                    <div>
                        <h3>Phone</h3>
                        <p>+1 (555) 123-4567</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="social-links">
            <a href="#"><i class="fab fa-github"></i></a>
            <a href="#"><i class="fab fa-linkedin-in"></i></a>
            <a href="#"><i class="fab fa-twitter"></i></a>
            <a href="#"><i class="fab fa-dribbble"></i></a>
        </div>
        <p>© 2023 Alex Morgan. All rights reserved.</p>
    </footer>

    <script>
        // Add smooth scrolling to navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Add scroll animation to elements
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('show');
                }
            });
        }, {
            threshold: 0.1
        });

        document.querySelectorAll('.glass').forEach((el) => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(30px)';
            el.style.transition = 'opacity 0.6s ease-out, transform 0.6s ease-out';
            
            observer.observe(el);
            
            el.addEventListener('transitionend', () => {
                el.classList.add('show');
            });
        });

        document.querySelectorAll('.show').forEach((el) => {
            el.style.opacity = '1';
            el.style.transform = 'translateY(0)';
        });
    </script>
</body>
</html>
```

## Key Features of This Portfolio Design:

1. **Glassmorphism Design**:
   - Frosted glass effect with backdrop blur
   - Subtle borders and shadows for depth
   - Smooth hover animations

2. **Neon Gradients**:
   - Animated gradient text effects
   - Vibrant gradient accents on buttons and icons
   - Subtle background gradients with animation

3. **Interactive Elements**:
   - Smooth scrolling navigation
   - Animated project cards with hover effects
   - Form with interactive inputs
   - Social media links with hover animations

4. **Responsive Design**:
   - Works on all device sizes
   - Mobile-friendly navigation
   - Flexible grid layouts

5. **Modern UI Components**:
   - Glassmorphism cards for content sections
   - Animated skill icons with gradient effects
   - Project showcase with hidden details on hover

The design uses a dark gradient background with animated radial gradients to create depth and visual interest. The glassmorphism effect is applied consistently throughout the interface, creating a cohesive and modern aesthetic. Neon accents are used strategically to draw attention to important elements without overwhelming the design.

Simply copy and paste the code into an HTML file and open it in any modern browser to see the full interactive experience!
