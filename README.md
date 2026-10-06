<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Prashant Ranjan (@PrashantRanjan-2006) — Animated GitHub Profile Preview</title>
  <style>
    :root {
      --bg-primary: #070B16;
      --bg-elevated: rgba(15, 23, 42, 0.72);
      --accent-blue: #247BFF;
      --accent-red: #FF354F;
      --text-primary: #F5F7FA;
      --text-secondary: #94A3B8;
      --border-glass: rgba(255, 255, 255, 0.1);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background-color: var(--bg-primary);
      background-image:
        radial-gradient(circle at 15% 10%, rgba(36, 123, 255, 0.14), transparent 35%),
        radial-gradient(circle at 85% 85%, rgba(255, 53, 79, 0.12), transparent 35%);
      color: var(--text-primary);
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
      min-height: 100vh;
      padding: 32px 16px 72px;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .topbar {
      width: 100%;
      max-width: 1012px;
      background: var(--bg-elevated);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border: 1px solid var(--border-glass);
      border-radius: 18px;
      padding: 14px 22px;
      margin-bottom: 24px;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      box-shadow: 0 18px 40px rgba(0, 0, 0, 0.45);
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .brand-dot {
      width: 10px;
      height: 10px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--accent-blue), var(--accent-red));
      box-shadow: 0 0 12px var(--accent-blue);
    }

    .brand-title {
      font-size: 14px;
      font-weight: 700;
      letter-spacing: 0.3px;
    }

    .brand-sub {
      font-family: 'JetBrains Mono', Consolas, monospace;
      font-size: 12px;
      color: var(--text-secondary);
    }

    .viewport-controls {
      display: flex;
      gap: 8px;
    }

    .vp-btn {
      background: rgba(7, 11, 22, 0.75);
      color: var(--text-secondary);
      border: 1px solid rgba(255, 255, 255, 0.1);
      border-radius: 10px;
      padding: 7px 14px;
      font-size: 12px;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.2s ease;
    }

    .vp-btn:hover,
    .vp-btn.active {
      color: var(--text-primary);
      border-color: var(--accent-blue);
      background: rgba(36, 123, 255, 0.18);
      box-shadow: 0 0 14px rgba(36, 123, 255, 0.3);
    }

    .readme-frame {
      width: 100%;
      max-width: 1012px;
      background: #0D1117;
      border: 1px solid #30363D;
      border-radius: 22px;
      padding: 28px;
      box-shadow: 0 24px 64px rgba(0, 0, 0, 0.65);
      transition: max-width 0.35s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .readme-frame.tablet {
      max-width: 768px;
    }

    .readme-frame.mobile {
      max-width: 412px;
      padding: 14px;
    }

    .readme-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding-bottom: 16px;
      margin-bottom: 22px;
      border-bottom: 1px solid #21262D;
      font-family: 'JetBrains Mono', Consolas, monospace;
      font-size: 12px;
      color: var(--text-secondary);
    }

    .svg-stack {
      display: flex;
      flex-direction: column;
      gap: 20px;
    }

    .svg-section {
      width: 100%;
      display: block;
      border-radius: 22px;
      overflow: hidden;
    }

    .svg-section object,
    .svg-section img {
      width: 100%;
      height: auto;
      display: block;
    }

    .links-dock {
      margin-top: 28px;
      padding: 28px 24px;
      border-radius: 20px;
      background: linear-gradient(145deg, rgba(15, 23, 42, 0.85), rgba(7, 11, 22, 0.92));
      border: 1px solid rgba(36, 123, 255, 0.28);
      text-align: center;
    }

    .links-title {
      font-size: 13px;
      font-family: 'JetBrains Mono', Consolas, monospace;
      color: #60A5FA;
      letter-spacing: 1.6px;
      text-transform: uppercase;
      margin-bottom: 16px;
    }

    .social-links {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 12px;
      margin-bottom: 24px;
    }

    .social-pill {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 10px 18px;
      border-radius: 12px;
      background: rgba(15, 23, 42, 0.9);
      border: 1px solid rgba(255, 255, 255, 0.12);
      color: var(--text-primary);
      text-decoration: none;
      font-size: 13.5px;
      font-weight: 600;
      transition: all 0.25s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .social-pill:hover {
      transform: translateY(-3px);
      border-color: var(--accent-blue);
      box-shadow: 0 8px 20px rgba(36, 123, 255, 0.32);
    }

    .social-pill.accent-red:hover {
      border-color: var(--accent-red);
      box-shadow: 0 8px 20px rgba(255, 53, 79, 0.32);
    }

    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 14px;
      margin-top: 12px;
      text-align: left;
    }

    .project-link-card {
      padding: 16px 18px;
      border-radius: 14px;
      background: rgba(7, 11, 22, 0.78);
      border: 1px solid rgba(255, 255, 255, 0.08);
      text-decoration: none;
      color: var(--text-primary);
      transition: all 0.25s ease;
    }

    .project-link-card:hover {
      transform: translateY(-3px);
      border-color: var(--accent-blue);
      background: rgba(15, 23, 42, 0.92);
    }

    .project-link-card h4 {
      font-size: 15px;
      font-weight: 700;
      margin-bottom: 6px;
    }

    .project-link-card p {
      font-size: 12px;
      color: var(--text-secondary);
      font-family: 'JetBrains Mono', Consolas, monospace;
    }
  </style>
