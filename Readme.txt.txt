Codigo INDEX:



<!DOCTYPE html>
<html lang="es">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="icon" href="img/flowers.png" type="image/x-icon">
  <title>Flowers</title>

  <style>
    body {
      display: flex;
      flex-direction: column;
      width: 100%;
      height: 100vh;
      justify-content: center;
      align-items: center;
      background-color: #fce4ec;
      margin: 0;
      font-family: Arial, sans-serif;
    }

    .container {
      width: 300px;
      text-align: center;
      padding: 20px;
      background-color: #fff;
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.25);
      border-radius: 10px;
      margin-bottom: 20px;
    }

    .container h2 {
      font-size: 1.7rem;
    }

    .input-display {
      text-align: center;
      margin: 10px 0;
      font-size: 30px;
    }

    .keypad {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;
    }

    .keypad button {
      padding: 15px;
      font-size: 25px;
      background-color: #f8bbd0;
      border: 1px black solid;
      outline: none;
      cursor: pointer;
      transition: background 0.2s;
      border-radius: 8px;
    }

    .keypad button:hover {
      background-color: #f48fb1;
    }

    .keypad button:last-child {
      grid-column: 2/3;
    }

    /* Ocultar saludo al inicio */
    .greetings,
    .description,
    .button {
      display: none;
      text-align: center;
    }

    .greetings {
      font-size: 2rem;
      margin: 20px 0;
    }

    .greetings span {
      opacity: 0;
      display: inline-block;
      font-size: 2.5rem;
      transition: opacity 0.3s ease;
    }

    .description {
      font-size: 1.2rem;
      margin-bottom: 20px;
      min-height: 1.5em; /* espacio reservado */
    }

    .botones {
      display: inline-block;
      padding: 12px 24px;
      background-color: #f48fb1;
      color: #fff;
      text-decoration: none;
      font-size: 1.1rem;
      border-radius: 8px;
      transition: background 0.3s;
      animation: bounceIn 0.8s ease, glow 1.5s infinite alternate;
    }

    .botones:hover {
      background-color: #ec407a;
    }

    /* Animación de rebote */
    @keyframes bounceIn {
      0% {
        transform: scale(0.5);
        opacity: 0;
      }
      60% {
        transform: scale(1.2);
        opacity: 1;
      }
      100% {
        transform: scale(1);
      }
    }

    /* Animación de brillo */
    @keyframes glow {
      0% {
        box-shadow: 0 0 5px #f48fb1, 0 0 10px #f48fb1, 0 0 20px #f48fb1;
      }
      100% {
        box-shadow: 0 0 15px #ec407a, 0 0 30px #ec407a, 0 0 45px #ec407a;
      }
    }
  </style>
</head>

<body>

  <!-- Pantalla de login -->
  <div class="container" id="loginBox">
    <h2>
      🔒<br />
      Ingrese la contraseña
    </h2>
    <div class="input-display" id="inputDisplay">••••</div>
    <div class="keypad">
      <button class="key" onclick="enterDigit('1')">1</button>
      <button class="key" onclick="enterDigit('2')">2</button>
      <button class="key" onclick="enterDigit('3')">3</button>
      <button class="key" onclick="enterDigit('4')">4</button>
      <button class="key" onclick="enterDigit('5')">5</button>
      <button class="key" onclick="enterDigit('6')">6</button>
      <button class="key" onclick="enterDigit('7')">7</button>
      <button class="key" onclick="enterDigit('8')">8</button>
      <button class="key" onclick="enterDigit('9')">9</button>
      <button class="key" onclick="enterDigit('0')">0</button>
    </div>
  </div>

  <!-- Pantalla de saludo -->
  <div class="greetings" id="greetings">
    <span>H</span>
    <span>o</span>
    <span>l</span>
    <span>a</span>
    <span>💗</span>
  </div>

  <div class="description" id="description"></div>

  <div class="button" id="buttonBox">
    <a href="flower.html" class="botones">DA CLICK AQUÍ</a>
  </div>

  <script>
    const correctPassword = "1999";
    const display = document.getElementById("inputDisplay");
    const loginBox = document.getElementById("loginBox");
    const greetings = document.getElementById("greetings");
    const description = document.getElementById("description");
    const buttonBox = document.getElementById("buttonBox");

    let input = "";

    function enterDigit(digit) {
      if (input.length < 4) {
        input += digit;
      }
      display.textContent = input.padEnd(4, "•");

      if (input.length === 4) {
        if (input === correctPassword) {
          // Ocultar login
          loginBox.style.display = "none";

          // Mostrar saludo
          greetings.style.display = "block";
          description.style.display = "block";
          buttonBox.style.display = "block";

          // Animar letras del "Hola 💗"
          const letters = greetings.querySelectorAll("span");
          letters.forEach((letter, index) => {
            setTimeout(() => {
              letter.style.opacity = 1;
            }, index * 400);
          });

          // Cuando termine "Hola 💗", escribir el texto
          setTimeout(() => {
            typeWriter("De Quique para Mich 💗", description, 80);
          }, letters.length * 400 + 500);

        } else {
          alert("Contraseña incorrecta, intenta de nuevo");
          input = "";
          display.textContent = "••••";
        }
      }
    }

    // Efecto máquina de escribir
    function typeWriter(text, element, speed) {
      let i = 0;
      element.textContent = "";
      const interval = setInterval(() => {
        element.textContent += text.charAt(i);
        i++;
        if (i >= text.length) {
          clearInterval(interval);
        }
      }, speed);
    }
  </script>

</body>
</html>












-------------------codigo Flowers-----------------------------




<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Flor eterna Mich</title>
    <style>
      * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
      }

      :root {
       --color-bg: linear-gradient(to top, #111205, #000000); /* fondo negro degradado */
        --line-color: linear-gradient(
          to left top,
          #82ff86 20%,
          #144425,
          #104e1c
        );
        --flower-center: radial-gradient(circle, #000, #ff5e00);
        --leaf-color: radial-gradient(circle, #82ff86, #104e1c);
        --petal-color: radial-gradient(circle, #ff5e00, #ffbb00);
      }

      body {
        background-image: var(--color-bg);
        min-height: 100vh;
        display: flex;
        align-items: flex-end;
        justify-content: center;
        overflow: hidden;
      }

      h1 {
        position: absolute;
        top: 20px;
        text-align: center;
        width: 100%;
        color: #fff;
        font-family: "Poppins", sans-serif;
        font-weight: 300;
        font-size: 28px;
      }
    

      .flower_wrapper {
        position: absolute;
        left: 50%;
        bottom: 20px;
        transform: translateX(-50%);
        z-index: 5;
      }

      .flower_stem {
        width: 20px;
        height: 400px;
        background-image: var(--line-color);
        border-radius: 20px;
      }

      .flower_center {
        position: absolute;
        top: -93px;
        left: 50%;
        transform: translateX(-50%);
        width: 150px;
        height: 150px;
        border-radius: 50%;
        background: var(--flower-center);
        z-index: 5;
        opacity: 0;
        animation: open-flower-center 1s ease-out forwards;
        animation-delay: 1s;
      }

      .flower_petal {
        position: absolute;
        width: 70px;
        height: 140px;
        background: var(--petal-color);
        clip-path: ellipse(35% 50% at 50% 50%);
        top: -40%;
        left: 50%;
        transform-origin: center bottom;
        opacity: 0;
        animation: open-flower-petal 1s ease-out forwards;
      }

      .flower_petal-1 {
        --rotate-deg: 0deg;
        animation-delay: 1.2s;
      }
      .flower_petal-2 {
        --rotate-deg: 30deg;
        animation-delay: 1.25s;
      }
      .flower_petal-3 {
        --rotate-deg: 60deg;
        animation-delay: 1.3s;
      }
      .flower_petal-4 {
        --rotate-deg: 90deg;
        animation-delay: 1.35s;
      }
      .flower_petal-5 {
        --rotate-deg: 120deg;
        animation-delay: 1.4s;
      }
      .flower_petal-6 {
        --rotate-deg: 150deg;
        animation-delay: 1.45s;
      }
      .flower_petal-7 {
        --rotate-deg: 180deg;
        animation-delay: 1.5s;
      }
      .flower_petal-8 {
        --rotate-deg: 210deg;
        animation-delay: 1.55s;
      }
      .flower_petal-9 {
        --rotate-deg: 240deg;
        animation-delay: 1.6s;
      }
      .flower_petal-10 {
        --rotate-deg: 270deg;
        animation-delay: 1.65s;
      }
      .flower_petal-11 {
        --rotate-deg: 300deg;
        animation-delay: 1.7s;
      }
      .flower_petal-12 {
        --rotate-deg: 330deg;
        animation-delay: 1.75s;
      }

      .flower_leaf {
        position: absolute;
        width: 70px;
        height: 120px;
        background: var(--leaf-color);
        border-radius: 100px 20px 100px 20px;
        transform-origin: center bottom;
      }

      .flower_leaf-1 {
        left: 60%;
        bottom: 150px;
        transform: translateX(-45%) rotate(80deg);
      }

      .flower_leaf-2 {
        left: 60%;
        bottom: 200px;
        transform: translateX(-55%) rotate(-80deg);
      }

      @keyframes open-flower-petal {
        0% {
          transform: translateX(-50%) translateY(50px) rotate(0deg);
          opacity: 0;
        }
        50% {
          opacity: 1;
        }
        100% {
          transform: translateX(-50%) translateY(0) rotate(var(--rotate-deg));
          opacity: 1;
        }
      }

      @keyframes open-flower-center {
        0% {
          transform: translateX(-50%) scale(0);
          opacity: 0;
        }
        100% {
          transform: translateX(-50%) scale(1);
          opacity: 1;
        }
      }

      .flower_light,
      .light {
        position: absolute;
        width: 10px;
        height: 10px;
        background-color: rgb(255, 255, 255);
        border-radius: 50%;
        filter: blur(2px);
        z-index: 1;
      }

      .flower_light {
        bottom: 450px;
        animation: light-ans 4s linear infinite backwards;
      }

      .light-1 {
        left: 5%;
        animation-delay: 1s;
      }
      .light-2 {
        left: 15%;
        animation-delay: 0.5s;
      }
      .light-3 {
        left: 25%;
        animation-delay: 0.3s;
      }
      .light-4 {
        left: 35%;
        animation-delay: 0.9s;
      }
      .light-5 {
        left: 45%;
        animation-delay: 1.5s;
      }
      .light-6 {
        left: 55%;
        animation-delay: 3s;
      }
      .light-7 {
        left: 65%;
        animation-delay: 2s;
      }
      .light-8 {
        left: 75%;
        animation-delay: 3.5s;
      }
      .light-9 {
        left: 85%;
        animation-delay: 2s;
      }
      .light-10 {
        left: 92%;
        animation-delay: 3.5s;
      }
      .light-11 {
        left: 95%;
        animation-delay: 3s;
      }
      .light-12 {
        left: 98%;
        animation-delay: 0.5s;
      }
      

    .flower_leaf-1 { left: 60%; bottom: 150px; transform: translateX(-45%) rotate(80deg); }
    .flower_leaf-2 { left: 60%; bottom: 200px; transform: translateX(-55%) rotate(-80deg); }

    
    /* Estrellas flotando */
    .star {
      position: absolute;
      width: 4px;
      height: 4px;
      background: #fff;
      border-radius: 50%;
      opacity: 0.8;
      animation: float-star 6s linear infinite;
      z-index: 1;
    }

    @keyframes float-star {
      0% { transform: translateY(0) scale(0.5); opacity: 0; }
      25% { opacity: 1; }
      50% { transform: translateY(-200px) scale(1); opacity: 1; }
      75% { opacity: 1; }
      100% { transform: translateY(-400px) scale(0.5); opacity: 0; }
    }

    .flower-btn {
      padding: 15px 30px;
      font-size: 18px;
      font-weight: 600;
      color: #fff;
      background: linear-gradient(45deg, #FFD700, #FFA500);
      border: none;
      border-radius: 50px;
      cursor: pointer;
      box-shadow: 0 8px 15px rgba(0, 0, 0, 0.3);
      transition: all 0.3s ease;
      position: relative;
      overflow: hidden;
      z-index: 10;
      margin: 40px 0;
    }

    .flower-btn:hover {
      transform: translateY(-3px);
      box-shadow: 0 12px 20px rgba(0, 0, 0, 0.4);
    }
  </style>
</head>
<body>
    <audio
      id="id_audio"
      src="Flor sin retoño.mp3"
    ></audio>
    <h1>“__🌻💛Yo vi esta flor y pensé en ti porque es bonita, y bueno en realidad a mi no me gusta, pero creí que te gustaría porque tú si eres bonita💛🌻"__
      De Quique:
      “🌻💛Te amo💛🌻“</h1>
  


  <div class="sunflower">
    <div class="flower_wrapper">
      <div class="flower_stem"></div>
      <div class="flower_center"></div>
      <div class="flower_petal flower_petal-1"></div>
      <div class="flower_petal flower_petal-2"></div>
      <div class="flower_petal flower_petal-3"></div>
      <div class="flower_petal flower_petal-4"></div>
      <div class="flower_petal flower_petal-5"></div>
      <div class="flower_petal flower_petal-6"></div>
      <div class="flower_petal flower_petal-7"></div>
      <div class="flower_petal flower_petal-8"></div>
      <div class="flower_petal flower_petal-9"></div>
      <div class="flower_petal flower_petal-10"></div>
      <div class="flower_petal flower_petal-11"></div>
      <div class="flower_petal flower_petal-12"></div>
      <div class="flower_leaf flower_leaf-1"></div>
      <div class="flower_leaf flower_leaf-2"></div>
    </div>
  </div>

  <!-- Estrellas -->
  <div class="star" style="left: 2%; animation-delay: 0s;"></div>
  <div class="star" style="left: 8%; animation-delay: 1s;"></div>
  <div class="star" style="left: 12%; animation-delay: 2s;"></div>
  <div class="star" style="left: 18%; animation-delay: 0.5s;"></div>
  <div class="star" style="left: 22%; animation-delay: 1.2s;"></div>
  <div class="star" style="left: 28%; animation-delay: 2.3s;"></div>
  <div class="star" style="left: 33%; animation-delay: 1.7s;"></div>
  <div class="star" style="left: 37%; animation-delay: 2.8s;"></div>
  <div class="star" style="left: 42%; animation-delay: 0.3s;"></div>
  <div class="star" style="left: 47%; animation-delay: 1.5s;"></div>
  <div class="star" style="left: 52%; animation-delay: 2.2s;"></div>
  <div class="star" style="left: 56%; animation-delay: 0.8s;"></div>
  <div class="star" style="left: 60%; animation-delay: 2.5s;"></div>
  <div class="star" style="left: 64%; animation-delay: 1.1s;"></div>
  <div class="star" style="left: 68%; animation-delay: 2.7s;"></div>
  <div class="star" style="left: 72%; animation-delay: 0.6s;"></div>
  <div class="star" style="left: 76%; animation-delay: 1.8s;"></div>
  <div class="star" style="left: 80%; animation-delay: 2.9s;"></div>
  <div class="star" style="left: 84%; animation-delay: 1.3s;"></div>
  <div class="star" style="left: 88%; animation-delay: 2.1s;"></div>
  <div class="star" style="left: 92%; animation-delay: 0.9s;"></div>
  <div class="star" style="left: 95%; animation-delay: 1.6s;"></div>
  <div class="star" style="left: 98%; animation-delay: 2.4s;"></div>
  <div class="star" style="left: 5%; animation-delay: 1.1s;"></div>
  <div class="star" style="left: 15%; animation-delay: 0.4s;"></div>
  <div class="star" style="left: 25%; animation-delay: 1.9s;"></div>
  <div class="star" style="left: 35%; animation-delay: 2.6s;"></div>
  <div class="star" style="left: 45%; animation-delay: 0.7s;"></div>
  <div class="star" style="left: 55%; animation-delay: 1.4s;"></div>

  <button class="flower-btn">CLICK AQUÍ</button>

  <script>
    const floweBtn = document.querySelector(".flower-btn");
    const audio = document.getElementById("id_audio");

    floweBtn.addEventListener("click", () => {
      audio.volume = 0.5; // establecer volumen primero
      audio.play().catch(error => {
        console.log("No se pudo reproducir el audio. Error:", error);
        alert("Haz clic para permitir reproducir el audio.");
      });
    });
  </script>
</body>
</html>