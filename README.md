<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mahashivratri Virtual Puja</title>
    <style>
        body {
            background-color: #1a1a1a; /* Dark meditative background */
            color: #f39c12; /* Saffron/Gold color */
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            margin: 0;
            font-family: 'Georgia', serif;
            overflow: hidden;
            position: relative;
        }
        h1 { margin-bottom: 10px; text-shadow: 0 0 10px #f39c12; }
        
        /* Shivling Container */
        .altar {
            position: relative;
            width: 300px;
            height: 400px;
            display: flex;
            justify-content: center;
            align-items: flex-end;
        }
        .shivling-img {
            width: 250px;
            z-index: 5;
        }

        /* Pouring Animations */
        .offering {
            position: absolute;
            top: 50px;
            width: 10px;
            height: 0;
            border-radius: 5px;
            z-index: 4;
            transition: height 0.5s ease-in;
        }
        .water { background: rgba(173, 216, 230, 0.7); box-shadow: 0 0 10px lightblue; }
        .milk { background: rgba(255, 255, 255, 0.9); box-shadow: 0 0 10px white; }

        /* Flower Petals */
        .petal {
            position: absolute;
            font-size: 20px;
            z-index: 6;
            animation: fall 3s linear forwards;
        }
        @keyframes fall {
            0% { transform: translateY(-50px) rotate(0deg); opacity: 1; }
            100% { transform: translateY(400px) rotate(360deg); opacity: 0; }
        }

        /* Buttons */
        .controls {
            margin-top: 30px;
            display: flex;
            gap: 15px;
            z-index: 10;
        }
        .puja-btn {
            background: #d35400;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            transition: 0.3s;
        }
        .puja-btn:hover { background: #e67e22; transform: scale(1.1); }
    </style>
</head>
<body>

    <h1>Om Namah Shivaya</h1>
    <p>Mahashivratri Virtual Puja</p>

    <div class="altar">
        <div id="liquidStream" class="offering"></div>
        <img src="shivling.png" class="shivling-img" alt="Shivling">
    </div>

    <div class="controls">
        <button class="puja-btn" onclick="pour('water')">Offer Water</button>
        <button class="puja-btn" onclick="pour('milk')">Offer Milk</button>
        <button class="puja-btn" onclick="offerFlowers()">Offer Flowers</button>
    </div>

    <script>
        function pour(type) {
            const stream = document.getElementById('liquidStream');
            stream.className = 'offering ' + type;
            stream.style.height = '250px';
            
            setTimeout(() => {
                stream.style.height = '0';
            }, 2000);
        }

        function offerFlowers() {
            for(let i=0; i<15; i++) {
                setTimeout(() => {
                    const petal = document.createElement('div');
                    petal.className = 'petal';
                    petal.innerHTML = '🌸';
                    petal.style.left = (Math.random() * 200 + 50) + 'px';
                    document.querySelector('.altar').appendChild(petal);
                    
                    setTimeout(() => petal.remove(), 3000);
                }, i * 200);
            }
        }
    </script>
</body>
</html>
