<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Matrix Effect</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background: black;
            color: red;
            font-family: monospace;
            font-size: 18px;
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            text-align: center;
        }
        canvas {
            position: absolute;
            top: 0;
            left: 0;
        }
        h1 {
            position: relative;
            color: white;
            font-size: 28px;
            font-weight: bold;
            z-index: 1;
            line-height: 1.5;
        }
    </style>
</head>
<body>
    <canvas id="matrix"></canvas>
    <h1>SI VOUS PENSEZ AVOIR LA BONNE RÉPONSE,<br>APPELEZ VOTRE GAME MASTER<br>ET DITES-LUI "BOITE DE PANDORE" ET LE CODE</h1>

    <script>
        const canvas = document.getElementById('matrix');
        const ctx = canvas.getContext('2d');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
        const fontSize = 18;
        const columns = canvas.width / fontSize;
        const drops = Array(Math.floor(columns)).fill(1);

        function drawMatrix() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            ctx.fillStyle = 'red';
            ctx.font = `${fontSize}px monospace`;

            drops.forEach((y, x) => {
                const text = letters.charAt(Math.floor(Math.random() * letters.length));
                ctx.fillText(text, x * fontSize, y * fontSize);

                if (y * fontSize > canvas.height && Math.random() > 0.975) {
                    drops[x] = 0;
                }

                drops[x]++;
            });
        }

        setInterval(drawMatrix, 50);
    </script>
</body>
</html>
