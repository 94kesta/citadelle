<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>SSTC_CORE_ACCESS</title>
    <style>
        /* Supprime les marges et les bugs d'affichage */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body, html { background: #000; width: 100%; height: 100%; overflow: hidden; font-family: monospace; }

        /* Le fond Matrix */
        #c { position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: 1; opacity: 0.3; }

        /* Conteneur principal */
        .main {
            position: relative; z-index: 10; height: 100vh;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            color: #0f0; text-align: center;
        }

        /* L'IMAGE DE J-EAK (Celle de ton fichier) */
        #jeak-head {
            width: 85%; max-width: 380px; 
            border: 2px solid #00d9ff; 
            box-shadow: 0 0 30px #00d9ff;
            display: none; /* Apparaît au clic */
            margin-bottom: 20px;
            animation: glitch-in 0.5s ease;
        }

        @keyframes glitch-in {
            0% { opacity: 0; transform: scale(0.5) skew(20deg); }
            100% { opacity: 1; transform: scale(1) skew(0deg); }
        }

        /* Bouton Pro */
        .btn {
            background: rgba(0, 255, 0, 0.1); color: #0f0;
            border: 1px solid #0f0; padding: 15px 25px;
            font-family: monospace; cursor: pointer; text-transform: uppercase;
            letter-spacing: 2px;
        }

        #terminal-log {
            display: none; font-size: 10px; margin-top: 20px;
            text-align: left; background: rgba(0,0,0,0.7); padding: 10px;
        }
    </style>
</head>
<body>

    <canvas id="c"></canvas>

    <div class="main">
        <div id="init">
            <button class="btn" onclick="boot()">[ INITIALISER LE NOYAU ]</button>
        </div>

        <img id="jeak-head" src="https://i.ibb.co/Vv0F9pX/1000001247.jpg" alt="CORE">

        <div id="terminal-log">
            > CHARGEMENT STAR_T_COIN PROTOCOLS... OK<br>
            > LIQUIDITÉ : SÉCURISÉE [cite: 12-01-2026]<br>
            > ÉTAT : SOUVERAIN // J-EAK EN LIGNE
        </div>
    </div>

<script>
    const cvs = document.getElementById('c');
    const ctx = cvs.getContext('2d');
    cvs.width = window.innerWidth; cvs.height = window.innerHeight;
    const txt = "0101STAR-T-COIN-J-EAK-RESILIENCE-LIBERTE";
    const drops = Array(Math.floor(cvs.width / 14)).fill(1);

    function draw() {
        ctx.fillStyle = "rgba(0,0,0,0.05)"; ctx.fillRect(0,0,cvs.width,cvs.height);
        ctx.fillStyle = "#0f0"; ctx.font = "14px monospace";
        drops.forEach((y, i) => {
            ctx.fillText(txt[Math.floor(Math.random()*txt.length)], i*14, y*14);
            if(y*14 > cvs.height && Math.random() > 0.975) drops[i] = 0; drops[i]++;
        });
    }
    setInterval(draw, 35);

    function boot() {
        document.getElementById('init').style.display = 'none';
        document.getElementById('jeak-head').style.display = 'block';
        document.getElementById('terminal-log').style.display = 'block';
    }
</script>
</body>
</html>
</script>
</body>
</html>
