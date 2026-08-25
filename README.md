<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>Prasad Thorat — Cybersecurity · AI · Software Engineering</title>
<meta name="description" content="Prasad Sudhir Thorat — B.Tech (Integrated) CSE, Cybersecurity Enthusiast, Aspiring Software Engineer.">

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,300;9..144,400;9..144,500;9..144,600&family=Inter:wght@300;400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">

<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

<style>
:root{
  --black:#08080a;
  --charcoal:#161412;
  --charcoal-2:#1d1a17;
  --orange:#d98a4f;
  --orange-dim:#8a5a35;
  --white:#f4f0e8;
  --blue-glow:#3d5468;
  --glass:rgba(244,240,232,0.06);
  --glass-border:rgba(244,240,232,0.14);
  --line:rgba(244,240,232,0.12);
  --muted:rgba(244,240,232,0.58);
  --faint:rgba(244,240,232,0.34);

  --display:'Fraunces', Georgia, serif;
  --body:'Inter', -apple-system, sans-serif;
  --mono:'JetBrains Mono', monospace;

  --ease:cubic-bezier(.22,1,.36,1);
}

*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
@media(prefers-reduced-motion: reduce){ html{scroll-behavior:auto;} }

body{
  background:var(--black);
  color:var(--white);
  font-family:var(--body);
  font-weight:400;
  overflow-x:hidden;
  -webkit-font-smoothing:antialiased;
}

a{color:inherit;text-decoration:none;}
button{font-family:inherit;cursor:pointer;border:none;background:none;color:inherit;}
img,video{display:block;max-width:100%;}
::selection{background:var(--orange-dim);color:var(--white);}

.eyebrow{
  font-family:var(--mono);
  font-size:11px;
  letter-spacing:0.22em;
  text-transform:uppercase;
  color:var(--orange);
  display:flex;align-items:center;gap:10px;
}
.eyebrow::before{content:'';width:22px;height:1px;background:var(--orange);display:inline-block;}

.wrap{max-width:1180px;margin:0 auto;padding:0 32px;}
@media(max-width:640px){.wrap{padding:0 22px;}}

/* ---------- NAV ---------- */
.nav{
  position:fixed;top:0;left:0;right:0;z-index:100;
  display:flex;align-items:center;justify-content:space-between;
  padding:22px 40px;
  transition:background .4s var(--ease), backdrop-filter .4s var(--ease), padding .4s var(--ease);
}
.nav.scrolled{
  background:rgba(8,8,10,0.72);
  backdrop-filter:blur(16px);
  -webkit-backdrop-filter:blur(16px);
  border-bottom:1px solid var(--line);
  padding:14px 40px;
}
.nav-logo{font-family:var(--display);font-size:19px;letter-spacing:0.04em;}
.nav-links{display:flex;gap:34px;list-style:none;}
.nav-links a{
  font-family:var(--mono);font-size:11px;letter-spacing:0.14em;text-transform:uppercase;
  color:var(--muted);position:relative;padding-bottom:4px;transition:color .3s;
}
.nav-links a::after{
  content:'';position:absolute;left:0;bottom:0;height:1px;width:0;background:var(--orange);
  transition:width .35s var(--ease);
}
.nav-links a:hover{color:var(--white);}
.nav-links a:hover::after{width:100%;}
.nav-toggle{display:none;width:36px;height:36px;position:relative;z-index:110;}
.nav-toggle span{display:block;position:absolute;left:8px;right:8px;height:1px;background:var(--white);transition:transform .35s var(--ease), opacity .3s;}
.nav-toggle span:nth-child(1){top:13px;}
.nav-toggle span:nth-child(2){top:19px;}
.nav-toggle span:nth-child(3){top:25px;}
.nav-toggle.open span:nth-child(1){transform:translateY(6px) rotate(45deg);}
.nav-toggle.open span:nth-child(2){opacity:0;}
.nav-toggle.open span:nth-child(3){transform:translateY(-6px) rotate(-45deg);}

.mobile-menu{
  position:fixed;inset:0;z-index:105;
  background:rgba(10,9,8,0.88);backdrop-filter:blur(22px);-webkit-backdrop-filter:blur(22px);
  display:flex;flex-direction:column;align-items:center;justify-content:center;gap:28px;
  opacity:0;pointer-events:none;transition:opacity .4s var(--ease);
}
.mobile-menu.open{opacity:1;pointer-events:auto;}
.mobile-menu a{font-family:var(--display);font-size:28px;color:var(--white);}

@media(max-width:860px){
  .nav-links{display:none;}
  .nav-toggle{display:block;}
  .nav{padding:18px 22px;}
  .nav.scrolled{padding:14px 22px;}
}

/* ---------- HERO ---------- */
.hero{
  position:relative;
  height:100svh;min-height:560px;
  overflow:hidden;
  display:flex;align-items:flex-end;
  background:#000;
}
.hero-bg-video, .hero-fg-video{
  position:absolute;top:0;left:0;width:100%;height:100%;object-fit:cover;
}
.hero-bg-video{
  filter:blur(38px) brightness(0.55) saturate(1.15);
  transform:scale(1.18);
  opacity:0.85;
}
.hero-fg-video{
  filter:brightness(0.92) contrast(1.04) saturate(1.05);
  -webkit-mask-image:radial-gradient(ellipse 68% 78% at 50% 42%, black 55%, transparent 100%);
  mask-image:radial-gradient(ellipse 68% 78% at 50% 42%, black 55%, transparent 100%);
  opacity:0;
}
.hero-grade{
  position:absolute;inset:0;pointer-events:none;
  background:
    radial-gradient(ellipse 60% 50% at 50% 30%, rgba(217,138,79,0.16), transparent 60%),
    radial-gradient(ellipse 40% 40% at 78% 68%, rgba(61,84,104,0.20), transparent 65%),
    linear-gradient(to bottom, rgba(8,8,10,0.55) 0%, rgba(8,8,10,0.15) 30%, rgba(8,8,10,0.35) 62%, rgba(8,8,10,0.96) 100%);
}
.hero-vignette{
  position:absolute;inset:0;pointer-events:none;
  box-shadow:inset 0 0 220px 60px rgba(0,0,0,0.85);
}
.hero-grain{
  position:absolute;inset:0;pointer-events:none;opacity:0.045;mix-blend-mode:overlay;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='120' height='120'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
}
#cinematic-canvas{position:absolute;inset:0;z-index:3;pointer-events:none;}

