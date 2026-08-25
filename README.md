<html lang="en" class="dark scroll-smooth">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>Prasad Thorat — Cybersecurity · AI · Software Engineering</title>
<meta name="description" content="Prasad Sudhir Thorat — B.Tech CSE, Cybersecurity Enthusiast, Aspiring Software Engineer & AI Tool Specialist. Explore interactive projects, certifications, and terminal.">

<!-- Fonts --> 
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300..700;1,9..144,300..700&family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@300;400;500;600&display=swap" rel="stylesheet">

<!-- Tailwind CSS -->
<script src="https://cdn.tailwindcss.com"></script>

<!-- Libraries: GSAP, ScrollTrigger, Three.js -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

<script>
  tailwind.config = {
    darkMode: 'class',
    theme: {
      extend: {
        colors: {
          dark: '#08080a',
          'dark-card': '#121115',
          'dark-border': 'rgba(244, 240, 232, 0.12)',
          accent: {
            DEFAULT: '#d98a4f',
            dim: '#8a5a35',
            glow: 'rgba(217, 138, 79, 0.25)',
          },
          cyber: {
            teal: '#00f2fe',
            green: '#10b981',
            purple: '#a855f7'
          }
        },
        fontFamily: {
          display: ['Fraunces', 'Georgia', 'serif'],
          sans: ['Inter', 'sans-serif'],
          mono: ['JetBrains Mono', 'monospace']
        }
      }
    }
  }
</script>

<style>
:root {
  --primary-accent: #d98a4f;
  --primary-accent-rgb: 217, 138, 79;
  --bg-main: #08080a;
  --card-bg: rgba(18, 17, 21, 0.7);
  --border-color: rgba(244, 240, 232, 0.12);
  --text-main: #f4f0e8;
  --text-muted: rgba(244, 240, 232, 0.65);
}

/* Theme Accents */
body[data-theme="teal"] {
  --primary-accent: #00e5ff;
  --primary-accent-rgb: 0, 229, 255;
}
body[data-theme="emerald"] {
  --primary-accent: #10b981;
  --primary-accent-rgb: 16, 185, 129;
}
body[data-theme="purple"] {
  --primary-accent: #b877fe;
  --primary-accent-rgb: 184, 119, 254;
}

body {
  background-color: var(--bg-main);
  color: var(--text-main);
  font-family: 'Inter', sans-serif;
  overflow-x: hidden;
  transition: background-color 0.4s ease, color 0.4s ease;
}

/* Custom Scrollbar */
::-webkit-scrollbar {
  width: 8px;
}
::-webkit-scrollbar-track {
  background: #08080a;
}
::-webkit-scrollbar-thumb {
  background: rgba(255, 255, 255, 0.15);
  border-radius: 4px;
}
::-webkit-scrollbar-thumb:hover {
  background: var(--primary-accent);
}

/* Glassmorphism Card */
.glass-panel {
  background: var(--card-bg);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border: 1px solid var(--border-color);
}

.glass-panel-hover {
  transition: transform 0.3s cubic-bezier(0.22, 1, 0.36, 1), border-color 0.3s ease, box-shadow 0.3s ease;
}
.glass-panel-hover:hover {
  border-color: var(--primary-accent);
  transform: translateY(-4px);
  box-shadow: 0 12px 30px -10px rgba(var(--primary-accent-rgb), 0.2);
}

/* Glowing text & border dynamic classes */
.text-accent-glow {
  color: var(--primary-accent);
  text-shadow: 0 0 12px rgba(var(--primary-accent-rgb), 0.4);
}
.border-accent-dynamic {
  border-color: var(--primary-accent);
}
.bg-accent-dynamic {
  background-color: var(--primary-accent);
}

/* Terminal Animation Cursor */
.terminal-cursor::after {
  content: '▋';
  animation: blink 1s infinite;
  color: var(--primary-accent);
}
@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

/* Custom Scanline for Cyber feel */
.scanline-bg {
  background: linear-gradient(
    to bottom,
    rgba(255, 255, 255, 0),
    rgba(255, 255, 255, 0) 50%,
    rgba(0, 0, 0, 0.25) 50%,
    rgba(0, 0, 0, 0.25)
  );
  background-size: 100% 4px;
}

/* Modal Blur Backing */
.modal-backdrop {
  background: rgba(4, 4, 6, 0.82);
  backdrop-filter: blur(12px);
}
</style>
</head>

<body class="selection:bg-amber-800/50 selection:text-white" data-theme="default">

<!-- NAVIGATION -->
<nav id="navbar" class="fixed top-0 left-0 right-0 z-50 transition-all duration-300 px-6 py-4">
  <div class="max-w-7xl mx-auto flex items-center justify-between">
    <!-- Brand / Logo -->
    <a href="#hero" class="flex items-center gap-2 font-mono font-bold text-lg tracking-wider text-white group">
      <span class="text-accent-glow">&gt;</span>
      <span class="group-hover:text-amber-400 transition-colors">PT_</span>
      <span class="inline-block w-2 h-2 rounded-full bg-emerald-500 animate-pulse ml-1" title="Available for hire/internship"></span>
    </a>

    <!-- Desktop Navigation Links -->
    <div class="hidden md:flex items-center gap-8 font-mono text-xs uppercase tracking-widest text-neutral-400">
      <a href="#about" class="hover:text-white transition-colors">About</a>
      <a href="#terminal-section" class="hover:text-white transition-colors">Terminal</a>
      <a href="#skills" class="hover:text-white transition-colors">Skills</a>
      <a href="#projects" class="hover:text-white transition-colors">Projects</a>
      <a href="#experience" class="hover:text-white transition-colors">Experience</a>
      <a href="#certifications" class="hover:text-white transition-colors">Certs</a>
      <a href="#contact" class="hover:text-white transition-colors">Contact</a>
    </div>

    <!-- Actions: Sound Toggle, Theme Switcher, Quick Contact -->
    <div class="flex items-center gap-3">
      <!-- Sound Synthesizer Toggle -->
      <button id="soundToggleBtn" aria-label="Toggle Cyber Sound Effects" title="Toggle Interactive Audio" 
              class="w-9 h-9 rounded-full glass-panel flex items-center justify-center text-neutral-300 hover:text-white hover:border-amber-500 transition-all">
        <svg id="soundIconOff" class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 5v14c0 .891-1.077 1.337-1.707.707L5.586 15z"></path>
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2"></path>
        </svg>
        <svg id="soundIconOn" class="w-4 h-4 hidden text-amber-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.536 8.464a5 5 0 010 7.072m2.828-9.9a9 9 0 010 12.728M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 5v14c0 .891-1.077 1.337-1.707.707L5.586 15z"></path>
        </svg>
      </button>

      <!-- Theme Switcher Menu -->
      <div class="relative group">
        <button aria-label="Theme Color Picker" class="w-9 h-9 rounded-full glass-panel flex items-center justify-center text-neutral-300 hover:text-white transition-all">
          <span class="w-3.5 h-3.5 rounded-full bg-accent-dynamic shadow-sm"></span>
        </button>
        <div class="absolute right-0 top-11 hidden group-hover:flex flex-col gap-2 p-2 rounded-xl glass-panel shadow-2xl border border-neutral-700/50 z-50">
          <button onclick="setTheme('default')" class="flex items-center gap-2 px-3 py-1.5 text-xs font-mono rounded-lg hover:bg-white/10 text-neutral-300">
            <span class="w-3 h-3 rounded-full bg-[#d98a4f]"></span> Ember
          </button>
          <button onclick="setTheme('teal')" class="flex items-center gap-2 px-3 py-1.5 text-xs font-mono rounded-lg hover:bg-white/10 text-neutral-300">
            <span class="w-3 h-3 rounded-full bg-[#00e5ff]"></span> Cyber Cyan
          </button>
          <button onclick="setTheme('emerald')" class="flex items-center gap-2 px-3 py-1.5 text-xs font-mono rounded-lg hover:bg-white/10 text-neutral-300">
            <span class="w-3 h-3 rounded-full bg-[#10b981]"></span> Matrix
          </button>
          <button onclick="setTheme('purple')" class="flex items-center gap-2 px-3 py-1.5 text-xs font-mono rounded-lg hover:bg-white/10 text-neutral-300">
            <span class="w-3 h-3 rounded-full bg-[#b877fe]"></span> Violet AI
          </button>
        </div>
      </div>

      <!-- Mobile Menu Toggle Button -->
      <button id="mobileNavToggle" aria-label="Open Navigation" class="md:hidden w-9 h-9 rounded-full glass-panel flex items-center justify-center text-neutral-300">
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
        </svg>
      </button>
    </div>
  </div>
