<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Oneness - Gratuit</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
      background: radial-gradient(circle, #1e1e2f, #3b3b5a);
      overflow: hidden;
      color: white;
      text-align: center;
    }

    #profile {
      margin-top: 100px;
      padding: 20px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 15px;
      width: 300px;
      margin-left: auto;
      margin-right: auto;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
      backdrop-filter: blur(10px);
    }

    h1 {
      background: linear-gradient(90deg, #ff758c, #ff7eb3);
      -webkit-background-clip: text;
      color: transparent;
      animation: glow 1.5s infinite alternate;
    }

    @keyframes glow {
      from {
        text-shadow: 0 0 10px #ff758c, 0 0 20px #ff758c, 0 0 30px #ff7eb3;
      }
      to {
        text-shadow: 0 0 5px #ff7eb3, 0 0 15px #ff758c, 0 0 25px #ff7eb3;
      }
    }

    #bio {
      font-size: 1.2em;
      margin: 10px 0;
    }

    button {
      background-color: #007bff;
      color: white;
      border: none;
      padding: 10px 15px;
      border-radius: 5px;
      cursor: pointer;
      font-size: 1rem;
    }

    button:hover {
      background-color: #0056b3;
    }

    /* Effets étoiles */
    .stars {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -1;
    }

    .star {
      position: absolute;
      width: 2px;
      height: 2px;
      background: white;
      border-radius: 50%;
      animation: move 5s linear infinite;
    }

    @keyframes move {
      0% {
        transform: translateY(0) translateX(0);
        opacity: 1;
      }
      100% {
        transform: translateY(100vh) translateX(100px);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <!-- Effets d'étoiles -->
  <div class="stars" id="stars"></div>

  <!-- Profil -->
  <div id="profile">
    <h1 id="username">Pseudo : Anonyme</h1>
    <p id="bio">Bio : Aucune bio.</p>
    <button onclick="editProfile()">Modifier le profil</button>
  </div>

  <script>
    // Animation des étoiles
    function createStars() {
      for (let i = 0; i < 100; i++) {
        const star = document.createElement("div");
        star.classList.add("star");
        star.style.left = Math.random() * 100 + "vw";
        star.style.top = Math.random() * -100 + "vh";
        star.style.animationDelay = Math.random() * 5 + "s";
        document.getElementById("stars").appendChild(star);
      }
    }

    createStars();

    // Modifier le profil
    function editProfile() {
      const username = prompt("Entrez votre pseudo :");
      const bio = prompt("Entrez votre bio :");

      if (username) {
        document.getElementById("username").textContent = `Pseudo : ${username}`;
      }
      if (bio) {
        document.getElementById("bio").textContent = `Bio : ${bio}`;
      }

      // Sauvegarde dans le navigateur
      if (username) localStorage.setItem("username", username);
      if (bio) localStorage.setItem("bio", bio);
    }

    // Charger les données sauvegardées
    window.onload = function () {
      const savedUsername = localStorage.getItem("username");
      const savedBio = localStorage.getItem("bio");

      if (savedUsername) {
        document.getElementById("username").textContent = `Pseudo : ${savedUsername}`;
      }
      if (savedBio) {
        document.getElementById("bio").textContent = `Bio : ${savedBio}`;
      }
    };
  </script>
</body>
</html>