.hero-content{
  position:relative;z-index:5;width:100%;
  padding:0 40px 84px;
}
.hero-inner{max-width:1180px;margin:0 auto;}
.hero-eyebrow{opacity:0;margin-bottom:22px;}
.hero-name{
  font-family:var(--display);
  font-weight:500;
  font-size:clamp(56px, 12vw, 148px);
  line-height:0.86;
  letter-spacing:-0.01em;
  color:var(--white);
}
.hero-name span{display:block;overflow:hidden;}
.hero-name span em{display:block;font-style:normal;transform:translateY(110%);opacity:0;}
.hero-name .accent{color:var(--orange);}

.hero-role{
  font-family:var(--body);font-weight:400;
  font-size:clamp(14px,2vw,18px);
  color:var(--muted);
  margin-top:22px;max-width:520px;
  opacity:0;
  line-height:1.55;
}
.hero-role strong{color:var(--white);font-weight:500;}
.hero-statement{
  font-family:var(--display);font-style:italic;font-weight:300;
  font-size:clamp(15px,1.6vw,19px);
  color:var(--faint);
  margin-top:18px;max-width:480px;
  opacity:0;
}

@media(max-width:640px){
  .hero-content{padding:0 22px 64px;}
}

/* glass controls */
.hero-controls{
  position:absolute;bottom:36px;right:32px;z-index:8;
  display:flex;gap:10px;align-items:center;
  opacity:0;
}
.glass-btn{
  width:46px;height:46px;border-radius:50%;
  background:rgba(20,18,16,0.45);
  backdrop-filter:blur(14px);-webkit-backdrop-filter:blur(14px);
  border:1px solid var(--glass-border);
  display:flex;align-items:center;justify-content:center;
  transition:transform .3s var(--ease), background .3s;
}
.glass-btn:hover{background:rgba(217,138,79,0.18);transform:translateY(-2px);}
.glass-btn:focus-visible{outline:1px solid var(--orange);outline-offset:3px;}
.glass-btn svg{width:16px;height:16px;stroke:var(--white);fill:none;}

.sound-hint{
  position:absolute;bottom:96px;right:32px;z-index:8;
  font-family:var(--mono);font-size:10px;letter-spacing:0.16em;text-transform:uppercase;
  color:var(--white);
  background:rgba(20,18,16,0.5);backdrop-filter:blur(10px);
  border:1px solid var(--glass-border);
  padding:8px 14px;border-radius:20px;
  opacity:0;pointer-events:none;
}

@media(max-width:640px){
  .hero-controls{right:20px;bottom:26px;}
  .sound-hint{right:20px;bottom:82px;}
}

/* socials */
.hero-socials{
  position:absolute;top:100px;right:32px;z-index:8;
  display:flex;flex-direction:column;gap:14px;
  opacity:0;
}
.hero-socials a{
  width:42px;height:42px;border-radius:50%;
  background:rgba(20,18,16,0.4);backdrop-filter:blur(12px);
  border:1px solid var(--glass-border);
  display:flex;align-items:center;justify-content:center;
  transition:transform .3s var(--ease), background .3s, box-shadow .3s;
}
.hero-socials a svg{width:17px;height:17px;stroke:var(--white);fill:none;transition:transform .3s var(--ease);}
.hero-socials a:hover{background:rgba(217,138,79,0.2);transform:translateX(-4px);box-shadow:0 0 22px rgba(217,138,79,0.25);}
.hero-socials a:hover svg{transform:scale(1.08);}
@media(max-width:860px){.hero-socials{display:none;}}

/* scroll indicator */
.scroll-indicator{
  position:absolute;left:50%;bottom:34px;transform:translateX(-50%);z-index:8;
  display:flex;flex-direction:column;align-items:center;gap:10px;
  opacity:0;
}
.scroll-indicator span{
  font-family:var(--mono);font-size:10px;letter-spacing:0.2em;text-transform:uppercase;color:var(--faint);
}
.scroll-line{width:1px;height:44px;background:rgba(244,240,232,0.18);position:relative;overflow:hidden;}
.scroll-line::after{
  content:'';position:absolute;top:-100%;left:0;width:100%;height:100%;
  background:linear-gradient(to bottom, transparent, var(--orange));
  animation:scrollLine 2.6s ease-in-out infinite;
}
@keyframes scrollLine{
  0%{top:-100%;}
  60%{top:100%;}
  100%{top:100%;}
}
@media(max-width:640px){.scroll-indicator{bottom:24px;}}

/* ---------- SECTION SHARED ---------- */
section{position:relative;}
.section-pad{padding:150px 0;}
@media(max-width:860px){.section-pad{padding:100px 0;}}
.section-label{margin-bottom:30px;}
.section-head{max-width:760px;}
.section-title{
  font-family:var(--display);font-weight:500;
  font-size:clamp(32px, 5vw, 58px);
  line-height:1.06;letter-spacing:-0.01em;
}
.section-title em{font-style:normal;color:var(--orange);}

/* ---------- ABOUT ---------- */
.about{background:var(--black);}
.about-grid{
  display:grid;grid-template-columns:1.1fr 0.9fr;gap:70px;margin-top:56px;align-items:start;
}
@media(max-width:900px){.about-grid{grid-template-columns:1fr;gap:40px;}}
.about-lead{
  font-family:var(--display);font-weight:400;font-size:clamp(20px,2.4vw,28px);
  line-height:1.45;color:var(--white);
}
.about-lead .hl{color:var(--orange);}
.about-body{color:var(--muted);font-size:15.5px;line-height:1.85;margin-top:26px;}
.about-facts{display:flex;flex-direction:column;gap:0;border-top:1px solid var(--line);}
.about-fact{
  padding:20px 0;border-bottom:1px solid var(--line);
  display:flex;justify-content:space-between;gap:20px;
}
.about-fact .k{font-family:var(--mono);font-size:11px;letter-spacing:0.1em;text-transform:uppercase;color:var(--faint);}
.about-fact .v{font-size:14.5px;color:var(--white);text-align:right;max-width:60%;}

