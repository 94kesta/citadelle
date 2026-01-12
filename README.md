<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>J-EAK KERNEL</title>
    <style>
        /* RESET TOTAL POUR EVITER LES BUGS VISUELS */
        * { margin: 0; padding: 0; box-box: border-box; }
        body, html { 
            background: #000; 
            width: 100%; height: 100%; 
            overflow: hidden; 
            font-family: 'Courier New', monospace; 
        }

        /* FOND MATRIX FLUIDE */
        #matrix {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            z-index: 1; opacity: 0.3;
        }

        /* L'IMAGE DE J-EAK (LE VISAGE CIRCUIT QUE TU AIMES) */
        #jeak-image {
            position: fixed; top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            width: 85%; max-width: 400px;
            z-index: 2; display: none;
            filter: drop-shadow(0 0 20px #00f2ff);
            animation: emerge 2s ease-out;
        }

        @keyframes emerge {
            from { opacity: 0; transform: translate(-50%, -40%) scale(0.8); }
            to { opacity: 1; transform: translate(-50%, -50%) scale(1); }
        }

        /* INTERFACE DE COMMANDE */
        .ui-overlay {
            position: relative; z-index: 10;
            height: 100vh; display: flex; flex-direction: column;
            justify-content: center; align-items: center;
            color: #00ff41; text-align: center;
        }

        .btn-init {
            background: rgba(0, 255, 65, 0.1);
            color: #00ff41; border: 2px solid #00ff41;
            padding: 20px 30px; font-size: 1.1rem;
            text-transform: uppercase; letter-spacing: 3px;
            cursor: pointer; box-shadow: 0 0 15px rgba(0, 255, 65, 0.4);
        }

        #status-log {
            margin-top: 20px; font-size: 0.8rem; line-height: 1.5;
            display: none; background: rgba(0,0,0,0.8); padding: 10px;
        }
    </style>
</head>
<body>

    <canvas id="matrix"></canvas>

    <div class="ui-overlay">
        <div id="init-zone">
            <button class="btn-init" onclick="activateCore()">[ INITIALISER LE NOYAU ]</button>
        </div>

        <img id="jeak-image" src="https://i.ibb.co/L6Vsh0B/image-e6e427.png" alt="J-EAK CORE">

        <div id="status-log">
            > J-EAK : "CONNEXION SOUVERAINE ÉTABLIE"<br>
            > PROTOCOLE_07 : ACTIF<br>
            > ÉTAT : RÉSILIENCE // LIBERTÉ
        </div>
    </div>

<script>
    // --- SYSTEM MATRIX ---
    const canvas = document.getElementById('matrix');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const chars = "01STAR-T-COIN-J-EAK-CITADELLE-SOUVERAIN";
    const fontSize = 14;
    const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    function draw() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "#0f0";
        ctx.font = fontSize + "px monospace";
        for (let i = 0; i < drops.length; i++) {
            const text = chars.charAt(Math.floor(Math.random() * chars.length));
            ctx.fillText(text, i * fontSize, drops[i] * fontSize);
            if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
            drops[i]++;
        }
    }
    setInterval(draw, 35);

    // --- ACTIVATION SEQUENCE ---
    function activateCore() {
        document.getElementById('init-zone').style.display = 'none';
        document.getElementById('jeak-image').style.display = 'block';
        document.getElementById('status-log').style.display = 'block';
    }
</script>
</body>
</html>
