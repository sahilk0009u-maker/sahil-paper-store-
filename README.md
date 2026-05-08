<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Sahil Paper Store – Scrap & Waste Dealers</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --rust:    #E8000D;
      --dark:    #FFFFFF;
      --paper:   #111111;
      --sand:    #444444;
      --green:   #CC0000;
      --charcoal:#FFF8E1;
      --white:   #222222;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'DM Sans', sans-serif;
      background: #FFFFFF;
      color: var(--white);
      overflow-x: hidden;
    }

    /* ── NAV ── */
    nav {
      position: fixed; top: 0; width: 100%; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 18px 5%;
      background: rgba(255,255,255,0.96);
      backdrop-filter: blur(10px);
      border-bottom: 2px solid rgba(232,0,13,0.30);
    }
    .nav-logo {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.7rem;
      color: var(--rust);
      letter-spacing: 2px;
    }
    .nav-logo span { color: #555555; }
    .nav-links { display: flex; gap: 32px; list-style: none; }
    .nav-links a {
      text-decoration: none; color: #555555; font-size: 0.88rem;
      font-weight: 500; letter-spacing: 1px; text-transform: uppercase;
      transition: color .25s;
    }
    .nav-links a:hover { color: var(--rust); }
    .nav-cta {
      background: var(--rust); color: #fff;
      padding: 9px 22px; border-radius: 3px;
      text-decoration: none; font-weight: 600; font-size: 0.85rem;
      letter-spacing: 1px; text-transform: uppercase;
      transition: background .25s;
    }
    .nav-cta:hover { background: #a83a12; }

    /* ── HERO ── */
    .hero {
      min-height: 100vh;
      display: flex; flex-direction: column; justify-content: center;
      padding: 120px 5% 80px;
      position: relative; overflow: hidden;
      background: #FFF9E6;
    }
    .hero::before {
      content: '';
      position: absolute; inset: 0;
      background:
        radial-gradient(ellipse 60% 70% at 80% 50%, rgba(232,0,13,0.10) 0%, transparent 70%),
        repeating-linear-gradient(
          45deg,
          transparent,
          transparent 40px,
          rgba(232,0,13,0.04) 40px,
          rgba(232,0,13,0.04) 41px
        );
    }
    .hero-badge {
      display: inline-block;
      background: rgba(232,0,13,0.10);
      border: 1px solid var(--rust);
      color: var(--rust); font-size: 0.75rem; font-weight: 600;
      letter-spacing: 3px; text-transform: uppercase;
      padding: 6px 16px; border-radius: 2px;
      margin-bottom: 28px; width: fit-content;
      animation: fadeUp .6s ease both;
    }
    .hero h1 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(3.5rem, 9vw, 8rem);
      line-height: .95; letter-spacing: 2px;
      color: var(--paper);
      animation: fadeUp .7s .1s ease both;
    }
    .hero h1 .accent { color: var(--rust); }
    .hero-sub {
      margin-top: 24px; max-width: 520px;
      font-size: 1.05rem; line-height: 1.75;
      color: #555555; font-weight: 400;
      animation: fadeUp .7s .2s ease both;
    }
    .hero-btns {
      display: flex; gap: 16px; margin-top: 40px; flex-wrap: wrap;
      animation: fadeUp .7s .3s ease both;
    }
    .btn-primary {
      background: var(--rust); color: #fff;
      padding: 14px 34px; border-radius: 3px;
      text-decoration: none; font-weight: 600;
      font-size: 0.9rem; letter-spacing: 1px; text-transform: uppercase;
      transition: all .25s; border: 2px solid var(--rust);
    }
    .btn-primary:hover { background: transparent; color: var(--rust); }
    .btn-outline {
      background: transparent; color: var(--sand);
      padding: 14px 34px; border-radius: 3px;
      text-decoration: none; font-weight: 500;
      font-size: 0.9rem; letter-spacing: 1px; text-transform: uppercase;
      border: 2px solid rgba(180,0,0,0.35);
      transition: all .25s;
    }
    .btn-outline:hover { border-color: var(--sand); color: var(--white); }

    /* big decorative text */
    .hero-deco {
      position: absolute; right: -2%; bottom: -5%;
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(8rem, 20vw, 20rem);
      color: rgba(232,0,13,0.08); user-select: none;
      line-height: 1; letter-spacing: 4px;
      animation: fadeUp .9s .4s ease both;
    }

    /* ── STATS BAR ── */
    .stats {
      background: var(--rust);
      display: flex; justify-content: space-around; flex-wrap: wrap;
      padding: 28px 5%; gap: 16px;
    }
    .stat { text-align: center; }
    .stat-num {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 2.2rem; color: #fff; letter-spacing: 2px;
    }
    .stat-label { font-size: 0.78rem; letter-spacing: 2px; color: rgba(255,255,255,0.85); text-transform: uppercase; }

    /* ── SECTION SHARED ── */
    section { padding: 90px 5%; }
    .section-tag {
      font-size: 0.72rem; font-weight: 600; letter-spacing: 4px;
      text-transform: uppercase; color: var(--rust); margin-bottom: 14px;
    }
    .section-title {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(2.2rem, 5vw, 4rem);
      color: var(--paper); line-height: 1.05; letter-spacing: 1px;
      margin-bottom: 16px;
    }
    .section-desc { color: #555555; line-height: 1.75; max-width: 580px; font-weight: 300; }

    /* ── MATERIALS ── */
    .materials { background: #FFF3CD; }
    .materials-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 2px; margin-top: 52px;
    }
    .material-card {
      background: #FFFFFF;
      padding: 36px 28px;
      position: relative; overflow: hidden;
      transition: transform .3s, background .3s;
      cursor: default;
    }
    .material-card::after {
      content: '';
      position: absolute; bottom: 0; left: 0;
      height: 3px; width: 0;
      background: var(--rust);
      transition: width .35s ease;
    }
    .material-card:hover::after { width: 100%; }
    .material-card:hover { background: #FFF3E0; transform: translateY(-4px); }
    .mat-icon { font-size: 2.4rem; margin-bottom: 18px; display: block; }
    .mat-name {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.35rem; letter-spacing: 1px;
      color: #111111; margin-bottom: 8px;
    }
    .mat-desc { font-size: 0.82rem; color: #555555; line-height: 1.6; }

    /* ── HOW IT WORKS ── */
    .how { background: #FFFFFF; }
    .steps {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 40px; margin-top: 52px;
    }
    .step { position: relative; padding-left: 0; }
    .step-num {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 4.5rem; color: rgba(232,0,13,0.20);
      line-height: 1; margin-bottom: 4px; letter-spacing: 2px;
    }
    .step-title {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.4rem; color: var(--paper);
      letter-spacing: 1px; margin-bottom: 10px;
    }
    .step-text { font-size: 0.88rem; color: #555555; line-height: 1.7; }

    /* ── WHY US ── */
    .why { background: #FFF3CD; }
    .why-grid {
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 3px; margin-top: 52px;
    }
    .why-card {
      background: #FFFFFF;
      padding: 34px 30px;
      display: flex; gap: 20px; align-items: flex-start;
      transition: background .25s;
    }
    .why-card:hover { background: #FFE0E0; }
    .why-icon { font-size: 1.8rem; flex-shrink: 0; margin-top: 4px; }
    .why-title { font-family: 'Bebas Neue', sans-serif; font-size: 1.25rem; letter-spacing: 1px; color: var(--paper); margin-bottom: 8px; }
    .why-text { font-size: 0.84rem; color: #555555; line-height: 1.65; }

    /* ── ECO BANNER ── */
    .eco {
      background: #CC0000;
      padding: 70px 5%; text-align: center;
    }
    .eco h2 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(2rem, 5vw, 4rem);
      color: var(--paper); letter-spacing: 2px; margin-bottom: 16px;
    }
    .eco p { color: rgba(240,232,213,0.8); max-width: 560px; margin: 0 auto 32px; line-height: 1.75; }

    /* ── CONTACT ── */
    .contact { background: #FFFFFF; }
    .contact-wrap {
      display: grid; grid-template-columns: 1fr 1fr; gap: 60px;
      margin-top: 52px; align-items: start;
    }
    .contact-info { display: flex; flex-direction: column; gap: 28px; }
    .contact-item { display: flex; gap: 16px; align-items: flex-start; }
    .contact-icon {
      width: 44px; height: 44px; border-radius: 4px;
      background: rgba(232,0,13,0.10); border: 1px solid rgba(201,75,26,0.3);
      display: flex; align-items: center; justify-content: center; font-size: 1.2rem;
      flex-shrink: 0;
    }
    .contact-label { font-size: 0.72rem; color: var(--rust); letter-spacing: 2px; text-transform: uppercase; margin-bottom: 4px; }
    .contact-val { font-size: 0.95rem; color: var(--paper); font-weight: 400; }
    .whatsapp-btn, .maps-btn {
      display: flex; align-items: center; gap: 10px;
      padding: 13px 22px; border-radius: 4px;
      font-family: 'DM Sans', sans-serif; font-size: 0.92rem;
      font-weight: 600; text-decoration: none;
      transition: transform .2s, opacity .2s;
      width: fit-content;
    }
    .whatsapp-btn:hover, .maps-btn:hover { transform: translateY(-2px); opacity: 0.88; }
    .whatsapp-btn { background: #25D366; color: #fff; }
    .maps-btn { background: #4285F4; color: #fff; }

    /* form */
    .contact-form { display: flex; flex-direction: column; gap: 14px; }
    .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }
    .form-group { display: flex; flex-direction: column; gap: 6px; }
    label { font-size: 0.75rem; letter-spacing: 2px; text-transform: uppercase; color: #555555; }
    input, textarea, select {
      background: #FFFDE7;
      border: 1px solid rgba(232,0,13,0.25);
      border-radius: 3px; padding: 12px 14px;
      color: #111111; font-family: 'DM Sans', sans-serif;
      font-size: 0.9rem; outline: none; width: 100%;
      transition: border-color .25s;
    }
    input:focus, textarea:focus, select:focus { border-color: var(--rust); }
    textarea { resize: vertical; min-height: 110px; }
    select option { background: var(--charcoal); }
    .submit-btn {
      background: var(--rust); color: #fff;
      border: none; padding: 14px; border-radius: 3px;
      font-family: 'DM Sans', sans-serif; font-size: 0.9rem;
      font-weight: 600; letter-spacing: 2px; text-transform: uppercase;
      cursor: pointer; transition: background .25s; margin-top: 4px;
    }
    .submit-btn:hover { background: #a83a12; }
    .form-success {
      display: none; background: rgba(61,107,79,0.2);
      border: 1px solid var(--green); border-radius: 3px;
      padding: 14px; text-align: center; color: #8fcca5; font-size: 0.9rem;
    }

    /* ── FOOTER ── */
    footer {
      background: #F5F5F5;
      border-top: 2px solid rgba(232,0,13,0.20);
      padding: 32px 5%; text-align: center;
    }
    .footer-logo {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.5rem; color: var(--rust); letter-spacing: 2px; margin-bottom: 10px;
    }
    .footer-logo span { color: #555555; }
    footer p { font-size: 0.8rem; color: rgba(50,50,50,0.5); }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(28px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 768px) {
      .nav-links { display: none; }
      .why-grid { grid-template-columns: 1fr; }
      .contact-wrap { grid-template-columns: 1fr; }
      .form-row { grid-template-columns: 1fr; }
      .hero-deco { display: none; }
    }
    @media (max-width: 480px) {
      .stats { flex-direction: column; gap: 24px; text-align: center; }
    }
  </style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">Sahil <span>Paper</span> Store</div>
  <ul class="nav-links">
    <li><a href="#materials">Materials</a></li>
    <li><a href="#how">How It Works</a></li>
    <li><a href="#why">Why Us</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="#contact" class="nav-cta">Get a Quote</a>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-badge">♻️ Chandigarh's Trusted Scrap Dealers</div>
  <h1>Turn Your<br/><span class="accent">Scrap</span> Into<br/>Cash Today</h1>
  <p class="hero-sub">
    We buy old iron, cardboard, newspapers, broken plastic, and all kinds of waste material — right from your doorstep. Fair prices. Hassle-free pickup.
  </p>
  <div class="hero-btns">
    <a href="#contact" class="btn-primary">Sell Your Scrap</a>
    <a href="#materials" class="btn-outline">What We Buy</a>
  </div>
  <div class="hero-deco">SCRAP</div>
</section>

<!-- STATS -->
<div class="stats">
  <div class="stat">
    <div class="stat-num">500+</div>
    <div class="stat-label">Happy Customers</div>
  </div>
  <div class="stat">
    <div class="stat-num">10+</div>
    <div class="stat-label">Years Experience</div>
  </div>
  <div class="stat">
    <div class="stat-num">50T+</div>
    <div class="stat-label">Waste Recycled</div>
  </div>
  <div class="stat">
    <div class="stat-num">100%</div>
    <div class="stat-label">Fair & Transparent</div>
  </div>
</div>

<!-- MATERIALS -->
<section class="materials" id="materials">
  <div class="section-tag">What We Accept</div>
  <h2 class="section-title">We Buy All<br/>Types of Scrap</h2>
  <p class="section-desc">From iron and steel to paper, plastic, and beyond — if it's waste, we want it. Best market rates guaranteed.</p>

  <div class="materials-grid">
    <div class="material-card">
      <span class="mat-icon">⚙️</span>
      <div class="mat-name">Iron & Steel</div>
      <div class="mat-desc">Old iron rods, gates, machinery parts, steel pipes, and all ferrous metal scrap.</div>
    </div>
    <div class="material-card">
      <span class="mat-icon">📦</span>
      <div class="mat-name">Cardboard</div>
      <div class="mat-desc">Used boxes, packaging cartons, corrugated sheets — any quantity accepted.</div>
    </div>
    <div class="material-card">
      <span class="mat-icon">📰</span>
      <div class="mat-name">Newspaper & Paper</div>
      <div class="mat-desc">Old newspapers, books, magazines, office paper waste, and other paper material.</div>
    </div>
    <div class="material-card">
      <span class="mat-icon">🧴</span>
      <div class="mat-name">Plastic</div>
      <div class="mat-desc">Broken plastic items, cans, containers, bottles, pipes, and mixed plastic waste.</div>
    </div>
    <div class="material-card">
      <span class="mat-icon">🔌</span>
      <div class="mat-name">E-Waste</div>
      <div class="mat-desc">Old wires, cables, broken electronics, circuit boards, and electrical components.</div>
    </div>
    <div class="material-card">
      <span class="mat-icon">🧱</span>
      <div class="mat-name">Other Waste</div>
      <div class="mat-desc">Aluminium, copper, brass, rubber, glass, and any other recyclable waste material.</div>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section class="how" id="how">
  <div class="section-tag">Simple Process</div>
  <h2 class="section-title">How It Works</h2>
  <p class="section-desc">Selling your scrap has never been easier. Three simple steps and you're done.</p>

  <div class="steps">
    <div class="step">
      <div class="step-num">01</div>
      <div class="step-title">Contact Us</div>
      <p class="step-text">Call us or fill out the form below. Tell us what type of scrap you have and the approximate quantity.</p>
    </div>
    <div class="step">
      <div class="step-num">02</div>
      <div class="step-title">We Visit & Weigh</div>
      <p class="step-text">Our team arrives at your location, weighs your material on the spot using accurate equipment.</p>
    </div>
    <div class="step">
      <div class="step-num">03</div>
      <div class="step-title">Get Paid Instantly</div>
      <p class="step-text">Receive fair payment on the spot — cash or online transfer. Quick, transparent, and honest.</p>
    </div>
    <div class="step">
      <div class="step-num">04</div>
      <div class="step-title">We Handle the Rest</div>
      <p class="step-text">We collect and haul everything away. No mess left behind. Your space is clean and clutter-free.</p>
    </div>
  </div>
</section>

<!-- WHY US -->
<section class="why" id="why">
  <div class="section-tag">Our Advantage</div>
  <h2 class="section-title">Why Choose<br/>Sahil Paper Store</h2>

  <div class="why-grid">
    <div class="why-card">
      <div class="why-icon">💰</div>
      <div>
        <div class="why-title">Best Market Rates</div>
        <p class="why-text">We offer competitive, up-to-date prices for all scrap materials. No haggling, no tricks — just honest pricing every time.</p>
      </div>
    </div>
    <div class="why-card">
      <div class="why-icon">🚚</div>
      <div>
        <div class="why-title">Free Doorstep Pickup</div>
        <p class="why-text">Don't worry about transport. We come to your home, shop, or factory and collect the scrap ourselves — free of cost.</p>
      </div>
    </div>
    <div class="why-card">
      <div class="why-icon">⚖️</div>
      <div>
        <div class="why-title">Accurate Weighing</div>
        <p class="why-text">We use certified weighing equipment to ensure every kilogram is counted fairly. Complete transparency guaranteed.</p>
      </div>
    </div>
    <div class="why-card">
      <div class="why-icon">🌱</div>
      <div>
        <div class="why-title">Eco-Friendly Recycling</div>
        <p class="why-text">All collected material is sent to certified recycling units, ensuring responsible disposal and a greener planet for everyone.</p>
      </div>
    </div>
    <div class="why-card">
      <div class="why-icon">🤝</div>
      <div>
        <div class="why-title">Trusted & Experienced</div>
        <p class="why-text">Over 10 years serving Chandigarh and surrounding areas. Hundreds of satisfied households, shops, and businesses.</p>
      </div>
    </div>
    <div class="why-card">
      <div class="why-icon">⚡</div>
      <div>
        <div class="why-title">Quick & Reliable</div>
        <p class="why-text">Same-day or next-day pickup available. We respect your time and always show up when we say we will.</p>
      </div>
    </div>
  </div>
</section>

<!-- ECO BANNER -->
<div class="eco">
  <h2>♻️ Recycle Today,<br/>Save Tomorrow</h2>
  <p>Every kilogram of scrap you sell is one less kilogram in a landfill. Join hundreds of responsible Chandigarh residents making a difference.</p>
  <a href="#contact" class="btn-primary">Schedule a Pickup</a>
</div>

<!-- CONTACT -->
<section class="contact" id="contact">
  <div class="section-tag">Reach Out</div>
  <h2 class="section-title">Get In Touch</h2>

  <div class="contact-wrap">
    <div class="contact-info">
      <div class="contact-item">
        <div class="contact-icon">📍</div>
        <div>
          <div class="contact-label">Location</div>
          <div class="contact-val">Near Primary School, Village Chachu Majra,<br/>Papri, Mohali, Punjab – 140306</div>
        </div>
      </div>
      <div class="contact-item">
        <div class="contact-icon">📞</div>
        <div>
          <div class="contact-label">Phone / WhatsApp</div>
          <div class="contact-val">+91 98552 28162</div>
        </div>
      </div>
      <a href="https://wa.me/919855228162?text=Hello%20Sahil%20Paper%20Store%2C%20I%20want%20to%20sell%20my%20scrap." target="_blank" class="whatsapp-btn">
        💬 &nbsp;Chat on WhatsApp
      </a>
      <a href="https://maps.google.com/?q=Village+Chachu+Majra,+Papri,+Mohali,+Punjab+140306,+India" target="_blank" class="maps-btn">
        📍 &nbsp;View on Google Maps
      </a>
      <div class="contact-item">
        <div class="contact-icon">🕐</div>
        <div>
          <div class="contact-label">Working Hours</div>
          <div class="contact-val">Mon – Sat: 9:00 AM – 7:00 PM<br/>Sunday: By Appointment</div>
        </div>
      </div>
      <div class="contact-item">
        <div class="contact-icon">♻️</div>
        <div>
          <div class="contact-label">We Accept</div>
          <div class="contact-val">Iron • Cardboard • Newspaper<br/>Plastic • E-Waste • All Scrap</div>
        </div>
      </div>
    </div>

    <div class="contact-form">
      <div class="form-row">
        <div class="form-group">
          <label for="name">Your Name</label>
          <input type="text" id="name" placeholder="Sahil Kumar"/>
        </div>
        <div class="form-group">
          <label for="phone">Phone Number</label>
          <input type="tel" id="phone" placeholder="+91 98765 43210"/>
        </div>
      </div>
      <div class="form-group">
        <label for="material">Type of Scrap</label>
        <select id="material">
          <option value="" disabled selected>Select material type</option>
          <option>Iron / Steel</option>
          <option>Cardboard</option>
          <option>Newspaper / Paper</option>
          <option>Plastic</option>
          <option>E-Waste</option>
          <option>Mixed / Other</option>
        </select>
      </div>
      <div class="form-group">
        <label for="address">Pickup Address</label>
        <input type="text" id="address" placeholder="Your area or full address"/>
      </div>
      <div class="form-group">
        <label for="message">Additional Details</label>
        <textarea id="message" placeholder="Approximate quantity, any special items, preferred pickup time..."></textarea>
      </div>
      <button class="submit-btn" onclick="submitForm()">Send Enquiry →</button>
      <div class="form-success" id="successMsg">✅ Thank you! We'll contact you shortly to arrange pickup.</div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">Sahil <span>Paper</span> Store</div>
  <p>Papri, Mohali, Punjab &nbsp;|&nbsp; Serving the community since over a decade<br/>© 2025 Sahil Paper Store. All rights reserved.</p>
</footer>

<script>
  function submitForm() {
    const name = document.getElementById('name').value.trim();
    const phone = document.getElementById('phone').value.trim();
    const material = document.getElementById('material').value;
    if (!name || !phone || !material) {
      alert('Please fill in your name, phone number, and select a material type.');
      return;
    }
    document.getElementById('successMsg').style.display = 'block';
    document.querySelector('.submit-btn').disabled = true;
    document.querySelector('.submit-btn').textContent = 'Sent!';
  }

  // Scroll-reveal animation
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.style.opacity = 1;
        e.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.12 });

  document.querySelectorAll('.material-card, .step, .why-card, .contact-item').forEach(el => {
    el.style.opacity = 0;
    el.style.transform = 'translateY(24px)';
    el.style.transition = 'opacity .5s ease, transform .5s ease';
    observer.observe(el);
  });
</script>
</body>
</html>
