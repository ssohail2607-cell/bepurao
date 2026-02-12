<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Missing You Bapurao</title>
    <style>
        /* 1. STYLING - Pure CSS, no external links to fail */
        body {
            margin: 0;
            padding: 0;
            background: #050505;
            color: white;
            font-family: Arial, sans-serif;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        #canvas {
            position: fixed;
            top: 0;
            left: 0;
            z-index: -1;
        }

        .card {
            background: rgba(255, 255, 255, 0.07);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 40px;
            border-radius: 20px;
            text-align: center;
            width: 320px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        h1 {
            color: #00d2ff;
            margin: 0 0 10px 0;
            font-size: 28px;
        }

        p {
            color: #bbb;
            font-size: 14px;
            line-height: 1.5;
        }

        .btn {
            background: #00d2ff;
            color: black;
            border: none;
            padding: 12px 25px;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
            margin-top: 20px;
            transition: 0.3s;
        }

        .btn:hover {
            background: #ffffff;
            transform: scale(1.05);
        }

        #surprise-content {
            display: none;
        }

        .heart {
            font-size: 40px;
            color: #ff3e3e;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

    <canvas id="canvas"></canvas>

    <div class="card">
        <div id="intro-content">
            <h1>Hello, Bapurao</h1>
            <p>I built this small space to let you know that you are missed, my friend.</p>
            <button class="btn" onclick="openBox()">Click Me</button>
        </div>

        <div id="surprise-content">
            <div class="heart">❤️</div>
            <h1 style="color: #ff3e3e;">Missing You!</h1>
            <p>Bapurao Chopade, things are quiet without you. Can't wait to catch up soon.</p>
            <button class="btn" onclick="location.reload()">Back</button>
        </div>
    </div>

    <script>
        // 2. JAVASCRIPT - Strictly audited for brackets
        var canvas = document.getElementById("canvas");
        var ctx = canvas.getContext("2d");
        var particles = [];

        function resize() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }

        window.onresize = resize;
        resize();

        // Particle Logic
        for (var i = 0; i < 50; i++) {
            particles.push({
                x: Math.random() * canvas.width,
                y: Math.random() * canvas.height,
                vx: Math.random() * 2 - 1,
                vy: Math.random() * 2 - 1
            });
        }

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = "#00d2ff";

            for (var i = 0; i < particles.length; i++) {
                var p = particles[i];
                p.x += p.vx;
                p.y += p.vy;

                if (p.x < 0 || p.x > canvas.width) p.vx *= -1;
                if (p.y < 0 || p.y > canvas.height) p.vy *= -1;

                ctx.beginPath();
                ctx.arc(p.x, p.y, 2, 0, Math.PI * 2);
                ctx.fill();
            }
            requestAnimationFrame(animate);
        }

        function openBox() {
            document.getElementById("intro-content").style.display = "none";
            document.getElementById("surprise-content").style.display = "block";
        }

        // Start Animation
        animate();
    </script>
</body>
</html>
