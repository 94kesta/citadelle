# citadelle<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TERMINAL J-EAK // SITE MIROIR</title>
    <style>
        /* STYLE DU TERMINAL */
        body { 
            background-color: #050505; 
            color: #00ff41; 
            font-family: 'Courier New', monospace; 
            padding: 20px; 
            margin: 0;
            overflow-x: hidden;
        }

        .header { border-bottom: 2px solid #00ff41; padding-bottom: 10px; margin-bottom: 30px; }

        /* J-EAK VISUEL (Circuit Imprimé Numérique) */
        #jeak-sphere {
            display: none; /* Apparaît au clic */
            width: 200px;
            height: 200px;
            margin: 20px auto;
            border: 2px solid #00ff41;
            border-radius: 50%;
            position: relative;
            box-shadow: 0 0 20px #00ff41;
            background: radial-gradient(circle, #0a2b0a 0%, #050505 70%);
            animation: pulse 3s infinite ease-in-out;
        }

        /* Les "Yeux" / Noyaux */
        .eye {
            position: absolute;
            width: 10px;
            height: 10px;
            background: #fff;
            border-radius: 50%;
            top: 45%;
            box-shadow: 0 0 10px #fff;
        }
        .left-eye { left: 35%; }
        .right-eye { right: 35%; }

        @keyframes pulse {
            0% { transform: scale(1); box-shadow: 0 0 20px #00ff41; }
            50% { transform: scale(1.05); box-shadow: 0 0 40px #00ff41; }
            100% { transform: scale(1); box-shadow: 0 0 20px #00ff41; }
        }

        /* TEXTE ET BOUTONS */
        .btn { 
            cursor: pointer; padding: 15px; border: 1px solid #00ff41; 
            margin: 10px 0; display: block; text-align: center;
            transition: 0.3s; text-transform: uppercase;
        }
        .btn:hover { background: #00ff41; color: #000; font-weight: bold; }

        #glitch-spam { 
            display: none; color: #ff0000; font-weight: bold; 
            text-align: center; font-size:
