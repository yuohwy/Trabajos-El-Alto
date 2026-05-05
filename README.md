<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Postulación Oficial | HOLA SOY TONY - Reclutamiento</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Inter:wght@300;400;600;800;900&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --bg-dark: #0f020c; 
            --text-main: #ffffff; 
            --text-muted: #e0b0d5; 
            --color-blue: #bc13fe;    
            --color-light-blue: #ff9ad0;
            --color-red: #ff007f;     
            --color-orange: #ffd700;  
            --color-green: #39ff14;   
            --card-bg: rgba(30, 5, 25, 0.65);
            --card-border: rgba(255, 255, 255, 0.08);
        }

        * { box-sizing: border-box; }

        body {
            margin: 0; padding: 0;
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-main);
            overflow-x: hidden;
            display: flex; justify-content: center; align-items: flex-start;
            min-height: 100vh; 
            padding: 20px 15px 40px 15px;
            touch-action: manipulation;
        }

        .fondo-general {
            position: fixed; inset: 0; z-index: -2;
            background: radial-gradient(circle at 50% 30%, #2a0520, #0f020c 70%);
        }

        /* --- CORAZONES AL TOCAR --- */
        .heart-layer { position: fixed; inset: 0; pointer-events: none; z-index: 9999; }
        .heart {
            position: absolute; width: 30px; height: 30px; transform-origin: center;
            will-change: transform, opacity; pointer-events: none;
            animation: rise 1000ms ease-out forwards;
        }
        .heart svg { width: 100%; height: 100%; display: block; }
        @keyframes rise {
            0% { transform: translateY(0) scale(0.8); opacity: 1; }
            100% { transform: translateY(-120px) scale(1.2); opacity: 0; }
        }

        /* --- CONTENEDOR PRINCIPAL --- */
        .container {
            width: 100%; max-width: 440px;
            display: flex; flex-direction: column; 
            gap: 20px;
            position: relative; z-index: 10;
        }

        /* --- TARJETAS CORPORATIVAS (PANELES) --- */
        .corporate-card {
            background: var(--card-bg);
            backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
            border: 1px solid var(--card-border);
            border-radius: 28px;
            padding: 30px 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4), inset 0 1px 0 rgba(255,255,255,0.1);
            text-align: center; position: relative; overflow: hidden;
            transition: transform 0.3s ease;
        }

        /* --- ESTILO DE PORTADA --- */
        .cover-card {
            padding: 0; 
            height: 380px;
            cursor: pointer;
            border-radius: 32px;
            display: flex; flex-direction: column; justify-content: flex-end;
        }

        .cover-img-container {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 1;
        }

        .cover-img-container img {
            width: 100%; height: 100%;
            object-fit: cover;
            object-position: center 15%;
        }

        .cover-fade {
            position: absolute; bottom: 0; left: 0; width: 100%; height: 75%;
            background: linear-gradient(to bottom, rgba(15,2,12,0) 0%, rgba(15,2,12,0.8) 50%, rgba(15,2,12,1) 100%);
            z-index: 2;
        }

        .cover-text {
            position: relative; z-index: 3;
            text-align: left; padding: 30px 25px;
            width: 100%;
        }

        /* --- NUEVO: CONTENEDOR DE TITULO Y LOGO --- */
        .title-wrapper {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 12px;
        }

        .company-logo {
            width: 58px;
            height: 58px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid var(--color-light-blue);
            box-shadow: 0 4px 15px rgba(188, 19, 254, 0.5);
            flex-shrink: 0;
            /* Animación de salto ligero y suave */
            animation: smoothBounce 3s ease-in-out infinite;
        }

        @keyframes smoothBounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-8px); }
        }

        .text-group {
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .cover-text h1 {
            font-family: 'Orbitron', sans-serif; font-size: 28px; 
            margin: 0; font-weight: 900; line-height: 1.1;
            background: linear-gradient(90deg, var(--color-blue), var(--color-red), var(--color-orange));
            background-size: 200% auto; -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            animation: gradientMove 5s linear infinite;
        }

        .assistant-text {
            font-family: 'Inter', sans-serif;
            font-size: 15px;
            color: var(--text-muted);
            font-weight: 600;
            margin-top: 4px;
        }

        .role-badge {
            display: inline-block;
            background: rgba(255, 215, 0, 0.15);
            border: 1px solid rgba(255, 215, 0, 0.3);
            backdrop-filter: blur(10px);
            padding: 8px 16px; border-radius: 20px;
        }

        .role-title {
            color: var(--color-orange); font-family: 'Orbitron', sans-serif;
            font-weight: 900; font-size: 14px; 
            text-transform: uppercase; letter-spacing: 1.5px; margin: 0;
        }

        @keyframes shake-img {
            0%, 100% { transform: translateX(0) rotate(0deg); }
            25% { transform: translateX(-4px) rotate(-1deg); }
            75% { transform: translateX(4px) rotate(1deg); }
        }
        .shake-active { animation: shake-img 0.4s ease-in-out !important; }

        /* --- SECCIÓN OFERTA Y TEMPORIZADOR --- */
        .offer-section { border-top: 4px solid var(--color-red); }
        
        .urgency-title {
            font-family: 'Orbitron', sans-serif;
            color: var(--color-red); font-size: 16px; font-weight: 900;
            text-transform: uppercase; margin-bottom: 20px; letter-spacing: 1px;
            animation: pulseText 2s infinite;
        }
        @keyframes pulseText { 0%, 100% { opacity: 1; } 50% { opacity: 0.7; } }

        .countdown { 
            display: flex; justify-content: space-between; gap: 8px; margin-bottom: 25px; 
        }
        .time-box {
            background: rgba(0, 0, 0, 0.5); border-radius: 16px; padding: 12px 5px;
            flex: 1; border: 1px solid rgba(255, 255, 255, 0.08);
            position: relative; overflow: hidden;
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
        }
        .time-box::before {
            content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 3px;
            background: linear-gradient(90deg, var(--color-blue), var(--color-orange));
        }
        .time-box span { font-family: 'Orbitron', sans-serif; display: block; font-size: 28px; font-weight: 900; color: #fff; line-height: 1.1; }
        .time-box small { font-size: 12px; color: var(--text-muted); text-transform: uppercase; font-weight: 700; letter-spacing: 0.5px; }

        .progress-container {
            width: 100%; height: 24px; background: rgba(0, 0, 0, 0.6);
            border-radius: 12px; margin-bottom: 12px; overflow: hidden; position: relative;
            border: 1px solid rgba(255,255,255,0.05);
        }
        .progress-bar {
            height: 100%; width: 0%; 
            background: linear-gradient(90deg, var(--color-blue), var(--color-red), var(--color-orange));
            background-size: 200% 100%; border-radius: 12px; 
            transition: width 2s cubic-bezier(0.25, 1, 0.5, 1); 
            animation: gradientMove 4s ease infinite;
            position: relative;
        }
        .progress-bar::after {
            content: ""; position: absolute; top: 0; left: 0; bottom: 0; right: 0;
            background: linear-gradient( -45deg, rgba(255,255,255,0.2) 25%, transparent 25%, transparent 50%, rgba(255,255,255,0.2) 50%, rgba(255,255,255,0.2) 75%, transparent 75%, transparent );
            background-size: 30px 30px; border-radius: 12px;
            animation: moveStripes 1.5s linear infinite;
        }
        
        @keyframes moveStripes { 0% { background-position: 0 0; } 100% { background-position: 30px 30px; } }
        @keyframes gradientMove { 0% { background-position: 0% 50%; } 50% { background-position: 100% 50%; } 100% { background-position: 0% 50%; } }

        .progress-text { font-size: 14px; color: var(--text-muted); font-weight: 600; margin-bottom: 25px; display: block; }

        /* --- CAJA DE SALARIO --- */
        .salary-box {
            background: rgba(0, 0, 0, 0.4); border-radius: 20px; padding: 20px 15px;
            border: 1px solid rgba(255, 215, 0, 0.2);
        }
        .dark-humor {
            font-size: 14px; color: #fff; margin-bottom: 20px; font-weight: 600;
            background: rgba(0, 0, 0, 0.5); padding: 12px 15px; border-radius: 12px;
            border-left: 4px solid var(--color-orange); text-align: left; line-height: 1.4;
        }
        .salary-row { 
            display: flex; justify-content: space-between; align-items: center; 
            margin-bottom: 12px; padding-bottom: 12px; border-bottom: 1px solid rgba(255,255,255,0.05);
        }
        .salary-row:last-child { margin-bottom: 0; padding-bottom: 0; border-bottom: none; }
        
        .salary-label { font-size: 16px; font-weight: 700; color: var(--text-muted); }
        .salary-label.highlight { color: #fff; font-size: 18px; }
        
        .price-tag {
            font-family: 'Orbitron', sans-serif; color: var(--color-red); font-weight: 900; font-size: 20px;
            background: rgba(255, 0, 127, 0.1); padding: 6px 14px; border-radius: 10px; border: 1px solid rgba(255,0,127,0.3);
        }
        .price-tag.mensual {
            font-size: 26px; color: #ffffff; background: linear-gradient(45deg, var(--color-blue), var(--color-red));
            border: none; box-shadow: 0 4px 15px rgba(255,0,127,0.3);
        }

        /* --- LISTAS Y CONTACTO --- */
        h2 { font-family: 'Orbitron', sans-serif; font-size: 22px; font-weight: 900; margin-bottom: 20px; text-transform: uppercase; letter-spacing: 1px;}
        
        .req-badge {
            background: rgba(255, 215, 0, 0.1); color: var(--color-orange); 
            padding: 8px 20px; border-radius: 20px; font-weight: 800; font-size: 15px; 
            margin-bottom: 25px; display: inline-block; border: 1px solid rgba(255,215,0,0.3);
        }

        ul.job-list { list-style: none; padding: 0; margin: 0 0 25px 0; text-align: left; }
        ul.job-list li {
            background: rgba(0, 0, 0, 0.4); margin-bottom: 12px; padding: 16px 20px; border-radius: 16px;
            font-size: 16px; font-weight: 600; display: flex; align-items: center;
            border-left: 5px solid var(--color-blue); color: #fff; line-height: 1.4;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        }

        .supervisor-contact {
            font-size: 16px; font-weight: 700; color: var(--text-muted); margin-bottom: 25px;
            background: rgba(0, 0, 0, 0.4); padding: 20px; border-radius: 20px;
            border: 1px dashed rgba(255,215,0,0.4);
        }
        .supervisor-contact .num {
            color: var(--color-red); font-family: 'Orbitron', sans-serif; font-size: 28px; 
            display: block; margin-top: 8px; letter-spacing: 2px; font-weight: 900;
            text-shadow: 0 0 10px rgba(255,0,127,0.4);
        }

        /* --- BOTONES --- */
        .btn-action {
            display: block; width: 100%; font-family: 'Orbitron', sans-serif;
            color: white; font-size: 18px; font-weight: 900; padding: 22px 15px;
            border-radius: 20px; text-transform: uppercase; letter-spacing: 1px;
            border: none; cursor: pointer; position: relative; z-index: 1;
            background: linear-gradient(90deg, var(--color-blue), var(--color-red));
            box-shadow: 0 8px 25px rgba(255, 0, 127, 0.4);
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }
        .btn-action:active { transform: translateY(2px); box-shadow: 0 4px 15px rgba(255, 0, 127, 0.4); }

        /* --- MAPA --- */
        .map-section { padding: 30px 20px; }
        .map-wrapper {
            display: block; border-radius: 20px; overflow: hidden; position: relative; padding: 3px;
            background: linear-gradient(45deg, var(--color-blue), var(--color-red));
            box-shadow: 0 10px 25px rgba(0,0,0,0.4);
            animation: floatMap 4s ease-in-out infinite; 
            margin-top: 15px;
        }
        @keyframes floatMap { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-5px); } }
        
        .map-wrapper::after {
            content: '📍 Toca para abrir GPS'; position: absolute; bottom: 15px; left: 50%;
            transform: translateX(-50%); background: rgba(0, 0, 0, 0.85); color: white;
            padding: 10px 24px; border-radius: 30px; font-size: 13px; font-weight: 800;
            width: max-content; z-index: 5; backdrop-filter: blur(5px);
            border: 1px solid rgba(255,255,255,0.1);
        }
        .map-img { width: 100%; height: auto; display: block; border-radius: 17px; }

    </style>
</head>
<body>

    <div class="fondo-general"></div>
    <div class="heart-layer" id="heartLayer"></div>

    <div class="container">
        
        <!-- Cabecera Perfil (Estilo Portada Glassmorphism) -->
        <div class="corporate-card cover-card" id="perfil-wrapper">
            <div class="cover-img-container">
                <img src="https://i.postimg.cc/SQCyghrD/IMG-20250419-153933-174.jpg" alt="YOU TONY">
                <div class="cover-fade"></div>
            </div>
            
            <div class="cover-text">
                <!-- NUEVO: Título y Logo alineados -->
                <div class="title-wrapper">
                    <!-- He colocado un logo temporal con las iniciales TE (Trabajos El Alto). Puedes cambiar el src por la URL de tu propio logo si ya tienes uno en Postimages. -->
                    <img src="https://ui-avatars.com/api/?name=TE&background=0f020c&color=ff9ad0&size=150&rounded=true&bold=true" alt="trabajos el alto" class="company-logo">
                    <div class="text-group">
                        <h1>YOU TONY</h1>
                        <span class="assistant-text">Tu asistente de trabajo</span>
                    </div>
                </div>

                <div class="role-badge">
                    <p class="role-title">🔥 Requerimos Personal 🔥</p>
                </div>
            </div>
        </div>

        <!-- Temporizador y Oferta -->
        <div class="corporate-card offer-section">
            <div class="urgency-title">Proceso Abierto hasta el <span id="end-date-text"></span></div>
            
            <div class="countdown" id="countdown">
                <div class="time-box"><span id="days">00</span><small>Días</small></div>
                <div class="time-box"><span id="hours">00</span><small>Hrs</small></div>
                <div class="time-box"><span id="minutes">00</span><small>Min</small></div>
                <div class="time-box"><span id="seconds">00</span><small>Seg</small></div>
            </div>

            <div class="progress-container">
                <div class="progress-bar" id="timeProgress"></div>
            </div>
            <span class="progress-text">Cupos de entrevista reduciéndose rápidamente...</span>

            <div class="salary-box">
                <div class="dark-humor">"Turnos disponibles: mañana o tarde (4 horas)"</div>
                
                <div class="salary-row">
                    <span class="salary-label">Ingreso Semanal</span>
                    <span class="price-tag">600 Bs</span>
                </div>
                <div class="salary-row">
                    <span class="salary-label highlight">Ingreso Mensual</span>
                    <span class="price-tag mensual">2.400 Bs</span>
                </div>
            </div>
        </div>

        <!-- Info Vacantes -->
        <div class="corporate-card">
            <h2>Puestos Administrativos</h2>
            
            <div class="req-badge">
                🎯 Requisito: 18 a 28 años
            </div>

            <ul class="job-list">
                <li style="border-left-color: var(--color-blue);">Gestión de Atención al Cliente</li>
                <li style="border-left-color: var(--color-orange);">Registro de Datos y Llamadas</li>
                <li style="border-left-color: var(--color-red);">Apoyo en Marketing Digital</li>
            </ul>

            <div class="supervisor-contact">
                👨‍💼 Directo con el supervisor:
                <span class="num">75954334</span>
            </div>

            <!-- El mensaje de WhatsApp fue actualizado con "YOU TONY" -->
            <a href="https://wa.me/59175954334?text=HOLA%20YOU%20TONY%20ME%20DAS%20MAS%20INFORMACION%20DEL%20TRABAJO" target="_blank" class="btn-action" style="text-align: center; text-decoration: none;">Agendar Entrevista Oficial</a>
        </div>

        <!-- Mapa -->
        <div class="corporate-card map-section">
            <p style="font-family: 'Orbitron', sans-serif; margin: 0 0 8px 0; font-weight: 900; font-size: 20px; text-transform: uppercase;">Ubicación de Entrevistas</p>
            <p style="font-size: 14px; color: var(--text-muted); margin: 0; font-weight: 400; line-height: 1.5;"> Bolivia - La Paz - El Alto <br> Al frente de la Alcaldía quemada </p>
            
            <a href="https://maps.app.goo.gl/RLQBz58jcMQYmAWQ7" target="_blank" class="map-wrapper">
                <img src="https://i.postimg.cc/R02BTsnZ/IMG-20260325-093736-975.jpg" alt="Mapa El Alto" class="map-img">
            </a>
        </div>
    </div>

    <script>
        /* 1. Temporizador */
        function setupTimer() {
            // Se actualizó para el 31 de mayo de 2026. (El mes 4 en JavaScript equivale a Mayo)
            const targetDate = new Date(2026, 4, 31, 23, 59, 59); 
            
            document.getElementById('end-date-text').innerText = "31 de Mayo";

            function updateCountdown() {
                const currentDate = new Date();
                let timeRemaining = targetDate.getTime() - currentDate.getTime();
                if (timeRemaining < 0) timeRemaining = 0;

                document.getElementById('days').innerText = Math.floor(timeRemaining / (1000 * 60 * 60 * 24)).toString().padStart(2, '0');
                document.getElementById('hours').innerText = Math.floor((timeRemaining / (1000 * 60 * 60)) % 24).toString().padStart(2, '0');
                document.getElementById('minutes').innerText = Math.floor((timeRemaining / 1000 / 60) % 60).toString().padStart(2, '0');
                document.getElementById('seconds').innerText = Math.floor((timeRemaining / 1000) % 60).toString().padStart(2, '0');

                // Fecha de inicio de referencia para la barra de progreso (1 de Mayo de 2026)
                const startDate = new Date(2026, 4, 1).getTime();
                let percentage = ((currentDate.getTime() - startDate) / (targetDate.getTime() - startDate)) * 100;
                
                document.getElementById('timeProgress').style.width = Math.min(Math.max(percentage, 0), 100) + '%';
            }
            setTimeout(updateCountdown, 100); 
            setInterval(updateCountdown, 1000);
        }
        document.addEventListener('DOMContentLoaded', setupTimer);

        /* 3. Corazones Optimizados */
        (function(){
            const layer = document.getElementById('heartLayer');
            const COLORS = ["#bc13fe", "#ff007f", "#ffd700", "#ff9ad0"];
            const HEART_SVG = (fill) => `<svg viewBox="0 0 32 29.6" xmlns="http://www.w3.org/2000/svg"><path fill="${fill}" d="M23.6 0c-2.9 0-5.4 1.5-6.6 3.8C15.8 1.5 13.3 0 10.4 0 4.7 0 0 4.8 0 10.6c0 6.9 5.3 12.1 13.3 18.4L16 29.6l2.7-0.6C26.7 22.7 32 17.5 32 10.6 32 4.8 27.3 0 23.6 0z"/></svg>`;

            function createHeart(x, y) {
                const el = document.createElement('span');
                el.className = 'heart';
                el.innerHTML = HEART_SVG(COLORS[Math.floor(Math.random() * COLORS.length)]);
                el.style.left = (x - 15) + 'px';
                el.style.top = (y - 15) + 'px';
                el.style.transform = `rotate(${(Math.random() * 40) - 20}deg)`;
                
                layer.appendChild(el);
                el.addEventListener('animationend', () => { el.remove(); }, { once: true });
            }

            function handlePointer(x, y) {
                const count = 1 + Math.floor(Math.random() * 2);
                for (let i=0; i<count; i++){
                    createHeart(x + (Math.random() * 20 - 10), y + (Math.random() * 20 - 10));
                }
            }

            window.addEventListener('click', (e) => { handlePointer(e.clientX, e.clientY); });
            window.addEventListener('touchstart', (e) => {
                handlePointer(e.touches[0].clientX, e.touches[0].clientY);
            }, {passive:true});
        })();

        /* 4. Audio Perfil */
        document.addEventListener("DOMContentLoaded", () => {
            const perfilWrapper = document.getElementById('perfil-wrapper');
            const bgAudio = new Audio("https://www.dropbox.com/scl/fi/sm7gtduc8eamj0c4bnryn/Alok_-Alan-Walker-Headlights-Lyrics-ft.-KIDDO-MP3_160K.mp3?rlkey=turyzxelynu77zog74kb1oajj&st=jeznsnl1&dl=1");

            perfilWrapper.addEventListener('click', (e) => {
                e.stopPropagation(); 
                if (bgAudio.paused) bgAudio.play().catch(() => {});
                perfilWrapper.classList.add('shake-active');
                setTimeout(() => { perfilWrapper.classList.remove('shake-active'); }, 400);
            });
        });
    </script>
</body>
</html>
