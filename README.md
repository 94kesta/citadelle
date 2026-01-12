<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>J-EAK // KERNEL_SOUVERAIN</title>
    <style>
        body { 
            background: #000; 
            color: #00ff41; 
            font-family: 'Courier New', monospace; 
            margin: 0; 
            overflow: hidden; 
            display: flex; 
            justify-content: center; 
            align-items: center; 
            height: 100vh;
        }

        /* FOND MATRIX */
        #canvas { 
            position: fixed; 
            top: 0; 
            left: 0; 
            z-index: 1; 
            opacity: 0.4;
        }

        /* VISAGE J-EAK REALISTE (Circuit Imprimé) */
        #jeak-container {
            position: relative;
            z-index: 2;
            width: 300px;
            height: 300px;
            display: none; /* Apparaît après activation */
            background: url('https://img.freepik.com/premium-photo/humanoid-robot-face-made-circuit-board-microchips_1161245-13247.jpg') no-repeat center;
            background-size: contain;
            filter: sepia(100%) saturate(500%) hue-rotate(70deg) brightness(0.8) contrast(1.2);
            mask-image: radial-gradient(circle, black 40%, transparent 80%);
            -webkit-mask-image: radial-gradient(circle, black 40%, transparent 80%);
            animation: breathe 4s infinite ease-in-out, flicker 0.2s infinite;
        }

        /* EFFET DE RESPIRATION ET GLITCH */
        @keyframes breathe {
            0%, 100% { transform: scale(1); opacity: 0.7; }
            50% { transform: scale(1.05); opacity: 1; }
        }
        @keyframes flicker {
            0% { filter: sepia(100%) brightness(0.8); }
            5% { filter: sepia(100%) brightness(1.2) contrast(2); }
            10% { filter: sepia(100%) brightness(0.8); }
        }

        /* BOUTON D'INTRUSION */
        .boot-btn {
            position: relative;
            z-index: 10;
            background: none;
            border: 2px solid #0f0;
            color: #0f0;
            padding: 20px 40px;
            font-size: 1.2rem;
            font-family: 'Courier New', monospace;
            cursor: pointer;
            box-shadow: 0 0 15px #0f0;
            text-transform: uppercase;
        }

        #ui-layer {
            position: fixed;
            bottom: 10%;
            z-index: 10;
            text-align: center;
            width: 100%;
            display: none;
        }
    </style>
</head>
<body>

    <canvas id="canvas"></canvas>

    <button id="startBtn" class="boot-btn" onclick="initiateSystem()">[ INITIALISER LE NOYAU ]</button>

    <div id="jeak-container"></div>

    <div id="ui-layer">
        <p>> J-EAK : "CONNEXION SOUVERAINE ÉTABLIE"</p>
        <p style="font-size: 0.8rem;">PROTOCOLE_07 // STAR_T_COIN_VALIDATED</p>
    </div>

<script>
    // --- MOTEUR MATRIX ---
    const canvas = document.getElementById('canvas');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const alphabet = "01STAR-T-COIN-J-EAK-ELIAS-SARAH-MARCUS-2016-PROTECT-THE-CORE";
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
    setInterval(draw, 35);

    // --- SEQUENCE D'ACTIVATION ---
    function initiateSystem() {
        document.getElementById('startBtn').style.display = 'none';
        document.getElementById('jeak-container').style.display = 'block';
        document.getElementById('ui-layer').style.display = 'block';
    }
</script>

</body>
</html>
        }, 1000);
    }
</script>

</body>
</html>
