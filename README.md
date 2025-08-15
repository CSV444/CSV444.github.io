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
      font-family: Arial, sans-serif;
      background-color: #fdfdfd;
      min-height: 200vh; /* juste pour tester le scroll */
    }

    /* Header sticky avec shadow */
    .site-header {
      position: sticky;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.75rem;
      padding: 1rem 2rem;
      background-color: #fff;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
      z-index: 1000;
    }

    .header-logo {
      width: min(64px, 10vw);
      height: auto;
      transition: transform 0.3s ease;
    }

    .brand-text {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
    }

    .brand-name {
      font-weight: bold;
      font-size: 1.25rem;
    }

    .brand-tag {
      font-size: 0.875rem;
      color: #555;
    }

    /* Suppression des boutons */
    .header-actions {
      display: none;
    }

    /* Option : animation logo au scroll (facultatif) */
    body.scrolled .header-logo {
      transform: scale(0.9);
    }

    @media (max-width: 768px) {
      .site-header {
        padding: 0.75rem 1rem;
        gap: 0.5rem;
      }

      .brand-name {
        font-size: 1.1rem;
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
      <img src="assets/logo.png" alt="Logo CSV" class="header-logo">
      <div class="brand-text">
        <span class="brand-name">CSV Horlogerie</span>
        <span class="brand-tag">Temps & Tradition</span>
      </div>
    </div>
    <div class="header-actions">
      <!-- boutons désactivés -->
    </div>
  </header>

  <main>
    <section style="padding:2rem;">
      <p>Contenu de la page...</p>
      <p>Fais défiler pour voir l’effet sticky et shadow.</p>
    </section>
  </main>

  <script>
    // Optionnel : ajout d'une classe body lors du scroll pour effet sur logo
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
