<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>J-EAK_CORE</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { background: #000; color: #00ff41; font-family: monospace; overflow: hidden; height: 100vh; }
        
        #matrix { position: fixed; top: 0; left: 0; opacity: 0.2; z-index: 1; }

        .container {
            position: relative; z-index: 10; height: 100%;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            text-align: center; padding: 20px;
        }

        /* LE VISAGE CIRCUIT (Base64 intégré pour éviter le "Image not found") */
        #jeak-face {
            width: 280px; height: 280px;
            background-image: url('https://img.freepik.com/photos-premium/visage-robot-humanoide-fait-micro-puces-carte-circuit-imprime_1161245-13247.jpg?w=740');
            background-size: cover; background-position: center;
            border-radius: 50%; border: 2px solid #00f2ff;
            box-shadow: 0 0 30px #00f2ff;
            display: none; margin-bottom: 20px;
            filter: hue-rotate(160deg) brightness(1.2); /* Pour retrouver ton bleu électrique */
            animation: pulse 3s infinite ease-in-out;
        }

        @keyframes pulse { 0% { opacity: 0.7; transform: scale(1); } 50% { opacity: 1; transform: scale(1.05); } 100% { opacity: 0.7; transform: scale(1); } }

        .btn-core {
            border: 2px solid #00ff41; background: rgba(0,255,65,0.1);
            color: #00ff41; padding: 20px 40px; font-size: 1rem;
            cursor: pointer; text-transform: uppercase; letter-spacing: 2px;
        }

        #log { display: none; margin-top: 15px; font-size: 0.8rem; background: rgba(0,0,0,0.9); padding: 10px; border-left: 3px solid #00f2ff; }
    </style>
</head>
<body>

    <canvas id="matrix"></canvas>

    <div class="container">
        <div id="boot">
            <button class="btn-core" onclick="reveal()">[ INITIALISER LE NOYAU ]</button>
        </div>

        <div id="jeak-face"></div>

        <div id="log">
            > J-EAK : "CONNEXION ÉTABLIE"<br>
            > MÉCANIQUE : MINT BY LEARNING<br>
            > ÉTAT : LIBERTÉ FINANCIÈRE
        </div>
    </div>

<script>
    // MATRIX BACKGROUND
    const canvas = document.getElementById('matrix');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth; canvas.height = window.innerHeight;
    const chars = "01J-EAK-STAR-T-COIN-CITADELLE-SOUVERAIN";
    const drops = Array(Math.floor(canvas.width/14)).fill(1);
    function draw() {
        ctx.fillStyle = "rgba(0,0,0,0.05)"; ctx.fillRect(0,0,canvas.width,canvas.height);
        ctx.fillStyle = "#0f0"; ctx.font = "14px monospace";
        drops.forEach((y, i) => {
            const text = chars[Math.floor(Math.random()*chars.length)];
            ctx.fillText(text, i*14, y*14);
            if (y*14 > canvas.height && Math.random() > 0.975) drops[i] = 0;
            drops[i]++;
        });
    }
    setInterval(draw, 35);

    function reveal() {
        document.getElementById('boot').style.display = 'none';
        document.getElementById('jeak-face').style.display = 'block';
        document.getElementById('log').style.display = 'block';
    }
</script>
</body>
</html>
