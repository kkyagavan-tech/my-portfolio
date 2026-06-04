<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover"/>
  <meta name="apple-mobile-web-app-capable" content="yes"/>
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"/>
  <meta name="theme-color" content="#080808"/>
  <title>Yagavan Karthikeyen | Photographer</title>
  <link rel="preconnect" href="https://fonts.googleapis.com"/>
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,300;0,400;0,500;1,300;1,400&family=Outfit:wght@200;300;400&display=swap" rel="stylesheet"/>

  <style>
    /* ═══════════════════════════════════════
       CSS CUSTOM PROPERTIES
    ═══════════════════════════════════════ */
    :root {
      --bg:        #080808;
      --surface:   #101010;
      --card:      #141414;
      --border:    #1e1e1e;
      --gold:      #c8a96d;
      --gold-soft: rgba(200,169,109,0.15);
      --gold-dim:  #7a6030;
      --white:     #f2ede5;
      --muted:     #696059;
      --text:      #bbb4a8;
      --radius:    0px;

      /* iOS safe area insets */
      --sat: env(safe-area-inset-top, 0px);
      --sar: env(safe-area-inset-right, 0px);
      --sab: env(safe-area-inset-bottom, 0px);
      --sal: env(safe-area-inset-left, 0px);
    }

    /* ═══════════════════════════════════════
       RESET & BASE
    ═══════════════════════════════════════ */
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
    }

    html {
      scroll-behavior: smooth;
      -webkit-text-size-adjust: 100%;
      text-size-adjust: 100%;
    }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'Outfit', sans-serif;
      font-weight: 300;
      letter-spacing: 0.03em;
      overflow-x: hidden;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      /* iOS momentum scrolling */
      -webkit-overflow-scrolling: touch;
    }

    img {
      display: block;
      max-width: 100%;
      /* Prevent iOS long-press save dialog on images */
      -webkit-user-select: none;
      user-select: none;
      -webkit-touch-callout: none;
    }

    a {
      -webkit-tap-highlight-color: transparent;
      touch-action: manipulation;
    }

    button {
      -webkit-tap-highlight-color: transparent;
      touch-action: manipulation;
      cursor: pointer;
    }

    /* ═══════════════════════════════════════
       GRAIN TEXTURE OVERLAY
    ═══════════════════════════════════════ */
    .grain {
      position: fixed;
      inset: 0;
      z-index: 9998;
      pointer-events: none;
      opacity: 0.035;
      background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='g'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23g)'/%3E%3C/svg%3E");
      background-repeat: repeat;
    }

    /* ═══════════════════════════════════════
       NAVIGATION
    ═══════════════════════════════════════ */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 500;
      display: -webkit-flex;
      display: flex;
      -webkit-justify-content: space-between;
      justify-content: space-between;
      -webkit-align-items: center;
      align-items: center;
      padding: calc(1.4rem + var(--sat)) 3rem 1.4rem;
      background: linear-gradient(to bottom, rgba(8,8,8,0.96) 0%, rgba(8,8,8,0.0) 100%);
      -webkit-backdrop-filter: blur(12px) saturate(0.8);
      backdrop-filter: blur(12px) saturate(0.8);
      transition: background 0.4s ease;
    }

    nav.scrolled {
      background: rgba(8,8,8,0.97);
    }

    .nav-logo {
      font-family: 'Playfair Display', serif;
      font-size: 1.15rem;
      font-weight: 400;
      letter-spacing: 0.16em;
      color: var(--white);
      text-decoration: none;
      white-space: nowrap;
    }

    .nav-logo span { color: var(--gold); }

    .nav-links {
      display: -webkit-flex;
      display: flex;
      gap: 2.6rem;
      list-style: none;
    }

    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 0.65rem;
      letter-spacing: 0.28em;
      text-transform: uppercase;
      transition: color 0.3s;
      padding: 4px 0;
    }

    .nav-links a:hover,
    .nav-links a:focus { color: var(--gold); outline: none; }

    /* ── HAMBURGER ── */
    .hamburger {
      display: none;
      -webkit-flex-direction: column;
      flex-direction: column;
      gap: 5px;
      background: none;
      border: none;
      padding: 8px;
      margin-right: -8px;
      z-index: 600;
      position: relative;
    }

    .hamburger span {
      display: block;
      width: 22px;
      height: 1px;
      background: var(--white);
      -webkit-transition: all 0.35s cubic-bezier(0.77,0,0.175,1);
      transition: all 0.35s cubic-bezier(0.77,0,0.175,1);
      -webkit-transform-origin: center;
      transform-origin: center;
    }

    .hamburger.open span:nth-child(1) {
      -webkit-transform: translateY(6px) rotate(45deg);
      transform: translateY(6px) rotate(45deg);
    }
    .hamburger.open span:nth-child(2) { opacity: 0; }
    .hamburger.open span:nth-child(3) {
      -webkit-transform: translateY(-6px) rotate(-45deg);
      transform: translateY(-6px) rotate(-45deg);
    }

    /* ── MOBILE FULL-SCREEN MENU ── */
    .mobile-menu {
      position: fixed;
      inset: 0;
      z-index: 490;
      background: rgba(8,8,8,0.99);
      display: -webkit-flex;
      display: flex;
      -webkit-flex-direction: column;
      flex-direction: column;
      -webkit-justify-content: center;
      justify-content: center;
      -webkit-align-items: center;
      align-items: center;
      gap: 0.4rem;
      /* iOS: use transform for performance */
      -webkit-transform: translateX(100%);
      transform: translateX(100%);
      -webkit-transition: -webkit-transform 0.5s cubic-bezier(0.77,0,0.175,1);
      transition: transform 0.5s cubic-bezier(0.77,0,0.175,1);
      /* Safe area padding at bottom for iOS home indicator */
      padding-bottom: var(--sab);
    }

    .mobile-menu.open {
      -webkit-transform: translateX(0);
      transform: translateX(0);
    }

    .mobile-menu a {
      font-family: 'Playfair Display', serif;
      font-size: 2.4rem;
      font-weight: 300;
      letter-spacing: 0.1em;
      color: var(--white);
      text-decoration: none;
      padding: 0.8rem 2rem;
      opacity: 0;
      -webkit-transform: translateX(20px);
      transform: translateX(20px);
      -webkit-transition: color 0.3s, opacity 0.4s ease, -webkit-transform 0.4s ease;
      transition: color 0.3s, opacity 0.4s ease, transform 0.4s ease;
    }

    .mobile-menu.open a {
      opacity: 1;
      -webkit-transform: none;
      transform: none;
    }

    .mobile-menu.open a:nth-child(1) { transition-delay: 0.15s; }
    .mobile-menu.open a:nth-child(2) { transition-delay: 0.22s; }
    .mobile-menu.open a:nth-child(3) { transition-delay: 0.29s; }
    .mobile-menu.open a:nth-child(4) { transition-delay: 0.36s; }

    .mobile-menu a:hover { color: var(--gold); }

    .mobile-gold-line {
      width: 1px;
      height: 60px;
      background: var(--gold-dim);
      margin: 1rem 0;
      opacity: 0;
      transition: opacity 0.5s 0.4s;
    }

    .mobile-menu.open .mobile-gold-line { opacity: 1; }

    /* ═══════════════════════════════════════
       HERO
    ═══════════════════════════════════════ */
    .hero {
      position: relative;
      width: 100%;
      height: 100vh;
      /* iOS: fallback for vh bug */
      height: 100svh;
      min-height: 580px;
      display: -webkit-flex;
      display: flex;
      -webkit-flex-direction: column;
      flex-direction: column;
      -webkit-justify-content: flex-end;
      justify-content: flex-end;
      -webkit-align-items: flex-start;
      align-items: flex-start;
      overflow: hidden;
    }

    .hero-bg {
      position: absolute;
      inset: 0;
      background: url('https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=1800&q=85') center center / cover no-repeat;
      -webkit-filter: brightness(0.28) contrast(1.12) saturate(0.85);
      filter: brightness(0.28) contrast(1.12) saturate(0.85);
      /* GPU acceleration for iOS */
      -webkit-transform: translateZ(0) scale(1.06);
      transform: translateZ(0) scale(1.06);
      will-change: transform;
      -webkit-animation: heroZoom 18s ease-in-out infinite alternate;
      animation: heroZoom 18s ease-in-out infinite alternate;
    }

    @-webkit-keyframes heroZoom {
      from { -webkit-transform: translateZ(0) scale(1.06); transform: translateZ(0) scale(1.06); }
      to   { -webkit-transform: translateZ(0) scale(1.12); transform: translateZ(0) scale(1.12); }
    }
    @keyframes heroZoom {
      from { transform: translateZ(0) scale(1.06); }
      to   { transform: translateZ(0) scale(1.12); }
    }

    .hero-gradient {
      position: absolute;
      inset: 0;
      background: linear-gradient(
        to top,
        rgba(8,8,8,1.0) 0%,
        rgba(8,8,8,0.55) 40%,
        rgba(8,8,8,0.08) 75%,
        transparent 100%
      );
    }

    .hero-content {
      position: relative;
      z-index: 2;
      padding: 0 clamp(1.4rem, 6vw, 5rem) clamp(3.5rem, 8vh, 6rem);
      padding-left: calc(clamp(1.4rem, 6vw, 5rem) + var(--sal));
      padding-right: calc(clamp(1.4rem, 6vw, 5rem) + var(--sar));
      padding-bottom: calc(clamp(3.5rem, 8vh, 6rem) + var(--sab));
      max-width: 700px;
      -webkit-animation: heroReveal 1.6s cubic-bezier(0.16,1,0.3,1) both;
      animation: heroReveal 1.6s cubic-bezier(0.16,1,0.3,1) both;
    }

    @-webkit-keyframes heroReveal {
      from { opacity: 0; -webkit-transform: translateY(40px); transform: translateY(40px); }
      to   { opacity: 1; -webkit-transform: none; transform: none; }
    }
    @keyframes heroReveal {
      from { opacity: 0; transform: translateY(40px); }
      to   { opacity: 1; transform: none; }
    }

    .hero-eyebrow {
      font-size: 0.6rem;
      letter-spacing: 0.45em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 1.4rem;
      -webkit-animation: heroReveal 1.6s 0.1s cubic-bezier(0.16,1,0.3,1) both;
      animation: heroReveal 1.6s 0.1s cubic-bezier(0.16,1,0.3,1) both;
    }

    .hero-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(3rem, 10vw, 7rem);
      font-weight: 300;
      line-height: 0.95;
      color: var(--white);
      margin-bottom: 1.8rem;
      -webkit-animation: heroReveal 1.6s 0.2s cubic-bezier(0.16,1,0.3,1) both;
      animation: heroReveal 1.6s 0.2s cubic-bezier(0.16,1,0.3,1) both;
    }

    .hero-title em {
      display: block;
      font-style: italic;
      color: var(--gold);
    }

    .hero-desc {
      font-size: clamp(0.75rem, 2.2vw, 0.88rem);
      line-height: 2;
      color: var(--muted);
      max-width: 380px;
      margin-bottom: 2.4rem;
      -webkit-animation: heroReveal 1.6s 0.3s cubic-bezier(0.16,1,0.3,1) both;
      animation: heroReveal 1.6s 0.3s cubic-bezier(0.16,1,0.3,1) both;
    }

    .hero-cta {
      display: -webkit-flex;
      display: flex;
      gap: 1.2rem;
      -webkit-flex-wrap: wrap;
      flex-wrap: wrap;
      -webkit-animation: heroReveal 1.6s 0.4s cubic-bezier(0.16,1,0.3,1) both;
      animation: heroReveal 1.6s 0.4s cubic-bezier(0.16,1,0.3,1) both;
    }

    .btn {
      display: inline-block;
      padding: 0.9rem 2.2rem;
      font-family: 'Outfit', sans-serif;
      font-size: 0.62rem;
      font-weight: 400;
      letter-spacing: 0.3em;
      text-transform: uppercase;
      text-decoration: none;
      border: 1px solid var(--gold);
      color: var(--gold);
      background: transparent;
      -webkit-transition: background 0.3s, color 0.3s, -webkit-transform 0.2s;
      transition: background 0.3s, color 0.3s, transform 0.2s;
      /* iOS active state */
      -webkit-tap-highlight-color: transparent;
      touch-action: manipulation;
    }

    .btn:hover, .btn:active {
      background: var(--gold);
      color: var(--bg);
    }

    .btn:active {
      -webkit-transform: scale(0.97);
      transform: scale(0.97);
    }

    .btn-ghost {
      border-color: rgba(242,237,229,0.2);
      color: rgba(242,237,229,0.5);
    }

    .btn-ghost:hover, .btn-ghost:active {
      background: rgba(242,237,229,0.06);
      color: var(--white);
    }

    /* scroll indicator */
    .scroll-hint {
      position: absolute;
      bottom: calc(2rem + var(--sab));
      right: calc(2.5rem + var(--sar));
      z-index: 2;
      display: -webkit-flex;
      display: flex;
      -webkit-flex-direction: column;
      flex-direction: column;
      -webkit-align-items: center;
      align-items: center;
      gap: 0.6rem;
      opacity: 0.45;
    }

    .scroll-hint span {
      font-size: 0.55rem;
      letter-spacing: 0.3em;
      text-transform: uppercase;
      color: var(--white);
      writing-mode: vertical-rl;
    }

    .scroll-line {
      width: 1px;
      height: 48px;
      background: linear-gradient(to bottom, var(--white), transparent);
      -webkit-animation: scrollPulse 2.5s ease-in-out infinite;
      animation: scrollPulse 2.5s ease-in-out infinite;
    }

    @-webkit-keyframes scrollPulse {
      0%, 100% { opacity: 0.4; -webkit-transform: scaleY(1); transform: scaleY(1); }
      50%       { opacity: 1;   -webkit-transform: scaleY(0.6); transform: scaleY(0.6); }
    }
    @keyframes scrollPulse {
      0%, 100% { opacity: 0.4; transform: scaleY(1); }
      50%       { opacity: 1;   transform: scaleY(0.6); }
    }

    /* ═══════════════════════════════════════
       SHARED SECTION STYLES
    ═══════════════════════════════════════ */
    .section-pad {
      padding: clamp(4rem, 10vh, 8rem) clamp(1.4rem, 6vw, 5rem);
      padding-left: calc(clamp(1.4rem, 6vw, 5rem) + var(--sal));
      padding-right: calc(clamp(1.4rem, 6vw, 5rem) + var(--sar));
    }

    .label {
      font-size: 0.58rem;
      letter-spacing: 0.42em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 1rem;
    }

    .heading {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 5.5vw, 3.8rem);
      font-weight: 300;
      color: var(--white);
      line-height: 1.08;
      margin-bottom: 1.8rem;
    }

    .heading em { font-style: italic; color: var(--gold); }

    .rule {
      width: 40px;
      height: 1px;
      background: var(--gold-dim);
      margin-bottom: 2.4rem;
    }

    /* ═══════════════════════════════════════
       ABOUT
    ═══════════════════════════════════════ */
    #about {
      background: var(--surface);
    }

    .about-inner {
      display: -webkit-flex;
      display: flex;
      gap: clamp(2.5rem, 6vw, 5.5rem);
      -webkit-align-items: center;
      align-items: center;
      max-width: 1240px;
      margin: 0 auto;
    }

    .about-visual {
      -webkit-flex: 0 0 38%;
      flex: 0 0 38%;
      position: relative;
    }

    .about-visual::after {
      content: '';
      position: absolute;
      top: -14px; left: -14px;
      right: 14px; bottom: 14px;
      border: 1px solid var(--gold-dim);
      pointer-events: none;
      z-index: 0;
    }

    .about-visual img {
      width: 100%;
      aspect-ratio: 3/4;
      -o-object-fit: cover;
      object-fit: cover;
      -webkit-filter: brightness(0.88) contrast(1.06) sepia(0.1);
      filter: brightness(0.88) contrast(1.06) sepia(0.1);
      position: relative;
      z-index: 1;
    }

    .about-tag {
      position: absolute;
      bottom: -14px; right: -14px;
      background: var(--bg);
      border: 1px solid var(--border);
      padding: 1rem 1.4rem;
      z-index: 2;
      text-align: center;
    }

    .about-tag strong {
      display: block;
      font-family: 'Playfair Display', serif;
      font-size: 1.9rem;
      font-weight: 300;
      color: var(--gold);
      line-height: 1;
    }

    .about-tag small {
      font-size: 0.56rem;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--muted);
      margin-top: 0.3rem;
      display: block;
    }

    .about-body { -webkit-flex: 1; flex: 1; }

    .about-body p {
      font-size: clamp(0.8rem, 1.8vw, 0.9rem);
      line-height: 2.05;
      color: var(--text);
      margin-bottom: 1.3rem;
    }

    .about-body p:last-of-type { margin-bottom: 2rem; }

    .stat-row {
      display: -webkit-flex;
      display: flex;
      gap: 2.5rem;
      -webkit-flex-wrap: wrap;
      flex-wrap: wrap;
      padding-top: 2rem;
      border-top: 1px solid var(--border);
      margin-top: 2.5rem;
    }

    .stat b {
      display: block;
      font-family: 'Playfair Display', serif;
      font-size: 2.2rem;
      font-weight: 300;
      color: var(--gold);
      line-height: 1;
    }

    .stat small {
      font-size: 0.58rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--muted);
      margin-top: 0.4rem;
      display: block;
    }

    /* ═══════════════════════════════════════
       GALLERY
    ═══════════════════════════════════════ */
    #gallery { background: var(--bg); }

    .gallery-hd {
      text-align: center;
      margin-bottom: clamp(2.5rem, 5vw, 4rem);
    }

    .gallery-hd .rule { margin: 0 auto 0; }

    .masonry {
      display: -webkit-flex;
      display: flex;
      gap: 1rem;
      max-width: 1300px;
      margin: 0 auto;
    }

    .masonry-col {
      -webkit-flex: 1;
      flex: 1;
      display: -webkit-flex;
      display: flex;
      -webkit-flex-direction: column;
      flex-direction: column;
      gap: 1rem;
    }

    .masonry-col:nth-child(2) { margin-top: 2.5rem; }
    .masonry-col:nth-child(3) { margin-top: 5rem; }

    .photo-card {
      position: relative;
      overflow: hidden;
      cursor: pointer;
      -webkit-transform: translateZ(0);
      transform: translateZ(0);
    }

    .photo-card img {
      width: 100%;
      -o-object-fit: cover;
      object-fit: cover;
      -webkit-filter: brightness(0.78) contrast(1.08) saturate(0.85);
      filter: brightness(0.78) contrast(1.08) saturate(0.85);
      -webkit-transition: -webkit-transform 0.7s cubic-bezier(0.25,0.46,0.45,0.94), -webkit-filter 0.5s ease;
      transition: transform 0.7s cubic-bezier(0.25,0.46,0.45,0.94), filter 0.5s ease;
      -webkit-transform: scale(1);
      transform: scale(1);
      will-change: transform;
    }

    .photo-card:hover img {
      -webkit-transform: scale(1.07);
      transform: scale(1.07);
      -webkit-filter: brightness(0.92) contrast(1.1) saturate(0.95);
      filter: brightness(0.92) contrast(1.1) saturate(0.95);
    }

    .photo-caption {
      position: absolute;
      inset: 0;
      background: linear-gradient(to top, rgba(8,8,8,0.82) 0%, transparent 55%);
      display: -webkit-flex;
      display: flex;
      -webkit-align-items: flex-end;
      align-items: flex-end;
      padding: 1.2rem;
      opacity: 0;
      -webkit-transition: opacity 0.4s ease;
      transition: opacity 0.4s ease;
    }

    .photo-card:hover .photo-caption { opacity: 1; }

    .photo-caption p {
      font-family: 'Playfair Display', serif;
      font-size: 1rem;
      font-style: italic;
      color: var(--white);
    }

    /* TOUCH: show caption always on touch devices */
    @media (hover: none) {
      .photo-caption { opacity: 1; }
    }

    /* ═══════════════════════════════════════
       PHILOSOPHY BAND
    ═══════════════════════════════════════ */
    .philosophy {
      background: var(--card);
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      padding: clamp(3rem, 7vh, 5.5rem) clamp(1.4rem, 6vw, 5rem);
      padding-left: calc(clamp(1.4rem, 6vw, 5rem) + var(--sal));
      padding-right: calc(clamp(1.4rem, 6vw, 5rem) + var(--sar));
      text-align: center;
    }

    .philosophy blockquote {
      font-family: 'Playfair Display', serif;
      font-size: clamp(1.5rem, 4vw, 2.6rem);
      font-weight: 300;
      font-style: italic;
      color: var(--white);
      max-width: 820px;
      margin: 0 auto 1.4rem;
      line-height: 1.55;
    }

    .philosophy cite {
      font-size: 0.62rem;
      letter-spacing: 0.28em;
      text-transform: uppercase;
      color: var(--gold);
      font-style: normal;
    }

    /* ═══════════════════════════════════════
       SERVICES
    ═══════════════════════════════════════ */
    #services { background: var(--surface); }

    .services-inner { max-width: 1240px; margin: 0 auto; }

    .services-grid {
      display: -webkit-flex;
      display: flex;
      gap: 1.4rem;
      -webkit-flex-wrap: wrap;
      flex-wrap: wrap;
      margin-top: 3rem;
    }

    .svc {
      -webkit-flex: 1 1 260px;
      flex: 1 1 260px;
      border: 1px solid var(--border);
      padding: 2.6rem 2.2rem;
      position: relative;
      overflow: hidden;
      -webkit-transition: border-color 0.4s, -webkit-transform 0.3s;
      transition: border-color 0.4s, transform 0.3s;
      background: var(--card);
    }

    .svc::after {
      content: '';
      position: absolute;
      bottom: 0; left: 0;
      width: 0; height: 2px;
      background: var(--gold);
      -webkit-transition: width 0.6s cubic-bezier(0.16,1,0.3,1);
      transition: width 0.6s cubic-bezier(0.16,1,0.3,1);
    }

    .svc:hover::after { width: 100%; }
    .svc:hover { border-color: #2a2a2a; }

    .svc-num {
      font-family: 'Playfair Display', serif;
      font-size: 3.5rem;
      font-weight: 300;
      color: var(--border);
      line-height: 1;
      margin-bottom: 1.4rem;
    }

    .svc-name {
      font-family: 'Playfair Display', serif;
      font-size: 1.35rem;
      font-weight: 400;
      color: var(--white);
      margin-bottom: 1rem;
    }

    .svc-desc {
      font-size: 0.8rem;
      line-height: 1.95;
      color: var(--muted);
    }

    /* ═══════════════════════════════════════
       TESTIMONIAL
    ═══════════════════════════════════════ */
    #testimonial {
      background: var(--bg);
      text-align: center;
      padding: clamp(4rem, 9vh, 7rem) clamp(1.4rem, 6vw, 5rem);
      padding-left: calc(clamp(1.4rem, 6vw, 5rem) + var(--sal));
      padding-right: calc(clamp(1.4rem, 6vw, 5rem) + var(--sar));
    }

    .testi-mark {
      font-family: 'Playfair Display', serif;
      font-size: 7rem;
      line-height: 0.3;
      color: var(--gold-dim);
      display: block;
      margin-bottom: 2rem;
    }

    .testi-text {
      font-family: 'Playfair Display', serif;
      font-size: clamp(1.3rem, 3.5vw, 2rem);
      font-weight: 300;
      font-style: italic;
      color: var(--white);
      max-width: 780px;
      margin: 0 auto 1.8rem;
      line-height: 1.6;
    }

    .testi-who {
      font-size: 0.62rem;
      letter-spacing: 0.28em;
      text-transform: uppercase;
      color: var(--gold);
    }

    .testi-who span {
      color: var(--muted);
      margin-left: 0.5rem;
    }

    /* ═══════════════════════════════════════
       CONTACT
    ═══════════════════════════════════════ */
    #contact { background: var(--surface); }

    .contact-inner {
      max-width: 720px;
      margin: 0 auto;
      text-align: center;
    }

    .contact-intro {
      font-size: clamp(0.78rem, 1.8vw, 0.88rem);
      line-height: 2;
      color: var(--muted);
      margin-bottom: 3rem;
    }

    .cform {
      display: -webkit-flex;
      display: flex;
      -webkit-flex-direction: column;
      flex-direction: column;
      gap: 1.1rem;
      text-align: left;
    }

    .cform-row {
      display: -webkit-flex;
      display: flex;
      gap: 1.1rem;
    }

    .cform input,
    .cform textarea,
    .cform select {
      width: 100%;
      background: var(--card);
      border: 1px solid var(--border);
      color: var(--white);
      padding: 1rem 1.2rem;
      font-family: 'Outfit', sans-serif;
      font-size: 0.8rem;
      font-weight: 300;
      letter-spacing: 0.08em;
      outline: none;
      -webkit-appearance: none;
      appearance: none;
      border-radius: 0;
      -webkit-transition: border-color 0.3s;
      transition: border-color 0.3s;
      /* iOS: prevent font zoom on focus */
      font-size: max(0.8rem, 16px);
    }

    .cform input:focus,
    .cform textarea:focus,
    .cform select:focus {
      border-color: var(--gold);
    }

    .cform input::-webkit-input-placeholder,
    .cform textarea::-webkit-input-placeholder { color: var(--muted); }
    .cform input::placeholder,
    .cform textarea::placeholder { color: var(--muted); }

    .cform textarea {
      resize: vertical;
      min-height: 130px;
    }

    .btn-submit {
      width: 100%;
      padding: 1.1rem;
      background: none;
      border: 1px solid var(--gold);
      color: var(--gold);
      font-family: 'Outfit', sans-serif;
      font-size: 0.65rem;
      letter-spacing: 0.32em;
      text-transform: uppercase;
      cursor: pointer;
      -webkit-transition: background 0.3s, color 0.3s, -webkit-transform 0.2s;
      transition: background 0.3s, color 0.3s, transform 0.2s;
    }

    .btn-submit:hover { background: var(--gold); color: var(--bg); }
    .btn-submit:active {
      -webkit-transform: scale(0.98);
      transform: scale(0.98);
    }

    .form-success {
      display: none;
      font-size: 0.78rem;
      letter-spacing: 0.15em;
      color: var(--gold);
      margin-top: 1.2rem;
      padding: 1rem;
      border: 1px solid var(--gold-dim);
    }

    /* ═══════════════════════════════════════
       FOOTER
    ═══════════════════════════════════════ */
    footer {
      border-top: 1px solid var(--border);
      background: var(--bg);
      padding: 2.5rem clamp(1.4rem, 6vw, 5rem);
      padding-left: calc(clamp(1.4rem, 6vw, 5rem) + var(--sal));
      padding-right: calc(clamp(1.4rem, 6vw, 5rem) + var(--sar));
      /* iOS home indicator safe area */
      padding-bottom: calc(2.5rem + var(--sab));
      display: -webkit-flex;
      display: flex;
      -webkit-justify-content: space-between;
      justify-content: space-between;
      -webkit-align-items: center;
      align-items: center;
      -webkit-flex-wrap: wrap;
      flex-wrap: wrap;
      gap: 1.2rem;
    }

    .footer-logo {
      font-family: 'Playfair Display', serif;
      font-size: 1rem;
      letter-spacing: 0.14em;
      color: var(--white);
    }

    .footer-copy {
      font-size: 0.6rem;
      letter-spacing: 0.16em;
      color: var(--muted);
    }

    .footer-links {
      display: -webkit-flex;
      display: flex;
      gap: 1.8rem;
    }

    .footer-links a {
      font-size: 0.6rem;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--muted);
      text-decoration: none;
      -webkit-transition: color 0.3s;
      transition: color 0.3s;
      padding: 8px 0;
    }

    .footer-links a:hover { color: var(--gold); }

    /* ═══════════════════════════════════════
       SCROLL REVEAL
    ═══════════════════════════════════════ */
    .reveal {
      opacity: 0;
      -webkit-transform: translateY(24px);
      transform: translateY(24px);
      -webkit-transition: opacity 0.9s cubic-bezier(0.16,1,0.3,1), -webkit-transform 0.9s cubic-bezier(0.16,1,0.3,1);
      transition: opacity 0.9s cubic-bezier(0.16,1,0.3,1), transform 0.9s cubic-bezier(0.16,1,0.3,1);
    }

    .reveal.on {
      opacity: 1;
      -webkit-transform: none;
      transform: none;
    }

    .reveal-d1 { transition-delay: 0.1s; }
    .reveal-d2 { transition-delay: 0.22s; }
    .reveal-d3 { transition-delay: 0.34s; }

    /* ═══════════════════════════════════════
       RESPONSIVE — TABLET
    ═══════════════════════════════════════ */
    @media (max-width: 900px) {
      .about-inner { -webkit-flex-direction: column; flex-direction: column; gap: 3rem; }
      .about-visual { -webkit-flex: none; flex: none; width: 70%; max-width: 340px; }
      .about-body { width: 100%; }
      .masonry-col:nth-child(3) { display: none; }
      .masonry-col:nth-child(2) { margin-top: 2rem; }
    }

    /* ═══════════════════════════════════════
       RESPONSIVE — MOBILE (≤ 768px)
    ═══════════════════════════════════════ */
    @media (max-width: 768px) {
      nav { padding: calc(1rem + var(--sat)) 1.4rem 1rem; }
      .nav-links { display: none; }
      .hamburger { display: -webkit-flex; display: flex; }

      .about-visual { width: 80%; }

      .masonry {
        -webkit-flex-direction: column;
        flex-direction: column;
        gap: 0.8rem;
      }

      .masonry-col { margin-top: 0 !important; }
      .masonry-col:nth-child(3) { display: -webkit-flex; display: flex; }

      .cform-row {
        -webkit-flex-direction: column;
        flex-direction: column;
      }

      footer {
        -webkit-flex-direction: column;
        flex-direction: column;
        text-align: center;
        gap: 1rem;
      }

      .scroll-hint { display: none; }

      .services-grid { gap: 1rem; }
    }

    /* ═══════════════════════════════════════
       RESPONSIVE — SMALL PHONES (≤ 430px)
    ═══════════════════════════════════════ */
    @media (max-width: 430px) {
      .about-visual { width: 100%; }
      .about-visual::after { display: none; }
      .about-tag { right: 0; }
    }

    /* ═══════════════════════════════════════
       iOS NOTCH / DYNAMIC ISLAND (≥ 390px)
       Extra safe-area class
    ═══════════════════════════════════════ */
    @supports (padding-top: env(safe-area-inset-top)) {
      .hero-content {
        padding-bottom: calc(clamp(3.5rem, 8vh, 6rem) + env(safe-area-inset-bottom, 0px));
      }
    }
  </style>
