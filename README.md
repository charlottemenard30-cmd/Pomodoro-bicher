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
            background: #