</nav>

<!-- Mobile Navigation Drawer -->
<div id="mobileDrawer" class="fixed inset-0 z-40 bg-black/95 backdrop-blur-xl flex flex-col items-center justify-center gap-6 text-xl font-mono opacity-0 pointer-events-none transition-all duration-300 md:hidden">
  <button id="closeDrawerBtn" aria-label="Close Navigation" class="absolute top-6 right-6 text-neutral-400 hover:text-white p-2">✕</button>
  <a href="#about" class="drawer-link hover:text-amber-400">About</a>
  <a href="#terminal-section" class="drawer-link hover:text-amber-400">CLI Terminal</a>
  <a href="#skills" class="drawer-link hover:text-amber-400">Skills</a>
  <a href="#projects" class="drawer-link hover:text-amber-400">Projects</a>
  <a href="#experience" class="drawer-link hover:text-amber-400">Experience</a>
  <a href="#certifications" class="drawer-link hover:text-amber-400">Certifications</a>
  <a href="#contact" class="drawer-link hover:text-amber-400">Contact</a>
</div>

<!-- HERO SECTION -->
<section id="hero" class="relative min-h-screen flex items-center justify-center pt-24 pb-16 overflow-hidden">
  <!-- 3D Three.js WebGL Interactive Particle Canvas -->
  <canvas id="hero3dCanvas" class="absolute inset-0 z-0 w-full h-full pointer-events-auto"></canvas>

  <!-- Ambient Light Overlays & Vignette -->
  <div class="absolute inset-0 bg-radial-vignette pointer-events-none bg-[radial-gradient(circle_at_center,transparent_20%,#08080a_90%)] z-10"></div>
  <div class="absolute inset-0 bg-gradient-to-b from-transparent via-black/20 to-[#08080a] pointer-events-none z-10"></div>

  <!-- Content Container -->
  <div class="relative z-20 max-w-5xl mx-auto px-6 text-center md:text-left flex flex-col md:flex-row items-center justify-between gap-12">
    
    <div class="flex-1 space-y-6">
      <!-- Status Badge -->
      <div class="inline-flex items-center gap-2.5 px-3.5 py-1.5 rounded-full glass-panel text-xs font-mono text-neutral-300 border border-neutral-700/60">
        <span class="w-2 h-2 rounded-full bg-emerald-400 animate-ping"></span>
        <span class="tracking-wide">B.Tech Integrated CSE Student · Kopargaon, MH</span>
      </div>

      <!-- Main Name Heading -->
      <h1 class="font-display text-5xl sm:text-7xl lg:text-8xl font-normal tracking-tight leading-[0.9] text-white">
        PRASAD <br />
        <span class="font-normal italic text-accent-glow">THORAT</span>
      </h1>

      <!-- Typing & Dynamic Tagline -->
      <p class="font-mono text-sm sm:text-base text-neutral-300 max-w-xl leading-relaxed">
        Engineering secure software systems at the intersection of 
        <span class="text-white font-semibold underline decoration-amber-500/50">Cybersecurity</span>, 
        <span class="text-white font-semibold underline decoration-cyan-500/50">Artificial Intelligence</span> & 
        <span class="text-white font-semibold underline decoration-emerald-500/50">Cloud Networking</span>.
      </p>

      <!-- Key Quick Metrics -->
      <div class="grid grid-cols-3 gap-4 pt-2 max-w-lg border-t border-neutral-800">
        <div>
          <p class="text-2xl font-mono font-bold text-white">2+</p>
          <p class="text-[10px] font-mono uppercase text-neutral-400">Months Internship</p>
        </div>
        <div>
          <p class="text-2xl font-mono font-bold text-white">15+</p>
          <p class="text-[10px] font-mono uppercase text-neutral-400">Certifications</p>
        </div>
        <div>
          <p class="text-2xl font-mono font-bold text-white">90%</p>
          <p class="text-[10px] font-mono uppercase text-neutral-400">Quiz Benchmark</p>
        </div>
      </div>

      <!-- Action Buttons -->
      <div class="flex flex-wrap items-center gap-4 pt-4 justify-center md:justify-start">
        <a href="#projects" class="px-6 py-3 rounded-xl bg-accent-dynamic text-black font-mono font-medium text-xs uppercase tracking-wider hover:opacity-90 transition-all shadow-lg shadow-amber-500/10 flex items-center gap-2">
          <span>View Projects</span>
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"></path></svg>
        </a>
        <a href="#terminal-section" class="px-6 py-3 rounded-xl glass-panel text-white font-mono text-xs uppercase tracking-wider hover:border-amber-500/50 transition-all flex items-center gap-2">
          <span class="text-emerald-400">&gt;_</span> Launch Terminal
        </a>
      </div>
    </div>

    <!-- Quick Floating Hologram Card / Profile Accent -->
    <div class="w-full md:w-80 glass-panel rounded-2xl p-6 border border-neutral-800 relative group glass-panel-hover">
      <div class="absolute -top-3 -right-3 w-8 h-8 rounded-full bg-accent-dynamic text-black font-mono text-xs font-bold flex items-center justify-center shadow-lg">
        SU
      </div>
      <div class="space-y-4 font-mono text-xs text-neutral-300">
        <div class="flex items-center gap-3">
          <div class="w-10 h-10 rounded-xl bg-neutral-800 flex items-center justify-center font-bold text-amber-400 border border-neutral-700">
            PT
          </div>
          <div>
            <h3 class="font-sans font-semibold text-sm text-white">Prasad Sudhir Thorat</h3>
            <p class="text-[11px] text-neutral-400">Sanjivani University</p>
          </div>
        </div>
        <div class="h-px bg-neutral-800"></div>
        <div class="space-y-2 text-[11px]">
          <div class="flex justify-between"><span class="text-neutral-500">Program:</span><span class="text-white">B.Tech Integrated CSE</span></div>
          <div class="flex justify-between"><span class="text-neutral-500">Experience:</span><span class="text-white">InternsPort Cyber Intern</span></div>
          <div class="flex justify-between"><span class="text-neutral-500">Focus:</span><span class="text-amber-400">Forensics &amp; GenAI</span></div>
          <div class="flex justify-between"><span class="text-neutral-500">Status:</span><span class="text-emerald-400">Open to Opportunities</span></div>
        </div>
        <div class="pt-2 flex items-center justify-between text-[10px] text-neutral-500 border-t border-neutral-800/80">
          <span>Interactive 3D Node</span>
          <span class="animate-pulse text-amber-400">Drag to Rotate Scene</span>
        </div>
      </div>
    </div>

  </div>

  <!-- Down Indicator -->
  <a href="#about" aria-label="Scroll to About section" class="absolute bottom-6 left-1/2 -translate-x-1/2 z-20 text-neutral-500 hover:text-white transition-colors flex flex-col items-center gap-2 font-mono text-[10px] uppercase tracking-widest">
    <span>Scroll Down</span>
    <div class="w-4 h-8 rounded-full border border-neutral-700 flex justify-center p-1">
      <div class="w-1 h-2 bg-amber-500 rounded-full animate-bounce"></div>
    </div>
  </a>
</section>

