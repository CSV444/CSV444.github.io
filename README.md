<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSV Horlogerie</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: "Helvetica Neue", Arial, sans-serif;
      background-color: #fdfdfd;
      min-height: 200vh; /* pour tester le scroll */
    }

    /* Header sticky premium */
    .site-header {
      position: sticky;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 1rem;
      padding: 1rem 2rem;
      background-color: #fff;
      box-shadow: 0 4px 10px rgba(0,0,0,0.08);
      z-index: 1000;
      opacity: 0;
      transform: translate(-50%, -20px);
      animation: fadeIn 1s ease forwards;
    }

    /* Animation d’apparition */
    @keyframes fadeIn {
      to {
        opacity: 1;
        transform: translate(-50%, 0);
      }
    }

    /* Logo animé */
    .logo-wrapper {
      position: relative;
      display: inline-block;
      overflow: hidden;
    }

    .header-logo {
      width: min(64px, 10vw);
      height: auto;
      animation: slowRotate 20s linear infinite; /* rotation très lente */
    }

    /* Brillance (reflet métallique) */
    .shine {
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(
        120deg,
        transparent 0%,
        rgba(255, 255, 255, 0.6) 50%,
        transparent 100%
      );
      animation: shineMove 6s linear infinite;
    }

    @keyframes shineMove {
      0% { left: -100%; }
      50% { left: 100%; }
      100% { left: 100%; }
    }

    @keyframes slowRotate {
      from { transform: rotate(0deg); }
      to { transform: rotate(360deg); }
    }

    /* Texte */
    .brand-text {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      transform: translateY(10px);
      opacity: 0;
      animation: slideUp 0.8s ease forwards;
      animation-delay: 0.3s;
    }

    @keyframes slideUp {
      to {
        transform: translateY(0);
        opacity: 1;
      }
    }

    .brand-name {
      font-weight: 700;
      font-size: 1.4rem;
      letter-spacing: 0.5px;
      color: #222;
    }

    .brand-tag {
      font-size: 0.9rem;
      color: #666;
      font-style: italic;
    }

    /* Effet au scroll */
    body.scrolled .header-logo {
      transform: scale(0.85);
    }

    body.scrolled .brand-name {
      font-size: 1.2rem;
    }

    body.scrolled .brand-tag {
      font-size: 0.8rem;
    }

    /* Mobile */
    @media (max-width: 768px) {
      .site-header {
        padding: 0.75rem 1rem;
        gap: 0.5rem;
      }

      .brand-name {
        font-size: 1.2rem;
      }

      .brand-tag {
        font-size: 0.75rem;
      }
    }
  </style>
</head>
<body>

  <header class="site-header">
    <div class="brand">
      <div class="logo-wrapper">
        <img src="assets/logo.png" alt="Logo CSV" class="header-logo">
        <div class="shine"></div>
      </div>
      <div class="brand-text">
        <span class="brand-name">CSV Horlogerie</span>
        <span class="brand-tag">Temps & Tradition</span>
      </div>
    </div>
  </header>

  <main>
    <section style="padding:2rem; max-width:600px; margin:auto; line-height:1.6;">
      <h1>Bienvenue chez CSV Horlogerie</h1>
      <p>
        Découvrez notre passion pour les montres, entre savoir-faire traditionnel et innovations modernes.
      </p>
      <p style="margin-top:1rem;">
        Faites défiler la page pour voir l’effet premium du header animé.
      </p>
    </section>
  </main>

  <script>
    // Ajout d'une classe quand on scrolle
    window.addEventListener('scroll', function() {
      if(window.scrollY > 50){
        document.body.classList.add('scrolled');
      } else {
        document.body.classList.remove('scrolled');
      }
    });
  </script>

</body>
</html>
