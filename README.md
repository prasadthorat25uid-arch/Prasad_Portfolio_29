import React, { useState, useEffect, useRef } from 'react';
import { 
  Shield, 
  Cpu, 
  Terminal, 
  Cloud, 
  Award, 
  Briefcase, 
  BookOpen, 
  Sparkles, 
  Play, 
  Pause, 
  Volume2, 
  VolumeX, 
  ArrowDown, 
  ExternalLink, 
  Linkedin, 
  Github, 
  MessageSquare, 
  CheckCircle2, 
  Menu, 
  X, 
  GraduationCap, 
  Zap, 
  Layers, 
  ChevronRight,
  Code,
  Lock,
  Share2
} from 'lucide-react';

const useScript = (src) => {
  const [loaded, setLoaded] = useState(false);
  useEffect(() => {
    if (document.querySelector(`script[src="${src}"]`)) {
      setLoaded(true);
      return;
    }
    const script = document.createElement('script');
    script.src = src;
    script.async = true;
    script.onload = () => setLoaded(true);
    document.body.appendChild(script);
  }, [src]);
  return loaded;
};

const CinematicLayer = () => {
  const canvasRef = useRef(null);
  const threeLoaded = useScript('https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js');

  useEffect(() => {
    if (!threeLoaded || !canvasRef.current || !window.THREE) return;

    const THREE = window.THREE;
    const canvas = canvasRef.current;
    
    // Setup Scene, Camera, Renderer
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(60, window.innerWidth / window.innerHeight, 0.1, 1000);
    camera.position.z = 30;

    const renderer = new THREE.WebGLRenderer({ canvas, alpha: true, antialias: true });
    renderer.setSize(window.innerWidth, window.innerHeight);
    renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

    // Particles Data
    const isMobile = window.innerWidth < 768;
    const particleCount = isMobile ? 60 : 140;
    const geometry = new THREE.BufferGeometry();
    const positions = new Float32Array(particleCount * 3);
    const colors = new Float32Array(particleCount * 3);
    const scales = new Float32Array(particleCount);

    // Warm Orange (#ff7b39) and Soft White (#f5f5f7) Palette
    const colorOrange = new THREE.Color(0xff7b39);
    const colorWhite = new THREE.Color(0xe2e8f0);
    const colorCyan = new THREE.Color(0x38bdf8);

    for (let i = 0; i < particleCount; i++) {
      positions[i * 3] = (Math.random() - 0.5) * 80;
      positions[i * 3 + 1] = (Math.random() - 0.5) * 80;
      positions[i * 3 + 2] = (Math.random() - 0.5) * 40;

      // Color mix
      const rand = Math.random();
      let pColor = colorOrange;
      if (rand > 0.6) pColor = colorWhite;
      else if (rand > 0.4) pColor = colorCyan;

      colors[i * 3] = pColor.r;
      colors[i * 3 + 1] = pColor.g;
      colors[i * 3 + 2] = pColor.b;

      scales[i] = Math.random() * 0.8 + 0.4;
    }

    geometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));
    geometry.setAttribute('color', new THREE.BufferAttribute(colors, 3));
    geometry.setAttribute('scale', new THREE.BufferAttribute(scales, 1));

    // Custom Particle Material with Soft Glow
    const textureCanvas = document.createElement('canvas');
    textureCanvas.width = 32;
    textureCanvas.height = 32;
    const ctx = textureCanvas.getContext('2d');
    const grad = ctx.createRadialGradient(16, 16, 0, 16, 16, 16);
    grad.addColorStop(0, 'rgba(255,255,255,1)');
    grad.addColorStop(0.3, 'rgba(255,123,57,0.8)');
    grad.addColorStop(1, 'rgba(0,0,0,0)');
    ctx.fillStyle = grad;
    ctx.fillRect(0, 0, 32, 32);

    const texture = new THREE.CanvasTexture(textureCanvas);
    const material = new THREE.PointsMaterial({
      size: 1.2,
      map: texture,
      transparent: true,
      blending: THREE.AdditiveBlending,
      vertexColors: true,
      depthWrite: false,
      opacity: 0.65
    });

    const particles = new THREE.Points(geometry, material);
    scene.add(particles);

    // Mouse Parallax Effect
    let mouseX = 0;
    let mouseY = 0;
    const handleMouseMove = (e) => {
      mouseX = (e.clientX / window.innerWidth - 0.5) * 2;
      mouseY = (e.clientY / window.innerHeight - 0.5) * 2;
    };
    window.addEventListener('mousemove', handleMouseMove);

    // Window Resize Handler
    const handleResize = () => {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(window.innerWidth, window.innerHeight);
    };
    window.addEventListener('resize', handleResize);

    // Animation Loop
    let animationFrameId;
    let clock = new THREE.Clock();

    const animate = () => {
      animationFrameId = requestAnimationFrame(animate);
      const elapsedTime = clock.getElapsedTime();

      // Sine wave floating movement
      particles.rotation.y = elapsedTime * 0.03;
      particles.rotation.x = Math.sin(elapsedTime * 0.02) * 0.05;

      // Smooth camera interpolation toward mouse target
      camera.position.x += (mouseX * 2 - camera.position.x) * 0.03;
      camera.position.y += (-mouseY * 2 - camera.position.y) * 0.03;
      camera.lookAt(scene.position);

      renderer.render(scene, camera);
    };

    animate();

    return () => {
      cancelAnimationFrame(animationFrameId);
      window.removeEventListener('mousemove', handleMouseMove);
      window.removeEventListener('resize', handleResize);
      geometry.dispose();
      material.dispose();
      texture.dispose();
      renderer.dispose();
    };
  }, [threeLoaded]);

  return (
    <canvas
      ref={canvasRef}
      className="fixed inset-0 pointer-events-none z-10 w-full h-full"
    />
  );
};

