# [Chat Log](https://chatgpt.com/share/6872f947-458c-8004-9427-979a67506bdc)

# [Interactive Artifact](https://chatgpt.com/canvas/shared/6872f930de2481919b3b2854d683ca79)
<img width="1908" height="1165" alt="image" src="https://github.com/user-attachments/assets/7a8c446c-e2df-40e3-8d5a-154def5c124a" />

# Prompt

## Create a visually stunning interactive personal portfolio website using glassmorphism and neon gradients.


# ChatGPT

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Neon Glass Portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;800&family=Inter:wght@400;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --neon-pink: #ff56f6;
      --neon-blue: #00f0ff;
      --neon-purple: #8456ff;
      --glass-bg: rgba(25, 28, 38, 0.60);
      --glass-blur: 16px;
      --radius: 2rem;
      --shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.25);
    }
    * { box-sizing: border-box; }
    body {
      min-height: 100vh;
      margin: 0;
      background: linear-gradient(135deg, var(--neon-pink) 0%, var(--neon-blue) 70%, var(--neon-purple) 100%);
      background-attachment: fixed;
      font-family: 'Inter', Arial, sans-serif;
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      padding: 0;
    }
    header {
      width: 100%;
      padding: 2rem 0 1.5rem 0;
      display: flex;
      justify-content: center;
      align-items: center;
      background: none;
    }
    .glass-card {
      background: var(--glass-bg);
      box-shadow: var(--shadow);
      border-radius: var(--radius);
      backdrop-filter: blur(var(--glass-blur));
      -webkit-backdrop-filter: blur(var(--glass-blur));
      border: 1.5px solid rgba(255,255,255,0.15);
      position: relative;
      overflow: hidden;
      margin: 1.5rem 0;
      width: 95vw;
      max-width: 450px;
      transition: transform 0.25s cubic-bezier(.4,2,.3,1), box-shadow 0.2s;
    }
    .glass-card:hover {
      transform: translateY(-7px) scale(1.025);
      box-shadow: 0 16px 48px 0 rgba(0,255,255,0.25);
      border: 2.5px solid var(--neon-blue);
    }
    .avatar {
      display: flex;
      justify-content: center;
      margin-top: -70px;
    }
    .avatar img {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      border: 3px solid var(--neon-pink);
      box-shadow: 0 0 24px var(--neon-pink), 0 0 60px var(--neon-blue);
      background: #23233d;
      object-fit: cover;
    }
    h1 {
      font-family: 'Orbitron', Arial, sans-serif;
      font-weight: 800;
      font-size: 2.5rem;
      text-align: center;
      margin-bottom: 0.25em;
      letter-spacing: 0.02em;
      background: linear-gradient(90deg, var(--neon-pink), var(--neon-blue), var(--neon-purple));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    h2 {
      font-family: 'Orbitron', Arial, sans-serif;
      font-weight: 500;
      font-size: 1.3rem;
      text-align: center;
      letter-spacing: 0.05em;
      margin-top: 0;
      margin-bottom: 0.8em;
      color: var(--neon-blue);
    }
    .bio {
      font-size: 1.08rem;
      text-align: center;
      color: #f0f0ff;
      padding: 0 1.2rem;
      margin-bottom: 1.6rem;
      line-height: 1.65;
    }
    .socials {
      display: flex;
      justify-content: center;
      gap: 1.2rem;
      margin: 1rem 0 1.7rem 0;
    }
    .socials a {
      color: var(--neon-blue);
      text-decoration: none;
      font-size: 2rem;
      transition: color 0.2s, filter 0.2s;
      filter: drop-shadow(0 0 4px var(--neon-pink));
    }
    .socials a:hover {
      color: var(--neon-pink);
      filter: drop-shadow(0 0 8px var(--neon-blue));
    }
    nav {
      display: flex;
      justify-content: center;
      gap: 1.4rem;
      margin-bottom: 2.2rem;
      flex-wrap: wrap;
    }
    nav button {
      background: linear-gradient(90deg, var(--neon-blue), var(--neon-pink));
      border: none;
      border-radius: 999px;
      color: #fff;
      padding: 0.5em 1.8em;
      font-size: 1.12rem;
      margin: 0 0.3em;
      font-family: 'Orbitron', Arial, sans-serif;
      font-weight: 500;
      cursor: pointer;
      box-shadow: 0 2px 16px 0 rgba(0,255,255,0.11);
      transition: background 0.2s, transform 0.2s;
    }
    nav button.active, nav button:hover {
      background: linear-gradient(90deg, var(--neon-pink), var(--neon-blue));
      transform: translateY(-2px) scale(1.07);
    }
    section {
      display: none;
      padding: 2rem 1.4rem 2.4rem 1.4rem;
      font-size: 1.1rem;
    }
    section.active {
      display: block;
      animation: fadeIn 0.9s cubic-bezier(.25,1,.5,1);
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(25px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .project-list {
      display: flex;
      flex-direction: column;
      gap: 1.3rem;
      margin-top: 1.2rem;
    }
    .project {
      background: rgba(0, 0, 0, 0.23);
      border-radius: 1.1rem;
      box-shadow: 0 1px 9px 0 rgba(0,255,255,0.06);
      padding: 1rem 1.3rem;
      border: 1.5px solid rgba(255,255,255,0.10);
      transition: box-shadow 0.22s, border 0.18s;
      position: relative;
    }
    .project:hover {
      box-shadow: 0 6px 24px 0 var(--neon-blue);
      border: 1.8px solid var(--neon-blue);
    }
    .project-title {
      font-family: 'Orbitron', Arial, sans-serif;
      font-size: 1.25rem;
      margin-bottom: 0.3em;
      color: var(--neon-pink);
    }
    .project-desc {
      font-size: 1.02rem;
      color: #e5e8fa;
    }
    .project-link {
      display: inline-block;
      margin-top: 0.6em;
      color: var(--neon-blue);
      text-decoration: underline;
      font-size: 1.02rem;
      transition: color 0.18s;
    }
    .project-link:hover {
      color: var(--neon-pink);
    }
    @media (max-width: 600px) {
      .glass-card { max-width: 99vw; padding: 0; }
      section { padding: 1.2rem 0.5rem 1.6rem 0.5rem; }
      .avatar img { width: 94px; height: 94px; }
    }
  </style>
  <script src="https://unpkg.com/@phosphor-icons/web"></script>
</head>
<body>
  <header>
    <div class="avatar">
      <img src="https://randomuser.me/api/portraits/men/32.jpg" alt="Avatar">
    </div>
  </header>
  <div class="glass-card">
    <h1>Your Name</h1>
    <h2>Creative Technologist &amp; Developer</h2>
    <div class="bio">
      I build beautiful, interactive experiences blending technology, design, and imagination. <br>
      Welcome to my neon glass portfolio—explore my projects, story, and how we can connect.
    </div>
    <div class="socials">
      <a href="#" title="Twitter"><i class="ph ph-twitter-logo"></i></a>
      <a href="#" title="GitHub"><i class="ph ph-github-logo"></i></a>
      <a href="#" title="LinkedIn"><i class="ph ph-linkedin-logo"></i></a>
      <a href="#" title="Email"><i class="ph ph-envelope"></i></a>
    </div>
    <nav>
      <button class="tab-btn active" data-tab="about">About</button>
      <button class="tab-btn" data-tab="projects">Projects</button>
      <button class="tab-btn" data-tab="contact">Contact</button>
    </nav>
    <section id="about" class="active">
      <h3 style="color:var(--neon-blue);margin-top:0;">Who I Am</h3>
      <p style="color:#e8eaff;font-size:1.07rem;">Passionate about blending code and art, I love building beautiful, intuitive apps. Skilled in React, JS, and design. Based in Austin, always learning, and excited for future collabs.</p>
    </section>
    <section id="projects">
      <h3 style="color:var(--neon-blue);margin-top:0;">Featured Projects</h3>
      <div class="project-list">
        <div class="project">
          <div class="project-title">NeonChat</div>
          <div class="project-desc">A real-time group chat app with glassy UI and smooth neon transitions. <br>React + Firebase.</div>
          <a href="#" class="project-link">View on GitHub</a>
        </div>
        <div class="project">
          <div class="project-title">Gradient Portfolio</div>
          <div class="project-desc">A personal portfolio template using glassmorphism and animated gradients.<br>Pure HTML/CSS/JS.</div>
          <a href="#" class="project-link">Live Demo</a>
        </div>
        <div class="project">
          <div class="project-title">FitSync AI</div>
          <div class="project-desc">AI-driven fitness tracker with playful UI, stats, and seamless mobile experience.</div>
          <a href="#" class="project-link">View on GitHub</a>
        </div>
      </div>
    </section>
    <section id="contact">
      <h3 style="color:var(--neon-blue);margin-top:0;">Let's Connect</h3>
      <form id="contact-form" autocomplete="off" style="display: flex; flex-direction: column; gap: 1rem;">
        <input required name="name" type="text" placeholder="Your Name" style="border-radius:8px;padding:0.7em 1em;border:none;background:rgba(255,255,255,0.14);color:#fff;font-size:1.05rem;">
        <input required name="email" type="email" placeholder="Your Email" style="border-radius:8px;padding:0.7em 1em;border:none;background:rgba(255,255,255,0.14);color:#fff;font-size:1.05rem;">
        <textarea required name="message" rows="4" placeholder="Message" style="border-radius:8px;padding:0.7em 1em;border:none;background:rgba(255,255,255,0.14);color:#fff;font-size:1.05rem;"></textarea>
        <button type="submit" style="background:linear-gradient(90deg,var(--neon-pink),var(--neon-blue));border:none;border-radius:999px;color:#fff;padding:0.6em 2em;font-size:1.18rem;box-shadow:0 2px 10px 0 var(--neon-pink);font-family:'Orbitron',Arial,sans-serif;letter-spacing:0.05em;cursor:pointer;">Send</button>
        <div id="form-status" style="font-size:1.01rem;min-height:24px;"></div>
      </form>
    </section>
  </div>

  <script>
    // Tab Navigation
    const tabBtns = document.querySelectorAll('.tab-btn');
    const sections = document.querySelectorAll('section');
    tabBtns.forEach(btn => {
      btn.addEventListener('click', () => {
        tabBtns.forEach(b => b.classList.remove('active'));
        sections.forEach(sec => sec.classList.remove('active'));
        btn.classList.add('active');
        document.getElementById(btn.dataset.tab).classList.add('active');
      });
    });
    // Contact Form (simulate success)
    document.getElementById('contact-form').addEventListener('submit', function(e) {
      e.preventDefault();
      document.getElementById('form-status').textContent = 'Thank you! I will get back to you soon.';
      this.reset();
    });
  </script>
</body>
</html>

```

Your **visually stunning interactive personal portfolio website** using **glassmorphism** and **neon gradients** is ready in Canvas! ✨

**Features:**

* Glassy, blurred cards with neon gradient highlights
* Responsive, animated navigation (About / Projects / Contact)
* Modern avatar and social links
* Featured Projects showcase (easy to edit)
* Stylish contact form (simulated submission)
* Fully responsive & beautiful on mobile

**How to Use / Edit:**

* Change `"Your Name"`, profile photo, and social links.
* Add or edit projects in the Projects section.
* Personalize the About text and Contact form as needed.

**View or edit the full HTML/CSS/JS code in the Canvas panel (Glassmorphism Neon Portfolio).**
Let me know if you want further customization, additional pages, or advanced interactivity (e.g. animated gradient backgrounds, project filtering, dark/light toggle, etc)!
