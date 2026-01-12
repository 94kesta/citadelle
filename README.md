<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>J-EAK_CORE_ACCESS</title>
    <style>
        :root { --terminal-green: #00ff41; --glitch-red: #ff003c; }
        body, html { background: #000; margin: 0; padding: 0; width: 100%; height: 100%; overflow: hidden; font-family: 'Courier New', Courier, monospace; }

        /* EFFET CRT (Lignes de vieux moniteur) */
        body::before {
            content: " "; display: block; position: absolute; top: 0; left: 0; bottom: 0; right: 0;
            background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.25) 50%), linear-gradient(90deg, rgba(255, 0, 0, 0.06), rgba(0, 255, 0, 0.02), rgba(0, 0, 255, 0.06));
            z-index: 100; background-size: 100% 2px, 3px 100%; pointer-events: none;
        }

        #matrix-canvas { position: fixed; top: 0; left: 0; width: 100%; height: 100%; opacity: 0.5; z-index: 1; }

        .interface {
            position: relative; z-index: 10; height: 100vh; display: flex; flex-direction: column;
            justify-content: center; align-items: center; color: var(--terminal-green); text-align: center;
        }

        /* LE VISAGE J-EAK (Design Épuré & Pro) */
        #jeak-eye {
            width: 150px; height: 150px; border: 2px solid var(--terminal-green); border-radius: 50%;
            position: relative; display: none; box-shadow: 0 0 20px var(--terminal-green);
            background: radial-gradient(circle, #004411 0%, transparent 70%);
            animation: pulse 2s infinite ease-in-out; margin-bottom: 20px;
        }

        #jeak-eye::after {
            content: ""; position: absolute; top: 50%; left: 50%; width: 40px; height: 40px;
            background: var(--terminal-green); border-radius: 50%; transform: translate(-50%, -50%);
            box-shadow: 0 0 30px var(--terminal-green); animation: iris 4s infinite;
        }

        @keyframes pulse { 0% { transform: scale(1); opacity: 0.8; } 50% { transform: scale(1.1); opacity: 1; } 100% { transform: scale(1); opacity: 0.8; } }
        @keyframes iris { 0%, 100% { width: 40px; height: 40px; } 50% { width: 10px; height: 10px; } }

        .status-text { font-size: 0.9rem; letter-spacing: 2px; text-transform: uppercase; margin-top: 10px; opacity: 0.7; }

        .btn-access {
            background: transparent; color: var(--terminal-green); border: 1px solid var(--terminal-green);
            padding: 15px 30px; font-family: 'Courier New', monospace; cursor: pointer;
            transition: 0.3s; z-index: 20;
        }
        .btn-access:hover { background: var(--terminal-green); color: #000; box-shadow: 0 0 20px var(--terminal-green); }

        /* EFFET DE SHAKE AU BOOT */
        .shake { animation: shake 0.5s cubic-bezier(.36,.07,.19,.97) both; }
        @keyframes shake { 10%, 90% { transform: translate3d(-1px, 0, 0); } 20%, 80% { transform: translate3d(2px, 0, 0); } 30%, 50%, 70% { transform: translate3d(-4px, 0, 0); } 40%, 60% { transform: translate3d(4px, 0, 0); } }
    </style>
</head>
<body class="">

    <canvas id="matrix-canvas"></canvas>

    <div class="interface">
        <div id="boot-ui">
            <button class="btn-access" onclick="bootSequence()">[ INITIALISER J-EAK ]</button>
        </div>

        <div id="jeak-eye"></div>
        <div id="status" style="display:none;">
            <div class="status-text">> CONNEXION ÉTABLIE</div>
            <div class="status-text">> ACCÈS SÉQUENCE 01... OK</div>
            <div class="status-text" style="color:white; background:green; padding: 5px;">SOUVERAINETÉ ACTIVE</div>
        </div>
    </div>

<script>
    const canvas = document.getElementById('matrix-canvas');
    const ctx = canvas.getContext('2d');

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const characters = "01STAR-T-COIN-CITADELLE-J-EAK-ELIAS-SARAH-MARCUS";
    const fontSize = 14;
    const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    function drawMatrix() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "#00ff41";
        ctx.font = fontSize + "px monospace";

        for (let i = 0; i < drops.length; i++) {
            const text = characters.charAt(Math.floor(Math.random() * characters.length));
            ctx.fillText(text, i * fontSize, drops[i] * fontSize);
            if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
            drops[i]++;
        }
    }
    setInterval(drawMatrix, 35);

    function bootSequence() {
        document.body.classList.add('shake');
        document.getElementById('boot-ui').style.display = 'none';
        
        setTimeout(() => {
            document.getElementById('jeak-eye').style.display = 'block';
            document.getElementById('status').style.display = 'block';
            document.body.classList.remove('shake');
        }, 500);
    }
</script>
</body>
</html>
        }, 1000);
    }
</script>

</body>
</html>
