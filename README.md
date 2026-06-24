# web-hmjti2
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>HMJ-TI UNISM</title>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=Lora:ital,wght@0,600;1,400&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --merah: #880000; --merah-gelap: #5c0000; --merah-muda: #fdf0f0;
      --emas: #c9a84c; --putih: #ffffff; --abu-terang: #f7f7f7;
      --abu: #6b6b6b; --hitam: #1a1a1a;
      --font-display: 'Lora', serif; --font-body: 'Plus Jakarta Sans', sans-serif;
    }
    html { scroll-behavior: smooth; }
    body { font-family: var(--font-body); color: var(--hitam); background: var(--putih); }

    nav {
      position: sticky; top: 0; z-index: 100; background: var(--merah);
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 5%; box-shadow: 0 2px 12px rgba(136,0,0,0.3);
    }
    .nav-logo { display: flex; align-items: center; gap: 12px; padding: 14px 0; text-decoration: none; }
    .nav-logo img { height: 44px; width: 44px; object-fit: contain; }
    .nav-logo span { color: var(--putih); font-weight: 800; font-size: 1rem; line-height: 1.2; }
    .nav-logo span small { display: block; font-weight: 400; font-size: 0.72rem; opacity: 0.8; }
    .nav-links { display: flex; gap: 4px; }
    .nav-links a {
      color: rgba(255,255,255,0.88); text-decoration: none;
      padding: 10px 16px; border-radius: 6px; font-size: 0.88rem; font-weight: 600; letter-spacing: 0.02em;
      transition: background 0.2s, color 0.2s;
    }
    .nav-links a:hover, .nav-links a.active { background: rgba(255,255,255,0.15); color: #fff; }
    .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; padding: 10px; }
    .hamburger span { width: 24px; height: 2px; background: #fff; border-radius: 2px; }

    .hero {
      background: linear-gradient(135deg, var(--merah-gelap) 0%, var(--merah) 60%, #b52020 100%);
      color: #fff; padding: 80px 5% 70px;
      display: flex; align-items: center; justify-content: space-between; gap: 40px;
      min-height: 420px; position: relative; overflow: hidden;
    }
    .hero::before {
      content: ''; position: absolute; inset: 0;
      background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.04'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
    }
    .hero-text { position: relative; max-width: 560px; }
    .hero-eyebrow {
      display: inline-block; background: rgba(255,255,255,0.15);
      border: 1px solid rgba(255,255,255,0.3); color: #fff; font-size: 0.78rem; font-weight: 700;
      letter-spacing: 0.1em; text-transform: uppercase; padding: 5px 14px; border-radius: 100px; margin-bottom: 20px;
    }
    .hero h1 { font-family: var(--font-display); font-size: clamp(1.8rem, 4vw, 2.8rem); line-height: 1.2; margin-bottom: 18px; }
    .hero h1 em { font-style: italic; color: var(--emas); }
    .hero p { font-size: 1rem; opacity: 0.85; line-height: 1.7; margin-bottom: 30px; max-width: 480px; }
    .hero-cta { display: flex; gap: 12px; flex-wrap: wrap; }
    .btn {
      display: inline-block; text-decoration: none; font-weight: 700;
      padding: 11px 24px; border-radius: 8px; font-size: 0.9rem;
      transition: transform 0.15s, box-shadow 0.15s; cursor: pointer; border: none;
    }
    .btn:hover { transform: translateY(-2px); box-shadow: 0 6px 18px rgba(0,0,0,0.2); }
    .btn-putih { background: #fff; color: var(--merah); }
    .btn-outline { background: transparent; color: #fff; border: 2px solid rgba(255,255,255,0.5); }
    .btn-outline:hover { border-color: #fff; }
    .hero-img { position: relative; flex-shrink: 0; }
    .hero-img img { width: 200px; height: 200px; object-fit: contain; filter: drop-shadow(0 8px 32px rgba(0,0,0,0.4)); animation: float 4s ease-in-out infinite; }
    @keyframes float { 0%,100% { transform: translateY(0); } 50% { transform: translateY(-12px); } }

    section { padding: 72px 5%; }
    .section-label {
      display: inline-flex; align-items: center; gap: 8px;
      color: var(--merah); font-size: 0.78rem; font-weight: 700; letter-spacing: 0.1em;
      text-transform: uppercase; margin-bottom: 10px;
    }
    .section-label::before { content: ''; width: 20px; height: 2px; background: var(--merah); }
    h2.section-title { font-family: var(--font-display); font-size: clamp(1.5rem, 3vw, 2.1rem); color: var(--hitam); margin-bottom: 8px; }
    .section-sub { color: var(--abu); font-size: 0.95rem; line-height: 1.7; max-width: 540px; }

    #berita { background: var(--putih); }
    .berita-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 24px; margin-top: 40px; }
    .berita-card {
      border: 1px solid #ebebeb; border-radius: 12px; overflow: hidden;
      transition: box-shadow 0.2s, transform 0.2s; text-decoration: none; color: inherit; display: flex; flex-direction: column;
    }
    .berita-card:hover { box-shadow: 0 8px 28px rgba(136,0,0,0.12); transform: translateY(-3px); }
    .berita-img {
      height: 180px; background: linear-gradient(135deg, var(--merah) 0%, var(--merah-gelap) 100%);
      display: flex; align-items: center; justify-content: center; font-size: 3rem;
    }
    .berita-body { padding: 20px; flex: 1; display: flex; flex-direction: column; gap: 8px; }
    .berita-tanggal { font-size: 0.75rem; color: var(--abu); }
    .berita-body h3 { font-size: 0.95rem; font-weight: 700; line-height: 1.5; color: var(--hitam); }
    .berita-body p { font-size: 0.85rem; color: var(--abu); line-height: 1.6; flex: 1; }
    .berita-read { font-size: 0.82rem; font-weight: 700; color: var(--merah); margin-top: 4px; }
    .lihat-semua { text-align: center; margin-top: 36px; }

    #tentang { background: var(--merah-muda); }
    .tentang-wrap { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center; }
    .tentang-img-box {
      background: linear-gradient(135deg, var(--merah) 0%, var(--merah-gelap) 100%);
      border-radius: 16px; padding: 48px; display: flex; align-items: center; justify-content: center;
    }
    .tentang-img-box img { width: 220px; height: 220px; object-fit: contain; filter: drop-shadow(0 8px 24px rgba(0,0,0,0.3)); }
    .tentang-text { display: flex; flex-direction: column; gap: 20px; }
    .tentang-text p { color: var(--abu); line-height: 1.8; }
    .stat-row { display: flex; gap: 32px; margin-top: 8px; }
    .stat { text-align: center; }
    .stat strong { display: block; font-size: 1.8rem; font-weight: 800; color: var(--merah); }
    .stat span { font-size: 0.8rem; color: var(--abu); }

    #visimisi { background: var(--putih); }
    .visimisi-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 32px; margin-top: 40px; }
    .visimisi-card { border-radius: 16px; padding: 36px; position: relative; overflow: hidden; }
    .visimisi-card.visi { background: var(--merah); color: #fff; }
    .visimisi-card.misi { background: var(--abu-terang); color: var(--hitam); border: 1px solid #e8e8e8; }
    .visimisi-card h3 { font-family: var(--font-display); font-size: 1.3rem; margin-bottom: 16px; }
    .visimisi-card.visi h3 { color: var(--emas); }
    .visimisi-card p, .visimisi-card li { font-size: 0.92rem; line-height: 1.8; }
    .visimisi-card.visi p { opacity: 0.9; }
    .misi-list { list-style: none; display: flex; flex-direction: column; gap: 10px; }
    .misi-list li { display: flex; gap: 10px; align-items: flex-start; }
    .misi-list li::before {
      content: '✓'; display: inline-flex; align-items: center; justify-content: center;
      width: 20px; height: 20px; background: var(--merah); color: #fff;
      border-radius: 50%; font-size: 0.7rem; font-weight: 900; flex-shrink: 0; margin-top: 2px;
    }
    .visimisi-deco { position: absolute; right: -20px; bottom: -20px; width: 120px; height: 120px; border-radius: 50%; background: rgba(255,255,255,0.08); }

    #pengurus { background: var(--abu-terang); }
    .pengurus-pimpinan { display: grid; grid-template-columns: repeat(2, 1fr); gap: 24px; max-width: 600px; margin: 40px auto 56px; }
    .pengurus-card {
      background: #fff; border-radius: 16px; overflow: hidden;
      box-shadow: 0 2px 12px rgba(0,0,0,0.06); text-align: center;
      transition: box-shadow 0.2s, transform 0.2s;
    }
    .pengurus-card:hover { box-shadow: 0 8px 28px rgba(136,0,0,0.12); transform: translateY(-3px); }
    .pengurus-foto {
      height: 180px; background: linear-gradient(160deg, var(--merah) 0%, var(--merah-gelap) 100%);
      display: flex; align-items: flex-end; justify-content: center; overflow: hidden;
    }
    .pengurus-foto img { width: 130px; object-fit: cover; object-position: top; }
    .pengurus-foto .emoji { font-size: 4rem; padding-bottom: 16px; }
    .pengurus-info { padding: 18px 16px; }
    .pengurus-info h4 { font-size: 0.95rem; font-weight: 700; color: var(--hitam); margin-bottom: 4px; }
    .pengurus-jabatan { display: inline-block; background: var(--merah-muda); color: var(--merah); font-size: 0.72rem; font-weight: 700; padding: 3px 10px; border-radius: 100px; }

    .divisi-title { text-align: center; font-family: var(--font-display); font-size: 1.2rem; color: var(--hitam); margin-bottom: 20px; }
    .divisi-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 16px; }
    .divisi-card { background: #fff; border-radius: 12px; padding: 20px; border-left: 4px solid var(--merah); box-shadow: 0 2px 8px rgba(0,0,0,0.05); }
    .divisi-card h4 { font-size: 0.82rem; font-weight: 800; color: var(--merah); text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 6px; }
    .divisi-card p { font-size: 0.85rem; color: var(--abu); line-height: 1.6; margin-bottom: 10px; }
    .divisi-card .koordinator { font-size: 0.82rem; font-weight: 700; color: var(--hitam); }

    #pengumuman { background: var(--putih); }
    .pengumuman-list { display: flex; flex-direction: column; gap: 16px; margin-top: 40px; }
    .pengumuman-item {
      display: flex; gap: 20px; align-items: flex-start;
      padding: 20px 24px; border-radius: 12px; border: 1px solid #ebebeb;
      text-decoration: none; color: inherit; transition: box-shadow 0.2s, border-color 0.2s;
    }
    .pengumuman-item:hover { box-shadow: 0 4px 16px rgba(136,0,0,0.1); border-color: var(--merah); }
    .pengumuman-date { flex-shrink: 0; text-align: center; background: var(--merah-muda); border-radius: 10px; padding: 10px 14px; line-height: 1.2; }
    .pengumuman-date strong { display: block; font-size: 1.4rem; font-weight: 800; color: var(--merah); }
    .pengumuman-date span { font-size: 0.75rem; color: var(--abu); text-transform: uppercase; }
    .pengumuman-body h4 { font-size: 0.97rem; font-weight: 700; margin-bottom: 5px; }
    .pengumuman-body p { font-size: 0.85rem; color: var(--abu); line-height: 1.6; }
    .badge { display: inline-block; font-size: 0.7rem; font-weight: 700; padding: 2px 9px; border-radius: 100px; margin-bottom: 6px; }
    .badge-penting { background: #fff3cd; color: #856404; }
    .badge-info { background: #d1ecf1; color: #0c5460; }

    #periode { background: var(--merah-muda); }
    .periode-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap: 20px; margin-top: 40px; }
    .periode-card { background: #fff; border-radius: 12px; overflow: hidden; text-align: center; box-shadow: 0 2px 8px rgba(0,0,0,0.06); transition: box-shadow 0.2s, transform 0.2s; }
    .periode-card:hover { box-shadow: 0 6px 20px rgba(136,0,0,0.12); transform: translateY(-3px); }
    .periode-foto { height: 140px; background: linear-gradient(160deg, var(--merah) 0%, var(--merah-gelap) 100%); display: flex; align-items: center; justify-content: center; font-size: 3rem; }
    .periode-info { padding: 16px 12px; }
    .periode-info h4 { font-size: 0.88rem; font-weight: 700; margin-bottom: 4px; }
    .periode-info p { font-size: 0.75rem; color: var(--abu); line-height: 1.5; }
    .periode-tahun { display: inline-block; background: var(--merah); color: #fff; font-size: 0.7rem; font-weight: 800; padding: 3px 10px; border-radius: 100px; margin-top: 6px; }

    /* LOGO FOOTER */
    .footer-logo-img { height: 56px; width: 56px; object-fit: contain; }

    footer { background: var(--merah-gelap); color: rgba(255,255,255,0.8); padding: 56px 5% 28px; }
    .footer-grid { display: grid; grid-template-columns: 2fr 1fr 1fr; gap: 48px; margin-bottom: 40px; }
    .footer-brand { display: flex; flex-direction: column; gap: 14px; }
    .footer-brand strong { color: #fff; font-size: 1rem; }
    .footer-brand p { font-size: 0.85rem; line-height: 1.7; opacity: 0.75; }
    .footer-col h5 { color: var(--emas); font-size: 0.8rem; text-transform: uppercase; letter-spacing: 0.08em; margin-bottom: 14px; }
    .footer-col a { display: block; color: rgba(255,255,255,0.7); text-decoration: none; font-size: 0.875rem; margin-bottom: 9px; transition: color 0.2s; }
    .footer-col a:hover { color: #fff; }
    .footer-bottom { border-top: 1px solid rgba(255,255,255,0.12); padding-top: 24px; display: flex; justify-content: space-between; align-items: center; font-size: 0.8rem; opacity: 0.6; flex-wrap: wrap; gap: 8px; }

    @media (max-width: 768px) {
      .nav-links { display: none; flex-direction: column; position: absolute; top: 100%; left: 0; right: 0; background: var(--merah-gelap); padding: 12px 5%; }
      .nav-links.open { display: flex; }
      .hamburger { display: flex; }
      nav { position: relative; flex-wrap: wrap; }
      .hero { flex-direction: column; text-align: center; padding: 56px 5% 48px; }
      .hero-cta { justify-content: center; }
      .hero-img img { width: 150px; height: 150px; }
      .tentang-wrap, .visimisi-grid { grid-template-columns: 1fr; }
      .footer-grid { grid-template-columns: 1fr; }
      .pengurus-pimpinan { grid-template-columns: 1fr 1fr; max-width: 100%; }
      .stat-row { gap: 20px; }
    }
  </style>
</head>
<body>

<nav id="navbar">
  <a href="#" class="nav-logo">
    <img src="data:image/png;base64,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