<!-- INTERACTIVE CLI TERMINAL SECTION -->
<section id="terminal-section" class="py-20 px-6 relative bg-black/40 border-y border-neutral-900">
  <div class="max-w-4xl mx-auto">
    <div class="flex items-center justify-between mb-4">
      <div>
        <span class="font-mono text-xs uppercase tracking-widest text-amber-500">// Interactive Command Shell</span>
        <h2 class="font-display text-2xl text-white">Prasad's Terminal Console</h2>
      </div>
      <span class="hidden sm:inline-block font-mono text-xs text-neutral-500">Type <code class="text-amber-400">help</code> for commands</span>
    </div>

    <!-- Shell Window Container -->
    <div class="glass-panel rounded-2xl overflow-hidden border border-neutral-800 shadow-2xl font-mono text-xs sm:text-sm">
      <!-- Window Topbar -->
      <div class="bg-neutral-900/90 px-4 py-3 border-b border-neutral-800 flex items-center justify-between">
        <div class="flex items-center gap-2">
          <span class="w-3 h-3 rounded-full bg-red-500/80 inline-block"></span>
          <span class="w-3 h-3 rounded-full bg-yellow-500/80 inline-block"></span>
          <span class="w-3 h-3 rounded-full bg-green-500/80 inline-block"></span>
          <span class="ml-2 text-xs text-neutral-400">guest@prasad-thorat-node:~</span>
        </div>
        <div class="text-[10px] text-neutral-500 uppercase tracking-widest">Bash v5.2</div>
      </div>

      <!-- Terminal Output Screen -->
      <div id="terminalScreen" class="p-6 h-80 overflow-y-auto space-y-3 scanline-bg text-neutral-300 font-mono">
        <div class="text-neutral-400">Welcome to Prasad Thorat's interactive CLI portfolio v2.0.26</div>
        <div class="text-neutral-500">Type <span class="text-amber-400">help</span> to list available commands, <span class="text-amber-400">whoami</span> for bio, or <span class="text-amber-400">projects</span> to view code.</div>
      </div>

      <!-- Terminal Input Line -->
      <div class="bg-neutral-950 px-4 py-3 border-t border-neutral-800 flex items-center gap-2">
        <span class="text-emerald-400 font-bold">prasad@sec-box:~$</span>
        <input type="text" id="terminalInput" placeholder="Type command here..." 
               class="flex-1 bg-transparent text-white focus:outline-none font-mono text-xs sm:text-sm"
               autocomplete="off" />
        <button id="terminalSendBtn" class="px-3 py-1 rounded bg-neutral-800 hover:bg-neutral-700 text-xs text-neutral-300">Run</button>
      </div>
    </div>
  </div>
</section>

<!-- ABOUT SECTION -->
<section id="about" class="py-24 px-6 max-w-7xl mx-auto">
  <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-start">
    
    <!-- Left Column: Story & Vision -->
    <div class="lg:col-span-7 space-y-6">
      <div class="space-y-2">
        <p class="font-mono text-xs uppercase tracking-widest text-amber-500">// Personal Background</p>
        <h2 class="font-display text-3xl sm:text-5xl font-medium text-white leading-tight">
          Securing the digital frontier, <br />
          <span class="italic font-normal text-amber-400">one packet at a time.</span>
        </h2>
      </div>

      <p class="text-neutral-300 text-sm sm:text-base leading-relaxed font-sans">
        Currently pursuing a <strong class="text-white">B.Tech (Integrated) in Computer Science &amp; Engineering</strong> at Sanjivani University in Kopargaon, Maharashtra. My passion lies in blending core software craftsmanship with security analysis and generative AI workflows.
      </p>

      <p class="text-neutral-400 text-sm leading-relaxed">
        From analyzing packet structures and subnets to automating cloud container infrastructure on AWS ECS and testing generative models, I believe the future software engineer must be security-first and AI-augmented.
      </p>

      <!-- Highlights Grid -->
      <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 pt-4">
        <div class="p-4 rounded-xl glass-panel border-l-2 border-l-amber-500 space-y-1">
          <h4 class="font-mono text-xs font-bold text-white uppercase">Networking &amp; Subnetting</h4>
          <p class="text-xs text-neutral-400">Regular technical author on LinkedIn demystifying IP Addressing, CIDR, and network security.</p>
        </div>
        <div class="p-4 rounded-xl glass-panel border-l-2 border-l-emerald-500 space-y-1">
          <h4 class="font-mono text-xs font-bold text-white uppercase">Hands-on Forensics</h4>
          <p class="text-xs text-neutral-400">Completed digital forensics labs, incident handling exercises, and cybersecurity internships.</p>
        </div>
      </div>
    </div>

    <!-- Right Column: Fact Sheet & Quick Info -->
    <div class="lg:col-span-5 glass-panel rounded-2xl p-6 sm:p-8 space-y-6 border border-neutral-800">
      <h3 class="font-mono text-sm uppercase tracking-wider text-white border-b border-neutral-800 pb-3">Quick Dossier</h3>
      
      <div class="space-y-4 font-mono text-xs">
        <div class="flex justify-between items-start">
          <span class="text-neutral-500">Location</span>
          <span class="text-white text-right">Kopargaon, Maharashtra, India</span>
        </div>
        <div class="flex justify-between items-start">
          <span class="text-neutral-500">University</span>
          <span class="text-white text-right">Sanjivani University</span>
        </div>
        <div class="flex justify-between items-start">
          <span class="text-neutral-500">Degree</span>
          <span class="text-white text-right">B.Tech Integrated CSE (2nd Year)</span>
        </div>
        <div class="flex justify-between items-start">
          <span class="text-neutral-500">Internship</span>
          <span class="text-amber-400 text-right">InternsPort Innovation (Cybersecurity)</span>
        </div>
        <div class="flex justify-between items-start">
          <span class="text-neutral-500">Core Focus</span>
          <span class="text-white text-right">Cybersecurity · AI · C / Python</span>
        </div>
      </div>

      <div class="pt-4 border-t border-neutral-800">
        <p class="font-mono text-[11px] text-neutral-400 mb-3">Core Philosophy</p>
        <blockquote class="font-display italic text-sm text-neutral-200 border-l-2 border-amber-500 pl-3 py-1">
          "Build resilient systems, understand lower-level protocol behaviors, and continuously adapt with cutting-edge tools."
        </blockquote>
      </div>
    </div>

  </div>
</section>

