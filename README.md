<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pomodoro Custom</title>
    <style>
        body {
            /* REMPLACE l'URL ci-dessous par ton lien d'image */
            background: url('https://i.postimg.cc/NF1tmXtV/IMG_5834.jpg') no-repeat center center fixed;
            background-size: cover;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 0;
            font-family: 'Segoe UI', sans-serif;
        }

        .glass-card {
            background: rgba(0, 0, 0, 0.4); /* Fond sombre transparent */
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            padding: 30px;
            border-radius: 30px;
            text-align: center;
            color: white;
            width: 300px;
        }

        .modes {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
        }

        .mode-btn {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            color: white;
            padding: 8px 15px;
            border-radius: 10px;
            cursor: pointer;
            font-size: 14px;
        }

        .mode-btn.active {
            background: white;
            color: black;
            font-weight: bold;
        }

        #timer { 
            font-size: 70px; 
            margin: 20px 0; 
            font-weight: bold; 
            font-variant-numeric: tabular-nums;
        }

        .controls button {
            background: #fff;
            border: none;
            padding: 12px 30px;
            border-radius: 50px;
            font-weight: bold;
            font-size: 18px;
            cursor: pointer;
        }
    </style>
</head>
<body>

<div class="glass-card">
    <div class="modes">
        <button class="mode-btn active" onclick="setTimer(25, this)">Work</button>
        <button class="mode-btn" onclick="setTimer(5, this)">Break</button>
    </div>
    
    <div id="timer">25:00</div>
    
    <div class="controls">
        <button onclick="toggleTimer()" id="startBtn">START</button>
    </div>
</div>

<script>
    let timeLeft = 25 * 60;
    let timerId = null;
    let isRunning = false;

    function setTimer(minutes, btn) {
        // Arrêter le timer si en cours
        clearInterval(timerId);
        timerId = null;
        isRunning = false;
        document.getElementById('startBtn').textContent = "START";

        // Mettre à jour le temps
        timeLeft = minutes * 60;
        updateDisplay();

        // Gérer l'apparence des boutons
        document.querySelectorAll('.mode-btn').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
    }

    function updateDisplay() {
        let m = Math.floor(timeLeft / 60);
        let s = timeLeft % 60;
        document.getElementById('timer').textContent = 
            `${m.toString().padStart(2, '0')}:${s.toString().padStart(2, '0')}`;
    }

    function toggleTimer() {
        if (isRunning) {
            clearInterval(timerId);
            timerId = null;
            document.getElementById('startBtn').textContent = "RESUME";
        } else {
            document.getElementById('startBtn').textContent = "PAUSE";
            timerId = setInterval(() => {
                if (timeLeft > 0) {
                    timeLeft--;
                    updateDisplay();
                } else {
                    clearInterval(timerId);
                    alert("C'est fini !");
                }
            }, 1000);
        }
        isRunning = !isRunning;
    }
</script>

</body>
</html>
