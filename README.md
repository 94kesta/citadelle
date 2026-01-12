<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>J-EAK KERNEL</title>
    <style>
        body { background: #000; color: #0f0; font-family: 'Courier New', monospace; margin: 0; overflow: hidden; }
        #canvas { position: fixed; top: 0; left: 0; z-index: -1; opacity: 0.3; }
        
        .overlay {
            position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%);
            text-align: center; width: 90%;
        }

        /* Le visage en circuit (ASCII complexe) */
        #jeak-face {
            font-size: 8px; line-height: 8px; color: #00ff41;
            white-space: pre; display: none; margin-bottom: 20px;
            text-shadow: 0 0 10px #00ff41; animation: flicker 0.1s infinite;
        }

        .btn-link {
            border: 2px solid #0f0; padding: 15px 30px; background: none;
            color: #0f0; font-family: 'Courier New', monospace; font-size: 1.2rem;
            cursor: pointer; text-transform: uppercase; letter-spacing: 2px;
        }

        @keyframes flicker {
            0% { opacity: 0.8; } 50% { opacity: 1; } 100% { opacity: 0.9; }
        }

        #status-box { margin-top: 20px; font-size: 0.8rem; display: none; }
    </style>
</head>
<body>

<canvas id="canvas"></canvas>

<div class="overlay">
    <div id="jeak-face">
     .--------.
    /  ______  \
   |  | ^  ^ |  |
   |  | >__< |  |
    \  \____/  /
     '--------'
    [CIRCUIT_LOAD]
    </div>

    <div id="ui">
        <button class="btn-link" onclick="ignite()">Initialiser J-EAK</button>
    </div>

    <div id="status-box">
        > INJECTION LIQUIDITE : OK<br>
        > PROTOCOLE 07 : ACTIF<br>
        > BIENVENUE BATISSEUR_S01
    </div>
</div>

<script>
    // EFFET MATRIX EN FOND
    const canvas = document.getElementById('canvas');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
    const alphabet = "01010101STAR_T_COIN_J_EAK_PROJET_CITADELLE";
    const fontSize = 16;
    const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    function draw() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "#0F0";
        ctx.font = fontSize + "px monospace";
        for (let i = 0; i < drops.length; i++) {
            const text = alphabet.charAt(Math.floor(Math.random() * alphabet.length));
            ctx.fillText(text, i * fontSize, drops[i] * fontSize);
            if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
            drops[i]++;
        }
    }
    setInterval(draw, 30);

    function ignite() {
        document.getElementById('ui').style.display = 'none';
        const face = document.getElementById('jeak-face');
        const status = document.getElementById('status-box');
        
        // APPARITION BRUTALE
        face.style.display = 'block';
        setTimeout(() => {
            status.style.display = 'block';
        }, 1000);
    }
</script>

</body>
</html>