<!-- SKILLS MATRIX SECTION -->
<section id="skills" class="py-24 px-6 bg-neutral-950/60 border-t border-neutral-900">
  <div class="max-w-7xl mx-auto space-y-12">
    
    <div class="text-center max-w-2xl mx-auto space-y-3">
      <span class="font-mono text-xs uppercase tracking-widest text-amber-500">// Technical Competencies</span>
      <h2 class="font-display text-3xl sm:text-5xl text-white">Skills &amp; Toolkit</h2>
      <p class="text-neutral-400 text-xs sm:text-sm">Filter through domain specialties or explore individual technology stacks.</p>
    </div>

    <!-- Skill Filter Tabs -->
    <div class="flex flex-wrap justify-center gap-2 font-mono text-xs">
      <button onclick="filterSkills('all')" class="skill-tab-btn px-4 py-2 rounded-full border border-amber-500 bg-amber-500 text-black font-semibold transition-all">All Skills</button>
      <button onclick="filterSkills('cyber')" class="skill-tab-btn px-4 py-2 rounded-full border border-neutral-800 glass-panel text-neutral-300 hover:border-amber-500 transition-all">Cybersecurity</button>
      <button onclick="filterSkills('ai')" class="skill-tab-btn px-4 py-2 rounded-full border border-neutral-800 glass-panel text-neutral-300 hover:border-amber-500 transition-all">AI &amp; GenAI</button>
      <button onclick="filterSkills('dev')" class="skill-tab-btn px-4 py-2 rounded-full border border-neutral-800 glass-panel text-neutral-300 hover:border-amber-500 transition-all">Programming &amp; Web</button>
      <button onclick="filterSkills('cloud')" class="skill-tab-btn px-4 py-2 rounded-full border border-neutral-800 glass-panel text-neutral-300 hover:border-amber-500 transition-all">Cloud &amp; DevOps</button>
    </div>

    <!-- Skills Grid -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6" id="skillsGrid">
      
      <!-- Skill Card 1: Programming -->
      <div class="skill-card glass-panel glass-panel-hover p-6 rounded-2xl space-y-4" data-category="dev">
        <div class="flex items-center justify-between">
          <span class="font-mono text-xs text-amber-400 uppercase tracking-wider">Languages</span>
          <span class="text-neutral-500 text-xs font-mono">01</span>
        </div>
        <h3 class="font-display text-xl text-white">Software Development</h3>
        <ul class="space-y-2 font-mono text-xs text-neutral-300">
          <li class="flex items-center justify-between"><span>C Programming</span><span class="text-emerald-400">Intermediate</span></li>
          <li class="flex items-center justify-between"><span>Python Scripting</span><span class="text-emerald-400">Intermediate</span></li>
          <li class="flex items-center justify-between"><span>HTML5 / Modern CSS</span><span class="text-emerald-400">Advanced</span></li>
          <li class="flex items-center justify-between"><span>Bash / Shell Scripting</span><span class="text-amber-400">Practicing</span></li>
        </ul>
      </div>

      <!-- Skill Card 2: Cybersecurity -->
      <div class="skill-card glass-panel glass-panel-hover p-6 rounded-2xl space-y-4" data-category="cyber">
        <div class="flex items-center justify-between">
          <span class="font-mono text-xs text-amber-400 uppercase tracking-wider">Defense &amp; Network</span>
          <span class="text-neutral-500 text-xs font-mono">02</span>
        </div>
        <h3 class="font-display text-xl text-white">Cybersecurity &amp; Forensics</h3>
        <ul class="space-y-2 font-mono text-xs text-neutral-300">
          <li class="flex items-center justify-between"><span>Digital Forensics Investigation</span><span class="text-emerald-400">Certified</span></li>
          <li class="flex items-center justify-between"><span>IP Subnetting &amp; Addressing</span><span class="text-emerald-400">Expertise</span></li>
          <li class="flex items-center justify-between"><span>Network Traffic Analysis</span><span class="text-amber-400">Practical</span></li>
          <li class="flex items-center justify-between"><span>Vulnerability Assessment</span><span class="text-amber-400">Foundational</span></li>
        </ul>
      </div>

      <!-- Skill Card 3: AI & GenAI -->
      <div class="skill-card glass-panel glass-panel-hover p-6 rounded-2xl space-y-4" data-category="ai">
        <div class="flex items-center justify-between">
          <span class="font-mono text-xs text-amber-400 uppercase tracking-wider">Generative Tooling</span>
          <span class="text-neutral-500 text-xs font-mono">03</span>
        </div>
        <h3 class="font-display text-xl text-white">Artificial Intelligence</h3>
        <ul class="space-y-2 font-mono text-xs text-neutral-300">
          <li class="flex items-center justify-between"><span>Claude AI &amp; Cowork</span><span class="text-emerald-400">Anthropic Cert</span></li>
          <li class="flex items-center justify-between"><span>Google GenAI Studio</span><span class="text-emerald-400">Certified</span></li>
          <li class="flex items-center justify-between"><span>ChatGPT / Prompt Eng.</span><span class="text-emerald-400">Advanced</span></li>
          <li class="flex items-center justify-between"><span>MS Excel AI Integration</span><span class="text-emerald-400">Certified</span></li>
        </ul>
      </div>

      <!-- Skill Card 4: Cloud & Infrastructure -->
      <div class="skill-card glass-panel glass-panel-hover p-6 rounded-2xl space-y-4" data-category="cloud">
        <div class="flex items-center justify-between">
          <span class="font-mono text-xs text-amber-400 uppercase tracking-wider">Infrastructure</span>
          <span class="text-neutral-500 text-xs font-mono">04</span>
        </div>
        <h3 class="font-display text-xl text-white">Cloud &amp; Systems</h3>
        <ul class="space-y-2 font-mono text-xs text-neutral-300">
          <li class="flex items-center justify-between"><span>AWS Elastic Container (ECS)</span><span class="text-emerald-400">Certified</span></li>
          <li class="flex items-center justify-between"><span>KodeKloud Cloud Labs</span><span class="text-emerald-400">Completed</span></li>
          <li class="flex items-center justify-between"><span>Linux Environment</span><span class="text-amber-400">Intermediate</span></li>
        </ul>
      </div>

      <!-- Skill Card 5: Soft Skills & Analytical -->
      <div class="skill-card glass-panel glass-panel-hover p-6 rounded-2xl space-y-4" data-category="dev">
        <div class="flex items-center justify-between">
          <span class="font-mono text-xs text-amber-400 uppercase tracking-wider">Professional</span>
          <span class="text-neutral-500 text-xs font-mono">05</span>
        </div>
        <h3 class="font-display text-xl text-white">Soft Skills &amp; Comms</h3>
        <ul class="space-y-2 font-mono text-xs text-neutral-300">
          <li class="flex items-center justify-between"><span>Technical Writing (LinkedIn)</span><span class="text-emerald-400">Active</span></li>
          <li class="flex items-center justify-between"><span>Problem Solving &amp; Logic</span><span class="text-emerald-400">Strong</span></li>
          <li class="flex items-center justify-between"><span>Hackathon Presentation</span><span class="text-emerald-400">SIH Team</span></li>
        </ul>
      </div>

    </div>
  </div>
</section>

<!-- PROJECTS & SHOWCASE SECTION -->
<section id="projects" class="py-24 px-6 max-w-7xl mx-auto">
  <div class="space-y-12">
    <div class="flex flex-col md:flex-row md:items-end justify-between gap-4">
      <div class="space-y-2">
        <span class="font-mono text-xs uppercase tracking-widest text-amber-500">// Hands-On Proof</span>
        <h2 class="font-display text-3xl sm:text-5xl text-white">Featured Projects</h2>
      </div>
      <p class="text-neutral-400 text-xs font-mono max-w-md">Interactive simulations &amp; implementations representing academic, security, and AI tool experiments.</p>
    </div>

    <!-- Projects Grid -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
      
      <!-- Project Card 1: Subnet & IP Calculator -->
      <div class="glass-panel glass-panel-hover rounded-2xl overflow-hidden border border-neutral-800 flex flex-col justify-between p-6 space-y-6">
        <div class="space-y-4">
          <div class="flex items-center justify-between text-xs font-mono">
            <span class="text-amber-400 uppercase">Networking Tool</span>
            <span class="text-neutral-500">Python / Web</span>
          </div>
          <h3 class="font-display text-2xl text-white">Interactive IP &amp; Subnet Calculator</h3>
          <p class="text-xs text-neutral-400 leading-relaxed">
            A practical tool for calculating network ranges, broadcast addresses, wildcard masks, and CIDR subnets. Born from LinkedIn educational posts.
          </p>
          <div class="flex flex-wrap gap-2 pt-2">
            <span class="px-2.5 py-1 rounded bg-neutral-800 text-[10px] font-mono text-neutral-300">Networking</span>
            <span class="px-2.5 py-1 rounded bg-neutral-800 text-[10px] font-mono text-neutral-300">IPv4 / Subnetting</span>
            <span class="px-2.5 py-1 rounded bg-neutral-800 text-[10px] font-mono text-neutral-300">Python</span>
          </div>
        </div>
        <button onclick="openProjectModal('subnet')" class="w-full py-2.5 rounded-xl glass-panel text-xs font-mono text-amber-400 hover:bg-amber-500 hover:text-black transition-all">
          Inspect Project Details &rarr;
        </button>
      </div>

      <!-- Project Card 2: Digital Forensics Incident Analysis -->
      <div class="glass-panel glass-panel-hover rounded-2xl overflow-hidden border border-neutral-800 flex flex-col justify-between p-6 space-y-6">
        <div class="space-y-4">
          <div class="flex items-center justify-between text-xs font-mono">
            <span class="text-amber-400 uppercase">Forensics Lab</span>
            <span class="text-neutral-500">Security</span>
          </div>
          <h3 class="font-display text-2xl text-white">Digital Forensics Investigation Suite</h3>
          <p class="text-xs text-neutral-400 leading-relaxed">
            Hands-on investigation workflow developed during Indian Cyber Club workshops for analyzing memory dumps and disk artifacts.
          </p>
          <div class="flex flex-wrap gap-2 pt-2">
            <span class="px-2.5 py-1 rounded bg-neutral-800 text-[10px] font-mono text-neutral-300">Forensics</span>
            <span class="px-2.5 py-1 rounded bg-neutral-800 text-[10px] font-mono text-neutral-300">Incident Analysis</span>
            <span class="px-2.5 py-1 rounded bg-neutral-800 text-[10px] font-mono text-neutral-300">Cybersecurity</span>
          </div>
        </div>
        <button onclick="openProjectModal('forensics')" class="w-full py-2.5 rounded-xl glass-panel text-xs font-mono text-amber-400 hover:bg-amber-500 hover:text-black transition-all">
          Inspect Project Details &rarr;
        </button>
      </div>

      <!-- Project Card 3: GenAI Prompt & Automation Suite -->
      <div class="glass-panel glass-panel-hover rounded-2xl overflow-hidden border border-neutral-800 flex flex-col justify-between p-6 space-y-6">
        <div class="space-y-4">
          <div class="flex items-center justify-between text-xs font-mono">
            <span class="text-amber-400 uppercase">AI &amp; Automation</span>
            <span class="text-neutral-500">Generative AI</span>
          </div>
          <h3 class="font-display text-2xl text-white">GenAI Workflow &amp; Productivity Studio</h3>
          <p class="text-xs text-neutral-400 leading-relaxed">
            Automating spreadsheet analytics and daily developer tasks using Claude Cowork and OpenAI API integrations built during GenAI Buildathon.
          </p>
          <div class="flex flex-wrap gap-2 pt-2">
            <span class="px-2.5 py-1 rounded bg-neutral-800 text-[10px] font-mono text-neutral-300">Claude AI</span>
            <span class="px-2.5 py-1 rounded bg-neutral-800 text-[10px] font-mono text-neutral-300">Excel AI</span>
            <span class="px-2.5 py-1 rounded bg-neutral-800 text-[10px] font-mono text-neutral-300">Automation</span>
          </div>
        </div>
        <button onclick="openProjectModal('genai')" class="w-full py-2.5 rounded-xl glass-panel text-xs font-mono text-amber-400 hover:bg-amber-500 hover:text-black transition-all">
          Inspect Project Details &rarr;
        </button>
      </div>

    </div>
  </div>
