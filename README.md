<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="Descubre Nador: Mediterráneo, Marchica y el Rif." />
  <title>Nador — Mediterráneo · Marchica · Rif</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html, body { height: 100%; }
    body {
      font-family: 'Inter', system-ui, sans-serif;
      background: #fff;
      color: #000;
      overflow-x: hidden;
      -webkit-font-smoothing: antialiased;
    }
    button { font-family: inherit; cursor: pointer; border: none; background: none; }
    a { color: inherit; text-decoration: none; }
    video { display: block; max-width: 100%; }

    .page {
      position: relative;
      min-height: 100vh;
      min-height: 100dvh;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      overflow: hidden;
      background: #fff;
    }

    /* Video */
    .video-layer {
      position: absolute;
      inset: 0;
      z-index: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      pointer-events: none;
      animation: videoIn 1.8s cubic-bezier(0.16, 1, 0.3, 1) both;
    }
    .video-wrapper {
      width: 80%;
      height: 80%;
      overflow: hidden;
      border-radius: 12px;
    }
    .video-wrapper video {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    @media (min-width: 768px) {
      .video-wrapper { width: 100%; height: 100%; border-radius: 0; }
    }

    /* Nav */
    .navbar {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 50;
      pointer-events: none;
      padding: 16px;
      animation: navIn 0.8s cubic-bezier(0.16, 1, 0.3, 1) both;
    }
    .navbar-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
    }
    .navbar-left, .navbar-right {
      display: flex;
      align-items: center;
      gap: 10px;
      pointer-events: auto;
    }
    .logo { display: flex; align-items: center; gap: 10px; }
    .logo-icon { width: 28px; height: 28px; flex-shrink: 0; }
    .logo-text {
      display: none;
      font-size: 14px;
      font-weight: 500;
      letter-spacing: -0.02em;
    }
    .menu-btn {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 4px 12px 4px 4px;
      background: #000;
      color: #fff;
      border-radius: 999px;
    }
    .menu-btn-circle {
      width: 28px; height: 28px;
      border-radius: 50%;
      background: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #000;
    }
    .menu-btn-label {
      font-size: 11px;
      font-weight: 500;
      padding-right: 4px;
    }
    .tags-pill, .adaptive-pill { display: none; }
    .tags-pill {
      align-items: center;
      gap: 8px;
      padding: 8px 14px;
      background: #f4f4f6;
      border-radius: 999px;
    }
    .tags-pill span {
      font-size: 11px;
      font-weight: 500;
      opacity: 0.7;
    }
    .tags-pill .divider {
      width: 1px; height: 12px;
      background: rgba(0,0,0,0.15);
    }
    .adaptive-pill {
      align-items: center;
      gap: 10px;
      padding: 4px 14px 4px 4px;
      background: #f4f4f6;
      border-radius: 999px;
    }
    .grid-btn {
      width: 28px; height: 28px;
      border-radius: 50%;
      background: #000;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .adaptive-label {
      font-size: 11px;
      font-weight: 500;
      opacity: 0.75;
    }
    @media (min-width: 768px) {
      .navbar { padding: 24px 32px; }
      .logo-text { display: block; }
      .menu-btn-circle, .grid-btn { width: 32px; height: 32px; }
      .tags-pill, .adaptive-pill { display: flex; }
    }

    /* Footer / hero */
    .footer {
      position: relative;
      z-index: 30;
      margin-top: auto;
      padding: 80px 16px 24px;
      background: linear-gradient(to top, #fff 0%, rgba(255,255,255,0.8) 50%, transparent 100%);
      animation: footerIn 1s cubic-bezier(0.16, 1, 0.3, 1) 0.5s both;
    }
    .footer-inner {
      display: flex;
      flex-direction: column;
      gap: 28px;
      align-items: flex-start;
    }
    .footer-left {
      display: flex;
      flex-direction: column;
      gap: 16px;
      max-width: 720px;
    }
    .subtitle {
      display: flex;
      align-items: center;
      gap: 8px;
      animation: up 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.6s both;
    }
    .subtitle-dot {
      width: 8px; height: 8px;
      border-radius: 50%;
      background: #000;
    }
    .subtitle-text {
      font-size: 13px;
      color: rgba(0,0,0,0.55);
    }
    .heading {
      font-weight: 300;
      font-size: clamp(2rem, 8vw, 4.5rem);
      letter-spacing: -0.03em;
      line-height: 1;
      animation: up 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.8s both;
    }
    .buttons {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 4px;
      animation: up 0.8s cubic-bezier(0.16, 1, 0.3, 1) 1s both;
    }
    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 12px 20px;
      border-radius: 999px;
      font-size: 13px;
      font-weight: 500;
    }
    .btn-primary { background: #000; color: #fff; }
    .btn-secondary {
      background: transparent;
      color: #000;
      border: 1px solid rgba(0,0,0,0.35);
    }
    .footer-right { display: flex; flex-wrap: wrap; gap: 8px; }
    .tech-tag {
      padding: 8px 14px;
      background: #fff;
      border: 1px solid rgba(0,0,0,0.12);
      border-radius: 999px;
      font-size: 11px;
      font-weight: 500;
    }
    @media (min-width: 768px) {
      .footer { padding: 120px 32px 40px; }
      .footer-inner {
        flex-direction: row;
        align-items: flex-end;
        justify-content: space-between;
        gap: 40px;
      }
      .heading { font-size: clamp(2.5rem, 5.5vw, 4.5rem); }
      .footer-right { flex-shrink: 0; padding-bottom: 4px; }
    }

    @keyframes navIn {
      from { opacity: 0; transform: translateY(-16px); }
      to { opacity: 1; transform: translateY(0); }
    }
    @keyframes videoIn {
      from { opacity: 0; transform: scale(1.05); }
      to { opacity: 1; transform: scale(1); }
    }
    @keyframes footerIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    @keyframes up {
      from { opacity: 0; transform: translateY(16px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>
  <div class="page">
    <div class="video-layer">
      <div class="video-wrapper">
        <video
          src="https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260508_215831_c6a8989c-d716-4d8d-8745-e972a2eec711.mp4"
          autoplay
          muted
          playsinline
          loop
        ></video>
      </div>
    </div>

    <nav class="navbar">
      <div class="navbar-inner">
        <div class="navbar-left">
          <a href="/" class="logo" aria-label="Nador">
            <svg class="logo-icon" viewBox="0 0 28 28" fill="none" aria-hidden="true">
              <rect x="4" y="8" width="14" height="8" rx="3" fill="#000" transform="rotate(-35 11 12)" />
              <rect x="10" y="12" width="14" height="8" rx="3" fill="#000" transform="rotate(-35 17 16)" />
            </svg>
            <span class="logo-text">Nador</span>
          </a>
          <button type="button" class="menu-btn" aria-label="Menú">
            <span class="menu-btn-circle">
              <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round">
                <path d="M12 5v14M5 12h14" />
              </svg>
            </span>
            <span class="menu-btn-label">Menú</span>
          </button>
          <div class="tags-pill">
            <span>Mediterráneo</span>
            <span class="divider" aria-hidden="true"></span>
            <span>Marchica</span>
          </div>
        </div>
        <div class="navbar-right">
          <div class="adaptive-pill">
            <span class="grid-btn" aria-hidden="true">
              <svg width="12" height="12" viewBox="0 0 12 12" fill="none">
                <circle cx="2.5" cy="2.5" r="1.2" fill="#fff" />
                <circle cx="9.5" cy="2.5" r="1.2" fill="#fff" />
                <circle cx="2.5" cy="9.5" r="1.2" fill="#fff" />
                <circle cx="9.5" cy="9.5" r="1.2" fill="#fff" />
              </svg>
            </span>
            <span class="adaptive-label">Costa del Rif</span>
          </div>
        </div>
      </div>
    </nav>

    <footer class="footer">
      <div class="footer-inner">
        <div class="footer-left">
          <div class="subtitle">
            <span class="subtitle-dot" aria-hidden="true"></span>
            <span class="subtitle-text">Joya del norte de Marruecos</span>
          </div>
          <h1 class="heading">
            Un mar, mil<br />historias. Nador.
          </h1>
          <div class="buttons">
            <button type="button" class="btn btn-primary">Descubrir Nador</button>
            <button type="button" class="btn btn-secondary">Qué visitar</button>
          </div>
        </div>
        <div class="footer-right">
          <span class="tech-tag">Playas</span>
          <span class="tech-tag">Marchica</span>
          <span class="tech-tag">Rif</span>
        </div>
      </div>
    </footer>
  </div>
</body>
</html>