.highlights{margin-top:64px;display:grid;grid-template-columns:repeat(3,1fr);gap:1px;background:var(--line);border:1px solid var(--line);}
@media(max-width:760px){.highlights{grid-template-columns:1fr;}}
.highlight-card{background:var(--black);padding:34px 30px;}
.highlight-card .num{font-family:var(--mono);font-size:11px;color:var(--orange);letter-spacing:0.1em;}
.highlight-card p{margin-top:16px;font-size:14.5px;line-height:1.7;color:var(--muted);}

/* ---------- SKILLS ---------- */
.skills{background:var(--charcoal);}
.skill-grid{margin-top:56px;display:grid;grid-template-columns:repeat(3,1fr);gap:1px;background:var(--line);border:1px solid var(--line);}
@media(max-width:900px){.skill-grid{grid-template-columns:repeat(2,1fr);}}
@media(max-width:600px){.skill-grid{grid-template-columns:1fr;}}
.skill-card{
  background:var(--charcoal);padding:36px 30px;transition:background .4s var(--ease);
}
.skill-card:hover{background:var(--charcoal-2);}
.skill-card h3{
  font-family:var(--mono);font-size:11.5px;letter-spacing:0.16em;text-transform:uppercase;color:var(--orange);
  margin-bottom:22px;
}
.skill-card ul{list-style:none;display:flex;flex-direction:column;gap:11px;}
.skill-card li{
  font-family:var(--display);font-size:17px;color:var(--white);
  padding-left:0;position:relative;transition:transform .25s var(--ease), color .25s;
}
.skill-card li:hover{transform:translateX(6px);color:var(--orange);}

/* ---------- EXPERIENCE ---------- */
.experience{background:var(--black);}
.timeline{margin-top:60px;position:relative;padding-left:44px;border-left:1px solid var(--line);}
@media(max-width:600px){.timeline{padding-left:28px;}}
.timeline-item{position:relative;padding-bottom:6px;}
.timeline-item::before{
  content:'';position:absolute;left:-49px;top:6px;width:9px;height:9px;border-radius:50%;
  background:var(--orange);box-shadow:0 0 0 4px rgba(217,138,79,0.15);
}
@media(max-width:600px){.timeline-item::before{left:-33px;}}
.timeline-date{font-family:var(--mono);font-size:11px;letter-spacing:0.1em;text-transform:uppercase;color:var(--faint);}
.timeline-role{font-family:var(--display);font-size:clamp(22px,3vw,32px);margin-top:10px;}
.timeline-org{color:var(--orange);font-size:15px;margin-top:6px;}
.timeline-list{margin-top:22px;display:flex;flex-direction:column;gap:12px;max-width:640px;}
.timeline-list li{
  list-style:none;display:flex;gap:12px;font-size:15px;line-height:1.6;color:var(--muted);
}
.timeline-list li::before{content:'—';color:var(--orange-dim);flex-shrink:0;}
.timeline-rec{
  margin-top:26px;padding:18px 22px;border:1px solid var(--glass-border);background:var(--glass);
  font-size:14.5px;color:var(--white);max-width:640px;line-height:1.6;
}