</section>

<!-- EXPERIENCE & TIMELINE SECTION -->
<section id="experience" class="py-24 px-6 bg-neutral-950/40 border-t border-neutral-900">
  <div class="max-w-5xl mx-auto space-y-12">
    <div class="space-y-2 text-center">
      <span class="font-mono text-xs uppercase tracking-widest text-amber-500">// Work Experience &amp; Milestones</span>
      <h2 class="font-display text-3xl sm:text-5xl text-white">Experience Timeline</h2>
    </div>

    <!-- Timeline Container -->
    <div class="relative pl-6 sm:pl-10 border-l border-neutral-800 space-y-12">
      
      <!-- Timeline Item 1: Internship -->
      <div class="relative group">
        <!-- Node Dot -->
        <div class="absolute -left-[31px] sm:-left-[47px] top-1.5 w-4 h-4 rounded-full bg-amber-500 border-4 border-[#08080a] group-hover:scale-125 transition-transform"></div>
        
        <div class="glass-panel p-6 sm:p-8 rounded-2xl border border-neutral-800 space-y-4">
          <div class="flex flex-wrap items-center justify-between gap-2 font-mono text-xs">
            <span class="text-amber-400 uppercase font-semibold">Feb 2026 — Apr 2026</span>
            <span class="px-3 py-1 rounded-full bg-emerald-500/10 text-emerald-400 border border-emerald-500/20">Verified LOR</span>
          </div>
          
          <div>
            <h3 class="font-display text-2xl text-white">Cybersecurity Intern</h3>
            <p class="text-xs font-mono text-neutral-400">InternsPort Innovation Pvt. Ltd.</p>
          </div>

          <ul class="space-y-2 text-xs sm:text-sm text-neutral-300 list-disc list-inside leading-relaxed">
            <li>Engaged in a comprehensive 2-month cybersecurity internship covering threat detection, analytical defense, and system auditing.</li>
            <li>Demonstrated problem-solving abilities and effective cross-team communication in security handling.</li>
            <li>Received official Letter of Recommendation from Head of Operations for exceptional initiative.</li>
          </ul>
        </div>
      </div>

      <!-- Timeline Item 2: SIH Hackathon -->
      <div class="relative group">
        <div class="absolute -left-[31px] sm:-left-[47px] top-1.5 w-4 h-4 rounded-full bg-neutral-700 border-4 border-[#08080a] group-hover:bg-amber-500 transition-colors"></div>
        
        <div class="glass-panel p-6 sm:p-8 rounded-2xl border border-neutral-800 space-y-4">
          <div class="font-mono text-xs text-neutral-400">Academic Year 2025 - 2026</div>
          <div>
            <h3 class="font-display text-2xl text-white">Smart India Hackathon — Internal Round</h3>
            <p class="text-xs font-mono text-neutral-400">Sanjivani University · Team "Code Warriors"</p>
          </div>
          <p class="text-xs sm:text-sm text-neutral-300 leading-relaxed">
            Selected for internal presentation rounds presenting creative solutions and software architecture proposals.
          </p>
        </div>
      </div>

      <!-- Timeline Item 3: Techfest IIT Bombay -->
      <div class="relative group">
        <div class="absolute -left-[31px] sm:-left-[47px] top-1.5 w-4 h-4 rounded-full bg-neutral-700 border-4 border-[#08080a] group-hover:bg-amber-500 transition-colors"></div>
        
        <div class="glass-panel p-6 sm:p-8 rounded-2xl border border-neutral-800 space-y-4">
          <div class="font-mono text-xs text-neutral-400">National Workshop</div>
          <div>
            <h3 class="font-display text-2xl text-white">Artificial Intelligence Workshop</h3>
            <p class="text-xs font-mono text-neutral-400">Techfest, IIT Bombay</p>
          </div>
          <p class="text-xs sm:text-sm text-neutral-300 leading-relaxed">
            Attended intensive hands-on sessions on modern machine learning trends and practical AI implementation paradigms at IIT Bombay.
          </p>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- CERTIFICATIONS & CREDENTIALS SECTION -->
