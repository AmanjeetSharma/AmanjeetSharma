<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Amanjeet Sharma</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600;700&family=Orbitron:wght@800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0d1117;
    --surface: #161b22;
    --border: #21262d;
    --green: #3fb950;
    --cyan: #58a6ff;
    --dim: #484f58;
    --text: #c9d1d9;
    --heading: #e6edf3;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    padding: 48px 20px;
  }

  .card {
    width: 100%;
    max-width: 720px;
  }

  .win-bar {
    background: var(--surface);
    border: 1px solid var(--border);
    border-bottom: none;
    border-radius: 10px 10px 0 0;
    padding: 11px 16px;
    display: flex;
    align-items: center;
    gap: 7px;
  }
  .dot { width: 12px; height: 12px; border-radius: 50%; flex-shrink: 0; }
  .dr { background: #ff5f57; }
  .dy { background: #febc2e; }
  .dg { background: #28c840; }
  .win-title {
    flex: 1;
    text-align: center;
    font-size: 11px;
    color: var(--dim);
    letter-spacing: 1px;
  }

  .body {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 0 0 10px 10px;
    padding: 36px 40px 40px;
  }

  .hero {
    text-align: center;
    margin-bottom: 32px;
    opacity: 0;
    animation: fadeUp 0.6s ease 0.1s forwards;
  }

  .gif-wrap { margin-bottom: 20px; }
  .gif-wrap img {
    width: 200px;
    border-radius: 8px;
    border: 1px solid var(--border);
  }

  .name {
    font-family: 'Orbitron', sans-serif;
    font-size: clamp(18px, 3.5vw, 28px);
    font-weight: 800;
    color: var(--heading);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 8px;
  }
  .name .hi { color: var(--green); }

  .tagline {
    font-size: 11px;
    color: var(--dim);
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  .cursor {
    display: inline-block;
    width: 2px; height: 13px;
    background: var(--green);
    vertical-align: middle;
    margin-left: 2px;
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 50% { opacity: 0; } }

  hr {
    border: none;
    height: 1px;
    background: var(--border);
    margin: 26px 0;
  }

  .cmd-line {
    font-size: 13px;
    margin-bottom: 16px;
    opacity: 0;
    animation: fadeUp 0.4s ease forwards;
  }
  .p { color: var(--green); margin-right: 8px; }
  .c { color: var(--cyan); }

  .section-label {
    font-size: 10px;
    color: var(--dim);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 10px;
    opacity: 0;
    animation: fadeUp 0.4s ease forwards;
  }

  .badge-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-bottom: 18px;
  }

  .badge-img {
    height: 22px;
    border-radius: 3px;
    opacity: 0;
    animation: popIn 0.35s cubic-bezier(0.34,1.56,0.64,1) forwards;
    transition: transform 0.18s ease, filter 0.18s ease;
    cursor: default;
  }
  .badge-img:hover {
    transform: translateY(-3px) scale(1.1);
    filter: brightness(1.2) drop-shadow(0 4px 8px rgba(88,166,255,0.35));
  }

  .social-list { display: flex; flex-direction: column; gap: 8px; }

  .social-item {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 8px 10px;
    border-radius: 6px;
    text-decoration: none;
    opacity: 0;
    animation: fadeUp 0.4s ease forwards;
    transition: background 0.15s;
  }
  .social-item:hover { background: rgba(255,255,255,0.04); }
  .social-item:hover .surl { color: var(--cyan); }

  .sbadge { height: 20px; }
  .sarrow { color: var(--dim); font-size: 11px; }
  .surl { font-size: 12px; color: var(--text); transition: color 0.15s; }

  .footer {
    margin-top: 26px;
    text-align: center;
    font-size: 11px;
    color: var(--dim);
    letter-spacing: 1.5px;
    opacity: 0;
    animation: fadeUp 0.4s ease forwards;
  }

  .status {
    display: inline-block;
    width: 7px; height: 7px;
    background: var(--green);
    border-radius: 50%;
    margin-right: 6px;
    vertical-align: middle;
    box-shadow: 0 0 6px var(--green);
    animation: pulse 2.5s ease-in-out infinite;
  }
  @keyframes pulse {
    0%,100% { opacity:1; transform:scale(1); }
    50% { opacity:0.5; transform:scale(1.3); }
  }

  @keyframes fadeUp {
    from { opacity:0; transform:translateY(6px); }
    to   { opacity:1; transform:translateY(0); }
  }
  @keyframes popIn {
    from { opacity:0; transform:scale(0.8); }
    to   { opacity:1; transform:scale(1); }
  }

  /* Delays */
  .d01{animation-delay:0.10s} .d02{animation-delay:0.20s} .d03{animation-delay:0.30s}
  .d04{animation-delay:0.40s} .d05{animation-delay:0.50s} .d06{animation-delay:0.58s}
  .d07{animation-delay:0.66s} .d08{animation-delay:0.74s} .d09{animation-delay:0.82s}
  .d10{animation-delay:0.90s} .d11{animation-delay:0.98s} .d12{animation-delay:1.06s}
  .d13{animation-delay:1.14s} .d14{animation-delay:1.22s} .d15{animation-delay:1.30s}
  .d16{animation-delay:1.38s} .d17{animation-delay:1.46s} .d18{animation-delay:1.54s}
  .d19{animation-delay:1.62s} .d20{animation-delay:1.70s} .d21{animation-delay:1.78s}
  .d22{animation-delay:1.86s} .d23{animation-delay:1.94s} .d24{animation-delay:2.02s}
  .d25{animation-delay:2.10s}

  @media(max-width:520px){
    .body { padding: 24px 20px; }
    .name { font-size: 16px; }
  }
</style>
</head>
<body>
<div class="card">

  <div class="win-bar">
    <div class="dot dr"></div>
    <div class="dot dy"></div>
    <div class="dot dg"></div>
    <div class="win-title">amanjeet@dev — profile.md</div>
  </div>

  <div class="body">

    <!-- HERO -->
    <div class="hero d01">
      <div class="gif-wrap">
        <img src="https://media.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif" alt="Coding"/>
      </div>
      <div class="name">💻 <span class="hi">Hi,</span> I'm Amanjeet Sharma! 👨‍💻<span class="cursor"></span></div>
      <div class="tagline">Full Stack Developer &nbsp;·&nbsp; CS Undergrad &nbsp;·&nbsp; Builder</div>
    </div>

    <hr/>

    <!-- TECH STACK -->
    <div class="cmd-line d02"><span class="p">$</span><span class="c">ls tech_stack/</span></div>

    <div class="section-label d03">🔤 &nbsp;Languages</div>
    <div class="badge-grid">
      <img class="badge-img d04" src="https://img.shields.io/badge/-Java-007396?style=flat-square&logo=java&logoColor=white" alt="Java"/>
      <img class="badge-img d05" src="https://img.shields.io/badge/-JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black" alt="JavaScript"/>
      <img class="badge-img d06" src="https://img.shields.io/badge/-C++-00599C?style=flat-square&logo=c%2B%2B&logoColor=white" alt="C++"/>
    </div>

    <div class="section-label d07">⚛️ &nbsp;Frameworks & Runtime</div>
    <div class="badge-grid">
      <img class="badge-img d08" src="https://img.shields.io/badge/-React-20232A?style=flat-square&logo=react&logoColor=61DAFB" alt="React"/>
      <img class="badge-img d09" src="https://img.shields.io/badge/-Node.js-339933?style=flat-square&logo=node.js&logoColor=white" alt="Node.js"/>
      <img class="badge-img d10" src="https://img.shields.io/badge/-Express-000000?style=flat-square&logo=express&logoColor=white" alt="Express"/>
    </div>

    <div class="section-label d11">🗄️ &nbsp;Databases</div>
    <div class="badge-grid">
      <img class="badge-img d12" src="https://img.shields.io/badge/-MongoDB-4DB33D?style=flat-square&logo=mongodb&logoColor=white" alt="MongoDB"/>
      <img class="badge-img d13" src="https://img.shields.io/badge/-MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white" alt="MySQL"/>
    </div>

    <div class="section-label d14">🎨 &nbsp;Styling</div>
    <div class="badge-grid">
      <img class="badge-img d15" src="https://img.shields.io/badge/-Tailwind%20CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white" alt="Tailwind CSS"/>
      <img class="badge-img d16" src="https://img.shields.io/badge/-Bootstrap-563D7C?style=flat-square&logo=bootstrap&logoColor=white" alt="Bootstrap"/>
    </div>

    <hr/>

    <!-- CONNECT -->
    <div class="cmd-line d17"><span class="p">$</span><span class="c">cat connect.json</span></div>

    <div class="social-list">
      <a href="https://linkedin.com/in/amanjeet-sharma-20b75a252" target="_blank" class="social-item d18">
        <img class="sbadge" src="https://img.shields.io/badge/-LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"/>
        <span class="sarrow">→</span>
        <span class="surl">linkedin.com/in/amanjeet-sharma-20b75a252</span>
      </a>
      <a href="https://github.com/AmanjeetSharma" target="_blank" class="social-item d19">
        <img class="sbadge" src="https://img.shields.io/badge/-GitHub-181717?style=flat-square&logo=github&logoColor=white" alt="GitHub"/>
        <span class="sarrow">→</span>
        <span class="surl">github.com/AmanjeetSharma</span>
      </a>
      <a href="mailto:amansharma23503@gmail.com" class="social-item d20">
        <img class="sbadge" src="https://img.shields.io/badge/-Email-D14836?style=flat-square&logo=gmail&logoColor=white" alt="Email"/>
        <span class="sarrow">→</span>
        <span class="surl">amansharma23503@gmail.com</span>
      </a>
    </div>

    <hr/>

    <!-- FOOTER -->
    <div class="footer d21">
      <span class="status"></span>
      ⭐️ &nbsp;Thanks for stopping by!
    </div>

  </div>
</div>
</body>
</html>
