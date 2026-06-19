<!DOCTYPE html>
<html>
<head>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap');

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: #0d1117;
    color: #e6edf3;
    font-family: 'Space Grotesk', sans-serif;
    min-height: 100vh;
    padding: 2rem;
  }

  .readme { max-width: 860px; margin: 0 auto; }

  .hero {
    background: linear-gradient(135deg, #161b22 0%, #0d1117 50%, #1a1f2e 100%);
    border: 1px solid #30363d;
    border-radius: 16px;
    padding: 2.5rem 2rem 2rem;
    margin-bottom: 1.5rem;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute;
    top: -60px; right: -60px;
    width: 220px; height: 220px;
    background: radial-gradient(circle, rgba(88,166,255,0.12) 0%, transparent 70%);
    border-radius: 50%;
    pointer-events: none;
  }

  .hero-top { display: flex; align-items: flex-start; gap: 1.5rem; margin-bottom: 1.5rem; }

  .avatar {
    width: 72px; height: 72px;
    border-radius: 50%;
    background: linear-gradient(135deg, #58a6ff 0%, #a371f7 100%);
    display: flex; align-items: center; justify-content: center;
    font-size: 26px; font-weight: 700;
    color: #fff;
    flex-shrink: 0;
    border: 2px solid #30363d;
  }

  .hero-info h1 { font-size: 28px; font-weight: 700; color: #e6edf3; margin-bottom: 4px; letter-spacing: -0.5px; }
  .hero-info h1 span {
    background: linear-gradient(90deg, #58a6ff, #a371f7);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .hero-info .tagline { color: #8b949e; font-size: 14px; margin-bottom: 10px; font-family: 'JetBrains Mono', monospace; }

  .hero-badges { display: flex; gap: 8px; flex-wrap: wrap; }
  .badge { background: #1c2128; border: 1px solid #30363d; border-radius: 20px; padding: 4px 12px; font-size: 12px; color: #8b949e; display: flex; align-items: center; gap: 5px; }
  .badge.blue { border-color: #1f6feb; color: #58a6ff; background: #0d2046; }
  .badge.purple { border-color: #6e40c9; color: #a371f7; background: #1e0e4a; }
  .badge.green { border-color: #1a7f37; color: #3fb950; background: #0a2510; }

  .hero-bio { background: #161b22; border: 1px solid #21262d; border-radius: 10px; padding: 1rem 1.25rem; position: relative; z-index: 1; }
  .bio-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
  .bio-item { display: flex; align-items: flex-start; gap: 8px; font-size: 13px; color: #8b949e; line-height: 1.4; }
  .bio-item .icon { font-size: 15px; margin-top: 1px; flex-shrink: 0; }
  .bio-item strong { color: #e6edf3; }

  .section { margin-bottom: 1.5rem; }
  .section-header { display: flex; align-items: center; gap: 10px; margin-bottom: 1rem; }
  .section-header h2 { font-size: 13px; font-weight: 600; text-transform: uppercase; letter-spacing: 1.5px; color: #8b949e; }
  .section-header .line { flex: 1; height: 1px; background: #21262d; }

  /* CATEGORY LABEL */
  .cat-label { font-size: 11px; color: #484f58; text-transform: uppercase; letter-spacing: 1.2px; margin-bottom: 8px; font-family: 'JetBrains Mono', monospace; }

  .tech-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(82px, 1fr));
    gap: 10px;
    margin-bottom: 16px;
  }
  .tech-card {
    background: #161b22;
    border: 1px solid #21262d;
    border-radius: 12px;
    padding: 14px 8px 10px;
    text-align: center;
    transition: border-color 0.2s, transform 0.2s;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
  }
  .tech-card:hover { border-color: #58a6ff55; transform: translateY(-3px); }
  .tech-card img { width: 38px; height: 38px; object-fit: contain; }
  .tech-name { font-size: 11px; color: #8b949e; font-weight: 500; }

  /* AI CARD special glow */
  .tech-card.ai-card { border-color: #a371f722; }
  .tech-card.ai-card:hover { border-color: #a371f766; }

  .platform-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  .platform-card {
    background: #161b22; border: 1px solid #21262d; border-radius: 12px; padding: 1rem 1.25rem;
    display: flex; align-items: center; gap: 12px; cursor: pointer; transition: border-color 0.2s;
    text-decoration: none; color: inherit;
  }
  .platform-card:hover { border-color: #30363d; }
  .platform-icon { width: 40px; height: 40px; border-radius: 10px; display: flex; align-items: center; justify-content: center; flex-shrink: 0; overflow: hidden; }
  .platform-icon img { width: 28px; height: 28px; object-fit: contain; }
  .platform-info { flex: 1; }
  .platform-info strong { font-size: 14px; font-weight: 600; color: #e6edf3; display: block; margin-bottom: 2px; }
  .platform-info span { font-size: 12px; color: #8b949e; }
  .platform-arrow { color: #30363d; font-size: 14px; }

  .connect-grid { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 12px; }

  .content-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; }
  .content-card { background: #161b22; border: 1px solid #21262d; border-radius: 12px; padding: 1rem; text-align: center; }
  .content-card .big-icon { font-size: 28px; margin-bottom: 8px; }
  .content-card h3 { font-size: 13px; font-weight: 600; color: #e6edf3; margin-bottom: 4px; }
  .content-card p { font-size: 11px; color: #8b949e; line-height: 1.5; }

  .stats-row { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; }
  .stat-card { background: #161b22; border: 1px solid #21262d; border-radius: 12px; padding: 1.2rem 1rem; text-align: center; }
  .stat-card .stat-num { font-size: 28px; font-weight: 700; color: #e6edf3; font-family: 'JetBrains Mono', monospace; margin-bottom: 4px; }
  .stat-card .stat-num span { background: linear-gradient(90deg, #58a6ff, #a371f7); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
  .stat-card .stat-label { font-size: 11px; color: #8b949e; text-transform: uppercase; letter-spacing: 1px; }

  .ticker-wrap { background: #161b22; border: 1px solid #21262d; border-radius: 10px; padding: 10px 1rem; overflow: hidden; white-space: nowrap; }
  .ticker-inner { display: inline-block; animation: ticker 20s linear infinite; }
  .ticker-inner span { font-family: 'JetBrains Mono', monospace; font-size: 13px; color: #8b949e; margin-right: 3rem; }
  .ticker-inner span em { color: #58a6ff; font-style: normal; font-weight: 500; }
  @keyframes ticker { from { transform: translateX(0); } to { transform: translateX(-50%); } }

  .footer { text-align: center; padding-top: 1rem; font-size: 11px; color: #484f58; font-family: 'JetBrains Mono', monospace; }
  .footer strong { color: #8b949e; }
</style>
</head>
<body>
<div class="readme">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-top">
      <div class="avatar">RK</div>
      <div class="hero-info">
        <h1>Hey, I'm <span>Ranjithkumar A</span> 👋</h1>
        <div class="tagline">$ student --major="AI & Data Science" --status=building</div>
        <div class="hero-badges">
          <span class="badge blue">🎓 BTech AI&DS</span>
          <span class="badge purple">⚡ AI & ML Explorer</span>
          <span class="badge green">🌐 Web Developer</span>
        </div>
      </div>
    </div>
    <div class="hero-bio">
      <div class="bio-grid">
        <div class="bio-item"><span class="icon">🌱</span><div>Currently learning <strong>Python, C, Java & DSA</strong></div></div>
        <div class="bio-item"><span class="icon">🛠️</span><div>Building <strong>AI/ML & Web Development</strong> projects</div></div>
        <div class="bio-item"><span class="icon">🔭</span><div>Exploring <strong>new technologies</strong> constantly</div></div>
        <div class="bio-item"><span class="icon">⚡</span><div>Fun fact: I <strong>love coding challenges</strong></div></div>
        <div class="bio-item"><span class="icon">💬</span><div>Ask me about <strong>anything Tech</strong></div></div>
        <div class="bio-item"><span class="icon">📚</span><div>Always <strong>learning & improving</strong> every day</div></div>
      </div>
    </div>
  </div>

  <!-- STATS -->
  <div class="section">
    <div class="stats-row">
      <div class="stat-card"><div class="stat-num"><span>13+</span></div><div class="stat-label">Tools & Languages</div></div>
      <div class="stat-card"><div class="stat-num"><span>AI</span></div><div class="stat-label">Primary Domain</div></div>
      <div class="stat-card"><div class="stat-num"><span>∞</span></div><div class="stat-label">Curiosity Level</div></div>
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="section">
    <div class="section-header">
      <h2>Tech Stack</h2>
      <div class="line"></div>
    </div>

    <!-- Languages -->
    <div class="cat-label">Languages</div>
    <div class="tech-grid">
      <div class="tech-card">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="Python">
        <div class="tech-name">Python</div>
      </div>
      <div class="tech-card">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" alt="Java">
        <div class="tech-name">Java</div>
      </div>
      <div class="tech-card">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-original.svg" alt="C">
        <div class="tech-name">C</div>
      </div>
      <div class="tech-card">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" alt="HTML5">
        <div class="tech-name">HTML5</div>
      </div>
      <div class="tech-card">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" alt="CSS3">
        <div class="tech-name">CSS3</div>
      </div>
      <div class="tech-card">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" alt="JavaScript">
        <div class="tech-name">JavaScript</div>
      </div>
    </div>

    <!-- Databases & Backend -->
    <div class="cat-label">Database & Backend</div>
    <div class="tech-grid">
      <div class="tech-card">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg" alt="MySQL">
        <div class="tech-name">MySQL</div>
      </div>
      <div class="tech-card">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/firebase/firebase-plain.svg" alt="Firebase">
        <div class="tech-name">Firebase</div>
      </div>
    </div>

    <!-- Tools & Platforms -->
    <div class="cat-label">Tools & Platforms</div>
    <div class="tech-grid">
      <div class="tech-card">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" alt="VS Code">
        <div class="tech-name">VS Code</div>
      </div>
      <div class="tech-card">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/netlify/netlify-original.svg" alt="Netlify">
        <div class="tech-name">Netlify</div>
      </div>
      <div class="tech-card">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vercel/vercel-original.svg" alt="Vercel" style="filter: invert(1);">
        <div class="tech-name">Vercel</div>
      </div>
      <div class="tech-card">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" alt="Git">
        <div class="tech-name">Git</div>
      </div>
    </div>

    <!-- AI Tools -->
    <div class="cat-label">AI Tools I Use</div>
    <div class="tech-grid">
      <div class="tech-card ai-card">
        <img src="https://upload.wikimedia.org/wikipedia/commons/0/04/ChatGPT_logo.svg" alt="ChatGPT">
        <div class="tech-name">ChatGPT</div>
      </div>
      <div class="tech-card ai-card">
        <img src="https://upload.wikimedia.org/wikipedia/commons/7/78/Anthropic_logo.svg" alt="Claude" style="filter: invert(1);">
        <div class="tech-name">Claude</div>
      </div>
      <div class="tech-card ai-card">
        <!-- Canva logo via devicons or fallback SVG -->
        <svg width="38" height="38" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect width="100" height="100" rx="22" fill="#7D2AE8"/>
          <path d="M70.5 32.2C67.1 28 62 25.5 56.5 25.5C48.5 25.5 41.8 30.7 39.3 38C37.5 36.9 35.4 36.3 33.2 36.3C26.7 36.3 21.5 41.6 21.5 48.1C21.5 54.7 26.7 59.9 33.2 59.9C34 59.9 34.8 59.8 35.6 59.6C37.5 65.4 42.9 69.5 49.3 69.5C53.3 69.5 56.9 67.9 59.6 65.3C61.6 67.7 64.6 69.2 68 69.2C74.3 69.2 79.4 64.1 79.4 57.8C79.4 53.8 77.3 50.2 74.2 48.2C75 46.5 75.5 44.6 75.5 42.6C75.5 38.6 73.5 35.1 70.5 32.2Z" fill="white"/>
        </svg>
        <div class="tech-name">Canva</div>
      </div>
    </div>

  </div>

  <!-- CODING PLATFORMS -->
  <div class="section">
    <div class="section-header">
      <h2>Coding Profiles</h2>
      <div class="line"></div>
    </div>
    <div class="platform-grid">
      <a class="platform-card" href="https://www.geeksforgeeks.org/profile/ranjith_a_k" target="_blank">
        <div class="platform-icon" style="background:#0e2a1a; border:1px solid #2f8d4640;">
          <img src="https://upload.wikimedia.org/wikipedia/commons/4/43/GeeksforGeeks.svg" alt="GFG">
        </div>
        <div class="platform-info">
          <strong>GeeksforGeeks</strong>
          <span>@ranjith_a_k</span>
        </div>
        <span class="platform-arrow">↗</span>
      </a>
      <a class="platform-card" href="https://leetcode.com/u/ranjith_ak/" target="_blank">
        <div class="platform-icon" style="background:#2a1f0a; border:1px solid #f89f1b40;">
          <img src="https://upload.wikimedia.org/wikipedia/commons/1/19/LeetCode_logo_black.png" alt="LeetCode" style="filter:invert(1) sepia(1) saturate(3) hue-rotate(5deg);">
        </div>
        <div class="platform-info">
          <strong>LeetCode</strong>
          <span>@ranjith_ak</span>
        </div>
        <span class="platform-arrow">↗</span>
      </a>
    </div>
  </div>

  <!-- CONNECT -->
  <div class="section">
    <div class="section-header">
      <h2>Connect</h2>
      <div class="line"></div>
    </div>
    <div class="connect-grid">
      <a class="platform-card" href="https://www.linkedin.com/in/ranjithkumar-a-456616280/" target="_blank">
        <div class="platform-icon" style="background:#0d2046; border:1px solid #0a66c240;">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" alt="LinkedIn">
        </div>
        <div class="platform-info">
          <strong>LinkedIn</strong>
          <span>Professional</span>
        </div>
        <span class="platform-arrow">↗</span>
      </a>
      <a class="platform-card" href="https://x.com/ARanjit06037457" target="_blank">
        <div class="platform-icon" style="background:#1a1a1a; border:1px solid #ffffff20;">
          <img src="https://upload.wikimedia.org/wikipedia/commons/c/ce/X_logo_2023.svg" alt="X" style="width:22px;height:22px;filter:invert(1);">
        </div>
        <div class="platform-info">
          <strong>X / Twitter</strong>
          <span>@ARanjit06037457</span>
        </div>
        <span class="platform-arrow">↗</span>
      </a>
      <a class="platform-card" href="https://ranjithak.netlify.app/" target="_blank">
        <div class="platform-icon" style="background:#1a120a; border:1px solid #ff6b3540;">
          <img src="https://www.netlify.com/v3/img/components/logomark.png" alt="Portfolio" style="width:26px;height:26px;">
        </div>
        <div class="platform-info">
          <strong>Portfolio</strong>
          <span>ranjithak.netlify.app</span>
        </div>
        <span class="platform-arrow">↗</span>
      </a>
    </div>
  </div>

  <!-- CONTENT PLATFORMS -->
  <div class="section">
    <div class="section-header">
      <h2>Content I Create</h2>
      <div class="line"></div>
    </div>
    <div class="content-grid">
      <div class="content-card">
        <div class="big-icon">📝</div>
        <h3>Medium Blog</h3>
        <p>Personal development, productivity & mindset shifts</p>
        <br>
        <a href="https://medium.com/@ranjithtamil160" target="_blank" style="font-size:11px;color:#58a6ff;text-decoration:none;">Read blog ↗</a>
      </div>
      <div class="content-card">
        <div class="big-icon">💬</div>
        <h3>WhatsApp Channel</h3>
        <p>Daily motivation, productivity tips & mindset insights</p>
        <br>
        <a href="https://whatsapp.com/channel/0029Vb7K9H30gcfJCnLVKI24" target="_blank" style="font-size:11px;color:#25D366;text-decoration:none;">Join channel ↗</a>
      </div>
      <div class="content-card">
        <div class="big-icon">⚡</div>
        <h3>RK Freelance</h3>
        <p>Websites & apps — let's build something together</p>
        <br>
        <a href="https://rkfreelance.in" target="_blank" style="font-size:11px;color:#f89f1b;text-decoration:none;">Hire me ↗</a>
      </div>
    </div>
  </div>

  <!-- MOTIVATIONAL TICKER -->
  <div class="section">
    <div class="ticker-wrap">
      <div class="ticker-inner">
        <span><em>Stay Hard 🔥</em></span>
        <span><em>Day One or One Day ⌛</em></span>
        <span><em>Never Give Up 💪</em></span>
        <span><em>Die With Memories, Not Dreams 🌅</em></span>
        <span><em>Discipline > Motivation ⚡</em></span>
        <span>•</span>
        <span><em>Stay Hard 🔥</em></span>
        <span><em>Day One or One Day ⌛</em></span>
        <span><em>Never Give Up 💪</em></span>
        <span><em>Die With Memories, Not Dreams 🌅</em></span>
        <span><em>Discipline > Motivation ⚡</em></span>
        <span>•</span>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <strong>Ranjithkumar A</strong> · BTech AI&DS · Salem, Tamil Nadu 🇮🇳<br>
    <span>Crafted with 💙 — one commit at a time</span>
  </div>

</div>
</body>
</html>
