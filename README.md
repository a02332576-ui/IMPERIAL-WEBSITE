<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Imperial Barber Shop — Premium NYC Grooming</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Playfair+Display:ital,wght@0,700;0,900;1,700;1,900&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --orange: #E8630A;
    --orange-light: #FF7A20;
    --orange-glow: rgba(232,99,10,0.35);
    --black: #080808;
    --black-rich: #0D0D0D;
    --charcoal: #1A1A1A;
    --charcoal-mid: #222222;
    --grey-text: #A0A0A0;
    --white: #F5F2EE;
    --font-display: 'Bebas Neue', sans-serif;
    --font-luxury: 'Playfair Display', serif;
    --font-serif: 'Cormorant Garamond', serif;
    --font-body: 'DM Sans', sans-serif;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body { background: var(--black); color: var(--white); font-family: var(--font-body); font-weight: 300; overflow-x: hidden; }
 
  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 999;
    display: flex; align-items: center; justify-content: space-between;
    padding: 4px 40px;
    background: linear-gradient(to bottom, rgba(8,8,8,0.97) 0%, rgba(8,8,8,0.82) 100%);
    transition: background 0.4s, box-shadow 0.4s;
    height: 76px;
  }
  nav.scrolled { background: rgba(8,8,8,0.99); box-shadow: 0 1px 0 rgba(255,255,255,0.05); }
 
  .nav-logo-wrap {
    display: flex; align-items: center; gap: 10px;
    text-decoration: none; height: 100%;
  }
  .nav-logo-img {
    height: 66px; width: auto; display: block; object-fit: contain;
    mix-blend-mode: lighten;
    flex-shrink: 0;
  }
  .nav-logo-text {
    font-family: var(--font-luxury);
    font-weight: 900;
    font-size: 1.1rem;
    letter-spacing: 0.1em;
    color: var(--white);
    text-decoration: none;
    white-space: nowrap;
    line-height: 1.1;
  }
  .nav-logo-text span { color: var(--orange); display: block; font-weight: 700; font-size: 0.75em; letter-spacing: 0.18em; }
 
  .nav-links { display: flex; gap: 28px; list-style: none; align-items: center; }
  .nav-links a {
    color: rgba(245,242,238,0.62); text-decoration: none;
    font-size: 0.73rem; letter-spacing: 0.16em; text-transform: uppercase;
    transition: color 0.2s; white-space: nowrap;
  }
  .nav-links a:hover { color: var(--orange); }
  .nav-cta {
    background: var(--orange) !important; color: #fff !important;
    padding: 9px 20px; border-radius: 2px; font-weight: 500 !important;
  }
  .nav-cta:hover { background: var(--orange-light) !important; }
 
  .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; }
  .hamburger span { width: 24px; height: 2px; background: var(--white); display: block; }
 
  .mobile-nav {
    display: none; position: fixed; inset: 0; z-index: 1000;
    background: rgba(8,8,8,0.98); flex-direction: column;
    align-items: center; justify-content: center; gap: 32px;
  }
  .mobile-nav.active { display: flex; }
  .mobile-nav a { font-family: var(--font-display); font-size: 2.6rem; letter-spacing: 0.1em; color: var(--white); text-decoration: none; transition: color 0.2s; }
  .mobile-nav a:hover { color: var(--orange); }
  .mobile-nav-close { position: absolute; top: 22px; right: 26px; font-size: 1.8rem; color: var(--white); cursor: pointer; background: none; border: none; line-height: 1; }
 
  /* HERO */
  #hero {
    position: relative; height: 100vh; min-height: 720px;
    display: flex; align-items: center; overflow: hidden;
  }
  .hero-bg { position: absolute; inset: 0; background: var(--black); }
 
  .hero-photo {
    position: absolute;
    right: 0; top: 0; bottom: 0;
    width: 65%;
  }
  .hero-photo img {
    width: 100%; height: 100%;
    object-fit: cover;
    object-position: center top;
    display: block;
  }
  .hero-photo::after {
    content: ''; position: absolute; inset: 0;
    background:
      linear-gradient(to right, var(--black) 0%, rgba(8,8,8,0.55) 30%, rgba(8,8,8,0.05) 65%),
      linear-gradient(to top, rgba(8,8,8,0.5) 0%, transparent 30%);
  }
 
  .hero-grain {
    position: absolute; inset: 0; pointer-events: none; z-index: 2;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.025'/%3E%3C/svg%3E");
    opacity: 0.6;
  }
 
  .hero-content {
    position: relative; z-index: 3;
    padding: 0 0 0 64px;
    max-width: 540px;
    text-align: left;
    animation: heroFade 1.3s ease-out both;
  }
  @keyframes heroFade {
    from { opacity: 0; transform: translateY(22px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .hero-eyebrow {
    font-size: 0.68rem; letter-spacing: 0.34em; text-transform: uppercase;
    color: var(--orange); margin-bottom: 16px;
    animation: heroFade 1.3s 0.2s ease-out both;
  }
  .hero-title {
    font-family: var(--font-luxury);
    font-weight: 900;
    font-size: clamp(4rem, 9vw, 9rem);
    line-height: 0.88; letter-spacing: 0.01em; color: var(--white);
    margin-bottom: 20px;
    animation: heroFade 1.3s 0.35s ease-out both;
    text-shadow: 0 4px 40px rgba(0,0,0,0.6);
  }
  .hero-title em {
    font-style: italic;
    color: var(--orange);
    display: block;
  }
  .hero-subtitle {
    font-family: var(--font-serif); font-style: italic;
    font-size: clamp(1rem, 1.7vw, 1.3rem);
    color: rgba(245,242,238,0.7); letter-spacing: 0.04em;
    margin-bottom: 44px; max-width: 400px;
    animation: heroFade 1.3s 0.5s ease-out both;
    line-height: 1.6;
  }
  .hero-btns { display: flex; gap: 14px; flex-wrap: wrap; animation: heroFade 1.3s 0.65s ease-out both; }
 
  .scroll-hint {
    position: absolute; bottom: 32px; left: 64px; z-index: 3;
    display: flex; flex-direction: column; gap: 8px; opacity: 0.4;
    animation: scrollBounce 2.5s ease-in-out infinite;
  }
  .scroll-hint span { font-size: 0.6rem; letter-spacing: 0.26em; text-transform: uppercase; }
  .scroll-arrow { width: 1px; height: 42px; background: linear-gradient(to bottom, transparent, rgba(255,255,255,0.5)); }
  @keyframes scrollBounce { 0%,100% { transform: translateY(0); } 50% { transform: translateY(6px); } }
 
  /* BUTTONS */
  .btn-primary {
    background: var(--orange); color: #fff; padding: 15px 36px;
    border: none; border-radius: 2px; font-family: var(--font-body);
    font-size: 0.76rem; font-weight: 500; letter-spacing: 0.18em;
    text-transform: uppercase; cursor: pointer; text-decoration: none;
    display: inline-block; transition: background 0.25s, transform 0.2s, box-shadow 0.25s;
  }
  .btn-primary:hover { background: var(--orange-light); transform: translateY(-2px); box-shadow: 0 8px 28px var(--orange-glow); }
  .btn-ghost {
    background: transparent; color: var(--white); padding: 14px 32px;
    border: 1px solid rgba(245,242,238,0.28); border-radius: 2px;
    font-family: var(--font-body); font-size: 0.76rem; font-weight: 400;
    letter-spacing: 0.18em; text-transform: uppercase; cursor: pointer;
    text-decoration: none; display: inline-block;
    transition: border-color 0.25s, color 0.25s, transform 0.2s;
  }
  .btn-ghost:hover { border-color: var(--orange); color: var(--orange); transform: translateY(-2px); }
 
  .sticky-cta {
    display: none; position: fixed; bottom: 0; left: 0; right: 0; z-index: 998;
    background: var(--orange); color: #fff; text-align: center; padding: 15px;
    font-family: var(--font-body); font-size: 0.8rem; font-weight: 500;
    letter-spacing: 0.16em; text-transform: uppercase; text-decoration: none;
    box-shadow: 0 -4px 20px rgba(232,99,10,0.4);
  }
 
  /* TRUST STRIP */
  #trust { background: var(--charcoal); border-top: 1px solid rgba(255,255,255,0.04); border-bottom: 1px solid rgba(255,255,255,0.04); padding: 28px 48px; }
  .trust-grid { max-width: 1100px; margin: 0 auto; display: grid; grid-template-columns: repeat(4,1fr); }
  .trust-item { text-align: center; padding: 8px 24px; position: relative; }
  .trust-item:not(:last-child)::after { content:''; position:absolute; right:0; top:10%; height:80%; width:1px; background: rgba(255,255,255,0.08); }
  .trust-num { font-family: var(--font-display); font-size: 2.3rem; color: var(--orange); line-height: 1; }
  .trust-label { font-size: 0.67rem; letter-spacing: 0.22em; text-transform: uppercase; color: var(--grey-text); margin-top: 4px; }
 
  /* SECTION COMMONS */
  .section-label { font-size: 0.62rem; letter-spacing: 0.38em; text-transform: uppercase; color: var(--orange); margin-bottom: 13px; display: block; }
  .section-title { font-family: var(--font-luxury); font-weight: 900; font-size: clamp(2.5rem, 4.8vw, 4.6rem); line-height: 0.95; letter-spacing: 0.01em; color: var(--white); margin-bottom: 24px; }
  .section-body { font-family: var(--font-serif); font-size: clamp(0.98rem, 1.3vw, 1.1rem); line-height: 1.85; color: rgba(245,242,238,0.62); max-width: 520px; }
 
  /* ABOUT */
  #about { padding: 120px 48px; background: var(--black-rich); }
  .about-inner { max-width: 1200px; margin: 0 auto; display: grid; grid-template-columns: 1fr 1fr; gap: 88px; align-items: center; }
  .about-pull { font-family: var(--font-luxury); font-style: italic; font-size: clamp(1.4rem, 2.3vw, 1.95rem); line-height: 1.45; color: var(--white); margin-bottom: 24px; border-left: 2px solid var(--orange); padding-left: 22px; }
  .about-img { position: relative; aspect-ratio: 4/5; overflow: hidden; border-radius: 1px; }
  .about-img img { width:100%; height:100%; object-fit:cover; transition:transform 0.8s ease; filter:grayscale(12%) contrast(1.05); }
  .about-img:hover img { transform:scale(1.04); }
  .about-img::after { content:''; position:absolute; inset:0; background:linear-gradient(to top,rgba(8,8,8,0.5) 0%,transparent 50%); pointer-events:none; }
  .about-badge { position:absolute; top:24px; right:24px; background:var(--orange); color:#fff; font-family:var(--font-display); font-size:0.9rem; letter-spacing:0.1em; padding:11px 15px; text-align:center; line-height:1.2; z-index:2; }
  .about-badge small { display:block; font-family:var(--font-body); font-size:0.57rem; letter-spacing:0.2em; text-transform:uppercase; font-weight:300; }
 
  /* SERVICES */
  #services { padding: 120px 48px; background: var(--black); }
  .services-header { max-width:1200px; margin:0 auto 56px; display:flex; align-items:flex-end; justify-content:space-between; gap:32px; }
  .services-grid { max-width:1200px; margin:0 auto; display:grid; grid-template-columns:repeat(4,1fr); gap:14px; }
  .service-card {
    background: rgba(255,255,255,0.03); border:1px solid rgba(255,255,255,0.07);
    backdrop-filter:blur(12px); -webkit-backdrop-filter:blur(12px);
    padding:32px 24px; border-radius:2px; cursor:default; position:relative; overflow:hidden;
    transition: transform 0.35s cubic-bezier(0.23,1,0.32,1), box-shadow 0.35s, border-color 0.35s, background 0.35s;
  }
  .service-card::before { content:''; position:absolute; inset:0; background:radial-gradient(ellipse at 50% 120%,var(--orange-glow) 0%,transparent 70%); opacity:0; transition:opacity 0.35s; }
  .service-card:hover { transform:translateY(-8px); box-shadow:0 24px 56px rgba(232,99,10,0.18),0 0 0 1px rgba(232,99,10,0.25); border-color:rgba(232,99,10,0.3); background:rgba(232,99,10,0.04); }
  .service-card:hover::before { opacity:1; }
  .service-name { font-family:var(--font-luxury); font-weight:700; font-size:1.2rem; letter-spacing:0.02em; color:var(--white); margin-bottom:8px; }
  .service-benefit { font-size:0.75rem; color:var(--grey-text); letter-spacing:0.05em; line-height:1.6; margin-bottom:24px; min-height:36px; }
  .service-meta { display:flex; align-items:center; justify-content:space-between; padding-top:16px; border-top:1px solid rgba(255,255,255,0.07); }
  .service-price { font-family:var(--font-display); font-size:1.7rem; color:var(--orange); letter-spacing:0.02em; line-height:1; }
  .service-duration { font-size:0.67rem; letter-spacing:0.18em; text-transform:uppercase; color:var(--grey-text); }
 
  /* GALLERY */
  #gallery { padding: 120px 48px; background: var(--black-rich); }
  .gallery-header { max-width:1200px; margin:0 auto 56px; }
  .gallery-grid {
    max-width: 1200px; margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: 290px 290px;
    gap: 12px;
  }
  .g-tall { grid-row: span 2; }
 
  .gallery-item {
    position: relative; overflow: hidden; border-radius: 2px; cursor: pointer;
    background: var(--charcoal-mid);
  }
  .gallery-item img {
    position: absolute; inset: 0;
    width: 100%; height: 100%;
    object-fit: cover; object-position: center top;
    filter: grayscale(12%) contrast(1.07);
    transition: transform 0.6s cubic-bezier(0.23,1,0.32,1), filter 0.4s;
    display: block;
  }
  .gallery-item:hover img { transform: scale(1.07); filter: grayscale(0%) contrast(1.05); }
  .gallery-overlay { position:absolute; inset:0; background:linear-gradient(to top,rgba(8,8,8,0.75) 0%,transparent 55%); opacity:0; transition:opacity 0.4s; display:flex; align-items:flex-end; padding:20px; z-index:2; }
  .gallery-item:hover .gallery-overlay { opacity:1; }
  .gallery-tag { font-size:0.67rem; letter-spacing:0.22em; text-transform:uppercase; color:var(--orange); }
 
  .lightbox { display:none; position:fixed; inset:0; z-index:2000; background:rgba(8,8,8,0.96); align-items:center; justify-content:center; }
  .lightbox.active { display:flex; }
  .lightbox img { max-width:90vw; max-height:90vh; object-fit:contain; border-radius:2px; }
  .lightbox-close { position:absolute; top:24px; right:32px; font-size:1.8rem; color:var(--white); cursor:pointer; opacity:0.7; transition:opacity 0.2s; background:none; border:none; line-height:1; }
  .lightbox-close:hover { opacity:1; color:var(--orange); }
 
  /* LOCATIONS */
  #locations { padding: 120px 48px; background: var(--black); }
  .locations-header { max-width:1200px; margin:0 auto 56px; }
  .locations-grid { max-width:1200px; margin:0 auto; display:grid; grid-template-columns:repeat(3,1fr); gap:22px; }
  .location-card { background:var(--charcoal); border:1px solid rgba(255,255,255,0.06); border-radius:2px; overflow:hidden; }
  .location-map { width:100%; height:190px; background:var(--charcoal-mid); border:none; display:block; }
  .location-body { padding:24px; }
  .location-name { font-family:var(--font-luxury); font-weight:700; font-size:1.3rem; letter-spacing:0.02em; color:var(--white); margin-bottom:4px; }
  .location-addr { font-size:0.78rem; color:var(--grey-text); line-height:1.6; margin-bottom:4px; }
  .location-phone { font-size:0.86rem; color:var(--orange); font-weight:500; text-decoration:none; letter-spacing:0.06em; display:block; margin-bottom:16px; }
  .location-phone:hover { color:var(--orange-light); }
  .location-btns { display:flex; gap:9px; flex-wrap:wrap; }
  .loc-btn-call { flex:1; min-width:88px; background:var(--orange); color:#fff; border:none; padding:11px 14px; font-family:var(--font-body); font-size:0.68rem; letter-spacing:0.16em; text-transform:uppercase; cursor:pointer; border-radius:2px; text-align:center; text-decoration:none; transition:background 0.2s; }
  .loc-btn-call:hover { background:var(--orange-light); }
  .loc-btn-dir { flex:1; min-width:88px; background:transparent; color:var(--white); border:1px solid rgba(255,255,255,0.14); padding:10px 14px; font-family:var(--font-body); font-size:0.68rem; letter-spacing:0.16em; text-transform:uppercase; cursor:pointer; border-radius:2px; text-align:center; text-decoration:none; transition:border-color 0.2s,color 0.2s; }
  .loc-btn-dir:hover { border-color:var(--orange); color:var(--orange); }
 
  /* CTA */
  #cta { padding:130px 48px; background:var(--charcoal); text-align:center; position:relative; overflow:hidden; }
  #cta::before { content:'IMPERIAL'; position:absolute; font-family:var(--font-display); font-size:22vw; color:rgba(255,255,255,0.015); top:50%; left:50%; transform:translate(-50%,-50%); letter-spacing:0.08em; white-space:nowrap; pointer-events:none; user-select:none; }
  .cta-label { margin:0 auto 16px; }
  .cta-title { font-family:var(--font-luxury); font-weight:900; font-size:clamp(2.7rem,6vw,6rem); line-height:0.95; letter-spacing:0.01em; color:var(--white); margin-bottom:36px; position:relative; }
  .cta-title em { font-style:italic; font-size:0.85em; color:rgba(245,242,238,0.65); display:block; }
  .cta-btns { display:flex; gap:14px; justify-content:center; flex-wrap:wrap; position:relative; }
 
  /* CONTACT */
  #contact { padding: 120px 48px; background: var(--black-rich); }
  .contact-inner { max-width:1100px; margin:0 auto; display:grid; grid-template-columns:1fr 1fr; gap:88px; align-items:start; }
  .hours-title { font-family:var(--font-display); font-size:0.9rem; letter-spacing:0.18em; text-transform:uppercase; color:var(--orange); margin-bottom:12px; }
  .hours-row { display:flex; justify-content:space-between; padding:9px 0; border-bottom:1px solid rgba(255,255,255,0.06); font-size:0.78rem; color:var(--grey-text); letter-spacing:0.03em; }
  .hours-row span:first-child { color:var(--white); }
  .form-group { margin-bottom:16px; }
  .form-group input,.form-group textarea { width:100%; background:rgba(255,255,255,0.04); border:1px solid rgba(255,255,255,0.1); border-radius:2px; padding:14px 17px; color:var(--white); font-family:var(--font-body); font-size:0.86rem; outline:none; transition:border-color 0.25s,background 0.25s; letter-spacing:0.03em; }
  .form-group input::placeholder,.form-group textarea::placeholder { color:var(--grey-text); }
  .form-group input:focus,.form-group textarea:focus { border-color:var(--orange); background:rgba(232,99,10,0.04); }
  .form-group textarea { resize:none; height:118px; }
  .form-submit { width:100%; background:var(--orange); color:#fff; border:none; padding:15px; font-family:var(--font-body); font-size:0.78rem; font-weight:500; letter-spacing:0.2em; text-transform:uppercase; cursor:pointer; border-radius:2px; transition:background 0.25s,box-shadow 0.25s; }
  .form-submit:hover { background:var(--orange-light); box-shadow:0 8px 28px var(--orange-glow); }
  .form-msg { display:none; margin-top:11px; font-size:0.78rem; color:#5dbe7a; letter-spacing:0.05em; line-height:1.6; }
 
  /* FOOTER */
  footer { background:#060606; border-top:1px solid rgba(255,255,255,0.04); padding:68px 48px 38px; }
  .footer-inner { max-width:1200px; margin:0 auto; display:grid; grid-template-columns:1.6fr 1fr 1fr 1fr; gap:48px; margin-bottom:48px; }
  .footer-brand-logo-wrap {
    display: flex; align-items: center; gap: 12px; margin-bottom: 18px;
  }
  .footer-logo-img {
    height: 78px; width: auto; display: block; object-fit: contain;
    mix-blend-mode: lighten;
    flex-shrink: 0;
  }
  .footer-logo-name {
    font-family: var(--font-luxury); font-weight: 900;
    font-size: 1.15rem; letter-spacing: 0.08em;
    color: var(--white); line-height: 1.2;
  }
  .footer-logo-name span { color: var(--orange); display: block; font-size: 0.75em; font-weight: 700; letter-spacing: 0.18em; }
  .footer-brand p { font-size:0.78rem; color:var(--grey-text); line-height:1.8; letter-spacing:0.03em; max-width:228px; }
  .footer-col-title { font-size:0.61rem; letter-spacing:0.3em; text-transform:uppercase; color:var(--orange); margin-bottom:16px; }
  .footer-col ul { list-style:none; }
  .footer-col ul li { margin-bottom:8px; font-size:0.78rem; color:var(--grey-text); line-height:1.5; letter-spacing:0.03em; }
  .footer-col ul li a { color:var(--grey-text); text-decoration:none; transition:color 0.2s; }
  .footer-col ul li a:hover { color:var(--orange); }
  .footer-bottom { max-width:1200px; margin:0 auto; padding-top:24px; border-top:1px solid rgba(255,255,255,0.05); display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:10px; }
  .footer-copy { font-size:0.68rem; color:rgba(255,255,255,0.2); letter-spacing:0.08em; }
  .footer-tagline { font-family:var(--font-serif); font-style:italic; font-size:0.8rem; color:rgba(245,242,238,0.18); }
 
  /* REVEAL */
  .reveal { opacity:0; transform:translateY(26px); transition:opacity 0.8s cubic-bezier(0.23,1,0.32,1),transform 0.8s cubic-bezier(0.23,1,0.32,1); }
  .reveal.visible { opacity:1; transform:none; }
  .reveal-delay-1 { transition-delay:0.1s; }
  .reveal-delay-2 { transition-delay:0.2s; }
  .reveal-delay-3 { transition-delay:0.3s; }
 
  /* RESPONSIVE */
  @media(max-width:1100px){
    .services-grid { grid-template-columns:repeat(2,1fr); }
    .footer-inner { grid-template-columns:1fr 1fr; }
  }
  @media(max-width:900px){
    nav { padding:12px 22px; }
    .nav-links { display:none; }
    .hamburger { display:flex; }
    .about-inner,.contact-inner { grid-template-columns:1fr; gap:44px; }
    .about-img { max-height:370px; }
    .locations-grid { grid-template-columns:1fr; }
    .trust-grid { grid-template-columns:repeat(2,1fr); }
    .trust-item:nth-child(2)::after { display:none; }
    .gallery-grid { grid-template-columns:1fr 1fr; grid-template-rows:260px 260px; }
    .g-tall { grid-row:span 1; }
    .hero-content { padding:0 0 0 36px; }
    .hero-photo { width:62%; }
  }
  @media(max-width:640px){
    nav { padding:10px 16px; height:64px; }
    .nav-logo-img { height:50px; }
    .hero-content { padding:0 20px; max-width:100%; }
    .hero-photo { width:100%; }
    .hero-photo img { object-position:55% top; }
    .hero-photo::after { background:linear-gradient(to right, rgba(8,8,8,0.85) 0%, rgba(8,8,8,0.55) 100%), linear-gradient(to top,rgba(8,8,8,0.7) 0%,transparent 40%); }
    #about,#services,#gallery,#locations,#cta,#contact { padding:80px 20px; }
    #trust { padding:26px 16px; }
    .services-header { flex-direction:column; align-items:flex-start; }
    .services-grid { grid-template-columns:1fr; }
    .gallery-grid { grid-template-columns:1fr; grid-template-rows:auto; }
    .gallery-item { height:240px !important; }
    .g-tall { grid-row:span 1; }
    footer { padding:52px 20px 80px; }
    .footer-inner { grid-template-columns:1fr; gap:30px; }
    .footer-logo-img { height:64px; }
    .footer-bottom { flex-direction:column; align-items:flex-start; }
    .sticky-cta { display:block; }
    .scroll-hint { left:20px; }
  }
</style>
</head>
<body>
 
<!-- NAVBAR -->
<nav id="navbar">
  <a href="#hero" class="nav-logo-wrap">
    <img id="navLogoImg" src="" alt="Imperial Barber Shop Logo" class="nav-logo-img">
    <div class="nav-logo-text">IMPERIAL <span>BARBER SHOP</span></div>
  </a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#gallery">Gallery</a></li>
    <li><a href="#locations">Locations</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="tel:+12125550100" class="nav-cta">Book Now</a></li>
  </ul>
  <div class="hamburger" onclick="toggleNav()">
    <span></span><span></span><span></span>
  </div>
</nav>
 
<!-- Mobile Nav -->
<div class="mobile-nav" id="mobileNav">
  <button class="mobile-nav-close" onclick="toggleNav()">✕</button>
  <a href="#about" onclick="toggleNav()">About</a>
  <a href="#services" onclick="toggleNav()">Services</a>
  <a href="#gallery" onclick="toggleNav()">Gallery</a>
  <a href="#locations" onclick="toggleNav()">Locations</a>
  <a href="#contact" onclick="toggleNav()">Contact</a>
  <a href="tel:+12125550100" style="color:var(--orange)">Call Now</a>
</div>
 
<!-- HERO -->
<section id="hero">
  <div class="hero-bg"></div>
  <div class="hero-photo">
    <img src="https://images.unsplash.com/photo-1503951914875-452162b0f3f1?w=1400&q=90" alt="Professional barber at work" loading="eager">
  </div>
  <div class="hero-grain"></div>
  <div class="hero-content">
    <p class="hero-eyebrow">NYC's Premier Barber Experience</p>
    <h1 class="hero-title">Sharp<br><em>Confidence</em></h1>
    <p class="hero-subtitle">Premium grooming. Precision cuts. New York City's finest barbers.</p>
    <div class="hero-btns">
      <a href="#contact" class="btn-primary">Book Appointment</a>
      <a href="tel:+12125550100" class="btn-ghost">Call Now</a>
    </div>
  </div>
  <div class="scroll-hint">
    <span>Scroll</span>
    <div class="scroll-arrow"></div>
  </div>
</section>
 
<!-- TRUST STRIP -->
<div id="trust">
  <div class="trust-grid">
    <div class="trust-item reveal"><div class="trust-num">10+</div><div class="trust-label">Years Experience</div></div>
    <div class="trust-item reveal reveal-delay-1"><div class="trust-num">10K+</div><div class="trust-label">Haircuts Delivered</div></div>
    <div class="trust-item reveal reveal-delay-2"><div class="trust-num">3</div><div class="trust-label">NYC Locations</div></div>
    <div class="trust-item reveal reveal-delay-3"><div class="trust-num">7</div><div class="trust-label">Days a Week</div></div>
  </div>
</div>
 
<!-- ABOUT -->
<section id="about">
  <div class="about-inner">
    <div class="about-text">
      <span class="section-label reveal">Our Story</span>
      <h2 class="section-title reveal">Grooming<br>Reimagined</h2>
      <p class="about-pull reveal">Where precision meets identity — and every visit is a transformation.</p>
      <p class="section-body reveal">Imperial Barber Shop isn't just where you get a haircut. It's where New York comes to feel its sharpest. Since our founding, we've built a reputation as the city's most trusted grooming destination — where master barbers, premium craft, and uncompromising detail converge.</p>
      <p class="section-body reveal" style="margin-top:14px;">We believe grooming is an act of confidence. Walk in knowing what you want. Leave knowing who you are.</p>
    </div>
    <div class="about-img reveal">
      <img src="https://images.unsplash.com/photo-1585747860715-2ba37e788b70?w=900&q=80" alt="Imperial Barber Shop interior">
      <div class="about-badge">NYC<small>Est. 2014</small></div>
    </div>
  </div>
</section>
 
<!-- SERVICES -->
<section id="services">
  <div class="services-header">
    <div>
      <span class="section-label reveal">What We Offer</span>
      <h2 class="section-title reveal">Our Services</h2>
    </div>
    <p class="section-body reveal" style="text-align:right;max-width:250px;">Every cut delivered by a master barber with a commitment to craft.</p>
  </div>
  <div class="services-grid">
    <div class="service-card reveal"><div class="service-name">Men's Haircut</div><div class="service-benefit">Classic cut tailored to your face shape and personal style.</div><div class="service-meta"><div class="service-price">$25</div><div class="service-duration">25 min</div></div></div>
    <div class="service-card reveal reveal-delay-1"><div class="service-name">Long Layered Cut</div><div class="service-benefit">Precision layering for volume, movement, and flow.</div><div class="service-meta"><div class="service-price">$30</div><div class="service-duration">30 min</div></div></div>
    <div class="service-card reveal reveal-delay-2"><div class="service-name">Buzzcut</div><div class="service-benefit">Clean, uniform, effortlessly sharp. Zero compromise.</div><div class="service-meta"><div class="service-price">$22</div><div class="service-duration">20 min</div></div></div>
    <div class="service-card reveal reveal-delay-3"><div class="service-name">Shape Up / Edge Up</div><div class="service-benefit">Crisp lines at hairline, temple, and neckline.</div><div class="service-meta"><div class="service-price">$12</div><div class="service-duration">10 min</div></div></div>
    <div class="service-card reveal"><div class="service-name">Kids Haircut</div><div class="service-benefit">Patient, gentle, and precise — every time.</div><div class="service-meta"><div class="service-price">$25</div><div class="service-duration">30 min</div></div></div>
    <div class="service-card reveal reveal-delay-1"><div class="service-name">Beard Trim</div><div class="service-benefit">Shape, define, and refine your beard to perfection.</div><div class="service-meta"><div class="service-price">$15</div><div class="service-duration">15 min</div></div></div>
    <div class="service-card reveal reveal-delay-2"><div class="service-name">Hot Towel Shave</div><div class="service-benefit">Old-world ritual. New-world smooth. Pure luxury.</div><div class="service-meta"><div class="service-price">$25</div><div class="service-duration">30 min</div></div></div>
    <div class="service-card reveal reveal-delay-3"><div class="service-name">Fades & More</div><div class="service-benefit">Skin fades, tapers, and custom blends — your vision.</div><div class="service-meta"><div class="service-price">Custom</div><div class="service-duration">Varies</div></div></div>
  </div>
</section>
 
<!-- GALLERY -->
<section id="gallery">
  <div class="gallery-header">
    <span class="section-label reveal">The Work</span>
    <h2 class="section-title reveal">Transformations</h2>
  </div>
  <div class="gallery-grid">
    <div class="gallery-item g-tall reveal" onclick="openLightbox('https://images.unsplash.com/photo-1621605815971-fbc98d665033?w=1200&q=85')">
      <img src="https://images.unsplash.com/photo-1621605815971-fbc98d665033?w=700&q=80" alt="Barber precision cut">
      <div class="gallery-overlay"><span class="gallery-tag">Skin Fade</span></div>
    </div>
    <div class="gallery-item reveal reveal-delay-1" onclick="openLightbox('https://images.unsplash.com/photo-1622286342621-4bd786c2447c?w=1200&q=85')">
      <img src="https://images.unsplash.com/photo-1622286342621-4bd786c2447c?w=700&q=80" alt="Beard grooming">
      <div class="gallery-overlay"><span class="gallery-tag">Beard Sculpt</span></div>
    </div>
    <div class="gallery-item g-tall reveal reveal-delay-2" onclick="openLightbox('https://images.unsplash.com/photo-1585747860715-2ba37e788b70?w=1200&q=85')">
      <img src="https://images.unsplash.com/photo-1585747860715-2ba37e788b70?w=700&q=80" alt="Premium barbershop">
      <div class="gallery-overlay"><span class="gallery-tag">Hot Towel Shave</span></div>
    </div>
    <div class="gallery-item reveal reveal-delay-1" onclick="openLightbox('https://images.unsplash.com/photo-1599351431202-1e0f0137899a?w=1200&q=85')">
      <img src="https://images.unsplash.com/photo-1599351431202-1e0f0137899a?w=700&q=80" alt="Classic cut">
      <div class="gallery-overlay"><span class="gallery-tag">Classic Cut</span></div>
    </div>
  </div>
  <!-- Second row -->
  <div style="max-width:1200px;margin:12px auto 0;display:grid;grid-template-columns:repeat(3,1fr);gap:12px;">
    <div class="gallery-item reveal" style="height:240px;" onclick="openLightbox('https://images.unsplash.com/photo-1503951914875-452162b0f3f1?w=1200&q=85')">
      <img src="https://images.unsplash.com/photo-1503951914875-452162b0f3f1?w=700&q=80" alt="Barber precision">
      <div class="gallery-overlay"><span class="gallery-tag">Edge Up</span></div>
    </div>
    <div class="gallery-item reveal reveal-delay-1" style="height:240px;" onclick="openLightbox('https://images.unsplash.com/photo-1605497788044-5a32c7078486?w=1200&q=85')">
      <img src="https://images.unsplash.com/photo-1605497788044-5a32c7078486?w=700&q=80" alt="Taper fade">
      <div class="gallery-overlay"><span class="gallery-tag">Taper Fade</span></div>
    </div>
    <div class="gallery-item reveal reveal-delay-2" style="height:240px;" onclick="openLightbox('https://images.unsplash.com/photo-1541533848490-bc8115cd6522?w=1200&q=85')">
      <img src="https://images.unsplash.com/photo-1541533848490-bc8115cd6522?w=700&q=80" alt="Barber shop interior">
      <div class="gallery-overlay"><span class="gallery-tag">Precision Cut</span></div>
    </div>
  </div>
</section>
 
<!-- Lightbox -->
<div class="lightbox" id="lightbox" onclick="closeLightbox()">
  <button class="lightbox-close" onclick="closeLightbox()">✕</button>
  <img id="lightboxImg" src="" alt="">
</div>
 
<!-- LOCATIONS -->
<section id="locations">
  <div class="locations-header">
    <span class="section-label reveal">Find Us</span>
    <h2 class="section-title reveal">Our Locations</h2>
  </div>
  <div class="locations-grid">
    <div class="location-card reveal">
      <iframe class="location-map" src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3022.617!2d-73.9857!3d40.7484!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zNDDCsDQ0JzU0LjIiTiA3M8KwNTknMDguNSJX!5e0!3m2!1sen!2sus!4v1" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
      <div class="location-body">
        <div class="location-name">Midtown</div>
        <div class="location-addr">44 W 44th St, New York, NY 10036</div>
        <a class="location-phone" href="tel:+12125550100">(212) 555-0100</a>
        <div class="location-btns">
          <a href="tel:+12125550100" class="loc-btn-call">📞 Call Now</a>
          <a href="https://maps.google.com/?q=44+W+44th+St+New+York+NY" target="_blank" class="loc-btn-dir">Directions</a>
        </div>
      </div>
    </div>
    <div class="location-card reveal reveal-delay-1">
      <iframe class="location-map" src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3022.617!2d-73.9957!3d40.7284!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zNDDCsDQzJzQyLjIiTiA3M8KwNTknNDQuNSJX!5e0!3m2!1sen!2sus!4v1" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
      <div class="location-body">
        <div class="location-name">Chelsea</div>
        <div class="location-addr">228 8th Ave, New York, NY 10011</div>
        <a class="location-phone" href="tel:+12125550200">(212) 555-0200</a>
        <div class="location-btns">
          <a href="tel:+12125550200" class="loc-btn-call">📞 Call Now</a>
          <a href="https://maps.google.com/?q=228+8th+Ave+New+York+NY" target="_blank" class="loc-btn-dir">Directions</a>
        </div>
      </div>
    </div>
    <div class="location-card reveal reveal-delay-2">
      <iframe class="location-map" src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3022.617!2d-73.9457!3d40.7684!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zNDDCsDQ2JzA2LjIiTiA3M8KwNTYnNDQuNSJX!5e0!3m2!1sen!2sus!4v1" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
      <div class="location-body">
        <div class="location-name">Upper East Side</div>
        <div class="location-addr">1564 2nd Ave, New York, NY 10028</div>
        <a class="location-phone" href="tel:+12125550300">(212) 555-0300</a>
        <div class="location-btns">
          <a href="tel:+12125550300" class="loc-btn-call">📞 Call Now</a>
          <a href="https://maps.google.com/?q=1564+2nd+Ave+New+York+NY" target="_blank" class="loc-btn-dir">Directions</a>
        </div>
      </div>
    </div>
  </div>
</section>
 
<!-- CTA -->
<section id="cta">
  <span class="section-label cta-label reveal">Ready?</span>
  <h2 class="cta-title reveal">Walk in different.<br><em>Leave transformed.</em></h2>
  <div class="cta-btns reveal">
    <a href="tel:+12125550100" class="btn-primary">Call Now</a>
    <a href="#contact" class="btn-ghost">Book Appointment</a>
  </div>
</section>
 
<!-- CONTACT -->
<section id="contact">
  <div class="contact-inner">
    <div class="contact-form">
      <span class="section-label reveal">Get In Touch</span>
      <h2 class="section-title reveal" style="font-size:clamp(1.9rem,3.8vw,3.2rem);">Book or<br>Inquire</h2>
      <div class="reveal">
        <div class="form-group"><input type="text" id="fname" placeholder="Your Name" autocomplete="name"></div>
        <div class="form-group"><input type="email" id="femail" placeholder="Email Address" autocomplete="email"></div>
        <div class="form-group"><input type="tel" id="fphone" placeholder="Phone Number" autocomplete="tel"></div>
        <div class="form-group"><textarea id="fmessage" placeholder="Your message or preferred appointment time..."></textarea></div>
        <button class="form-submit" onclick="submitForm()">Send Message →</button>
        <div class="form-msg" id="formMsg">✓ Your email app will open with the message pre-filled — just hit Send to reach us at Imperialbarbershop44@gmail.com</div>
      </div>
    </div>
    <div class="contact-info">
      <span class="section-label reveal">Hours & Info</span>
      <p class="section-body reveal" style="margin-bottom:10px;">Walk-ins welcome. Appointments recommended for peak hours. Open seven days a week across all three NYC locations.</p>
      <div style="margin-top:30px;" class="reveal">
        <div class="hours-title">Working Hours</div>
        <div class="hours-row"><span>Monday – Friday</span><span>8:30 AM – 7:30 PM</span></div>
        <div class="hours-row"><span>Saturday</span><span>9:00 AM – 6:00 PM</span></div>
        <div class="hours-row"><span>Sunday</span><span>10:00 AM – 5:00 PM</span></div>
      </div>
      <div style="margin-top:28px;" class="reveal">
        <div class="hours-title">Direct Contact</div>
        <div class="hours-row"><span>Midtown</span><span><a href="tel:+12125550100" style="color:var(--orange);text-decoration:none;">(212) 555-0100</a></span></div>
        <div class="hours-row"><span>Chelsea</span><span><a href="tel:+12125550200" style="color:var(--orange);text-decoration:none;">(212) 555-0200</a></span></div>
        <div class="hours-row"><span>Upper East Side</span><span><a href="tel:+12125550300" style="color:var(--orange);text-decoration:none;">(212) 555-0300</a></span></div>
        <div class="hours-row"><span>Email</span><span style="font-size:0.71rem;color:var(--grey-text);">Imperialbarbershop44@gmail.com</span></div>
      </div>
    </div>
  </div>
</section>
 
<!-- FOOTER -->
<footer>
  <div class="footer-inner">
    <div class="footer-brand">
      <div class="footer-brand-logo-wrap">
        <img id="footerLogoImg" src="" alt="Imperial Barber Shop" class="footer-logo-img">
        <div class="footer-logo-name">IMPERIAL <span>BARBER SHOP</span></div>
      </div>
      <p>Premium NYC grooming experience.<br>Three locations. One standard of excellence.</p>
    </div>
    <div class="footer-col">
      <div class="footer-col-title">Services</div>
      <ul>
        <li><a href="#services">Men's Haircut — $25</a></li>
        <li><a href="#services">Buzzcut — $22</a></li>
        <li><a href="#services">Shape Up — $12</a></li>
        <li><a href="#services">Beard Trim — $15</a></li>
        <li><a href="#services">Hot Towel Shave — $25</a></li>
        <li><a href="#services">Kids Haircut — $25</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <div class="footer-col-title">Locations</div>
      <ul>
        <li>44 W 44th St, Midtown</li>
        <li>228 8th Ave, Chelsea</li>
        <li>1564 2nd Ave, Upper East Side</li>
      </ul>
      <div class="footer-col-title" style="margin-top:20px;">Hours</div>
      <ul>
        <li>Mon–Fri: 8:30 AM – 7:30 PM</li>
        <li>Sat: 9:00 AM – 6:00 PM</li>
        <li>Sun: 10:00 AM – 5:00 PM</li>
      </ul>
    </div>
    <div class="footer-col">
      <div class="footer-col-title">Call Us</div>
      <ul>
        <li><a href="tel:+12125550100">(212) 555-0100</a></li>
        <li><a href="tel:+12125550200">(212) 555-0200</a></li>
        <li><a href="tel:+12125550300">(212) 555-0300</a></li>
      </ul>
      <div style="margin-top:24px;">
        <a href="#contact" class="btn-primary" style="padding:12px 20px;font-size:0.71rem;">Book Now</a>
      </div>
    </div>
  </div>
  <div class="footer-bottom">
    <span class="footer-copy">© 2025 Imperial Barber Shop NYC. All rights reserved.</span>
    <span class="footer-tagline">Precision. Identity. Confidence.</span>
  </div>
</footer>
 
<a href="tel:+12125550100" class="sticky-cta">📞 Call to Book — Available Now</a>
 
<script>
  const LOGO_SRC = 'data:image/png;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/4gHYSUNDX1BST0ZJTEUAAQEAAAHIAAAAAAQwAABtbnRyUkdCIFhZWiAH4AABAAEAAAAAAABhY3NwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAQAA9tYAAQAAAADTLQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAlkZXNjAAAA8AAAACRyWFlaAAABFAAAABRnWFlaAAABKAAAABRiWFlaAAABPAAAABR3dHB0AAABUAAAABRyVFJDAAABZAAAAChnVFJDAAABZAAAAChiVFJDAAABZAAAAChjcHJ0AAABjAAAADxtbHVjAAAAAAAAAAEAAAAMZW5VUwAAAAgAAAAcAHMAUgBHAEJYWVogAAAAAAAAb6IAADj1AAADkFhZWiAAAAAAAABimQAAt4UAABjaWFlaIAAAAAAAACSgAAAPhAAAts9YWVogAAAAAAAA9tYAAQAAAADTLXBhcmEAAAAAAAQAAAACZmYAAPKnAAANWQAAE9AAAApbAAAAAAAAAABtbHVjAAAAAAAAAAEAAAAMZW5VUwAAACAAAAAcAEcAbwBvAGcAbABlACAASQBuAGMALgAgADIAMAAxADb/2wBDAAUDBAQEAwUEBAQFBQUGBwwIBwcHBw8LCwkMEQ8SEhEPERETFhwXExQaFRERGCEYGh0dHx8fExciJCIeJBweHx7/2wBDAQUFBQcGBw4ICA4eFBEUHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh7/wAARCAGiAWMDASIAAhEBAxEB/8QAHQABAAICAwEBAAAAAAAAAAAAAAYHBQgBAgQDCf/EAFMQAAEDAwIDBQQFCAUICAYDAAECAwQABREGEgchMRMiQVFhFDJxgQgjQpGhFTNSYoKxwdEWJHKS0kNjc5SissLhFyU0RlOT8PEYNVRWg7MmRIT/xAAaAQEAAgMBAAAAAAAAAAAAAAAAAQQCAwUG/8QALREAAgICAQQBBAEEAgMAAAAAAAECAwQREgUhMUFRExQVIlIyQmGhIzMGJIH/2gAMAwEAAhEDEQA/ANMqUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClK+rDLjzqWmm1OLUcJSkEk/AUB8qVnGdJame3luwXMhtO5ZMVYAHnzFdEaavS1BKYDqlH7II3fdnNRtEqLZhz0rivXcbfNtz/AGE2K/Gc/QdQUn8a8uM1KYaOKUpQgUpSgFKUoBSlKAUpSgFKUoBSlKAUpSgFKUoBSlKAUpSgFKUoBSlKAUpSgFKUoBSlKAUpSgFK5HWp7wsjxY7F1vMq2xrgthKI8VqQkLb7VZJyUnqdqTjyJFRKSitsyhBzlxRAa+8OJJlu9lFjvPr/AEWkFR+4VeF4kWi4yzfbLw3szaCkFTaWluoac8SEBYTtzzAUnx55rxQbjq24Mdnbbg3DSAQlqOG44AzzASkjl6VWeXBF+PTrH5K/jcP9UuMJkP24QGVN9ohc15EcKHoFkE/dWUiaGt0UpVd78iQT/wD17W0p5R8wVqASk/AKqWr0fqJ5pT8yStJI3LU5Gecx8SlBz99fSBp6EHwJ+so9uI+0YD5H+4K0Tzk/BZr6al/UfO16dmQwl6w8OC4pGQJE+IqYo8gDlDg7L19zl4V9LlB18iK2iZbtSR4TIwhlplTLLY8koRhKfkKktu0/IODYuLdqcc+wy686wfxFe2TI4w6YZTLcek3GGP8ALxnhJaI8zjmBVaeVOXguQw64+EVZJeLxDM2ZccZ5odcWrB+BNZeDplq5IQi0XZp59Se5GlEIcUryBPI/I59KsGJriw6jjKb1bZLXOfCtiyQWZAHnuAH8fjXwvfC6FLj+2aRmSo76hlmFMwO1Hk24O6T6HBrX9eT8m9UQXorl8Xe0BdrusIhIBSuJNY7VrmCCUhXNCsE4UnCh4Go5e9Lx5SVSLE0ttxCSt6EpW5QAGSps9VDH2TzHrVkWO+svOL01ryLIfjA9l2yk4kQ1dAtJPMgHqDWJ1lYJ2k7y0yJPasOJD9vntnaHE+CgfAjNWacpxaTKuThxmtpdymTSpxrq2pmwzqWO0hp3tA1cWUISlKHCO66kD7K8HIxyUD5ioMPGunBqS2jgWVuuWmcUpSsjWKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKt7Ta06d0ppppQ7Rbr6rvKQUglIKghCPUFtsKwf/ENVEgZUBV56kYjJv7cFTmGETHYYeUBuDbe1pGceiRVfJlxgXsCvnYe2NbDbNVvQoVxchtuEO2qaCQhTbg3NbiPApOM+BBrLq2e2rRrHS6ZDTTnZynUt7XUfrBSefzORXksLIkwntN3dhYudn3httR77sbOVpT5lJ7yfQmphbr1M0+3DiaibRdLK+jZDmY3LCT9gq8+vI8q4Fj13PSo86NPv26Oq96NvFzetaO+43CkKD8dI+0WjkLSPMV3k6g1a3a03CdDtOtbE4MKeMcJeR6EjvIUPUGuqy3ovVcSdaZTjmm7msriPbubKs95HpjyNSi4xpNtfc1Tp1hkvFHaXS2t/wDZ5zPi4hPQK8/KtSkQyvZendH6xaU/pNtyFcmwVrtcggOEePZHovHkKi9vf1Jpl8vWK6ymgjk4hJJ2/qrQeY/dUhucK26q1DMc09uYkhr223EHa4QO8Ukj7QIPOuGZkjVoMS4gwdVxE4YkoG0TQn7K8dF48fGtyfYHLmpbHqJZicQLMmLLcTiPeIKEgg+ClAclfKvPqCJqLRLLfYXJu46clfmZTKt7RwMgH9Ff3V8LYDcRJjtxEi5M5VKtqhtbkY5koH2V905A618bHc3LLEdJYVN03NUY86E7zS2T5eR8ldc8qkHp14hOprPH1AjaJzYDbxHdUsYHJXPxHQ+hHhWGtd2VftHPaYlth1+MsyLe4R3m1Dqj1BHh6CsrAhsw507T7Ulb1vnxS7b3ljvLTzKAT+kFZSfXNQmE+uDcxIZJQvIUPiDzFbodyNGWtXYvQGBKTliWpVtmoz7yHBlCvilY3j+wKp5xOxxafJRFWixckRoUmO0VJlOTGpDBSBhGwqOef9ofdXe4Wu2anW/KuQjw7i8lREiOyGkhfMguNoG1QP2lJAUMk4ViuhRaorTONnY0pPlEqele67W+XaZ7kKa1seRgnBBBBAKVAjkQQQQa8NXzjilKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUrkdaAJ5Grt1Myq43SW4j6kvOrkNNK64cHbJ+Bwr8KrbQlqauNzclTGu1gwEB+QjcE9p3glDef1lEA454yfCpfdZt0OpHZk58KuJcDqiOgUMDbjoBjAx4AYqnmS/XR1emx/Zy9Fg2lM3VdlYvVpdMfVtkSNqQcKltpHn4rA5Y8RU30hd7PqqwvtuxcpUCi6WtXvMK8XG/HrggjoeRqooN0kWuW3fLO4tloqC32m195pY648cZ6fdU1lqTqSONZ6UkKgalifWS22lbBIH6YT5nxT0PPx5Vx5x2tHbUj53SC7YWZWnrhLXP0vcVpXFnJ5qivZ7iyPAjmFDxGfSs3w71M5AWdP35woegnLTmc7R4KT+khQPMeINQuPqdF1eUZUBtm4ry3Kh7iGJifHaD7i/4/dXoeSxNhNJVLLQaOLZMc5Fo5GY0jyHkrw+BrU4aM9nm1xCmaM1wi7W5KUQi8ZEJ1rm2tsnmAfTPSpzOjWW8NwtVQAlESaUMSVIPfhvZ7qs/Mj4HzAqLuqn3iwy7Md6vZSXH7eTuXGWOq2x1Wg58OYHmKjmkb8/peY4w4TItE5JaktDyV4geCkkAg1ml+ug2iT8U7bKhz4mqIS+zmtOdnMQ11LyPtfPlR161yPZr2ptKLZcgI12bbGEoUrkHMeYPMHl+NZTiRIQ3Btl1ZnNy2JbKW5CkBW1wJA2ufEpPjzBTVfQLgqNbbzalkLY2OAehScgj7hUxixs4uSZ1kun5LlPF1yzXAt5SORGeo9FYSajd1dSbk5sO7LiwPDkSCKmeqEpkR3bgtSkqkRLe8rHicFCj8e4aicv2WTfJUmKkpiJcJaB/QHIfurfHsYtnkbQpOQkKWc5UAB3RWWYabcQ7OjOqZdR3lt71EBQ6qSr064POs9ouVZo7yXfyxNt85XLe6wlUc+i8Hdj5Gspre0tpC7s1b2IMgrSifHYx2TqV4KX29vLacEHHiRSU0vJjxIFqiMq/admOoaaTLtf9aQUkA9iSA4kegUQsDwyrFVjVyaVSpOr4MNtwD2pDsIkpyMOtqQM/3gap55vs3FIJyUqINdbGsc4bZ5/qFShPsfKlKVYKApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKClBQFh6fbeh6OgoQ3/ANvkuSiSoEOBv6tvI8MEu/fWa1DbW0JDsd9yerskOSHkp5NuKGSknxNY22Izo+wu9NrLvL07Zzn9/wC+sxabmuJaXGW0AuOO7k55jO0DOPPy+Nc3Lf7Hounr/hRhLfMl2yWHVBIeHJW8bkLHkpPjWcYuMWI83dbPLftkncD2Ayps58UqByPgRj1rN3jRKbRYEXC9uOCZJxhlIIS0k8++r9Ll7o6eNRGDp263C5Ii26I/3+Y3jACfM+VU3OCW2y9xl6RJL1qaz36MHbjagxc08xLgbQFke6VoPXn4j7q5s10iSVDfKQh5ScPoe9yQPI+R9fxFSC3cJY6YwMq4uh9Q5lsZSPvr7wuD8ZclP/WEh10+6ltsZUK5/wB/jt6Ui59jao8miG3CHPs9zTPsz0lt1odoWyr61pA6KSR7yOuCPnWagXKw6zbVDuiWLbeHAAzMSNrTzn6DqeiSf0h41LJvByZGjoeYuN2aDXNtbje4IPmPEVGrrwuvBd3tzoryj7y9hbP3cxWz7uleWalRN+CI3Ry52ky9O3Lt0lp9O1Dh5pUDzA+RPxzXkusgomTUtHvKBaI8+6AfxzU9uugtQXEQHJ0iO+9H2oU4pfeWhJ7oKvHA5fCvrbeFm64OybtNDqVkqCWeWMnJ61LzaIrewsa1vTRgNWLULXHtMdK1ykRIzLyEJOWwhJWc8vNZHyqOQoyhsjMJSpSsk5cSnJ+ZrYG02iDbEOJhspSXCSpau8pRPUk+NeO/6WtF4aUl1osrPRaFEEH4dDXP/Mw5acXr5Li6VLjy3tlaw9MT2Wkqft8qAtYyFOoKmVHzORyHqCR8Kktldan2tek7wwqPLbc9maU5/kw4eXPxb3bVA+GPWvCP6R6FfQy1MLsBxzCUL70dzP2VoIwn4jFeziVNg3qzxNUQmFQJsRQbcAGS2tJ/Nq9OW5J8kmr8bI2rlEpWVSrepEAix3bZr22tyUlKmLk3vBHQhY/kaqW4f9uf/wBIr99XFqVTk7VarsBuS6+zIX0H5xQ/iTVW6zhN23Vt4tzSipuLPfZQT1IS4pI/dXdwn+hwOqL9kYc0pSrpyBSlKAUpSgFKUoBSlKAUpSgFKUoBSlKAUpSgFKUoBSlKAUpSgFKUoBSlKAUpSgJ9psuydIsu71qTDfcjkKGEo7TC0gH1w4flVk8JoFpbel6ivrwbt9qQlaWwe888eSUgeJ5E/Kqt4XzGWRfI77JdK4aHWufuLbebVu/u7h86nGhoybpdY0SYpSbdFCpkvB5FCU5I+JxgfGuZnRO/06e6tFg6qvUq9z7OuehJmym0Kt8EIy1EbP8AlFJPvHHQHrjJqY6S0+A6zboYHauqy485zWs+KlHqT/7VX3DNqVqriQu6yQpJkvdmyhI5ISB7o8kITgfOrjsMuJZdVIXNkIbZYWpHarIGeRAzXlc+LUoR3+p6XCf/ABykvKXY8d9t7dsuCobb/a9mAF+ivGrB4dWJqLb0z19558Agke6PAVW92kol3OTKbWFpddUUqBzkeFW/ox1Lunoak+DYB9DWnp1UJZEu3ZGXU7bPto7fnyZjsweqU/dWIuulrPc+8/GSlZ+233T94rNjpXNehdULFqSPORtnF7i9EcjaNsEcgiElZHQrWVfvNZJmy2tCNqIMYJHh2YrIEU3YqI49MfESZX2y8yPAuz21aC2qEwWz9jYMVXfEjT8K19hKhNpZS4SktpHU46irVByKr/i5LYESPEKvrS52mPJIBH8apdSqq+i20XOn22/XjplTantouthlwSQkuNkpUR0I6GqsspkOQJ9lnLBfWyG1ZVgOICsJV8U4x8DV4WtvdcogdQQlTrfI+IJFVDxoi/kPiBIcYaDex5Sk45ZB9a53RZvTg/B2ep/1r5IpblNzSgPjC47TSTnz7cD9xqueIrjbuv8AULzK+0bXdJSkKA5EF1RBqwFNJc13Ehs80O3AAHzCl5/jVTzjma+f84r99e1w1qJ4zqr/AHSPPSlKuHJFKUoBSlKAUpSgFKUoBSlKAUpSgFKUoBSlKAUpSgFKUoBSlKAUpSgFKUoBSlKAkfDuQlrVMeM46Gmp4VCcWpW1KQ6NoUo/opUUqP8AZqcWaRJsjd2jvIUy682qPtUMZ72CPwNVMg4UDVw6ylKd1NOU52zaEKL0dDvJWxwlxGR4HC6p5kdrZ1emS/Zouv6NttDcW6aldThuC12DCTyyojKlf8/jUiiWt2+T3nzcUxljv7XHuzBJPWsPw/mt6e4VuQ3W3VypKErUhtOTgjp8T/Goong3r3Vy1XG6SVwO1VluPnmhPh0PlXl7a4ZVi760eohKWPW38lut6FvAjAty2pSR+bHb7zj4mu9kuV70s8RIhumOTzQscs+YNUS9pDitw7uiJFkvkha2zkNoeOFgfqK5EVLdP/SWuMVxULWulwtbYCStjKVE5G7KVfPpWa6fWpcqpdzTLMuUONq3Fl5W/X9skOoafadZKjjKiCkfOpiy4h5tLjagpKhkEVQ0bXnDbWj77NlfcgTgklKHWdgWcdOVTPh5qZEUN2eYFc1YaWOePQ1EMmyiz6Vz8+Gap4kbKvqUp9vJY6lYr5lYHvKAz5mozqq/SWLhHtFuKUypCSrevokAE8vM8jVZHirom1GQ9qW8PT7i1kpjtpJHLoAPdzVxXKUuMe5UVL47ZeK3z7OXWEB4/ZCVjB+dVdq2x6lkzvyg/B9r7RQBbadT3Ujw7xAxVa6m+kjdrk+u1aC06UZOG338uLPqEDkPmaiVu0Xxi16+6/cdQzUhY3LQ7LUlCSSTjYDgfCpycau6PGx6NmNOyl84otaBISm7oSYj8ZTL4StDpBOQRnmORHPwqvPpU21MTV7U5BUFSGgQT54/mK+mm7JrDhzq6EnUDjs+2dont1J3KCE5zuGfDzrJfSrfZmXCEple4JZyOXhgEfvrn41EcezSe9nSvuleovXhFM2IrXqVmSFpSWGHZQc8AW2lKBz8QPwqpVkqUVKOVE5Jq3JIbY0Ve7jAjPPqYhIjSVKyUtLedI3DHTCE4+JqoyCa9bjf0nkuoy3adKUpVg54pSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQFvfR30zAuj0+63CVGjNMSWYqnXQcsJU288t1PqExynz7/Ks3xCYjv61jyV3KdIjvKA3zmtjxQjugE4yQQAATzx8KwfAuQk2a+QljuuNvPAeqIj6R/wDsqdcVmXDbLRKkMqKkvLWFHkOzKgNo8xmuHnXyVvD0el6TjxlXz9luaAs8y5txnWCw2tlptR3DulWBgY++vdrTiXetO215x2MyktEhRQ0VH5ZOPvrH6Pv0i0qRMba39q0MoXy54/5VILBMsL6ZsfUEQuG4E9p2yfq1JPh6da81jzip9n333O/lVy1uUdrXYrHVo4oT2bTelv22Im6sqcjJKg/02nBIG0HasnAzyQaj9rZvt6t8L2y123VDrzLhfYaZ2SGC2VKWAeiuQB5Y94D4XZceEdmn25UOz6luNvt5Wl1uMhe9ptY+0nmCDzx16V4FcOYelLRKdXrSe32jRQtaCEKUny3ZKsegOPSvQbxvpb9nBjbku3SfYrrSOkNNy5Tdx03CU3I5hISVZQSn7SVdORzUv0Wxcp7764iUtS4Z7N9ClY2qScgj49a66LW3pt/tI0ZzCm8bXFkFZIwCcjPQVkdBWZu96tuyXJUmMlcRtZ7Be053qHWvOzlHIt4pvZ6OVk8eptpJGPu92uCLk1cXnnDMadCUYODuGU7em3GCc+marq7aE02zM+viTrlcZLuGoSFn61SlYA5YwMnGSat3XulU6duFvbRNckJwpwbwCd3MfxrAanag3CXGmJD0RaAEh9pakKQrduIyPDOD86VTePbxkyEo5NSlSvJXkuHqSzqRDs8ez2Oc5MMVMRDJWslOQsrcPLltHLx3CpNaLrr/AEtpmRrGWmDKtrU1cZbzTgbX3FbVFKFcljdy5eRqUMcOU6vWuc9q+Qh5eO0W2cOE4x3iNpJxyycmpTD4X6ctiIz14u8m6sQUJ9nYkrSGWto6hI9eeM9a9BGeNOHL3/s89KWTCzhLwdbDejr60txpraI7ykb0O4yc+WD/ADqrPpG2+ewylUzAfbWGgpHIKQUnB/CrTfsVwnTpF5s2xmNu3MhPIkDpt9Kqvj3fZk6xxnZCU9ql8K5DAGznzrkxnq1b8t9n8nXrj+u4Na13XwRfgeq1txpqL7crwzb5jm15EHKEZTySt1Q54yTgffVUcc4kKNrNLkNlDRfjJVICEhIU8la2lrwOQ3FvcQPEmrs09FmHhnDkNMobbDyoy0oTyWezC93x/wCdVd9JCOYl5tkVbKW3GUzELOOaj7W6rn/er0PT75OxxZw+sY9cYKcfJUh61xSldg86KUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClS6w6Euc6IJ9xkRbLAPNL85RSpz+w2AVr+IGPWs6xo3RiI6g7eb9MeCj34sFCGyPD3lE0BWlKslGk9DvtlLN6vsV8+6p+I0pA+OFg/dXgvnDe6R4y5tmmRb3FQMrTHBRIQPMsq7x88p3AeJoCC0rsoFKilQwRXWgFKUoC3/o9KgPSpcSQva8t1tKknBSWHEqbWevULLXLyJ8quvia05K4f2/LAVKtD6mZCf/ABCl1BwfQjnWsPCmWWdbwY3b9gmev2JS8gbO17iVZPTaopV8q2c1625deHrdzG5Jns4lKSSgNyWxtWSPJRTj51wep18bVNez0vRrdw+mZWwye3hNSCpLigopKknkspVjPzxn51eKrZButrQH2W3G1pO07fPHMGtftGqjpsEdmOrclpCRndnJxzOfU5rYXSMtmVYoy2jkJTsPoRyNcDCgnfOLO11ObVMJQ9EeVoIpASxdJSEjw5VxE4fw230yJk5+W6nmjtMFIPng5qdiuqhXWeJWzjrLt+SmNfW8W7UrzKSSFJSsEnJ5isjwcjuo1Hc5Kh3FRm0D47lGvlxRW27qpa0LCz2aQvHgR4fdiszwhZUDOePQlIT6kCuFRBQz3rwd22bfTU5+TjjOnLlqdPvYcR8gR/OsDoNi3TZr0WcUqS6gJShXukfzqQ8YYzjjVvkp5oQVpV6E4qDWR4xrrGeSvZh1IJ9MjNY5rf3ibXYnp8U8FpPuTGXw27CQp22XFxkH/J45fhX1t+gpC3Qq6XBbwSQdgJOfjmrDcRtxzzkV1UK7aw6ovejiLNta1s86I6I8PsmkJQlKCABWqPHHnaseK5KkgevOtqL7NbgWmRKcVgIQcfHw/HFai8dHHHYTJaTlSXC64c9Mnka05Ki7oRiXOn8uE5MnOm4ql+waecUlmG3KXMfUfstISkq+/aBWu30iry5dtcFLidikJW+pvaRsMhxT4T64Q4j93hV/zZTtt02lYiPtrnsqQlSz3vZkJU6581JGPnWoF7uEi63SVcZayuRJeU84rzKjk11ukxk1Kcjldcsi3GMTwGlKV2zzwpSuyElaglIJUTgADrQHWlTy08NrmYyZd+nxLIyoBQaeCnJJT59igEp/b258M17P6K6IaaQh683qS/8AaUzGaQj5AqJ++gK3pVjv6M0k4hsMXm9QVE99UuAlaQPMbFZrFX3h7d7fAVc4MmHeban3pMBzeW+WfrGzhxAx4lOPImgIbSlKAUpSgFKUoBSlKAUpSgFKUoDshJUQEgknkAKvDhRwzmv3uNb4UFufqYje+mQ2Fx7WkjA3JIIW7zzg8knHLIyITwrsilqe1A4ytxUd1Ee3tgcnJaz3c+iR3vjtr9DeAmgYmjdKNNqw/cXj2kuSod9x053c+uAeQ+FCGR/h39HzTVmcRcdRNm/3Y95cmaQ4N3iQk5H35qzxpSyNthtmC00gDAShAA/dUgBzXBFBopLiZwj0rqFK25VrYjyVD6qZFbDbnoTjr8DWpOsbJfuG2qXLPPUJDKDvjqJOxxGOS0nqhXLqCCK/QPVisLY+B/hWt/0wLXHe0Tbrx2QMmHKDQOOZQsHI/AVPrZr5/toobU2mrfre3fle17Gp6EJQp1SUoKnD9iRjkc/Ze8ScK8xTE2JIhS3YktpbMhlZQ42sYKVDqDVq6Hucq2XlMhiO5LiqTsmR0AntWT7wIHp4+Bwa9/HvS8YQmdQQ1LdcYLbTzxHKRGcGY75/W99CifFKfOsU9m0pSlKVIOyDhQPlW4mgNVwL/oabCfRu9vJmtEYSEqXydSB5BYWMeorTpPWs7prUVwsUpDsVYW0F7lsOZ2K+7mPiCKqZmM74aT0XcLK+3s3o2B4fut26G2kBS3EvGOSV4SlAcVg/MhXyArYjhLc2wJFvlS0ICcKaC+Wc9QP/AF41qxpiRIg6kRaRD7Zh5xEtsKPuMuoS6kqPjtQoZPqqrghSWZUdEmO4lxpYylQryWfyw7lYlv5PZYyjm47rb18GxJVjyPwNYrUV9iWiGXH3E7ycJQDzUaqxXEZ2z25MN+TGbU2jIW6vmU+eKrfW/EVK3VKhOC4Sh1ecV9UjH3bvgOVWHnStjquPdlWrpihPdkuyJPeb3HRei/c1upYdDkl7s+aiEjOB8yn5V7+FnE22J7eHEeW+x2pWW1AhxvPUgeRPP4k1SE6Lqa7yYq5TUy4S5BV7Mx2vZJwrkVJSnCtv6x2isG/LvNinrWmZlcZ3s0ntd6d2OYB8QMj76irAcVzb/Y335EJ/q/6TYnXPFGwybq1b75JXFiqeTmOkneQCcbgOgJAPrgeVYuBMaen3BqO6XWo0gpacPvFJAUnPqMkfKqISbndVMT35QWl1ZJ2IGcg94fHGDjyNTtqyXe3R/wAqWG5LVFUntHX2Sp1DZx/lm1ZUOvvDI5dKxyML6kdt/sZY2TCp6S/U2h0nq+HdEpjy3AxK5DC+SVfCpUetan2nU8mM+3Fv8URVKALctrmy565HT91WVp3WsuBDUiPJamNLOUFS84HofKsKcuyj9LY7/wAmi/p8bP3pl/8ACVcW5TqYUSKg4bcUVr8yR0rVziped9/UwyhJQEdkvPMHn/DJq5bzd5NwfXLnvBSsE9cJSPIDwFUQ0ynUPEG026UhI9ruzTchIVgFK3E5/A/jWOL/AO1lc/hFqcftMVR9+WTL6QetYDOl2ILWVSGoC4iNq+jjpAVzH6KAr+8POtWKyF8u0u8TlSpaxkklKEjCEAnOEjwFY+vYY1P0YKJ4jKv+tY5HWlKVYKp6bZBlXKezAhMrekvrCGm0DJUo9BV06esVq0Nam7pIeQ/cXm1pEhlf1hV0Ulj9BA5gu9TzCcDr5uA+lW3IjmorihSG3kO7XFJ5txmx9c4n9ZSiGkkf5weFY3Wk6bc7+/NmxTE3YSxHCCkNND3EpB8AKhsEh0Fp6/cSdSJtUNQjxWgVSFpT3GkeKj4qUefMkk+dbc8M+FOldPBLNttjDz2O/Mkthx1XXxPu/AYqA/RHtTMTh7IuiUAPzpRClgYJSjugfDrWwukjhD6fJQ/jUGl2ftxOV6TsbrfZv29l1PiFJGD8sYqrdf8A0fNM3AuXPSfaaduwBUhyGdiCryKBgYPjjFXhQVkbEfmhxa4b3GPd5Md+2MW7ULSS6uNHb2sXBsdXGgOSV+JQAAfDB5GmK/T/AOkRoRvVmknH4iUM3eEfaIUhPJaHU+6AfI9PuNfn5xWtH9YjamaZDKLmtaZLQwOylox2oI8N2Qvy7xA6UJ330QKlKUJFKUoBSlKAUpSgFKUoDYPgNChru3Dq2pUpaZL0m5yUqIIDwdcaTjy7kdHzJr9ANMLSu2pSDzScKHka/OLQd0Xpp3QWolgpaQwpRx4oEuQlX4A1vnYrqh2Mzcbe+h2O+gONrScpWkjINDXOXFon1fKS83HaLjhwkVHVX2Wfst/dWNlyX5ThW84o5+z4D5VOjB3I+txlKlylOnknokeQqgfpiXViNoy22grBkTJXabEnvBCAMn71Crlv94t9htL9zusluNGYSVLWo8j5JHmT5VpFxY1nI1zrOTeXNyIyfqojJP5toE4+ZySfjST7aMa1yns+PDfUuptM3Ca5pmJ7U/Kjll5AjF47Cc5AHOpzcYv5e4KwhIhrclLhXCAtvaUKLkdPtDJI8wUEY9cVaPCrSUbTPCqHcENbpk5Iky1JA3LSo5Sjr0A8PU15+I9ztUS1xZrTa47TL82TKAQM5TCXnkP2R8TWCRu5rlpGi1KUrIzORXot7Tciawy86Gm1uJSpZ+yCetecUoC9LzCuku+TH9NImyIhaREbVkLfS2htLYStCSSk4TjmPhXosdn10mIY8Zz8lxUK3KdmykRsHywshRHwBqF3GSt63WKU2/2r67chK1be8FoWtOCfHASn8K6KeuUQtuutuNqcTvbXzTvTkjIPxBrkZNSlPbPTYdr+ktE8g6TkXSf/AFie9eZAP1nsmVMJHmt9WGwPnWYhR9O2O4lKJMG53bOGkNJ3RIWOeSTydUPTlz8elVpK1FeJbCGH5Et9pA5IU6SkfLpXk9vnbO432QPjjmfnVd0L0WfqP2XNddXWm2QpsaIt6XJlbky7i4cOuj/w0+SfXkPDHhVeQLHcNSyWnkyYUSKnIabdfSC2Cf0Sc8z4nrWW4bPaNMyNM1K687KQsFSXkkNcj4Y6n41fE7UHB24ltx0Q1pxjCXEAfME1XnNwejaktbfdGv8A+THtMLejXR2FNtjxAcRHlI7ZpSfdcQknO4Z8j41JtMOSLUpqXHurjsFzPs9zh8y0rydb/elWM+BNW9bb5wfglXZN23s8YIU42QPlmqU4oXjQzl1lr0ymSxIc5JXGX2bSk/reBqFJz8hpN7S0Te/yG3bCpF1gIZbWconwWi9EWT1UUjvsKI6gjHoaqtTnsi1rt0xcYKUdr0RZUhY8i31B+GPhWIs2otSWvBt8p9OPeS2SRt/snIr5XHUE24b334EdS/tuNNBJrbGr+RjzcfBkJEvU61LSZ0mQHBtOFHp5bVYP4V9bI1dYuo4d6uCnLamGrtmpEpvkXEglHdOCrvY6A8qjbj01aD2naIR4EOqKfuzRyUY9hvhKUrdERPZOKzlol5tJKefI4URVnHqip+Ctl3S+k9kDuMb2SY5HDzb2w43ozg/fXnpnNK7R5fyda5FDQdaEGzqG5mn+E8iNDaKnmlwbUwlvKwRs9peAHiFOuKOPWoTxJ1FqLUl9bmanhmJOaYSyGlRy0oIGSMg/E1sXwFZtdz0/NdPZSVxriJUZRGQO0ithKh8ia9X0kdJR71w7k3bsEGfak9shzHeLf20k+Ixz+Ioa3NKWmeH6Il6ZmaBkWgOBTsGSokZ57V979+avW3zDCkhwDKTyUM9RWh/BrXT+hNWt3A7jAkbWZqAeqCfeHqOo+fnW7VluMG82xi5W2S3JivoC23EKyCDUGqzs+RYcZ9t9oOtqyk/hX2zUIjy5MUjsXCB5V7032YfBH3VkZK6Jk9TOJRb9h6qUMCvz243RW2Zevra1vDUW5tTGko5BKivao4+Dn4Ct3dSXhmFAk3a5yEtx47anHFKPJIAzWhurr2/c4+t9QFolFySAAfshb6MfPAqDKuXJtlN0pShtFKUoBSlKAUpSgFKUoCz9COrvWhnLWtbi5FukKDIPMNtO95IHkO0C/m7Vh8H+Ml50Kz+SJzC7laN35orw6wfEpJ8PQ1Q+kb09YrwiajcWiC2+2FY7Rs9U/HxHkQD4Vaku0N6pgJvViWmRKKN8hlIwqQPF1A/S/TR1B5jINQ3oaTWmbL2zj9w6lMhT86XCc+029HUSn5jIrFak+kbo+G0pNmiTLq8PEp7JsHyJPP7hWpawptZQtJCgcEGs1atN3KdH9qWlqFFPJD0lRSFnySOalfsg02anTBeTNcSeJOo9eTe0urwbiIOWobRIab9ceJ9T+FQzdiri0XwYul6badjWe5XEqBAU84mCynHlu3OL6n7KalqeA9wZgrfcRYW1pHJhlhchSj5ZccSM07sz3CK0iW8MeI+m7toiz29U9LV2ZaRDVCVzdW4EgDaB1BHPPh41Un0ndR/ktM2zQ5RdWG1xVOYBKnHlBb46eCAhH7VezSam7aZt90y7b491tbpjuszbOhlTRXkBeUunAzy3YwDjOAao3i23eP6SLk3BbzrK+TTi04OeqwoeC9xOfkemKJGEYreyEGuK5NcVJtFBSlAT22FR09aEbEpX2boQrHMkuK61ZT2nWZ9khG3h2X7NGSlxwZ3PSDkkEnohCcDA9PE1BbeqOjRumFob+vCZJc553Dtu7y9MH76tjhxcpLmmH4zLSGkqPsTL6hzU87zWof2WwTn0FcfNbi9o9Hgf9RFNJ6OcujbtwuEhEW1R0qdfWo99aR72PTPL4nFYW/NKkOG4lktRVgCI0Ry7Mch+6rRfbRdNIi0W1G12+3Vu3xEhWNjDXezn1yCT61j7narVP11dblJQVae06ER22AMe0OoASloHyKuZ9KpRsb8l7RAmrO9Es6bjKjkuSsIhsrTjeVcgrH9k/gK8QsbjrSXinYVuLSEHrtQOavhnI+VWRqD2+560kJbCFSbOwhOEpwhMteEgJ9AsnHogV4WYaXNT6phsZWzZbO8w0AOXd2oKh+0pSviTWXIJEYY00HYAWyner8niYg45qAXtWPl1+RrzWi0CZbZr7QSt6M32ykHqpGQFEfDI+VTu1tPwdE6f1TC2PiO+4w+jqShWN6CfIgn+8a99o0+xZL3OubLPb2wtInxSDlL8JzuvI9SEqII8xWHP4JIFbbNcodzhvxtxMlovw880v4B3tn7lJxVgW2CmQzGvul1JjTpTJWIikAszwn85HcQeXaJ54P2hjxryWyEuPOmaNW4HXbfI/KNleI99AAWUj0WgA/GskIMy13DUVlt4KFFKNQWZf6BAClJB8sHGP1ah2NkEMmzLLbpL0pNtQq2XBtwGEtIKor6eqAeoSeWPIH0qHSmY6eHuq3nGd7o9jbbcx7mXskfMJH3VL+MLMNeoo14gBKIt0jomEJOQlax3h/e/fUBvyZLGh7oWj/VXrjFZPLrhDyx+4Vfw+8kynn/9LK+Fc11rtXYPNHWuR1rilAbcfRF1VEVCatzriu0kMeyulRwS+zktY8gWSlA8SWlVPeNvEvTaOHd4tcWcl+4y2lRDEAIcbJ5KKgRyxzrVXgYzeGLs9corrjEJBCC4kd5UgAlns/NQUQT4BJVnrVuasDN2mw7rfXoUm+XpwtMw4FnS4VgYSHNynU5STgBWOeCelDVOK3tlLE5PlU24acTdSaFkbYMgybepWXIbxy2c9SP0T6j8att/gJdFxEusosLylDPZOx3Y6x6ZbWoZqFaz4OXOyNqXIttytxR1Wgpmxz+0jC0/NKvjUGfOElpls6c+kVo6c3tvEadankjnlHaoPwKef4VkLnx/4ew4ynGJUya4OjbUdSSfmcAVqldtO3KAyZASmZGH+WjHelPoodUH0UAaxLYUtYQhJUs9Ejqab0YfRh6LP4ucXb3r9abZDZXAtRWAmMFblPK8N58efQDl8agPEFSLHodizh1Ik3J5K3kJPPsms8z6FxSgP9HUhi2tjSlucu99+rmhoKQ1kZjIV0J/zqhyQjqOajjFVDqW8PXq6uTnUJaBAQ20kkpaQkYSkZ8AKJtmxRUVpGLpSlSSKUpQClKUApSlAKUpQHas9pTU1x05L7aIsqbJBW0VEAkeII5pV6j8awNcCgNhdP6qtOsmmZci0xXLk2sIMpxOxxtQQpZUtCe46AlKsK7pyBked6cDbXCfmTZ64yVuiOwve+kLfytsr94dORTyGAK164VWEM6EcmKUhp92K4+lTwCA32rqWAcnr9Wh5Q+PKrmhX68ac/LupbHEe/Iz/YJTKuLJZZSlCQ0kob99eeXkKGq19i3OGtySfyrFStAcgXaS1hPhuX2n/HXt1TqnSlhluNXLUNtjbTkpU+krAPmkc/wqlYabVKlvZud/1RPlOdpJj2Jn2aMpR6hboxu8BzUak1o0dqKMlBtGitKac3pDiXZmZcgZ8eXTp51KND7FZXhxiVxbuGrrEfarPLOyVHjwZDyJDZGHNxDYQN2CevWsPqi0Wq421+KLbe7kypQQ005B2OlvPLvbye0RywrHMcjkVNuNN41ro2PHbv8AqOZNiTUuNpXBYaYRyA3IIUCRyVy8+dVBo2PpO+aqt1nMS5W8y3g0mSZKVbFnknI27SN2BWLLEPGyDa84ezNPSHnYUr8owm0lxZ7Bxp+OnOMPNLAKTzHNO5P61QatoHJMy6XifGuD8qfJUiUe1kNgdklllxDyCByHRPTkevWtX6k2ClKUBYFocU/o20uJbSOwkSY4HirGxwE/+YR8qtbQlxbj6WuUsoQ3Es8F0M5PN2Q9hAV8QD+BqoNOrW9osIaB/qtxWp0+XbNo2f8A6V1N9NrM2XGtQ7QW2MkyJWScKCBuUo8/2R8a5WctnoenP/jLA0VM/J95tKH+6mx2Z+5PDxS44lSwPjtCRUg0rZbdK0zbYrkhRejTG5U9Ozkp1SS+sqOfBAA9MVC9Ee0X5rWl5kOhvfB+sUDgYWsZT/cSUgetSqw3tuFwX1LfXl7Zk6W43HRnvfWAIGPgkGuUdAxvDQrmew3JQUp68ahL0hQHPY2Mj/aWa+HDdof9JF9gOrybpClIBWeZV2pOPwqQ8MUxrdozSLriub9wCOnmtRP7k1HdUhWkuK1puiSBvd3HHQ5UpJ/Go5d9GSWj3aUbVF4Ualti0LU7apQlNjb1TnCjjxGK9PCqfHd1B/RC4KKoU1hb1sUo8kb0ntGv7J94eRFTu6WyIu+PNMEew320OpIHipe8j+Aqi7VKkxLXAuzJUbhYpWCc81JSoApPpgioT2SyT6zadg2SBqCIns7lpmYiFJGOa2Cco3fA5T86mOsrvbxq3R2pAGkQZLRjOFKxjs3EhSfwWR8q8FzTEna41LZ3NwjajtSno4x3S6Edqk/Hy+FUrJuU53T0OK/IUWoby2kpPVJwCBj5GpUXLwQejVaUx1P2ZSucCY60g+becp+I/nWFvMVLnDm9uPBRDbjD7YKjgKS52eR8UvKr1XVSrhcI0lKtzslIbcyerg5Z+YIrA6xu77Wj2LcokCa8Fbc4+qZ3AAjxBWon4t11cKOtHP6hLVTRX1KUrrHnBU+0Jw8mX5TUm4Prgw1oDrbbLC35clPk00gHr+kspT45PSoDW1EKdcHNUNx7POkww6+00lyKBiQmSAGMA8iA3nrnA6UB1sEK3RosGPItl2gRGe67Fat4VtZzzSFFQJUsjK14yc45AYrJaTei2ziy1rHU8lLUNtCm2WnYUhlMdO3agJyjbhIwPe9arbUrekrNqCfaWYlynIiPqbEj2kI7QpON2NvLmKujhBc9ea0tj0y06glRYMNQazcGGnUKPI7AEgEgDGfjUJmEl22XfpPVWmb5LbFrv9tkrB3bESElWP7Oc/hXj1vLDl1sUZzm5KugVj0Qha/4CoNddF3+RuevWh9MagS3zW/AWYj/AMRnqfnUXmuW+BNacj3i9aaucNRXHjagYL7AVjmlDx6Z6clVl5KyezNcaoFsYurUkQwy6Yj7wfYwlxRbUggnwWNqld1WQdtUzqa+W3Qtq/KTNmgsz5cp6M3LjkredU2ltSigK7rCdrqDnBOVchyyLI1Ldb3qBNo1LqGAtq1+xuttyoLZcjrS6jBKh76DkJ6gjlVJcXra8nRzDkotOuMNxn2nEL3IIIUw5gg473Zsk48hUNG+DKy1RqK4X+SXZrh2BRU20D3Uk9SfNR8SedYSufCuKG0UpSgFKUoBSlKAUpSgFKUoDtWb0PZRqHU8S0rf7Bp3et5wDJQ02hTjhA8TtQrA8TisJXusN0l2W8RbpBUEvxnAtGeaVeaVDxSRkEeIJFAbIRlRlXVpi0wm1XqGIrbKHUhMOHGSkgJV4buaMrPMqUrHPnVyaO0u3rJH5e1dMeu7aSUNRlq2RWlJKkqAYTywMDClEk+Qxz15s82RqvTEp+B3pDsdt2M22SHEuRlgFlX6WG3SoHnkJHQg1aFs4rOaXhzY0ViPPmSHvaldo52bMJakguJWv7R3BRwjPx8KI1yi34LW4TOez2GZZXB9fap70Zaj1UN25BP7KhWW1HxD0VZ4rce5aihiU2s4YbV2jhBxjknJ65qr+DemJPEu/XO5aofvjcB9IePsqTDizDyGP/EWADyJI5eXSvdx+0Tp3Rpt8yzpn2yPIa7FuHbylpDjqTkrceIK+YUkYB5461shFzkoo1Sj22yM8bbmxxEYtsWNFvMe3RlKd3rhdmXlEAZy4tOABn76qpix2S2XBiRHLq3I7qXk77xGaUSk5Hdwr99WLxgai3+w6U1K80lanreYbuVE4cZOCDz64IPOoPC08xPZWtqK32aMh3u9BjkPieg9SKvLpkpQc960YwvitRMlP1fZ/wAsT5yYkiG7c/aw6grQtr65hSVhK0nnle1XQVrHV96E0qw97Vd7qpDlubEqM2hKiVCQlha2yrl7pIGKoSuaWxXI61xXI60BOuEoS5+X2nnFJjCAlxzyBDzYB+Pex8zUptbxt2kp8sLw9PdTGHLq0kbyPmSj7qrnRM1mHd1tydgYmMLirUvojcO6s+gUEk+gNTCf7QERorsdKPZl+zubF53qGTu5HywMjlyqhlw2tnY6dYktMldsuP5L4aTIrYUJV0lIb9ezT3lZ9M7PvNZPVMpi3WrTmnUKS4AUSJWD9s9B8gPxqDNP7lAqOEoVyH769l0lrnyTMUVEJ2qSSOu1IFct1nbRatxlJtfDWxL3DtIV2+rwefIpV/OvZ9I+Gn2C1XJkbVBbnP0Uren/AHhVbR7jLu8O2WJ0HCZJkKJ6qykD9w/GrH1/em7zwPssmQlPtDDy4qiR+gpKQfmnFV1Bp9yZEh05eDM03pa4NqUt726OyEjnkF4HH3BVVncP+q+J97sjiR7NJku7R5jJxWQ4STHWbfYGXlENuanaYbHglKEZP4uCvFxaW2OICbsxyCpbiT8AsjNRx1LQXczOv7p+R7ppi8MIw4zb4hIPkAttSfuGKrfVA7O4zEsnDDy0voHqRn/iNZjXt2kXBxaHthRDS1GbKTzKd61c/XvVHLtJXIS28oYPJB59cJAz+FWILRB10y2XLm1KWQI8LMh0noAkHA+ZAA9SKiXEp1RukSBvyIURDZT+itRLix96zWXbuS7bBnyCWy0AhBQefaq3bkAemU5PoPWoDIfekvuPvrK3HFFSlE8ySck12MWpx7s4XUb0/wBEfGlKVcOSd2m1OLCEDKlHAHnWzdq1XZLRfI8iJAkyPyU/2MYKeS2ztaZDLf1ij4YJ6eNaxAkHI61fGt9JKjz2rnHEZuLJkpira7QkduG0Kdxy9wKURnwwaA5TYbJPkOKcMjtXVlZUm7RXFEnmeWE5++rf4LX1jQNklWybGvT1uddMhDwghZZVgA5LalApwBzqrp2n0QGmzIhNpbXzZ3I6p8/kRg+oNTrhlGYsGh9W6mZbLTjjDdtYKFEd905WoDlzCcdPOuj+PfBTUt7KzvXeLL801r/SN6gKYt1+iLlOrBUytWxzA8NqsHrWG4pJTcY1lsTa0g3O5tNrPj2ScqcHzSMfOo1wD0RpXV0W4zLumdc220pZMacQsMuddzbuAvp4HpWG4t2SZww1XBnaZXeHbc00Vocnt+2RY6jyKOX1iE48RnrVOyDqlxYUU/BnNVaYOjkuXXSc960okrQ0beQXojzilAAFCj3Mk9UYxg1S0hq2SwuDdIKHLtJiyFXFttW2NLYCshTak4wvCCoLHIlGCDk1Mr1xPc1lEhsSW2bXNi9o+llte9ExwIIbDaxyBCjnCsHlyqqbxcpGlLLEfmDCWIaWHGs4cdW8tTpbBPROEp3eQOOqq172bIRa8lR60sqtPann2cuB0RndqXB9pJAUD9xFYevZfLjIu92lXKWvc/JcLi/Qk9K8dQbTrSlKAUpSgFKUoBSlKAUpSgFKUoCa8O73IYbetLMhxl910ORFIc2krKVIWjOcDclXzKQPGrN4QIZHESC3qG2FSGVnYzIb2obUkgnkR4AHPjy861/QtSFBSSQR5VsrbbzIvHDOLeX3UG4wZbE9TqXMkpeBZdWcfa7RsLI8CayguUlH5IZsM9xSYh8SbNZLchHsTjwZkSCMBWcp2jyAV4+lSL6TdpVceHC5jacrt7yZGPEpzg4+/PyrVlpbxt7EhpavaI8nCVJHME94fiDW8NvDWo9HRvyjB2tToiS9GdTjG4AlJFdTKpWLOEolaE3amma3aP0lN1joG42YlxhqLOZnRJLjR2FLiVBYRjrywcDxxWck6Rg2WwS7ZEQshLCnN2DvcKQQScDJ5E9MZ5pT1Jq5bdHjxYzUSMw2yztUwG0DaAPAYFVdxJ1TbtP3VmM48l2UpwBxpBBKAruqJ8u6cc/UDrVTJz5STinpMtYmH9SajFdyjNPL9hm6mt/Z9qoJF0ZbIyFuR198euUKUM9DzI5Gtdtc21q0auukBhW+O3IUWFbdu5tXeQceqSK2IjqTaOIMJ6UcttTlRJB8FMuZQr5YNU/x2sK7NqRlxThWVByI7lWSHI6tnTwBb7Ij41zqp81sv5+L9vJRK7PWuKUrcUDtU3sV1bmphuvBxciI4n2jnu7RAwErx5gcj8j4moRXZpxbTgcbUULByFA4IrGUVJaZtqtdctosKe7HZmyUsrDjRUotqT0KfD8MV6HVFEVDQPvbUE+n/sKj8O8tXLaiX2TE08lPKO1D/qfBK/XofQ9ZOYM2TazIU2Q5BbbWpkDvLZOQHR+knvDmK5ttDitnexsuNnvuZaxymmLmZ+PzDO1I9QkAfxqRakmts8HtL21DiVuyHXpTiR5dosAH+6n8Kgr5VHiNuhXKSx2iPXCiCPkU13fmNm3RYgGFNFZAHMHIT/KqThsvt7JVbbibZp3ScjCQlF3lSif2mU/8J++sbrS6Nzrkez5oTKcUnn9kqJFfHVS1o0XptKOW0PqHxLv/ACFYphKn+0DSStbaCtSQOeOn7yKcFvZKej1XiaXWFpUcLdkJX8kg5/fXRC2UWRVxfAWoS0sxmye64cZWSPIAAfFQrzzIriJz7LxC1sEtJQk5y99oZ8hjmaid7vRQwIER9S0gYWvPIZ5kI+Pirx6dOtyijmUMrMVS0j46snNPykR2EJDbScOEHO9wkkn5Z2j4eprBA9a4BoK6kFxWjz1knNuTOtKUqTAkPDmAm5a1tcR1C1se0B14IQFENt5Ws48glKifQGthbqw+9eNOWtxCg6xE9skp5Z7eSouY58s4KRg8uYB5VV30d7QqbfJj3s3aKf7K2suEc2lPLBcUD/oUPJPourRtby9TcQX7ggpQJ1xKG1KRuCWUnaMg+GxNarJ8S9g433FnEuD+h9tvtlj2qSyUL7JLge2FK0LUMgjPPpgc+u3B5jNR/Xum5+kdFWTTkhC3WEPSbjKfbbJaUoDa0knoCRnkfMVNeGeqLTqSetptxDcrtCoNq7pUnON3ryxz8fHnzqzrtBi3Ft2NKYbejKV7PsWncnHjyPyq5i5rjpt7XwU8vCdU9NEe+jlZfyPwxhvOIKZFwWuU7kYzuOE/7IFRG28VWLpra9Wi6FpEND624j+PeSFbdpHr4Grd1IoWHQ0422Or+pwlhhtsZIIScYrSBYVFspfKzvkPqKD44R4/ea6GHSsuU5TKM5OpJIj/ABPbbe17Mi6et6wyt0NFiMyVBbmTgBI6HwGOuMjrVd8T7xJmSIdqkTFyXIW9clSnAvMhe1Ku8OuENtJ+KTVwXWYu0cMk3TtNj8sy7ockoUScx2MHrnKlKHwFa2VyrI8JtFxPaBrilKxApSlAKUpQClKUApSlAKUpQClKUAq+/o8Tot7s7ukZKyHn25EJI7oG15HaMkeJKXm15P66RVPaJt7N21barbISVMypbTKwk4JClAY/GtkNN6Am2KYmZa9PxYEltbS0utyVFQLawse8o+IGeXOtN2VChpyNtdMrPBO/owWSPcRMuU1AdU0EpQysZAcSeaj6jJraCwupXC2DkW1FJFar6GOodKzpsi3stpVMdW+4kqG3co5IAzyHOpnb9f6oiyVPLcjAqTgoSjKfj8a0X9crsf7M3R6fOPgznFzWs6zXK62K0sKbmsxUzm31AEKG4BSUjz2lXP8AVqg+IGHdVSpaR3Je2Sgk5OFoCsZ9DkfKrT1Dco2obyzdrqpPtLcdcfLaSnchQIIPn1rEy9P6VmNRkPuPq9mbDbZCjnaCSAeXrXJv6rW5HpOmQhjx3JdyAcRoKptgavrCD/XIKFbh4uoyhf4pB+Kqg30gW2bhp226h35/KTUaY2ccy4UKafGfDvNIPzrYq6RLfdLU1anMJiMZ7FtAxtSfD/1558awMjQljlWGNYpUZybBY7UIbcdOSHFJWRuGDgKSFDy51tp6vTFaZzc6uzInv0jR+gxW4CeBmige7p1Ss+c1z/FX2RwM0qrknSsf9qW4P+OrH5vG+Sg8C0075VxW5X/QHptX/dSOP/8AY5/jrujgVopv87phIz0/rbn+Kn5vG+SPsbEaZVl7ZepMRgRVKWuOM7UhWCjPXB9fKtt/+hjhvsIe05tB8Uyncj/arzDg5wnT+dtMkeX9ae/nT8vjP5CxbYvaNe4l3hzbQ1AS6Vso3rSFJ2uMqVjcPHKCQOn4V0jqSqU1tUnmrbzPmMVsMvhXwVZTn2Oc0se6puW+D8q+0jQfBhzZucuDG1GzuKc73qe71qtZn48n22dCmy2C1IoG9TJRiRYD5OxgK2J/R3HJH316GbjGgaZlOB5piXLWlRd7TBQ0hWQhI6lRUATjoEirr/odwQjTUPLk3J5KeZbcLikq9DgDl6V5Llo/gbOmqkPNTlqUBhPaPISgeSQBgCorzKF52ZW22t/qa0XS9KdYXHiqWlLnJxauqh5AeArBEVtcNBcD1fmrdKPn/WH6J0JweSkBNkC/i8//AIqtrqmPFaWznSxLpvbNUOdc1tadA8LF/mdPNHz+tkf464Tw64cKPd04wP8A873+Op/MY4XT7Wap/KlbcNcLuHa8Y00yM/597/HWRj8IeHK05OmWP9Ye/wAdYvrOP/kfj7SvuDEVqwcM5WpVqaLrUGTNQW1ElLryvZGEkHluGHlcvBY+Uk0Rb37dpqXenfzbEEsD0cc7g/AqPyNT9rh/pt61O2ePHXEhOOtLLTKyEp7MKCUjPPblRJz1JzUpiaeiR7E7ZWI/bw3cb0Oc+gIHP5/eAarW9YoktF7CpsolyZTfD1So+o0XMKUhNvZclKUD02oOP9oitgeEetJt5u0Cy3VhSpyYImuPJTgd490KHgdu0/OoRF4cojxpjEZlwplNhtZ7QAhIUFYH3VnLBbr7p+9y7xbozIkymkNK3KylKEJwEgZ5DkPurXT1SmJ0uoOGTHsu+uxdV/WDFS0RkLVz+Vaq/SY0+xbLnHk2lAbVLTsEdIAHaLV1AHQndVpT7/xAee7XZFOE42lI29euM9agWtLRrLUN9hXSdFYW7CeTIaQFpCN6VZTkZ548q6eP12qt/qzzsumznoon6R16RDY/oxE2diwWYOQQe5FR3gPQurUc+O2qKrbTUnC+fdlMLnaZt855sL+sclELVvcUs5IWAeaj8sVrrxUs7Ng11cbQzGEVuP2X1KVFQQotIUoA5PiT41Ypy68iT4s0W48qe0iJ0rk9a4qwahSlKAUpSgFKUoBSle6yWi5XqcINqgyJskpKg0w2VqwOpwKA8WKYqXJ4ZcQVe7o2+Kx5Q1/yrl7hhxDZaLruir8hCeqjCXgfhWPOK9mXCREMUxWcZ0hql5/sGtOXdbn6Ihrz+6swnhTxKKQsaG1BtPT+oOfypzj8hwl8GI0A4prW1kWj3hPZx/fFXrbZcx1QJfkKPosmqz0rw517b9UWqVN0feo7LUxpa1uw1pSlIWCSSRyAFbYfRCYaeu98S60heGGiNwzjma5vUFGxxii7izdcW2ivra6+rbucdz6qqVWpLy9pUVKHqauHRltjPcXdTuKbRsbaaSlJSCBkD+VTKVZIjmqI8vsWwExlpI2/rCuPLCnOO186Lcs6MXrRSdsY7+VpBz0yKzC47OPzaPuqfavhsM6mshQygJU8UqASOY5Vn5ce2KkogORWit1BUBsB5Cq66bKUpLfgy/IJa0vJSjiR4JSPgK8ryiKubT1niRJ9waCELQFgpCk9MjP/AK+FeAzbZP1HDjsQylTa1lRWzgHAPTzrU8CUYpuXdsPOW+0SmHlPJxlxwftV4VyZRI2vOj4KrY+XDss+Q7bHobK1hreQUDofI1H+HtmiQU3eEtDbnYS1JBIycYFbJdNlBpb8j8hteClGZEo8jIeJ/t1kYrj+AhTzh+KqnPCe3NP3+9TFtpUhpxTYBH65P8KyvEiAy3dbNIbSlIU8EEJGARkGtawpOtzfyS8vcuJAoyeRPnWQYZaUkqU0g/KptxMjMMWuIppltJLngnHhUZ00hKrzGCkhQ7RPI/GtFlUq58TKNylDkdo8WOUHLDX9wV7I8CEU7lRGDn9SrDdZhe0piqioUVJzkJqNtQG0akMVsJU12uSknOOWa3W4NlSTT3srxylLfYwEm3W3BUYEb/yk/wAqxT1vt4R/2GP/AOWn+VWRq+FHbs6nWY7aVIUOiQK7W9EKPp9uVIjoWkJGTsBPXFbFgWc+Dl62Qsta3oqV2JE/+kY/uCsbKjxwnamOyP2KtrUFkhs3m2TI7CUpW+lKwBgGs88zbDLRBchNqW4kqH1QxgetbIdOnJtcvBk85JJpGucqMyCAlpsfBNeFbYQe80f7lXvpSzwoeq7zGQ02to7FhJT7uQeVfO5XKzytQQbS1CIeRLwtS4+1JASc4OOdYfZPhzb96Niz3vWil46FZCvCsrF5N1e8uNaXZaLe7EYUtxBcALYPIGqf1RbG7Vf5EJnPZBWUg+APPH41rycOVMOW9m7Hy1c9a0fOG2pSklKSfgK9jy1IxjxqwNHQYVu0ymetpLyyjtFrAyrFfbT7cCZdpzjSEKaV2eBt9DWCwpSUXvvIwecttcfBUsh54AgvOYHhmsbJkSSoBDrysde8TV12m3tJtlyU7GQPrndu5A6VjdE2m3WvTpvctsFS0lalq5lKc8sVsj02fJJswWfDW9FF3GVLTuCnnUnyC6jl1lXJIUVSJKMn9I1sXxKsEG42qDf4jSEOtOtr3JR76FKHX76l8hm1tiNHlw2lKkqKE5bBGcZ5/dVmvAlF62RLqEOO9GjlxuM8bsS3x8HDVLcW1LXruYtaiVKZjEknJJ9nbrbD6TelbdpvUsd62NpYjzmivskDAQsHnjyzWuHEPQ+sLrqt6bbdNXSbGdjRVIdZjqWhQ9nbGQQPMH7q7PToKqTTK2XNWQTRWWKYqUvcPNdMq2vaQvaD5exL/lXaHw519LUUxtG351Q6hMBwn91dXnH5OeokUAoKmp4UcSh10LqEfGA5/KvkrhjxDTjOi76M+cJf8qhTj8jiyHmuKymoLDedPykRr1bJdvecTvQiQ0UFSckZGfUGsbWRidaUpQHI61nNE6gk6Y1FGvEZpp/siQ6w7zQ82eSkK9CPu61gq5NAbq6X1rpyfHjzYGjbeIslsLaUHPDOCD3eoOQfUVMoMhqbs9njphZ6dkrpWofA/VrdovCbLcXiiDLWC2snk074fJXQ+uPDNbYaY6t15DqlE6J7T7M7mJKM4a9oz8uwXV2NlvU85pP6KBy/fUHv2nbql3crVVxcA+yRyP41bY5ws/CoRqX7VctZE4+GWeKIMFKiQ3kvKMopbPeWefSpb9Dk7rve1ecZr/eNRC5D+ryP9Gf3V8eA+u2NDTZrz8ByYJSEoAQsJ24JPj8a6uLdp8pGq+rcNRNl9FMbNc6rk4x2khpPxwipSmUDbjKUcqCTVI6f4xwI8+5SU2aSfbXw8cuDu90DFe1viamRYXLb+TnW3FE4c3jABVnH3cqtxzY1po50sWx+ixtWJUubYn8ZxKAV8xXvvd4g2koclJKlkHZhOT8KgkjXDNxRDSIKkezOJc5uAZwK+ep72b0tlRZ7PswT1z1qtZ1GMeTj5Ztrw5duS7Ew0VcV3STcJZQpKS6AAT0AFeRc9U7VcFBt78UNqdSFLTgL5eFRjTOpkWJpxsxi+VnPJWK9Fw1+0uXEkiApPYFR5K8xitdeZCdSU33T2TPGmptxXYsSQG0e0ustNmSlsc/E8jgH8aiXCuTImxrtJmn69cpW8eXIcqj/AP0k9lc3JSre4plxpKSjeM5yef3GvHa+JEO3SJrjVoc2SnO0wFjIOMHNbrMyuUotM1xxLUn2Jfw2hLastycSnDkiU8U/eQK9muIinbNAW4QXI77aiR9xqCRuJCW7GYEGE7HcOdrwUDzJyTXsZ4giTaEQ5kBb7oCQt0qACiDnNSsyhVuHsl49nLeiU8SosiXbIbcZhbpDmTtHQYqIaX53uKPNxP76zo4hsuNqT+T1DCR9tNRu1ykxrk1KUkkJXu2561z8m2uU4yizfTVOMHFotx2RtmMxuzUrtEqVvHQYrE2yH2epJKtxXsSDuPXKqx41itQ7kMA+qv8AlXzt16daW++42HFvr3HnjbyxgVftz6Jtd/HcpxpsXhGfnx3V2meh0JOStScHPqKWgNKskYPpSpBAGFDPPNYSPqCQw04h9JkFXio9B5Vj39RqTahAbZCcAALB90g5rJ59PNNfA+3s1rRktVSZR1Pa4yglMXtAtKh1JqQuy+zuDMPslntUFe8dEgedQS76sRJMVb0FQcjOhwEKHPHhXeVxKbQhQRbVbx0+sFIZ1MZtt+TL7ezSWjOadhKhawvALzjvaNtrBWckZzyrH3u4qm6qtkUW6UyhiYfrlp7i+6ehqI2niA7Auk2fMiF1cnGEoVjaBXouXE9iYqMfyU6OweDv50c8AjH41rnmVuHF+dmf29kZeC2HQ2XlKS2nt0oISrxx/wC+Ko6+yJUu/wAl6YAl7tCFJHQYrPDia29c0SkW90ISyULSXB55HOsBqG7MXe5KnsRTH3pBUknOT51p6hlV31ri/BYw8edc9yRY2gJFwbiNwJkbLCm9zToGU7fKstZIrUS+T0MgBKwleAOhOaili1kIdqajiGVLSjalQVgGusDVLsWZJlPsdsuQoHkcBIHhU1ZdcIQ29tGuzGsnOTS8k1TOTNts5SWyjsitvmeuB1rBvNOXLhqpmEgurXFIAHiR4VHIus0Q4ktpUIq7dxa87se9WJ0nrp7T7a4siOZEVSitPPCk1u/I1ykts1/Z262l3JzeUGDw6aYk9xYbabx+tuTyrLalv1o07aUXC8PJZayEoWUkkKPSqd19r5++vRmm2CxCZcS8UkgrWR51iOLPEaPqrTDdtZtjsdaHg4FqWMHA6dKyjmRi2l8aRLxJvXJe+5C+Pms2da39p+GhaIcVJbYKuqufNXzr52h3trHBQ2nsVIjp7yTzzt61CLr41NdPf/J4v+hR+6tV9kuO99zpU0RS0Ziz2C7PSA6jVNwZCjnagch+NT226du7cLcrVM9wD7JTyP41iNOAYbqwImPyea5TyrH7EopPWiFT5BgbvaU+3f6VWKil31VY2e1XM0vbQw2lS33nF5CEJGSen4eJ5VI9V9VVqpx21aZk9zT0F0Fllf8AWVpPJSx0T8B1Pr8K6PTarMmzu+3sr32Rrh/kh3EvU51bquRdW4jcGJktxIrY5MtAnanPieeSfEk1Ga4rmvYpJLSOEdaUpUgUHWlKAyumrPOv98iWm2tFyVIXhPkkAZKj5AAEk+QrejSSNrcdvcTsbQgk9VEJAKvnjNUfwZ0n/RyzpmSGluXW5NhTwCebLJ5pbBxnceSlYP6I8DV46X3JUjcgjPnXl+uZKm1CPo7ODS4x5P2T9v8A+Xj4VB9S9VVNUOtCB3nUDl+kKg+pXmiVbXEH9oV59RLxDJwbUl1LhUEn3sHw8awkNGhELSlifcyB1ykGs5LwQsjnUC1Vo+JcFKkNMvxZKge+x0J9U9K6VHFrUnoyk2l2JxERptP5iTKVjrkVl4jkNpQS05nzyofzrWi/ac1DaSVLL7rI59ohSjgeZHhWDTKlf/VPj4LNdBdOVse0is7mjc6CZqkpVHbbOOveKqyiXLyE95lgftVFeFPEKJZ+GGnLaEoXKdSlLqyn3G9+1R58yrvfgavbha6bloxlmdtfmQ1uRH1nmSpCiMn4jB+dY/hnLxIysyJ1xUmuxVrrsvP9YDY8tvOviUsue+pf7NYW46LvFzkXjTUPeH7Xde0adU4QlLDozkn0wk4qX2fRcfStuR2Ly5k1ZHavuKyVY54T5D08fE4rGHQ5N+Tdbk0xr3y7mHWLQBhx99KvEbc/xrqhnTiuq5n92o1xyjLYt6rtbpCUSbXKauLIQrkppwZJx44WlI/bJ8RVP/SKRKTsu8GTJZaTKKklpxQSpmSgPI6cuSw6P/arC6BLy5HO/J69GxqGdMpHJ6aP2f8AnXoQzaEjDPtR88itCmdVamZz2WobujPXbNcGfxruNY6t/wDue9f6+7/ip+BX8zCXUeXo3yCSOTQz5Z5E1zm7AjY1HPxrQwax1XnP9Jb1/r7v+KuTrPV3/wB0XwfC4O/4qldBS/vMfv2b7FzVacBiLBUT1BVRDvEcfmIFn9dyzWhC9YasWMK1Nej8Zzp/4q+Y1RqMf94Lv/rrn86ldCS/u/0YvPfwb3zn+Khd7tvsp/8Ayn+deNx/iccdrAs48sLNaNK1LqFXvX+6q+Mxw/xrqjUmoU+7fbmPPEtf86n8Gv5f6IWfL4N3XVa+OQ9EtY8sLUf4151HVhx2kaHWmA1ZqgElOpbynPlOc/nXcay1b46ovf8Ar7v+Kn4Nfy/0bF1DXlG4jovXLtY7Q8uZr5NiRv8ArGxu8dlafnVmqT/3mvPznOfzr5r1LqJeA5f7qseSpbh/jT8Iv5f6Ml1P/Buixu8UqT8ay8TvlQ6YOK16+j23NEd3UVynyFw0OuylIcdKtyYyNxPM+K3UD1INXNwNZLFuiyZLynVuvvXR9K1Dnt5Njny97cOviPAmtcv/AB+T8MzXVF7RN4pTsAUpKcedewKjqHfcWP7NeC9aIj6ptm5EpcOY1kNuoyArryUPEcz15j1FR3T2lLrAu+ndK3JKyqVcVzJKwolK22xyGfIgK5VofQ2vZeqyarIt77kseZtIH1qpQz5JrwSEab+25NGfNGKsXi1JTbdKIixCliXNkNsNLQkApBUCo/JINUtr7iRDu/Dm7IDaI81tK9obGNyTkIUPXA5j+dPw2v7jTDInODml2R7pY0eTuVJljP8AmxWAuDegyT2k24/soFapKmSlJ70l0/tmsxY9P6ivBQqOiShg/wCVWVBP/Osvxca1uUiY3OXkvqexw1Od867/ALKBXqtyIyWEiCtaooADKljvFPhn1xUD0xoeNBUmRMTJlvp6dpnaPlU7hJ2fZ2gdBjFUcjjH9YvZZg/ZN9O/YqexSfYDVf6ddaGwKdQP2hU9iOtGAdrqD+0K5so6MJ95EL1JsEjK07khXMA4JHx8K0W11Y5WntUTbXKJUptwlLhH5xB5pV8x/Gt5dTFSnF7UKPI9BVNcUNGf0ugmIGyi6xwpcBahgOK6qaJx9rHLwCseZrudFyo1S4S9lHMpc47Xo1hzXNd3m1tOKbWkpUklKgfAjqK6V6w4x1pSlAcjrUh0FPs1s1ExcL5GXJjRwXENBsLSp0e4FAkZTnmR44qO1yaA2bt/0kjHQlbrr7ricDamC2kn/axX1P0kLC+nMy0XN7HglDaB+Cq1fFc+FUJ9Mx5vcolpZdi8M2Rmce9ESOStKXXGPe9rGfuzisVL4qcN39zn5FvbbngAsH/jqgxQioXS8ZeIk/e2/JsDD426bhEiLbrsAP0ko/xVlP8A4lUJb7FLM4I8jGaP/FWtJrip/GY/8SHmWv2bBy+P7MptSVsSwD4eztn/AIqjPtemdby1pY3W+eCnH1AQHEk4Uo7SR3c5PQ4zVSZrOaEmex6tt6ytxDTjwZe7M8y2vuqH3GtsMOqC1FaI+7s9suuDGl2dbtnluBci3OGMpSehCehHoRg1tzwD9rcgPznU/wBVuDLMho5/ymza5+KQfnWuvscK4a70/KmlKWLxFaXIz0W8z9U6n/ZBNbc6c7BqNGajNobabIbSlAwACBgVNdSjNtHRzc2NuNGHs9NzYQzMKw2kduk7seKh0P41XXETUtq07aluTnwXSkhthPNTny8vwqU8ar1c9OaJevdpYadkxnUZ7QZASTg/wrUPXMuTM1TMkSpLsguqDja3Dk7FDcn8DXc6fhrIlt+DzuRc4LsSmbc5OqmI0p5I3S2JFtKdxOV5DjI5+JP7qhOrIzN94PNtuIQqSxCfi9orJ2uxVe0IOPMtFxAz51nNAsTbgibBj9olLKmpodbRuKHG1YAHmSlaviQK+aWW252s7QO8iK41eYyEkfm0qHagdR+bWfPoPOtvUo106hEwx25d2apimayGo4S7XfJttcSQYshxoAnJwlRArwVx/BbOtcigoaA4pSlAKUpQClKUAzXIrisxo22NXjU1vtr6yhh59IeUOqWxzWr5JBPyoC99MtvW/hT7OEdmuU3GtaAlON5UsyHT8e8lJ+AqfxL3/RpmXNjL3pQWLS0noFpaTueUPXd/vGsI0r2m+aRtKxjsoz17mI64U8VKTnPQhCUj5ivPraLLt6bfCkoV+aU/vxgOKcVnIzjntCM11emcJ7jL2VcmTh3Rsdw71DaL/aESLc8guAAOMA5Ug+WOuPwqwrRGQqWp1QCiwjswSPHxrSjQE6XbtURpsSS5H7Dc84pCsbkoSVEHzBxW3nBu73G/aDhXe6sttSpW5xQRnBGcA8/hTqWCqHzXsjHyXJaRGfpACWiKm57CYtuiPrG3me2cAbSQPQKUa1UlWyRqB9qzRnG2Xpyw12i+iUjvEnHgAmt3NUhiTBltSUJcjulSdihnckDH781qGzGTC1bqN+3K3JgxVR2MHOHpKw2jB8cJJPwrhTrbltHpsLNhVjyi/OipHXtP6LurUe4pXc5hbDx+oQtDYVzTyURzKcK+BFS2Fx4jRW0JbZlgAYwIzWP96qd4gTfb9Z3R8HuCQptv6zfhtHcQAfIJSAPQCsEKTxYW/wBSOb91Z6Nlh9JVAb7NTUxYPXMVr/FWNn8crDP3e1W+5q3eTSB/xVr0edMVoXTMdf2k/dW/JfCOKPD5Ki8ux3pbp8nEpH+/Xuh8c9HRlBA0lPUj9L2zn91a9Uo+l48vMQ8u1+zaFj6R+mY6sw7Td2D5qDa8feqvY/8ASJt0iOXWr2uMvwbdtm4j5jIrVHFKhdKxk9qJH3VvyTHi1e7PqHVZu9pYbbMhlCpam2eyQ4/z3LCfAnlnzOT41D6Uq+lpaK7e2daUpUkClKUApSlAKUpQClKUArlJKVBQOCK4pQG0cCYmboS06khrQRbJ7MtIbyEoblIw6nzwh9tac+eTVxJ4hqvkiTpO1Odnm3rdafSratchsBxKQfAEJIx61rNwpvoi8PJ8a6KV+TpDEm3I6qIcGx9r4ALK/wC+qpRw+uzkS+2a6NkqcakNKIB6jIBHzGR866HT8eNvPl6Rpuk14N17wwxrPhs+0nBTc7aSnPRKlIyB8jWtWlOGN31V7FNmBUGG22Y763E4W5sUQFIHj3cDNbLcNbfLtWnTa5i0rDEl32cjr2CllTefXBrw6pu1qsEh5d2ucOE0TvSXnUp5H41rryp0NqHhmDrViTZAXtNW2w29Fvt8ZSIwOxzAJKwrkST4k/eegwMmtduJV9csGsWpNt7FyQYrsV9ChuS4hQKSDj0KfmOXLFXLxG4kQ7lbnWNKMOTHSCn254FmM2DyJ3rxnl5daoT8lQ23ZFxuU1NwfcUXHJUgFuKhR8Up5KdPokYqpZbKx7kWIRjFaRXmrraxeIL14ZaVGnxWG1SUZyh5sYR2g8QrOM9c8zy8YHWyt6g2qx2eHP2x56brFStUqQg/1hp1CkOtFtJylKRjGCCDjHPFUtxJ04zp69BmMXDHcCsBfPYtKiFJCsDd4HOB1x1FYktkRpXPnQdKkHFKUoBSlKAUpSgFWFpq2NWG3IuUlgvT5sRRZQQQIqFnaHCOpURnHgAoHnmvDws01G1BdFOTELdjsOISWUnaHFK3EBSuoThKicczjAxnIuS2sQ9SWq46glGPBVb2S57WygkISkobaY7JR5tlAHL0qGwc8ML05f8AWE+fP7BuZKQ2yhDaQlKGkgDalPwSBz/S9a2GTpy26ngri3NjtGue1STzbwcZSTzGDy8xjCh0NayNWeCXY90tkxNskoIUJDOXITiumc+81nxSoVf/AA/4jwIdsRG1Y0qA6MD2xOXoznLAIcTkDp0POprslB7REoqS0yIal4cX3S3taIqDPjTS3GafaTkpSpYPeHh7oGenerZeY4zorhwtSUjZardtbT03KSnAB+KsffXk0lcLXe3kO2+dGmM+9uZdSsHHwNe3iPbl3azR4PL2cym3pXmpps71JHx2gVcszJ5HGM/RpjSq02ilH+IxtMh7R9yJe9kgNo7dWSr2jZuWFKPqoj0xVQy70mzcPHr653ZtwlTbsFYz+aT2MfHmO1Xn5GsPrS8OSp93ujgKXXnnHefhuUe78qwvGO6xHNAQlWwqXBWI1rYWRtUOwb7V7Kf1nHEc/wBU9a2Z1MKuPH2hVJy8lG0pSuebxSlKAUpSgFKUoBSlKAUpSgFKUoBSlKAUpSgFKUoBSlKAtrRunZtz4f2eU0Gyw9NmJO9wIGWktKPePL3VeNTvROm9Uwp0eTZ2LmqQgdqx7OmO6AnONyd5wR645Goxol9L/D+0NQJsVqfCUtLQd7qNxW6XUEkbd5StondyKQBnlire4dSrvaL32Nrd0iw3DjluPLekuJadSsha04StWCD4cvSpjJxe0arCeW7iFxNh3WNbzpkKnyoyGmk3G4IQHC0O86EoTyJzz51xf9Ha11ff2b1qibp+2SQ2I6Fw4QfcSkEkYLoIByTzAzUY1hqK+vX6yvzdUaQ+odXiTBUVrjbk4zsWsbgenQ/Cu0yZGuqQl/UuttXqHL2e2Q/ZmPgVYTy+CqeTDlrsevWuj9DaetM1+ZqBT9+LKxGenyEvrDmDt2tEFI5+SfhVSydDagTZDqGbBk3NQIPbXF0stDPglKjlQHrtAx0NXVpjTWplBSrNpCx6VStPKVPWZswnzGOWfiarHiC1qlrU8q1XK5MSXGlDZcZznagAgH6plIxnn+icY61DRmpHl0JDvC5ciQzKamTpUVbW9xKexaZQNxDKDjtCNvIJASPWqq43OOoEG27XzGjSpK2nXzlZU4iOpaFHxKVZz6k1ZdjhSGHbnPj3WQq4Q4a3luOrAmraHJSW0DKWhg8yolWOgqtuOi0viwJZ2hqBGet+88lOqS+t8OK9S3IaGfEpPlWJmVbSlKyMhSlKAUpSgFKUoC3eBTUWRBmsqckh0y23ilhQSrc2y6WgknqorJ5fq48asbXkC8xr2lb78SFPjRkRnAkD2R5sjI7RPRCiCMpWNuehFVZwPgvvM3VS+1biPLZacWg4KOzKn1rSfBSUNHn4bvWrO1Pb3xcIcmRdXRcpMVuQp1lWZSEKSNoeaOA5gAc0c8dRUMxkeZnQ9+YsrWoIMGbad4J7WAVPR+vPcgEqTy/tAirh0tovQl/tjMqyagXFuvZJ7d6BIS0SvHe3MgbOueW2q+4ZM6ol6pbtdpubEBa0qX7dCfw2sAe65HUMZ59NqTVjag03fWwk3zRdm1NtHOVanPZJQHmUnlnn4KqUjXKbXg92nNK600Xd3rtpaXpy5PPNltapcP2da07sjJa7pPrivlfNf8SrndZ0BjT6mJ0eN7Mv8mTkOJaWshQc7NxPNWAQM8sGo63cWLYVIZ1frDSis82LpE9oZSPLcQrl+1XOh9R35mfd3YWp9GqMl/eXZpU25K5e/tQshI8MYqV2I5v2Vbq/TWqJU2XKvEW6NuqIdfMgsMJTuONxKTjmR1xUM1lpida+G13my8Bhq5xGkIDocCVracXkEcs7Skcv4VdPEKVeLten48+RpKS3LjpU7LZkLU22WtxQ2ApaQSSTy5jnzqo+IbvZ6DmKmSmZD8l0KkLbOW1vb0ltKcct6Udpkp5BJA51MpOXkzgtlKmuKUrE2ClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUBPOFepk2WeIUpQMd15LrJUe627goOc5wFJUQTjqEnoKv/SrkBiTBVcdNTbwmPLfS+BbWnS+nkAneg4UUnJCsAEGtRqvu0XuSrT9g1I4txTsV+PKKuWVgHsnc48MtA/tetDBrZeF7ehXiyhnSfDi9W51LqHEykwWo4wkjIJKgMEDFSSx6m1vqa19rp+xWKLFCi0ZL83tglSeRACBjPzNZTg29/wDw/wDJ6lZVb5TsZHq3u3NH5oUmuvDlabfdNT6YVtR7BcvaY7aR3exkAOAj9oLqUitN6ejzx9IaougJ1JraWpA5Fi2o9nQfQqyVEfMVr1x5s1y0Pqc263zS1CnM9q062ja6vngpWrJUo9PGtv08n1DHIjmKoL6ZkWObHYJh2pkJkOthR8QUgn9wozOvuyleDc5MXiPbUyApceetUOSCclSHQUn99d+M1tTH0UlUgq9oQtAJT7pcadejEn4obb+415+GNsW5qSFen1dlAt76X3HlA4UpJylCfFSiR0HOsLxk1ii6OKtMNzcyHNzgGCEAFagnPiSpxxascsqA54rEsNFYUpSpJFKUoBSlKAUpSgL44TwUL0Pa4MXPbXJ/s3DnmFPyexPy7NjH7avOvBxWuarnxFusptZDbL5YZweQQ33E/gmsbwZ1mxb3YtpuCQUtPAx1ZwrHaJcCUnzS4ncPPcseIr2a8tJg32TMjO+026Y8t6PJT7qtx3FJ8lDOCDzqGzEnPASxXHXeonYtznExILQWp9ScvAk4CUuZCk9POr/kaS1Xa9o07rKSWQeUa6tCQk+gWMKH41CPobxIiNH3eWgpMhydscHiEhA2/fk1eSj9ckY6DP31JpsepFbX7VGstPQ0o1BZLG+3IPYNvR5wbSpRzjIWMZOOmaj1gegWWwNxtU8Or1cn0Elc1yC2/nJ80qPnipvrxhV31bpXT4P1ImKuUnlyKGEd0fNa0iu3GR2OdNxoMtWI8mWgyP8AQtguuf7KMfOpMEUdqdURU2UYVgm2puTPQWULtrTBZRsOWypZ7uSConBwBWv/ABO1SdSXMJaIEZpxx3ujCS4vAJA8glKEjPl4ZqybrcVMaJvup5hSh+f7Q+wCs7lKdV2De0+YCnlY8kGqDzUeSzDsga4pShkKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQHarC4YanhRor9hu+z2N7ft3nA74AUAr7KgUoUknllODyNV7SgN3+EutIdpU01KuUd9lcdtp1YV2ayEDa2varHPZhJHjgEE1Ob5ebBH1Ixqm2X+1JfMf2WWw5KSlMhvqnmeikknHxIr8+IF7u8BhbEK6zorKyCptl9SEqI6EgHBr7tao1G0oKav10aUPFuWtJ/A1JrdSl5N+rzxh0dBjqfXIdddb95LSNw59AVe6PvrXPinxWsd/vZulxH5QWyCiLFWve2wM4OEIOCrxypWD5eFa/zZcmZIckS5D0h5w5W46srUo+pPM18BTZMa1HwS/UWvbvcUdgw4qMyAUgJwCAeoAAAQP7IFRBVcV2qDM60pSgFKUoBSlKAUpSgOcmpnprXtyt6THmAzGFYBKiFKIHgoKylY/tDPkRULrk0BsZwn4o6f05dxcLUBCLxSmTDS5sbdHnscOAoeaV459K2HtXGHRdwYL7U1bTijgIeRsH973fxr87a+0aVJjOh2PJeZcHRbaykj5ihi4J+T9FNPXqxm9TdTXDUlnelusJYZaYkJIjsg52dclRJyT8PKq44yastt8L7SbohmMllbSdig4pKFH6xe0H3iAUjJAAJya1Hc1bqd1BS9fp72eqnHipX948/xrw3C7XS4IQidc5stKBhIffUsJ+GTyoYxrSeybcT9VxbhCRYLUd0Nl1DilJOU9xBS2gHx271knxUtWOQBNd4pimKGw4pSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUApSlAKUpQClKUB//9k=';
  document.getElementById('navLogoImg').src = LOGO_SRC;
  document.getElementById('footerLogoImg').src = LOGO_SRC;
 
  // Nav scroll
  const navbar = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    navbar.classList.toggle('scrolled', window.scrollY > 60);
  });
 
  function toggleNav() {
    document.getElementById('mobileNav').classList.toggle('active');
  }
 
  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const revealObserver = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); revealObserver.unobserve(e.target); }
    });
  }, { threshold: 0.07, rootMargin: '0px 0px -28px 0px' });
  reveals.forEach(el => revealObserver.observe(el));
 
  // Lightbox
  function openLightbox(src) {
    document.getElementById('lightboxImg').src = src;
    document.getElementById('lightbox').classList.add('active');
    document.body.style.overflow = 'hidden';
  }
  function closeLightbox() {
    document.getElementById('lightbox').classList.remove('active');
    document.body.style.overflow = '';
  }
  document.addEventListener('keydown', e => { if (e.key === 'Escape') closeLightbox(); });
 
  // Contact form
  function submitForm() {
    const name  = document.getElementById('fname').value.trim();
    const email = document.getElementById('femail').value.trim();
    const phone = document.getElementById('fphone').value.trim();
    const msg   = document.getElementById('fmessage').value.trim();
    if (!name || !email || !msg) {
      alert('Please fill in your name, email address, and message.');
      return;
    }
    const to      = 'Imperialbarbershop44@gmail.com';
    const subject = encodeURIComponent('Appointment Inquiry — Imperial Barber Shop');
    const body    = encodeURIComponent(
      'Name: ' + name + '\n' +
      'Email: ' + email + '\n' +
      'Phone: ' + (phone || 'Not provided') + '\n\n' +
      'Message:\n' + msg
    );
    window.location.href = 'mailto:' + to + '?subject=' + subject + '&body=' + body;
    document.getElementById('formMsg').style.display = 'block';
  }
</script>
</body>
</html>
