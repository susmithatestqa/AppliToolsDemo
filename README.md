<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Applitools Visual Testing Demo</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #800080; /* solid purple background */
      color: #f0f0f0;
      margin: 0;
      padding: 20px;
    }
    h1 {
      font-size: 2rem;
      margin-bottom: 10px;
      transition: color 0.5s ease;
    }
    .static-text {
      font-size: 1.1rem;
      margin-bottom: 20px;
    }
    .button-area {
      display: flex;
      margin-top: 40px;
    }
    button {
      background: #9370db;
      color: white;
      border: none;
      border-radius: 8px;
      padding: 12px 20px;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.5s ease;
    }
  </style>
</head>
<body>
  <h1 id="title">Applitools Visual Testing Demo</h1>

  <!-- Static text about AI role in testing -->
  <div class="static-text">
    Artificial Intelligence plays a crucial role in modern software testing.  
    It helps detect subtle visual differences, adapts to dynamic content,  
    and reduces reliance on brittle locators by focusing on how users actually experience applications.
  </div>

  <div class="button-area" id="buttonArea">
    <button id="actionButton">Click Me</button>
  </div>

  <script>
    // Heading colour changes on refresh
    const title = document.getElementById("title");
    const hue = Math.floor(Math.random() * 360);
    title.style.color = `hsl(${hue}, 70%, 60%)`;

    // Button placement changes on refresh
    const placements = ["flex-start", "center", "flex-end"];
    const buttonArea = document.getElementById("buttonArea");
    buttonArea.style.justifyContent =
      placements[Math.floor(Math.random() * placements.length)];

    const button = document.getElementById("actionButton");
    button.style.marginTop = Math.floor(Math.random() * 50) + "px";
  </script>
</body>
</html>
