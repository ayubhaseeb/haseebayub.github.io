# haseebayub.github.io
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Haseeb Ayub</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #0d0d0d;
      --off-white: #f0ece4;
      --accent: #e8430a;
      --muted: #6b6560;
      --card-bg: #161412;
      --border: rgba(240, 236, 228, 0.08);
    }

    body {
      background: var(--bg);
      color: var(--off-white);
      font-family: 'DM Sans', sans-serif;
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* Noise grain overlay */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 100;
      opacity: 0.6;
    }

    /* Warm glow top-left */
    .glow {
      position: fixed;
      top: -200px;
      left: -100px;
      width: 600px;
      height: 600px;
      background: radial-gradient(circle, rgba(232, 67, 10, 0.12) 0%, transparent 70%);
      pointer-events: none;
      z-index: 0;
    }

    nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 2rem 4rem;
      position: relative;
      z-index: 10;
      border-bottom: 1px solid var(--border);
      opacity: 0;
      animation: fadeDown 0.6s ease forwards;
      animation-delay: 0.1s;
    }

    .nav-logo {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.4rem;
      letter-spacing: 0.15em;
      color: var(--off-white);
    }

    .nav-links {
      display: flex;
      gap: 2.5rem;
      list-style: none;
    }

    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 0.82rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      transition: color 0.2s;
    }

    .nav-links a:hover { color: var(--off-white); }

    /* ---- HERO ---- */
    .hero {
      position: relative;
      z-index: 10;
      padding: 5rem 4rem 4rem;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 4rem;
      align-items: start;
      max-width: 1400px;
      margin: 0 auto;
    }

    .hero-left { display: flex; flex-direction: column; }

    .eyebrow {
      display: flex;
      align-items: center;
      gap: 0.75rem;
      margin-bottom: 1.5rem;
      opacity: 0;
      animation: fadeUp 0.7s ease forwards;
      animation-delay: 0.3s;
    }

    .eyebrow-line {
      width: 36px;
      height: 1px;
      background: var(--accent);
    }

    .eyebrow span {
      font-size: 0.72rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--accent);
      font-weight: 500;
    }

    h1 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(3.5rem, 7vw, 7rem);
      line-height: 0.95;
      letter-spacing: 0.02em;
      margin-bottom: 2rem;
      opacity: 0;
      animation: fadeUp 0.8s ease forwards;
      animation-delay: 0.45s;
    }

    h1 em {
      font-style: normal;
      color: var(--accent);
    }

    .hero-desc {
      font-size: 1rem;
      line-height: 1.75;
      color: rgba(240, 236, 228, 0.65);
      font-weight: 300;
      max-width: 480px;
      margin-bottom: 3rem;
      opacity: 0;
      animation: fadeUp 0.8s ease forwards;
      animation-delay: 0.6s;
    }

    .hero-desc strong {
      color: var(--off-white);
      font-weight: 500;
    }

    .cta-row {
      display: flex;
      align-items: center;
      gap: 1.5rem;
      opacity: 0;
      animation: fadeUp 0.8s ease forwards;
      animation-delay: 0.75s;
    }

    .btn-primary {
      background: var(--accent);
      color: var(--off-white);
      padding: 0.85rem 2rem;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.82rem;
      font-weight: 500;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      border: none;
      cursor: pointer;
      text-decoration: none;
      transition: background 0.2s, transform 0.2s;
      display: inline-block;
    }

    .btn-primary:hover {
      background: #c73508;
      transform: translateY(-1px);
    }

    .btn-ghost {
      color: var(--muted);
      font-size: 0.82rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      text-decoration: none;
      display: flex;
      align-items: center;
      gap: 0.5rem;
      transition: color 0.2s;
    }

    .btn-ghost:hover { color: var(--off-white); }
    .btn-ghost::after { content: '→'; transition: transform 0.2s; }
    .btn-ghost:hover::after { transform: translateX(4px); }

    /* ---- RIGHT COLUMN ---- */
    .hero-right {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      padding-top: 1rem;
    }

    .stat-card {
      background: var(--card-bg);
      border: 1px solid var(--border);
      padding: 1.5rem 2rem;
      display: flex;
      align-items: center;
      gap: 1.5rem;
      opacity: 0;
      transform: translateX(20px);
      animation: fadeInRight 0.7s ease forwards;
    }

    .stat-card:nth-child(1) { animation-delay: 0.5s; }
    .stat-card:nth-child(2) { animation-delay: 0.65s; }
    .stat-card:nth-child(3) { animation-delay: 0.8s; }

    .stat-card:hover {
      border-color: rgba(232, 67, 10, 0.3);
      transition: border-color 0.3s;
    }

    .stat-icon {
      font-size: 1.6rem;
      width: 48px;
      flex-shrink: 0;
      text-align: center;
    }

    .stat-label {
      font-size: 0.7rem;
      text-transform: uppercase;
      letter-spacing: 0.16em;
      color: var(--muted);
      margin-bottom: 0.3rem;
    }

    .stat-value {
      font-size: 0.95rem;
      font-weight: 500;
      color: var(--off-white);
      line-height: 1.4;
    }

    /* ---- TAGS ---- */
    .tags-row {
      display: flex;
      flex-wrap: wrap;
      gap: 0.6rem;
      margin-top: 0.5rem;
      opacity: 0;
      animation: fadeUp 0.8s ease forwards;
      animation-delay: 0.9s;
    }

    .tag {
      font-size: 0.72rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--muted);
      border: 1px solid var(--border);
      padding: 0.35rem 0.85rem;
      transition: color 0.2s, border-color 0.2s;
    }

    .tag:hover {
      color: var(--off-white);
      border-color: rgba(240, 236, 228, 0.25);
    }

    /* ---- DIVIDER ---- */
    .divider {
      max-width: 1400px;
      margin: 0 auto;
      padding: 0 4rem;
      border-top: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding-top: 2rem;
      padding-bottom: 2rem;
      opacity: 0;
      animation: fadeUp 0.7s ease forwards;
      animation-delay: 1.1s;
    }

    .divider-companies {
      display: flex;
      align-items: center;
      gap: 0.75rem;
      font-size: 0.72rem;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: var(--muted);
    }

    .divider-companies span {
      color: rgba(240, 236, 228, 0.35);
      font-size: 1rem;
    }

    .company-name {
      color: rgba(240, 236, 228, 0.5);
      transition: color 0.2s;
    }
    .company-name:hover { color: var(--off-white); }

    .availability {
      display: flex;
      align-items: center;
      gap: 0.6rem;
      font-size: 0.72rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--muted);
    }

    .dot {
      width: 7px;
      height: 7px;
      border-radius: 50%;
      background: #4ade80;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.4; }
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(18px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeDown {
      from { opacity: 0; transform: translateY(-12px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeInRight {
      from { opacity: 0; transform: translateX(20px); }
      to   { opacity: 1; transform: translateX(0); }
    }

    @media (max-width: 900px) {
      nav { padding: 1.5rem 2rem; }
      .nav-links { display: none; }
      .hero { grid-template-columns: 1fr; padding: 3rem 2rem 2rem; gap: 2.5rem; }
      .divider { padding: 1.5rem 2rem; flex-direction: column; align-items: flex-start; gap: 1rem; }
    }
  </style>
</head>
<body>
  <div class="glow"></div>

  <nav>
    <div class="nav-logo">Haseeb Ayub</div>
    <ul class="nav-links">
      <li><a href="#">Work</a></li>
      <li><a href="#">Projects</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </nav>

  <section class="hero">
    <div class="hero-left">

      <div class="eyebrow">
        <div class="eyebrow-line"></div>
        <span>Mechanical Engineer · McMaster University '26</span>
      </div>

      <h1>Engineering better systems—<br>from the <em>drawing board</em><br>to the open road.</h1>

      <p class="hero-desc">
        I'm a mechanical engineer passionate about <strong>designing, prototyping, and optimizing</strong> the machines and processes that move us. Whether I'm building lean systems on a factory floor, modelling components in CAD, or hand-assembling a prototype, I bring the same obsessive attention to detail — and a deep love for <strong>everything automotive</strong>.
      </p>

      <div class="cta-row">
        <a href="#" class="btn-primary">View My Work</a>
        <a href="#" class="btn-ghost">Download Resume</a>
      </div>

      <div class="tags-row">
        <div class="tag">Lean Manufacturing</div>
        <div class="tag">CAD / FEA</div>
        <div class="tag">3D Printing</div>
        <div class="tag">Six Sigma</div>
        <div class="tag">Process Optimization</div>
        <div class="tag">Automotive</div>
      </div>

    </div>

    <div class="hero-right">
      <div class="stat-card">
        <div class="stat-icon">🏭</div>
        <div>
          <div class="stat-label">Industry Experience</div>
          <div class="stat-value">Collins Aerospace · Webasto · Magna — real-world manufacturing, lean ops & production line engineering</div>
        </div>
      </div>
      <div class="stat-card">
        <div class="stat-icon">🔧</div>
        <div>
          <div class="stat-label">Design & Prototyping</div>
          <div class="stat-value">SolidWorks, CATIA, FEA-certified — from concept sketches to physical prototypes and production-ready parts</div>
        </div>
      </div>
      <div class="stat-card">
        <div class="stat-icon">🚗</div>
        <div>
          <div class="stat-label">Automotive Passion</div>
          <div class="stat-value">Solar car suspension engineer, worked across Ford, GM, Honda & Stellantis vehicle programs</div>
        </div>
      </div>
    </div>
  </section>

  <div class="divider">
    <div class="divider-companies">
      <span>Experience at</span>
      <span class="company-name">Collins Aerospace</span>
      <span>·</span>
      <span class="company-name">Webasto</span>
      <span>·</span>
      <span class="company-name">Magna COSMA</span>
    </div>
    <div class="availability">
      <div class="dot"></div>
      <span>Available May 2026</span>
    </div>
  </div>

</body>
</html>
