<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Don Navaja — Barbearia</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=Barlow:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  :root {
    --cream: #F5F0E8;
    --ink: #1A1410;
    --gold: #C9A84C;
    --gold-light: #E8C96A;
    --rust: #8B3A2A;
    --warm-gray: #6B6560;
    --light-bg: #FAF7F2;
    --border: #D4C9B8;
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Barlow', sans-serif;
    background: var(--light-bg);
    color: var(--ink);
    overflow-x: hidden;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.2rem 5%;
    background: rgba(26,20,16,0.96);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid rgba(201,168,76,0.2);
  }

  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem;
    font-weight: 900;
    color: var(--gold);
    letter-spacing: 0.05em;
    text-decoration: none;
  }

  .nav-logo span { color: #fff; }

  .nav-links {
    display: flex;
    gap: 2.5rem;
    list-style: none;
  }

  .nav-links a {
    font-size: 0.78rem;
    font-weight: 600;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: #ccc;
    text-decoration: none;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--gold); }

  .nav-cta {
    background: var(--gold);
    color: var(--ink) !important;
    padding: 0.55rem 1.4rem;
    border-radius: 2px;
    font-weight: 700 !important;
    transition: background 0.2s !important;
  }

  .nav-cta:hover { background: var(--gold-light) !important; }

  /* HERO */
  .hero {
    min-height: 100vh;
    background: var(--ink);
    display: grid;
    grid-template-columns: 1fr 1fr;
    position: relative;
    overflow: hidden;
  }

  .hero-left {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 10rem 6% 6rem 7%;
    position: relative;
    z-index: 2;
  }

  .hero-eyebrow {
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1.5rem;
    display: flex;
    align-items: center;
    gap: 0.8rem;
  }

  .hero-eyebrow::before {
    content: '';
    display: block;
    width: 2rem;
    height: 1px;
    background: var(--gold);
  }

  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(3rem, 5.5vw, 5.5rem);
    font-weight: 900;
    line-height: 1.0;
    color: #fff;
    margin-bottom: 1.5rem;
  }

  .hero h1 em {
    font-style: italic;
    color: var(--gold);
  }

  .hero-desc {
    font-size: 1.05rem;
    font-weight: 300;
    color: rgba(255,255,255,0.6);
    line-height: 1.8;
    max-width: 380px;
    margin-bottom: 2.5rem;
  }

  .hero-actions {
    display: flex;
    gap: 1rem;
    align-items: center;
  }

  .btn-primary {
    background: var(--gold);
    color: var(--ink);
    padding: 0.9rem 2rem;
    font-family: 'Barlow', sans-serif;
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    border: none;
    cursor: pointer;
    text-decoration: none;
    display: inline-block;
    border-radius: 2px;
    transition: background 0.2s, transform 0.15s;
  }

  .btn-primary:hover { background: var(--gold-light); transform: translateY(-1px); }

  .btn-ghost {
    color: #fff;
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    text-decoration: none;
    display: flex;
    align-items: center;
    gap: 0.5rem;
    transition: color 0.2s;
  }

  .btn-ghost:hover { color: var(--gold); }

  .btn-ghost::after {
    content: '→';
    font-size: 1rem;
  }

  .hero-right {
    position: relative;
    overflow: hidden;
  }

  .hero-bg-pattern {
    position: absolute;
    inset: 0;
    background:
      repeating-linear-gradient(
        45deg,
        transparent,
        transparent 30px,
        rgba(201,168,76,0.04) 30px,
        rgba(201,168,76,0.04) 31px
      );
  }

  .hero-image-block {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .barber-pole {
    width: 80px;
    height: 400px;
    position: relative;
    border-radius: 40px;
    overflow: hidden;
    box-shadow: 0 0 60px rgba(201,168,76,0.3);
    background: #fff;
  }

  .pole-stripe {
    position: absolute;
    width: 200%;
    height: 200%;
    top: -50%;
    left: -50%;
    background: repeating-linear-gradient(
      60deg,
      #CC2936 0px,
      #CC2936 20px,
      #fff 20px,
      #fff 40px,
      #1B4FD8 40px,
      #1B4FD8 60px,
      #fff 60px,
      #fff 80px
    );
    animation: spin 4s linear infinite;
  }

  @keyframes spin {
    to { transform: translateY(50%); }
  }

  .pole-cap {
    position: absolute;
    left: 0; right: 0;
    height: 50px;
    background: var(--ink);
    z-index: 2;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .pole-cap.top { top: 0; border-bottom: 3px solid var(--gold); }
  .pole-cap.bottom { bottom: 0; border-top: 3px solid var(--gold); }

  .hero-badge {
    position: absolute;
    bottom: 3rem;
    right: 3rem;
    width: 110px;
    height: 110px;
    border: 2px solid var(--gold);
    border-radius: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    color: var(--gold);
    animation: rotate 20s linear infinite;
  }

  @keyframes rotate { to { transform: rotate(360deg); } }

  .hero-badge-inner {
    animation: rotate-reverse 20s linear infinite;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  @keyframes rotate-reverse { to { transform: rotate(-360deg); } }

  .hero-badge-num {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    font-weight: 900;
    line-height: 1;
  }

  .hero-badge-text {
    font-size: 0.55rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    line-height: 1.3;
  }

  /* SECTION COMMON */
  section { padding: 6rem 7%; }

  .section-label {
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--gold);
    display: flex;
    align-items: center;
    gap: 0.8rem;
    margin-bottom: 1rem;
  }

  .section-label::before {
    content: '';
    display: block;
    width: 2rem;
    height: 1px;
    background: var(--gold);
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 4vw, 3.5rem);
    font-weight: 900;
    line-height: 1.1;
    color: var(--ink);
    margin-bottom: 1rem;
  }

  /* SERVICES */
  .services {
    background: var(--ink);
    color: #fff;
  }

  .services .section-title { color: #fff; }

  .services-header {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    margin-bottom: 4rem;
    flex-wrap: wrap;
    gap: 1rem;
  }

  .services-subtitle {
    font-size: 1rem;
    color: rgba(255,255,255,0.5);
    max-width: 300px;
    line-height: 1.7;
  }

  .services-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: rgba(255,255,255,0.1);
    border: 1px solid rgba(255,255,255,0.1);
  }

  .service-card {
    background: var(--ink);
    padding: 2.5rem 2rem;
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
    cursor: default;
  }

  .service-card:hover { background: #261e17; }

  .service-card:hover .service-arrow { opacity: 1; transform: translateX(0); }

  .service-num {
    font-family: 'Playfair Display', serif;
    font-size: 3rem;
    font-weight: 900;
    color: rgba(201,168,76,0.15);
    line-height: 1;
    margin-bottom: 1.5rem;
    transition: color 0.3s;
  }

  .service-card:hover .service-num { color: rgba(201,168,76,0.3); }

  .service-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.3rem;
    font-weight: 700;
    color: #fff;
    margin-bottom: 0.7rem;
  }

  .service-desc {
    font-size: 0.85rem;
    color: rgba(255,255,255,0.45);
    line-height: 1.7;
    margin-bottom: 1.5rem;
  }

  .service-price {
    font-size: 1.4rem;
    font-weight: 700;
    color: var(--gold);
  }

  .service-price span {
    font-size: 0.75rem;
    font-weight: 400;
    color: rgba(255,255,255,0.4);
    margin-left: 0.3rem;
  }

  .service-arrow {
    position: absolute;
    bottom: 2rem;
    right: 2rem;
    font-size: 1.5rem;
    color: var(--gold);
    opacity: 0;
    transform: translateX(-8px);
    transition: opacity 0.3s, transform 0.3s;
  }

  /* ABOUT */
  .about {
    background: var(--cream);
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6rem;
    align-items: center;
    padding: 7rem 7%;
  }

  .about-visual {
    position: relative;
    height: 500px;
  }

  .about-frame {
    position: absolute;
    width: 70%;
    height: 80%;
    top: 0; left: 0;
    background: var(--ink);
    border-radius: 4px;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }

  .scissors-icon {
    font-size: 5rem;
    color: var(--gold);
    opacity: 0.3;
  }

  .about-frame-pattern {
    position: absolute;
    inset: 0;
    background: repeating-linear-gradient(
      135deg,
      transparent, transparent 10px,
      rgba(201,168,76,0.06) 10px,
      rgba(201,168,76,0.06) 11px
    );
  }

  .about-accent-box {
    position: absolute;
    width: 55%;
    height: 55%;
    bottom: 0; right: 0;
    background: var(--gold);
    border-radius: 4px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 0.3rem;
  }

  .about-stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 3.5rem;
    font-weight: 900;
    color: var(--ink);
    line-height: 1;
  }

  .about-stat-label {
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: rgba(26,20,16,0.7);
  }

  .about-content p {
    font-size: 1rem;
    color: var(--warm-gray);
    line-height: 1.9;
    margin-bottom: 1.5rem;
  }

  .about-features {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    margin-top: 2rem;
  }

  .about-feature {
    display: flex;
    align-items: flex-start;
    gap: 0.8rem;
    font-size: 0.88rem;
    color: var(--ink);
    font-weight: 500;
  }

  .about-feature::before {
    content: '✦';
    color: var(--gold);
    font-size: 0.7rem;
    margin-top: 3px;
    flex-shrink: 0;
  }

  /* TEAM */
  .team {
    background: var(--light-bg);
  }

  .team-header {
    text-align: center;
    margin-bottom: 4rem;
  }

  .team-header .section-label {
    justify-content: center;
  }

  .team-header .section-label::before { display: none; }

  .team-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
  }

  .team-card {
    background: #fff;
    border: 1px solid var(--border);
    border-radius: 4px;
    overflow: hidden;
    transition: transform 0.3s, box-shadow 0.3s;
  }

  .team-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 20px 50px rgba(26,20,16,0.12);
  }

  .team-photo {
    height: 280px;
    background: var(--ink);
    position: relative;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .team-photo-pattern {
    position: absolute;
    inset: 0;
    background: repeating-linear-gradient(
      45deg,
      transparent, transparent 15px,
      rgba(201,168,76,0.07) 15px,
      rgba(201,168,76,0.07) 16px
    );
  }

  .team-photo-icon {
    font-size: 4rem;
    position: relative;
    z-index: 1;
  }

  .team-info {
    padding: 1.5rem;
    border-top: 3px solid var(--gold);
  }

  .team-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    font-weight: 700;
    margin-bottom: 0.3rem;
  }

  .team-role {
    font-size: 0.78rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.8rem;
  }

  .team-bio {
    font-size: 0.85rem;
    color: var(--warm-gray);
    line-height: 1.7;
  }

  /* TESTIMONIALS */
  .testimonials {
    background: var(--ink);
    color: #fff;
  }

  .testimonials .section-title { color: #fff; }
  .testimonials-header { text-align: center; margin-bottom: 4rem; }
  .testimonials-header .section-label { justify-content: center; }
  .testimonials-header .section-label::before { display: none; }

  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }

  .testimonial-card {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: 4px;
    padding: 2rem;
    position: relative;
    transition: border-color 0.3s;
  }

  .testimonial-card:hover {
    border-color: rgba(201,168,76,0.3);
  }

  .testimonial-quote {
    font-family: 'Playfair Display', serif;
    font-size: 4rem;
    color: var(--gold);
    opacity: 0.4;
    line-height: 0.8;
    margin-bottom: 1rem;
  }

  .testimonial-text {
    font-size: 0.92rem;
    color: rgba(255,255,255,0.65);
    line-height: 1.8;
    margin-bottom: 1.5rem;
    font-style: italic;
  }

  .testimonial-author {
    display: flex;
    align-items: center;
    gap: 0.8rem;
  }

  .author-avatar {
    width: 38px;
    height: 38px;
    border-radius: 50%;
    background: var(--gold);
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    font-size: 0.8rem;
    color: var(--ink);
    flex-shrink: 0;
  }

  .author-name {
    font-size: 0.88rem;
    font-weight: 600;
    color: #fff;
  }

  .author-stars {
    font-size: 0.7rem;
    color: var(--gold);
    letter-spacing: 0.1em;
  }

  /* BOOKING */
  .booking {
    background: var(--cream);
    text-align: center;
  }

  .booking .section-label { justify-content: center; }
  .booking .section-label::before { display: none; }

  .booking-box {
    max-width: 700px;
    margin: 0 auto;
  }

  .booking-subtitle {
    font-size: 1.05rem;
    color: var(--warm-gray);
    line-height: 1.8;
    margin-bottom: 3rem;
  }

  .booking-form {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    text-align: left;
    margin-bottom: 1.5rem;
  }

  .form-group {
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
  }

  .form-group.full { grid-column: 1 / -1; }

  .form-group label {
    font-size: 0.72rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--warm-gray);
  }

  .form-group input,
  .form-group select {
    padding: 0.9rem 1rem;
    border: 1px solid var(--border);
    border-radius: 2px;
    background: #fff;
    font-family: 'Barlow', sans-serif;
    font-size: 0.92rem;
    color: var(--ink);
    outline: none;
    transition: border-color 0.2s;
  }

  .form-group input:focus,
  .form-group select:focus {
    border-color: var(--gold);
  }

  /* FOOTER */
  footer {
    background: #110d0a;
    color: rgba(255,255,255,0.5);
    padding: 4rem 7% 2rem;
  }

  .footer-top {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 4rem;
    padding-bottom: 3rem;
    border-bottom: 1px solid rgba(255,255,255,0.08);
    margin-bottom: 2rem;
  }

  .footer-brand-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.8rem;
    font-weight: 900;
    color: var(--gold);
    margin-bottom: 1rem;
  }

  .footer-brand-desc {
    font-size: 0.87rem;
    line-height: 1.8;
    max-width: 240px;
  }

  .footer-col h4 {
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: #fff;
    margin-bottom: 1.2rem;
  }

  .footer-col ul { list-style: none; }

  .footer-col ul li {
    margin-bottom: 0.7rem;
    font-size: 0.87rem;
  }

  .footer-col ul a {
    color: rgba(255,255,255,0.5);
    text-decoration: none;
    transition: color 0.2s;
  }

  .footer-col ul a:hover { color: var(--gold); }

  .footer-bottom {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 0.8rem;
  }

  .footer-bottom a {
    color: var(--gold);
    text-decoration: none;
  }

  /* DIVIDER */
  .divider {
    width: 100%;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
    opacity: 0.3;
  }

  /* SCROLL ANIMATION */
  .fade-in {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }

  .fade-in.visible {
    opacity: 1;
    transform: translateY(0);
  }

  @media (max-width: 900px) {
    .hero { grid-template-columns: 1fr; }
    .hero-right { display: none; }
    .about { grid-template-columns: 1fr; }
    .services-grid, .team-grid, .testimonials-grid { grid-template-columns: 1fr; }
    .booking-form { grid-template-columns: 1fr; }
    .footer-top { grid-template-columns: 1fr 1fr; }
    .nav-links { display: none; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">Don <span>Navaja</span></a>
  <ul class="nav-links">
    <li><a href="#servicos">Serviços</a></li>
    <li><a href="#sobre">Sobre</a></li>
    <li><a href="#equipe">Equipe</a></li>
    <li><a href="#depoimentos">Depoimentos</a></li>
    <li><a href="#agendar" class="nav-cta">Agendar</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero" id="inicio">
  <div class="hero-left">
    <p class="hero-eyebrow">Est. 2008 — Curitiba, PR</p>
    <h1>A arte do<br><em>corte perfeito</em></h1>
    <p class="hero-desc">Tradição, precisão e estilo em cada navalha. Venha viver a experiência de uma barbearia de verdade.</p>
    <div class="hero-actions">
      <a href="#agendar" class="btn-primary">Agendar Horário</a>
      <a href="#servicos" class="btn-ghost">Ver Serviços</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="hero-bg-pattern"></div>
    <div class="hero-image-block">
      <div class="barber-pole">
        <div class="pole-stripe"></div>
        <div class="pole-cap top"></div>
        <div class="pole-cap bottom"></div>
      </div>
    </div>
    <div class="hero-badge">
      <div class="hero-badge-inner">
        <span class="hero-badge-num">15+</span>
        <span class="hero-badge-text">Anos de<br>Tradição</span>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- SERVICES -->
<section class="services" id="servicos">
  <div class="services-header">
    <div>
      <p class="section-label">O que oferecemos</p>
      <h2 class="section-title">Nossos<br>Serviços</h2>
    </div>
    <p class="services-subtitle">Cada serviço é executado com atenção total aos detalhes, usando os melhores produtos do mercado.</p>
  </div>
  <div class="services-grid">
    <div class="service-card fade-in">
      <div class="service-num">01</div>
      <h3 class="service-name">Corte Clássico</h3>
      <p class="service-desc">Corte tradicional com tesoura ou máquina, finalizado com produtos premium para um resultado impecável.</p>
      <div class="service-price">R$ 55 <span>/ sessão</span></div>
      <div class="service-arrow">→</div>
    </div>
    <div class="service-card fade-in">
      <div class="service-num">02</div>
      <h3 class="service-name">Barba Completa</h3>
      <p class="service-desc">Modelagem completa com navalha quente, toalha quente e finalização com balm nutritivo.</p>
      <div class="service-price">R$ 45 <span>/ sessão</span></div>
      <div class="service-arrow">→</div>
    </div>
    <div class="service-card fade-in">
      <div class="service-num">03</div>
      <h3 class="service-name">Combo Especial</h3>
      <p class="service-desc">Corte + barba completa com ritual de cuidados e massagem capilar relaxante incluída.</p>
      <div class="service-price">R$ 90 <span>/ sessão</span></div>
      <div class="service-arrow">→</div>
    </div>
    <div class="service-card fade-in">
      <div class="service-num">04</div>
      <h3 class="service-name">Pigmentação</h3>
      <p class="service-desc">Cobertura de fios brancos na barba ou cabelo com produtos naturais e longa duração.</p>
      <div class="service-price">R$ 70 <span>/ sessão</span></div>
      <div class="service-arrow">→</div>
    </div>
    <div class="service-card fade-in">
      <div class="service-num">05</div>
      <h3 class="service-name">Hidratação</h3>
      <p class="service-desc">Tratamento intensivo para cabelo e couro cabeludo, restaurando força e brilho natural.</p>
      <div class="service-price">R$ 60 <span>/ sessão</span></div>
      <div class="service-arrow">→</div>
    </div>
    <div class="service-card fade-in">
      <div class="service-num">06</div>
      <h3 class="service-name">Pacote Mensal</h3>
      <p class="service-desc">4 cortes mensais com fidelidade e agendamento prioritário. A melhor relação custo-benefício.</p>
      <div class="service-price">R$ 180 <span>/ mês</span></div>
      <div class="service-arrow">→</div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ABOUT -->
<div class="about" id="sobre">
  <div class="about-visual fade-in">
    <div class="about-frame">
      <div class="about-frame-pattern"></div>
      <div class="scissors-icon">✂</div>
    </div>
    <div class="about-accent-box">
      <span class="about-stat-num">8.000+</span>
      <span class="about-stat-label">Clientes atendidos</span>
    </div>
  </div>
  <div class="about-content fade-in">
    <p class="section-label">Nossa história</p>
    <h2 class="section-title">Mais que uma<br>barbearia</h2>
    <p>A Don Navaja nasceu em 2008 com uma missão simples: resgatar a cultura da barbearia clássica e oferecer um espaço onde homens pudessem se cuidar com qualidade e conforto.</p>
    <p>Ao longo de 15 anos, construímos uma reputação baseada em técnica, respeito pelo cliente e paixão pelo ofício. Cada detalhe do nosso espaço foi pensado para proporcionar uma experiência única.</p>
    <div class="about-features">
      <div class="about-feature">Profissionais certificados</div>
      <div class="about-feature">Produtos importados</div>
      <div class="about-feature">Ambiente climatizado</div>
      <div class="about-feature">Wi-Fi gratuito</div>
      <div class="about-feature">Bebidas cortesia</div>
      <div class="about-feature">Estacionamento</div>
    </div>
  </div>
</div>

<div class="divider"></div>

<!-- TEAM -->
<section class="team" id="equipe">
  <div class="team-header fade-in">
    <p class="section-label">Conheça</p>
    <h2 class="section-title">Nossa Equipe</h2>
  </div>
  <div class="team-grid">
    <div class="team-card fade-in">
      <div class="team-photo">
        <div class="team-photo-pattern"></div>
        <div class="team-photo-icon">✂️</div>
      </div>
      <div class="team-info">
        <h3 class="team-name">Ricardo Souza</h3>
        <p class="team-role">Barbeiro Master</p>
        <p class="team-bio">Fundador da Don Navaja com 20 anos de experiência. Especialista em cortes clássicos e técnicas de navalha europeia.</p>
      </div>
    </div>
    <div class="team-card fade-in">
      <div class="team-photo">
        <div class="team-photo-pattern"></div>
        <div class="team-photo-icon">💈</div>
      </div>
      <div class="team-info">
        <h3 class="team-name">André Lima</h3>
        <p class="team-role">Especialista em Barba</p>
        <p class="team-bio">Mestre em modelagem de barba, André combina técnica tradicional com tendências contemporâneas do estilo masculino.</p>
      </div>
    </div>
    <div class="team-card fade-in">
      <div class="team-photo">
        <div class="team-photo-pattern"></div>
        <div class="team-photo-icon">🪮</div>
      </div>
      <div class="team-info">
        <h3 class="team-name">Felipe Martins</h3>
        <p class="team-role">Colorista & Estilista</p>
        <p class="team-bio">Formado em cosmetologia com especialização em coloração masculina e tratamentos capilares avançados.</p>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- TESTIMONIALS -->
<section class="testimonials" id="depoimentos">
  <div class="testimonials-header fade-in">
    <p class="section-label">O que dizem</p>
    <h2 class="section-title">Depoimentos</h2>
  </div>
  <div class="testimonials-grid">
    <div class="testimonial-card fade-in">
      <div class="testimonial-quote">"</div>
      <p class="testimonial-text">Melhor barbearia de Curitiba, sem dúvida. O Ricardo tem uma habilidade incrível e o ambiente é muito acolhedor. Nunca saio daqui sem um sorriso no rosto.</p>
      <div class="testimonial-author">
        <div class="author-avatar">MP</div>
        <div>
          <div class="author-name">Marcos Pereira</div>
          <div class="author-stars">★★★★★</div>
        </div>
      </div>
    </div>
    <div class="testimonial-card fade-in">
      <div class="testimonial-quote">"</div>
      <p class="testimonial-text">Frequento a Don Navaja há 4 anos. O atendimento é sempre excelente e o resultado do corte supera as expectativas. Recomendo a todos os amigos.</p>
      <div class="testimonial-author">
        <div class="author-avatar">LB</div>
        <div>
          <div class="author-name">Lucas Borges</div>
          <div class="author-stars">★★★★★</div>
        </div>
      </div>
    </div>
    <div class="testimonial-card fade-in">
      <div class="testimonial-quote">"</div>
      <p class="testimonial-text">O combo corte + barba é simplesmente fantástico. O André domina a navalha como poucos. Saí completamente transformado na primeira visita.</p>
      <div class="testimonial-author">
        <div class="author-avatar">GC</div>
        <div>
          <div class="author-name">Gabriel Costa</div>
          <div class="author-stars">★★★★★</div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- BOOKING -->
<section class="booking" id="agendar">
  <div class="booking-box">
    <p class="section-label">Reserve sua vez</p>
    <h2 class="section-title">Agendar<br>Horário</h2>
    <p class="booking-subtitle">Escolha o serviço, o profissional e o horário que preferir. Confirmação imediata por WhatsApp.</p>
    <div class="booking-form">
      <div class="form-group">
        <label>Nome completo</label>
        <input type="text" placeholder="Seu nome">
      </div>
      <div class="form-group">
        <label>WhatsApp</label>
        <input type="tel" placeholder="(41) 9 0000-0000">
      </div>
      <div class="form-group">
        <label>Serviço</label>
        <select>
          <option>Corte Clássico — R$ 55</option>
          <option>Barba Completa — R$ 45</option>
          <option>Combo Especial — R$ 90</option>
          <option>Pigmentação — R$ 70</option>
          <option>Hidratação — R$ 60</option>
        </select>
      </div>
      <div class="form-group">
        <label>Profissional</label>
        <select>
          <option>Ricardo Souza</option>
          <option>André Lima</option>
          <option>Felipe Martins</option>
        </select>
      </div>
      <div class="form-group">
        <label>Data</label>
        <input type="date">
      </div>
      <div class="form-group">
        <label>Horário</label>
        <select>
          <option>09:00</option>
          <option>09:30</option>
          <option>10:00</option>
          <option>10:30</option>
          <option>11:00</option>
          <option>14:00</option>
          <option>14:30</option>
          <option>15:00</option>
          <option>15:30</option>
          <option>16:00</option>
          <option>17:00</option>
          <option>17:30</option>
          <option>18:00</option>
        </select>
      </div>
    </div>
    <button class="btn-primary" style="width:100%; padding: 1.1rem; font-size: 0.85rem; border-radius: 2px;">Confirmar Agendamento</button>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-top">
    <div>
      <div class="footer-brand-name">Don Navaja</div>
      <p class="footer-brand-desc">Barbearia tradicional desde 2008. Tradição, técnica e estilo em cada corte.</p>
    </div>
    <div class="footer-col">
      <h4>Serviços</h4>
      <ul>
        <li><a href="#">Corte Clássico</a></li>
        <li><a href="#">Barba Completa</a></li>
        <li><a href="#">Combo Especial</a></li>
        <li><a href="#">Pigmentação</a></li>
        <li><a href="#">Pacote Mensal</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Horários</h4>
      <ul>
        <li>Seg – Sex: 9h – 20h</li>
        <li>Sábado: 9h – 18h</li>
        <li>Domingo: Fechado</li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Contato</h4>
      <ul>
        <li><a href="#">(41) 99999-9999</a></li>
        <li><a href="#">@donnavajapr</a></li>
        <li>R. XV de Novembro, 123<br>Curitiba – PR</li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <span>© 2024 Don Navaja. Todos os direitos reservados.</span>
    <span>Feito com ✦ em Curitiba</span>
  </div>
</footer>

<script>
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 80);
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));

  document.querySelector('.booking-form').closest('section').querySelector('.btn-primary').addEventListener('click', function() {
    const name = document.querySelector('input[placeholder="Seu nome"]').value;
    if (!name.trim()) {
      alert('Por favor, informe seu nome para continuar.');
      return;
    }
    this.textContent = '✓ Agendamento Confirmado!';
    this.style.background = '#2a7a4b';
    this.style.color = '#fff';
    setTimeout(() => {
      this.textContent = 'Confirmar Agendamento';
      this.style.background = '';
      this.style.color = '';
    }, 3000);
  });
</script>

</body>
</html>
