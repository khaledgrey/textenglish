<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Ejercicio Phrasal Verbs</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f1f5f9;
      margin: 0;
      padding: 40px 20px;
    }

    h1 {
      text-align: center;
      color: #2563eb;
      margin-bottom: 30px;
    }

    .quiz-container {
      max-width: 900px;
      margin: 0 auto;
      background: #ffffff;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
    }

    .question {
      margin-bottom: 20px;
    }

    .question label {
      font-weight: 500;
      display: block;
      margin-bottom: 10px;
    }

    select {
      width: 100%;
      padding: 10px;
      font-size: 16px;
      border-radius: 8px;
      border: 1px solid #ccc;
    }

    button {
      width: 100%;
      padding: 15px;
      font-size: 18px;
      background-color: #2563eb;
      color: white;
      border: none;
      border-radius: 10px;
      margin-top: 30px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    button:hover {
      background-color: #1d4ed8;
    }

    .alert {
      background-color: #e0f2fe;
      border: 2px solid #2563eb;
      padding: 20px;
      margin-top: 30px;
      text-align: center;
      font-size: 20px;
      color: #1e3a8a;
      border-radius: 10px;
      animation: pop 0.5s ease;
    }

    @keyframes pop {
      from { transform: scale(0.8); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }
  </style>
</head>
<body>
  <h1>Completa con el Phrasal Verb correcto</h1>

  <div class="quiz-container" id="quiz"></div>

  <button onclick="revisar()">Ver Resultados</button>

  <div id="resultado" class="alert" style="display: none;"></div>

  <script>
    const preguntas = [
      {
        oracion: "Yesterday, I ___ the project after a long break (retomar).",
        respuesta: "went about",
        opciones: ["went about", "picked on", "hung up"]
      },
      {
        oracion: "She has ___ her apartment completely (renovar).",
        respuesta: "done up",
        opciones: ["done up", "blown away", "let down"]
      },
      {
        oracion: "We are ___ at John's place this evening (pasar el rato).",
        respuesta: "hanging out",
        opciones: ["hanging out", "stood up", "took care"]
      },
      {
        oracion: "The frog ___ a prince in the fairy tale (convertirse).",
        respuesta: "turned into",
        opciones: ["turned into", "took off", "watched up"]
      },
      {
        oracion: "Have you ___ the application form yet? (rellenar).",
        respuesta: "filled out",
        opciones: ["filled out", "called on", "undid"]
      },
      {
        oracion: "I ___ all my old clothes yesterday (botar).",
        respuesta: "threw away",
        opciones: ["threw away", "brushed up", "took off"]
      },
      {
        oracion: "He ___ after arguing with his mom (colgar).",
        respuesta: "hung up",
        opciones: ["hung up", "picked up", "stood up"]
      },
      {
        oracion: "She ___ the phone before it rang again (descolgar).",
        respuesta: "unhung",
        opciones: ["unhung", "read out", "got rid of"]
      },
      {
        oracion: "Can you ___ the kids from school later? (recoger).",
        respuesta: "pick up",
        opciones: ["pick up", "let down", "sit back"]
      },
      {
        oracion: "He ___ the article in a clear voice (leer en voz alta).",
        respuesta: "read out",
        opciones: ["read out", "dressed up", "hung up"]
      },
      {
        oracion: "I often ___ my future plans (pensar en).",
        respuesta: "think about",
        opciones: ["think about", "brush up", "stand up"]
      },
      {
        oracion: "She ___ her grandmother after school (cuidar).",
        respuesta: "takes care of",
        opciones: ["takes care of", "goes about", "picks on"]
      },
      {
        oracion: "The teacher ___ him for being noisy (regañar).",
        respuesta: "took off",
        opciones: ["took off", "put away", "went about"]
      },
      {
        oracion: "Everyone ___ when the judge entered (levantarse).",
        respuesta: "stood up",
        opciones: ["stood up", "filled out", "let down"]
      },
      {
        oracion: "They ___ for the Halloween party (vestirse elegante).",
        respuesta: "dressed up",
        opciones: ["dressed up", "watched up", "took off"]
      },
      {
        oracion: "He quickly ___ his shoes before running (desamarrar).",
        respuesta: "undid",
        opciones: ["undid", "read out", "took care"]
      },
      {
        oracion: "Please don’t ___! We’re having a private conversation (entrometerse).",
        respuesta: "butt in",
        opciones: ["butt in", "go about", "blow away"]
      },
      {
        oracion: "I had to ___ last night to finish my work (trasnocharse).",
        respuesta: "stay up",
        opciones: ["stay up", "pick on", "dress up"]
      },
      {
        oracion: "He ___ the interview by arriving late (arruinar).",
        respuesta: "screwed up",
        opciones: ["screwed up", "stood up", "read out"]
      },
      {
        oracion: "I won’t ___ you again, I promise (decepcionar).",
        respuesta: "let down",
        opciones: ["let down", "call on", "watch up"]
      }
    ];

    const quizContainer = document.getElementById("quiz");

    preguntas.forEach((p, index) => {
      const div = document.createElement("div");
      div.className = "question";

      let optionsHTML = `<select id="q${index}"><option value="">-- Selecciona --</option>`;
      p.opciones.forEach(op => {
        optionsHTML += `<option value="${op}">${op}</option>`;
      });
      optionsHTML += `</select>`;

      div.innerHTML = `<label>${index + 1}. ${p.oracion.replace("___", optionsHTML)}</label>`;
      quizContainer.appendChild(div);
    });

    function revisar() {
      let buenas = 0;
      let malas = 0;

      preguntas.forEach((p, i) => {
        const seleccion = document.getElementById(`q${i}`).value.trim().toLowerCase();
        if (seleccion === p.respuesta.toLowerCase()) {
          buenas++;
        } else {
          malas++;
        }
      });

      const resultado = document.getElementById("resultado");
      resultado.innerHTML = `✅ Respuestas correctas: <strong>${buenas}</strong><br>❌ Respuestas incorrectas: <strong>${malas}</strong>`;
      resultado.style.display = "block";
    }
  </script>
</body>
</html>

