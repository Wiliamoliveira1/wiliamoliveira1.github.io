<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Biofabricarobot</title>
    <style>
        body {
            background: linear-gradient(135deg, #ff00ff, #8a2be2, #00ffff);
            color: white;
            font-family: 'Poppins', sans-serif;
            text-align: center;
            margin: 0;
            padding: 0;
            overflow: hidden;
        }
        header {
            background: rgba(0, 0, 0, 0.8);
            padding: 20px;
            font-size: 26px;
            font-weight: bold;
            letter-spacing: 2px;
            text-transform: uppercase;
            box-shadow: 0px 4px 10px rgba(255, 255, 255, 0.2);
        }
        section {
            padding: 50px;
            animation: fadeIn 2s ease-in-out;
        }
        .btn {
            background: #ff00ff;
            color: white;
            padding: 15px 30px;
            border: none;
            cursor: pointer;
            font-size: 18px;
            border-radius: 10px;
            transition: 0.3s;
            box-shadow: 0 0 10px #ff00ff;
            animation: pulse 1.5s infinite alternate;
        }
        .btn:hover {
            background: #00ffff;
            box-shadow: 0 0 20px #00ffff;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes pulse {
            from { transform: scale(1); }
            to { transform: scale(1.1); }
        }
    </style>
</head>
<body>
    <header>
        <h1>Biofabricarobot</h1>
    </header>
    <section>
        <h2>Robô SCARA para Biofabricação</h2>
        <p>Alta precisão e modularidade para impressão 3D, eletrofiação e melt electrowriting.</p>
        <button class="btn">Saiba mais</button>
    </section>
</body>
</html>