const CinematicHeroVisual = ({ isPlaying, setIsPlaying, isMuted, setIsMuted, showSoundHint, setShowSoundHint }) => {
  const canvasRef = useRef(null);
  const audioContextRef = useRef(null);
  const speechUtteranceRef = useRef(null);

  // Canvas visual rendering representing Prasad's workstation with talking head animation frame state
  useEffect(() => {
    const canvas = canvasRef.current;
    if (!canvas) return;
    const ctx = canvas.getContext('2d');
    let frameId;
    let tick = 0;

    const renderFrame = () => {
      tick++;
      canvas.width = canvas.offsetWidth;
      canvas.height = canvas.offsetHeight;
      const w = canvas.width;
      const h = canvas.height;

      // Dark futuristic room background
      const bgGradient = ctx.createLinearGradient(0, 0, w, h);
      bgGradient.addColorStop(0, '#0a0d14');
      bgGradient.addColorStop(0.5, '#0e1320');
      bgGradient.addColorStop(1, '#06080d');
      ctx.fillStyle = bgGradient;
      ctx.fillRect(0, 0, w, h);

      // Warm desk lamp ambient light glow (Left-Center)
      const lampGlow = ctx.createRadialGradient(w * 0.3, h * 0.35, 10, w * 0.3, h * 0.35, Math.min(w, h) * 0.5);
      lampGlow.addColorStop(0, 'rgba(255, 150, 60, 0.28)');
      lampGlow.addColorStop(0.5, 'rgba(255, 100, 30, 0.08)');
      lampGlow.addColorStop(1, 'rgba(0,0,0,0)');
      ctx.fillStyle = lampGlow;
      ctx.fillRect(0, 0, w, h);

      // Blue Monitor Cyber Security HUD Glow (Left & Right)
      const monitorGlow = ctx.createRadialGradient(w * 0.2, h * 0.45, 10, w * 0.2, h * 0.45, w * 0.4);
      monitorGlow.addColorStop(0, 'rgba(0, 210, 255, 0.18)');
      monitorGlow.addColorStop(1, 'rgba(0,0,0,0)');
      ctx.fillStyle = monitorGlow;
      ctx.fillRect(0, 0, w, h);

      // Draw Desktop Monitors with Cyber HUD Elements
      // Left Monitor
      ctx.fillStyle = '#08121f';
      ctx.strokeStyle = 'rgba(56, 189, 248, 0.3)';
      ctx.lineWidth = 2;
      const leftMonW = w * 0.35;
      const leftMonH = h * 0.45;
      const leftMonX = w * 0.05;
      const leftMonY = h * 0.15;
      ctx.fillRect(leftMonX, leftMonY, leftMonW, leftMonH);
      ctx.strokeRect(leftMonX, leftMonY, leftMonW, leftMonH);

      // Animated Cyber Circle inside left monitor
      ctx.beginPath();
      ctx.arc(leftMonX + leftMonW * 0.5, leftMonY + leftMonH * 0.5, Math.min(leftMonW, leftMonH) * 0.25, 0, Math.PI * 2);
      ctx.strokeStyle = `rgba(0, 229, 255, ${0.4 + Math.sin(tick * 0.05) * 0.2})`;
      ctx.lineWidth = 3;
      ctx.stroke();

      ctx.beginPath();
      ctx.arc(leftMonX + leftMonW * 0.5, leftMonY + leftMonH * 0.5, Math.min(leftMonW, leftMonH) * 0.35, tick * 0.02, tick * 0.02 + Math.PI * 1.3);
      ctx.strokeStyle = 'rgba(255, 123, 57, 0.6)';
      ctx.lineWidth = 2;
      ctx.stroke();

      // Digital Forensics Data Bars on Monitor
      for (let i = 0; i < 6; i++) {
        const barH = 10 + Math.sin(tick * 0.08 + i) * 12;
        ctx.fillStyle = i % 2 === 0 ? 'rgba(56, 189, 248, 0.7)' : 'rgba(255, 123, 57, 0.7)';
        ctx.fillRect(leftMonX + 20 + i * 18, leftMonY + leftMonH - 30 - barH, 12, barH);
      }

      // Prasad Avatar Character Silhouettes Representation (Head, Glasses, Hoodie, Desk)
      const centerX = w * 0.58;
      const centerY = h * 0.52;
      const scale = Math.min(w, h) * 0.0028;

      // Desk Surface
      ctx.fillStyle = '#111520';
      ctx.fillRect(0, h * 0.68, w, h * 0.32);
      ctx.fillStyle = 'rgba(255, 123, 57, 0.15)';
      ctx.fillRect(0, h * 0.68, w, 2);

      // Hoodie Body (Dark hoodie)
      ctx.fillStyle = '#161922';
      ctx.beginPath();
      ctx.moveTo(centerX - 130 * scale, centerY + 200 * scale);
      ctx.lineTo(centerX - 90 * scale, centerY + 60 * scale);
      ctx.quadraticCurveTo(centerX, centerY + 40 * scale, centerX + 90 * scale, centerY + 60 * scale);
      ctx.lineTo(centerX + 130 * scale, centerY + 200 * scale);
      ctx.closePath();
      ctx.fill();

      // Neck
      ctx.fillStyle = '#d4a373';
      ctx.fillRect(centerX - 22 * scale, centerY + 25 * scale, 44 * scale, 35 * scale);

      // Head Base
      ctx.beginPath();
      ctx.ellipse(centerX, centerY - 25 * scale, 48 * scale, 62 * scale, 0, 0, Math.PI * 2);
      ctx.fillStyle = '#e2b384';
      ctx.fill();

      // Hair (Neat black hair)
      ctx.beginPath();
      ctx.ellipse(centerX, centerY - 65 * scale, 52 * scale, 30 * scale, 0, Math.PI, Math.PI * 2);
      ctx.fillStyle = '#1a181b';
      ctx.fill();

      // Glasses (Stylish black frame)
      ctx.strokeStyle = '#0f0f12';
      ctx.lineWidth = 4 * scale;
      // Left Lens
      ctx.strokeRect(centerX - 38 * scale, centerY - 38 * scale, 32 * scale, 24 * scale);
      // Right Lens
      ctx.strokeRect(centerX + 6 * scale, centerY - 38 * scale, 32 * scale, 24 * scale);
      // Glasses Bridge
      ctx.beginPath();
      ctx.moveTo(centerX - 6 * scale, centerY - 28 * scale);
      ctx.lineTo(centerX + 6 * scale, centerY - 28 * scale);
      ctx.stroke();

      // Eyes
      ctx.fillStyle = '#221e1a';
      ctx.beginPath();
      ctx.arc(centerX - 22 * scale, centerY - 26 * scale, 5 * scale, 0, Math.PI * 2);
      ctx.arc(centerX + 22 * scale, centerY - 26 * scale, 5 * scale, 0, Math.PI * 2);
      ctx.fill();

      // Expressive Subtle Talking Mouth Motion when playing
      ctx.beginPath();
      const mouthOpen = isPlaying ? Math.abs(Math.sin(tick * 0.15)) * 8 * scale + 2 : 2;
      ctx.ellipse(centerX, centerY + 12 * scale, 12 * scale, mouthOpen, 0, 0, Math.PI);
      ctx.fillStyle = '#a05246';
      ctx.fill();

      // Subtle posture micro-movement
      if (isPlaying) {
        ctx.fillStyle = 'rgba(255,255,255,0.03)';
        ctx.fillRect(0, 0, w, h);
      }

      frameId = requestAnimationFrame(renderFrame);
    };

    renderFrame();

    return () => cancelAnimationFrame(frameId);
  }, [isPlaying]);

  // Handle Speech Audio Playback when user unmutes
  const toggleAudio = () => {
    if (isMuted) {
      setIsMuted(false);
      setShowSoundHint(false);
      if ('speechSynthesis' in window) {
        window.speechSynthesis.cancel();
        const text = "Hello, I'm Prasad. Currently I am pursuing my integrated B.Tech at Sanjivani University. Welcome to my portfolio.";
        const utterance = new SpeechSynthesisUtterance(text);
        utterance.rate = 0.95;
        utterance.pitch = 1.0;
        utterance.onend = () => {
          setIsMuted(true);
        };
        speechUtteranceRef.current = utterance;
        window.speechSynthesis.speak(utterance);
      }
    } else {
      setIsMuted(true);
      if ('speechSynthesis' in window) {
        window.speechSynthesis.cancel();
      }
    }
  };

  const togglePlay = () => {
    setIsPlaying(!isPlaying);
  };

  return (
    <div className="relative w-full h-full min-h-[100vh] flex items-center justify-center overflow-hidden bg-slate-950">
      {/* Background Blurred Video Replica for Cinematic Ambient Aura */}
      <div className="absolute inset-0 overflow-hidden pointer-events-none z-0">
        <canvas
          ref={canvasRef}
          className="w-full h-full object-cover scale-110 blur-2xl opacity-40 filter brightness-75 contrast-125"
        />
      </div>

      {/* Foreground Sharp Visual Display */}
      <div className="absolute inset-0 z-0">
        <canvas
          ref={canvasRef}
          className="w-full h-full object-cover opacity-90 transition-opacity duration-1000"
        />
      </div>

      {/* Cinematic Layer Gradients & Vignette */}
      <div className="absolute inset-0 bg-gradient-to-t from-slate-950 via-slate-950/40 to-slate-950/70 z-10 pointer-events-none" />
      <div className="absolute inset-0 bg-radial-gradient from-transparent via-slate-950/30 to-slate-950/90 z-10 pointer-events-none" />
      <div className="absolute inset-0 bg-gradient-to-r from-slate-950/80 via-transparent to-slate-950/80 z-10 pointer-events-none" />

      {/* Sound Hint Floating Badge */}
      {showSoundHint && (
        <div className="absolute top-28 right-6 md:right-12 z-30 animate-bounce">
          <button
            onClick={toggleAudio}
            className="flex items-center gap-2 px-4 py-2 rounded-full bg-orange-500/20 backdrop-blur-md border border-orange-500/50 text-orange-300 text-xs font-semibold tracking-wider shadow-lg shadow-orange-500/10 hover:bg-orange-500/30 transition-all duration-300 cursor-pointer"
          >
            <Sparkles className="w-3.5 h-3.5 animate-spin" />
            <span>TAP FOR SOUND</span>
          </button>
        </div>
      )}

      {/* Glassmorphism Floating Video Controls */}
      <div className="absolute bottom-10 right-6 md:right-12 z-30 flex items-center gap-3 bg-slate-900/60 backdrop-blur-xl border border-white/10 p-2 rounded-full shadow-2xl">
        <button
          onClick={togglePlay}
          aria-label={isPlaying ? "Pause Video" : "Play Video"}
          className="w-10 h-10 rounded-full flex items-center justify-center bg-white/10 hover:bg-orange-500 hover:text-white text-slate-200 transition-all duration-300"
        >
          {isPlaying ? <Pause className="w-4 h-4" /> : <Play className="w-4 h-4 ml-0.5" />}
        </button>

        <button
          onClick={toggleAudio}
          aria-label={isMuted ? "Unmute Audio" : "Mute Audio"}
          className="w-10 h-10 rounded-full flex items-center justify-center bg-white/10 hover:bg-orange-500 hover:text-white text-slate-200 transition-all duration-300"
        >
          {isMuted ? <VolumeX className="w-4 h-4" /> : <Volume2 className="w-4 h-4" />}
        </button>
      </div>
    </div>
  );
};

const Navigation = () => {
  const [scrolled, setScrolled] = useState(false);
  const [mobileMenuOpen, setMobileMenuOpen] = useState(false);

  useEffect(() => {
    const handleScroll = () => {
      setScrolled(window.scrollY > 50);
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const navItems = [
    { label: 'Home', href: '#hero' },
    { label: 'About', href: '#about' },
    { label: 'Skills', href: '#skills' },
    { label: 'Experience', href: '#experience' },
    { label: 'Certifications', href: '#certifications' },
    { label: 'Moments', href: '#moments' },
    { label: 'Contact', href: '#contact' }
  ];

  const handleNavClick = (e, href) => {
    e.preventDefault();
    setMobileMenuOpen(false);
    const target = document.querySelector(href);
    if (target) {
      target.scrollIntoView({ behavior: 'smooth' });
    }
  };

  return (
    <nav
      className={`fixed top-0 left-0 right-0 z-50 transition-all duration-500 ${
        scrolled ? 'bg-slate-950/80 backdrop-blur-md border-b border-white/10 py-4 shadow-xl' : 'bg-transparent py-6'
      }`}
    >
      <div className="max-w-7xl mx-auto px-6 md:px-12 flex items-center justify-between">
        {/* Brand Logo */}
        <a
          href="#hero"
          onClick={(e) => handleNavClick(e, '#hero')}
          className="group flex items-center gap-3"
        >
          <div className="w-10 h-10 rounded-xl bg-gradient-to-br from-orange-500 to-amber-600 flex items-center justify-center font-bold text-white tracking-wider shadow-lg shadow-orange-500/20 group-hover:scale-105 transition-transform duration-300">
            PT
          </div>
          <div className="flex flex-col">
            <span className="text-white font-semibold text-sm tracking-wide group-hover:text-orange-400 transition-colors">
              Prasad Thorat
            </span>
            <span className="text-slate-400 text-[10px] uppercase tracking-widest">
              AI & Cyber Security
            </span>
          </div>
        </a>

        {/* Desktop Navigation Links */}
        <div className="hidden md:flex items-center gap-8 bg-slate-900/40 backdrop-blur-md px-6 py-2.5 rounded-full border border-white/10">
          {navItems.map((item) => (
            <a
              key={item.label}
              href={item.href}
              onClick={(e) => handleNavClick(e, item.href)}
              className="text-xs uppercase tracking-widest text-slate-300 hover:text-orange-400 transition-colors duration-200 font-medium"
            >
              {item.label}
            </a>
          ))}
        </div>

        {/* Action Button */}
        <div className="hidden md:flex items-center gap-4">
          <a
            href="https://wa.me/918010989708"
            target="_blank"
            rel="noopener noreferrer"
            className="flex items-center gap-2 px-4 py-2 rounded-full bg-orange-500 hover:bg-orange-600 text-white text-xs font-semibold tracking-wider transition-all duration-300 shadow-lg shadow-orange-500/25 hover:scale-105"
          >
            <MessageSquare className="w-3.5 h-3.5" />
            <span>Connect</span>
          </a>
        </div>

        {/* Mobile Hamburger Toggle */}
        <button
          onClick={() => setMobileMenuOpen(!mobileMenuOpen)}
          className="md:hidden w-10 h-10 rounded-lg bg-slate-900/80 border border-white/10 flex items-center justify-center text-slate-200 hover:text-white"
          aria-label="Toggle Navigation Menu"
        >
          {mobileMenuOpen ? <X className="w-5 h-5" /> : <Menu className="w-5 h-5" />}
        </button>
      </div>

      {/* Mobile Drawer */}
      {mobileMenuOpen && (
        <div className="md:hidden absolute top-full left-0 right-0 bg-slate-950/95 backdrop-blur-2xl border-b border-white/10 p-6 flex flex-col gap-4 shadow-2xl animate-fadeIn">
          {navItems.map((item) => (
            <a
              key={item.label}
              href={item.href}
              onClick={(e) => handleNavClick(e, item.href)}
              className="text-sm font-medium text-slate-200 hover:text-orange-400 py-2 border-b border-white/5"
            >
              {item.label}
            </a>
          ))}
          <a
            href="https://wa.me/918010989708"
            target="_blank"
            rel="noopener noreferrer"
            className="mt-2 flex items-center justify-center gap-2 w-full py-3 rounded-xl bg-orange-500 text-white font-semibold text-sm shadow-lg shadow-orange-500/30"
          >
            <MessageSquare className="w-4 h-4" />
            <span>Connect on WhatsApp</span>
          </a>
        </div>
      )}
    </nav>
  );
};

const Hero = ({ setIsPlaying, setIsMuted, setShowSoundHint }) => {
  const [isPlayingState, setIsPlayingState] = useState(true);
  const [isMutedState, setIsMutedState] = useState(true);
  const [showHint, setShowHint] = useState(true);

  // Load GSAP dynamically for entrance animation
  const gsapLoaded = useScript('https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js');
  const heroRef = useRef(null);

  useEffect(() => {
    if (!gsapLoaded || !window.gsap) return;
    const gsap = window.gsap;

    const ctx = gsap.context(() => {
      const tl = gsap.timeline({ defaults: { ease: 'power3.out' } });

      tl.fromTo('.gsap-eyebrow', { opacity: 0, y: 30 }, { opacity: 1, y: 0, duration: 1, delay: 0.3 })
        .fromTo('.gsap-name-prasad', { opacity: 0, y: 50 }, { opacity: 1, y: 0, duration: 1.2 }, '-=0.6')
        .fromTo('.gsap-name-thorat', { opacity: 0, y: 50 }, { opacity: 1, y: 0, duration: 1.2 }, '-=1.0')
        .fromTo('.gsap-role', { opacity: 0, y: 20 }, { opacity: 1, y: 0, duration: 0.8 }, '-=0.6')
        .fromTo('.gsap-statement', { opacity: 0, y: 20 }, { opacity: 1, y: 0, duration: 0.8 }, '-=0.6')
        .fromTo('.gsap-socials', { opacity: 0, scale: 0.9 }, { opacity: 1, scale: 1, duration: 0.8 }, '-=0.4')
        .fromTo('.gsap-scroll-indicator', { opacity: 0 }, { opacity: 1, duration: 1 }, '-=0.4');
    }, heroRef);

    return () => ctx.revert();
  }, [gsapLoaded]);

  const scrollToAbout = () => {
    const aboutSection = document.querySelector('#about');
    if (aboutSection) {
      aboutSection.scrollIntoView({ behavior: 'smooth' });
    }
  };

  return (
    <section id="hero" ref={heroRef} className="relative min-h-screen w-full flex items-center justify-center overflow-hidden">
      {/* Background Talking Head Video Layer */}
      <CinematicHeroVisual
        isPlaying={isPlayingState}
        setIsPlaying={setIsPlayingState}
        isMuted={isMutedState}
        setIsMuted={setIsMutedState}
        showSoundHint={showHint}
        setShowSoundHint={setShowHint}
      />

      {/* Typography Content Overlay */}
      <div className="relative z-20 max-w-7xl mx-auto px-6 md:px-12 w-full pt-28 pb-20 flex flex-col items-start justify-center min-h-screen">
        {/* Eyebrow Tag */}
        <div className="gsap-eyebrow inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-white/5 border border-white/10 backdrop-blur-md mb-6">
          <span className="w-2 h-2 rounded-full bg-orange-500 animate-pulse" />
          <span className="text-xs font-semibold uppercase tracking-[0.25em] text-slate-300">
            CYBERSECURITY • AI • SOFTWARE ENGINEERING
          </span>
        </div>

        {/* Huge Bold Name */}
        <h1 className="font-extrabold tracking-tight text-white leading-none mb-6">
          <span className="gsap-name-prasad block text-6xl sm:text-8xl lg:text-9xl font-black bg-clip-text text-transparent bg-gradient-to-r from-white via-slate-100 to-slate-400">
            PRASAD
          </span>
          <span className="gsap-name-thorat block text-6xl sm:text-8xl lg:text-9xl font-black text-transparent bg-clip-text bg-gradient-to-r from-orange-400 via-amber-500 to-orange-600">
            THORAT
          </span>
        </h1>

        {/* Subtitle & Role */}
        <div className="gsap-role text-lg sm:text-2xl font-medium text-slate-200 mb-4 tracking-wide max-w-2xl">
          B.Tech (Integrated) CSE <span className="text-orange-400 font-normal">|</span> Cybersecurity Enthusiast <span className="text-orange-400 font-normal">|</span> Aspiring Software Engineer
        </div>

        {/* Short Cinematic Statement */}
        <p className="gsap-statement text-sm sm:text-base text-slate-400 max-w-xl font-light leading-relaxed mb-10">
          Exploring the intersection of cybersecurity, artificial intelligence, and software engineering. Building resilient systems with hands-on digital forensics and generative AI integration.
        </p>

        {/* Social Quick Links Bar */}
        <div className="gsap-socials flex flex-wrap items-center gap-4 mb-16">
          <a
            href="https://www.linkedin.com/in/prasad-thorat-a38578372?utm_source=share_via&utm_content=profile&utm_medium=member_android"
            target="_blank"
            rel="noopener noreferrer"
            className="flex items-center gap-2.5 px-5 py-3 rounded-xl bg-slate-900/80 hover:bg-slate-800 text-slate-200 hover:text-white border border-white/10 hover:border-orange-500/50 transition-all duration-300 shadow-xl group hover:-translate-y-1"
          >
            <Linkedin className="w-4 h-4 text-orange-400 group-hover:scale-110 transition-transform" />
            <span className="text-xs font-semibold tracking-wider uppercase">LinkedIn</span>
          </a>

          <a
            href="https://github.com/prasadthorat25uid-arch"
            target="_blank"
            rel="noopener noreferrer"
            className="flex items-center gap-2.5 px-5 py-3 rounded-xl bg-slate-900/80 hover:bg-slate-800 text-slate-200 hover:text-white border border-white/10 hover:border-orange-500/50 transition-all duration-300 shadow-xl group hover:-translate-y-1"
          >
            <Github className="w-4 h-4 text-orange-400 group-hover:scale-110 transition-transform" />
            <span className="text-xs font-semibold tracking-wider uppercase">GitHub</span>
          </a>

          <a
            href="https://wa.me/918010989708"
            target="_blank"
            rel="noopener noreferrer"
            className="flex items-center gap-2.5 px-5 py-3 rounded-xl bg-emerald-950/40 hover:bg-emerald-900/50 text-emerald-300 hover:text-emerald-200 border border-emerald-500/30 transition-all duration-300 shadow-xl group hover:-translate-y-1"
          >
            <MessageSquare className="w-4 h-4 text-emerald-400 group-hover:scale-110 transition-transform" />
            <span className="text-xs font-semibold tracking-wider uppercase">WhatsApp</span>
          </a>
        </div>

        {/* Scroll Indicator */}
        <button
          onClick={scrollToAbout}
          className="gsap-scroll-indicator self-center md:self-start flex flex-col items-center gap-3 cursor-pointer group opacity-80 hover:opacity-100 transition-opacity"
          aria-label="Scroll down to explore about section"
        >
          <span className="text-[10px] uppercase tracking-[0.3em] text-slate-400 group-hover:text-orange-400 transition-colors">
            SCROLL TO EXPLORE
          </span>
          <div className="w-5 h-9 rounded-full border-2 border-slate-700 group-hover:border-orange-500/80 p-1 flex justify-center transition-colors">
            <div className="w-1 h-2 rounded-full bg-orange-400 animate-bounce" />
          </div>
        </button>
      </div>
    </section>
  );
};

const About = () => {
  return (
    <section id="about" className="relative z-20 py-28 bg-slate-950 border-t border-white/5">
      <div className="max-w-7xl mx-auto px-6 md:px-12">
        {/* Section Header */}
        <div className="flex flex-col items-start mb-16">
          <div className="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-orange-500/10 border border-orange-500/20 text-orange-400 text-xs font-semibold tracking-widest uppercase mb-3">
            <GraduationCap className="w-3.5 h-3.5" />
            <span>BACKGROUND & VISION</span>
          </div>
          <h2 className="text-3xl sm:text-5xl font-extrabold text-white tracking-tight">
            THE PERSON BEHIND THE SCREEN
          </h2>
        </div>

        {/* Grid Content Layout */}
        <div className="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
          {/* Main Story Text */}
          <div className="lg:col-span-7 flex flex-col gap-6 text-slate-300 text-base sm:text-lg leading-relaxed font-light">
            <p>
              I am Prasad Sudhir Thorat, currently pursuing my B.Tech (Integrated) in Computer Science & Engineering at Sanjivani University, Kopargaon, Maharashtra (2nd Year).
            </p>
            <p>
              Driven by a deep passion for modern digital infrastructure, I specialize in the convergence of <strong className="text-orange-400 font-semibold">Cybersecurity</strong>, <strong className="text-orange-400 font-semibold font-sans">Artificial Intelligence</strong>, and <strong className="text-orange-400 font-semibold font-sans">Software Engineering</strong>.
            </p>
            <p>
              Through hands-on internship experience in cybersecurity, digital forensics workshops, and continuous exploration of LLM toolchains like Claude and Generative AI Studio, I build resilient systems and optimized workflows for future enterprise challenges.
            </p>

            {/* Quick Location & Education Meta */}
            <div className="grid grid-cols-1 sm:grid-cols-2 gap-4 mt-4 pt-6 border-t border-white/10">
              <div className="p-4 rounded-xl bg-slate-900/50 border border-white/5 flex flex-col">
                <span className="text-xs uppercase tracking-wider text-slate-400 mb-1">Location</span>
                <span className="text-white font-medium text-sm">Kopargaon, Maharashtra, India</span>
              </div>
              <div className="p-4 rounded-xl bg-slate-900/50 border border-white/5 flex flex-col">
                <span className="text-xs uppercase tracking-wider text-slate-400 mb-1">University</span>
                <span className="text-white font-medium text-sm">Sanjivani University (2nd Year B.Tech)</span>
              </div>
            </div>
          </div>

          {/* Key Pillar Highlight Cards */}
          <div className="lg:col-span-5 grid grid-cols-1 gap-4">
            <div className="p-6 rounded-2xl bg-gradient-to-br from-slate-900 to-slate-900/60 border border-white/10 hover:border-orange-500/40 transition-all duration-300 shadow-xl group">
              <div className="w-12 h-12 rounded-xl bg-orange-500/10 border border-orange-500/20 flex items-center justify-center text-orange-400 mb-4 group-hover:scale-110 transition-transform">
                <Shield className="w-6 h-6" />
              </div>
              <h3 className="text-white font-bold text-lg mb-2">Cybersecurity & Forensics</h3>
              <p className="text-slate-400 text-sm leading-relaxed">
                Hands-on practical investigation experience, IP subnetting, network protocols, and vulnerability analysis.
              </p>
            </div>

            <div className="p-6 rounded-2xl bg-gradient-to-br from-slate-900 to-slate-900/60 border border-white/10 hover:border-orange-500/40 transition-all duration-300 shadow-xl group">
              <div className="w-12 h-12 rounded-xl bg-cyan-500/10 border border-cyan-500/20 flex items-center justify-center text-cyan-400 mb-4 group-hover:scale-110 transition-transform">
                <Cpu className="w-6 h-6" />
              </div>
              <h3 className="text-white font-bold text-lg mb-2">Artificial Intelligence</h3>
              <p className="text-slate-400 text-sm leading-relaxed">
                Utilizing Claude, Generative AI Studio, and ChatGPT to build intelligent automation and software tools.
              </p>
            </div>

            <div className="p-6 rounded-2xl bg-gradient-to-br from-slate-900 to-slate-900/60 border border-white/10 hover:border-orange-500/40 transition-all duration-300 shadow-xl group">
              <div className="w-12 h-12 rounded-xl bg-emerald-500/10 border border-emerald-500/20 flex items-center justify-center text-emerald-400 mb-4 group-hover:scale-110 transition-transform">
                <Terminal className="w-6 h-6" />
              </div>
              <h3 className="text-white font-bold text-lg mb-2">Software Engineering</h3>
              <p className="text-slate-400 text-sm leading-relaxed">
                Writing clean C, Python, and web software combined with AWS cloud containers for deployment.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>
  );
};

const Skills = () => {
  const skillCategories = [
    {
      title: 'PROGRAMMING',
      icon: Code,
      color: 'from-amber-500/20 to-orange-500/10',
      borderColor: 'border-amber-500/30',
      textColor: 'text-amber-400',
      skills: ['C', 'Python', 'HTML']
    },
    {
      title: 'CYBERSECURITY',
      icon: Shield,
      color: 'from-red-500/20 to-orange-500/10',
      borderColor: 'border-red-500/30',
      textColor: 'text-red-400',
      skills: ['Digital Forensics', 'Network Basics', 'IP Addressing', 'Subnetting', 'Cybersecurity Fundamentals']
    },
    {
      title: 'CLOUD & DEVOPS',
      icon: Cloud,
      color: 'from-blue-500/20 to-cyan-500/10',
      borderColor: 'border-blue-500/30',
      textColor: 'text-blue-400',
      skills: ['AWS Elastic Container Service (ECS)', 'KodeKloud Labs']
    },
    {
      title: 'AI & GENERATIVE AI',
      icon: Sparkles,
      color: 'from-purple-500/20 to-pink-500/10',
      borderColor: 'border-purple-500/30',
      textColor: 'text-purple-400',
      skills: ['Claude AI', 'Google Workspace AI', 'Generative AI Studio', 'ChatGPT']
    },
    {
      title: 'PRODUCTIVITY & AUTOMATION',
      icon: Zap,
      color: 'from-emerald-500/20 to-teal-500/10',
      borderColor: 'border-emerald-500/30',
      textColor: 'text-emerald-400',
      skills: ['Microsoft Excel with AI', 'Python Scripting']
    }
  ];

  return (
    <section id="skills" className="relative z-20 py-28 bg-slate-900/60 border-t border-white/5">
      <div className="max-w-7xl mx-auto px-6 md:px-12">
        <div className="flex flex-col items-start mb-16">
          <div className="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-orange-500/10 border border-orange-500/20 text-orange-400 text-xs font-semibold tracking-widest uppercase mb-3">
            <Layers className="w-3.5 h-3.5" />
            <span>CORE COMPETENCIES</span>
          </div>
          <h2 className="text-3xl sm:text-5xl font-extrabold text-white tracking-tight">
            TECHNICAL DOMAINS
          </h2>
        </div>

        {/* Skill Category Cards */}
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          {skillCategories.map((cat, idx) => {
            const IconComp = cat.icon;
            return (
              <div
                key={idx}
                className={`p-8 rounded-2xl bg-slate-950 border ${cat.borderColor} hover:border-orange-500/50 transition-all duration-300 shadow-2xl relative overflow-hidden group hover:-translate-y-1.5`}
              >
                {/* Subtle Ambient Color Glow */}
                <div className={`absolute top-0 right-0 w-32 h-32 bg-gradient-to-bl ${cat.color} rounded-full blur-3xl pointer-events-none group-hover:scale-150 transition-transform duration-500`} />

                <div className="flex items-center gap-3 mb-6 relative z-10">
                  <div className={`w-10 h-10 rounded-xl bg-slate-900 border border-white/10 flex items-center justify-center ${cat.textColor}`}>
                    <IconComp className="w-5 h-5" />
                  </div>
                  <h3 className="text-white font-extrabold text-sm tracking-widest uppercase">
                    {cat.title}
                  </h3>
                </div>

                <div className="flex flex-wrap gap-2.5 relative z-10">
                  {cat.skills.map((skill, sIdx) => (
                    <span
                      key={sIdx}
                      className="px-3.5 py-2 rounded-lg bg-slate-900/90 border border-white/10 text-slate-200 text-xs font-medium hover:border-orange-500/40 hover:text-orange-400 transition-all duration-200"
                    >
                      {skill}
                    </span>
                  ))}
                </div>
              </div>
            );
          })}
        </div>
      </div>
    </section>
  );
};

const Experience = () => {
  return (
    <section id="experience" className="relative z-20 py-28 bg-slate-950 border-t border-white/5">
      <div className="max-w-7xl mx-auto px-6 md:px-12">
        <div className="flex flex-col items-start mb-16">
          <div className="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-orange-500/10 border border-orange-500/20 text-orange-400 text-xs font-semibold tracking-widest uppercase mb-3">
            <Briefcase className="w-3.5 h-3.5" />
            <span>INDUSTRY EXPERIENCE</span>
          </div>
          <h2 className="text-3xl sm:text-5xl font-extrabold text-white tracking-tight">
            WORK & INTERNSHIPS
          </h2>
        </div>

        {/* Vertical Timeline */}
        <div className="relative border-l-2 border-slate-800 ml-4 md:ml-8 pl-6 md:pl-12 flex flex-col gap-12">
          {/* Timeline Item */}
          <div className="relative group">
            {/* Timeline Node Icon */}
            <div className="absolute -left-[31px] md:-left-[55px] top-0 w-12 h-12 rounded-full bg-slate-900 border-2 border-orange-500 flex items-center justify-center text-orange-400 shadow-lg shadow-orange-500/20 group-hover:scale-110 transition-transform">
              <Shield className="w-5 h-5" />
            </div>

            {/* Card Details */}
            <div className="p-8 rounded-2xl bg-slate-900/50 border border-white/10 hover:border-orange-500/40 transition-all duration-300 shadow-2xl">
              <div className="flex flex-wrap items-center justify-between gap-4 mb-4">
                <div>
                  <h3 className="text-xl sm:text-2xl font-bold text-white">
                    Cybersecurity Intern
                  </h3>
                  <div className="text-orange-400 text-sm font-semibold tracking-wide mt-1">
                    InternsPort Innovation Pvt. Ltd.
                  </div>
                </div>
                <span className="px-3.5 py-1.5 rounded-full bg-slate-800 border border-white/10 text-slate-300 text-xs font-semibold">
                  February 2026 – April 2026 (2 Months)
                </span>
              </div>

              <ul className="flex flex-col gap-3 text-slate-300 text-sm sm:text-base leading-relaxed font-light mb-6">
                <li className="flex items-start gap-3">
                  <CheckCircle2 className="w-4 h-4 text-orange-400 shrink-0 mt-1" />
                  <span>Completed an intensive 2-month Cybersecurity internship focusing on threat vector analysis and security fundamentals.</span>
                </li>
                <li className="flex items-start gap-3">
                  <CheckCircle2 className="w-4 h-4 text-orange-400 shrink-0 mt-1" />
                  <span>Demonstrated strong analytical thinking and structured technical problem-solving abilities.</span>
                </li>
                <li className="flex items-start gap-3">
                  <CheckCircle2 className="w-4 h-4 text-orange-400 shrink-0 mt-1" />
                  <span>Demonstrated effective cross-functional technical communication.</span>
                </li>
              </ul>

              {/* Recommendation Highlight Badge */}
              <div className="p-4 rounded-xl bg-orange-500/10 border border-orange-500/30 flex items-center gap-3 text-orange-300 text-xs sm:text-sm font-medium">
                <Award className="w-5 h-5 text-orange-400 shrink-0" />
                <span>Earned Letter of Recommendation (LoR) from Head of Operations.</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  );
};

const Certifications = () => {
  const [activeTab, setActiveTab] = useState('ALL');

  const certs = [
    // Cloud
    { title: 'AWS Elastic Container Service (ECS)', issuer: 'KodeKloud', category: 'CLOUD' },
    { title: 'KodeKloud Challenges Completion Certificate', issuer: 'KodeKloud', category: 'CLOUD' },

    // Programming
    { title: 'Introduction to Python', issuer: 'Infosys Springboard', category: 'PROGRAMMING' },
    { title: 'Python Fundamentals', issuer: 'Infosys Springboard', category: 'PROGRAMMING' },
    { title: 'Introduction to C', issuer: 'Sololearn', category: 'PROGRAMMING' },
    { title: 'Programming For Beginners: Master the C Language', issuer: 'Learn Programming Academy', category: 'PROGRAMMING' },

    // AI
    { title: 'AI Fluency: AI Capabilities & Limitations', issuer: 'Anthropic', category: 'AI' },
    { title: 'Introduction to Claude Cowork', issuer: 'Anthropic', category: 'AI' },
    { title: 'Claude 101', issuer: 'Anthropic', category: 'AI' },
    { title: 'Bring AI to Work Workshop', issuer: 'Google Workspace', category: 'AI' },
    { title: 'Introduction to Generative AI Studio', issuer: 'Simplilearn', category: 'AI' },
    { title: 'Generative AI Mastery Workshop', issuer: 'NxtWave / OpenAI Academy', category: 'AI' },
    { title: 'AI Tools & ChatGPT Workshop', issuer: '10X / BeLux', category: 'AI' },
    { title: 'Microsoft Excel Using AI', issuer: 'OfficeMaster', category: 'AI' },

    // Cybersecurity
    { title: 'Cybersecurity Mastery', issuer: 'Unstop', category: 'CYBERSECURITY' },
    { title: 'Hands-on Digital Forensics & Investigation Workshop', issuer: 'Indian Cyber Club', category: 'CYBERSECURITY' },
    { title: 'SEBI Investor Awareness Test', issuer: 'NISM', category: 'CYBERSECURITY' },

    // Soft Skills
    { title: 'Communication Skills', issuer: 'MindLuster', category: 'SKILLS' }
  ];

  const categories = ['ALL', 'CLOUD', 'PROGRAMMING', 'AI', 'CYBERSECURITY', 'SKILLS'];

  const filteredCerts = activeTab === 'ALL' ? certs : certs.filter(c => c.category === activeTab);

  return (
    <section id="certifications" className="relative z-20 py-28 bg-slate-900/40 border-t border-white/5">
      <div className="max-w-7xl mx-auto px-6 md:px-12">
        <div className="flex flex-col items-start mb-12">
          <div className="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-orange-500/10 border border-orange-500/20 text-orange-400 text-xs font-semibold tracking-widest uppercase mb-3">
            <Award className="w-3.5 h-3.5" />
            <span>VERIFIED CREDENTIALS</span>
          </div>
          <h2 className="text-3xl sm:text-5xl font-extrabold text-white tracking-tight">
            CERTIFICATIONS
          </h2>
        </div>

        {/* Category Filter Tabs */}
        <div className="flex flex-wrap items-center gap-2 mb-12 border-b border-white/10 pb-4">
          {categories.map((cat) => (
            <button
              key={cat}
              onClick={() => setActiveTab(cat)}
              className={`px-4 py-2 rounded-lg text-xs font-bold tracking-wider uppercase transition-all duration-200 cursor-pointer ${
                activeTab === cat
                  ? 'bg-orange-500 text-white shadow-lg shadow-orange-500/20'
                  : 'bg-slate-900/60 text-slate-400 hover:text-white hover:bg-slate-800'
              }`}
            >
              {cat}
            </button>
          ))}
        </div>

        {/* Certifications Grid */}
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          {filteredCerts.map((cert, idx) => (
            <div
              key={idx}
              className="p-6 rounded-xl bg-slate-950 border border-white/10 hover:border-orange-500/40 transition-all duration-300 shadow-xl flex flex-col justify-between group hover:-translate-y-1"
            >
              <div>
                <div className="flex items-center justify-between mb-3">
                  <span className="text-[10px] font-bold tracking-widest text-orange-400 uppercase bg-orange-500/10 px-2.5 py-1 rounded border border-orange-500/20">
                    {cert.category}
                  </span>
                  <Award className="w-4 h-4 text-slate-500 group-hover:text-orange-400 transition-colors" />
                </div>
                <h3 className="text-white font-semibold text-base mb-2 line-clamp-2">
                  {cert.title}
                </h3>
              </div>
              <div className="mt-4 pt-3 border-t border-white/5 text-xs text-slate-400 flex items-center justify-between">
                <span>Issued by:</span>
                <span className="text-slate-200 font-medium">{cert.issuer}</span>
              </div>
            </div>
          ))}
        </div>
      </div>
    </section>
  );
};

const Moments = () => {
  const events = [
    {
      title: 'Artificial Intelligence Workshop',
      org: 'Techfest, IIT Bombay',
      desc: 'Participated in advanced AI training sessions at Asia’s largest science & technology festival.'
    },
    {
      title: 'Smart India Hackathon Internal',
      org: 'Sanjivani University (Team: Code Warriors)',
      desc: 'Idea Presentation for problem-solving challenge with innovative software architecture.'
    },
    {
      title: 'Constitution Day Quiz Competition',
      org: 'Sanjivani University',
      desc: 'Achieved an outstanding score of 90% in constitutional law and governance principles.'
    },
    {
      title: 'GenAI Buildathon',
      org: 'NxtWave / OpenAI Academy',
      desc: 'Hands-on project development leveraging generative models and LLM APIs.'
    },
    {
      title: 'MYBharat Online Quizzes',
      org: 'MYBharat Platform',
      desc: 'Active engagement in national tech and governance knowledge competitions.'
    },
    {
      title: 'Dr. B.R. Ambedkar Quiz 2025',
      org: 'Ministry of Social Justice & Empowerment',
      desc: 'National quiz competition recognition.'
    }
  ];

  return (
    <section id="moments" className="relative z-20 py-28 bg-slate-950 border-t border-white/5">
      <div className="max-w-7xl mx-auto px-6 md:px-12">
        <div className="flex flex-col items-start mb-16">
          <div className="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-orange-500/10 border border-orange-500/20 text-orange-400 text-xs font-semibold tracking-widest uppercase mb-3">
            <Sparkles className="w-3.5 h-3.5" />
            <span>MILESTONES & COMPETITIONS</span>
          </div>
          <h2 className="text-3xl sm:text-5xl font-extrabold text-white tracking-tight">
            EVENTS & ACHIEVEMENTS
          </h2>
        </div>

        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          {events.map((ev, idx) => (
            <div
              key={idx}
              className="p-8 rounded-2xl bg-gradient-to-br from-slate-900 to-slate-900/40 border border-white/10 hover:border-orange-500/40 transition-all duration-300 shadow-xl group hover:-translate-y-1.5"
            >
              <div className="w-10 h-10 rounded-xl bg-orange-500/10 border border-orange-500/20 flex items-center justify-center text-orange-400 mb-6 group-hover:scale-110 transition-transform">
                <Sparkles className="w-5 h-5" />
              </div>
              <h3 className="text-white font-bold text-lg mb-2">
                {ev.title}
              </h3>
              <div className="text-orange-400 text-xs font-semibold tracking-wide uppercase mb-3">
                {ev.org}
              </div>
              <p className="text-slate-400 text-sm leading-relaxed font-light">
                {ev.desc}
              </p>
            </div>
          ))}
        </div>

        {/* Learning Highlights Banner */}
        <div className="mt-16 p-8 rounded-2xl bg-gradient-to-r from-slate-900 via-slate-900/90 to-orange-950/30 border border-orange-500/30 shadow-2xl flex flex-col lg:flex-row items-center justify-between gap-8">
          <div className="flex items-start gap-4">
            <div className="w-12 h-12 rounded-xl bg-orange-500/20 border border-orange-500/40 flex items-center justify-center text-orange-400 shrink-0">
              <Share2 className="w-6 h-6" />
            </div>
            <div>
              <h4 className="text-white font-bold text-xl mb-1">
                Active Knowledge Sharing on LinkedIn
              </h4>
              <p className="text-slate-300 text-sm max-w-2xl font-light leading-relaxed">
                Actively publishing technical breakdowns on Computer Networking, IP Addressing, and Subnetting. Continually exploring practical applications of AI tools in software engineering.
              </p>
            </div>
          </div>
          <a
            href="https://www.linkedin.com/in/prasad-thorat-a38578372?utm_source=share_via&utm_content=profile&utm_medium=member_android"
            target="_blank"
            rel="noopener noreferrer"
            className="px-6 py-3 rounded-xl bg-orange-500 hover:bg-orange-600 text-white font-semibold text-xs tracking-wider uppercase transition-all duration-300 shadow-lg shadow-orange-500/20 shrink-0 flex items-center gap-2"
          >
            <span>Follow LinkedIn Activity</span>
            <ChevronRight className="w-4 h-4" />
          </a>
        </div>
      </div>
    </section>
  );
};

const Contact = () => {
  return (
    <section id="contact" className="relative z-20 py-28 bg-slate-950 border-t border-white/5">
      <div className="max-w-7xl mx-auto px-6 md:px-12 text-center flex flex-col items-center">
        <div className="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-orange-500/10 border border-orange-500/20 text-orange-400 text-xs font-semibold tracking-widest uppercase mb-6">
          <MessageSquare className="w-3.5 h-3.5" />
          <span>GET IN TOUCH</span>
        </div>

        <h2 className="text-4xl sm:text-6xl font-black text-white tracking-tight mb-4">
          LET'S BUILD WHAT'S NEXT.
        </h2>

        <p className="text-slate-400 text-base sm:text-lg max-w-xl font-light leading-relaxed mb-12">
          Cybersecurity. AI. Software Engineering. Available for opportunities, collaboration, and engineering discussions.
        </p>

        {/* Large Action Buttons */}
        <div className="flex flex-wrap items-center justify-center gap-4 mb-16">
          <a
            href="https://www.linkedin.com/in/prasad-thorat-a38578372?utm_source=share_via&utm_content=profile&utm_medium=member_android"
            target="_blank"
            rel="noopener noreferrer"
            className="flex items-center gap-3 px-8 py-4 rounded-xl bg-orange-500 hover:bg-orange-600 text-white font-bold text-sm tracking-wider uppercase transition-all duration-300 shadow-xl shadow-orange-500/25 hover:scale-105"
          >
            <Linkedin className="w-5 h-5" />
            <span>Connect on LinkedIn</span>
          </a>

          <a
            href="https://github.com/prasadthorat25uid-arch"
            target="_blank"
            rel="noopener noreferrer"
            className="flex items-center gap-3 px-8 py-4 rounded-xl bg-slate-900 hover:bg-slate-800 text-white font-bold text-sm tracking-wider uppercase border border-white/10 hover:border-orange-500/50 transition-all duration-300 shadow-xl hover:scale-105"
          >
            <Github className="w-5 h-5 text-orange-400" />
            <span>View GitHub</span>
          </a>

          <a
            href="https://wa.me/918010989708"
            target="_blank"
            rel="noopener noreferrer"
            className="flex items-center gap-3 px-8 py-4 rounded-xl bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-sm tracking-wider uppercase transition-all duration-300 shadow-xl shadow-emerald-600/25 hover:scale-105"
          >
            <MessageSquare className="w-5 h-5" />
            <span>Message on WhatsApp</span>
          </a>
        </div>

        {/* Footer Meta Copyright */}
        <div className="pt-12 border-t border-white/5 w-full flex flex-col sm:flex-row items-center justify-between text-xs text-slate-500 gap-4">
          <div>
            © {new Date().getFullYear()} Prasad Sudhir Thorat. All rights reserved.
          </div>
          <div className="flex items-center gap-6">
            <span>Sanjivani University, Maharashtra</span>
            <span>B.Tech CSE</span>
          </div>
        </div>
      </div>
    </section>
  );
};

export default function App() {
  return (
    <div className="min-h-screen bg-slate-950 text-slate-100 font-sans selection:bg-orange-500 selection:text-white relative overflow-x-hidden">
      {/* Reusable Three.js Bokeh Layer */}
      <CinematicLayer />

      {/* Floating Top Navbar */}
      <Navigation />

      {/* Hero Section */}
      <Hero />

      {/* About Section */}
      <About />

      {/* Skills Domain Section */}
      <Skills />

      {/* Experience Section */}
      <Experience />

      {/* Certifications Section */}
      <Certifications />

      {/* Moments & Events Section */}
      <Moments />

      {/* Contact Section */}
      <Contact />
    </div>
  );
}
