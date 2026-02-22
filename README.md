<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Amanjeet Sharma · dev</title>
  <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    :root {
      --bg: #0a0c0f;
      --surface: #101318;
      --border: #2a2f3a;
      --green: #2bde8f;
      --cyan: #4db5ff;
      --dim: #6b7482;
      --text: #e1e7f0;
      --glow: rgba(43, 222, 143, 0.15);
    }

    body {
      background: var(--bg);
      font-family: 'JetBrains Mono', monospace;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 24px 16px;
      color: var(--text);
    }

    /* terminal window */
    .window {
      width: 100%;
      max-width: 700px;
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 18px 18px 16px 16px;
      box-shadow: 0 20px 35px -12px rgba(0,0,0,0.8), 0 0 0 1px rgba(43,222,143,0.1);
      backdrop-filter: blur(2px);
    }

    /* window title bar — minimal, just dots and path */
    .title-bar {
      background: #1c2128;
      padding: 12px 18px;
      border-radius: 16px 16px 0 0;
      display: flex;
      align-items: center;
      gap: 10px;
      border-bottom: 1px solid var(--border);
    }

    .dots {
      display: flex;
      gap: 8px;
      margin-right: 12px;
    }
    .dot {
      width: 13px;
      height: 13px;
      border-radius: 50%;
      background: #4f5a66;
    }
    .dot.red { background: #ff5f6d; }
    .dot.yellow { background: #ffc107; }
    .dot.green { background: #2bde8f; }

    .path {
      color: var(--dim);
      font-size: 12px;
      letter-spacing: 0.3px;
      background: #262d36;
      padding: 4px 12px;
      border-radius: 40px;
      border: 1px solid #364153;
    }
    .path span {
      color: var(--green);
      font-weight: 500;
    }

    .main {
      padding: 36px 30px 32px;
    }

    /* intro line: command + status */
    .intro-line {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 30px;
      font-size: 13px;
      background: rgba(43,222,143,0.05);
      padding: 8px 16px;
      border-radius: 40px;
      border: 1px solid #28323e;
      width: fit-content;
    }
    .prompt {
      color: var(--green);
      font-weight: 500;
    }
    .status-badge {
      display: flex;
      align-items: center;
      gap: 6px;
      background: #1e282f;
      padding: 4px 12px;
      border-radius: 30px;
    }
    .pulse {
      width: 9px;
      height: 9px;
      background: var(--green);
      border-radius: 50%;
      box-shadow: 0 0 10px var(--green);
      animation: pulse 2s infinite;
    }
    @keyframes pulse { 0% { opacity:1; transform:scale(1); } 50% { opacity:0.6; transform:scale(1.3); } }

    /* name + handle – clean and technical */
    .identity {
      margin-bottom: 30px;
    }
    .name {
      font-size: 32px;
      font-weight: 700;
      letter-spacing: -0.5px;
      line-height: 1.1;
      color: #f0f6fc;
    }
    .name .accent {
      color: var(--green);
      background: rgba(43,222,143,0.1);
      padding: 0 4px;
    }
    .handle {
      font-size: 13px;
      color: var(--dim);
      margin-top: 6px;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .handle .at {
      color: var(--cyan);
    }
    .handle .divider {
      color: #364153;
    }

    /* tech stack — small badges, compact */
    .tech-section {
      margin: 28px 0 24px;
    }
    .tech-label {
      font-size: 11px;
      text-transform: uppercase;
      color: var(--dim);
      letter-spacing: 1.5px;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .tech-label i {
      color: var(--green);
      font-style: normal;
    }
    .badge-group {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }
    .badge {
      background: #1e2630;
      border: 1px solid #2f3a48;
      color: #cdd9e6;
      padding: 6px 16px;
      border-radius: 40px;
      font-size: 12px;
      font-weight: 500;
      letter-spacing: 0.2px;
      transition: 0.15s ease;
      cursor: default;
    }
    .badge:hover {
      border-color: var(--green);
      background: #28323f;
      color: white;
      box-shadow: 0 0 10px var(--glow);
    }

    /* social links — minimal, command‑line style */
    .links {
      margin: 24px 0 16px;
      display: flex;
      flex-direction: column;
      gap: 2px;
    }
    .link-row {
      display: flex;
      align-items: center;
      padding: 6px 0;
      border-bottom: 1px dashed #28323e;
      font-size: 13px;
    }
    .link-row .arrow {
      color: var(--green);
      margin-right: 10px;
      font-weight: 500;
      width: 18px;
      text-align: center;
    }
    .link-row a {
      color: var(--text);
      text-decoration: none;
      display: flex;
      align-items: center;
      gap: 8px;
      transition: 0.1s;
      flex-wrap: wrap;
    }
    .link-row a:hover {
      color: var(--cyan);
    }
    .link-meta {
      color: var(--dim);
      font-size: 11px;
      background: #1c2128;
      padding: 2px 8px;
      border-radius: 30px;
      margin-left: 8px;
    }

    .footer-cmd {
      margin-top: 30px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-top: 1px solid #28323e;
      padding-top: 20px;
      font-size: 12px;
      color: var(--dim);
    }
    .footer-cmd .cursor {
      display: inline-block;
      width: 8px;
      height: 16px;
      background: var(--green);
      vertical-align: middle;
      margin-left: 6px;
      animation: blink 1s step-end infinite;
    }
    @keyframes blink { 50% { opacity: 0; } }

    /* responsive */
    @media (max-width: 450px) {
      .main { padding: 24px 18px; }
      .name { font-size: 26px; }
      .link-row { flex-wrap: wrap; }
    }
  </style>
</head>
<body>
<div class="window">

  <!-- window bar : only dots + path (ultra clean) -->
  <div class="title-bar">
    <div class="dots">
      <div class="dot red"></div>
      <div class="dot yellow"></div>
      <div class="dot green"></div>
    </div>
    <div class="path"><span>~/dev</span>/amanjeet</div>
  </div>

  <div class="main">
    <!-- top line with prompt and live status (techie) -->
    <div class="intro-line">
      <span class="prompt">$></span>
      <span>whoami</span>
      <div class="status-badge">
        <div class="pulse"></div>
        <span>online /* 0.0.1 */</span>
      </div>
    </div>

    <!-- identity – clean, no extra "builder" -->
    <div class="identity">
      <div class="name">
        <span class="accent">Amanjeet</span> Sharma
      </div>
      <div class="handle">
        <span class="at">⎇</span> amanjeet@dev <span class="divider">|</span> <span>full‑stack · cs</span>
      </div>
    </div>

    <!-- tech stack : presented like a compact manifest (short & vibe) -->
    <div class="tech-section">
      <div class="tech-label">
        <i>⚙️</i> STACK // init
      </div>
      <div class="badge-group">
        <span class="badge">Java</span>
        <span class="badge">JavaScript</span>
        <span class="badge">C++</span>
        <span class="badge">React</span>
        <span class="badge">Node.js</span>
        <span class="badge">Express</span>
        <span class="badge">MongoDB</span>
        <span class="badge">MySQL</span>
        <span class="badge">Tailwind</span>
        <span class="badge">Bootstrap</span>
      </div>
    </div>

    <!-- social + contact with minimal, pipeline style -->
    <div class="links">
      <div class="link-row">
        <span class="arrow">↳</span>
        <a href="https://linkedin.com/in/amanjeet-sharma-20b75a252" target="_blank">
          <span>linkedin</span>
          <span class="link-meta">in/amanjeet</span>
        </a>
      </div>
      <div class="link-row">
        <span class="arrow">↳</span>
        <a href="https://github.com/AmanjeetSharma" target="_blank">
          <span>github</span>
          <span class="link-meta">AmanjeetSharma</span>
        </a>
      </div>
      <div class="link-row">
        <span class="arrow">↳</span>
        <a href="mailto:amansharma23503@gmail.com">
          <span>mail</span>
          <span class="link-meta">amansharma23503</span>
        </a>
      </div>
    </div>

    <!-- footer line: command + thanks (replaces old footer) -->
    <div class="footer-cmd">
      <div><span style="color: var(--green);">$</span> echo "$GREET"</div>
      <div>thanks, visitor <span class="cursor"></span></div>
    </div>
  </div>
</div>
</body>
</html>
