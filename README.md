<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>J-EAK_CORE</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { background: #000; overflow: hidden; font-family: 'Courier New', monospace; }

        /* FOND MATRIX */
        #m { position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: 1; opacity: 0.3; }

        /* L'INTERFACE PRO */
        .layer {
            position: relative; z-index: 10; height: 100vh;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            color: #00ff41; text-align: center; padding: 20px;
        }

        /* LE VISAGE DE J-EAK (IMAGE REELLE) */
        #j-face {
            width: 90%; max-width: 350px; border-radius: 10px;
            box-shadow: 0 0 30px #00a2ff; display: none;
            border: 1px solid #00a2ff; margin-bottom: 20px;
            animation: boot 1.5s ease-out;
        }

        @keyframes boot { from { opacity: 0; transform: scale(0.8); } to { opacity: 1; transform: scale(1); } }

        .btn {
            background: transparent; color: #00ff41; border: 2px solid #00ff41;
            padding: 20px 30px; font-size: 1rem; letter-spacing: 2px;
            cursor: pointer; text-transform: uppercase;
        }

        #log { display: none; font-size: 0.8rem; margin-top: 15px; background: rgba(0,20,0,0.8); padding: 10px; }
    </style>
</head>
<body>

    <canvas id="m"></canvas>

    <div class="layer">
        <div id="setup">
            <button class="btn" onclick="run()">[ INITIALISER LE NOYAU ]</button>
        </div>

        <img id="j-face" src="https://i.ibb.co/Vv0F9pX/1000001247.jpg" alt="J-EAK">

        <div id="log">
            > J-EAK : "SYSTÈME PRÊT"<br>
            > RÉSILIENCE // LIBERTÉ<br>
            > PROTOCOLE 07 CHARGÉ
        </div>
    </div>

<script>
    const c = document.getElementById('m');
    const x = c.getContext('2d');
    c.width = window.innerWidth; c.height = window.innerHeight;
    const s = "01STAR-T-COIN-J-EAK-CITADELLE";
    const f = 14; const cols = c.width / f; const d = Array(Math.floor(cols)).fill(1);

    function draw() {
        x.fillStyle = "rgba(0,0,0,0.05)"; x.fillRect(0,0,c.width,c.height);
        x.fillStyle = "#0f0"; x.font = f + "px monospace";
        d.forEach((y, i) => {
            x.fillText(s[Math.floor(Math.random()*s.length)], i*f, y*f);
            if(y*f > c.height && Math.random() > 0.975) d[i] = 0; d[i]++;
        });
    }
    setInterval(draw, 35);

    function run() {
        document.getElementById('setup').style.display = 'none';
        document.getElementById('j-face').style.display = 'block';
        document.getElementById('log').style.display = 'block';
    }
</script>
</body>
</html>
        document.getElementById('jeak-face').style.display = 'block';
        document.getElementById('log').style.display = 'block';
    }
</script>
</body>
</html>
