<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reserva de Clases</title>
    <style>
        body {
            background: linear-gradient(to bottom, white, black);
            font-family: 'Arial', sans-serif;
            color: white;
        }
        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            text-align: center;
        }
        .options {
            margin: 20px 0;
        }
        .button {
            padding: 20px;
            margin: 10px;
            font-size: 20px;
            background-color: rgba(0, 0, 0, 0.7);
            border: none;
            cursor: pointer;
            color: white;
            width: 200px;
        }
        .button:hover {
            background-color: rgba(255, 255, 255, 0.3);
        }
        .name {
            position: fixed;
            bottom: 20px;
            right: 20px;
            font-size: 16px;
            color: rgba(255, 255, 255, 0.7);
        }
        .hidden {
            display: none;
        }
        .form-container {
            background-color: rgba(0, 0, 0, 0.8);
            padding: 20px;
            border-radius: 10px;
        }
        .form-container input, .form-container textarea {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
            color: black;
        }
        .form-container button {
            padding: 10px;
            margin-top: 10px;
            background-color: white;
            color: black;
            border: none;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 style="color: black;">¿De qué quieres que te dé clase?</h1>
        <div class="options">
            <button class="button" onclick="showExperience('math')">MATEMÁTICAS</button>
            <button class="button" onclick="showExperience('english')">INGLÉS</button>
        </div>
        <div class="name">Marcos Martínez Aguiar</div>
    </div>

    <div id="experience-math" class="hidden">
        <div class="container">
            <h2>Experiencia en este ámbito:</h2>
            <p>Marcos Martínez es un apasionado de las matemáticas, ha cursado esta asignatura toda su vida y con grandes resultados. Actualmente Marcos está estudiando la carrera de Ciencia de los Datos Aplicada en la Universidad Complutense de Madrid, dicha carrera destaca por ser muy novedosa, adaptando las matemáticas y la programación a las ciencias sociales, lo que le sirve para estar considerada como una de las carreras del futuro. Por lo que el profesor sigue formándose con las matemáticas de la mano.</p>
            <button class="button" onclick="showForm()">Reservar Clase</button>
        </div>
    </div>

    <div id="experience-english" class="hidden">
        <div class="container">
            <h2>Experiencia en este ámbito:</h2>
            <p>Marcos Martínez ha formado toda su vida parte de un colegio bilingüe, por lo que siempre ha tenido el inglés muy presente. Además, nuestro profesor ha viajado a varios países para poder seguir desarrollando este idioma, hospedándose tanto en residencias como en familias del país visitado. Dicha lista de países son Irlanda, Reino Unido y Estados Unidos. Marcos estuvo este último verano trabajando en este país en un campamento en el estado de Nueva York, lo que fue una gran experiencia para él. Todas estas vivencias le han dado mucho conocimiento del Inglés, haciéndolo prácticamente bilingüe.</p>
            <button class="button" onclick="showForm()">Reservar Clase</button>
        </div>
    </div>

    <div id="form" class="hidden">
        <div class="container">
            <div class="form-container">
                <h2>Reservar Clase</h2>
                <input type="text" id="studentName" placeholder="Nombre y apellidos del alumno" required>
                <input type="text" id="studentAddress" placeholder="Dirección de la casa del alumno" required>
                <input type="text" id="classDuration" placeholder="Duración de la clase" required>
                <input type="text" id="classStartTime" placeholder="Hora de comienzo" required>
                <input type="text" id="classDay" placeholder="Día de la semana" required>
                <input type="tel" id="studentPhone" placeholder="Teléfono de contacto" required>
                <input type="email" id="studentEmail" placeholder="e mail de contacto" required>
                <button onclick="submitForm()">Enviar</button>
            </div>
        </div>
    </div>

    <script>
        function showExperience(subject) {
            document.querySelector('.container').classList.add('hidden');
            document.getElementById('experience-' + subject).classList.remove('hidden');
        }

        function showForm() {
            document.getElementById('experience-math').classList.add('hidden');
            document.getElementById('experience-english').classList.add('hidden');
            document.getElementById('form').classList.remove('hidden');
        }

        function submitForm() {
            const name = document.getElementById('studentName').value;
            const address = document.getElementById('studentAddress').value;
            const duration = document.getElementById('classDuration').value;
            const startTime = document.getElementById('classStartTime').value;
            const day = document.getElementById('classDay').value;
            const phone = document.getElementById('studentPhone').value;
            const email = document.getElementById('studentEmail').value;

            const mailtoLink = `https://mail.google.com/mail/?view=cm&fs=1&to=marcosmartinezaguiar@gmail.com&su=Reserva%20de%20Clase&body=Nombre:%20${name}%0A
                Dirección:%20${address}%0A
                Duración:%20${duration}%0A
                Hora%20de%20comienzo:%20${startTime}%0A
                Día%20de%20la%20semana:%20${day}%0A
                Teléfono:%20${phone}%0A
                e%20mail:%20${email}`;

            window.open(mailtoLink, '_blank');
            alert("Muchas gracias por la oportunidad, esperamos que la clase vaya genial !!!!");
            setTimeout(function() {
                location.reload();
            }, 3000);
        }
    </script>
</body>
</html>
