<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Prem Choithani — Portfolio</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&family=Syne:wght@400;600;700;800&display=swap');

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }

body {
  background-color: #080808;
  color: #e8e8e0;
  font-family: 'Syne', 'Segoe UI', sans-serif;
  line-height: 1.7;
  overflow-x: hidden;
  min-height: 100vh;
}

/* BG GRID - real div, no pseudo-element, fully VS Code safe */
#bg-grid {
  position: fixed; inset: 0; z-index: 0; pointer-events: none;
  background-image:
    linear-gradient(rgba(255,107,0,0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,107,0,0.04) 1px, transparent 1px);
  background-size: 52px 52px;
}
#bg-radial {
  position: fixed;
  top: -300px; left: 50%; transform: translateX(-50%);
  width: 1000px; height: 700px;
  background: radial-gradient(ellipse at center, rgba(255,107,0,0.06) 0%, transparent 68%);
  z-index: 0; pointer-events: none;
}

.wrapper { position: relative; z-index: 1; max-width: 920px; margin: 0 auto; padding: 0 2rem; }

/* ─── NAV ─── */
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 999;
  background: rgba(8,8,8,0.88);
  border-bottom: 1px solid rgba(255,107,0,0.12);
  padding: 0.85rem 2.5rem;
  display: flex; align-items: center; justify-content: space-between;
  -webkit-backdrop-filter: blur(14px);
  backdrop-filter: blur(14px);
}
.nav-logo { font-family: 'JetBrains Mono', monospace; font-size: 0.82rem; color: #FF6B00; letter-spacing: 0.04em; }
.nav-logo span { color: #555; }
.nav-links { display: flex; gap: 1.8rem; list-style: none; }
.nav-links a {
  font-family: 'JetBrains Mono', monospace; font-size: 0.75rem;
  color: #666; text-decoration: none; letter-spacing: 0.1em;
  text-transform: uppercase; transition: color 0.2s;
}
.nav-links a:hover { color: #FF6B00; }

/* ─── BANNER HERO ─── */
#hero { padding-top: 56px; position: relative; z-index: 1; }

.banner-container {
  position: relative;
  width: 100%;
  max-height: 380px;
  overflow: hidden;
}
.banner-container img {
  width: 100%;
  max-height: 380px;
  object-fit: cover;
  object-position: center top;
  display: block;
}
/* Cinematic letter-box bars */
.banner-container::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0;
  height: 60px;
  background: linear-gradient(to bottom, #080808 0%, transparent 100%);
  z-index: 2;
}
.banner-container::after {
  content: '';
  position: absolute; bottom: 0; left: 0; right: 0;
  height: 120px;
  background: linear-gradient(to top, #080808 0%, transparent 100%);
  z-index: 2;
}

/* Orange scan-line overlay on banner */
.banner-scanline {
  position: absolute; inset: 0; z-index: 3; pointer-events: none;
  background: repeating-linear-gradient(
    transparent, transparent 3px,
    rgba(255,107,0,0.03) 3px, rgba(255,107,0,0.03) 4px
  );
  mix-blend-mode: screen;
}

/* Hero content overlapping the banner bottom */
.hero-content {
  margin-top: -80px;
  position: relative; z-index: 4;
  padding: 0 0 4rem;
}
.hero-content .wrapper { padding-top: 0; }

.hero-eyebrow {
  font-family: 'JetBrains Mono', monospace; font-size: 0.75rem;
  color: #FF6B00; letter-spacing: 0.18em; text-transform: uppercase;
  margin-bottom: 1rem;
  display: inline-flex; align-items: center; gap: 0.7rem;
}
.hero-eyebrow::before { content: ''; display: block; width: 32px; height: 1px; background: #FF6B00; }

h1.hero-name {
  font-size: clamp(3rem, 7vw, 6rem);
  font-weight: 800; line-height: 1.0; letter-spacing: -0.04em;
  margin-bottom: 0.6rem;
}
h1.hero-name .accent { color: #FF6B00; }

.hero-typewriter {
  font-family: 'JetBrains Mono', monospace;
  font-size: clamp(0.85rem, 1.8vw, 1rem);
  color: #666; margin-bottom: 2rem; min-height: 1.5em;
}
.hero-typewriter .cursor {
  display: inline-block; width: 2px; height: 0.9em;
  background: #FF6B00; vertical-align: middle; margin-left: 1px;
  animation: blink 0.9s step-end infinite;
}
@keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

.hero-desc {
  max-width: 500px; font-size: 1rem; color: rgba(232,232,224,0.65);
  margin-bottom: 2.5rem;
}

.cta-row { display: flex; gap: 1rem; flex-wrap: wrap; }
.btn {
  padding: 0.7rem 1.6rem;
  font-family: 'JetBrains Mono', monospace; font-size: 0.8rem;
  font-weight: 500; letter-spacing: 0.08em; text-transform: uppercase;
  text-decoration: none; border-radius: 4px; cursor: pointer;
  display: inline-flex; align-items: center; gap: 0.4rem;
  transition: all 0.2s; border: 1px solid transparent;
}
.btn-primary { background-color: #FF6B00; color: #000; border-color: #FF6B00; }
.btn-primary:hover { background-color: #cc5500; border-color: #cc5500; transform: translateY(-2px); box-shadow: 0 8px 28px rgba(255,107,0,0.28); }
.btn-secondary { background-color: transparent; color: #e8e8e0; border-color: rgba(255,107,0,0.4); }
.btn-secondary:hover { border-color: #FF6B00; color: #FF6B00; transform: translateY(-2px); }
.btn-ghost {
  background-color: transparent; color: #aaa; border-color: rgba(255,255,255,0.08);
  padding: 0.5rem 1.1rem; font-size: 0.72rem;
}
.btn-ghost:hover { color: #FF6B00; border-color: rgba(255,107,0,0.35); }

/* ─── SECTIONS ─── */
section { padding: 5rem 0; position: relative; z-index: 1; }

.divider {
  position: relative; z-index: 1;
  height: 1px;
  background: linear-gradient(90deg, transparent 0%, rgba(255,107,0,0.18) 50%, transparent 100%);
}

.section-tag {
  font-family: 'JetBrains Mono', monospace; font-size: 0.72rem;
  color: #FF6B00; letter-spacing: 0.18em; text-transform: uppercase;
  margin-bottom: 0.6rem;
  display: flex; align-items: center; gap: 0.5rem;
}
.section-tag::before { content: '//'; color: #444; }

h2 { font-size: clamp(1.7rem, 3.5vw, 2.6rem); font-weight: 700; letter-spacing: -0.025em; margin-bottom: 2.8rem; }

/* ─── CODE BLOCK ─── */
.code-block {
  background-color: #0e0e0e; border: 1px solid rgba(255,107,0,0.14);
  border-radius: 10px; overflow: hidden;
}
.code-header {
  background-color: #141414; border-bottom: 1px solid rgba(255,107,0,0.1);
  padding: 0.65rem 1.2rem;
  display: flex; align-items: center; gap: 0.5rem;
  font-family: 'JetBrains Mono', monospace; font-size: 0.73rem; color: #555;
}
.dot { width: 11px; height: 11px; border-radius: 50%; flex-shrink: 0; }
.dot-r { background-color: #ff5f56; }
.dot-y { background-color: #ffbd2e; }
.dot-g { background-color: #27c93f; }
.code-body { padding: 1.5rem 1.8rem; font-family: 'JetBrains Mono', monospace; font-size: 0.86rem; line-height: 2.1; overflow-x: auto; }
.line { display: block; }
.kw { color: #c678dd; }
.cls { color: #e5c07b; }
.str { color: #98c379; }
.cm { color: #4b5563; font-style: italic; }
.num { color: #FF6B00; }

/* ─── TECH STACK ─── */
.tech-group { margin-bottom: 2.2rem; }
.tech-group-label {
  font-family: 'JetBrains Mono', monospace; font-size: 0.7rem;
  color: #555; letter-spacing: 0.12em; text-transform: uppercase;
  margin-bottom: 1rem; padding-left: 0.7rem;
  border-left: 2px solid #FF6B00;
}
.tech-grid { display: flex; flex-wrap: wrap; gap: 0.85rem; }

.tech-chip {
  display: flex; align-items: center; gap: 0.55rem;
  background-color: #111; border: 1px solid rgba(255,107,0,0.12);
  border-radius: 6px; padding: 0.55rem 1rem;
  transition: all 0.22s; cursor: default;
}
.tech-chip:hover {
  border-color: rgba(255,107,0,0.5);
  background-color: rgba(255,107,0,0.06);
  transform: translateY(-3px);
  box-shadow: 0 6px 22px rgba(255,107,0,0.1);
}
.tech-chip img { width: 20px; height: 20px; object-fit: contain; display: block; }
.tech-chip-name { font-family: 'JetBrains Mono', monospace; font-size: 0.78rem; color: #aaa; white-space: nowrap; }
.tech-chip:hover .tech-chip-name { color: #e8e8e0; }

/* ─── PROJECTS ─── */
.projects-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem; }
@media(max-width:650px) { .projects-grid { grid-template-columns: 1fr; } }

.proj-card {
  background-color: #0e0e0e;
  border: 1px solid rgba(255,107,0,0.12);
  border-radius: 10px; padding: 1.6rem;
  transition: all 0.25s; position: relative; overflow: hidden;
  display: flex; flex-direction: column;
}
.proj-card-top-bar {
  position: absolute; top: 0; left: 0; right: 0; height: 2px;
  background: linear-gradient(90deg, #FF6B00, transparent);
  opacity: 0; transition: opacity 0.25s;
}
.proj-card:hover { border-color: rgba(255,107,0,0.4); transform: translateY(-5px); box-shadow: 0 14px 42px rgba(255,107,0,0.1); }
.proj-card:hover .proj-card-top-bar { opacity: 1; }

.proj-head { display: flex; align-items: flex-start; justify-content: space-between; margin-bottom: 1rem; }
.proj-icon { font-size: 1.7rem; line-height: 1; }
.proj-title { font-size: 1rem; font-weight: 600; color: #e8e8e0; margin-bottom: 0.3rem; }
.proj-lang {
  font-family: 'JetBrains Mono', monospace; font-size: 0.68rem;
  color: #FF6B00; letter-spacing: 0.05em;
}
.proj-desc { font-size: 0.87rem; color: rgba(232,232,224,0.55); line-height: 1.6; margin-bottom: 1.1rem; }
.proj-features { list-style: none; margin-bottom: 1.4rem; flex: 1; }
.proj-features li {
  font-size: 0.8rem; color: #555; padding: 0.22rem 0;
  display: flex; align-items: flex-start; gap: 0.45rem;
}
.proj-features li::before { content: '→'; color: #FF6B00; flex-shrink: 0; margin-top: 0.05rem; }
.proj-footer { margin-top: auto; padding-top: 1rem; border-top: 1px solid rgba(255,107,0,0.08); }

/* ─── STATS ─── */
.stats-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-bottom: 1rem; }
@media(max-width:600px){ .stats-grid{ grid-template-columns:1fr; } }
.stats-img {
  width: 100%; border-radius: 8px; display: block;
  border: 1px solid rgba(255,107,0,0.1);
  background-color: #111;
}
.stats-full { width: 100%; border-radius: 8px; display: block; border: 1px solid rgba(255,107,0,0.1); margin-bottom: 1rem; background-color: #111; }

/* ─── CONNECT ─── */
.connect-grid { display: flex; flex-wrap: wrap; gap: 1rem; }
.connect-link {
  display: flex; align-items: center; gap: 0.9rem;
  background-color: #0e0e0e; border: 1px solid rgba(255,107,0,0.12);
  border-radius: 8px; padding: 1.1rem 1.5rem;
  text-decoration: none; color: #e8e8e0; transition: all 0.2s;
  flex: 1; min-width: 220px;
}
.connect-link:hover { border-color: rgba(255,107,0,0.5); color: #FF6B00; transform: translateY(-3px); box-shadow: 0 8px 28px rgba(255,107,0,0.1); }
.connect-link img { width: 28px; height: 28px; object-fit: contain; }
.connect-sub { font-family: 'JetBrains Mono', monospace; font-size: 0.68rem; color: #555; letter-spacing: 0.06em; display: block; margin-bottom: 0.15rem; }
.connect-val { font-size: 0.9rem; font-weight: 500; }

/* ─── FOOTER ─── */
footer { border-top: 1px solid rgba(255,107,0,0.1); padding: 2.5rem; text-align: center; position: relative; z-index: 1; }
.footer-text { font-family: 'JetBrains Mono', monospace; font-size: 0.82rem; color: #444; }
.footer-text span { color: #FF6B00; }

/* ─── SCROLL REVEAL ─── */
.reveal { opacity: 0; transform: translateY(22px); transition: opacity 0.55s ease, transform 0.55s ease; }
.reveal.in { opacity: 1; transform: translateY(0); }
</style>
</head>
<body>

<!-- VS Code note: open this file in a real browser (double-click) or use Live Server extension for full rendering -->

<!-- BG LAYERS -->
<div id="bg-grid"></div>
<div id="bg-radial"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo"><span>~/</span>prem-choithani</div>
  <ul class="nav-links">
    <li><a href="#about">about</a></li>
    <li><a href="#stack">stack</a></li>
    <li><a href="#projects">projects</a></li>
    <li><a href="#stats">stats</a></li>
    <li><a href="#connect">connect</a></li>
  </ul>
</nav>

<!-- HERO + BANNER -->
<section id="hero">

  <!-- BANNER — displayed as a cinematic strip -->
  <div class="banner-container">
    <img
      src="https://raw.githubusercontent.com/prem-choithani23/prem-choithani23/main/assets/banner.png?v=3"
      alt="Prem Choithani Banner"
      onerror="this.style.display='none';document.getElementById('banner-fallback').style.display='block'"
    />
    <!-- Fallback orange stripe if banner fails to load -->
    <div id="banner-fallback" style="display:none; height:220px; background: linear-gradient(135deg, #0e0e0e 0%, #1a0a00 50%, #0e0e0e 100%); border-bottom: 1px solid rgba(255,107,0,0.2);"></div>
    <div class="banner-scanline"></div>
  </div>

  <!-- HERO CONTENT overlapping banner bottom -->
  <div class="hero-content">
    <div class="wrapper">
      <div class="hero-eyebrow">To be intern in Barclays · Jun 2026</div>
      <h1 class="hero-name">Prem<br/><span class="accent">Choithani.</span></h1>
      <div class="hero-typewriter">
        <span id="tw"></span><span class="cursor"></span>
      </div>
      <p class="hero-desc">
        Full Stack Developer from Mumbai, India. Building production-grade backends with Spring Boot, crafting React UIs, and playing the violin by night.
      </p>
      <div class="cta-row">
        <a href="#projects" class="btn btn-primary">↓ View Projects</a>
        <a href="#connect" class="btn btn-secondary">Get in Touch</a>
        <a href="https://github.com/prem-choithani23" target="_blank" class="btn btn-ghost">GitHub ↗</a>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ABOUT -->
<section id="about">
  <div class="wrapper">
    <div class="section-tag">about me</div>
    <h2>whoami</h2>
    <div class="code-block reveal">
      <div class="code-header">
        <div class="dot dot-r"></div>
        <div class="dot dot-y"></div>
        <div class="dot dot-g"></div>
        <span style="margin-left:6px;">Developer.java</span>
      </div>
      <div class="code-body">
        <span class="line"><span class="kw">public class</span> <span class="cls">Developer</span> {</span>
        <span class="line">&nbsp;</span>
        <span class="line">&nbsp;&nbsp;<span class="kw">private final</span> String  name&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; = <span class="str">"Prem Choithani"</span>;</span>
        <span class="line">&nbsp;&nbsp;<span class="kw">private final</span> String  location&nbsp; = <span class="str">"Mumbai, India 🇮🇳"</span>;</span>
        <span class="line">&nbsp;&nbsp;<span class="kw">private final</span> String  role&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; = <span class="str">"Full Stack Developer"</span>;</span>
        <span class="line">&nbsp;&nbsp;<span class="kw">private final</span> String  focus&nbsp;&nbsp;&nbsp;&nbsp; = <span class="str">"Spring Boot &amp; Backend Architecture"</span>;</span>
        <span class="line">&nbsp;&nbsp;<span class="kw">private final</span> String  hobby&nbsp;&nbsp;&nbsp;&nbsp; = <span class="str">"Playing the Violin 🎻"</span>;</span>
        <span class="line">&nbsp;</span>
        <span class="line">&nbsp;&nbsp;<span class="cm">// Life philosophy</span></span>
        <span class="line">&nbsp;&nbsp;<span class="kw">private final</span> String  mantra&nbsp;&nbsp;&nbsp; =</span>
        <span class="line">&nbsp;&nbsp;&nbsp;&nbsp;<span class="str">"Code with rhythm, just like the violin 🎶"</span>;</span>
        <span class="line">&nbsp;</span>
        <span class="line">}</span>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- TECH STACK -->
<section id="stack">
  <div class="wrapper">
    <div class="section-tag">technologies</div>
    <h2>Tech Arsenal</h2>

    <div class="tech-group reveal">
      <div class="tech-group-label">Languages</div>
      <div class="tech-grid">
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/java/java-original.svg" alt="Java"/>
          <span class="tech-chip-name">Java</span>
        </div>
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg" alt="JavaScript"/>
          <span class="tech-chip-name">JavaScript</span>
        </div>
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/c/c-original.svg" alt="C"/>
          <span class="tech-chip-name">C</span>
        </div>
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original.svg" alt="Python"/>
          <span class="tech-chip-name">Python</span>
        </div>
      </div>
    </div>

    <div class="tech-group reveal">
      <div class="tech-group-label">Frontend</div>
      <div class="tech-grid">
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/react/react-original.svg" alt="React"/>
          <span class="tech-chip-name">React</span>
        </div>
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg" alt="HTML5"/>
          <span class="tech-chip-name">HTML5</span>
        </div>
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg" alt="CSS3"/>
          <span class="tech-chip-name">CSS3</span>
        </div>
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/tailwindcss/tailwindcss-original.svg" alt="Tailwind"/>
          <span class="tech-chip-name">Tailwind CSS</span>
        </div>
      </div>
    </div>

    <div class="tech-group reveal">
      <div class="tech-group-label">Backend &amp; Database</div>
      <div class="tech-grid">
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/spring/spring-original.svg" alt="Spring Boot"/>
          <span class="tech-chip-name">Spring Boot</span>
        </div>
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original.svg" alt="MySQL"/>
          <span class="tech-chip-name">MySQL</span>
        </div>
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/postgresql/postgresql-original.svg" alt="PostgreSQL"/>
          <span class="tech-chip-name">PostgreSQL</span>
        </div>
      </div>
    </div>

    <div class="tech-group reveal">
      <div class="tech-group-label">Tools &amp; IDEs</div>
      <div class="tech-grid">
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/git/git-original.svg" alt="Git"/>
          <span class="tech-chip-name">Git</span>
        </div>
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/vscode/vscode-original.svg" alt="VS Code"/>
          <span class="tech-chip-name">VS Code</span>
        </div>
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/intellij/intellij-original.svg" alt="IntelliJ IDEA"/>
          <span class="tech-chip-name">IntelliJ IDEA</span>
        </div>
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/webstorm/webstorm-original.svg" alt="WebStorm"/>
          <span class="tech-chip-name">WebStorm</span>
        </div>
        <div class="tech-chip">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/pycharm/pycharm-original.svg" alt="PyCharm"/>
          <span class="tech-chip-name">PyCharm</span>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- PROJECTS -->
<section id="projects">
  <div class="wrapper">
    <div class="section-tag">work</div>
    <h2>Projects</h2>
    <div class="projects-grid">

      <div class="proj-card reveal">
        <div class="proj-card-top-bar"></div>
        <div class="proj-head">
          <span class="proj-icon">🧵</span>
        </div>
        <div class="proj-title">Multi-Threaded File Downloader</div>
        <div class="proj-lang">Java · Concurrency</div>
        <p class="proj-desc">Concurrent file downloader handling multiple downloads in parallel with real-time terminal progress bars and automatic retry on failure.</p>
        <ul class="proj-features">
          <li>ExecutorService fixed thread pool</li>
          <li>Callable &amp; Future for async task management</li>
          <li>Synchronized Singleton for thread-safe rendering</li>
        </ul>
        <div class="proj-footer">
          <a href="https://github.com/prem-choithani23/multi-threaded-file-downloader" target="_blank" class="btn btn-ghost" style="display:inline-flex;">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" alt="" style="width:14px;height:14px;filter:invert(1);opacity:0.7"/>
            View on GitHub ↗
          </a>
        </div>
      </div>

      <div class="proj-card reveal">
        <div class="proj-card-top-bar"></div>
        <div class="proj-head">
          <span class="proj-icon">🧬</span>
        </div>
        <div class="proj-title">Spring Schema Engine</div>
        <div class="proj-lang">Java · Spring · Jackson</div>
        <p class="proj-desc">Schema-driven entity generator that reads JSON metadata and outputs relationally correct Java entity classes.</p>
        <ul class="proj-features">
          <li>Auto-infers 1:1, 1:N, M:N relationships</li>
          <li>Formal database modeling rules as backbone</li>
          <li>Metadata as single source of truth</li>
        </ul>
        <div class="proj-footer">
          <a href="https://github.com/prem-choithani23/Spring-Schema-Engine" target="_blank" class="btn btn-ghost" style="display:inline-flex;">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" alt="" style="width:14px;height:14px;filter:invert(1);opacity:0.7"/>
            View on GitHub ↗
          </a>
        </div>
      </div>

      <div class="proj-card reveal">
        <div class="proj-card-top-bar"></div>
        <div class="proj-head">
          <span class="proj-icon">📄</span>
        </div>
        <div class="proj-title">Spring API Doc Generator</div>
        <div class="proj-lang">Java · Spring</div>
        <p class="proj-desc">Scans Spring controller classes and auto-generates a clickable, structured API documentation file.</p>
        <ul class="proj-features">
          <li>Parses annotations at class &amp; method level</li>
          <li>Auto-detects server ports from config</li>
          <li>Centralizes all endpoints into one output</li>
        </ul>
        <div class="proj-footer">
          <a href="https://github.com/prem-choithani23/Spring-API-Doc-Generator" target="_blank" class="btn btn-ghost" style="display:inline-flex;">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" alt="" style="width:14px;height:14px;filter:invert(1);opacity:0.7"/>
            View on GitHub ↗
          </a>
        </div>
      </div>

      <div class="proj-card reveal">
        <div class="proj-card-top-bar"></div>
        <div class="proj-head">
          <span class="proj-icon">🎬</span>
        </div>
        <div class="proj-title">Film Fiesta</div>
        <div class="proj-lang">React · Tailwind · JavaScript</div>
        <p class="proj-desc">Responsive movie discovery app powered by the TMDB API with full dark/light mode and a fluid, modern UI.</p>
        <ul class="proj-features">
          <li>Live movie search &amp; discovery</li>
          <li>Dark / Light mode toggle</li>
          <li>Fully responsive across all devices</li>
        </ul>
        <div class="proj-footer">
          <a href="https://github.com/prem-choithani23/Film-Fiesta" target="_blank" class="btn btn-ghost" style="display:inline-flex;">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" alt="" style="width:14px;height:14px;filter:invert(1);opacity:0.7"/>
            View on GitHub ↗
          </a>
        </div>
      </div>

    </div>
  </div>
</section>

<div class="divider"></div>

<!-- STATS -->
<section id="stats">
  <div class="wrapper">
    <div class="section-tag">activity</div>
    <h2>GitHub Stats</h2>
    <div class="stats-grid reveal">
      <img class="stats-img"
        src="https://github-readme-stats.vercel.app/api?username=prem-choithani23&show_icons=true&theme=dark&hide_border=true&bg_color=0e0e0e&title_color=FF6B00&icon_color=FF6B00&text_color=e0e0e0&rank_icon=github"
        alt="GitHub Stats"/>
      <img class="stats-img"
        src="https://github-readme-stats.vercel.app/api/top-langs/?username=prem-choithani23&layout=compact&theme=dark&hide_border=true&bg_color=0e0e0e&title_color=FF6B00&text_color=e0e0e0&langs_count=6"
        alt="Top Languages"/>
    </div>
    <img class="stats-full reveal"
      src="https://streak-stats.demolab.com/?user=prem-choithani23&theme=dark&hide_border=true&background=0e0e0e&ring=FF6B00&fire=FF3D00&currStreakLabel=FF6B00&sideLabels=FF6B00&dates=888&stroke=FF6B00"
      alt="GitHub Streak"/>
    <img class="stats-full reveal"
      src="https://github-readme-activity-graph.vercel.app/graph?username=prem-choithani23&bg_color=0e0e0e&color=FF6B00&line=FF6B00&point=ffffff&area=true&area_color=FF6B0022&hide_border=true"
      alt="Activity Graph"/>
  </div>
</section>

<div class="divider"></div>

<!-- CONNECT -->
<section id="connect">
  <div class="wrapper">
    <div class="section-tag">contact</div>
    <h2>Connect</h2>
    <div class="connect-grid">
      <a href="mailto:premchoithani4@gmail.com" class="connect-link reveal">
        <img src="https://cdn.simpleicons.org/gmail/FF6B00" alt="Gmail" style="width:28px;height:28px;"/>
        <div>
          <span class="connect-sub">Email</span>
          <span class="connect-val">premchoithani4@gmail.com</span>
        </div>
      </a>
      <a href="https://www.linkedin.com/in/prem-choithani-937a27340" target="_blank" class="connect-link reveal">
        <img src="https://cdn.simpleicons.org/linkedin/FF6B00" alt="LinkedIn" style="width:28px;height:28px;"/>
        <div>
          <span class="connect-sub">LinkedIn</span>
          <span class="connect-val">Prem Choithani</span>
        </div>
      </a>
      <a href="https://github.com/prem-choithani23" target="_blank" class="connect-link reveal">
        <img src="https://cdn.simpleicons.org/github/FF6B00" alt="GitHub" style="width:28px;height:28px;"/>
        <div>
          <span class="connect-sub">GitHub</span>
          <span class="connect-val">prem-choithani23</span>
        </div>
      </a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-text">
    <span>🎻</span> Code with rhythm, just like the violin. <span>🎶</span>
    &nbsp;·&nbsp; Built by Prem Choithani
  </div>
</footer>

<script>
  // ── Typewriter ──
  const roles = [
    'Full Stack Developer 🚀',
    'Java · Spring Boot Enthusiast ☕',
    'React Builder 🔧',
    'Always shipping, always learning 📦',
    'Violin Player by night 🎻'
  ];
  var ri = 0, ci = 0, del = false;
  var tw = document.getElementById('tw');
  function type() {
    var cur = roles[ri];
    if (!del) {
      tw.textContent = cur.slice(0, ++ci);
      if (ci === cur.length) { del = true; setTimeout(type, 2200); return; }
    } else {
      tw.textContent = cur.slice(0, --ci);
      if (ci === 0) { del = false; ri = (ri + 1) % roles.length; }
    }
    setTimeout(type, del ? 36 : 72);
  }
  type();

  // ── Scroll Reveal ──
  var reveals = document.querySelectorAll('.reveal');
  if ('IntersectionObserver' in window) {
    var obs = new IntersectionObserver(function(entries) {
      entries.forEach(function(e, i) {
        if (e.isIntersecting) {
          setTimeout(function(){ e.target.classList.add('in'); }, i * 90);
          obs.unobserve(e.target);
        }
      });
    }, { threshold: 0.08 });
    reveals.forEach(function(r){ obs.observe(r); });
  } else {
    // Fallback for VS Code preview which may not support IntersectionObserver
    reveals.forEach(function(r){ r.classList.add('in'); });
  }
</script>
</body>
</html>