</head>
<body>
  <header class="topbar">
    <div class="brand">
      <span class="brand-dot"></span>
      <div>
        <div class="brand-title">Prashant Ranjan — GitHub Profile README Preview</div>
        <div class="brand-sub">PrashantRanjan-2006 / README.md • Dark Luxury SVG Engine</div>
      </div>
    </div>
    <div class="viewport-controls">
      <button class="vp-btn active" onclick="setViewport('desktop', this)">Desktop (100%)</button>
      <button class="vp-btn" onclick="setViewport('tablet', this)">Tablet (768px)</button>
      <button class="vp-btn" onclick="setViewport('mobile', this)">Mobile (412px)</button>
    </div>
  </header>

  <main class="readme-frame" id="readmeFrame">
    <div class="readme-header">
      <span>PrashantRanjan-2006 / README.md</span>
      <span>SVG + CSS + SMIL • Zero External Assets</span>
    </div>

    <div class="svg-stack">
      <div class="svg-section">
        <object type="image/svg+xml" data="./assets/hero.svg?v=1" aria-label="Hero Section">
          <img src="./assets/hero.svg?v=1" alt="Hero" />
        </object>
      </div>

      <div class="svg-section">
        <object type="image/svg+xml" data="./assets/about-life.svg?v=1" aria-label="About Section">
          <img src="./assets/about-life.svg?v=1" alt="About" />
        </object>
      </div>

      <div class="svg-section">
        <object type="image/svg+xml" data="./assets/stack.svg?v=1" aria-label="Tech Stack Section">
          <img src="./assets/stack.svg?v=1" alt="Stack" />
        </object>
      </div>

      <div class="svg-section">
        <object type="image/svg+xml" data="./assets/id-dashboard.svg?v=1" aria-label="ID Dashboard Section">
          <img src="./assets/id-dashboard.svg?v=1" alt="ID" />
        </object>
      </div>

      <div class="svg-section">
        <object type="image/svg+xml" data="./assets/connect.svg?v=1" aria-label="Connect Section">
          <img src="./assets/connect.svg?v=1" alt="Connect" />
        </object>
      </div>
    </div>

    <section class="links-dock">
      <div class="links-title">// Clickable Social Links (Below Connect SVG)</div>
      <div class="social-links">
        <a class="social-pill" href="https://github.com/PrashantRanjan-2006" target="_blank" rel="noopener">GitHub ↗</a>
        <a class="social-pill" href="https://www.linkedin.com/in/prashant-ranjan-a39077330/" target="_blank" rel="noopener">LinkedIn ↗</a>
        <a class="social-pill accent-red" href="https://my-portfolio-weld-two-13.vercel.app/" target="_blank" rel="noopener">Portfolio ↗</a>
        <a class="social-pill" href="mailto:prashantranjan20192006@gmail.com">Email ↗</a>
        <a class="social-pill accent-red" href="https://x.com/prashant5916" target="_blank" rel="noopener">Twitter / X ↗</a>
      </div>

      <div class="links-title">// Featured Project Repositories</div>
      <div class="projects-grid">
        <a class="project-link-card" href="https://github.com/PrashantRanjan-2006" target="_blank" rel="noopener">
          <h4>Hospital Management System ↗</h4>
          <p>Java • Spring Boot • MySQL • React</p>
        </a>
        <a class="project-link-card" href="https://github.com/PrashantRanjan-2006/E-commerce-shopkart" target="_blank" rel="noopener">
          <h4>Quick Bite ↗</h4>
          <p>Spring Boot • MySQL • JPA • React</p>
        </a>
        <a class="project-link-card" href="https://github.com/PrashantRanjan-2006/Health-care-system" target="_blank" rel="noopener">
          <h4>Healthcare System ↗</h4>
          <p>React • JavaScript • HTML • CSS</p>
        </a>
      </div>
    </section>
  </main>

  <script>
    function setViewport(mode, btn) {
      var frame = document.getElementById('readmeFrame');
      frame.className = 'readme-frame' + (mode === 'desktop' ? '' : ' ' + mode);
      var buttons = document.querySelectorAll('.vp-btn');
      for (var i = 0; i < buttons.length; i++) {
        buttons[i].classList.remove('active');
      }
      btn.classList.add('active');
    }
  </script>
</body>
</html>