/* ---------- CERTIFICATIONS ---------- */
.certs{background:var(--charcoal);}
.cert-tabs{margin-top:44px;display:flex;gap:10px;flex-wrap:wrap;}
.cert-tab{
  font-family:var(--mono);font-size:11px;letter-spacing:0.08em;text-transform:uppercase;
  padding:9px 16px;border:1px solid var(--glass-border);border-radius:20px;color:var(--muted);
  transition:all .3s var(--ease);
}
.cert-tab.active,.cert-tab:hover{background:var(--orange);color:#1a1108;border-color:var(--orange);}
.cert-groups{margin-top:40px;display:flex;flex-direction:column;gap:52px;}
.cert-group-title{
  font-family:var(--mono);font-size:11px;letter-spacing:0.14em;text-transform:uppercase;color:var(--orange);
  margin-bottom:20px;
}
.cert-list{display:grid;grid-template-columns:repeat(2,1fr);gap:1px;background:var(--line);border:1px solid var(--line);}
@media(max-width:760px){.cert-list{grid-template-columns:1fr;}}
.cert-item{
  background:var(--charcoal);padding:22px 24px;display:flex;flex-direction:column;gap:6px;
  transition:background .3s var(--ease);
}
.cert-item:hover{background:var(--charcoal-2);}
.cert-item .name{font-family:var(--display);font-size:16.5px;color:var(--white);line-height:1.4;}
.cert-item .issuer{font-family:var(--mono);font-size:10.5px;letter-spacing:0.08em;text-transform:uppercase;color:var(--faint);}

/* ---------- MOMENTS ---------- */
.moments{background:var(--black);}
.moments-list{margin-top:56px;display:flex;flex-direction:column;}
.moment-row{
  display:grid;grid-template-columns:90px 1fr 220px;gap:24px;align-items:baseline;
  padding:26px 0;border-top:1px solid var(--line);
  transition:padding-left .3s var(--ease);
}
.moment-row:last-child{border-bottom:1px solid var(--line);}
.moment-row:hover{padding-left:12px;}
.moment-row .idx{font-family:var(--mono);font-size:12px;color:var(--orange-dim);}
.moment-row .title{font-family:var(--display);font-size:clamp(18px,2.4vw,25px);color:var(--white);}
.moment-row .meta{font-family:var(--mono);font-size:11px;letter-spacing:0.06em;color:var(--faint);text-align:right;}
@media(max-width:700px){
  .moment-row{grid-template-columns:40px 1fr;grid-template-rows:auto auto;}
  .moment-row .meta{grid-column:2;text-align:left;margin-top:4px;}
}

/* ---------- CONTACT ---------- */
.contact{
  background:var(--charcoal);
  padding:170px 0 120px;
  position:relative;overflow:hidden;
}
.contact::before{
  content:'';position:absolute;inset:0;
  background:radial-gradient(ellipse 60% 50% at 50% 0%, rgba(217,138,79,0.10), transparent 70%);
  pointer-events:none;
}
.contact-inner{position:relative;text-align:center;max-width:760px;margin:0 auto;}
.contact-title{
  font-family:var(--display);font-weight:500;
  font-size:clamp(34px,6.5vw,72px);line-height:1.04;letter-spacing:-0.01em;
}
.contact-title em{font-style:normal;color:var(--orange);}
.contact-sub{margin-top:22px;color:var(--muted);font-family:var(--mono);font-size:12px;letter-spacing:0.1em;text-transform:uppercase;}
.contact-buttons{margin-top:52px;display:flex;flex-wrap:wrap;gap:14px;justify-content:center;}
.cta-btn{
  display:inline-flex;align-items:center;gap:10px;
  padding:16px 28px;border-radius:30px;
  font-family:var(--mono);font-size:12px;letter-spacing:0.08em;text-transform:uppercase;
  border:1px solid var(--glass-border);
  transition:all .35s var(--ease);
}
.cta-btn.primary{background:var(--orange);color:#1a1108;border-color:var(--orange);}
.cta-btn.primary:hover{background:var(--white);border-color:var(--white);transform:translateY(-3px);}
.cta-btn:not(.primary):hover{background:var(--glass);border-color:var(--white);transform:translateY(-3px);}
.cta-btn svg{width:15px;height:15px;stroke:currentColor;fill:none;}

/* ---------- FOOTER ---------- */
footer{
  background:var(--black);border-top:1px solid var(--line);
  padding:34px 0;
}
.footer-inner{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:14px;}
.footer-inner p{font-family:var(--mono);font-size:11px;color:var(--faint);letter-spacing:0.04em;}

/* reveal helper */
.reveal{opacity:0;transform:translateY(36px);}

/* focus visibility */
a:focus-visible, button:focus-visible{outline:1px solid var(--orange);outline-offset:3px;}

@media(prefers-reduced-motion: reduce){
  .reveal{opacity:1;transform:none;}
}
</style>
</head>
<body>

<!-- NAV -->
<nav class="nav" id="nav">
  <a href="#hero" class="nav-logo">PT</a>
  <ul class="nav-links">
    <li><a href="#hero">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#certifications">Certifications</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <button class="nav-toggle" id="navToggle" aria-label="Open menu" aria-expanded="false">
    <span></span><span></span><span></span>
  </button>
</nav>
<div class="mobile-menu" id="mobileMenu">
  <a href="#hero">Home</a>
  <a href="#about">About</a>
  <a href="#skills">Skills</a>
  <a href="#experience">Experience</a>
  <a href="#certifications">Certifications</a>
  <a href="#contact">Contact</a>
</div>

<!-- HERO -->
<section class="hero" id="hero">
  <video class="hero-bg-video" src="prasad-hero.mp4" autoplay loop muted playsinline aria-hidden="true"></video>
  <video class="hero-fg-video" id="fgVideo" src="prasad-hero.mp4" autoplay loop muted playsinline
         aria-label="Prasad Sudhir Thorat introducing himself"></video>
  <div class="hero-grade"></div>
  <div class="hero-vignette"></div>
  <div class="hero-grain"></div>
  <canvas id="cinematic-canvas"></canvas>

  <div class="hero-socials" id="heroSocials">
    <a href="https://www.linkedin.com/in/prasad-thorat-a38578372?utm_source=share_via&utm_content=profile&utm_medium=member_android" target="_blank" rel="noopener noreferrer" aria-label="LinkedIn profile">
      <svg viewBox="0 0 24 24" stroke-width="1.6"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-4 0v7h-4V8h4v1.5A6 6 0 0 1 16 8Z"/><rect x="2" y="8" width="4" height="13"/><circle cx="4" cy="3" r="1.6"/></svg>
    </a>
    <a href="https://github.com/prasadthorat25uid-arch" target="_blank" rel="noopener noreferrer" aria-label="GitHub profile">
      <svg viewBox="0 0 24 24" stroke-width="1.6"><path d="M9 19c-4.3 1.4-4.3-2.5-6-3m12 5v-3.5c0-1 .1-1.4-.5-2 2.8-.3 5.5-1.4 5.5-6a4.6 4.6 0 0 0-1.3-3.2 4.2 4.2 0 0 0-.1-3.2s-1.1-.3-3.5 1.3a12.3 12.3 0 0 0-6.4 0C6.5 2.8 5.4 3.1 5.4 3.1a4.2 4.2 0 0 0-.1 3.2A4.6 4.6 0 0 0 4 9.5c0 4.6 2.7 5.7 5.5 6-.6.6-.6 1.2-.5 2V21"/></svg>
    </a>
    <a href="https://wa.me/918010989708" target="_blank" rel="noopener noreferrer" aria-label="Message on WhatsApp">
      <svg viewBox="0 0 24 24" stroke-width="1.6"><path d="M3 21l1.4-4.2A8.5 8.5 0 1 1 8 19.6L3 21Z"/><path d="M8.5 9.5c0 3.5 2.5 6 6 6 .6 0 1-.5.9-1.1l-.3-1.3a.9.9 0 0 0-1-.7l-1.3.3a5.6 5.6 0 0 1-2.5-2.5l.3-1.3a.9.9 0 0 0-.7-1l-1.3-.3c-.6-.1-1.1.3-1.1.9Z"/></svg>
    </a>
  </div>

  <div class="hero-content">
    <div class="hero-inner">
      <p class="eyebrow hero-eyebrow">Cybersecurity • AI • Software Engineering</p>
      <h1 class="hero-name">
        <span><em>PRASAD</em></span>
        <span><em class="accent">THORAT</em></span>
      </h1>
      <p class="hero-role">
        <strong>B.Tech (Integrated) CSE</strong> — Cybersecurity Enthusiast · Aspiring Software Engineer<br>
        Sanjivani University, Kopargaon, Maharashtra
      </p>
      <p class="hero-statement">Exploring the intersection of cybersecurity, artificial intelligence and software engineering.</p>
    </div>
  </div>

  <p class="sound-hint" id="soundHint">Tap for sound</p>
  <div class="hero-controls">
    <button class="glass-btn" id="playBtn" aria-label="Pause video">
      <svg id="playIcon" viewBox="0 0 24 24" stroke-width="1.6"><rect x="6" y="5" width="4" height="14"/><rect x="14" y="5" width="4" height="14"/></svg>
    </button>
    <button class="glass-btn" id="muteBtn" aria-label="Unmute video">
      <svg id="muteIcon" viewBox="0 0 24 24" stroke-width="1.6"><polygon points="4,9 8,9 12,5 12,19 8,15 4,15"/><line x1="16" y1="8" x2="22" y2="16"/><line x1="22" y1="8" x2="16" y2="16"/></svg>
    </button>
  </div>

  <div class="scroll-indicator" id="scrollIndicator" role="link" tabindex="0" aria-label="Scroll to explore">
    <span>Scroll to explore</span>
    <div class="scroll-line"></div>
  </div>
</section>

<!-- ABOUT -->
<section class="about section-pad" id="about">
  <div class="wrap">
    <p class="eyebrow section-label reveal">About</p>
    <div class="section-head reveal">
      <h2 class="section-title">The person <em>behind</em><br>the screen.</h2>
    </div>

    <div class="about-grid">
      <div>
        <p class="about-lead reveal">
          A second-year <span class="hl">Computer Science &amp; Engineering</span> student at Sanjivani University,
          building toward software engineering through the lens of <span class="hl">cybersecurity</span> and
          <span class="hl">artificial intelligence</span>.
        </p>
        <p class="about-body reveal">
          Prasad's work sits between three disciplines that increasingly depend on each other: networking and digital
          forensics on one side, generative AI tooling on the other, and the software engineering fundamentals that
          tie them together. That combination has shown up in a two-month cybersecurity internship, a growing list of
          workshops and certifications, and a habit of sharing what he learns — particularly around computer
          networking, IP addressing and subnetting — with a wider audience on LinkedIn.
        </p>
        <p class="about-body reveal">
          Still early in the degree, the approach so far has been practical experimentation over theory alone: cloud
          labs, AI tools, hackathon rounds, and hands-on forensics exercises, each treated as another rep toward
          becoming a well-rounded engineer.
        </p>
      </div>

      <div class="about-facts reveal">
        <div class="about-fact"><span class="k">Based in</span><span class="v">Kopargaon, Maharashtra, India</span></div>
        <div class="about-fact"><span class="k">Studying</span><span class="v">B.Tech (Integrated), CSE — Sanjivani University</span></div>
        <div class="about-fact"><span class="k">Year</span><span class="v">2nd Year</span></div>
        <div class="about-fact"><span class="k">Focus</span><span class="v">Cybersecurity · AI · Software Engineering</span></div>
        <div class="about-fact"><span class="k">Internship</span><span class="v">Cybersecurity Intern, InternsPort Innovation</span></div>
      </div>
    </div>

    <div class="highlights">
      <div class="highlight-card reveal">
        <p class="num">Networking</p>
        <p>Actively shares technical content on LinkedIn, particularly around computer networking, IP addressing and subnetting.</p>
      </div>
      <div class="highlight-card reveal">
        <p class="num">AI Tooling</p>
        <p>Exploring AI tools and their practical applications in productivity and software development.</p>
      </div>
      <div class="highlight-card reveal">
        <p class="num">Cybersecurity</p>
        <p>Hands-on exposure through a cybersecurity internship and dedicated forensics and networking workshops.</p>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section class="skills section-pad" id="skills">
  <div class="wrap">
    <p class="eyebrow section-label reveal">Skills</p>
    <div class="section-head reveal">
      <h2 class="section-title">Tools across the <em>stack</em>.</h2>
    </div>

    <div class="skill-grid">
      <div class="skill-card reveal">
        <h3>Programming</h3>
        <ul><li>C</li><li>Python</li><li>HTML</li></ul>
      </div>
      <div class="skill-card reveal">
        <h3>Cybersecurity</h3>
        <ul>
          <li>Digital Forensics</li><li>Network Basics</li><li>IP Addressing</li>
          <li>Subnetting</li><li>Cybersecurity Fundamentals</li>
        </ul>
      </div>
      <div class="skill-card reveal">
        <h3>Cloud &amp; DevOps</h3>
        <ul><li>AWS Elastic Container Service</li><li>KodeKloud Labs</li></ul>
      </div>
      <div class="skill-card reveal">
        <h3>AI &amp; Generative AI</h3>
        <ul><li>Claude AI</li><li>Google Workspace AI</li><li>Generative AI Studio</li><li>ChatGPT</li></ul>
      </div>
      <div class="skill-card reveal">
        <h3>Productivity</h3>
        <ul><li>Microsoft Excel with AI</li><li>Python Scripting</li></ul>
      </div>
    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section class="experience section-pad" id="experience">
  <div class="wrap">
    <p class="eyebrow section-label reveal">Experience</p>
    <div class="section-head reveal">
      <h2 class="section-title">On the <em>job</em>.</h2>
    </div>

    <div class="timeline">
      <div class="timeline-item reveal">
        <p class="timeline-date">February 2026 — April 2026</p>
        <h3 class="timeline-role">Cybersecurity Intern</h3>
        <p class="timeline-org">InternsPort Innovation Pvt. Ltd.</p>
        <ul class="timeline-list">
          <li>Completed a 2-month cybersecurity internship.</li>
          <li>Demonstrated analytical thinking and problem-solving abilities.</li>
          <li>Demonstrated effective communication.</li>
        </ul>
        <p class="timeline-rec">Earned a Letter of Recommendation from the Head of Operations.</p>
      </div>
    </div>
  </div>
</section>

<!-- CERTIFICATIONS -->
<section class="certs section-pad" id="certifications">
  <div class="wrap">
    <p class="eyebrow section-label reveal">Certifications</p>
    <div class="section-head reveal">
      <h2 class="section-title">Proof of <em>practice</em>.</h2>
    </div>

    <div class="cert-tabs" id="certTabs">
      <button class="cert-tab active" data-filter="all">All</button>
      <button class="cert-tab" data-filter="cloud">Cloud &amp; Infrastructure</button>
      <button class="cert-tab" data-filter="programming">Programming</button>
      <button class="cert-tab" data-filter="ai">AI &amp; GenAI</button>
      <button class="cert-tab" data-filter="cyber">Cybersecurity</button>
      <button class="cert-tab" data-filter="soft">Soft Skills</button>
    </div>

    <div class="cert-groups" id="certGroups">
      <div class="cert-group" data-group="cloud">
        <p class="cert-group-title">Cloud &amp; Infrastructure</p>
        <div class="cert-list">
          <div class="cert-item reveal"><span class="name">AWS Elastic Container Service (ECS)</span><span class="issuer">KodeKloud</span></div>
          <div class="cert-item reveal"><span class="name">KodeKloud Challenges Completion Certificate</span><span class="issuer">KodeKloud</span></div>
        </div>
      </div>

      <div class="cert-group" data-group="programming">
        <p class="cert-group-title">Programming</p>
        <div class="cert-list">
          <div class="cert-item reveal"><span class="name">Introduction to Python</span><span class="issuer">Infosys Springboard</span></div>
          <div class="cert-item reveal"><span class="name">Python Fundamentals</span><span class="issuer">Infosys Springboard</span></div>
          <div class="cert-item reveal"><span class="name">Introduction to C</span><span class="issuer">Sololearn</span></div>
          <div class="cert-item reveal"><span class="name">Programming For Beginners: Master the C Language</span><span class="issuer">Learn Programming Academy</span></div>
        </div>
      </div>

      <div class="cert-group" data-group="ai">
        <p class="cert-group-title">Artificial Intelligence &amp; GenAI</p>
        <div class="cert-list">
          <div class="cert-item reveal"><span class="name">AI Fluency: AI Capabilities &amp; Limitations</span><span class="issuer">Anthropic</span></div>
          <div class="cert-item reveal"><span class="name">Introduction to Claude Cowork</span><span class="issuer">Anthropic</span></div>
          <div class="cert-item reveal"><span class="name">Claude 101</span><span class="issuer">Anthropic</span></div>
          <div class="cert-item reveal"><span class="name">Bring AI to Work Workshop</span><span class="issuer">Google Workspace</span></div>
          <div class="cert-item reveal"><span class="name">Introduction to Generative AI Studio</span><span class="issuer">Simplilearn</span></div>
          <div class="cert-item reveal"><span class="name">Generative AI Mastery Workshop</span><span class="issuer">NxtWave / OpenAI Academy</span></div>
          <div class="cert-item reveal"><span class="name">AI Tools &amp; ChatGPT Workshop</span><span class="issuer">10X / BeLux</span></div>
          <div class="cert-item reveal"><span class="name">Microsoft Excel Using AI</span><span class="issuer">OfficeMaster</span></div>
        </div>
      </div>

      <div class="cert-group" data-group="cyber">
        <p class="cert-group-title">Cybersecurity</p>
        <div class="cert-list">
          <div class="cert-item reveal"><span class="name">Cybersecurity Mastery</span><span class="issuer">Unstop</span></div>
          <div class="cert-item reveal"><span class="name">Hands-on Digital Forensics &amp; Investigation Workshop</span><span class="issuer">Indian Cyber Club</span></div>
          <div class="cert-item reveal"><span class="name">SEBI Investor Awareness Test</span><span class="issuer">NISM</span></div>
        </div>
      </div>

      <div class="cert-group" data-group="soft">
        <p class="cert-group-title">Soft Skills</p>
        <div class="cert-list">
          <div class="cert-item reveal"><span class="name">Communication Skills</span><span class="issuer">MindLuster</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- MOMENTS -->
<section class="moments section-pad" id="moments">
  <div class="wrap">
    <p class="eyebrow section-label reveal">Events &amp; Achievements</p>
    <div class="section-head reveal">
      <h2 class="section-title">Moments along <em>the way</em>.</h2>
    </div>

    <div class="moments-list">
      <div class="moment-row reveal">
        <span class="idx">01</span>
        <span class="title">Artificial Intelligence Workshop</span>
        <span class="meta">Techfest, IIT Bombay</span>
      </div>
      <div class="moment-row reveal">
        <span class="idx">02</span>
        <span class="title">Smart India Hackathon — Internal Round</span>
        <span class="meta">Sanjivani University · Team Code Warriors, Idea Presentation</span>
      </div>
      <div class="moment-row reveal">
        <span class="idx">03</span>
        <span class="title">Constitution Day Quiz Competition</span>
        <span class="meta">Sanjivani University · Scored 90%</span>
      </div>
      <div class="moment-row reveal">
        <span class="idx">04</span>
        <span class="title">GenAI Buildathon</span>
        <span class="meta">NxtWave / OpenAI Academy</span>
      </div>
      <div class="moment-row reveal">
        <span class="idx">05</span>
        <span class="title">MYBharat Online Quizzes</span>
        <span class="meta">MYBharat</span>
      </div>
      <div class="moment-row reveal">
        <span class="idx">06</span>
        <span class="title">Dr. B.R. Ambedkar Quiz 2025</span>
        <span class="meta">Ministry of Social Justice &amp; Empowerment</span>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section class="contact" id="contact">
  <div class="wrap contact-inner">
    <p class="eyebrow reveal" style="justify-content:center;">Get in touch</p>
    <h2 class="contact-title reveal">Let's build <em>what's next.</em></h2>
    <p class="contact-sub reveal">Cybersecurity · AI · Software Engineering</p>
    <div class="contact-buttons reveal">
      <a class="cta-btn primary" href="https://www.linkedin.com/in/prasad-thorat-a38578372?utm_source=share_via&utm_content=profile&utm_medium=member_android" target="_blank" rel="noopener noreferrer">
        <svg viewBox="0 0 24 24" stroke-width="1.6"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-4 0v7h-4V8h4v1.5A6 6 0 0 1 16 8Z"/><rect x="2" y="8" width="4" height="13"/><circle cx="4" cy="3" r="1.6"/></svg>
        Connect on LinkedIn
      </a>
      <a class="cta-btn" href="https://github.com/prasadthorat25uid-arch" target="_blank" rel="noopener noreferrer">
        <svg viewBox="0 0 24 24" stroke-width="1.6"><path d="M9 19c-4.3 1.4-4.3-2.5-6-3m12 5v-3.5c0-1 .1-1.4-.5-2 2.8-.3 5.5-1.4 5.5-6a4.6 4.6 0 0 0-1.3-3.2 4.2 4.2 0 0 0-.1-3.2s-1.1-.3-3.5 1.3a12.3 12.3 0 0 0-6.4 0C6.5 2.8 5.4 3.1 5.4 3.1a4.2 4.2 0 0 0-.1 3.2A4.6 4.6 0 0 0 4 9.5c0 4.6 2.7 5.7 5.5 6-.6.6-.6 1.2-.5 2V21"/></svg>
        View GitHub
      </a>
      <a class="cta-btn" href="https://wa.me/918010989708" target="_blank" rel="noopener noreferrer">
        <svg viewBox="0 0 24 24" stroke-width="1.6"><path d="M3 21l1.4-4.2A8.5 8.5 0 1 1 8 19.6L3 21Z"/><path d="M8.5 9.5c0 3.5 2.5 6 6 6 .6 0 1-.5.9-1.1l-.3-1.3a.9.9 0 0 0-1-.7l-1.3.3a5.6 5.6 0 0 1-2.5-2.5l.3-1.3a.9.9 0 0 0-.7-1l-1.3-.3c-.6-.1-1.1.3-1.1.9Z"/></svg>
        Message on WhatsApp
      </a>
    </div>
  </div>
</section>

<footer>
  <div class="wrap footer-inner">
    <p>© 2026 Prasad Sudhir Thorat</p>
    <p>Kopargaon, Maharashtra, India</p>
  </div>
</footer>

<script>
gsap.registerPlugin(ScrollTrigger);
const reduceMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

/* ---------------- NAV ---------------- */
const nav = document.getElementById('nav');
window.addEventListener('scroll', () => {
  nav.classList.toggle('scrolled', window.scrollY > 40);
}, {passive:true});

const navToggle = document.getElementById('navToggle');
const mobileMenu = document.getElementById('mobileMenu');
navToggle.addEventListener('click', () => {
  const open = navToggle.classList.toggle('open');
  mobileMenu.classList.toggle('open', open);
  navToggle.setAttribute('aria-expanded', open);
});
mobileMenu.querySelectorAll('a').forEach(a => a.addEventListener('click', () => {
  navToggle.classList.remove('open');
  mobileMenu.classList.remove('open');
}));

/* ---------------- VIDEO CONTROLS ---------------- */
const fgVideo = document.getElementById('fgVideo');
const bgVideo = document.querySelector('.hero-bg-video');
const playBtn = document.getElementById('playBtn');
const muteBtn = document.getElementById('muteBtn');
const soundHint = document.getElementById('soundHint');
let userInteracted = false;

function hideSoundHint(){
  if (reduceMotion){ soundHint.style.opacity = 0; return; }
  gsap.to(soundHint, {opacity:0, duration:.5, onComplete:()=>soundHint.style.pointerEvents='none'});
}
setTimeout(hideSoundHint, 4500);

playBtn.addEventListener('click', () => {
  if (fgVideo.paused){
    fgVideo.play(); bgVideo.play();
    playBtn.setAttribute('aria-label','Pause video');
    document.getElementById('playIcon').innerHTML = '<rect x="6" y="5" width="4" height="14"/><rect x="14" y="5" width="4" height="14"/>';
  } else {
    fgVideo.pause(); bgVideo.pause();
    playBtn.setAttribute('aria-label','Play video');
    document.getElementById('playIcon').innerHTML = '<polygon points="7,4 20,12 7,20"/>';
  }
});

muteBtn.addEventListener('click', () => {
  userInteracted = true;
  fgVideo.muted = !fgVideo.muted;
  if (!fgVideo.muted){ fgVideo.play().catch(()=>{}); }
  muteBtn.setAttribute('aria-label', fgVideo.muted ? 'Unmute video' : 'Mute video');
  if (!reduceMotion) hideSoundHint();
  document.getElementById('muteIcon').innerHTML = fgVideo.muted
    ? '<polygon points="4,9 8,9 12,5 12,19 8,15 4,15"/><line x1="16" y1="8" x2="22" y2="16"/><line x1="22" y1="8" x2="16" y2="16"/>'
    : '<polygon points="4,9 8,9 12,5 12,19 8,15 4,15"/><path d="M16 8a5 5 0 0 1 0 8"/><path d="M18.5 5.5a9 9 0 0 1 0 13"/>';
});

/* ---------------- SCROLL INDICATOR ---------------- */
const scrollIndicator = document.getElementById('scrollIndicator');
function scrollToAbout(){
  document.getElementById('about').scrollIntoView({behavior: reduceMotion ? 'auto' : 'smooth'});
}
scrollIndicator.addEventListener('click', scrollToAbout);
scrollIndicator.addEventListener('keydown', e => { if(e.key==='Enter'||e.key===' ') scrollToAbout(); });

/* ---------------- CINEMATIC PARTICLE LAYER (Three.js) ---------------- */
(function initCinematicLayer(){
  const canvas = document.getElementById('cinematic-canvas');
  if (!window.THREE) return;

  const isMobile = window.innerWidth < 760;
  const particleCount = reduceMotion ? 0 : (isMobile ? 60 : 160);

  const renderer = new THREE.WebGLRenderer({canvas, alpha:true, antialias:false});
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, isMobile ? 1.3 : 1.8));
  renderer.setSize(window.innerWidth, window.innerHeight);

  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(55, window.innerWidth/window.innerHeight, 0.1, 100);
  camera.position.z = 12;

  let geometry, material, points;
  const positions = new Float32Array(particleCount * 3);
  const speeds = new Float32Array(particleCount);
  const colors = new Float32Array(particleCount * 3);

  const orange = new THREE.Color(0xd98a4f);
  const white = new THREE.Color(0xf4f0e8);
  const dust = new THREE.Color(0x8a8378);

  for (let i=0;i<particleCount;i++){
    positions[i*3] = (Math.random()-0.5) * 22;
    positions[i*3+1] = (Math.random()-0.5) * 14;
    positions[i*3+2] = (Math.random()-0.5) * 12;
    speeds[i] = 0.15 + Math.random()*0.35;
    const c = Math.random();
    const col = c < 0.35 ? orange : c < 0.6 ? white : dust;
    colors[i*3]=col.r; colors[i*3+1]=col.g; colors[i*3+2]=col.b;
  }

  geometry = new THREE.BufferGeometry();
  geometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));
  geometry.setAttribute('color', new THREE.BufferAttribute(colors, 3));

  material = new THREE.PointsMaterial({
    size: isMobile ? 0.16 : 0.13,
    vertexColors:true,
    transparent:true,
    opacity:0.55,
    blending:THREE.AdditiveBlending,
    depthWrite:false
  });

  points = new THREE.Points(geometry, material);
  scene.add(points);

  let mouseX=0, mouseY=0, targetX=0, targetY=0;
  window.addEventListener('mousemove', e => {
    mouseX = (e.clientX / window.innerWidth - 0.5);
    mouseY = (e.clientY / window.innerHeight - 0.5);
  }, {passive:true});

  let clock = new THREE.Clock();
  let rafId;
  let heroVisible = true;
  const heroEl = document.getElementById('hero');
  const io = new IntersectionObserver(entries => {
    heroVisible = entries[0].isIntersecting;
  }, {threshold:0.05});
  io.observe(heroEl);

  function animate(){
    rafId = requestAnimationFrame(animate);
    if (!heroVisible){ return; }
    const t = clock.getElapsedTime();
    const pos = geometry.attributes.position.array;
    for (let i=0;i<particleCount;i++){
      pos[i*3+1] += Math.sin(t*speeds[i] + i) * 0.0009;
      pos[i*3] += Math.cos(t*speeds[i]*0.6 + i) * 0.0006;
    }
    geometry.attributes.position.needsUpdate = true;

    targetX += (mouseX - targetX) * 0.02;
    targetY += (mouseY - targetY) * 0.02;
    camera.position.x = targetX * 1.2;
    camera.position.y = -targetY * 0.8;
    camera.lookAt(scene.position);

    renderer.render(scene, camera);
  }
  if (particleCount > 0) animate();

  window.addEventListener('resize', () => {
    camera.aspect = window.innerWidth/window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
  });

  window.addEventListener('beforeunload', () => {
    cancelAnimationFrame(rafId);
    geometry.dispose();
    material.dispose();
    renderer.dispose();
  });
})();

