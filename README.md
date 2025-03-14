<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Moschea della Città</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Poppins', sans-serif;
            background: #f5f1e9;
            color: #4a3f35;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            transition: background 0.3s, color 0.3s;
        }
        .container {
            max-width: 900px;
            width: 100%;
            text-align: center;
        }
        header h1 {
            font-size: 2.5em;
            color: #b6895b;
            margin-bottom: 10px;
        }
        header p {
            font-size: 1.2em;
            color: #6b5b4b;
            margin-bottom: 20px;
        }
        .info-box {
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease-in-out;
            cursor: pointer;
            margin-bottom: 15px;
            text-align: left;
        }
        .info-box:hover {
            transform: translateY(-5px);
        }
        .info-box h3 {
            font-size: 1.5rem;
            color: #4a3f35;
        }
        .details {
            display: none;
            padding: 15px;
            background: #faf3e0;
            margin-top: 10px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            font-size: 1.1em;
            line-height: 1.6;
        }
        footer {
            background: #4a3f35;
            color: white;
            padding: 15px;
            text-align: center;
            margin-top: 30px;
            width: 100%;
        }
        /* Modalità Notte */
        .night-mode {
            background: #1e1e1e;
            color: #f5f5f5;
        }
        .night-mode .info-box {
            background: #2c2c2c;
            color: #f5f5f5;
        }
        .night-mode .details {
            background: #3c3c3c;
        }
        .toggle-btn {
            background: #b6895b;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1em;
            margin-bottom: 20px;
            transition: background 0.3s;
        }
        .toggle-btn:hover {
            background: #9e724c;
        }
    </style>
</head>
<body>

    <button class="toggle-btn" id="modeToggle" onclick="toggleNightMode()">🌙 Modalità Notte</button>

    <div class="container">
        <header>
            <h1>Moschea della Città</h1>
            <p>Un luogo di preghiera, comunità e conoscenza.</p>
        </header>

        <div class="info-box" onclick="toggleDetails('chi-siamo')">
            <h3>🏛️ Chi Siamo</h3>
            <div id="chi-siamo" class="details">
                <p>La Moschea della Città è un luogo di culto e comunità che accoglie tutti i fedeli. Offriamo supporto spirituale e sociale.</p>
            </div>
        </div>
        
        <div class="info-box" onclick="toggleDetails('ramadan')">
            <h3>📄 Orari Ramadan 2025</h3>
            <div id="ramadan" class="details">
                <iframe src="Sabato 1 giorno . Ramadan 2025.pdf" width="100%" height="500px"></iframe>
                <p><a href="Sabato 1 giorno . Ramadan 2025.pdf" target="_blank">📥 Scarica il PDF di Ramadan 2025</a></p>
            </div>
        </div>

        <div class="info-box" onclick="toggleDetails('associazione')">
            <h3>🏢 Associazione Culturale</h3>
            <div id="associazione" class="details">
                <p><strong>Nome:</strong> Associazione Culturale Italo-Araba di Legnano</p>
                <p><strong>Indirizzo:</strong> Via XX Settembre, 96, 20025 Legnano, MI</p>
                <p><strong>Email:</strong> <a href="mailto:ASS.CULT.ITALO.ARABA@TISCALI.IT">ASS.CULT.ITALO.ARABA@TISCALI.IT</a></p>
                <p><strong>Telefono:</strong> +39 389 167 8940</p>
                <p><strong>Facebook:</strong> <a href="#">Associazione Culturale Italo-Araba di Legnano</a></p>
            </div>
        </div>
    </div>

    <footer>
        &copy; 2025 Moschea della Città | Tutti i diritti riservati.
    </footer>

    <script>
        function toggleDetails(id) {
            var section = document.getElementById(id);
            var allSections = document.querySelectorAll('.details');
            allSections.forEach(s => {
                if (s.id !== id) s.style.display = 'none';
            });
            section.style.display = (section.style.display === 'block') ? 'none' : 'block';
        }

        function toggleNightMode() {
            let body = document.body;
            let button = document.getElementById("modeToggle");

            body.classList.toggle("night-mode");

            if (body.classList.contains("night-mode")) {
                localStorage.setItem("theme", "dark");
                button.innerHTML = "☀ Modalità Giorno";
            } else {
                localStorage.setItem("theme", "light");
                button.innerHTML = "🌙 Modalità Notte";
            }
        }

        // Mantiene la modalità selezionata tra una visita e l'altra
        document.addEventListener("DOMContentLoaded", function () {
            if (localStorage.getItem("theme") === "dark") {
                document.body.classList.add("night-mode");
                document.getElementById("modeToggle").innerHTML = "☀ Modalità Giorno";
            }
        });
    </script>

</body>
</html>