<section id="certifications" class="py-24 px-6 max-w-7xl mx-auto">
  <div class="space-y-10">
    
    <div class="flex flex-col md:flex-row md:items-end justify-between gap-6">
      <div class="space-y-2">
        <span class="font-mono text-xs uppercase tracking-widest text-amber-500">// Proof of Continuous Learning</span>
        <h2 class="font-display text-3xl sm:text-5xl text-white">Certifications &amp; Badges</h2>
      </div>

      <!-- Live Search Filter for Certifications -->
      <div class="w-full md:w-72">
        <input type="text" id="certSearchInput" placeholder="Search certs (e.g., Python, AWS, AI)..." 
               class="w-full px-4 py-2.5 rounded-xl glass-panel text-xs font-mono text-white placeholder-neutral-500 focus:outline-none focus:border-amber-500 transition-all border border-neutral-800" />
      </div>
    </div>

    <!-- Certification Filter Categories -->
    <div class="flex flex-wrap gap-2 font-mono text-xs">
      <button onclick="filterCerts('all')" class="cert-tab-btn px-3.5 py-1.5 rounded-full border border-amber-500 bg-amber-500 text-black font-semibold">All</button>
      <button onclick="filterCerts('ai')" class="cert-tab-btn px-3.5 py-1.5 rounded-full border border-neutral-800 glass-panel text-neutral-300 hover:border-amber-500">AI &amp; GenAI</button>
      <button onclick="filterCerts('cloud')" class="cert-tab-btn px-3.5 py-1.5 rounded-full border border-neutral-800 glass-panel text-neutral-300 hover:border-amber-500">Cloud &amp; DevOps</button>
      <button onclick="filterCerts('code')" class="cert-tab-btn px-3.5 py-1.5 rounded-full border border-neutral-800 glass-panel text-neutral-300 hover:border-amber-500">Programming</button>
      <button onclick="filterCerts('cyber')" class="cert-tab-btn px-3.5 py-1.5 rounded-full border border-neutral-800 glass-panel text-neutral-300 hover:border-amber-500">Cybersecurity</button>
    </div>

    <!-- Certs Grid -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4" id="certsContainer">
      
      <!-- Cert Item -->
      <div class="cert-card glass-panel glass-panel-hover p-5 rounded-xl border border-neutral-800 flex flex-col justify-between space-y-3" data-category="cloud" data-name="AWS Elastic Container Service ECS KodeKloud">
        <div class="space-y-1">
          <span class="text-[10px] font-mono text-amber-400 uppercase">KodeKloud</span>
          <h4 class="font-sans font-semibold text-sm text-white">AWS Elastic Container Service (ECS)</h4>
        </div>
        <span class="text-[10px] font-mono text-neutral-500">Verified Credentials</span>
      </div>

      <div class="cert-card glass-panel glass-panel-hover p-5 rounded-xl border border-neutral-800 flex flex-col justify-between space-y-3" data-category="ai" data-name="AI Fluency Capabilities Limitations Anthropic Claude">
        <div class="space-y-1">
          <span class="text-[10px] font-mono text-amber-400 uppercase">Anthropic</span>
          <h4 class="font-sans font-semibold text-sm text-white">AI Fluency: AI Capabilities &amp; Limitations</h4>
        </div>
        <span class="text-[10px] font-mono text-neutral-500">Anthropic Education</span>
      </div>

      <div class="cert-card glass-panel glass-panel-hover p-5 rounded-xl border border-neutral-800 flex flex-col justify-between space-y-3" data-category="ai" data-name="Claude 101 Cowork Anthropic">
        <div class="space-y-1">
          <span class="text-[10px] font-mono text-amber-400 uppercase">Anthropic</span>
          <h4 class="font-sans font-semibold text-sm text-white">Claude 101 &amp; Intro to Claude Cowork</h4>
        </div>
        <span class="text-[10px] font-mono text-neutral-500">Verified Badge</span>
      </div>

      <div class="cert-card glass-panel glass-panel-hover p-5 rounded-xl border border-neutral-800 flex flex-col justify-between space-y-3" data-category="code" data-name="Introduction Python Fundamentals Infosys Springboard">
        <div class="space-y-1">
          <span class="text-[10px] font-mono text-amber-400 uppercase">Infosys Springboard</span>
          <h4 class="font-sans font-semibold text-sm text-white">Python Fundamentals &amp; Intro to Python</h4>
        </div>
        <span class="text-[10px] font-mono text-neutral-500">Infosys Certification</span>
      </div>

      <div class="cert-card glass-panel glass-panel-hover p-5 rounded-xl border border-neutral-800 flex flex-col justify-between space-y-3" data-category="cyber" data-name="Cybersecurity Mastery Unstop">
        <div class="space-y-1">
          <span class="text-[10px] font-mono text-amber-400 uppercase">Unstop</span>
          <h4 class="font-sans font-semibold text-sm text-white">Cybersecurity Mastery</h4>
        </div>
        <span class="text-[10px] font-mono text-neutral-500">Certificate of Completion</span>
      </div>

      <div class="cert-card glass-panel glass-panel-hover p-5 rounded-xl border border-neutral-800 flex flex-col justify-between space-y-3" data-category="cyber" data-name="Digital Forensics Investigation Indian Cyber Club">
        <div class="space-y-1">
          <span class="text-[10px] font-mono text-amber-400 uppercase">Indian Cyber Club</span>
          <h4 class="font-sans font-semibold text-sm text-white">Hands-on Digital Forensics Workshop</h4>
        </div>
        <span class="text-[10px] font-mono text-neutral-500">Practical Forensics Lab</span>
      </div>

      <div class="cert-card glass-panel glass-panel-hover p-5 rounded-xl border border-neutral-800 flex flex-col justify-between space-y-3" data-category="code" data-name="Master C Language SoloLearn Programming Academy">
        <div class="space-y-1">
          <span class="text-[10px] font-mono text-amber-400 uppercase">Sololearn / Academy</span>
          <h4 class="font-sans font-semibold text-sm text-white">Master C Language &amp; Programming</h4>
        </div>
        <span class="text-[10px] font-mono text-neutral-500">Verified Course</span>
      </div>

      <div class="cert-card glass-panel glass-panel-hover p-5 rounded-xl border border-neutral-800 flex flex-col justify-between space-y-3" data-category="ai" data-name="Bring AI to Work Google Workspace Generative AI Studio">
        <div class="space-y-1">
          <span class="text-[10px] font-mono text-amber-400 uppercase">Google / Simplilearn</span>
          <h4 class="font-sans font-semibold text-sm text-white">Bring AI to Work &amp; GenAI Studio</h4>
        </div>
        <span class="text-[10px] font-mono text-neutral-500">Workshop Credentials</span>
      </div>

      <div class="cert-card glass-panel glass-panel-hover p-5 rounded-xl border border-neutral-800 flex flex-col justify-between space-y-3" data-category="ai" data-name="Excel AI OfficeMaster">
        <div class="space-y-1">
          <span class="text-[10px] font-mono text-amber-400 uppercase">OfficeMaster</span>
          <h4 class="font-sans font-semibold text-sm text-white">Microsoft Excel Using AI Certification</h4>
        </div>
        <span class="text-[10px] font-mono text-neutral-500">AI Productivity Suite</span>
      </div>

    </div>
  </div>
</section>

<!-- FLOATING AI ASSISTANT CHAT BOT -->
<div id="aiChatWidget" class="fixed bottom-6 right-6 z-40 flex flex-col items-end">
  
  <!-- Chat Popup Window -->
  <div id="chatBox" class="hidden w-80 sm:w-96 rounded-2xl glass-panel border border-neutral-800 shadow-2xl mb-4 overflow-hidden font-mono text-xs flex-col transition-all duration-300">
    <!-- Chat Header -->
    <div class="bg-neutral-900 p-4 border-b border-neutral-800 flex items-center justify-between">
      <div class="flex items-center gap-2">
        <span class="w-2.5 h-2.5 rounded-full bg-emerald-400 animate-pulse"></span>
        <span class="font-bold text-white text-xs">Prasad AI Assistant</span>
      </div>
      <button onclick="toggleChat()" class="text-neutral-400 hover:text-white">✕</button>
    </div>

    <!-- Messages Area -->
    <div id="chatMessages" class="p-4 h-64 overflow-y-auto space-y-3 text-neutral-300">
      <div class="p-3 rounded-xl bg-neutral-800/80 max-w-[85%] text-xs leading-relaxed">
        Hello! I'm Prasad's AI assistant. Ask me about his cybersecurity internship, programming skills, or university projects!
      </div>
    </div>

    <!-- Quick Prompts -->
    <div class="p-2 bg-neutral-950/80 border-t border-neutral-900 flex gap-1 overflow-x-auto text-[10px]">
      <button onclick="askBot('What is Prasad studying?')" class="px-2 py-1 rounded bg-neutral-800 text-neutral-300 hover:bg-neutral-700 whitespace-nowrap">Education?</button>
      <button onclick="askBot('Tell me about his internship.')" class="px-2 py-1 rounded bg-neutral-800 text-neutral-300 hover:bg-neutral-700 whitespace-nowrap">Internship?</button>
      <button onclick="askBot('What are his certs?')" class="px-2 py-1 rounded bg-neutral-800 text-neutral-300 hover:bg-neutral-700 whitespace-nowrap">Certs?</button>
    </div>

    <!-- Input Box -->
    <div class="p-3 bg-neutral-950 border-t border-neutral-800 flex items-center gap-2">
      <input type="text" id="chatInput" placeholder="Ask anything..." 
             class="flex-1 bg-transparent text-white focus:outline-none text-xs" 
             onkeydown="if(event.key==='Enter') sendChatMessage()" />
      <button onclick="sendChatMessage()" class="text-amber-400 hover:text-amber-300 font-bold px-2">Send</button>
    </div>
  </div>

  <!-- Toggle Button -->
  <button onclick="toggleChat()" aria-label="Open Prasad AI Chatbot" class="px-4 py-3 rounded-full bg-accent-dynamic text-black font-mono font-bold text-xs uppercase tracking-wider shadow-2xl hover:scale-105 transition-all flex items-center gap-2">
    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 10h.01M12 10h.01M16 10h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z"></path></svg>
    <span>Ask Prasad AI</span>
  </button>
</div>

<!-- CONTACT & CONNECT SECTION -->
<section id="contact" class="py-24 px-6 border-t border-neutral-900 bg-neutral-950/80 relative">
  <div class="max-w-4xl mx-auto space-y-12 text-center">
    
    <div class="space-y-3">
      <span class="font-mono text-xs uppercase tracking-widest text-amber-500">// Get In Touch</span>
      <h2 class="font-display text-4xl sm:text-6xl text-white">Let's Connect</h2>
      <p class="text-neutral-400 text-xs sm:text-sm max-w-lg mx-auto">
        Interested in cybersecurity collaboration, software projects, or academic discussions? Drop a message below.
      </p>
    </div>

    <!-- Contact Form -->
    <form id="contactForm" onsubmit="handleContactSubmit(event)" class="glass-panel p-8 rounded-2xl border border-neutral-800 text-left space-y-4 max-w-xl mx-auto">
      <div class="space-y-1">
        <label class="font-mono text-xs text-neutral-400 uppercase">Your Name</label>
        <input type="text" required placeholder="John Doe" 
               class="w-full px-4 py-2.5 rounded-xl bg-neutral-900/90 text-xs font-mono text-white border border-neutral-800 focus:outline-none focus:border-amber-500" />
      </div>
      <div class="space-y-1">
        <label class="font-mono text-xs text-neutral-400 uppercase">Your Email</label>
        <input type="email" required placeholder="john@example.com" 
               class="w-full px-4 py-2.5 rounded-xl bg-neutral-900/90 text-xs font-mono text-white border border-neutral-800 focus:outline-none focus:border-amber-500" />
      </div>
      <div class="space-y-1">
        <label class="font-mono text-xs text-neutral-400 uppercase">Message</label>
        <textarea rows="4" required placeholder="Hello Prasad..." 
                  class="w-full px-4 py-2.5 rounded-xl bg-neutral-900/90 text-xs font-mono text-white border border-neutral-800 focus:outline-none focus:border-amber-500"></textarea>
      </div>
      <button type="submit" class="w-full py-3 rounded-xl bg-accent-dynamic text-black font-mono font-bold text-xs uppercase tracking-wider hover:opacity-90 transition-all">
        Send Message
      </button>
      <p id="formFeedback" class="hidden text-xs font-mono text-center text-emerald-400 pt-2"></p>
    </form>

    <!-- Social Action Badges -->
    <div class="flex flex-wrap justify-center items-center gap-4 pt-4 font-mono text-xs">
      <a href="https://www.linkedin.com/in/prasad-thorat-a38578372" target="_blank" rel="noopener noreferrer" 
         class="px-5 py-2.5 rounded-xl glass-panel border border-neutral-800 hover:border-amber-500 text-neutral-300 hover:text-white transition-all flex items-center gap-2">
        LinkedIn &rarr;
      </a>
      <a href="https://github.com/prasadthorat25uid-arch" target="_blank" rel="noopener noreferrer" 
         class="px-5 py-2.5 rounded-xl glass-panel border border-neutral-800 hover:border-amber-500 text-neutral-300 hover:text-white transition-all flex items-center gap-2">
        GitHub &rarr;
      </a>
      <a href="https://wa.me/918010989708" target="_blank" rel="noopener noreferrer" 
         class="px-5 py-2.5 rounded-xl glass-panel border border-neutral-800 hover:border-amber-500 text-neutral-300 hover:text-white transition-all flex items-center gap-2">
        WhatsApp &rarr;
      </a>
    </div>

  </div>
