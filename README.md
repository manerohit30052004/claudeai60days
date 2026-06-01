<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>60-Day Claude AI Challenge — Rohit Mane</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #070a0f;
    --surface: #0d1117;
    --card: #111820;
    --border: #1e2d3d;
    --accent: #00d4ff;
    --accent2: #7c3aed;
    --accent3: #10b981;
    --gold: #f59e0b;
    --text: #e2e8f0;
    --muted: #64748b;
    --mono: 'Space Mono', monospace;
    --sans: 'Syne', sans-serif;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    min-height: 100vh;
    overflow-x: hidden;
    position: relative;
  }

  /* Animated grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
    animation: gridPulse 8s ease-in-out infinite;
  }

  @keyframes gridPulse {
    0%, 100% { opacity: 0.4; }
    50% { opacity: 1; }
  }

  /* Floating orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    pointer-events: none;
    z-index: 0;
    animation: float 12s ease-in-out infinite;
  }
  .orb1 { width: 400px; height: 400px; background: rgba(0,212,255,0.06); top: -100px; right: -100px; animation-delay: 0s; }
  .orb2 { width: 300px; height: 300px; background: rgba(124,58,237,0.08); bottom: 200px; left: -80px; animation-delay: -4s; }
  .orb3 { width: 250px; height: 250px; background: rgba(16,185,129,0.05); bottom: -50px; right: 30%; animation-delay: -8s; }

  @keyframes float {
    0%, 100% { transform: translateY(0) scale(1); }
    50% { transform: translateY(-30px) scale(1.05); }
  }

  .wrapper {
    position: relative;
    z-index: 1;
    max-width: 900px;
    margin: 0 auto;
    padding: 60px 24px 100px;
  }

  /* ── HERO ── */
  .hero {
    text-align: center;
    padding: 60px 0 40px;
    animation: fadeUp 0.8s ease both;
  }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(0,212,255,0.08);
    border: 1px solid rgba(0,212,255,0.25);
    border-radius: 100px;
    padding: 6px 18px;
    font-family: var(--mono);
    font-size: 12px;
    color: var(--accent);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 28px;
    animation: fadeUp 0.8s ease 0.1s both;
  }

  .badge::before {
    content: '';
    width: 6px; height: 6px;
    background: var(--accent);
    border-radius: 50%;
    animation: blink 1.4s ease-in-out infinite;
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.2; }
  }

  .hero h1 {
    font-family: var(--sans);
    font-size: clamp(36px, 8vw, 72px);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -0.02em;
    background: linear-gradient(135deg, #ffffff 0%, var(--accent) 50%, var(--accent2) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 10px;
    animation: fadeUp 0.8s ease 0.2s both;
  }

  .hero-sub {
    font-family: var(--mono);
    font-size: 14px;
    color: var(--muted);
    letter-spacing: 0.08em;
    margin-bottom: 24px;
    animation: fadeUp 0.8s ease 0.3s both;
  }

  .hero-sub span { color: var(--accent3); }

  .hero-desc {
    font-size: 17px;
    color: #94a3b8;
    max-width: 560px;
    margin: 0 auto 40px;
    line-height: 1.65;
    animation: fadeUp 0.8s ease 0.4s both;
  }

  /* Stats row */
  .stats-row {
    display: flex;
    justify-content: center;
    gap: 16px;
    flex-wrap: wrap;
    margin-bottom: 48px;
    animation: fadeUp 0.8s ease 0.5s both;
  }

  .stat-pill {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 12px 24px;
    text-align: center;
    min-width: 110px;
    transition: border-color 0.3s, transform 0.2s;
  }

  .stat-pill:hover {
    border-color: var(--accent);
    transform: translateY(-3px);
  }

  .stat-pill .num {
    font-family: var(--mono);
    font-size: 26px;
    font-weight: 700;
    color: var(--accent);
    display: block;
  }

  .stat-pill .lbl {
    font-size: 11px;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin-top: 2px;
  }

  /* ── DIVIDER ── */
  .divider {
    display: flex;
    align-items: center;
    gap: 16px;
    margin: 48px 0 40px;
    animation: fadeUp 0.8s ease 0.6s both;
  }

  .divider::before, .divider::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
  }

  .divider span {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    white-space: nowrap;
  }

  /* ── SECTION HEADER ── */
  .section-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 24px;
  }

  .section-header .tag {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--accent);
    background: rgba(0,212,255,0.08);
    border: 1px solid rgba(0,212,255,0.2);
    padding: 3px 10px;
    border-radius: 4px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  .section-header h2 {
    font-size: 22px;
    font-weight: 700;
    color: #fff;
  }

  /* ── ABOUT CARD ── */
  .about-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 32px;
    position: relative;
    overflow: hidden;
    margin-bottom: 40px;
    animation: fadeUp 0.8s ease 0.6s both;
  }

  .about-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent2), var(--accent), var(--accent3));
  }

  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 24px;
  }

  @media (max-width: 600px) {
    .about-grid { grid-template-columns: 1fr; }
  }

  .about-item { display: flex; flex-direction: column; gap: 4px; }

  .about-item .label {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 0.12em;
    text-transform: uppercase;
  }

  .about-item .value {
    font-size: 15px;
    color: var(--text);
    font-weight: 600;
  }

  .about-item .value.accent { color: var(--accent); }
  .about-item .value.green { color: var(--accent3); }
  .about-item .value.gold { color: var(--gold); }

  /* ── GOALS ── */
  .goals-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 16px;
    margin-bottom: 40px;
    animation: fadeUp 0.8s ease 0.7s both;
  }

  .goal-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px;
    transition: border-color 0.3s, transform 0.25s;
    position: relative;
    overflow: hidden;
  }

  .goal-card:hover {
    transform: translateY(-4px);
    border-color: rgba(0,212,255,0.4);
  }

  .goal-card .icon {
    font-size: 28px;
    margin-bottom: 14px;
    display: block;
  }

  .goal-card h3 {
    font-size: 15px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 8px;
  }

  .goal-card p {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.6;
  }

  .goal-card .num-tag {
    position: absolute;
    top: 16px; right: 16px;
    font-family: var(--mono);
    font-size: 10px;
    color: rgba(0,212,255,0.4);
    letter-spacing: 0.1em;
  }

  /* ── TRACKER ── */
  .tracker-section {
    margin-bottom: 40px;
    animation: fadeUp 0.8s ease 0.8s both;
  }

  .week-block {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px;
    margin-bottom: 12px;
    transition: border-color 0.3s;
  }

  .week-block:hover { border-color: rgba(0,212,255,0.3); }

  .week-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 16px;
  }

  .week-header .title {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--accent);
    font-weight: 700;
  }

  .week-header .dates {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
  }

  .day-grid {
    display: flex;
    gap: 6px;
    flex-wrap: wrap;
  }

  .day {
    width: 36px;
    height: 36px;
    border-radius: 8px;
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    transition: all 0.2s;
    cursor: default;
  }

  .day.done {
    background: rgba(16,185,129,0.12);
    border-color: rgba(16,185,129,0.4);
    color: var(--accent3);
  }

  .day.active {
    background: rgba(0,212,255,0.12);
    border-color: var(--accent);
    color: var(--accent);
    box-shadow: 0 0 12px rgba(0,212,255,0.2);
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { box-shadow: 0 0 8px rgba(0,212,255,0.2); }
    50% { box-shadow: 0 0 18px rgba(0,212,255,0.5); }
  }

  /* ── RULES ── */
  .rules-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-bottom: 40px;
    animation: fadeUp 0.8s ease 0.9s both;
  }

  .rules-list li {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 14px 18px;
    display: flex;
    align-items: flex-start;
    gap: 12px;
    font-size: 14px;
    color: #94a3b8;
    transition: border-color 0.3s, color 0.3s;
  }

  .rules-list li:hover {
    border-color: rgba(0,212,255,0.3);
    color: var(--text);
  }

  .rules-list .marker {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--accent);
    background: rgba(0,212,255,0.08);
    border: 1px solid rgba(0,212,255,0.2);
    padding: 2px 8px;
    border-radius: 4px;
    white-space: nowrap;
    flex-shrink: 0;
    margin-top: 1px;
  }

  /* ── TOOLS ── */
  .tools-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-bottom: 40px;
    animation: fadeUp 0.8s ease 1s both;
  }

  .tool-chip {
    background: rgba(124,58,237,0.1);
    border: 1px solid rgba(124,58,237,0.25);
    border-radius: 8px;
    padding: 8px 16px;
    font-family: var(--mono);
    font-size: 12px;
    color: #a78bfa;
    transition: all 0.2s;
  }

  .tool-chip:hover {
    background: rgba(124,58,237,0.2);
    border-color: rgba(124,58,237,0.5);
    transform: translateY(-2px);
  }

  /* ── PROGRESS BAR ── */
  .progress-section {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 28px;
    margin-bottom: 40px;
    animation: fadeUp 0.8s ease 1s both;
  }

  .progress-label {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 14px;
  }

  .progress-label span:first-child {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--text);
    font-weight: 700;
  }

  .progress-label span:last-child {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--accent);
  }

  .progress-bar {
    width: 100%;
    height: 8px;
    background: rgba(255,255,255,0.05);
    border-radius: 100px;
    overflow: hidden;
  }

  .progress-fill {
    height: 100%;
    border-radius: 100px;
    background: linear-gradient(90deg, var(--accent2), var(--accent));
    width: 1.67%;
    animation: fillBar 1.5s ease 1.2s both;
    position: relative;
  }

  .progress-fill::after {
    content: '';
    position: absolute;
    top: 0; right: 0;
    width: 20px; height: 100%;
    background: rgba(255,255,255,0.4);
    border-radius: 100px;
    animation: shimmer 2s ease-in-out infinite;
  }

  @keyframes fillBar {
    from { width: 0; }
    to { width: 1.67%; }
  }

  @keyframes shimmer {
    0%, 100% { opacity: 0; }
    50% { opacity: 1; }
  }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    padding: 40px 0 0;
    animation: fadeUp 0.8s ease 1.1s both;
  }

  .footer-quote {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--muted);
    letter-spacing: 0.05em;
    border-left: 2px solid var(--accent);
    padding-left: 16px;
    text-align: left;
    max-width: 500px;
    margin: 0 auto 24px;
    line-height: 1.7;
  }

  .footer-sig {
    font-family: var(--mono);
    font-size: 11px;
    color: rgba(0,212,255,0.4);
    letter-spacing: 0.15em;
    text-transform: uppercase;
  }

  .footer-sig span { color: var(--accent); }

  /* ── TERMINAL CURSOR ── */
  .cursor {
    display: inline-block;
    width: 10px;
    height: 1.1em;
    background: var(--accent);
    vertical-align: text-bottom;
    animation: blink 1s step-start infinite;
    border-radius: 1px;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── TERMINAL BLOCK ── */
  .terminal {
    background: #0a0e14;
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px 24px;
    margin-bottom: 40px;
    font-family: var(--mono);
    font-size: 13px;
    line-height: 1.8;
    animation: fadeUp 0.8s ease 0.5s both;
    position: relative;
    overflow: hidden;
  }

  .terminal::before {
    content: '● ● ●';
    display: block;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 4px;
    margin-bottom: 16px;
    opacity: 0.5;
  }

  .terminal .prompt { color: var(--accent3); }
  .terminal .cmd { color: var(--text); }
  .terminal .comment { color: var(--muted); }
  .terminal .output { color: var(--accent); }
  .terminal .warn { color: var(--gold); }
</style>
</head>
<body>

<div class="orb orb1"></div>
<div class="orb orb2"></div>
<div class="orb orb3"></div>

<div class="wrapper">

  <!-- HERO -->
  <div class="hero">
    <div class="badge">🚀 Day 01 of 60 — June 1, 2026</div>
    <h1>60-Day Claude AI<br>Challenge</h1>
    <p class="hero-sub">Started by <span>Rohit Mane</span> · June 1 – July 30, 2026</p>
    <p class="hero-desc">
      One AI challenge. Sixty days. Zero excuses.<br>
      Building real skills, real projects, and real results — one Claude session at a time.
    </p>

    <div class="stats-row">
      <div class="stat-pill">
        <span class="num">60</span>
        <span class="lbl">Total Days</span>
      </div>
      <div class="stat-pill">
        <span class="num">01</span>
        <span class="lbl">Days Done</span>
      </div>
      <div class="stat-pill">
        <span class="num">59</span>
        <span class="lbl">Days Left</span>
      </div>
      <div class="stat-pill">
        <span class="num" style="color:var(--gold)">1.67%</span>
        <span class="lbl">Complete</span>
      </div>
    </div>
  </div>

  <!-- TERMINAL -->
  <div class="terminal">
    <span class="prompt">rohit@masters-union:~$</span> <span class="cmd">init challenge --name "60-Day Claude AI" --start "2026-06-01"</span><br>
    <span class="comment"># Initializing challenge parameters...</span><br>
    <span class="output">✔ Challenge registered: Rohit Mane</span><br>
    <span class="output">✔ Start date: June 1, 2026</span><br>
    <span class="output">✔ End date: July 30, 2026</span><br>
    <span class="output">✔ Daily commitment: 1 session minimum</span><br>
    <span class="warn">⚡ Status: ACTIVE — Day 1 of 60</span><br>
    <span class="prompt">rohit@masters-union:~$</span> <span class="cursor"></span>
  </div>

  <!-- ABOUT -->
  <div class="section-header">
    <span class="tag">// info</span>
    <h2>About This Challenge</h2>
  </div>

  <div class="about-card">
    <div class="about-grid">
      <div class="about-item">
        <span class="label">Challenger</span>
        <span class="value accent">Rohit Mane</span>
      </div>
      <div class="about-item">
        <span class="label">Challenge</span>
        <span class="value">60-Day Claude AI Challenge</span>
      </div>
      <div class="about-item">
        <span class="label">Start Date</span>
        <span class="value green">June 1, 2026</span>
      </div>
      <div class="about-item">
        <span class="label">End Date</span>
        <span class="value green">July 30, 2026</span>
      </div>
      <div class="about-item">
        <span class="label">Platform</span>
        <span class="value">Claude.ai (Anthropic)</span>
      </div>
      <div class="about-item">
        <span class="label">Category</span>
        <span class="value gold">AI · Productivity · Growth</span>
      </div>
    </div>
  </div>

  <!-- GOALS -->
  <div class="section-header">
    <span class="tag">// goals</span>
    <h2>What I'm Building For</h2>
  </div>

  <div class="goals-grid">
    <div class="goal-card">
      <span class="icon">🧠</span>
      <span class="num-tag">01</span>
      <h3>AI Mastery</h3>
      <p>Master prompting, tool use, and creative AI workflows that deliver real, measurable output daily.</p>
    </div>
    <div class="goal-card">
      <span class="icon">📈</span>
      <span class="num-tag">02</span>
      <h3>Sales Performance</h3>
      <p>Apply AI to sales enablement, lead research, pitch prep, and call support at Masters' Union.</p>
    </div>
    <div class="goal-card">
      <span class="icon">🎨</span>
      <span class="num-tag">03</span>
      <h3>Creative Production</h3>
      <p>Build marketing assets, ad concepts, and content pieces using AI as my co-creator.</p>
    </div>
    <div class="goal-card">
      <span class="icon">🚀</span>
      <span class="num-tag">04</span>
      <h3>Startup Thinking</h3>
      <p>Validate and document ideas like SalesVaani — use Claude to build MVPs and business cases.</p>
    </div>
    <div class="goal-card">
      <span class="icon">📝</span>
      <span class="num-tag">05</span>
      <h3>Public Logging</h3>
      <p>Document every day's learning publicly. Build accountability, share knowledge, grow in the open.</p>
    </div>
    <div class="goal-card">
      <span class="icon">⚡</span>
      <span class="num-tag">06</span>
      <h3>Discipline Streak</h3>
      <p>Zero missed days. Make AI a non-negotiable daily habit the way great athletes train without exception.</p>
    </div>
  </div>

  <!-- RULES -->
  <div class="section-header">
    <span class="tag">// rules</span>
    <h2>The Rules</h2>
  </div>

  <ul class="rules-list">
    <li>
      <span class="marker">R-01</span>
      One meaningful Claude session every single day — no skipping, no exceptions, for 60 consecutive days.
    </li>
    <li>
      <span class="marker">R-02</span>
      Each session must produce a real output: a document, analysis, creative asset, code, or actionable plan.
    </li>
    <li>
      <span class="marker">R-03</span>
      Document what was built each day with a short log entry (title + 1-line summary + key learning).
    </li>
    <li>
      <span class="marker">R-04</span>
      Apply learnings to real work — sales, content, or personal projects — not just hypothetical exercises.
    </li>
    <li>
      <span class="marker">R-05</span>
      Share progress publicly on LinkedIn or GitHub every week to maintain accountability.
    </li>
    <li>
      <span class="marker">R-06</span>
      Use at least 3 different Claude use-cases across the 60 days (writing, research, code, creative, strategy).
    </li>
  </ul>

  <!-- TRACKER -->
  <div class="section-header">
    <span class="tag">// tracker</span>
    <h2>Day Tracker</h2>
  </div>

  <div class="tracker-section" id="tracker"></div>

  <!-- PROGRESS -->
  <div class="progress-section">
    <div class="progress-label">
      <span>Overall Progress</span>
      <span id="pct-label">Day 1 / 60</span>
    </div>
    <div class="progress-bar">
      <div class="progress-fill" id="progress-fill"></div>
    </div>
  </div>

  <!-- TOOLS -->
  <div class="section-header">
    <span class="tag">// stack</span>
    <h2>Tools &amp; Use Cases</h2>
  </div>

  <div class="tools-grid">
    <div class="tool-chip">Claude.ai</div>
    <div class="tool-chip">Prompt Engineering</div>
    <div class="tool-chip">Sales Enablement</div>
    <div class="tool-chip">Content Creation</div>
    <div class="tool-chip">HTML / CSS</div>
    <div class="tool-chip">Research &amp; Analysis</div>
    <div class="tool-chip">Startup Ideation</div>
    <div class="tool-chip">Creative Marketing</div>
    <div class="tool-chip">AI Artifacts</div>
    <div class="tool-chip">Data Summarization</div>
    <div class="tool-chip">Script Writing</div>
    <div class="tool-chip">Strategic Planning</div>
  </div>

  <div class="divider"><span>// challenge log</span></div>

  <!-- DAILY LOG -->
  <div class="section-header">
    <span class="tag">// log</span>
    <h2>Daily Log</h2>
  </div>

  <div class="about-card" style="animation-delay: 1s;">
    <div style="font-family:var(--mono); font-size:13px; line-height:2;">
      <div style="color:var(--accent); margin-bottom:16px; font-size:15px; font-weight:700;">📅 Day 01 — June 1, 2026</div>
      <div style="color:var(--muted); margin-bottom:8px;">Task: Built animated 60-Day Claude AI Challenge README</div>
      <div style="color:var(--muted); margin-bottom:8px;">Output: HTML README with day tracker, stats, goals &amp; progress bar</div>
      <div style="color:var(--accent3);">Key Learning: Claude can produce production-quality UI from a single prompt — design intent matters as much as technical output.</div>
      <br>
      <div style="color:var(--muted); font-style:italic; font-size:11px;">// Days 02–60 will be added here as the challenge progresses</div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="footer-quote">
      "The people who are crazy enough to think they can change the world are the ones who do."<br>
      — Steve Jobs
    </div>
    <br>
    <p class="footer-sig">
      Built by <span>Rohit Mane</span> · Started <span>June 1, 2026</span> · 60 Days of Claude AI
    </p>
  </div>

</div>

<script>
  // Build the day tracker — 60 days across 9 weeks
  const tracker = document.getElementById('tracker');
  const startDate = new Date('2026-06-01');
  const today = new Date('2026-06-01');
  const totalDays = 60;

  const daysDone = Math.floor((today - startDate) / (1000*60*60*24)) + 1;

  const weeksData = [
    { label: 'WEEK 01', range: 'Jun 01 – Jun 07', days: [1,2,3,4,5,6,7] },
    { label: 'WEEK 02', range: 'Jun 08 – Jun 14', days: [8,9,10,11,12,13,14] },
    { label: 'WEEK 03', range: 'Jun 15 – Jun 21', days: [15,16,17,18,19,20,21] },
    { label: 'WEEK 04', range: 'Jun 22 – Jun 28', days: [22,23,24,25,26,27,28] },
    { label: 'WEEK 05', range: 'Jun 29 – Jul 05', days: [29,30,31,32,33,34,35] },
    { label: 'WEEK 06', range: 'Jul 06 – Jul 12', days: [36,37,38,39,40,41,42] },
    { label: 'WEEK 07', range: 'Jul 13 – Jul 19', days: [43,44,45,46,47,48,49] },
    { label: 'WEEK 08', range: 'Jul 20 – Jul 26', days: [50,51,52,53,54,55,56] },
    { label: 'WEEK 09', range: 'Jul 27 – Jul 30', days: [57,58,59,60] },
  ];

  weeksData.forEach(week => {
    const block = document.createElement('div');
    block.className = 'week-block';
    block.innerHTML = `
      <div class="week-header">
        <span class="title">${week.label}</span>
        <span class="dates">${week.range}</span>
      </div>
      <div class="day-grid">
        ${week.days.map(d => {
          let cls = 'day';
          if (d < daysDone) cls += ' done';
          else if (d === daysDone) cls += ' active';
          return `<div class="${cls}">${String(d).padStart(2,'0')}</div>`;
        }).join('')}
      </div>
    `;
    tracker.appendChild(block);
  });

  // Animate progress bar after load
  const pct = ((daysDone / totalDays) * 100).toFixed(2);
  setTimeout(() => {
    document.getElementById('progress-fill').style.width = pct + '%';
    document.getElementById('pct-label').textContent = `Day ${daysDone} / ${totalDays}`;
  }, 1400);
</script>
</body>
</html>