/* ---------------- GSAP ENTRANCE SEQUENCE ---------------- */
const introTl = gsap.timeline({defaults:{ease:'power3.out'}});

if (!reduceMotion){
  introTl
    .to('.hero-bg-video', {opacity:0.85, duration:1.6}, 0.1)
    .to('.hero-fg-video', {opacity:1, duration:1.8}, 0.5)
    .to('.hero-eyebrow', {opacity:1, y:0, duration:.8}, 1.2)
    .to('.hero-name span:nth-child(1) em', {y:'0%', opacity:1, duration:1.1}, 1.5)
    .to('.hero-name span:nth-child(2) em', {y:'0%', opacity:1, duration:1.1}, 1.7)
    .to('.hero-role', {opacity:1, y:0, duration:.9}, 2.15)
    .to('.hero-statement', {opacity:1, y:0, duration:.9}, 2.35)
    .to('.hero-socials', {opacity:1, duration:.8}, 2.4)
    .to('.hero-controls', {opacity:1, duration:.8}, 2.5)
    .to('#soundHint', {opacity:1, duration:.6}, 2.6)
    .to('.scroll-indicator', {opacity:1, duration:.8}, 2.7);

  gsap.set(['.hero-role','.hero-statement','.hero-eyebrow'], {y:16});
} else {
  gsap.set(['.hero-bg-video','.hero-fg-video','.hero-eyebrow','.hero-role','.hero-statement',
    '.hero-socials','.hero-controls','#soundHint','.scroll-indicator'], {opacity:1, y:0});
  document.querySelectorAll('.hero-name em').forEach(e => gsap.set(e, {y:'0%', opacity:1}));
}

/* ---------------- SCROLL REVEALS ---------------- */
if (!reduceMotion){
  gsap.utils.toArray('.reveal').forEach((el, i) => {
    gsap.to(el, {
      opacity:1, y:0, duration:.9, ease:'power3.out',
      scrollTrigger:{ trigger: el, start:'top 88%', toggleActions:'play none none none' }
    });
  });
} else {
  gsap.set('.reveal', {opacity:1, y:0});
}

/* ---------------- CERT FILTER ---------------- */
const certTabs = document.querySelectorAll('.cert-tab');
const certGroups = document.querySelectorAll('.cert-group');
certTabs.forEach(tab => {
  tab.addEventListener('click', () => {
    certTabs.forEach(t => t.classList.remove('active'));
    tab.classList.add('active');
    const filter = tab.dataset.filter;
    certGroups.forEach(g => {
      const show = filter === 'all' || g.dataset.group === filter;
      g.style.display = show ? '' : 'none';
    });
    ScrollTrigger.refresh();
  });
});
</script>
</body>
</html>
