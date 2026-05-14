# FinnsProfile
<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Finn – GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Bebas+Neue&family=Rajdhani:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --yellow: #FFE500;
    --black: #0a0a0a;
    --dark: #111111;
    --card: #161616;
    --border: #2a2a2a;
    --text: #e8e8e8;
    --muted: #888;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--black);
    color: var(--text);
    font-family: 'Rajdhani', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* SCANLINE OVERLAY */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(255,229,0,0.015) 2px,
      rgba(255,229,0,0.015) 4px
    );
    pointer-events: none;
    z-index: 999;
  }

  /* NOISE TEXTURE */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    opacity: 0.3;
    pointer-events: none;
    z-index: 998;
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 20px 80px;
    position: relative;
    z-index: 1;
  }

  /* ── HEADER ── */
  .header {
    display: flex;
    align-items: center;
    gap: 32px;
    margin-bottom: 48px;
    animation: slideDown 0.8s cubic-bezier(0.16, 1, 0.3, 1) both;
  }

  @keyframes slideDown {
    from { opacity: 0; transform: translateY(-30px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .avatar-wrap {
    position: relative;
    flex-shrink: 0;
  }

  .avatar-ring {
    width: 110px;
    height: 110px;
    border-radius: 50%;
    border: 2px solid var(--yellow);
    padding: 4px;
    position: relative;
    animation: spinRing 8s linear infinite;
  }

  @keyframes spinRing {
    from { box-shadow: 0 0 0 2px var(--yellow), 0 0 20px rgba(255,229,0,0.3); }
    50%  { box-shadow: 0 0 0 3px var(--yellow), 0 0 40px rgba(255,229,0,0.5); }
    to   { box-shadow: 0 0 0 2px var(--yellow), 0 0 20px rgba(255,229,0,0.3); }
  }

  .avatar {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background: var(--card);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 42px;
    color: var(--yellow);
    letter-spacing: 2px;
    overflow: hidden;
  }

  .avatar svg { width: 60px; height: 60px; fill: var(--yellow); opacity: 0.8; }

  .online-dot {
    position: absolute;
    bottom: 6px;
    right: 6px;
    width: 14px;
    height: 14px;
    background: #22c55e;
    border-radius: 50%;
    border: 2px solid var(--black);
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { box-shadow: 0 0 0 0 rgba(34,197,94,0.6); }
    50%       { box-shadow: 0 0 0 6px rgba(34,197,94,0); }
  }

  .header-info { flex: 1; }

  .name-line {
    display: flex;
    align-items: baseline;
    gap: 12px;
    margin-bottom: 4px;
  }

  .first-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 52px;
    line-height: 1;
    color: var(--text);
    letter-spacing: 3px;
  }

  .last-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 52px;
    line-height: 1;
    color: var(--yellow);
    letter-spacing: 3px;
  }

  .role-line {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-bottom: 12px;
  }

  .role-text {
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  .cursor {
    width: 8px;
    height: 16px;
    background: var(--yellow);
    display: inline-block;
    animation: blink 1s step-end infinite;
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50%       { opacity: 0; }
  }

  .tag-row { display: flex; gap: 8px; flex-wrap: wrap; }

  .tag {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    color: var(--yellow);
    border: 1px solid rgba(255,229,0,0.3);
    padding: 3px 10px;
    letter-spacing: 1px;
    text-transform: uppercase;
    transition: all 0.2s;
  }

  .tag:hover {
    background: rgba(255,229,0,0.1);
    border-color: var(--yellow);
  }

  /* ── SECTION TITLE ── */
  .section-label {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 13px;
    letter-spacing: 5px;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(to right, var(--border), transparent);
  }

  /* ── STATS GRID ── */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 2px;
    margin-bottom: 32px;
    animation: fadeUp 0.8s 0.2s cubic-bezier(0.16, 1, 0.3, 1) both;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .stat-card {
    background: var(--card);
    padding: 24px 16px;
    text-align: center;
    border: 1px solid var(--border);
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s, transform 0.3s;
    cursor: default;
  }

  .stat-card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(255,229,0,0.05) 0%, transparent 60%);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .stat-card:hover { border-color: var(--yellow); transform: translateY(-2px); }
  .stat-card:hover::before { opacity: 1; }

  .stat-number {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 48px;
    line-height: 1;
    color: var(--yellow);
    display: block;
    position: relative;
  }

  .stat-plus {
    font-size: 28px;
    vertical-align: super;
  }

  .stat-label {
    font-family: 'Space Mono', monospace;
    font-size: 9px;
    color: var(--muted);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-top: 6px;
    display: block;
  }

  /* ── ABOUT & INFO ── */
  .two-col {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    margin-bottom: 32px;
    animation: fadeUp 0.8s 0.3s cubic-bezier(0.16, 1, 0.3, 1) both;
  }

  .info-card {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 28px;
    transition: border-color 0.3s;
  }

  .info-card:hover { border-color: rgba(255,229,0,0.4); }

  .info-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 11px;
    letter-spacing: 4px;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .info-title span { color: var(--yellow); }

  .info-row {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    padding: 10px 0;
    border-bottom: 1px solid var(--border);
  }

  .info-row:last-child { border-bottom: none; }

  .info-key {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  .info-val {
    font-family: 'Rajdhani', sans-serif;
    font-size: 15px;
    font-weight: 600;
    color: var(--text);
    text-align: right;
  }

  .info-val a { color: var(--yellow); text-decoration: none; }
  .info-val a:hover { text-decoration: underline; }

  /* ── SKILLS ── */
  .skills-card {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 28px;
    animation: fadeUp 0.8s 0.4s cubic-bezier(0.16, 1, 0.3, 1) both;
    margin-bottom: 32px;
  }

  .skill-row {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 18px;
  }

  .skill-row:last-child { margin-bottom: 0; }

  .skill-name {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--text);
    letter-spacing: 1px;
    width: 130px;
    flex-shrink: 0;
  }

  /* ── CUSTOM CURSOR GLOW ── */
  .cursor-glow {
    position: fixed;
    width: 400px;
    height: 400px;
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    background: radial-gradient(circle at center,
      rgba(255,229,0,0.18) 0%,
      rgba(255,229,0,0.07) 25%,
      rgba(255,229,0,0.02) 50%,
      transparent 70%
    );
    filter: blur(18px);
    mix-blend-mode: screen;
    transition: left 0.06s linear, top 0.06s linear;
  }

  /* ── LANGUAGE FLAGS ── */
  .lang-flags {
    display: flex;
    flex-direction: column;
    gap: 6px;
    align-items: flex-end;
  }

  .flag-item {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 14px;
    font-weight: 600;
    color: var(--text);
  }

  .flag-img {
    width: 24px;
    height: 16px;
    border-radius: 2px;
    object-fit: cover;
    box-shadow: 0 0 6px rgba(255,229,0,0.5), 0 0 12px rgba(255,229,0,0.2);
    border: 1px solid rgba(255,229,0,0.2);
  }

  .skill-bar-bg {
    flex: 1;
    height: 4px;
    background: var(--border);
    position: relative;
    overflow: hidden;
  }

  .skill-bar-fill {
    height: 100%;
    background: var(--yellow);
    width: 0%;
    transition: width 1.5s cubic-bezier(0.16, 1, 0.3, 1);
    position: relative;
  }

  .skill-pct {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--yellow);
    width: 36px;
    text-align: right;
    flex-shrink: 0;
  }

  /* ── PROJECTS ── */
  .projects-section {
    animation: fadeUp 0.8s 0.5s cubic-bezier(0.16, 1, 0.3, 1) both;
    margin-bottom: 32px;
  }

  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
  }

  .project-card {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 24px;
    display: flex;
    align-items: flex-start;
    gap: 16px;
    text-decoration: none;
    color: var(--text);
    transition: border-color 0.3s, transform 0.2s, background 0.3s;
    position: relative;
    overflow: hidden;
  }

  .project-card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(255,229,0,0.04) 0%, transparent 70%);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .project-card:hover { border-color: var(--yellow); transform: translateY(-2px); }
  .project-card:hover::before { opacity: 1; }
  .project-card:hover .project-arrow { color: var(--yellow); transform: translate(3px, -3px); }

  .project-number {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 36px;
    line-height: 1;
    color: rgba(255,229,0,0.15);
    flex-shrink: 0;
    transition: color 0.3s;
  }

  .project-card:hover .project-number { color: rgba(255,229,0,0.35); }

  .project-body { flex: 1; }

  .project-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 20px;
    letter-spacing: 2px;
    color: var(--text);
    margin-bottom: 6px;
  }

  .project-desc {
    font-family: 'Rajdhani', sans-serif;
    font-size: 13px;
    color: var(--muted);
    line-height: 1.5;
    margin-bottom: 12px;
  }

  .project-tags { display: flex; gap: 6px; flex-wrap: wrap; }

  .ptag {
    font-family: 'Space Mono', monospace;
    font-size: 9px;
    color: var(--yellow);
    border: 1px solid rgba(255,229,0,0.25);
    padding: 2px 8px;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  .project-arrow {
    color: var(--border);
    flex-shrink: 0;
    transition: color 0.3s, transform 0.3s;
  }

  .project-arrow svg { width: 18px; height: 18px; }

  @media (max-width: 600px) {
    .projects-grid { grid-template-columns: 1fr; }
  }

  /* ── GITHUB STATS CARDS ── */
  .github-section {
    animation: fadeUp 0.8s 0.5s cubic-bezier(0.16, 1, 0.3, 1) both;
    margin-bottom: 32px;
  }

  .github-cards {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
  }

  .gh-card {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 20px 24px;
    transition: border-color 0.3s;
  }

  .gh-card:hover { border-color: rgba(255,229,0,0.4); }

  .gh-card-title {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  .gh-langs {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .gh-lang-row {
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .lang-dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  .lang-name {
    font-family: 'Rajdhani', sans-serif;
    font-size: 13px;
    color: var(--text);
    flex: 1;
  }

  .lang-pct {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    color: var(--muted);
  }

  .gh-stat-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .gh-mini-stat { text-align: center; }

  .gh-mini-num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 32px;
    color: var(--yellow);
    display: block;
    line-height: 1;
  }

  .gh-mini-label {
    font-family: 'Space Mono', monospace;
    font-size: 9px;
    color: var(--muted);
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-top: 4px;
  }

  /* ── CONTRIBUTION BAR ── */
  .contrib-section {
    animation: fadeUp 0.8s 0.6s cubic-bezier(0.16, 1, 0.3, 1) both;
    margin-bottom: 32px;
  }

  .contrib-card {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 24px;
  }

  .contrib-grid {
    display: grid;
    grid-template-columns: repeat(52, 1fr);
    gap: 2px;
  }

  .contrib-week { display: grid; grid-template-rows: repeat(7, 1fr); gap: 2px; }

  .contrib-day {
    width: 100%;
    aspect-ratio: 1;
    border-radius: 1px;
    background: var(--border);
    transition: background 0.3s;
  }

  .contrib-day.l1 { background: rgba(255,229,0,0.2); }
  .contrib-day.l2 { background: rgba(255,229,0,0.45); }
  .contrib-day.l3 { background: rgba(255,229,0,0.7); }
  .contrib-day.l4 { background: var(--yellow); }

  /* ── CONTACT ── */
  .contact-section {
    animation: fadeUp 0.8s 0.7s cubic-bezier(0.16, 1, 0.3, 1) both;
  }

  .contact-row {
    display: flex;
    gap: 2px;
    flex-wrap: wrap;
  }

  .contact-btn {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 14px 24px;
    display: flex;
    align-items: center;
    gap: 10px;
    text-decoration: none;
    color: var(--text);
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 1px;
    text-transform: uppercase;
    transition: all 0.2s;
    cursor: pointer;
  }

  .contact-btn:hover {
    background: var(--yellow);
    color: var(--black);
    border-color: var(--yellow);
  }

  .contact-btn svg { width: 16px; height: 16px; flex-shrink: 0; }

  /* ── FOOTER ── */
  .footer {
    margin-top: 60px;
    padding-top: 24px;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
    animation: fadeUp 0.8s 0.8s both;
  }

  .footer-logo {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 20px;
    letter-spacing: 3px;
    color: var(--muted);
  }

  .footer-logo span { color: var(--yellow); }

  .footer-text {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 1px;
  }

  /* RESPONSIVE */
  @media (max-width: 600px) {
    .stats-grid { grid-template-columns: repeat(2, 1fr); }
    .two-col { grid-template-columns: 1fr; }
    .github-cards { grid-template-columns: 1fr; }
    .header { flex-direction: column; text-align: center; }
    .first-name, .last-name { font-size: 40px; }
    .name-line { justify-content: center; }
    .role-line { justify-content: center; }
    .tag-row { justify-content: center; }
    .contrib-grid { grid-template-columns: repeat(26, 1fr); }
  }
</style>
</head>
<body>
<div class="cursor-glow" id="cursorGlow"></div>
<div class="container">

  <!-- HEADER -->
  <header class="header">
    <div class="avatar-wrap">
      <div class="avatar-ring">
        <div class="avatar">
          <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path d="M12 12c2.7 0 4.8-2.1 4.8-4.8S14.7 2.4 12 2.4 7.2 4.5 7.2 7.2 9.3 12 12 12zm0 2.4c-3.2 0-9.6 1.6-9.6 4.8v2.4h19.2v-2.4c0-3.2-6.4-4.8-9.6-4.8z"/>
          </svg>
        </div>
      </div>
      <span class="online-dot"></span>
    </div>
    <div class="header-info">
      <div class="name-line">
        <span class="first-name">FINN</span>
      </div>
      <div class="role-line">
        <span class="role-text" id="typewriter">Web Developer &amp; Designer</span>
        <span class="cursor"></span>
      </div>
      <div class="tag-row">
        <span class="tag">Potsdam, Germany</span>
        <span class="tag">HTML · CSS · Java</span>
        <span class="tag">Open to Work</span>
      </div>
    </div>
  </header>

  <!-- STATS -->
  <div class="section-label">Stats</div>
  <div class="stats-grid">
    <div class="stat-card">
      <span class="stat-number"><span class="count" data-target="2">0</span><span class="stat-plus">+</span></span>
      <span class="stat-label">Years of Experience</span>
    </div>
    <div class="stat-card">
      <span class="stat-number"><span class="count" data-target="6">0</span><span class="stat-plus">+</span></span>
      <span class="stat-label">Completed Projects</span>
    </div>
    <div class="stat-card">
      <span class="stat-number"><span class="count" data-target="2">0</span><span class="stat-plus">+</span></span>
      <span class="stat-label">Happy Clients</span>
    </div>
    <div class="stat-card">
      <span class="stat-number"><span class="count" data-target="3">0</span><span class="stat-plus">+</span></span>
      <span class="stat-label">Technologies</span>
    </div>
  </div>

  <!-- INFO -->
  <div class="two-col">
    <div class="info-card">
      <div class="info-title">About <span>Me</span></div>
      <div class="info-row">
        <span class="info-key">First Name</span>
        <span class="info-val">Finn</span>
      </div>
      <div class="info-row">
        <span class="info-key">Age</span>
        <span class="info-val">15</span>
      </div>
      <div class="info-row">
        <span class="info-key">Nationality</span>
        <span class="info-val">German</span>
      </div>
      <div class="info-row">
        <span class="info-key">Languages</span>
        <span class="info-val lang-flags">
          <span class="flag-item"><img class="flag-img" src="data:image/png;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/4gHYSUNDX1BST0ZJTEUAAQEAAAHIAAAAAAQwAABtbnRyUkdCIFhZWiAH4AABAAEAAAAAAABhY3NwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAQAA9tYAAQAAAADTLQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAlkZXNjAAAA8AAAACRyWFlaAAABFAAAABRnWFlaAAABKAAAABRiWFlaAAABPAAAABR3dHB0AAABUAAAABRyVFJDAAABZAAAAChnVFJDAAABZAAAAChiVFJDAAABZAAAAChjcHJ0AAABjAAAADxtbHVjAAAAAAAAAAEAAAAMZW5VUwAAAAgAAAAcAHMAUgBHAEJYWVogAAAAAAAAb6IAADj1AAADkFhZWiAAAAAAAABimQAAt4UAABjaWFlaIAAAAAAAACSgAAAPhAAAts9YWVogAAAAAAAA9tYAAQAAAADTLXBhcmEAAAAAAAQAAAACZmYAAPKnAAANWQAAE9AAAApbAAAAAAAAAABtbHVjAAAAAAAAAAEAAAAMZW5VUwAAACAAAAAcAEcAbwBvAGcAbABlACAASQBuAGMALgAgADIAMAAxADb/2wBDAAUDBAQEAwUEBAQFBQUGBwwIBwcHBw8LCwkMEQ8SEhEPERETFhwXExQaFRERGCEYGh0dHx8fExciJCIeJBweHx7/2wBDAQUFBQcGBw4ICA4eFBEUHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh7/wAARCAJYA+gDASIAAhEBAxEB/8QAFgABAQEAAAAAAAAAAAAAAAAAAAcI/8QAFBABAAAAAAAAAAAAAAAAAAAAAP/EABYBAQEBAAAAAAAAAAAAAAAAAAAHBf/EABwRAQAABwEAAAAAAAAAAAAAAAAVF2JkoaLh4v/aAAwDAQACEQMRAD8AxkAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAALUMGN0Z4rEr7rT2iotQRujPCV91p7RUWoI3RnhK+609oqLUEbozwlfdae0VFqCN0Z4SvutPaKi1BG6M8JX3WntFRagjdGeEr7rT2iotQRujPCV91p7RUWoI3RnhK+609oqLUEbozwlfdae0VFqCN0Z4SvutPaKi1BG6M8JX3WntFRagjdGeEr7rT2iotQRujPCV91p7RUWoI3RnhK+609oqLUEbozwlfdae0VFqCN0Z4SvutPaKi1BG6M8JX3WntFRagjdGeEr7rT2iotQRujPCV91p7RUWoI3RnhK+609oqLUEbozwlfdae0VFqCN0Z4SvutPaKi1BG6M8JX3WntFRagjdGeEr7rT2iotQRujPCV91p7RUWoI3RnhK+609oqLUEbozwlfdae0VFqCN0Z4SvutPaKi1BG6M8JX3WntFRagjdGeEr7rT2iotQRujPCV91p7RUWoI3RnhK+609oqLUEbozwlfdae0VFqCN0Z4SvutPaKi1BG6M8JX3WntFRagjdGeEr7rT2iotQRujPCV91p7RUWoI3RnhK+609oqLUEbozwlfdae0VFqCN0Z4SvutPaKi1BG6M8JX3WntFRagjdGeEr7rT2iotQRujPCV91p7RUWoI3RnhK+609oqLUEbozwlfdae0VFqCN0Z4SvutPaKi1BG6M8JX3WntFRagjdGeEr7rT2iotQRujPCV91p7RUWoI3RnhK+609oqLUEbozwlfdae0VFqCN0Z4SvutPaKi1BG6M8JX3WntFRagjdGeEr7rT2iotQRujPCV91p7RUWoI3RnhK+609oqLUEbozwlfdae0VFqCN0Z4SvutPaKi1BG6M8JX3WntFRagjdGeEr7rT2iotQRujPCV91p7RUWoI3RnhK+609gDCVgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABtEBCERAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAf//Z" alt="DE"> German</span>
          <span class="flag-item"><img class="flag-img" src="data:image/png;base64,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" alt="GB"> English</span>
        </span>
      </div>
    </div>
    <div class="info-card">
      <div class="info-title">Contact <span>&amp;</span> Links</div>
      <div class="info-row">
        <span class="info-key">Location</span>
        <span class="info-val">Potsdam, Germany</span>
      </div>
      <div class="info-row">
        <span class="info-key">E-Mail</span>
        <span class="info-val"><a href="mailto:finnhesener@gmx.de">finnhesener@gmx.de</a></span>
      </div>
      <div class="info-row">
        <span class="info-key">Gmail</span>
        <span class="info-val"><a href="mailto:finnhesener1@gmail.com">finnhesener1@gmail.com</a></span>
      </div>
    </div>
  </div>

  <div class="section-label">My Skills</div>
  <div class="skills-card">
    <div class="skill-row">
      <span class="skill-name">HTML</span>
      <div class="skill-bar-bg"><div class="skill-bar-fill" data-pct="40"></div></div>
      <span class="skill-pct">40%</span>
    </div>
    <div class="skill-row">
      <span class="skill-name">CSS</span>
      <div class="skill-bar-bg"><div class="skill-bar-fill" data-pct="10"></div></div>
      <span class="skill-pct">10%</span>
    </div>
    <div class="skill-row">
      <span class="skill-name">Java</span>
      <div class="skill-bar-bg"><div class="skill-bar-fill" data-pct="5"></div></div>
      <span class="skill-pct">5%</span>
    </div>
  </div>

  <!-- PROJECTS -->
  <div class="projects-section">
    <div class="section-label">My Projects</div>
    <div class="projects-grid">

      <a class="project-card" href="https://moonmc.carrd.co/#" target="_blank">
        <div class="project-number">01</div>
        <div class="project-body">
          <div class="project-name">MoonMC</div>
          <div class="project-desc">Minecraft-Server Website — Navigation, Team, Ranks & Socials</div>
        </div>
        <div class="project-arrow">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M7 17L17 7M17 7H7M17 7v10"/></svg>
        </div>
      </a>

      <a class="project-card" href="https://whichforwhatfish.my.canva.site/" target="_blank">
        <div class="project-number">02</div>
        <div class="project-body">
          <div class="project-name">Which For What Fish</div>
          <div class="project-desc">Interaktive Fisch-Guide-App — Welcher Köder für welchen Fisch?</div>
        </div>
        <div class="project-arrow">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M7 17L17 7M17 7H7M17 7v10"/></svg>
        </div>
      </a>

      <a class="project-card" href="https://immokalulator.my.canva.site/" target="_blank">
        <div class="project-number">03</div>
        <div class="project-body">
          <div class="project-name">ImmoKalkulator</div>
          <div class="project-desc">Immobilien-Kalkulator — Kaufpreis, Rendite & Finanzierung berechnen</div>
        </div>
        <div class="project-arrow">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M7 17L17 7M17 7H7M17 7v10"/></svg>
        </div>
      </a>

      <a class="project-card" href="https://autoscout.my.canva.site/" target="_blank">
        <div class="project-number">04</div>
        <div class="project-body">
          <div class="project-name">AutoScout Redesign</div>
          <div class="project-desc">Eigenes Redesign-Konzept der AutoScout24-Plattform</div>
        </div>
        <div class="project-arrow">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M7 17L17 7M17 7H7M17 7v10"/></svg>
        </div>
      </a>

    </div>
  </div>

  <!-- CONTACT -->
  <div class="contact-section">
    <div class="section-label">Contact</div>
    <div class="contact-row">
      <a class="contact-btn" href="mailto:finnhesener@gmx.de">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>
        GMX
      </a>
      <a class="contact-btn" id="gmailBtn" href="#" onclick="openGmail(event)">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M21.35 11.1h-9.17v2.73h6.51c-.33 3.81-3.5 5.44-6.5 5.44C8.36 19.27 5 16.25 5 12c0-4.1 3.2-7.27 7.2-7.27 3.09 0 4.9 1.97 4.9 1.97L19 4.72S16.56 2 12.1 2C6.42 2 2.03 6.8 2.03 12c0 5.05 4.13 10 10.22 10 5.35 0 9.25-3.67 9.25-9.09 0-1.15-.15-1.81-.15-1.81z"/></svg>
        Gmail
      </a>
    </div>
  </div>

</div>

<script>
  // ── CURSOR GLOW ──
  const glow = document.getElementById('cursorGlow');
  document.addEventListener('mousemove', e => {
    glow.style.left = e.clientX + 'px';
    glow.style.top  = e.clientY + 'px';
  });

  // ── GMAIL: App first, then browser ──
  function openGmail(e) {
    e.preventDefault();
    const email = 'finnhesener1@gmail.com';
    const isMobile = /Android|iPhone|iPad/i.test(navigator.userAgent);
    if (isMobile) {
      const appUrl = 'googlegmail://co?to=' + email;
      const fallback = 'https://mail.google.com/mail/?view=cm&to=' + email;
      const start = Date.now();
      window.location = appUrl;
      setTimeout(() => {
        if (Date.now() - start < 1500) window.open(fallback, '_blank');
      }, 800);
    } else {
      window.open('https://mail.google.com/mail/?view=cm&to=' + email, '_blank');
    }
  }

  // ── COUNTER ANIMATION ──
  function animateCounters() {
    document.querySelectorAll('.count').forEach(el => {
      const target = parseInt(el.dataset.target);
      const duration = 1400;
      const start = performance.now();
      const step = ts => {
        const p = Math.min((ts - start) / duration, 1);
        const ease = 1 - Math.pow(1 - p, 3);
        el.textContent = Math.floor(ease * target);
        if (p < 1) requestAnimationFrame(step);
        else el.textContent = target;
      };
      requestAnimationFrame(step);
    });
  }

  // ── SKILL BARS ──
  function animateBars() {
    document.querySelectorAll('.skill-bar-fill').forEach(bar => {
      const pct = bar.dataset.pct;
      setTimeout(() => { bar.style.width = pct + '%'; }, 100);
    });
  }

  const observed = new Set();
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting && !observed.has(e.target)) {
        observed.add(e.target);
        if (e.target.classList.contains('stats-grid')) animateCounters();
        if (e.target.classList.contains('skills-card')) animateBars();
      }
    });
  }, { threshold: 0.2 });

  document.querySelectorAll('.stats-grid, .skills-card').forEach(el => observer.observe(el));

  // ── TYPEWRITER ──
  const roles = ['Web Developer', 'UI Designer', 'Frontend Learner', 'Creative Coder'];
  let ri = 0, ci = 0, deleting = false;
  const tw = document.getElementById('typewriter');
  function type() {
    const role = roles[ri];
    if (!deleting) {
      tw.textContent = role.slice(0, ++ci);
      if (ci === role.length) { deleting = true; setTimeout(type, 1800); return; }
    } else {
      tw.textContent = role.slice(0, --ci);
      if (ci === 0) { deleting = false; ri = (ri + 1) % roles.length; }
    }
    setTimeout(type, deleting ? 60 : 100);
  }
  type();
</script>
</body>
</html>
