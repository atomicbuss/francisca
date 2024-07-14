<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¿Me perdonas?</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
            margin: 0;
            font-family: Arial, sans-serif;
            position: relative;
            overflow: hidden;
        }

        .container {
            text-align: center;
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            z-index: 2;
        }

        h1 {
            margin-bottom: 20px;
        }

        .cat-image {
            max-width: 100%;
            height: auto;
            border-radius: 10px;
        }

        .buttons {
            margin-top: 20px;
        }

        button {
            padding: 10px 20px;
            margin: 5px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            transition: transform 0.3s;
        }

        #no-button {
            background-color: #ff4d4d;
            color: white;
        }

        #yes-button {
            background-color: #4caf50;
            color: white;
        }

        .message {
            margin-top: 20px;
            background-color: #ffc;
            border: 1px solid #ffa;
            padding: 5px 10px;
            border-radius: 5px;
            margin: 5px;
            display: none;
        }

        .heart {
            width: 20px;
            height: 20px;
            background-color: red;
            position: absolute;
            transform: rotate(-45deg);
            animation: fall 5s linear infinite;
            z-index: 1;
        }

        .heart::before,
        .heart::after {
            content: '';
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: red;
            border-radius: 50%;
        }

        .heart::before {
            top: -10px;
            left: 0;
        }

        .heart::after {
            top: 0;
            left: 10px;
        }

        @keyframes fall {
            0% {
                top: -10%;
                opacity: 1;
            }
            100% {
                top: 110%;
                opacity: 0;
            }
        }

        #thank-you-message {
            display: none;
            margin-top: 20px;
            font-size: 18px;
            color: #4caf50;
        }

        .hidden-image {
            display: none;
            margin-top: 20px;
            max-width: 100%;
            height: auto;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>¿Me perdonas?</h1>
        <img src="img/cat1.jpg" alt="Gatito" id="cat-image" class="cat-image">
        <div class="buttons">
            <button id="no-button">No</button>
            <button id="yes-button">Sí</button>
        </div>
        <div id="thank-you-message">¡Gracias amor, te amo!</div>
        <img src="img/happycat.gif" alt="Gatito Feliz" id="happycat-image" class="hidden-image">
        <div class="message" id="message">Perdóname</div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            const yesButton = document.getElementById('yes-button');
            const noButton = document.getElementById('no-button');
            const thankYouMessage = document.getElementById('thank-you-message');
            const messageElement = document.getElementById('message');
            const catImage = document.getElementById('cat-image');
            const happyCatImage = document.getElementById('happycat-image');
            let clickCount = 0;

            const messages = [
                "Perdóname",
                "Lo siento mucho",
                "No fue mi intención",
                "Perdóname, amor",
                "Te quiero",
                "No lo haré de nuevo",
                "Lo siento de verdad",
                "Eres lo más importante",
                "Por favor, perdóname",
                "Eres todo para mí",
                "No puedo perderte",
                "Te necesito",
                "Perdóname, mi amor",
                "¡Déjame compensártelo!",
                "Te extraño"
            ];

            noButton.addEventListener('click', function () {
                clickCount++;
                yesButton.style.transform = `scale(${1 + clickCount * 0.1})`;
                const randomImageIndex = Math.floor(Math.random() * 3) + 1;
                catImage.src = `img/cat${randomImageIndex}.jpg`;
                const randomMessageIndex = Math.floor(Math.random() * messages.length);
                messageElement.textContent = messages[randomMessageIndex];
                messageElement.style.display = 'block';
            });

            yesButton.addEventListener('click', function () {
                thankYouMessage.style.display = 'block';
                happyCatImage.style.display = 'block';
                createHearts();
            });

            function createHearts() {
                for (let i = 0; i < 100; i++) {
                    const heart = document.createElement('div');
                    heart.classList.add('heart');
                    heart.style.left = Math.random() * 100 + 'vw';
                    heart.style.animationDuration = Math.random() * 2 + 3 + 's';
                    document.body.appendChild(heart);
                    setTimeout(() => {
                        heart.remove();
                    }, 5000);
                }
            }
        });
    </script>
</body>
</html>