</head>
<body>

  <!-- GRAIN -->
  <div class="grain" aria-hidden="true"></div>

  <!-- ════════ NAV ════════ -->
  <nav id="nav">
    <a class="nav-logo" href="#" aria-label="Yagavan Karthikeyen Home">
      Y. <span>Karthikeyen</span>
    </a>
    <ul class="nav-links" role="list">
      <li><a href="#about">About</a></li>
      <li><a href="#gallery">Gallery</a></li>
      <li><a href="#services">Services</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <button class="hamburger" id="burger" aria-label="Toggle menu" aria-expanded="false" aria-controls="mobileNav">
      <span></span><span></span><span></span>
    </button>
  </nav>

  <!-- ════════ MOBILE NAV ════════ -->
  <nav class="mobile-menu" id="mobileNav" aria-hidden="true">
    <div class="mobile-gold-line"></div>
    <a href="#about"    onclick="closeNav()">About</a>
    <a href="#gallery"  onclick="closeNav()">Gallery</a>
    <a href="#services" onclick="closeNav()">Services</a>
    <a href="#contact"  onclick="closeNav()">Contact</a>
    <div class="mobile-gold-line"></div>
  </nav>

  <!-- ════════ HERO ════════ -->
  <header class="hero" id="home">
    <div class="hero-bg" aria-hidden="true"></div>
    <div class="hero-gradient" aria-hidden="true"></div>

    <div class="hero-content">
      <p class="hero-eyebrow">Fine Art · Documentary · Portrait</p>
      <h1 class="hero-title">
        Yagavan<br/>
        <em>Karthikeyen</em>
      </h1>
      <p class="hero-desc">
        Every frame breathes with intention. Every shadow whispers what words 
        can never say. I photograph the world at its most honest, luminous, 
        and quietly extraordinary.
      </p>
      <div class="hero-cta">
        <a href="#gallery" class="btn">View Work</a>
        <a href="#contact" class="btn btn-ghost">Book a Session</a>
      </div>
    </div>

    <div class="scroll-hint" aria-hidden="true">
      <span>Scroll</span>
      <div class="scroll-line"></div>
    </div>
  </header>

  <!-- ════════ ABOUT ════════ -->
  <section id="about" class="section-pad">
    <div class="about-inner">

      <div class="about-visual reveal">
        <img
          src="https://images.unsplash.com/photo-1516035069371-29a1b244cc32?w=800&q=80"
          alt="Yagavan Karthikeyen at work"
          loading="lazy"
          decoding="async"
        />
        <div class="about-tag">
          <strong>12+</strong>
          <small>Years Behind<br/>the Lens</small>
        </div>
      </div>

      <div class="about-body">
        <p class="label reveal">About Me</p>
        <h2 class="heading reveal">
          A Soul Who<br/><em>Sees Differently</em>
        </h2>
        <div class="rule reveal"></div>

        <p class="reveal reveal-d1">
          I am <strong style="color:var(--white); font-weight:400;">Yagavan Karthikeyen</strong> — 
          a visual storyteller rooted in Tamil Nadu, India, shaped by its mist-covered hills, 
          ancient temples, and the unhurried light that falls just before dusk. Photography, 
          for me, is not a profession. It is a language I was born knowing but spent years 
          learning to speak fluently.
        </p>
        <p class="reveal reveal-d2">
          Over a decade behind the lens has taught me one enduring truth: the most powerful 
          photographs are not made — they are witnessed. My role is simply to be present, 
          patient, and awake enough to recognize the moment before it slips away forever. 
          Whether I am shooting the fog-draped peaks of the Nilgiris or the quiet grace 
          of a face at rest, I bring the same reverence.
        </p>
        <p class="reveal reveal-d3">
          My work has taken me across South Asia and beyond, documenting weddings, 
          landscapes, people, and the sacred space between. I believe a great photograph 
          should make the viewer feel the temperature of the air, the weight of the silence, 
          the warmth behind a stranger's eyes.
        </p>

        <a href="#contact" class="btn reveal">Commission a Project</a>

        <div class="stat-row">
          <div class="stat reveal">
            <b>12+</b>
            <small>Years Active</small>
          </div>
          <div class="stat reveal reveal-d1">
            <b>340+</b>
            <small>Projects Done</small>
          </div>
          <div class="stat reveal reveal-d2">
            <b>28</b>
            <small>Awards Won</small>
          </div>
          <div class="stat reveal reveal-d3">
            <b>19</b>
            <small>Countries Visited</small>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ════════ GALLERY ════════ -->
  <section id="gallery" class="section-pad">
    <div class="gallery-hd">
      <p class="label reveal">Selected Work</p>
      <h2 class="heading reveal">The Gallery</h2>
      <div class="rule reveal" style="margin:0 auto 0;"></div>
    </div>

    <div class="masonry reveal">
      <!-- Col 1 -->
      <div class="masonry-col">
        <div class="photo-card">
          <img src="https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=700&q=80"
               alt="Alpine Silence" loading="lazy" decoding="async" style="aspect-ratio:3/4;"/>
          <div class="photo-caption"><p>Alpine Silence</p></div>
        </div>
        <div class="photo-card">
          <img src="https://images.unsplash.com/photo-1500534314209-a25ddb2bd429?w=700&q=80"
               alt="Emerald Canopy" loading="lazy" decoding="async" style="aspect-ratio:4/3;"/>
          <div class="photo-caption"><p>Emerald Canopy</p></div>
        </div>
        <div class="photo-card">
          <img src="https://images.unsplash.com/photo-1518020382113-a7e8fc38eac9?w=700&q=80"
               alt="Night Wanderer" loading="lazy" decoding="async" style="aspect-ratio:1/1;"/>
          <div class="photo-caption"><p>Night Wanderer</p></div>
        </div>
      </div>

      <!-- Col 2 -->
      <div class="masonry-col">
        <div class="photo-card">
          <img src="https://images.unsplash.com/photo-1470071459604-3b5ec3a7fe05?w=700&q=80"
               alt="Mountain Mist" loading="lazy" decoding="async" style="aspect-ratio:4/3;"/>
          <div class="photo-caption"><p>Mountain Mist</p></div>
        </div>
        <div class="photo-card">
          <img src="https://images.unsplash.com/photo-1505118380757-91f5f5632de0?w=700&q=80"
               alt="Shore Lines" loading="lazy" decoding="async" style="aspect-ratio:3/4;"/>
          <div class="photo-caption"><p>Shore Lines</p></div>
        </div>
        <div class="photo-card">
          <img src="https://images.unsplash.com/photo-1476610182048-b716b8518aae?w=700&q=80"
               alt="Golden Hours" loading="lazy" decoding="async" style="aspect-ratio:4/3;"/>
          <div class="photo-caption"><p>Golden Hours</p></div>
        </div>
      </div>

      <!-- Col 3 -->
      <div class="masonry-col">
        <div class="photo-card">
          <img src="https://images.unsplash.com/photo-1493246507139-91e8fad9978e?w=700&q=80"
               alt="Still Waters" loading="lazy" decoding="async" style="aspect-ratio:3/4;"/>
          <div class="photo-caption"><p>Still Waters</p></div>
        </div>
        <div class="photo-card">
          <img src="https://images.unsplash.com/photo-1419242902214-272b3f66ee7a?w=700&q=80"
               alt="Stellar Plains" loading="lazy" decoding="async" style="aspect-ratio:1/1;"/>
          <div class="photo-caption"><p>Stellar Plains</p></div>
        </div>
        <div class="photo-card">
          <img src="https://images.unsplash.com/photo-1542224566-6e85f2e6772f?w=700&q=80"
               alt="Monochrome Soul" loading="lazy" decoding="async" style="aspect-ratio:4/3;"/>
          <div class="photo-caption"><p>Monochrome Soul</p></div>
        </div>
      </div>
    </div>
  </section>

  <!-- ════════ PHILOSOPHY BAND ════════ -->
  <div class="philosophy">
    <blockquote class="reveal">
      "Photography is not about the camera. It is about the willingness 
      to stand in the dark and wait for the light to arrive."
    </blockquote>
    <cite class="reveal">— Yagavan Karthikeyen</cite>
  </div>

  <!-- ════════ SERVICES ════════ -->
  <section id="services" class="section-pad">
    <div class="services-inner">
      <p class="label reveal">What I Offer</p>
      <h2 class="heading reveal">Photography <em>Services</em></h2>
      <div class="rule reveal"></div>

      <div class="services-grid">
        <div class="svc reveal">
          <div class="svc-num">01</div>
          <div class="svc-name">Portrait & Editorial</div>
          <p class="svc-desc">
            Character-driven portraits that strip pretense and reveal the genuine 
            soul within. Shot in golden natural light or artfully crafted studio 
            environments tailored to your story.
          </p>
        </div>
        <div class="svc reveal reveal-d1">
          <div class="svc-num">02</div>
          <div class="svc-name">Landscape & Nature</div>
          <p class="svc-desc">
            Epic vistas, intimate details, and everything between. I travel to 
            the edges of the earth — from Himalayan ridgelines to coastal estuaries — 
            to bring back images that command silence and wonder.
          </p>
        </div>
        <div class="svc reveal reveal-d2">
          <div class="svc-num">03</div>
          <div class="svc-name">Weddings & Ceremonies</div>
          <p class="svc-desc">
            Your story deserves more than posed smiles. I document weddings 
            as they truly are — messy, beautiful, unrepeatable chapters of life 
            unfolding in real time, never to be staged again.
          </p>
        </div>
        <div class="svc reveal reveal-d3">
          <div class="svc-num">04</div>
          <div class="svc-name">Commercial & Brand</div>
          <p class="svc-desc">
            Visual identities built on authenticity. I work closely with brands 
            to create imagery that earns trust, communicates craft, and outlasts 
            every passing trend.
          </p>
        </div>
      </div>
    </div>
  </section>

  <!-- ════════ TESTIMONIAL ════════ -->
  <section id="testimonial">
    <span class="testi-mark reveal" aria-hidden="true">"</span>
    <p class="testi-text reveal">
      Yagavan doesn't just take photographs. He finds the light that lives 
      inside a moment and holds it perfectly still for the rest of us to see.
    </p>
    <p class="testi-who reveal">
      Priya Shanmugam <span>· Wedding Client, Chennai</span>
    </p>
  </section>

  <!-- ════════ CONTACT ════════ -->
  <section id="contact" class="section-pad">
    <div class="contact-inner">
      <p class="label reveal">Get In Touch</p>
      <h2 class="heading reveal">Let's Create Something<br/><em>Timeless</em></h2>
      <div class="rule reveal" style="margin:0 auto 2rem;"></div>
      <p class="contact-intro reveal">
        Whether you arrive with a fully formed vision or simply a feeling you 
        wish to capture, I am here to listen, collaborate, and craft images 
        that outlive the moment they were made. Reach out — every great 
        project begins with a single conversation.
      </p>

      <form class="cform reveal" id="contactForm" novalidate>
        <div class="cform-row">
          <input type="text"  name="name"    placeholder="Your Full Name"    required autocomplete="name"/>
          <input type="email" name="email"   placeholder="Email Address"     required autocomplete="email"/>
        </div>
        <input type="tel" name="phone" placeholder="Phone Number (optional)" autocomplete="tel"/>
        <input type="text" name="subject" placeholder="Subject — e.g. Wedding Photography, Portrait Session"/>
        <textarea name="message" placeholder="Tell me about your vision, your story, the feeling you want to capture…" required></textarea>
        <button type="submit" class="btn-submit">Send Message →</button>
      </form>

      <div class="form-success" id="formSuccess" role="alert">
        ✦ &nbsp; Thank you, message received. I'll be in touch within 24 hours.
      </div>
    </div>
  </section>

  <!-- ════════ FOOTER ════════ -->
  <footer>
    <div class="footer-logo">Yagavan Karthikeyen</div>
    <div class="footer-copy">© 2026 · All rights reserved</div>
    <nav class="footer-links" aria-label="Social links">
      <a href="#" aria-label="Instagram">Instagram</a>
      <a href="#" aria-label="Behance">Behance</a>
      <a href="#" aria-label="500px">500px</a>
    </nav>
  </footer>

  <!-- ════════ SCRIPTS ════════ -->
  <script>
    "use strict";

    /* ── NAV SCROLL ── */
    const navEl = document.getElementById('nav');
    window.addEventListener('scroll', () => {
      navEl.classList.toggle('scrolled', window.scrollY > 60);
    }, { passive: true });

    /* ── HAMBURGER ── */
    const burger   = document.getElementById('burger');
    const mobileNav = document.getElementById('mobileNav');
    let menuOpen = false;

    function openNav() {
      menuOpen = true;
      burger.classList.add('open');
      burger.setAttribute('aria-expanded', 'true');
      mobileNav.classList.add('open');
      mobileNav.setAttribute('aria-hidden', 'false');
      document.body.style.overflow = 'hidden';
    }

    function closeNav() {
      menuOpen = false;
      burger.classList.remove('open');
      burger.setAttribute('aria-expanded', 'false');
      mobileNav.classList.remove('open');
      mobileNav.setAttribute('aria-hidden', 'true');
      document.body.style.overflow = '';
    }

    burger.addEventListener('click', () => menuOpen ? closeNav() : openNav());

    /* Close on Escape */
    document.addEventListener('keydown', e => {
      if (e.key === 'Escape' && menuOpen) closeNav();
    });

    /* ── INTERSECTION OBSERVER (scroll reveal) ── */
    const revealEls = document.querySelectorAll('.reveal');

    if ('IntersectionObserver' in window) {
      const io = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('on');
            io.unobserve(entry.target);
          }
        });
      }, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });

      revealEls.forEach(el => io.observe(el));
    } else {
      /* Fallback for older iOS WebKit */
      revealEls.forEach(el => el.classList.add('on'));
    }

    /* ── CONTACT FORM ── */
    document.getElementById('contactForm').addEventListener('submit', function(e) {
      e.preventDefault();
      this.style.display = 'none';
      const ok = document.getElementById('formSuccess');
      ok.style.display = 'block';
    });
  </script>
</body>
</html>
