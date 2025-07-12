# [Chat Log](https://chatgpt.com/share/6872f5c0-f9f0-8004-8bbc-738d83045e55)
# [Interactive Artifact](https://chatgpt.com/canvas/shared/6872f584447c819193ba45faee172ef2)

<img width="1909" height="1154" alt="image" src="https://github.com/user-attachments/assets/5b86e43a-7dd5-4213-a2ea-f8ecf436a81b" />

# Prompt

## Create a visually stunning interactive personal portfolio website using glassmorphism and neon gradients.

# ChatGPT
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My Neon Glass Portfolio</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --neon-gradient: linear-gradient(45deg, #ff00ff, #00ffff, #ff00ff);
      --glass-bg: rgba(255, 255, 255, 0.1);
      --glass-border: rgba(255, 255, 255, 0.25);
    }
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }
    html {
      scroll-behavior: smooth;
    }
    body {
      min-height: 100vh;
      background: radial-gradient(circle at 25% 25%, #111 0%, #000 60%);
      overflow-x: hidden;
      color: #fff;
    }
    /* Neon animated backdrop */
    body::before {
      content: "";
      position: fixed;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: var(--neon-gradient);
      animation: rotate 15s linear infinite;
      filter: blur(120px);
      opacity: 0.4;
      z-index: -2;
    }
    @keyframes rotate {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }
    /* Navigation */
    nav {
      position: fixed;
      width: 100%;
      top: 0;
      left: 0;
      display: flex;
      justify-content: center;
      padding: 1rem 0;
      z-index: 1000;
    }
    nav ul {
      list-style: none;
      display: flex;
      gap: 2rem;
      padding: 0 2rem;
      background: var(--glass-bg);
      border: 1px solid var(--glass-border);
      backdrop-filter: blur(10px);
      border-radius: 50px;
    }
    nav a {
      color: #fff;
      text-decoration: none;
      font-weight: 600;
      position: relative;
    }
    nav a::after {
      content: "";
      position: absolute;
      left: 0;
      bottom: -4px;
      width: 100%;
      height: 2px;
      background: var(--neon-gradient);
      opacity: 0;
      transition: opacity 0.3s;
    }
    nav a.active::after, nav a:hover::after {
      opacity: 1;
    }

    /* Sections */
    section {
      min-height: 100vh;
      padding: 100px 8%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      position: relative;
    }
    .glass {
      width: 100%;
      max-width: 1100px;
      background: var(--glass-bg);
      border: 1px solid var(--glass-border);
      backdrop-filter: blur(12px);
      border-radius: 20px;
      padding: 3rem 4rem;
      margin: 1rem 0;
      position: relative;
      overflow: hidden;
    }
    .glass::before {
      content: "";
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: var(--neon-gradient);
      animation: rotate 20s linear reverse infinite;
      filter: blur(80px);
      opacity: 0.35;
      z-index: -1;
    }

    h1, h2, h3 {
      text-align: center;
      margin-bottom: 1rem;
    }

    /* Hero */
    #home .glass {
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
    }
    #home h1 {
      font-size: 3rem;
    }
    #home p {
      margin-top: 1rem;
      font-size: 1.2rem;
      max-width: 800px;
    }

    /* Projects */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 2rem;
      margin-top: 2rem;
      width: 100%;
    }
    .project-card {
      perspective: 800px;
    }
    .project-inner {
      background: var(--glass-bg);
      border: 1px solid var(--glass-border);
      backdrop-filter: blur(10px);
      border-radius: 15px;
      padding: 1.5rem;
      transition: transform 0.4s ease;
    }
    .project-inner h3 {
      margin-bottom: 0.5rem;
    }
    .project-inner p {
      font-size: 0.9rem;
      opacity: 0.8;
    }

    /* Contact */
    form {
      width: 100%;
      max-width: 600px;
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }
    input, textarea {
      background: var(--glass-bg);
      border: 1px solid var(--glass-border);
      backdrop-filter: blur(6px);
      border-radius: 8px;
      padding: 0.8rem 1rem;
      color: #fff;
      resize: none;
      font-size: 1rem;
    }
    button {
      padding: 0.8rem 1rem;
      border: none;
      border-radius: 50px;
      font-weight: 600;
      background: var(--neon-gradient);
      cursor: pointer;
      transition: opacity 0.3s;
    }
    button:hover { opacity: 0.8; }

    /* Responsive */
    @media (max-width: 600px) {
      #home h1 { font-size: 2.2rem; }
      nav ul { gap: 1rem; }
    }
  </style>
