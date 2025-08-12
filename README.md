<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>CSV Horlogerie — Temps & Tradition</title>
  <link rel="icon" href="assets/favicon.png" sizes="32x32" />
  <link rel="apple-touch-icon" href="assets/apple-touch-icon.png" />
  <link rel="manifest" href="assets/site.webmanifest" />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;600;700&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    :root{
      --green:#0e4736;
      --green-dark:#0a3528;
      --gold:#d4b675;
      --gold-deep:#b89a57;
      --silver:#e7e7e7;
      --mx: 50;
      --my: 50;
    }

    *{ box-sizing:border-box; }
    html,body{ height:100%; }
    body{
      margin:0; display:flex; align-items:center; justify-content:center; min-height:100vh; color:var(--silver);
      font-family:"Inter", system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji", "Segoe UI Emoji";
      background:
        radial-gradient(1200px 800px at 20% 0%, rgba(255,255,255,0.04), transparent 60%),
        radial-gradient(1000px 700px at 100% 100%, rgba(255,255,255,0.03), transparent 60%),
        repeating-linear-gradient(135deg, rgba(255,255,255,0.02) 0 10px, rgba(0,0,0,0.03) 10px 20px),
        var(--green);
    }

    .frame{ position:relative; width:min(920px, 92vw); aspect-ratio:3/4; padding:4.5rem 3rem; }
    .frame::before{
      content:""; position:absolute; inset:1.25rem; border:3px solid rgba(0,0,0,0.35);
      border-radius:14px; box-shadow:0 0 0 2px rgba(255,255,255,0.06) inset;
    }
    .frame::after{
      content:""; position:absolute; inset:2.2rem; border:2px solid rgba(0,0,0,0.25); border-radius:10px;
      clip-path:path("M 40 0 H calc(100% - 40) Q 100% 0 100% 40 V calc(100% - 40) Q 100% 100% calc(100% - 40) 100% H 40 Q 0 100% 0 calc(100% - 40) V 40 Q 0 0 40 0 Z");
      pointer-events:none;
    }

    .stack{ position:relative; height:100%; display:grid; grid-template-rows: 1fr auto auto; row-gap:1.25rem; }

    .centerpiece{ display:grid; place-items:center; perspective:1000px; }
    .logo-wrap{ position:relative; display:inline-block; transform: rotateX(calc((50 - var(--my)) * 0.18deg)) rotateY(calc((var(--mx) - 50) * 0.18deg)); transition: transform .08s ease-out; }
    .logo-img{ width:min(360px, 64%); height:auto; filter: drop-shadow(0 12px 24px rgba(0,0,0,.45)); }
    .logo-wrap::after{
      content:""; position:absolute; inset:-10%; pointer-events:none;
      background: radial-gradient(180px 120px at calc(var(--mx)*1%) calc(var(--my)*1%), rgba(255,255,255,.45), rgba(255,255,255,.12) 28%, rgba(255,255,255,0) 60%);
      mix-blend-mode:screen; filter: blur(10px); opacity:.55; transition: opacity .3s ease;
    }
    .logo-wrap:hover::after{ opacity:.75; }

    .title{ text-align:center; text-transform:uppercase; letter-spacing:.16em; color:var(--gold);
            font-family:"Cormorant Garamond", serif; font-weight:700; line-height:1.15; }
    .title .small{ display:block; font-size:1rem; letter-spacing:.35em; color:rgba(231,231,231,.8); margin-top:.5rem; font-weight:400; }
    .title .big{ display:block; font-size:1.45rem; color:var(--silver); letter-spacing:.4em; margin-top:.25rem; }
    .title .tagline{ display:block; margin-top:.35rem; font-weight:600; font-size:1.05rem; letter-spacing:.18em; color:rgba(212,182,117,.95); }

    .divider{ display:flex; align-items:center; justify-content:center; gap:.75rem; margin:.5rem 0 1.2rem; opacity:.9; }
    .divider .dot{ width:6px; height:6px; border-radius:50%; background:var(--gold); }

    .actions{ display:flex; gap:1rem; justify-content:center; flex-wrap:wrap; margin-top:.25rem; align-items:center; }
    .btn-icon{
      background:none;
      border:none;
      cursor:pointer;
      padding:0.4rem;
      border-radius:50%;
      transition:transform 0.1s ease;
    }
    .btn-icon img{ width:48px; height:48px; display:block; }
    .btn-icon:hover{ transform:scale(1.05); }

    .btn-gold{
      appearance:none; border:none; cursor:pointer; padding:.9rem 1.2rem; border-radius:999px; font-weight:600; letter-spacing:.06em; text-transform:uppercase; font-size:.86rem; text-decoration:none; color:#1a1a1a; background:linear-gradient(180deg, #f0dca6, var(--gold));
      box-shadow:0 6px 18px rgba(0,0,0,.35), inset 0 1px 0 rgba(255,255,255,.35); transition:transform .08s ease, filter .2s ease, background .2s ease;
    }
    .btn-gold:hover{ transform:translateY(-1px); background:linear-gradient(180deg, #f5e4b9, var(--gold-deep)); filter:saturate(1.05); }
    .btn-gold:active{ transform:translateY(0); }

    .legal{ text-align:center; font-size:.8rem; letter-spacing:.25em; text-transform:uppercase; color:rgba(231,231,231,.7); }
    /* Header bandeau */
    .site-header{ position:absolute; top:2.2rem; left:2.6rem; right:2.6rem; display:flex; align-items:center; justify-content:space-between; pointer-events:auto; }
    .brand{ display:flex; align-items:center; gap:.75rem; }
    .header-logo{ width:44px; height:44px; object-fit:contain; filter: drop-shadow(0 4px 10px rgba(0,0,0,.35)); }
    .brand-text{ line-height:1.05; }
    .brand-name{ font-family:"Cormorant Garamond", serif; font-weight:700; letter-spacing:.12em; text-transform:uppercase; color:var(--gold); font-size:1.05rem; }
    .brand-tag{ display:block; font-size:.72rem; color:rgba(231,231,231,.8); letter-spacing:.2em; text-transform:uppercase; }
    /* Header bandeau */
    .site-header{ position:absolute; top:2.2rem; left:2.6rem; right:2.6rem; display:flex; align-items:center; justify-content:space-between; pointer-events:auto; }
    .brand{ display:flex; align-items:center; gap:.75rem; }
    .header-logo{ width:44px; height:44px; object-fit:contain; filter: drop-shadow(0 4px 10px rgba(0,0,0,.35)); }
    .brand-text{ line-height:1.05; }
    .brand-name{ font-family:"Cormorant Garamond", serif; font-weight:700; letter-spacing:.12em; text-transform:uppercase; color:var(--gold); font-size:1.05rem; }
    .brand-tag{ display:block; font-size:.72rem; color:rgba(231,231,231,.8); letter-spacing:.2em; text-transform:uppercase; }
    .header-actions{ display:flex; align-items:center; gap:.6rem; }
    .btn-sm{ padding:.6rem 1rem; font-size:.78rem; }
  </style>
</head>
<body>
  <main class="frame" role="main" aria-label="CSV Horlogerie — vitrine">
    <header class="site-header" aria-label="En-tête">
      <div class="brand">
        <img src="assets/logo-csv.png" alt="Logo CSV" class="header-logo" />
        <div class="brand-text">
          <span class="brand-name">CSV Horlogerie</span>
          <span class="brand-tag">Temps & Tradition</span>
        </div>
      </div>
    </header>
      <nav class="header-actions" aria-label="Actions en-tête">
        <a class="btn-gold btn-sm" href="mailto:contact@tondomaine.fr">Contact</a>
        <a class="btn-gold btn-sm" href="https://wa.me/XXXXXXXXXXX" target="_blank" rel="noopener" aria-label="Ouvrir WhatsApp">WhatsApp</a>
      </nav>
    <div class="stack">

      <section class="centerpiece" aria-label="logo principal">
        <div class="logo-wrap" id="logoWrap">
          <img src="assets/logo-csv.png" alt="Logo CSV Horlogerie" class="logo-img" />
        </div>
      </section>

      <section aria-label="titres">
        <h1 class="title" style="margin:0">
          <span class="small">L'UNIVERS CSV</span>
          <span class="big">TEMPS ET TRADITION</span>
          <span class="tagline">Atelier & Négoce de Montres</span>
        </h1>
        <div class="divider" aria-hidden="true"><span class="dot"></span><span class="dot"></span><span class="dot"></span></div>
      </section>

      <nav class="actions" aria-label="Réseaux et paiement">
        <a class="btn-icon" href="https://urldefense.com/v3/__https://www.instagram.com/noahsrl___/profilecard/?igsh=MTc2cW10ZDN4dzNwNQ==__;!!N-YFn6XDn0i53t4!2YG7SzYgOQfDrzvWMpIlSvQ5khAM5hLqLHUF7xGzy2g6r5v5mWNkhVqA2uMxP581oEkMISy4gvUMhpSsOkS2kenJjQWP$" target="_blank" rel="noopener"><img src="assets/logo-instagram.png" alt="Instagram"></a>
        <a class="btn-gold" href="https://buy.stripe.com/ton_lien" target="_blank" rel="noopener">Acquérir la formation</a>
        <a class="btn-icon" href="https://www.tiktok.com/@csvj444" target="_blank" rel="noopener"><img src="logo-csv.png" alt="TikTok"></a>
      </nav>

      <p class="legal">Maison indépendante — CSV Horlogerie</p>

    </div>
  </main>

  <script>
    (function(){
      // Effet parallax
      const root = document.documentElement;
      const frame = document.querySelector('.frame');
      function update(e){
        const r = frame.getBoundingClientRect();
        const x = ((e.clientX - r.left) / r.width) * 100;
        const y = ((e.clientY - r.top) / r.height) * 100;
        root.style.setProperty('--mx', x.toFixed(2));
        root.style.setProperty('--my', y.toFixed(2));
      }
      frame.addEventListener('mousemove', update);
      frame.addEventListener('touchmove', function(ev){
        if(!ev.touches || !ev.touches[0]) return;
        const t = ev.touches[0];
        update({ clientX:t.clientX, clientY:t.clientY });
      }, { passive:true });

      // Rendu robuste des logos : essaie plusieurs noms de fichiers
      const candidates = {
        ig: [
          'assets/logo-instagram.png',
          'assets/instagram-logo.png',
          'assets/instagram.png',
          'assets/ig.png'
        ],
        tk: [
          'assets/logo-tiktok.png',
          'assets/tiktok-logo.png',
          'assets/tiktok.png',
          'assets/tt.png'
        ],
        brand: [ 'assets/logo-csv.png' ]
      };

      function tryLoad(imgEl, list){
        let i = 0;
        function next(){
          if(i >= list.length){ return; }
          const src = list[i++];
          const test = new Image();
          test.onload = () => { imgEl.src = src; };
          test.onerror = next;
          test.src = src;
        }
        next();
      }

      tryLoad(document.querySelector('img[alt="Instagram"]'), candidates.ig);
      tryLoad(document.querySelector('img[alt="TikTok"]'), candidates.tk);
      tryLoad(document.querySelector('img[alt="Logo CSV Horlogerie"]'), candidates.brand);
    })();
  </script>
</body>
</html>
