# AppliToolsDemo
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Selenium Demo – Chaos Page</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    :root {
      --bg: #ffffff;
      --fg: #111111;
      --accent: #4a90e2;
    }
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: var(--bg);
      color: var(--fg);
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .container {
      max-width: 900px;
      padding: 24px;
      border: 3px solid var(--accent);
      border-radius: 10px;
    }
    .title {
      font-size: 2rem;
      margin-bottom: 12px;
      text-align: center;
    }
    .subtitle {
      margin-bottom: 20px;
      opacity: 0.8;
      text-align: center;
    }
    .card {
      border: 1px dashed var(--accent);
      border-radius: 8px;
      padding: 16px;
      margin: 12px;
      flex: 1;
    }
    .btn {
      border: none;
      background: var(--accent);
      color: #fff;
      padding: 10px 16px;
      border-radius: 6px;
      font-weight: bold;
      cursor: pointer;
    }
    .footer {
      margin-top: 20px;
      font-size: 0.9rem;
      opacity: 0.7;
      text-align: center;
    }

    /* Layout variations */
    .layout-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
    }
    .layout-flex {
      display: flex;
      flex-direction: row;
      justify-content: space-around;
    }
    .layout-column {
      display: flex;
      flex-direction: column;
      align-items: stretch;
    }
    .layout-masonry {
      column-count: 2;
      column-gap: 16px;
    }
    .layout-masonry .card {
      display: inline-block;
      width: 100%;
    }
  </style>
</head>
<body>
  <main class="container" id="container">
    <h1 class="title" id="title">Loading…</h1>
    <p class="subtitle" id="subtitle">Please wait while we surprise you.</p>

    <div id="cards">
      <section class="card" id="card-1">
        <p id="card-1-text">Random content appears here.</p>
        <button class="btn" id="cta-btn">Click me</button>
      </section>

      <section class="card" id="card-2">
        <p id="card-2-text">And here, too.</p>
      </section>
    </div>

    <div class="footer" id="footer">
      <small>Demo page for Selenium & Applitools</small>
    </div>
  </main>

  <script>
    // Random string generator for IDs/classes
    const randToken = (len = 6) =>
      Math.random().toString(36).substring(2, 2 + len);

    // Random theme
    const randHue = () => Math.floor(Math.random() * 360);
    const theme = (() => {
      const hue = randHue();
      return {
        bg: `hsl(${hue}, 80%, 95%)`,
        fg: `hsl(${(hue+180)%360}, 30%, 20%)`,
        accent: `hsl(${hue}, 70%, 50%)`
      };
    })();
    document.documentElement.style.setProperty('--bg', theme.bg);
    document.documentElement.style.setProperty('--fg', theme.fg);
    document.documentElement.style.setProperty('--accent', theme.accent);

    // Random content
    const messages = [
      "Visual AI > brittle locators.",
      "Every refresh is unique.",
      "Selectors change, eyes don’t.",
      "Testing made resilient.",
      "Automation needs stability."
    ];
    const tips = [
      "Snapshot your DOM—watch selectors mutate.",
      "Refresh again—notice the chaos.",
      "Visual testing beats locator fragility.",
      "Applitools thrives in randomness.",
      "Selenium scripts break here."
    ];
    document.getElementById('title').textContent =
      messages[Math.floor(Math.random() * messages.length)];
    document.getElementById('subtitle').textContent =
      tips[Math.floor(Math.random() * tips.length)];
    document.getElementById('card-1-text').textContent =
      messages[Math.floor(Math.random() * messages.length)];
    document.getElementById('card-2-text').textContent =
      tips[Math.floor(Math.random() * tips.length)];

    // Rotate locators invisibly
    const rotateLocators = (el, base) => {
      const id = `${base}-${randToken()}`;
      const cls = `${base}__${randToken()}`;
      el.id = id;
      el.className = cls;
      el.setAttribute('data-role', randToken());
    };
    rotateLocators(document.getElementById('container'), 'container');
    rotateLocators(document.querySelector('section'), 'card');
    rotateLocators(document.querySelectorAll('section')[1], 'card');
    rotateLocators(document.getElementById('cta-btn'), 'button');

    // Random layout assignment
    const layouts = ["layout-grid", "layout-flex", "layout-column", "layout-masonry"];
    const chosen = layouts[Math.floor(Math.random() * layouts.length)];
    document.getElementById('cards').classList.add(chosen);

    // Button accent change
    const btn = document.querySelector('button');
    btn.addEventListener('click', () => {
      document.documentElement.style.setProperty('--accent', `hsl(${randHue()}, 70%, 50%)`);
      btn.textContent = "Changed!";
    });
  </script>
</body>
</html>