</head>
<body>
  <nav>
    <ul>
      <li><a href="#home" class="nav-link active">Home</a></li>
      <li><a href="#about" class="nav-link">About</a></li>
      <li><a href="#projects" class="nav-link">Projects</a></li>
      <li><a href="#contact" class="nav-link">Contact</a></li>
    </ul>
  </nav>

  <!-- Hero Section -->
  <section id="home">
    <div class="glass">
      <h1>Hello, I'm <span style="background: var(--neon-gradient); -webkit-background-clip: text; color: transparent;">Your Name</span></h1>
      <p>Creative developer & designer crafting immersive digital experiences with cutting‑edge technologies and a touch of neon magic.</p>
    </div>
  </section>

  <!-- About Section -->
  <section id="about">
    <div class="glass">
      <h2>About Me</h2>
      <p>
        I'm a multidisciplinary developer passionate about blending art with code. I specialize in creating interactive, visually engaging web applications that push boundaries and delight users.
      </p>
    </div>
  </section>

  <!-- Projects Section -->
  <section id="projects">
    <div class="glass">
      <h2>Projects</h2>
      <div class="projects-grid">
        <div class="project-card">
          <div class="project-inner">
            <h3>Project One</h3>
            <p>A brief description of the amazing project showcasing cutting-edge tech.</p>
          </div>
        </div>
        <div class="project-card">
          <div class="project-inner">
            <h3>Project Two</h3>
            <p>A brief description of another incredible project you're proud of.</p>
          </div>
        </div>
        <div class="project-card">
          <div class="project-inner">
            <h3>Project Three</h3>
            <p>This project highlights your skills in creative coding and design.</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Contact Section -->
  <section id="contact">
    <div class="glass">
      <h2>Contact</h2>
      <form onsubmit="event.preventDefault(); alert('Message sent!'); this.reset();">
        <input type="text" placeholder="Your Name" required />
        <input type="email" placeholder="Your Email" required />
        <textarea rows="5" placeholder="Your Message" required></textarea>
        <button type="submit">Send Message</button>
      </form>
    </div>
  </section>

  <script>
    // Smooth nav active state
    const sections = document.querySelectorAll('section');
    const navLinks = document.querySelectorAll('.nav-link');

    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          navLinks.forEach(link => link.classList.toggle('active', link.getAttribute('href').slice(1) === entry.target.id));
        }
      });
    }, { threshold: 0.6 });

    sections.forEach(sec => observer.observe(sec));

    // Tilt effect for project cards
    document.querySelectorAll('.project-card').forEach(card => {
      const inner = card.querySelector('.project-inner');
      card.addEventListener('mousemove', e => {
        const rect = card.getBoundingClientRect();
        const x = e.clientX - rect.left - rect.width / 2;
        const y = e.clientY - rect.top - rect.height / 2;
        const rotateX = (+1 * y / (rect.height / 2)) * 10;
        const rotateY = (-1 * x / (rect.width / 2)) * 10;
        inner.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
      });
      card.addEventListener('mouseleave', () => {
        inner.style.transform = 'rotateX(0deg) rotateY(0deg)';
      });
    });
  </script>
</body>
</html>

```
Your full portfolio site code is now available in the canvas on the right.
**How to use it**

1. Click the “Download” icon (⤓) in the canvas header to save `portfolio.html`.
2. Open the file in any modern browser—no build tools required.
3. Replace the placeholder text, add images or additional project cards, and tweak colors in the `:root` variables to customise the neon palette.

Enjoy your new glass-neon portfolio! If you’d like iterations (extra pages, dark-light toggle, 3-D hero, etc.) just let me know.