</section>

<!-- FOOTER -->
<footer class="py-8 px-6 border-t border-neutral-900 text-center font-mono text-xs text-neutral-500">
  <div class="max-w-7xl mx-auto flex flex-col sm:flex-row items-center justify-between gap-4">
    <p>© 2026 Prasad Sudhir Thorat. All rights reserved.</p>
    <p>Sanjivani University · Kopargaon, MH</p>
  </div>
</footer>

<!-- PROJECT DETAILS MODAL -->
<div id="projectModal" class="fixed inset-0 z-50 modal-backdrop hidden items-center justify-center p-6">
  <div class="glass-panel max-w-2xl w-full p-8 rounded-2xl border border-neutral-800 space-y-6 relative max-h-[85vh] overflow-y-auto">
    <button onclick="closeProjectModal()" class="absolute top-6 right-6 text-neutral-400 hover:text-white font-mono text-sm">✕</button>
    <div id="modalContent"></div>
  </div>
</div>

<!-- JAVASCRIPT & INTERACTIVE ENGINES -->
<script>
// WEB AUDIO SYNTHESIZER SOUND ENGINE
let audioCtx = null;
let soundEnabled = false;

function initAudio() {
  if (!audioCtx) {
    audioCtx = new (window.AudioContext || window.webkitAudioContext)();
  }
}

function playSound(freq = 440, type = 'sine', duration = 0.08) {
  if (!soundEnabled || !audioCtx) return;
  try {
    const osc = audioCtx.createOscillator();
    const gain = audioCtx.createGain();
    osc.type = type;
    osc.frequency.setValueAtTime(freq, audioCtx.currentTime);
    gain.gain.setValueAtTime(0.05, audioCtx.currentTime);
    gain.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + duration);
    osc.connect(gain);
    gain.connect(audioCtx.destination);
    osc.start();
    osc.stop(audioCtx.currentTime + duration);
  } catch(e){}
}

document.getElementById('soundToggleBtn').addEventListener('click', () => {
  initAudio();
  soundEnabled = !soundEnabled;
  document.getElementById('soundIconOff').classList.toggle('hidden', soundEnabled);
  document.getElementById('soundIconOn').classList.toggle('hidden', !soundEnabled);
  if (soundEnabled) playSound(880, 'sine', 0.12);
});

// Sound triggers on buttons
document.querySelectorAll('button, a').forEach(el => {
  el.addEventListener('mouseenter', () => playSound(600, 'sine', 0.04));
  el.addEventListener('click', () => playSound(400, 'triangle', 0.08));
});

// THREE.JS 3D HERO CANVAS
(function initThreeJS() {
  const canvas = document.getElementById('hero3dCanvas');
  if (!canvas || !window.THREE) return;

  const renderer = new THREE.WebGLRenderer({ canvas, alpha: true, antialias: true });
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
  renderer.setSize(window.innerWidth, window.innerHeight);

  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(60, window.innerWidth / window.innerHeight, 0.1, 1000);
  camera.position.z = 25;

  // Nodes & Particles
  const count = 120;
  const geometry = new THREE.BufferGeometry();
  const positions = new Float32Array(count * 3);
  const velocities = [];

  for (let i = 0; i < count; i++) {
    positions[i * 3] = (Math.random() - 0.5) * 40;
    positions[i * 3 + 1] = (Math.random() - 0.5) * 40;
    positions[i * 3 + 2] = (Math.random() - 0.5) * 30;
    velocities.push({
      x: (Math.random() - 0.5) * 0.02,
      y: (Math.random() - 0.5) * 0.02,
      z: (Math.random() - 0.5) * 0.02
    });
  }

  geometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));

  const material = new THREE.PointsMaterial({
    color: 0xd98a4f,
    size: 0.6,
    transparent: true,
    opacity: 0.75
  });

  const points = new THREE.Points(geometry, material);
  scene.add(points);

  // Central Rotating Wireframe Icosahedron
  const icoGeo = new THREE.IcosahedronGeometry(7, 1);
  const icoMat = new THREE.MeshBasicMaterial({
    color: 0xd98a4f,
    wireframe: true,
    transparent: true,
    opacity: 0.15
  });
  const icoMesh = new THREE.Mesh(icoGeo, icoMat);
  scene.add(icoMesh);

  // Mouse Parallax
  let mouseX = 0, mouseY = 0;
  window.addEventListener('mousemove', (e) => {
    mouseX = (e.clientX / window.innerWidth - 0.5) * 2;
    mouseY = (e.clientY / window.innerHeight - 0.5) * 2;
  });

  // Animation Loop
  function animate() {
    requestAnimationFrame(animate);

    icoMesh.rotation.x += 0.002;
    icoMesh.rotation.y += 0.003;

    const pos = geometry.attributes.position.array;
    for (let i = 0; i < count; i++) {
      pos[i * 3] += velocities[i].x;
      pos[i * 3 + 1] += velocities[i].y;
      pos[i * 3 + 2] += velocities[i].z;

      if (Math.abs(pos[i * 3]) > 25) velocities[i].x *= -1;
      if (Math.abs(pos[i * 3 + 1]) > 25) velocities[i].y *= -1;
      if (Math.abs(pos[i * 3 + 2]) > 20) velocities[i].z *= -1;
    }
    geometry.attributes.position.needsUpdate = true;

    camera.position.x += (mouseX * 3 - camera.position.x) * 0.05;
    camera.position.y += (-mouseY * 3 - camera.position.y) * 0.05;
    camera.lookAt(scene.position);

    renderer.render(scene, camera);
  }
  animate();

  window.addEventListener('resize', () => {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
  });
})();

// CLI TERMINAL LOGIC
const terminalInput = document.getElementById('terminalInput');
const terminalScreen = document.getElementById('terminalScreen');
const terminalSendBtn = document.getElementById('terminalSendBtn');

const COMMANDS = {
  help: 'Available commands: whoami, skills, projects, certs, contact, clear, matrix',
  whoami: 'Prasad Sudhir Thorat — B.Tech Integrated CSE student at Sanjivani University. Focused on Cybersecurity, AI tools, and Software Engineering.',
  skills: 'Programming: C, Python, HTML/CSS\nCybersecurity: Digital Forensics, Subnetting, IPv4\nCloud: AWS ECS, KodeKloud\nAI: Claude AI, GenAI Studio, ChatGPT',
  projects: '1. Subnet & IP Calculator\n2. Digital Forensics Suite\n3. GenAI Productivity Studio',
  certs: 'Certifications across Anthropic, AWS, Infosys Springboard, Unstop Cybersecurity, Sololearn, and NISM.',
  contact: 'LinkedIn: linkedin.com/in/prasad-thorat-a38578372\nGitHub: github.com/prasadthorat25uid-arch\nWhatsApp: +91 8010989708',
  matrix: 'Wake up, Neo... The matrix has you.',
};

