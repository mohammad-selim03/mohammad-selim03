<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Your Name — Full Stack Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;0,700;1,300;1,400&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&display=swap" rel="stylesheet"/>
<style>
  /* ── RESET ── */
  *, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
  html { scroll-behavior:smooth; }

  /* ── TOKENS ── */
  :root {
    --space-0:     #020209;
    --space-1:     #060612;
    --space-2:     #0b0b20;
    --space-3:     #10102e;
    --glass-bg:    rgba(16,16,46,0.55);
    --glass-bd:    rgba(212,160,23,0.18);
    --gold-dim:    #8a6514;
    --gold-mid:    #c9933a;
    --gold-bright: #e8b86d;
    --gold-shine:  #f5d27a;
    --gold-star:   #fde68a;
    --white-soft:  #f0ead8;
    --white-muted: #b8b09a;
    --white-faint: #6a6254;
    --accent-vio:  rgba(100,60,200,0.35);
    --font-display: 'Cormorant Garamond', Georgia, serif;
    --font-body:    'DM Sans', system-ui, sans-serif;
    --ease-gold:    cubic-bezier(0.22, 1, 0.36, 1);
  }

  /* ── BASE ── */
  body {
    background: var(--space-0);
    color: var(--white-soft);
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 1.75;
    overflow-x: hidden;
  }

  /* ── CANVAS STARFIELD ── */
  #starfield {
    position: fixed;
    inset: 0;
    z-index: 0;
    pointer-events: none;
  }

  /* ── GOLD GRADIENT ORBS ── */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    pointer-events: none;
    z-index: 0;
    animation: orbDrift 18s ease-in-out infinite alternate;
  }
  .orb-1 {
    width: 700px; height: 700px;
    top: -200px; right: -200px;
    background: radial-gradient(circle, rgba(201,147,58,0.12) 0%, transparent 70%);
    animation-duration: 22s;
  }
  .orb-2 {
    width: 500px; height: 500px;
    bottom: 10%; left: -150px;
    background: radial-gradient(circle, rgba(100,60,200,0.1) 0%, transparent 70%);
    animation-duration: 17s; animation-delay: -8s;
  }
  .orb-3 {
    width: 400px; height: 400px;
    top: 40%; right: 5%;
    background: radial-gradient(circle, rgba(232,184,109,0.07) 0%, transparent 70%);
    animation-duration: 25s; animation-delay: -4s;
  }
  @keyframes orbDrift {
    0%   { transform: translate(0,0) scale(1); }
    50%  { transform: translate(40px,-30px) scale(1.05); }
    100% { transform: translate(-20px,50px) scale(0.97); }
  }

  /* ── LAYOUT WRAPPER ── */
  .page { position: relative; z-index: 1; }

  /* ── GOLD LINE ── */
  .gold-rule {
    width: 100%;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold-mid), transparent);
    opacity: 0.4;
  }

  /* ── SECTION BASE ── */
  section { padding: 120px 80px; position: relative; }
  section + section { padding-top: 80px; }

  /* ── FADE-IN REVEAL ── */
  .reveal {
    opacity: 0;
    transform: translateY(36px);
    transition: opacity 0.9s var(--ease-gold), transform 0.9s var(--ease-gold);
  }
  .reveal.visible { opacity: 1; transform: none; }
  .reveal-delay-1 { transition-delay: 0.1s; }
  .reveal-delay-2 { transition-delay: 0.22s; }
  .reveal-delay-3 { transition-delay: 0.34s; }
  .reveal-delay-4 { transition-delay: 0.46s; }
  .reveal-delay-5 { transition-delay: 0.58s; }
  .reveal-delay-6 { transition-delay: 0.70s; }

  /* ═══════════════════════════════════════
     HERO
  ═══════════════════════════════════════ */
  #hero {
    min-height: 100vh;
    padding: 0 80px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    position: relative;
    overflow: hidden;
  }

  .hero-eyebrow {
    font-family: var(--font-body);
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--gold-mid);
    margin-bottom: 32px;
    display: flex;
    align-items: center;
    gap: 16px;
  }
  .hero-eyebrow::before {
    content: '';
    width: 40px; height: 1px;
    background: var(--gold-mid);
    opacity: 0.6;
  }

  .hero-name {
    font-family: var(--font-display);
    font-size: clamp(72px, 9vw, 140px);
    font-weight: 300;
    line-height: 0.92;
    letter-spacing: -0.02em;
    color: var(--white-soft);
    margin-bottom: 16px;
  }
  .hero-name em {
    font-style: italic;
    background: linear-gradient(135deg, var(--gold-mid) 0%, var(--gold-shine) 50%, var(--gold-bright) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-tagline {
    font-family: var(--font-display);
    font-size: clamp(22px, 2.8vw, 38px);
    font-weight: 300;
    font-style: italic;
    color: var(--white-muted);
    margin-bottom: 48px;
    max-width: 780px;
  }

  .hero-desc {
    font-size: 17px;
    color: var(--white-muted);
    max-width: 620px;
    margin-bottom: 64px;
    line-height: 1.8;
  }

  .hero-ctas {
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
    align-items: center;
    margin-bottom: 80px;
  }

  .btn-primary {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 16px 36px;
    background: linear-gradient(135deg, var(--gold-dim) 0%, var(--gold-mid) 50%, var(--gold-bright) 100%);
    color: var(--space-0);
    font-family: var(--font-body);
    font-size: 13px;
    font-weight: 500;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    text-decoration: none;
    border: none;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    transition: transform 0.3s var(--ease-gold), box-shadow 0.3s var(--ease-gold);
    box-shadow: 0 0 40px rgba(201,147,58,0.25), 0 4px 20px rgba(0,0,0,0.4);
  }
  .btn-primary::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, transparent 0%, rgba(255,255,255,0.18) 50%, transparent 100%);
    transform: translateX(-100%);
    transition: transform 0.5s var(--ease-gold);
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 0 60px rgba(201,147,58,0.4), 0 8px 30px rgba(0,0,0,0.5); }
  .btn-primary:hover::before { transform: translateX(100%); }

  .btn-ghost {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 15px 34px;
    background: transparent;
    color: var(--gold-bright);
    font-family: var(--font-body);
    font-size: 13px;
    font-weight: 400;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    text-decoration: none;
    border: 1px solid rgba(232,184,109,0.35);
    transition: border-color 0.3s, background 0.3s, transform 0.3s;
  }
  .btn-ghost:hover {
    border-color: var(--gold-bright);
    background: rgba(232,184,109,0.07);
    transform: translateY(-2px);
  }

  .status-pill {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 8px 18px;
    border: 1px solid rgba(34,197,94,0.3);
    background: rgba(34,197,94,0.06);
    font-size: 12px;
    font-weight: 500;
    letter-spacing: 0.06em;
    color: #4ade80;
  }
  .status-dot {
    width: 7px; height: 7px;
    border-radius: 50%;
    background: #4ade80;
    animation: pulse-green 2s ease-in-out infinite;
  }
  @keyframes pulse-green {
    0%,100% { box-shadow: 0 0 0 0 rgba(74,222,128,0.5); }
    50%      { box-shadow: 0 0 0 6px rgba(74,222,128,0); }
  }

  .hero-metrics {
    display: grid;
    grid-template-columns: repeat(4, auto);
    gap: 0;
    border-top: 1px solid rgba(212,160,23,0.12);
    padding-top: 48px;
    width: fit-content;
  }
  .metric-item {
    padding: 0 48px 0 0;
    margin-right: 48px;
    border-right: 1px solid rgba(212,160,23,0.12);
  }
  .metric-item:last-child { border-right: none; margin-right: 0; padding-right: 0; }
  .metric-num {
    font-family: var(--font-display);
    font-size: 48px;
    font-weight: 300;
    line-height: 1;
    background: linear-gradient(135deg, var(--gold-mid), var(--gold-shine));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 6px;
  }
  .metric-label {
    font-size: 12px;
    color: var(--white-faint);
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }

  /* HERO scroll indicator */
  .scroll-hint {
    position: absolute;
    bottom: 48px;
    left: 80px;
    display: flex;
    align-items: center;
    gap: 12px;
    color: var(--white-faint);
    font-size: 11px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
  }
  .scroll-line {
    width: 40px; height: 1px;
    background: var(--gold-dim);
    position: relative;
    overflow: hidden;
  }
  .scroll-line::after {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--gold-bright);
    transform: translateX(-100%);
    animation: scrollSlide 2s ease-in-out infinite;
  }
  @keyframes scrollSlide {
    0%   { transform: translateX(-100%); }
    50%  { transform: translateX(0%); }
    100% { transform: translateX(100%); }
  }

  /* ═══════════════════════════════════════
     INTRO / POSITIONING
  ═══════════════════════════════════════ */
  #intro { padding: 100px 80px; }

  .section-label {
    font-family: var(--font-body);
    font-size: 10px;
    font-weight: 500;
    letter-spacing: 0.35em;
    text-transform: uppercase;
    color: var(--gold-mid);
    margin-bottom: 28px;
    display: flex;
    align-items: center;
    gap: 14px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    max-width: 48px;
    height: 1px;
    background: var(--gold-dim);
    opacity: 0.6;
  }

  .section-heading {
    font-family: var(--font-display);
    font-size: clamp(42px, 5vw, 72px);
    font-weight: 300;
    line-height: 1.08;
    letter-spacing: -0.01em;
    color: var(--white-soft);
    margin-bottom: 40px;
  }
  .section-heading em {
    font-style: italic;
    color: var(--gold-bright);
  }

  .intro-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: start;
  }
  .intro-body {
    font-size: 17px;
    color: var(--white-muted);
    line-height: 1.85;
  }
  .intro-body p + p { margin-top: 20px; }
  .intro-body strong { color: var(--white-soft); font-weight: 500; }

  .quote-block {
    border-left: 2px solid var(--gold-mid);
    padding: 32px 40px;
    background: var(--glass-bg);
    backdrop-filter: blur(12px);
    border-top: 1px solid var(--glass-bd);
    border-right: 1px solid var(--glass-bd);
    border-bottom: 1px solid var(--glass-bd);
  }
  .quote-text {
    font-family: var(--font-display);
    font-size: 22px;
    font-weight: 300;
    font-style: italic;
    line-height: 1.55;
    color: var(--white-soft);
    margin-bottom: 20px;
  }
  .quote-source {
    font-size: 12px;
    letter-spacing: 0.1em;
    color: var(--gold-mid);
    text-transform: uppercase;
  }

  /* ═══════════════════════════════════════
     SERVICES
  ═══════════════════════════════════════ */
  #services { padding: 100px 80px; }

  .services-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    margin-top: 64px;
  }

  .service-card {
    padding: 48px 40px;
    background: var(--glass-bg);
    border: 1px solid rgba(212,160,23,0.1);
    position: relative;
    overflow: hidden;
    transition: border-color 0.4s, background 0.4s, transform 0.4s var(--ease-gold);
    cursor: default;
  }
  .service-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--gold-mid), transparent);
    opacity: 0;
    transition: opacity 0.4s;
  }
  .service-card::after {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse at 50% 0%, rgba(201,147,58,0.07) 0%, transparent 65%);
    opacity: 0;
    transition: opacity 0.5s;
  }
  .service-card:hover {
    border-color: rgba(232,184,109,0.28);
    background: rgba(16,16,46,0.8);
    transform: translateY(-4px);
  }
  .service-card:hover::before { opacity: 1; }
  .service-card:hover::after  { opacity: 1; }

  .service-num {
    font-family: var(--font-display);
    font-size: 72px;
    font-weight: 300;
    line-height: 1;
    color: rgba(201,147,58,0.1);
    margin-bottom: -8px;
    letter-spacing: -0.02em;
    transition: color 0.4s;
  }
  .service-card:hover .service-num { color: rgba(201,147,58,0.2); }

  .service-title {
    font-family: var(--font-display);
    font-size: 26px;
    font-weight: 400;
    color: var(--white-soft);
    margin-bottom: 16px;
    line-height: 1.2;
  }
  .service-desc {
    font-size: 15px;
    color: var(--white-muted);
    line-height: 1.75;
    margin-bottom: 28px;
  }
  .service-outcome {
    font-size: 12px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--gold-mid);
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .service-outcome::before {
    content: '';
    width: 20px; height: 1px;
    background: var(--gold-mid);
  }

  /* ═══════════════════════════════════════
     CASE STUDIES
  ═══════════════════════════════════════ */
  #work { padding: 100px 80px; }

  .case-studies { margin-top: 64px; display: flex; flex-direction: column; gap: 2px; }

  .case-card {
    padding: 56px 64px;
    background: var(--glass-bg);
    border: 1px solid rgba(212,160,23,0.1);
    position: relative;
    overflow: hidden;
    transition: border-color 0.4s;
    cursor: pointer;
  }
  .case-card::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 3px;
    background: linear-gradient(180deg, transparent, var(--gold-mid), transparent);
    opacity: 0;
    transition: opacity 0.4s;
  }
  .case-card:hover { border-color: rgba(232,184,109,0.22); }
  .case-card:hover::before { opacity: 1; }

  .case-header {
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 40px;
    align-items: start;
    margin-bottom: 40px;
  }
  .case-label {
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold-mid);
    margin-bottom: 12px;
  }
  .case-title {
    font-family: var(--font-display);
    font-size: 34px;
    font-weight: 300;
    color: var(--white-soft);
    line-height: 1.2;
  }
  .case-industry {
    font-size: 12px;
    letter-spacing: 0.1em;
    color: var(--white-faint);
    text-transform: uppercase;
    text-align: right;
    padding-top: 8px;
  }

  .case-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 48px; }

  .case-col-label {
    font-size: 10px;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--gold-dim);
    margin-bottom: 12px;
  }
  .case-body {
    font-size: 15px;
    color: var(--white-muted);
    line-height: 1.75;
  }

  .case-results {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }
  .result-row {
    display: flex;
    align-items: baseline;
    gap: 16px;
    padding: 16px 20px;
    border: 1px solid rgba(212,160,23,0.1);
    background: rgba(201,147,58,0.04);
  }
  .result-num {
    font-family: var(--font-display);
    font-size: 28px;
    font-weight: 300;
    color: var(--gold-bright);
    white-space: nowrap;
    min-width: 90px;
  }
  .result-desc {
    font-size: 13px;
    color: var(--white-muted);
    line-height: 1.5;
  }

  .stack-row {
    margin-top: 36px;
    padding-top: 28px;
    border-top: 1px solid rgba(212,160,23,0.1);
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }
  .stack-tag {
    padding: 5px 14px;
    border: 1px solid rgba(212,160,23,0.2);
    font-size: 11px;
    letter-spacing: 0.06em;
    color: var(--gold-mid);
    background: rgba(201,147,58,0.05);
  }

  /* ═══════════════════════════════════════
     TECH STACK
  ═══════════════════════════════════════ */
  #stack { padding: 100px 80px; }

  .stack-table-wrap {
    margin-top: 64px;
    border: 1px solid rgba(212,160,23,0.12);
  }
  .stack-row-item {
    display: grid;
    grid-template-columns: 200px 1fr 200px;
    gap: 40px;
    padding: 28px 40px;
    border-bottom: 1px solid rgba(212,160,23,0.08);
    align-items: center;
    transition: background 0.3s;
  }
  .stack-row-item:last-child { border-bottom: none; }
  .stack-row-item:hover { background: rgba(201,147,58,0.04); }
  .stack-tech {
    font-family: var(--font-display);
    font-size: 20px;
    font-weight: 400;
    color: var(--white-soft);
  }
  .stack-purpose {
    font-size: 15px;
    color: var(--white-muted);
    line-height: 1.6;
  }
  .stack-outcome-tag {
    font-size: 11px;
    letter-spacing: 0.07em;
    color: var(--gold-mid);
    text-transform: uppercase;
    text-align: right;
  }

  /* ═══════════════════════════════════════
     PROCESS
  ═══════════════════════════════════════ */
  #process { padding: 100px 80px; }

  .process-steps {
    margin-top: 72px;
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 0;
    position: relative;
  }
  .process-steps::before {
    content: '';
    position: absolute;
    top: 28px;
    left: 10%;
    right: 10%;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold-dim), var(--gold-mid), var(--gold-dim), transparent);
    opacity: 0.4;
  }

  .process-step {
    padding: 0 24px;
    text-align: center;
  }
  .step-circle {
    width: 56px; height: 56px;
    border: 1px solid rgba(232,184,109,0.3);
    background: var(--glass-bg);
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto 28px;
    position: relative;
    transition: border-color 0.3s, background 0.3s;
  }
  .step-circle::before {
    content: '';
    position: absolute;
    inset: -4px;
    border: 1px solid rgba(232,184,109,0.1);
  }
  .process-step:hover .step-circle {
    border-color: var(--gold-bright);
    background: rgba(201,147,58,0.1);
  }
  .step-num {
    font-family: var(--font-display);
    font-size: 22px;
    font-weight: 300;
    color: var(--gold-bright);
  }
  .step-title {
    font-size: 14px;
    font-weight: 500;
    color: var(--white-soft);
    margin-bottom: 12px;
    letter-spacing: 0.03em;
  }
  .step-desc {
    font-size: 13px;
    color: var(--white-faint);
    line-height: 1.65;
  }

  /* ═══════════════════════════════════════
     TESTIMONIALS
  ═══════════════════════════════════════ */
  #testimonials { padding: 100px 80px; }

  .testi-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    margin-top: 64px;
  }

  .testi-card {
    padding: 48px 40px;
    background: var(--glass-bg);
    border: 1px solid rgba(212,160,23,0.1);
    position: relative;
    transition: border-color 0.4s, transform 0.4s var(--ease-gold);
  }
  .testi-card:hover {
    border-color: rgba(232,184,109,0.25);
    transform: translateY(-3px);
  }

  .testi-stars {
    display: flex;
    gap: 4px;
    margin-bottom: 28px;
  }
  .star {
    width: 12px; height: 12px;
    background: var(--gold-bright);
    clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
  }

  .testi-quote {
    font-family: var(--font-display);
    font-size: 18px;
    font-weight: 300;
    font-style: italic;
    line-height: 1.7;
    color: var(--white-soft);
    margin-bottom: 32px;
  }
  .testi-quote::before { content: '\201C'; color: var(--gold-dim); font-size: 48px; line-height: 0; vertical-align: -0.5em; margin-right: 4px; }
  .testi-quote::after  { content: '\201D'; color: var(--gold-dim); font-size: 48px; line-height: 0; vertical-align: -0.5em; margin-left: 4px; }

  .testi-author {
    border-top: 1px solid rgba(212,160,23,0.12);
    padding-top: 24px;
  }
  .testi-name {
    font-size: 14px;
    font-weight: 500;
    color: var(--white-soft);
    margin-bottom: 4px;
  }
  .testi-role {
    font-size: 12px;
    color: var(--gold-mid);
    letter-spacing: 0.06em;
  }

  /* ═══════════════════════════════════════
     COMPARISON / WHY ME
  ═══════════════════════════════════════ */
  #why { padding: 100px 80px; }

  .comparison-wrap {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    margin-top: 64px;
  }
  .comp-col {
    padding: 48px;
    background: var(--glass-bg);
    border: 1px solid rgba(212,160,23,0.1);
  }
  .comp-col.gold-col {
    border-color: rgba(232,184,109,0.25);
    background: rgba(16,16,46,0.7);
    position: relative;
    overflow: hidden;
  }
  .comp-col.gold-col::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--gold-dim), var(--gold-shine), var(--gold-dim));
  }
  .comp-head {
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--white-faint);
    margin-bottom: 32px;
    padding-bottom: 20px;
    border-bottom: 1px solid rgba(212,160,23,0.1);
  }
  .comp-col.gold-col .comp-head { color: var(--gold-mid); }

  .comp-item {
    display: flex;
    gap: 16px;
    padding: 16px 0;
    border-bottom: 1px solid rgba(212,160,23,0.06);
    font-size: 14px;
    color: var(--white-faint);
    line-height: 1.5;
    align-items: flex-start;
  }
  .comp-item:last-child { border-bottom: none; }
  .comp-icon { flex-shrink: 0; width: 18px; margin-top: 2px; }
  .comp-col.gold-col .comp-item { color: var(--white-muted); }

  /* ═══════════════════════════════════════
     CTA / FOOTER
  ═══════════════════════════════════════ */
  #cta {
    padding: 140px 80px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  #cta::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse at 50% 100%, rgba(201,147,58,0.12) 0%, transparent 60%);
    pointer-events: none;
  }

  .cta-heading {
    font-family: var(--font-display);
    font-size: clamp(48px, 6vw, 92px);
    font-weight: 300;
    line-height: 1.05;
    letter-spacing: -0.01em;
    color: var(--white-soft);
    margin-bottom: 28px;
  }
  .cta-heading em {
    font-style: italic;
    background: linear-gradient(135deg, var(--gold-mid), var(--gold-shine));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .cta-sub {
    font-size: 18px;
    color: var(--white-muted);
    margin-bottom: 20px;
  }
  .cta-note {
    font-size: 14px;
    color: var(--white-faint);
    margin-bottom: 56px;
    line-height: 1.7;
    max-width: 560px;
    margin-left: auto;
    margin-right: auto;
  }
  .cta-note strong { color: var(--white-muted); font-weight: 500; }

  .cta-buttons {
    display: flex;
    gap: 20px;
    justify-content: center;
    flex-wrap: wrap;
    margin-bottom: 64px;
  }

  .contact-row {
    display: flex;
    justify-content: center;
    gap: 40px;
    flex-wrap: wrap;
    padding-top: 56px;
    border-top: 1px solid rgba(212,160,23,0.12);
  }
  .contact-link {
    display: flex;
    align-items: center;
    gap: 10px;
    text-decoration: none;
    color: var(--white-faint);
    font-size: 13px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    transition: color 0.3s;
  }
  .contact-link:hover { color: var(--gold-bright); }
  .contact-link-icon {
    width: 28px; height: 28px;
    border: 1px solid rgba(212,160,23,0.25);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 13px;
    transition: border-color 0.3s, background 0.3s;
  }
  .contact-link:hover .contact-link-icon {
    border-color: var(--gold-bright);
    background: rgba(232,184,109,0.08);
  }

  footer {
    padding: 40px 80px;
    border-top: 1px solid rgba(212,160,23,0.08);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .footer-name {
    font-family: var(--font-display);
    font-size: 20px;
    font-weight: 300;
    color: var(--gold-mid);
  }
  .footer-note {
    font-size: 12px;
    color: var(--white-faint);
    letter-spacing: 0.08em;
  }

  /* ═══════════════════════════════════════
     GOLD DIVIDER ORNAMENT
  ═══════════════════════════════════════ */
  .ornament {
    text-align: center;
    padding: 24px 80px;
    color: var(--gold-dim);
    font-size: 14px;
    letter-spacing: 0.4em;
    opacity: 0.5;
  }
  .ornament::before, .ornament::after {
    content: '─────';
    margin: 0 16px;
  }

  /* ═══════════════════════════════════════
     ANIMATED COUNTER
  ═══════════════════════════════════════ */
  .counter { display: inline; }
</style>
</head>
<body>

<!-- Starfield canvas -->
<canvas id="starfield"></canvas>

<!-- Ambient orbs -->
<div class="orb orb-1"></div>
<div class="orb orb-2"></div>
<div class="orb orb-3"></div>

<div class="page">

  <!-- ╔══════════ HERO ══════════╗ -->
  <section id="hero">
    <div class="hero-eyebrow reveal">
      Full Stack Developer &nbsp;·&nbsp; React &nbsp;·&nbsp; Next.js &nbsp;·&nbsp; TypeScript &nbsp;·&nbsp; Node.js
    </div>

    <h1 class="hero-name reveal reveal-delay-1">
      Your<br/><em>Name</em>
    </h1>

    <p class="hero-tagline reveal reveal-delay-2">
      I don't write code — I build revenue.
    </p>

    <p class="hero-desc reveal reveal-delay-3">
      When a potential client visits this page, they shouldn't feel like they found a developer.
      They should feel like they found the answer to a problem they've been carrying for months.
      That's the only standard I hold myself to.
    </p>

    <div class="hero-ctas reveal reveal-delay-4">
      <div class="status-pill">
        <div class="status-dot"></div>
        Available — 2 project slots open
      </div>
    </div>

    <div class="hero-ctas reveal reveal-delay-4" style="margin-top: -44px;">
      <a href="mailto:your@email.com" class="btn-primary">→ Start a Project</a>
      <a href="https://calendly.com/yourhandle" class="btn-ghost">Book Free 30-min Call</a>
      <a href="https://yourportfolio.com" class="btn-ghost">View Portfolio</a>
    </div>

    <div class="hero-metrics reveal reveal-delay-5">
      <div class="metric-item">
        <div class="metric-num"><span class="counter" data-target="3">0</span>+</div>
        <div class="metric-label">Years Delivering</div>
      </div>
      <div class="metric-item">
        <div class="metric-num"><span class="counter" data-target="30">0</span>+</div>
        <div class="metric-label">Products Shipped</div>
      </div>
      <div class="metric-item">
        <div class="metric-num"><span class="counter" data-target="98">0</span>%</div>
        <div class="metric-label">Client Satisfaction</div>
      </div>
      <div class="metric-item">
        <div class="metric-num">&lt;1<span style="font-size:28px">s</span></div>
        <div class="metric-label">Avg Page Load</div>
      </div>
    </div>

    <div class="scroll-hint">
      <div class="scroll-line"></div>
      Scroll
    </div>
  </section>

  <div class="gold-rule"></div>

  <!-- ╔══════════ INTRO ══════════╗ -->
  <section id="intro">
    <div class="section-label reveal">01 — About</div>
    <h2 class="section-heading reveal reveal-delay-1">
      Most developers write code.<br/><em>I ship outcomes.</em>
    </h2>

    <div class="intro-grid">
      <div class="intro-body reveal reveal-delay-2">
        <p>
          You've felt it before — a developer who was technically impressive but completely missed
          the point. They built what you <strong>asked for</strong>, not what you <strong>needed</strong>.
          Technically on-spec. Strategically useless.
        </p>
        <p>
          I work at the intersection of engineering and business strategy. Before writing a single
          line, I understand your users, your revenue model, and your growth bottleneck.
          The result isn't just a product — it's a <strong>system designed to perform from day one</strong>.
        </p>
        <p>
          I partner with startup founders, SaaS companies, and digital agencies across the US, UK,
          Germany, Australia, and Canada — remote, async, and zero hand-holding required.
        </p>
      </div>

      <div class="quote-block reveal reveal-delay-3">
        <div class="quote-text">
          If your product needs to generate revenue, retain users, and scale without breaking —
          you're in the right place.
        </div>
        <div class="quote-source">— The one question I ask before every project</div>
      </div>
    </div>
  </section>

  <div class="ornament">✦</div>

  <!-- ╔══════════ SERVICES ══════════╗ -->
  <section id="services">
    <div class="section-label reveal">02 — Services</div>
    <h2 class="section-heading reveal reveal-delay-1">
      What I build —<br/><em>framed as what it solves.</em>
    </h2>

    <div class="services-grid">
      <div class="service-card reveal reveal-delay-1">
        <div class="service-num">01</div>
        <div class="service-title">MVP & Product Launch</div>
        <div class="service-desc">
          From concept to deployed product in weeks, not months. I handle architecture,
          build, QA, and launch so you can focus on users and growth instead of technical decisions.
        </div>
        <div class="service-outcome">Idea → Deployed Product → First Revenue</div>
      </div>

      <div class="service-card reveal reveal-delay-2">
        <div class="service-num">02</div>
        <div class="service-title">SaaS Platform Development</div>
        <div class="service-desc">
          Full-featured, subscription-ready platforms. Auth, billing, dashboards, role
          management, APIs, admin panels — built on a foundation that handles 10 or 100,000 users.
        </div>
        <div class="service-outcome">Ship once. Sell forever.</div>
      </div>

      <div class="service-card reveal reveal-delay-3">
        <div class="service-num">03</div>
        <div class="service-title">AI Feature Integration</div>
        <div class="service-desc">
          LLM integration, GPT-powered features, RAG pipelines, AI automation — giving
          your product capabilities your competitors haven't shipped yet.
        </div>
        <div class="service-outcome">Features users didn't know they needed.</div>
      </div>

      <div class="service-card reveal reveal-delay-4">
        <div class="service-num">04</div>
        <div class="service-title">Performance Rescue</div>
        <div class="service-desc">
          Deep audit, refactor, and architectural rebuild for speed and reliability.
          Apps that don't collapse the moment real success arrives.
        </div>
        <div class="service-outcome">4.8s load → 0.9s. Zero downtime under traffic.</div>
      </div>

      <div class="service-card reveal reveal-delay-5">
        <div class="service-num">05</div>
        <div class="service-title">E-Commerce Engineering</div>
        <div class="service-desc">
          Headless storefronts, optimized checkout flows, custom pricing logic, loyalty
          systems — engineering more revenue from your existing traffic.
        </div>
        <div class="service-outcome">More sales. Same visitors.</div>
      </div>

      <div class="service-card reveal reveal-delay-6">
        <div class="service-num">06</div>
        <div class="service-title">API & Integration Systems</div>
        <div class="service-desc">
          Stripe, Paddle, CRMs, ERPs, third-party APIs, webhooks, and automation
          pipelines — your entire stack becomes one cohesive, reliable system.
        </div>
        <div class="service-outcome">No more data silos or manual workarounds.</div>
      </div>
    </div>
  </section>

  <div class="gold-rule"></div>

  <!-- ╔══════════ CASE STUDIES ══════════╗ -->
  <section id="work">
    <div class="section-label reveal">03 — Case Studies</div>
    <h2 class="section-heading reveal reveal-delay-1">
      Real problems.<br/><em>Measurable results.</em>
    </h2>

    <div class="case-studies">

      <!-- Case 1 -->
      <div class="case-card reveal reveal-delay-2">
        <div class="case-header">
          <div>
            <div class="case-label">Case Study 01</div>
            <div class="case-title">B2B SaaS Analytics Dashboard</div>
          </div>
          <div class="case-industry">SaaS · B2B · Data</div>
        </div>
        <div class="case-grid">
          <div>
            <div class="case-col-label">The Problem</div>
            <div class="case-body">
              A B2B data startup was generating client reports manually in spreadsheets —
              20+ hours per week of error-prone work. Clients were frustrated. The business
              couldn't scale without hiring more people just to run reports.
            </div>
            <div class="stack-row">
              <span class="stack-tag">Next.js</span>
              <span class="stack-tag">TypeScript</span>
              <span class="stack-tag">PostgreSQL</span>
              <span class="stack-tag">Prisma</span>
              <span class="stack-tag">Stripe</span>
              <span class="stack-tag">Tailwind CSS</span>
            </div>
          </div>
          <div class="case-results">
            <div class="result-row">
              <div class="result-num">0 hrs</div>
              <div class="result-desc">Weekly reporting time (down from 20+ hrs, fully automated)</div>
            </div>
            <div class="result-row">
              <div class="result-num">100%</div>
              <div class="result-desc">Report accuracy (up from ~87% manual)</div>
            </div>
            <div class="result-row">
              <div class="result-num">$3k+</div>
              <div class="result-desc">New monthly revenue per Enterprise client from new tier</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Case 2 -->
      <div class="case-card reveal reveal-delay-3">
        <div class="case-header">
          <div>
            <div class="case-label">Case Study 02</div>
            <div class="case-title">Headless E-Commerce Rebuild</div>
          </div>
          <div class="case-industry">DTC · E-Commerce · Shopify</div>
        </div>
        <div class="case-grid">
          <div>
            <div class="case-col-label">The Problem</div>
            <div class="case-body">
              Stuck on a slow template Shopify store with 4.8s load time. Custom pricing
              logic was impossible. Flash sale traffic caused crashes. Customers were
              abandoning at checkout and conversion was suffering.
            </div>
            <div class="stack-row">
              <span class="stack-tag">Next.js</span>
              <span class="stack-tag">TypeScript</span>
              <span class="stack-tag">Shopify API</span>
              <span class="stack-tag">Tailwind CSS</span>
              <span class="stack-tag">Node.js</span>
              <span class="stack-tag">MongoDB</span>
            </div>
          </div>
          <div class="case-results">
            <div class="result-row">
              <div class="result-num">0.9s</div>
              <div class="result-desc">Page load (down from 4.8s — 80% faster)</div>
            </div>
            <div class="result-row">
              <div class="result-num">+22%</div>
              <div class="result-desc">Conversion rate post-launch</div>
            </div>
            <div class="result-row">
              <div class="result-num">8,000</div>
              <div class="result-desc">Concurrent flash-sale users — zero downtime</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Case 3 -->
      <div class="case-card reveal reveal-delay-4">
        <div class="case-header">
          <div>
            <div class="case-label">Case Study 03</div>
            <div class="case-title">AI-Powered Legal Document Intelligence</div>
          </div>
          <div class="case-industry">Legal-Tech · AI · SaaS</div>
        </div>
        <div class="case-grid">
          <div>
            <div class="case-col-label">The Problem</div>
            <div class="case-body">
              A legal-tech startup needed clients to upload contracts and instantly get
              clause extractions, red flags, risk scoring, and plain-English summaries —
              without paying $500/hr lawyer fees — at scale.
            </div>
            <div class="stack-row">
              <span class="stack-tag">Next.js</span>
              <span class="stack-tag">TypeScript</span>
              <span class="stack-tag">OpenAI API</span>
              <span class="stack-tag">Node.js</span>
              <span class="stack-tag">PostgreSQL</span>
              <span class="stack-tag">AWS S3</span>
            </div>
          </div>
          <div class="case-results">
            <div class="result-row">
              <div class="result-num">&lt;30s</div>
              <div class="result-desc">40-page contract fully analyzed (clause extraction + risk scoring)</div>
            </div>
            <div class="result-row">
              <div class="result-num">200+</div>
              <div class="result-desc">SMB clients in first 3 months post-launch</div>
            </div>
            <div class="result-row">
              <div class="result-num">Seed</div>
              <div class="result-desc">Core feature supporting the startup's funding round</div>
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>

  <div class="ornament">✦</div>

  <!-- ╔══════════ STACK ══════════╗ -->
  <section id="stack">
    <div class="section-label reveal">04 — Technology</div>
    <h2 class="section-heading reveal reveal-delay-1">
      Every tool in service<br/><em>of your business.</em>
    </h2>

    <div class="stack-table-wrap reveal reveal-delay-2">
      <div class="stack-row-item">
        <div class="stack-tech">Next.js + React</div>
        <div class="stack-purpose">Fast, SEO-optimized frontends that load instantly, rank on Google, and convert visitors into customers.</div>
        <div class="stack-outcome-tag">Frontend Excellence</div>
      </div>
      <div class="stack-row-item">
        <div class="stack-tech">TypeScript</div>
        <div class="stack-purpose">Fewer bugs in production. Codebases that scale from 1 developer to 10 without falling apart.</div>
        <div class="stack-outcome-tag">Reliability at Scale</div>
      </div>
      <div class="stack-row-item">
        <div class="stack-tech">Node.js + Express</div>
        <div class="stack-purpose">High-performance APIs and backend services that handle real traffic without performance degradation.</div>
        <div class="stack-outcome-tag">Backend Power</div>
      </div>
      <div class="stack-row-item">
        <div class="stack-tech">PostgreSQL + MongoDB</div>
        <div class="stack-purpose">The right data architecture for your product — relational integrity or document flexibility, chosen deliberately.</div>
        <div class="stack-outcome-tag">Data Foundation</div>
      </div>
      <div class="stack-row-item">
        <div class="stack-tech">Tailwind CSS</div>
        <div class="stack-purpose">Pixel-perfect UI delivered in half the time, fully consistent across every device and screen size.</div>
        <div class="stack-outcome-tag">Design System</div>
      </div>
      <div class="stack-row-item">
        <div class="stack-tech">Stripe / Paddle</div>
        <div class="stack-purpose">Complete revenue infrastructure — subscriptions, one-time payments, billing portals, and usage-based billing.</div>
        <div class="stack-outcome-tag">Revenue Infrastructure</div>
      </div>
      <div class="stack-row-item">
        <div class="stack-tech">OpenAI / LLMs</div>
        <div class="stack-purpose">Intelligent features that feel magical to end users — the capabilities your competitors haven't shipped yet.</div>
        <div class="stack-outcome-tag">AI Integration</div>
      </div>
      <div class="stack-row-item">
        <div class="stack-tech">AWS + Vercel</div>
        <div class="stack-purpose">Infrastructure that stays live, scales automatically, and doesn't require a 3am incident response call.</div>
        <div class="stack-outcome-tag">Always-On Deployment</div>
      </div>
    </div>
  </section>

  <div class="gold-rule"></div>

  <!-- ╔══════════ PROCESS ══════════╗ -->
  <section id="process">
    <div class="section-label reveal">05 — Process</div>
    <h2 class="section-heading reveal reveal-delay-1">
      How we'll work together —<br/><em>no surprises, ever.</em>
    </h2>

    <div class="process-steps">
      <div class="process-step reveal reveal-delay-1">
        <div class="step-circle"><div class="step-num">01</div></div>
        <div class="step-title">Discovery Call</div>
        <div class="step-desc">Free 30-min conversation about your goals, constraints, and what success actually looks like. No pitch.</div>
      </div>
      <div class="process-step reveal reveal-delay-2">
        <div class="step-circle"><div class="step-num">02</div></div>
        <div class="step-title">Proposal & Scope</div>
        <div class="step-desc">Detailed written proposal within 48 hrs: scope, architecture, timeline, milestones, fixed cost. Full clarity upfront.</div>
      </div>
      <div class="process-step reveal reveal-delay-3">
        <div class="step-circle"><div class="step-num">03</div></div>
        <div class="step-title">Build Phase</div>
        <div class="step-desc">Weekly staging demos. Daily async updates. You're never left wondering what's happening with your money.</div>
      </div>
      <div class="process-step reveal reveal-delay-4">
        <div class="step-circle"><div class="step-num">04</div></div>
        <div class="step-title">QA & Refinement</div>
        <div class="step-desc">You test on staging. You give feedback. I refine. Nothing ships until you're confident it performs.</div>
      </div>
      <div class="process-step reveal reveal-delay-5">
        <div class="step-circle"><div class="step-num">05</div></div>
        <div class="step-title">Launch & Beyond</div>
        <div class="step-desc">Deployed, documented, clean handoff. Then you choose: full handoff, retainer, or as-needed support.</div>
      </div>
    </div>
  </section>

  <div class="ornament">✦</div>

  <!-- ╔══════════ TESTIMONIALS ══════════╗ -->
  <section id="testimonials">
    <div class="section-label reveal">06 — Client Voice</div>
    <h2 class="section-heading reveal reveal-delay-1">
      What clients<br/><em>actually say.</em>
    </h2>

    <div class="testi-grid">
      <div class="testi-card reveal reveal-delay-1">
        <div class="testi-stars">
          <div class="star"></div><div class="star"></div><div class="star"></div>
          <div class="star"></div><div class="star"></div>
        </div>
        <div class="testi-quote">
          We interviewed 12 developers before working with him. Most talked about frameworks.
          He talked about our users, our revenue model, and our deployment timeline.
          That's why we hired him — and we haven't looked back.
        </div>
        <div class="testi-author">
          <div class="testi-name">Sarah M.</div>
          <div class="testi-role">Founder, B2B SaaS Startup · 🇺🇸 USA</div>
        </div>
      </div>

      <div class="testi-card reveal reveal-delay-2">
        <div class="testi-stars">
          <div class="star"></div><div class="star"></div><div class="star"></div>
          <div class="star"></div><div class="star"></div>
        </div>
        <div class="testi-quote">
          He took our half-baked idea and shipped a working MVP in 6 weeks.
          We used it to close our first 3 paying clients before we officially launched.
          Exceptional communicator. Exceptional developer.
        </div>
        <div class="testi-author">
          <div class="testi-name">James K.</div>
          <div class="testi-role">Co-Founder, PropTech Startup · 🇬🇧 UK</div>
        </div>
      </div>

      <div class="testi-card reveal reveal-delay-3">
        <div class="testi-stars">
          <div class="star"></div><div class="star"></div><div class="star"></div>
          <div class="star"></div><div class="star"></div>
        </div>
        <div class="testi-quote">
          Our site went from 6 seconds load time to under 1 second. Bounce rate dropped 38%
          and form submissions doubled in the first month. The ROI was immediate and
          completely undeniable.
        </div>
        <div class="testi-author">
          <div class="testi-name">Laura T.</div>
          <div class="testi-role">Marketing Director, E-Commerce · 🇩🇪 Germany</div>
        </div>
      </div>
    </div>
  </section>

  <div class="gold-rule"></div>

  <!-- ╔══════════ WHY ME ══════════╗ -->
  <section id="why">
    <div class="section-label reveal">07 — Difference</div>
    <h2 class="section-heading reveal reveal-delay-1">
      What you get vs.<br/><em>what you usually get.</em>
    </h2>

    <div class="comparison-wrap">
      <div class="comp-col reveal reveal-delay-2">
        <div class="comp-head">❌ &nbsp; Typical Developer</div>
        <div class="comp-item">
          <div class="comp-icon" style="color:var(--white-faint)">✗</div>
          <div>Asks: "What features do you want?" — builds to spec, misses the point</div>
        </div>
        <div class="comp-item">
          <div class="comp-icon" style="color:var(--white-faint)">✗</div>
          <div>Disappears for weeks, then sends a Loom at midnight</div>
        </div>
        <div class="comp-item">
          <div class="comp-icon" style="color:var(--white-faint)">✗</div>
          <div>Works on their machine. Production server? Good luck.</div>
        </div>
        <div class="comp-item">
          <div class="comp-icon" style="color:var(--white-faint)">✗</div>
          <div>Scope creep shows up as a surprise invoice</div>
        </div>
        <div class="comp-item">
          <div class="comp-icon" style="color:var(--white-faint)">✗</div>
          <div>Code only they can understand or maintain</div>
        </div>
        <div class="comp-item">
          <div class="comp-icon" style="color:var(--white-faint)">✗</div>
          <div>Technically correct. Strategically irrelevant.</div>
        </div>
      </div>

      <div class="comp-col gold-col reveal reveal-delay-3">
        <div class="comp-head">✦ &nbsp; Working With Me</div>
        <div class="comp-item">
          <div class="comp-icon" style="color:var(--gold-mid)">✦</div>
          <div>Asks: "What does your user need to do to pay you?" — strategy first</div>
        </div>
        <div class="comp-item">
          <div class="comp-icon" style="color:var(--gold-mid)">✦</div>
          <div>Weekly demos, staging previews, async daily updates</div>
        </div>
        <div class="comp-item">
          <div class="comp-icon" style="color:var(--gold-mid)">✦</div>
          <div>Deployed, production-tested, monitored from day 1</div>
        </div>
        <div class="comp-item">
          <div class="comp-icon" style="color:var(--gold-mid)">✦</div>
          <div>Detailed scope document upfront — zero surprises, ever</div>
        </div>
        <div class="comp-item">
          <div class="comp-icon" style="color:var(--gold-mid)">✦</div>
          <div>Clean, documented code your next developer will thank you for</div>
        </div>
        <div class="comp-item">
          <div class="comp-icon" style="color:var(--gold-mid)">✦</div>
          <div>Every technical decision tied directly to a business outcome</div>
        </div>
      </div>
    </div>
  </section>

  <div class="ornament">✦</div>

  <!-- ╔══════════ CTA ══════════╗ -->
  <section id="cta">
    <div class="section-label reveal" style="justify-content:center">08 — Let's Build</div>

    <h2 class="cta-heading reveal reveal-delay-1">
      Ready to build<br/>something <em>real?</em>
    </h2>

    <p class="cta-sub reveal reveal-delay-2">2 project slots currently available.</p>

    <p class="cta-note reveal reveal-delay-3">
      The best way to start is simple — tell me what you're building, your rough timeline,
      and a budget range. No lengthy RFPs. No NDAs before hello.
      <strong>Just a real conversation between two professionals.</strong>
    </p>

    <div class="cta-buttons reveal reveal-delay-4">
      <a href="mailto:your@email.com" class="btn-primary">→ Send a Message</a>
      <a href="https://calendly.com/yourhandle" class="btn-ghost">Book Free 30-Min Call</a>
    </div>

    <div class="contact-row reveal reveal-delay-5">
      <a href="mailto:your@email.com" class="contact-link">
        <div class="contact-link-icon">✉</div>
        your@email.com
      </a>
      <a href="https://linkedin.com/in/yourhandle" class="contact-link">
        <div class="contact-link-icon">in</div>
        LinkedIn
      </a>
      <a href="https://github.com/YOURUSERNAME" class="contact-link">
        <div class="contact-link-icon">⌥</div>
        GitHub
      </a>
      <a href="https://t.me/yourhandle" class="contact-link">
        <div class="contact-link-icon">✈</div>
        Telegram
      </a>
      <a href="https://yourportfolio.com" class="contact-link">
        <div class="contact-link-icon">◈</div>
        Portfolio
      </a>
    </div>
  </section>

  <footer>
    <div class="footer-name">Your Name</div>
    <div class="footer-note">
      🇺🇸 USA &nbsp;·&nbsp; 🇬🇧 UK &nbsp;·&nbsp; 🇩🇪 Germany &nbsp;·&nbsp; 🇦🇺 Australia &nbsp;·&nbsp; 🇨🇦 Canada &nbsp;·&nbsp; 🌐 Worldwide
    </div>
    <div class="footer-note">Full Stack Developer &nbsp;·&nbsp; Remote</div>
  </footer>

</div><!-- /page -->

<script>
/* ═══════ STARFIELD ═══════ */
(function(){
  const canvas = document.getElementById('starfield');
  const ctx = canvas.getContext('2d');
  let W, H, stars = [];

  function resize(){
    W = canvas.width  = window.innerWidth;
    H = canvas.height = window.innerHeight;
  }

  function initStars(){
    stars = [];
    const count = Math.floor((W * H) / 3800);
    for(let i = 0; i < count; i++){
      stars.push({
        x: Math.random() * W,
        y: Math.random() * H,
        r: Math.random() * 1.3 + 0.2,
        alpha: Math.random() * 0.7 + 0.15,
        speed: Math.random() * 0.4 + 0.05,
        twinkleSpeed: Math.random() * 0.012 + 0.004,
        twinklePhase: Math.random() * Math.PI * 2,
        gold: Math.random() < 0.12
      });
    }
  }

  let frame = 0;
  function draw(){
    ctx.clearRect(0, 0, W, H);
    frame += 0.008;

    for(let s of stars){
      const twinkle = 0.5 + 0.5 * Math.sin(frame / s.twinkleSpeed * 0.1 + s.twinklePhase);
      const a = s.alpha * (0.4 + 0.6 * twinkle);
      ctx.beginPath();
      ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);

      if(s.gold){
        ctx.fillStyle = `rgba(232, 184, 109, ${a})`;
      } else if(s.r > 1.1){
        ctx.fillStyle = `rgba(240, 234, 216, ${a})`;
      } else {
        ctx.fillStyle = `rgba(180, 176, 154, ${a * 0.7})`;
      }
      ctx.fill();

      /* rare bright stars with glow */
      if(s.r > 1.2 && a > 0.55){
        ctx.beginPath();
        ctx.arc(s.x, s.y, s.r * 2.8, 0, Math.PI * 2);
        ctx.fillStyle = s.gold
          ? `rgba(232, 184, 109, ${a * 0.06})`
          : `rgba(240, 234, 216, ${a * 0.04})`;
        ctx.fill();
      }

      /* slow parallax drift */
      s.y -= s.speed * 0.012;
      if(s.y < -2){ s.y = H + 2; s.x = Math.random() * W; }
    }

    requestAnimationFrame(draw);
  }

  resize();
  initStars();
  draw();
  window.addEventListener('resize', ()=>{ resize(); initStars(); });
})();

/* ═══════ SCROLL REVEAL ═══════ */
(function(){
  const els = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(e=>{
      if(e.isIntersecting){ e.target.classList.add('visible'); io.unobserve(e.target); }
    });
  }, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });
  els.forEach(el => io.observe(el));
})();

/* ═══════ COUNTER ANIMATION ═══════ */
(function(){
  const counters = document.querySelectorAll('.counter[data-target]');
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(e=>{
      if(!e.isIntersecting) return;
      const el = e.target;
      const target = parseInt(el.dataset.target);
      let start = 0;
      const dur = 1800;
      const step = timestamp => {
        if(!start) start = timestamp;
        const progress = Math.min((timestamp - start) / dur, 1);
        const eased = 1 - Math.pow(1 - progress, 3);
        el.textContent = Math.floor(eased * target);
        if(progress < 1) requestAnimationFrame(step);
        else el.textContent = target;
      };
      requestAnimationFrame(step);
      io.unobserve(el);
    });
  }, { threshold: 0.5 });
  counters.forEach(c => io.observe(c));
})();
</script>
</body>
</html>
