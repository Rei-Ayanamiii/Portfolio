<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Mori Lopez | Portfolio</title>

  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #0d1117;
      color: #e6edf3;
    }

    header {
      background: #161b22;
      text-align: center;
      padding: 2rem;
      border-bottom: 1px solid #30363d;
    }

    header h1 {
      margin: 0;
      font-size: 2.5rem;
    }

    header p {
      color: #8b949e;
    }

    nav {
      display: flex;
      justify-content: center;
      background: #161b22;
      position: sticky;
      top: 0;
      border-bottom: 1px solid #30363d;
    }

    nav a {
      color: #e6edf3;
      padding: 1rem;
      text-decoration: none;
      transition: 0.3s;
    }

    nav a:hover {
      background: #21262d;
    }

    section {
      padding: 2rem;
      max-width: 800px;
      margin: auto;
    }

    h2 {
      border-bottom: 1px solid #30363d;
      padding-bottom: 0.5rem;
    }

    .project {
      background: #161b22;
      padding: 1rem;
      margin-bottom: 1rem;
      border-radius: 10px;
      border: 1px solid #30363d;
      transition: 0.3s;
    }

    .project:hover {
      transform: translateY(-5px);
      border-color: #58a6ff;
    }

    a {
      color: #58a6ff;
    }

    footer {
      text-align: center;
      padding: 1rem;
      background: #161b22;
      border-top: 1px solid #30363d;
      color: #8b949e;
    }

    html {
      scroll-behavior: smooth;
    }
  </style>

</head>
<body>

  <header>
    <h1>Mori Lopez</h1>
    <p>IT Support Staff</p>
  </header>

  <nav>
    <a href="#about">About</a>
    <a href="#projects">Projects</a>
    <a href="#contact">Contact</a>
  </nav>

  <section id="about">
    <h2>About Me</h2>
    <p>I Always Live</p>
  </section>

  <section id="projects">
    <h2>Projects</h2>

    <div class="project">
      <h3>Project Title</h3>
      <p>Description of your project.</p>
      <a href="#">View Project</a>
    </div>

    <div class="project">
      <h3>Another Project</h3>
      <p>Description here.</p>
      <a href="#">View Project</a>
    </div>

  </section>

  <section id="contact">
    <h2>Contact</h2>
    <p>Email: your@email.com</p>
    <p>LinkedIn: your link</p>
  </section>

  <footer>
    <p>© 2026 Your Name</p>
  </footer>

  <script>
    console.log("Dark portfolio loaded!");
  </script>

</body>
</html>