function executeCommand() {
  const val = terminalInput.value.trim().toLowerCase();
  if (!val) return;

  const line = document.createElement('div');
  line.className = 'text-amber-400';
  line.textContent = `prasad@sec-box:~$ ${val}`;
  terminalScreen.appendChild(line);

  if (val === 'clear') {
    terminalScreen.innerHTML = '';
  } else if (COMMANDS[val]) {
    const resp = document.createElement('div');
    resp.className = 'text-neutral-300 whitespace-pre-line text-xs pl-2 border-l border-amber-500/40';
    resp.textContent = COMMANDS[val];
    terminalScreen.appendChild(resp);
  } else {
    const err = document.createElement('div');
    err.className = 'text-red-400 text-xs';
    err.textContent = `Command not found: '${val}'. Type 'help' for commands.`;
    terminalScreen.appendChild(err);
  }

  terminalInput.value = '';
  terminalScreen.scrollTop = terminalScreen.scrollHeight;
  playSound(700, 'sine', 0.05);
}

terminalInput?.addEventListener('keydown', (e) => { if (e.key === 'Enter') executeCommand(); });
terminalSendBtn?.addEventListener('click', executeCommand);

// THEME SWITCHER
function setTheme(themeName) {
  if (themeName === 'default') document.body.removeAttribute('data-theme');
  else document.body.setAttribute('data-theme', themeName);
  playSound(800, 'triangle', 0.1);
}

// SKILLS FILTERING
function filterSkills(cat) {
  const cards = document.querySelectorAll('#skillsGrid .skill-card');
  cards.forEach(card => {
    if (cat === 'all' || card.dataset.category === cat) card.style.display = 'block';
    else card.style.display = 'none';
  });
}

// CERTIFICATE FILTER & SEARCH
function filterCerts(cat) {
  const certs = document.querySelectorAll('#certsContainer .cert-card');
  certs.forEach(cert => {
    if (cat === 'all' || cert.dataset.category === cat) cert.style.display = 'flex';
    else cert.style.display = 'none';
  });
}

document.getElementById('certSearchInput')?.addEventListener('input', (e) => {
  const q = e.target.value.toLowerCase();
  const certs = document.querySelectorAll('#certsContainer .cert-card');
  certs.forEach(cert => {
    const name = cert.dataset.name.toLowerCase();
    if (name.includes(q)) cert.style.display = 'flex';
    else cert.style.display = 'none';
  });
});

// PROJECT MODAL
function openProjectModal(type) {
  const modal = document.getElementById('projectModal');
  const content = document.getElementById('modalContent');

  const data = {
    subnet: {
      title: 'Interactive IP & Subnet Calculator',
      tech: 'Python / IPv4 Networking',
      desc: 'Detailed breakdown of IPv4 address classification, CIDR mask calculations, broadcast address calculation, and host capacity evaluation.',
      code: `def calculate_subnet(ip, cidr):\n    # Calculates network range and wildcard mask\n    mask = (0xFFFFFFFF << (32 - cidr)) & 0xFFFFFFFF\n    return f"Subnet Mask: {mask}"`
    },
    forensics: {
      title: 'Digital Forensics Investigation Suite',
      tech: 'Forensics Artifact Analysis',
      desc: 'Simulated memory dump inspection, FTK Imager evidence handling, and timeline construction for cyber incident analysis.',
      code: `/* Forensics Evidence Hash Check */\nSHA256: 8f9b2c3a4e1d... [MATCH VERIFIED]`
    },
    genai: {
      title: 'GenAI Workflow & Productivity Studio',
      tech: 'Claude API / Excel Automation',
      desc: 'Automating analytical reporting with generative AI tools and Anthropic Claude workflows.',
      code: `import anthropic\nclient = anthropic.Anthropic()\nresponse = client.messages.create(model="claude-3-5-sonnet-20241022")`
    }
  };

  const item = data[type];
  if (!item) return;

  content.innerHTML = `
    <span class="font-mono text-xs text-amber-400 uppercase">${item.tech}</span>
    <h3 class="font-display text-2xl text-white mt-1">${item.title}</h3>
    <p class="text-xs text-neutral-300 leading-relaxed">${item.desc}</p>
    <div class="bg-neutral-950 p-4 rounded-xl border border-neutral-800 font-mono text-xs text-emerald-400 overflow-x-auto">
      <pre>${item.code}</pre>
    </div>
  `;

  modal.classList.remove('hidden');
  modal.classList.add('flex');
}

function closeProjectModal() {
  const modal = document.getElementById('projectModal');
  modal.classList.add('hidden');
  modal.classList.remove('flex');
}

// AI CHATBOT LOGIC
function toggleChat() {
  const chatBox = document.getElementById('chatBox');
  chatBox.classList.toggle('hidden');
  chatBox.classList.toggle('flex');
}

function askBot(query) {
  const input = document.getElementById('chatInput');
  input.value = query;
  sendChatMessage();
}

function sendChatMessage() {
  const input = document.getElementById('chatInput');
  const messages = document.getElementById('chatMessages');
  const q = input.value.trim();
  if (!q) return;

  // User Message
  const userMsg = document.createElement('div');
  userMsg.className = 'p-3 rounded-xl bg-amber-500/10 border border-amber-500/20 text-amber-300 text-xs ml-auto max-w-[85%]';
  userMsg.textContent = q;
  messages.appendChild(userMsg);

  input.value = '';

  // Bot Response
  setTimeout(() => {
    const botMsg = document.createElement('div');
    botMsg.className = 'p-3 rounded-xl bg-neutral-800/80 text-neutral-300 text-xs max-w-[85%]';

    const lower = q.toLowerCase();
    if (lower.includes('education') || lower.includes('studying')) {
      botMsg.textContent = "Prasad is currently in his 2nd year of B.Tech (Integrated) CSE at Sanjivani University in Kopargaon, MH.";
    } else if (lower.includes('intern') || lower.includes('experience')) {
      botMsg.textContent = "Prasad completed a 2-month Cybersecurity Internship at InternsPort Innovation Pvt. Ltd. and earned an official LOR!";
    } else if (lower.includes('cert')) {
      botMsg.textContent = "He holds certs from Anthropic (Claude), AWS (ECS), Infosys Springboard, Unstop, and Indian Cyber Club!";
    } else {
      botMsg.textContent = "Prasad is passionate about Cybersecurity, AI tools, and Software Engineering. Connect with him on LinkedIn or WhatsApp!";
    }

    messages.appendChild(botMsg);
    messages.scrollTop = messages.scrollHeight;
    playSound(650, 'sine', 0.08);
  }, 400);
}

// CONTACT FORM HANDLING
function handleContactSubmit(e) {
  e.preventDefault();
  const feedback = document.getElementById('formFeedback');
  feedback.textContent = "Thank you! Your message has been dispatched to Prasad.";
  feedback.classList.remove('hidden');
  e.target.reset();
  playSound(900, 'sine', 0.15);
}

// MOBILE DRAWER
const mobileNavToggle = document.getElementById('mobileNavToggle');
const mobileDrawer = document.getElementById('mobileDrawer');
const closeDrawerBtn = document.getElementById('closeDrawerBtn');

mobileNavToggle?.addEventListener('click', () => {
  mobileDrawer.classList.remove('opacity-0', 'pointer-events-none');
});
closeDrawerBtn?.addEventListener('click', () => {
  mobileDrawer.classList.add('opacity-0', 'pointer-events-none');
});
document.querySelectorAll('.drawer-link').forEach(link => {
  link.addEventListener('click', () => {
    mobileDrawer.classList.add('opacity-0', 'pointer-events-none');
  });
});

// GSAP SCROLL TRIGGER ANIMATIONS
if (window.gsap && window.ScrollTrigger) {
  gsap.registerPlugin(ScrollTrigger);

  gsap.from('#hero h1', { opacity: 0, y: 30, duration: 1, ease: 'power3.out' });
  gsap.from('#hero p', { opacity: 0, y: 20, duration: 1, delay: 0.3, ease: 'power3.out' });

  gsap.utils.toArray('section').forEach(sec => {
    gsap.from(sec, {
      opacity: 0,
      y: 40,
      duration: 0.8,
      scrollTrigger: {
        trigger: sec,
        start: 'top 85%',
        toggleActions: 'play none none none'
      }
    });
  });
}
</script>

</body>
</html>
