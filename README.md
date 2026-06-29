<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>XV Años · Ivanna Reyes Ávila</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Georgia', serif;
            background: linear-gradient(135deg, #f5f0ff 0%, #fff5f7 100%);
            color: #4a4a4a;
            overflow-x: hidden;
        }

        /* Audio player */
        audio {
            display: none;
        }

        .audio-controls {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 1000;
            background: rgba(200, 150, 220, 0.9);
            border-radius: 50px;
            padding: 10px 20px;
            cursor: pointer;
            font-size: 24px;
            transition: all 0.3s ease;
        }

        .audio-controls:hover {
            background: rgba(200, 150, 220, 1);
            transform: scale(1.1);
        }

        /* Animación de mariposas */
        @keyframes flutter {
            0%, 100% { transform: translateY(0px) rotate(0deg); opacity: 1; }
            50% { transform: translateY(-20px) rotate(10deg); }
        }

        @keyframes float {
            0%, 100% { transform: translateX(0px) translateY(0px); }
            25% { transform: translateX(30px) translateY(-30px); }
            50% { transform: translateX(0px) translateY(-60px); }
            75% { transform: translateX(-30px) translateY(-30px); }
        }

        .butterfly {
            position: fixed;
            font-size: 30px;
            pointer-events: none;
            z-index: 10;
        }

        .butterfly:nth-child(1) { animation: float 8s infinite; left: 10%; top: 20%; animation-delay: 0s; }
        .butterfly:nth-child(2) { animation: float 10s infinite; right: 10%; top: 30%; animation-delay: 2s; }
        .butterfly:nth-child(3) { animation: float 12s infinite; left: 20%; top: 60%; animation-delay: 4s; }
        .butterfly:nth-child(4) { animation: float 11s infinite; right: 20%; top: 70%; animation-delay: 1s; }
        .butterfly:nth-child(5) { animation: float 9s infinite; left: 50%; top: 40%; animation-delay: 3s; }

        /* Secciones principales */
        .section {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 40px 20px;
        }

        /* Portada */
        .cover {
            background: linear-gradient(135deg, #d4a5d9 0%, #f0e6f6 50%, #fef5eb 100%);
            position: relative;
            overflow: hidden;
        }

        .cover-content {
            text-align: center;
            z-index: 5;
            animation: fadeInDown 1s ease;
        }

        .cover h1 {
            font-size: 150px;
            font-weight: bold;
            background: linear-gradient(135deg, #c494c8 0%, #d4a5d9 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            line-height: 1;
            margin: 20px 0;
        }

        .cover h2 {
            font-size: 48px;
            color: #8b5a8e;
            margin: 20px 0;
            font-weight: 500;
        }

        .cover .subtitle {
            font-size: 24px;
            color: #a073a0;
            margin: 40px 0;
            letter-spacing: 4px;
        }

        .butterfly-symbol {
            font-size: 40px;
            margin: 20px 0;
            animation: flutter 2s infinite;
        }

        .open-btn {
            margin-top: 40px;
            padding: 15px 40px;
            background: linear-gradient(135deg, #c494c8 0%, #d4a5d9 100%);
            color: white;
            border: none;
            border-radius: 50px;
            font-size: 18px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 30px rgba(196, 148, 200, 0.3);
        }

        .open-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(196, 148, 200, 0.4);
        }

        /* Invitación */
        .invitation {
            background: linear-gradient(135deg, #fef5eb 0%, #fff5f7 50%, #f5f0ff 100%);
            display: none;
        }

        .invitation.show {
            display: flex;
        }

        .invitation-content {
            max-width: 600px;
            text-align: center;
            animation: fadeInUp 1s ease;
        }

        .invitation h2 {
            font-size: 36px;
            color: #8b5a8e;
            margin-bottom: 30px;
        }

        .invitation h3 {
            font-size: 120px;
            color: #d4a5d9;
            font-weight: bold;
            line-height: 1;
            margin: 20px 0;
        }

        .invitation .year {
            font-size: 48px;
            color: #a073a0;
            margin: 20px 0;
        }

        .invitation-text {
            font-size: 18px;
            line-height: 1.8;
            color: #6a6a6a;
            margin: 40px 0;
            font-style: italic;
        }

        .scroll-hint {
            margin-top: 60px;
            font-size: 14px;
            color: #c494c8;
            animation: bounce 2s infinite;
        }

        /* Padres y Padrinos */
        .family {
            background: linear-gradient(135deg, #f5f0ff 0%, #fef5eb 100%);
        }

        .family-content {
            max-width: 800px;
            width: 100%;
        }

        .family h2 {
            text-align: center;
            font-size: 42px;
            color: #8b5a8e;
            margin-bottom: 60px;
        }

        .family-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-bottom: 60px;
        }

        .family-card {
            text-align: center;
            animation: fadeInUp 0.8s ease;
        }

        .family-card h3 {
            font-size: 14px;
            color: #c494c8;
            letter-spacing: 2px;
            margin-bottom: 15px;
            text-transform: uppercase;
        }

        .family-card .name {
            font-size: 28px;
            color: #8b5a8e;
            margin-bottom: 20px;
            font-weight: 500;
        }

        /* Cuenta Regresiva */
        .countdown {
            background: linear-gradient(135deg, #d4a5d9 0%, #f0e6f6 50%, #fef5eb 100%);
        }

        .countdown-content {
            text-align: center;
            max-width: 900px;
        }

        .countdown h2 {
            font-size: 48px;
            color: #8b5a8e;
            margin-bottom: 60px;
        }

        .countdown-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
            gap: 20px;
            margin: 40px 0;
        }

        .countdown-item {
            background: rgba(255, 255, 255, 0.8);
            padding: 30px 20px;
            border-radius: 15px;
            backdrop-filter: blur(10px);
            box-shadow: 0 8px 32px rgba(196, 148, 200, 0.15);
        }

        .countdown-item .number {
            font-size: 48px;
            font-weight: bold;
            color: #d4a5d9;
        }

        .countdown-item .label {
            font-size: 14px;
            color: #8b5a8e;
            margin-top: 10px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* Detalles del Evento */
        .event-details {
            background: linear-gradient(135deg, #fef5eb 0%, #fff5f7 50%, #f5f0ff 100%);
        }

        .event-content {
            max-width: 800px;
            width: 100%;
        }

        .event-content h2 {
            text-align: center;
            font-size: 42px;
            color: #8b5a8e;
            margin-bottom: 80px;
        }

        .event-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 50px;
        }

        .event-card {
            text-align: center;
            animation: fadeInUp 0.8s ease;
        }

        .event-icon {
            font-size: 48px;
            margin-bottom: 20px;
        }

        .event-card h3 {
            font-size: 24px;
            color: #8b5a8e;
            margin-bottom: 15px;
        }

        .event-time {
            font-size: 36px;
            font-weight: bold;
            color: #d4a5d9;
            margin: 15px 0;
        }

        .event-location {
            font-size: 16px;
            color: #6a6a6a;
            margin: 15px 0;
        }

        .event-link {
            display: inline-block;
            margin-top: 15px;
            padding: 10px 20px;
            background: linear-gradient(135deg, #c494c8 0%, #d4a5d9 100%);
            color: white;
            text-decoration: none;
            border-radius: 25px;
            font-size: 14px;
            transition: all 0.3s ease;
        }

        .event-link:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(196, 148, 200, 0.3);
        }

        /* Código de Vestimenta */
        .dress-code {
            background: linear-gradient(135deg, #f5f0ff 0%, #fef5eb 100%);
        }

        .dress-code-content {
            max-width: 600px;
            text-align: center;
        }

        .dress-code h2 {
            font-size: 48px;
            color: #8b5a8e;
            margin-bottom: 40px;
        }

        .dress-code p {
            font-size: 20px;
            color: #6a6a6a;
            line-height: 1.8;
            margin: 20px 0;
        }

        .dress-code strong {
            color: #d4a5d9;
            font-weight: 600;
        }

        /* Confirmación */
        .confirmation {
            background: linear-gradient(135deg, #d4a5d9 0%, #f0e6f6 50%, #fef5eb 100%);
        }

        .confirmation-content {
            max-width: 600px;
            text-align: center;
        }

        .confirmation h2 {
            font-size: 42px;
            color: #8b5a8e;
            margin-bottom: 20px;
        }

        .confirmation p {
            font-size: 18px;
            color: #6a6a6a;
            line-height: 1.8;
            margin: 30px 0;
        }

        .confirm-btn {
            margin-top: 30px;
            padding: 15px 50px;
            background: linear-gradient(135deg, #c494c8 0%, #d4a5d9 100%);
            color: white;
            border: none;
            border-radius: 50px;
            font-size: 18px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 30px rgba(196, 148, 200, 0.3);
        }

        .confirm-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(196, 148, 200, 0.4);
        }

        /* Footer */
        footer {
            background: linear-gradient(135deg, #8b5a8e 0%, #c494c8 100%);
            color: white;
            text-align: center;
            padding: 30px 20px;
            font-size: 16px;
        }

        /* Animaciones */
        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .cover h1 {
                font-size: 80px;
            }

            .cover h2 {
                font-size: 28px;
            }

            .invitation h3 {
                font-size: 70px;
            }

            .countdown-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .event-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Mariposas animadas -->
    <div class="butterfly">🦋</div>
    <div class="butterfly">🦋</div>
    <div class="butterfly">🦋</div>
    <div class="butterfly">🦋</div>
    <div class="butterfly">🦋</div>

    <!-- Control de audio -->
    <audio id="backgroundMusic" autoplay loop>
        <source src="musica/cancion.mp3" type="audio/mpeg">
    </audio>
    
    <div class="audio-controls" onclick="toggleMusic()">🎵</div>

    <!-- Portada -->
    <section class="section cover">
        <div class="cover-content">
            <p class="subtitle">Con todo nuestro amor, te invitamos a celebrar</p>
            <h1>XV</h1>
            <p style="font-size: 24px; color: #a073a0; margin: 10px 0;">Años</p>
            <div class="butterfly-symbol">✦</div>
            <h2>Ivanna Reyes Ávila</h2>
            <div class="butterfly-symbol">✦</div>
            <p class="subtitle" style="margin-top: 30px;">10 · Octubre · 2026</p>
            <button class="open-btn" onclick="scrollToSection('invitation')">🦋 Abrir Invitación</button>
        </div>
    </section>

    <!-- Invitación -->
    <section class="section invitation" id="invitation">
        <div class="invitation-content">
            <p style="font-size: 18px; color: #a073a0;">Con todo nuestro amor te invitamos a mis</p>
            <h3>XV</h3>
            <div class="butterfly-symbol">🦋</div>
            <h2>Ivanna Reyes Ávila</h2>
            <div class="butterfly-symbol">✦</div>
            <p class="year">10 · Octubre · 2026</p>
            
            <div class="invitation-text">
                <p>Existen momentos en la vida que imaginamos, soñamos y esperamos, uno de esos momentos ha llegado…</p>
                <p style="margin-top: 20px;">Deseo compartirlo con las personas que siempre están presentes en mi vida…</p>
                <p style="margin-top: 20px; color: #c494c8;"><em>Tú eres una de ellas…</em></p>
            </div>

            <div class="scroll-hint">↓ Desliza ↓</div>
        </div>
    </section>

    <!-- Padres y Padrinos -->
    <section class="section family">
        <div class="family-content">
            <p style="text-align: center; font-size: 18px; color: #a073a0; margin-bottom: 20px;">Con el amor de</p>
            <h2>Quienes la han visto crecer 🦋</h2>
            
            <div class="family-grid">
                <div class="family-card">
                    <h3>Sus Padres</h3>
                    <div class="name">Azucena Ávila Carrera</div>
                    <div class="name" style="color: #6a6a6a; font-size: 18px; margin: 0;">y</div>
                    <div class="name">Braulio Reyes González</div>
                </div>
            </div>

            <h2 style="margin-top: 60px; margin-bottom: 40px;">Padrinos</h2>
            <div class="family-grid">
                <div class="family-card">
                    <div class="name">Luis Alberto Ávila</div>
                </div>
                <div class="family-card">
                    <div class="name">Maria Isabel Galeno García</div>
                </div>
            </div>

            <div style="text-align: center; margin-top: 60px; font-size: 36px;">✦</div>
        </div>
    </section>

    <!-- Cuenta Regresiva -->
    <section class="section countdown">
        <div class="countdown-content">
            <h2>La gran noche se acerca 🦋</h2>
            <div class="countdown-grid">
                <div class="countdown-item">
                    <div class="number" id="days">--</div>
                    <div class="label">Días</div>
                </div>
                <div class="countdown-item">
                    <div class="number" id="hours">--</div>
                    <div class="label">Horas</div>
                </div>
                <div class="countdown-item">
                    <div class="number" id="minutes">--</div>
                    <div class="label">Minutos</div>
                </div>
                <div class="countdown-item">
                    <div class="number" id="seconds">--</div>
                    <div class="label">Segundos</div>
                </div>
            </div>
            <p style="font-size: 18px; color: #6a6a6a; margin-top: 60px; line-height: 1.8;">
                Una noche mágica para celebrar el inicio de una nueva etapa llena de sueños, mariposas y amor.
            </p>
        </div>
    </section>

    <!-- Detalles del Evento -->
    <section class="section event-details">
        <div class="event-content">
            <h2>Esperamos tu presencia</h2>
            <div class="event-grid">
                <div class="event-card">
                    <div class="event-icon">⛪</div>
                    <h3>Ceremonia Religiosa</h3>
                    <div class="event-time">5:00 pm</div>
                    <div class="event-location">✦</div>
                    <div class="event-location">Iglesia del Carmen</div>
                    <a href="https://maps.app.goo.gl/iQB4kXKF3JeeUBV16" target="_blank" class="event-link">Ver ubicación en Maps</a>
                </div>
                <div class="event-card">
                    <div class="event-icon">🥂</div>
                    <h3>Recepción</h3>
                    <div class="event-time">6:00 pm</div>
                    <div class="event-location">✦</div>
                    <div class="event-location">Salón de Eventos ARRO</div>
                    <a href="https://maps.app.goo.gl/Zw4wrgHcZgs8275q8" target="_blank" class="event-link">Ver ubicación en Maps</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Código de Vestimenta -->
    <section class="section dress-code">
        <div class="dress-code-content">
            <h2>Código de Vestimenta</h2>
            <p style="font-size: 32px; margin-bottom: 40px;">Etiqueta Formal</p>
            <div style="font-size: 18px; line-height: 2;">
                <p>✦</p>
                <p>El tono <strong>lila</strong> está reservado<br>exclusivamente para la quinceañera.</p>
                <p style="margin-top: 40px;">🦋</p>
            </div>
        </div>
    </section>

    <!-- Confirmación -->
    <section class="section confirmation">
        <div class="confirmation-content">
            <h2>Confirmación de Asistencia 🦋</h2>
            <p>Tu presencia es el mejor regalo para Ivanna en este día tan especial.</p>
            <button class="confirm-btn" onclick="confirmAttendance()">Confirmar Asistencia</button>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p>Con cariño · Familia Reyes Ávila · 2026</p>
        <p style="font-size: 24px; margin-top: 10px;">🎵</p>
    </footer>

    <script>
        // Control de música
        let musicPlaying = true;
        const audioElement = document.getElementById('backgroundMusic');

        function toggleMusic() {
            const btn = document.querySelector('.audio-controls');
            if (musicPlaying) {
                audioElement.pause();
                btn.textContent = '🔇';
                musicPlaying = false;
            } else {
                audioElement.play();
                btn.textContent = '🎵';
                musicPlaying = true;
            }
        }

        // Scroll suave
        function scrollToSection(sectionId) {
            const section = document.getElementById(sectionId);
            if (section) {
                section.classList.add('show');
                section.scrollIntoView({ behavior: 'smooth' });
            }
        }

        // Cuenta Regresiva
        function updateCountdown() {
            const targetDate 
