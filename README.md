# Mejor-amigo-Carlos
Trabajo Alura
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Encuentra a tu mejor amigo</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            padding: 20px;
        }
        .container {
            max-width: 400px;
            margin: auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px gray;
        }
        input, button {
            margin-top: 10px;
            padding: 10px;
            font-size: 16px;
        }
        button {
            background-color: #28a745;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 5px;
        }
        button:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>

    <div class="container" id="juego">
        <h1>¿Quién es tu mejor amigo?</h1>
        <p>Un nombre ha sido elegido al azar. ¡Adivina cuál es!</p>
        <p>Tienes <span id="intentos">3</span> intentos.</p>
        
        <input type="text" id="nombreInput" placeholder="Escribe un nombre aquí">
        <button onclick="verificarNombre()">Intentar</button>
        
        <p id="mensaje"></p>
    </div>

    <script>
        let nombresValidos = ["Miguel", "Carlos", "Flora", "Claudia", "Raúl", "José", "Sofía", "Juan", "Juana", "Eduardo"];
        let nombreCorrecto = nombresValidos[Math.floor(Math.random() * nombresValidos.length)];
        let intentosRestantes = 3;

        function verificarNombre() {
            let inputNombre = document.getElementById("nombreInput").value.trim();
            let mensaje = document.getElementById("mensaje");
            let intentos = document.getElementById("intentos");

            if (inputNombre === nombreCorrecto) {
                mensaje.innerHTML = "🎉 ¡Correcto! " + inputNombre + " es tu mejor amigo.";
                mensaje.style.color = "green";
                document.getElementById("nombreInput").disabled = true;
            } else {
                intentosRestantes--;
                intentos.innerHTML = intentosRestantes;

                if (intentosRestantes > 0) {
                    mensaje.innerHTML = "❌ Incorrecto. Intenta de nuevo.";
                    mensaje.style.color = "red";
                } else {
                    mensaje.innerHTML = "😢 Se acabaron los intentos. El nombre correcto era <b>" + nombreCorrecto + "</b>.";
                    mensaje.style.color = "red";
                    document.getElementById("nombreInput").disabled = true;
                }
            }
        }
    </script>

</body>
</html>