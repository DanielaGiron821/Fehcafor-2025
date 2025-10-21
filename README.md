<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FEHCAFOR</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        /* CSS adicional */
        body {
            
            font-family: 'Poppins', sans-serif;
            scroll-behavior: smooth;
        }

        .hero-slider {
            position: relative;
            height: 90vh;
            overflow: hidden;
            animation: fadeIn 4s ease-in-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .slides {
            position: relative;
            width: 100%;
            height: 100%;
        }

        .slide {
            position: absolute;
            width: 100%;
            height: 100%;
            object-fit: cover;
            opacity: 0;
            transition: opacity 4s ease-in-out;
        }

        .slide.active {
            opacity: 1;
        }

        .program {
            animation: slideInUp 0.4s ease-in-out;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s, box-shadow 0.3s, background-color 0.3s;
            cursor: pointer;
            /* Para interactividad */
        }

        .program:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
        }

        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .search-results {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1001;
            animation: zoomIn 0.1s ease-in-out;
        }

        @keyframes zoomIn {
            from {
                transform: scale(0.9);
                opacity: 0;
            }

            to {
                transform: scale(1);
                opacity: 1;
            }
        }

        .results-content {
            max-width: 500px;
            padding: 20px;
            background-color: white;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        .results-content ul {
            padding: 0;
        }

        .results-content ul li {
            list-style: none;
            margin-bottom: 10px;
        }

        .scroll-to-top {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: blue;
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: background 0.4s;
            opacity: 0;
            visibility: hidden;
            z-index: 999;
        }

        .scroll-to-top.show {
            opacity: 1;
            visibility: visible;
        }

        .logo-large {
            width: 130px;
            height: 150px;
            border-radius: 0px;
            object-fit: cover;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .navbar-spaced {
            padding: 1rem 3rem;
        }

        .fixed-header {
            position: fixed;
            top: 64px;
            width: 100%;
            background-color: #f9f9f9;
            z-index: 40;
            padding: 1rem;
            text-align: center;
        }

        /* Modal styles for interactivity */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 2000;
            animation: zoomIn 0.3s ease-in-out;
        }

        .modal-content {
            background: white;
            padding: 20px;
            border-radius: 10px;
            max-width: 500px;
            text-align: center;
            color: black;
            
        }

        .media-container {
    display: flex; /* Alinea elementos horizontalmente */
    justify-content: center; /* Centra el grupo horizontalmente en la página (opcional) */
    align-items: center; /* Alinea verticalmente si tienen alturas diferentes */
    gap: 20px; /* Espacio entre video e imagen (ajusta a gusto) */
}
video {
    width: 640px; /* Ancho fijo para el video; ajusta si es necesario */
    height: auto; /* Mantiene proporción */
}
img {
    width: 50%; /* Como en tu código; ajusta si quieres tamaño fijo */
    height: auto; /* Mantiene proporción */
    max-width: 300px; /* Límite opcional para evitar que sea demasiado grande */
}

        
    </style>
</head>

<body class="bg-gray-50">
    <!-- Scroll to Top Button -->
    <button class="scroll-to-top" onclick="window.scrollTo({top: 0, behavior: 'smooth'})"
        aria-label="Ir arriba">↑</button>

    <!-- Barra de navegación -->
    <nav
        class="bg-green-900 bg-opacity-95 backdrop-blur-sm text-white fixed top-0 w-full z-50 flex justify-between items-center navbar-spaced transition-all duration-300">
        <ul class="flex space-x-8">
            <li><a href="inicio.html" class="hover:text-yellow-400 font-semibold transition duration-200">Inicio</a>
            </li>
            <li><a href="quienes-somos.html" class="hover:text-yellow-400 font-semibold transition duration-200">Quiénes
                    Somos</a></li>
            <li><a href="sala-informativa.html" class="hover:text-yellow-400 font-semibold transition duration-200">Sala
                    Informativa</a>
            </li>
            <li><a href="galeria.html" class="hover:text-yellow-400 font-semibold transition duration-200">Galeria</a>
            </li>
            <li><a href="enlaces-interes.html"
                    class="hover:text-yellow-400 font-semibold transition duration-200">Enlaces de Interes</a></li>

            <li><a href="contactos.html"
                    class="hover:text-yellow-400 font-semibold transition duration-200">contactanos</a>
            </li>
        </ul>
    </nav>

    <!-- Sección fija para el logo -->
    <div
        class="bg-white -800 bg-opacity-95 backdrop-blur-sm fixed-header text-white  flex flex-row  items-center justify-center gap-8">
        <img src="img/logo_fehcafor.1.png" alt="Logo Fehcafor" class="logo-large w-50 h-auto">
        <div>
            <h1 class="text-3xl font-bold text-green-700 mb-2">FEHCAFOR</h1>
            <p class="text-xl text-green-700"><b>FEDERACIÓN HONDUREÑA DE COOPERATIVAS AGROFORESTALES</b></p>
        </div>
    </div> <br><br><br><br><br><br><br>

    <!-- Slider hero -->
    <section class="hero-slider">
        <div class="slides">
            <img src="img/img9.jpg" alt="Estudiantes trabajando en un taller" class="slide active" />
            <img src="img/img4.jpg" alt="Evento deportivo" class="slide" />
            <img src="img/img18.jpg" alt="Aula de alta tecnología" class="slide" />
            <img src="img/img8.jpg" alt="Aula de alta tecnología" class="slide" />
            <img src="img/img03.jpg" alt="Aula de alta tecnología" class="slide" />
            
        </div>
    </section>

    <!-- Sección de Nuestros Principios y Visión, ahora más atractiva e interactiva -->
    <section class="py-20" style="background-color: #ffffff;">
        <div class="container mx-auto px-6">
            <h2 class="text-4xl font-bold text-center text-green-800 mb-16"></h2>
            <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-10">
                <div class="program p-8 rounded-xl shadow-xl transform hover:scale-105 transition duration-300"
                    style="background: linear-gradient(135deg, #4CAF50 0%, #66BB6A 100%); color: black;"
                    onclick="openModal('vision')">
                    <h3 class="text-2xl font-semibold text-black mb-6 text-center"> Visión</h3>
                    <p class="text-black">Ser la organización grado lider, competitiva y sostenible del sector
                        agroforestal que promueve e impulsa el desarrollo ambiental, social y económico entre sus
                        organizaciones socias, basando su accionar en la aplicación de los principios y valores del
                        sector cooperativo.</p>
                    <button class="bg-black text-white py-2 px-4 rounded mt-4" onclick="openModal('vision')">Ver
                        más</button>
                </div>
                <div class="program p-8 rounded-xl shadow-xl transform hover:scale-105 transition duration-300"
                    style="background: linear-gradient(135deg, #4CAF50 0%, #66BB6A 100%); color: black;"
                    onclick="openModal('principios')">
                    <h3 class="text-2xl font-semibold text-black mb-6 text-center"> Principios Cooperativos</h3>
                    <p class="text-black text-center">1. Membresia abierta y voluntaria <br><br> 2. Control democrático
                        de los miembros <br><br> 3. Participacion económica de los miembros <br><br> 4. Autonomia e
                        Independencia <br><br> 5. Educación, Formación e Información <br><br> 6. Compromiso con la
                        comunidad <br><br> 7. Cooperación entre cooperativas</p>
                    <button class="bg-black text-white py-2 px-4 rounded mt-4" onclick="openModal('principios')">Ver
                        más</button>
                </div>
                <div class="program p-8 rounded-xl shadow-xl transform hover:scale-105 transition duration-300"
                    style="background: linear-gradient(135deg, #4CAF50 0%, #66BB6A 100%); color: black;"
                    onclick="openModal('mision')">
                    <h3 class="text-2xl font-semibold text-black mb-6 text-center"> Misión</h3>
                    <p class="text-black">Somos una organización de segundo grado del movimiento cooperativo hondureño,
                        que busca el desarrollo económico, ecológico y social de sus cooperativas de base, lográndolo a
                        traves de su representación gremial y brindando de manera eficiente y efectiva los servicios de
                        asesoría económica, empresarial, técnico y legal.</p>
                    <button class="bg-black text-white py-2 px-4 rounded mt-4" onclick="openModal('mision')">Ver
                        más</button>
                </div>
            </div>
        </div>
    </section>

    <!-- Modal para interactividad -->
    <div id="modal" class="modal">
        <div class="modal-content bg-white p-6 rounded-lg">
            <span class="close-btn text-black text-2xl cursor-pointer float-right" onclick="closeModal()">&times;</span>
            <h3 id="modal-title" class="text-2xl font-bold text-green-800 mb-4"></h3>
            <p id="modal-content" class="text-gray-700"></p>
        </div>
    </div>

    <!-- Presentación de la institución -->
    <section id="quienes-somos" class="py-20 bg-gradient-to-r from-gray-100 to-green-50">
        <div class="container mx-auto px-6 text-center">
            <h2 class="text-4xl font-bold text-black-900 mb-10">Presentación de Nuestra Federación</h2>
           
            <div class="media-container">
              <video controls>
               <source src="img/presentacion.mp4" type="video/mp4">
              </video>
             <img src="img/logo_fehcafor.1.png" alt="logo fehcafor" width="50" height="50">
            </div>
        </div>
    </section>

    <!-- Sección Historia -->
    <section id="historia" class="py-20 bg-white">
        <div class="container mx-auto px-6 max-w-4xl">
            <h2 class="text-4xl font-bold text-center text-black-900 mb-10">Historia</h2>
            <p class="text-lg text-gray-700 leading-relaxed">
                La Federación Hondureña de Cooperativas Agroforestales “FEHCAFOR” fue fundada el 8 de Agosto de 1974.
                En la actualidad FEHCAFOR cuenta con 96 Cooperativas afiliadas que agrupan aproximadamente a 4,800
                cooperativistas que se benefician en forma directa del manejo sostenible de recursos forestales, con un
                promedio de 24,000 personas que se relacionan en las actividades de trabajo con los mismos.
            </p>
        </div>
    </section>

    <!-- Pie de página -->
    <footer class="bg-green-900 text-white py-6 text-center">
        <p>&copy; 2025 FEHCAFOR.</p>
    </footer>

    <script>
        
        // Slider automático
        const slides = document.querySelectorAll('.slide');
        let currentSlide = 0;
        const slideInterval = 4000; // 4 segundos

        function showSlide(index) {
            slides.forEach((slide, i) => slide.classList.toggle('active', i === index));
        }

        function nextSlide() {
            currentSlide = (currentSlide + 1) % slides.length;
            showSlide(currentSlide);
        }

        setInterval(nextSlide, slideInterval);

        // Modal interactivity
        function openModal(type) {
            const modal = document.getElementById('modal');
            const title = document.getElementById('modal-title');
            const content = document.getElementById('modal-content');

            if (type === 'vision') {
                title.innerHTML = ' Visión Detallada';
                content.innerHTML = 'Estamos comprometidos con el liderazgo en el sector agroforestal, promoviendo prácticas sostenibles para el beneficio de todos.';
            } else if (type === 'principios') {
                title.innerHTML = ' Principios Cooperativos Detallados';
                content.innerHTML = 'Explora cada principio en profundidad.';
            } else if (type === 'mision') {
                title.innerHTML = ' Misión Detallada';
                content.innerHTML = 'Nuestra misión incluye servicios de asesoría económica y más, para el desarrollo de cooperativas en Honduras.';
            }
            modal.style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('modal').style.display = 'none';
        }

        
        // Animaciones de entrada
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('animate-fadeIn');
                    observer.unobserve(entry.target);
                }
            });
        });

        document.querySelectorAll('.program').forEach(el => observer.observe(el));

        
    </script>
</body>

</html>

<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FEHCAFOR - Quienes-somos</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        /* CSS adicional */
        body {
            font-family: 'Poppins', sans-serif;
            scroll-behavior: smooth;
        }

        .hero-slider {
            position: relative;
            height: 90vh;
            overflow: hidden;
            animation: fadeIn 4s ease-in-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .slides {
            position: relative;
            width: 100%;
            height: 100%;
        }

        .slide {
            position: absolute;
            width: 100%;
            height: 100%;
            object-fit: cover;
            opacity: 0;
            transition: opacity 4s ease-in-out;
        }

        .slide.active {
            opacity: 1;
        }

        .program {
            animation: slideInUp 0.4s ease-in-out;
        }
        

        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .search-results {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1001;
            animation: zoomIn 0.1s ease-in-out;
        }

        @keyframes zoomIn {
            from {
                transform: scale(0.9);
                opacity: 0;
            }

            to {
                transform: scale(1);
                opacity: 1;
            }
        }

        .results-content {
            max-width: 500px;
            padding: 20px;
            background-color: white;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        .results-content ul {
            padding: 0;
        }

        .results-content ul li {
            list-style: none;
            margin-bottom: 10px;
        }

        .scroll-to-top {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: blue;
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: background 0.4s;
            opacity: 0;
            visibility: hidden;
            z-index: 999;
        }

        .scroll-to-top.show {
            opacity: 1;
            visibility: visible;
        }

        .logo-large {
            width: 130px;
            height: 150px;
            border-radius: 0px;
            object-fit: cover;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .navbar-spaced {
            padding: 1rem 3rem;
        }
      /* Nueva clase para el contenedor fijo del logo */
        .fixed-header {
            position: fixed;
            top: 64px; /* Ajusta según la altura de la barra de navegación (aprox. 64px) */
            width: 100%;
            background-color: #f9f9f9; /* Color de fondo claro para que se vea bien */
            z-index: 40; /* Menor que la barra de navegación */
            padding: 1rem;
            text-align: center;
        }
        
        /* Estilos para secciones interactivas */
        .interactive-card {
            transition: transform 0.3s, box-shadow 0.3s;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }
        
        .interactive-card:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
        }
        
        .animate-fadeIn {
            animation: fadeIn 1s ease-in-out;
        }
    </style>
</head>

<body class="bg-gray-50">
    <!-- Scroll to Top Button -->
    <button class="scroll-to-top" onclick="window.scrollTo({top: 0, behavior: 'smooth'})"
        aria-label="Ir arriba">↑</button>

    <!-- Barra de navegación -->
    <nav
        class="bg-green-900 bg-opacity-95 backdrop-blur-sm text-white fixed top-0 w-full z-50 flex justify-between items-center navbar-spaced transition-all duration-300">
        <ul class="flex space-x-8">
            <li><a href="inicio.html" class="hover:text-yellow-400 font-semibold transition duration-200">Inicio</a>
            </li>
            <li><a href="quienes-somos.html" class="hover:text-yellow-400 font-semibold transition duration-200">Quiénes
                    Somos</a></li>
            <li><a href="sala-informativa.html" class="hover:text-yellow-400 font-semibold transition duration-200">Sala
                    Informativa</a>
            </li>
            <li><a href="galeria.html" class="hover:text-yellow-400 font-semibold transition duration-200">Galeria</a>
            </li>
            <li><a href="enlaces-interes.html"
                    class="hover:text-yellow-400 font-semibold transition duration-200">Enlaces de Interes</a></li>

            <li><a href="contactos.html"
                    class="hover:text-yellow-400 font-semibold transition duration-200">contactanos</a>
            </li>
        </ul>
    </nav>

    <!-- Sección fija para el logo y texto debajo de la barra de navegación -->
    <div class="bg-white -800 bg-opacity-95 backdrop-blur-sm fixed-header text-white  flex flex-row  items-center justify-center gap-8">
        <img src="img/logo_fehcafor.1.png" alt="Logo Fehcafor" class="logo-large w-50 h-auto"><!-- Reduje el tamaño para que quepa mejor -->
        <div>
            <h1 class="text-3xl font-bold text-green-700 mb-2">FEHCAFOR</h1>
            <p class="text-xl text-green-700"><b>FEDERACIÓN HONDUREÑA DE COOPERATIVAS AGROFORESTALES</b></p>
        </div>
    </div> <br><br><br><br><br><br><br>

    <!-- Sección Quiénes Somos - Interactiva y Llamativa -->
    <section id="quienes-somos" class="py-24 bg-green-100 animate-fadeIn">
        <div class="container mx-auto px-6">
            <h2 class="text-5xl font-bold text-center text-green-800 mb-12">Quiénes Somos en FEHCAFOR</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
                <!-- Tarjeta 1: Historia -->
                <div class="interactive-card p-8 bg-white rounded-xl shadow-lg hover:shadow-xl transition-all duration-300">
                    <h3 class="text-3xl font-semibold text-green-600 mb-4">Nuestra Historia</h3>
                    <p class="text-gray-700 mb-4">FEHCAFOR fue fundada en 1974 como una federación de cooperativas agroforestales en Honduras. Surgimos para unir esfuerzos en el manejo sostenible de recursos forestales y apoyar a comunidades rurales a través de iniciativas colectivas.</p>
                    <button onclick="window.open('https://www.fehcafor.org', '_blank')" class="bg-blue-500 text-white py-2 px-4 rounded hover:bg-blue-600 transition">Más sobre nuestra historia</button>
                </div>
                
                <!-- Tarjeta 2: Estructura y Miembros -->
                <div class="interactive-card p-8 bg-white rounded-xl shadow-lg hover:shadow-xl transition-all duration-300">
                    <h3 class="text-3xl font-semibold text-green-600 mb-4">Estructura y Miembros</h3>
                    <p class="text-gray-700 mb-4">Somos una organización que agrupa a 96 cooperativas, representando a más de 4,800 cooperativistas. Nuestros miembros trabajan en equipo para fomentar el desarrollo en áreas rurales, con un enfoque en la inclusión y la sostenibilidad.</p>
                    <button onclick="alert('Explora más sobre nuestros miembros en Facebook!')" class="bg-yellow-500 text-white py-2 px-4 rounded hover:bg-yellow-600 transition">Ver miembros interactivos</button>
                </div>
                
                <!-- Tarjeta 3: Actividades y Proyectos -->
                <div class="interactive-card p-8 bg-white rounded-xl shadow-lg hover:shadow-xl transition-all duration-300">
                    <h3 class="text-3xl font-semibold text-green-600 mb-4">Actividades y Proyectos</h3>
                    <p class="text-gray-700 mb-4">Nuestras actividades incluyen reforestación, capacitación en agricultura ecológica y alianzas internacionales. Participamos en proyectos que combaten la deforestación y generan empleos en Honduras.</p>
                    <button onclick="window.open('https://www.fehcafor.org', '_blank')" class="bg-purple-500 text-white py-2 px-4 rounded hover:bg-purple-600 transition">Explorar proyectos</button>
                </div>
                
                <!-- Tarjeta 4: Impacto -->
                <div class="interactive-card p-8 bg-white rounded-xl shadow-lg hover:shadow-xl transition-all duration-300">
                    <h3 class="text-3xl font-semibold text-green-600 mb-4">Nuestro Impacto</h3>
                    <p class="text-gray-700 mb-4">Hemos impactado a más de 24,000 personas a través de empleos y desarrollo comunitario. Nuestros esfuerzos protegen el medio ambiente y fortalecen la economía local en Honduras.</p>
                    <button onclick="window.open('https://www.facebook.com/FEHCAFOR', '_blank')" class="bg-red-500 text-white py-2 px-4 rounded hover:bg-red-600 transition">Ver impacto en acción</button>
                </div>
            </div>
        </div>
    </section>

    <!-- Pie de página -->
    <footer class="bg-green-900 text-white py-6 text-center">
        <p>&copy; 2025 FEHCAFOR.</p>
    </footer>

    <script>
        // Script para scroll suave
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FEHCAFOR - sala-informativa</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        /* CSS adicional */
        body {
            font-family: 'Poppins', sans-serif;
            scroll-behavior: smooth;
        }

        .hero-slider {
            position: relative;
            height: 90vh;
            overflow: hidden;
            animation: fadeIn 4s ease-in-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .slides {
            position: relative;
            width: 100%;
            height: 100%;
        }

        .slide {
            position: absolute;
            width: 100%;
            height: 100%;
            object-fit: cover;
            opacity: 0;
            transition: opacity 4s ease-in-out;
        }

        .slide.active {
            opacity: 1;
        }

        .program {
            animation: slideInUp 0.4s ease-in-out;
        }


        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .search-results {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1001;
            animation: zoomIn 0.1s ease-in-out;
        }

        @keyframes zoomIn {
            from {
                transform: scale(0.9);
                opacity: 0;
            }

            to {
                transform: scale(1);
                opacity: 1;
            }
        }

        .results-content {
            max-width: 500px;
            padding: 20px;
            background-color: white;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        .results-content ul {
            padding: 0;
        }

        .results-content ul li {
            list-style: none;
            margin-bottom: 10px;
        }

        .scroll-to-top {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: blue;
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: background 0.4s;
            opacity: 0;
            visibility: hidden;
            z-index: 999;
        }

        .scroll-to-top.show {
            opacity: 1;
            visibility: visible;
        }

        .logo-large {
            width: 130px;
            height: 150px;
            border-radius: 0px;
            object-fit: cover;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .navbar-spaced {
            padding: 1rem 3rem;
        }

        /* Nueva clase para el contenedor fijo del logo */
        .fixed-header {
            position: fixed;
            top: 64px;
            /* Ajusta según la altura de la barra de navegación (aprox. 64px) */
            width: 100%;
            background-color: #f9f9f9;
            /* Color de fondo claro para que se vea bien */
            z-index: 40;
            /* Menor que la barra de navegación */
            padding: 1rem;
            text-align: center;
        }

        .section-bg {
            background-color: #e0e0e0;
            padding: 2rem;
            border-radius: 1rem;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        .btn-facebook {
            background-color: #1877f2;
            /* Color de Facebook */
            color: white;
            padding: 0.75rem 1.5rem;
            border-radius: 0.5rem;
            transition: background-color 0.3s;
        }

        .btn-facebook:hover {
            background-color: #166fe5;
        }
    </style>
</head>

<body class="bg-gray-50">
    <!-- Scroll to Top Button -->
    <button class="scroll-to-top" onclick="window.scrollTo({top: 0, behavior: 'smooth'})"
        aria-label="Ir arriba">↑</button>

    <!-- Barra de navegación -->
    <nav
        class="bg-green-900 bg-opacity-95 backdrop-blur-sm text-white fixed top-0 w-full z-50 flex justify-between items-center navbar-spaced transition-all duration-300">
        <ul class="flex space-x-8">
            <li><a href="inicio.html" class="hover:text-yellow-400 font-semibold transition duration-200">Inicio</a>
            </li>
            <li><a href="quienes-somos.html" class="hover:text-yellow-400 font-semibold transition duration-200">Quiénes
                    Somos</a></li>
            <li><a href="sala-informativa.html" class="hover:text-yellow-400 font-semibold transition duration-200">Sala
                    Informativa</a>
            </li>
            <li><a href="galeria.html" class="hover:text-yellow-400 font-semibold transition duration-200">Galeria</a>
            </li>
            <li><a href="enlaces-interes.html"
                    class="hover:text-yellow-400 font-semibold transition duration-200">Enlaces de Interes</a></li>

            <li><a href="contactos.html"
                    class="hover:text-yellow-400 font-semibold transition duration-200">contactanos</a>
            </li>
        </ul>
    </nav>

    <!-- Sección fija para el logo y texto debajo de la barra de navegación -->
    <div
        class="bg-white -800 bg-opacity-95 backdrop-blur-sm fixed-header text-white  flex flex-row  items-center justify-center gap-8">
        <img src="img/logo_fehcafor.1.png" alt="Logo Fehcafor"
            class="logo-large w-50 h-auto"><!-- Reduje el tamaño para que quepa mejor -->
        <div>
            <h1 class="text-3xl font-bold text-green-700 mb-2">FEHCAFOR</h1>
            <p class="text-xl text-green-700"><b>FEDERACIÓN HONDUREÑA DE COOPERATIVAS AGROFORESTALES</b></p>
        </div>
    </div> <br><br><br><br><br><br><br>

    <!-- Contenido de Sala Informativa -->
    <header id="inicio" class="py-20 bg-green-600 text-white text-center">
        <div class="container mx-auto px-6">
            <h1 class="text-4xl font-bold mb-4">Capacitaciones y Asambleas</h1>
            <p class="text-xl">Encuentra información sobre los eventos, capacitaciones y asambleas de FEHCAFOR. Todo el
                contenido detallado está disponible en nuestra página de Facebook.</p>
        </div>
    </header>

    <!-- Sección de Capacitaciones -->
    <section id="capacitaciones" class="py-16">
        <div class="container mx-auto px-6">
            <h2 class="text-3xl font-bold text-center mb-6">Capacitaciones de FEHCAFOR</h2>
            <div class="section-bg">
                <p class="text-gray-700 mb-4">FEHCAFOR ofrece capacitaciones en temas como manejo sostenible de recursos
                    forestales, agricultura ecológica y desarrollo comunitario. Estas sesiones incluyen talleres
                    prácticos y cursos para empoderar a cooperativistas y comunidades rurales.</p>
                <p class="text-gray-700 mb-4">Para ver los detalles de las próximas capacitaciones, horarios,
                    inscripciones y materiales, visita nuestra página de Facebook donde publicamos actualizaciones
                    regulares.</p>
                <a href="https://www.facebook.com/FEHCAFOR" target="_blank" class="btn-facebook block mx-auto w-fit">Ir
                    a Facebook para más información</a>
            </div>
        </div>
    </section>

    <!-- Sección de Asambleas -->
    <section id="asambleas" class="py-16 bg-gray-100">
        <div class="container mx-auto px-6">
            <h2 class="text-3xl font-bold text-center mb-6">Asambleas y Eventos</h2>
            <div class="section-bg">
                <p class="text-gray-700 mb-4">Las asambleas de FEHCAFOR son eventos clave para discutir temas
                    importantes como el control democrático, planes de acción y alianzas. Incluyen reuniones generales,
                    conferencias y actividades comunitarias.</p>
                <p class="text-gray-700 mb-4">Encuentra fechas, agendas, resúmenes y fotos de asambleas pasadas en
                    nuestra página de Facebook. ¡Síguenos para no perderte ningún evento!</p>
                <a href="https://www.facebook.com/FEHCAFOR" target="_blank" class="btn-facebook block mx-auto w-fit">Ver
                    asambleas en Facebook</a>
            </div>
        </div>
    </section>

    <!-- Sección de Contacto -->
<section id="contacto" class="py-16">
    <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center mb-6">Contacto</h2>
        <div class="section-bg text-center">
            <p class="text-gray-700 mb-4">Si necesitas más detalles sobre capacitaciones o asambleas, contáctanos directamente:</p>
            <p><strong>Correo:</strong> <a href="mailto:fehcafor1974@gmail.com" class="text-blue-600 hover:underline">fehcafor1974@gmail.com</a></p>
            <p><strong>Teléfono:</strong> <a href="tel:+50422270059" class="text-blue-600 hover:underline">+504 2227-0059</a></p>
           <p><strong>Dirección:</strong> <a
                            href="https://www.google.com/maps/search/Colonia+Mayangle+2da+entrada%2C+casa+1659%2C+una+cuadra+Oeste+de+Cruz+Roja+Hondureña%2C+Comayagüela%2C+Honduras"
                            target="_blank" class="text-blue-600 hover:underline">Col- Mayangle. esquina opuesta a Cruz
                            Roja Hondureña, contiguo a Save The Childrens, Casa No. 2211.</a></p>
            <p class="mt-4">O síguenos en redes para actualizaciones en tiempo real:</p>
            <a href="https://www.facebook.com/FEHCAFOR" target="_blank" class="text-blue-600 hover:underline">Página de Facebook de FEHCAFOR</a>
        </div>
    </div>
</section>


    <!-- Pie de página -->
    <footer class="bg-green-900 text-white py-6 text-center">
        <p>&copy; 2025 FEHCAFOR.</p>
    </footer>

    <script>
        // Script para scroll suave
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });
    </script>
</body>

</html>

<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FEHCAFOR - Galeria</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        /* CSS adicional */
        body {
            font-family: 'Poppins', sans-serif;
            scroll-behavior: smooth;
        }

        .hero-slider {
            position: relative;
            height: 90vh;
            overflow: hidden;
            animation: fadeIn 4s ease-in-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .slides {
            position: relative;
            width: 100%;
            height: 100%;
        }

        .slide {
            position: absolute;
            width: 100%;
            height: 100%;
            object-fit: cover;
            opacity: 0;
            transition: opacity 4s ease-in-out;
        }

        .slide.active {
            opacity: 1;
        }

        .program {
            animation: slideInUp 0.4s ease-in-out;
        }


        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .search-results {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1001;
            animation: zoomIn 0.1s ease-in-out;
        }

        @keyframes zoomIn {
            from {
                transform: scale(0.9);
                opacity: 0;
            }

            to {
                transform: scale(1);
                opacity: 1;
            }
        }

        .results-content {
            max-width: 500px;
            padding: 20px;
            background-color: rgb(255, 255, 255);
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        .results-content ul {
            padding: 0;
        }

        .results-content ul li {
            list-style: none;
            margin-bottom: 10px;
        }

        .scroll-to-top {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: blue;
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: background 0.4s;
            opacity: 0;
            visibility: hidden;
            z-index: 999;
        }

        .scroll-to-top.show {
            opacity: 1;
            visibility: visible;
        }

        .logo-large {
            width: 130px;
            height: 150px;
            border-radius: 0px;
            object-fit: cover;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .navbar-spaced {
            padding: 1rem 3rem;
        }

        .fixed-header {
            position: fixed;
            top: 64px;
            width: 100%;
            background-color: #f9f9f9;
            z-index: 40;
            padding: 1rem;
            text-align: center;
        }

        /* Estilos para la galería */
        .gallery-section {
            padding: 4rem 2rem;
            background-color: #f0f8ff;
            /* Azul claro para hacerlo más atractivo */
            margin-bottom: 2rem;
            animation: slideInUp 0.5s ease-in-out;
            border-radius: 10px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
        }

        .gallery-image {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 10px;
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
        }

        .gallery-image:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
        }

        /* Lightbox styles */
        .lightbox {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.9);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            animation: zoomIn 0.3s ease-in-out;
        }

        .lightbox img {
            max-width: 90%;
            max-height: 90%;
            object-fit: contain;
        }

        .lightbox-caption {
            color: rgb(255, 255, 255);
            text-align: center;
            margin-top: 10px;
        }
    </style>
</head>

<body class="bg-gray-50">
    <!-- Scroll to Top Button -->
    <button class="scroll-to-top" onclick="window.scrollTo({top: 0, behavior: 'smooth'})"
        aria-label="Ir arriba">↑</button>

    <!-- Barra de navegación -->
    <nav
        class="bg-green-900 bg-opacity-95 backdrop-blur-sm text-white fixed top-0 w-full z-50 flex justify-between items-center navbar-spaced transition-all duration-300">
        <ul class="flex space-x-8">
            <li><a href="inicio.html" class="hover:text-yellow-400 font-semibold transition duration-200">Inicio</a>
            </li>
            <li><a href="quienes-somos.html" class="hover:text-yellow-400 font-semibold transition duration-200">Quiénes
                    Somos</a></li>
            <li><a href="sala-informativa.html" class="hover:text-yellow-400 font-semibold transition duration-200">Sala
                    Informativa</a>
            </li>
            <li><a href="galeria.html" class="hover:text-yellow-400 font-semibold transition duration-200">Galeria</a>
            </li>
            <li><a href="enlaces-interes.html"
                    class="hover:text-yellow-400 font-semibold transition duration-200">Enlaces de Interes</a></li>

            <li><a href="contactos.html"
                    class="hover:text-yellow-400 font-semibold transition duration-200">contactanos</a>
            </li>
        </ul>
    </nav>

    <!-- Sección fija para el logo (sin cambios) -->
    <div
        class="bg-white -800 bg-opacity-95 backdrop-blur-sm fixed-header text-white  flex flex-row  items-center justify-center gap-8">
        <img src="img/logo_fehcafor.1.png" alt="Logo Fehcafor" class="logo-large w-50 h-auto">
        <div>
            <h1 class="text-3xl font-bold text-green-700 mb-2">FEHCAFOR</h1>
            <p class="text-xl text-green-700"><b>FEDERACIÓN HONDUREÑA DE COOPERATIVAS AGROFORESTALES</b></p>
        </div>
    </div> <br><br><br><br><br><br><br>

    <!-- Introducción a la galería -->
    <section class="py-16 bg-gradient-to-r from-green-100 to-green-200 text-center animate-fadeIn">
        <h2 class="text-4xl font-bold text-green-800 mb-4">¡Descubre Nuestra Galería de Momentos Increíbles!</h2>
        <p class="text-lg text-gray-700 max-w-2xl mx-auto">Explora imágenes organizadas por secciones y años. Selecciona
            las fotos de Capacitación, Asamblea, Proyectos y Eventos para 2024 o 2025, y vive la experiencia interactiva
            con solo un clic.</p>
        <div class="mt-8 flex justify-center gap-4">
            <a href="#capacitacion"
                class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700">Capacitación</a>
            <a href="#asamblea" class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700">Asamblea</a>
            <a href="#proyectos" class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700">Proyectos</a>
            <a href="#eventos" class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700">Eventos</a>
            <a href="#aserradero" class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700">Aserradero</a>
        </div>
    </section>

    <!-- Secciones de Galería -->
    <section id="galeria" class="py-12">
        <!-- Sección: Capacitación -->
        <section id="capacitacion" class="gallery-section">
            <h3 class="text-3xl font-bold text-center text-green-800 mb-6">Capacitaciones 2025</h3>
            <div class="grid grid-cols-2 gap-4">
                <!-- Casilla 2024 -->
                <div class="bg-white p-4 rounded-lg shadow-md">

                    <div class="gallery-grid">
                        <img src="img/capacitacion 9 2025.jpg" alt="Capacitacion de Genero" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/capa 1.jpg" alt="Capacitacion de Genero" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                    </div>
                </div>
                <!-- Casilla 2025 -->
                <div class="bg-white p-4 rounded-lg shadow-md">

                    <div class="gallery-grid">
                        <img src="img/capaa.jpg" alt="Capacitacion de Genero" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/capacitacion juventud 2025.jpg" alt="Capacitacion de Juventud"
                            class="gallery-image" onclick="openLightbox(this.src, this.alt)">
                    </div>
                </div>
            </div>
        </section>

        <!-- Sección: Asamblea -->
        <section id="asamblea" class="gallery-section">
            <h3 class="text-3xl font-bold text-center text-green-800 mb-6">Asamblea</h3>
            <div class="grid grid-cols-2 gap-4">
                <!-- Casilla 2024 -->
                <div class="bg-white p-4 rounded-lg shadow-md">
                    <h4 style="text-align: center;" class="text-2xl font-bold text-green-600 mb-4">2024</h4>
                    <div class="gallery-grid">
                        <img src="img/asambl 2024.jpeg" alt="Asamblea 2024" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/asamblea - 2024.jpeg" alt="Asamblea 2024" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/asamblea - 2024.jpeg" alt="Asamblea 2024" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/asamblea. 2024.jpeg" alt="Asamblea 2024" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                    </div>
                </div>
                <!-- Casilla 2025 -->
                <div class="bg-white p-4 rounded-lg shadow-md">
                    <h4 style="text-align: center;" class="text-2xl font-bold text-green-600 mb-4">2025</h4>
                    <div class="gallery-grid">
                        <img src="img/asam 2025.jpg" alt="Asamblea 2025" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/asamblea 1 2025.jpg" alt="Asamblea 2025" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/asamblea 2025..jpg" alt="Asamblea 2025" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/asamblea 2025.jpg" alt="Asamblea 2025" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                    </div>
                </div>
            </div>
        </section>

        <!-- Sección: Proyectos -->
        <section id="proyectos" class="gallery-section">
            <h3 class="text-3xl font-bold text-center text-green-800 mb-6">Proyectos 2025</h3>
            <div class="grid grid-cols-2 gap-4">
                <!-- Casilla 2024 -->
                <div class="bg-white p-4 rounded-lg shadow-md">

                    <div class="gallery-grid">
                        <img src="img/proyecto 2025.jpg"
                            alt="𝘗𝘳𝘰𝘺𝘦𝘤𝘵𝘰 𝘔𝘢𝘯𝘦𝘫𝘰 𝘊𝘰𝘮𝘶𝘯𝘪𝘵𝘢𝘳𝘪𝘰 𝘚𝘰𝘴𝘵𝘦𝘯𝘪𝘣𝘭𝘦 𝘥𝘦 𝘉𝘰𝘴𝘲𝘶𝘦𝘴 𝘥𝘦 𝘗𝘪𝘯𝘰 𝘺 𝘌𝘹𝘵𝘳𝘢𝘤𝘤𝘪𝘰́𝘯 𝘥𝘦 𝘙𝘦𝘴𝘪𝘯𝘢 𝘥𝘦 𝘱𝘪𝘯𝘰 𝘐𝘈𝘍."
                            class="gallery-image" onclick="openLightbox(this.src, this.alt)">
                        <img src="img/proyecto 3 2025.jpg"
                            alt="𝘗𝘳𝘰𝘺𝘦𝘤𝘵𝘰 𝘔𝘢𝘯𝘦𝘫𝘰 𝘊𝘰𝘮𝘶𝘯𝘪𝘵𝘢𝘳𝘪𝘰 𝘚𝘰𝘴𝘵𝘦𝘯𝘪𝘣𝘭𝘦 𝘥𝘦 𝘉𝘰𝘴𝘲𝘶𝘦𝘴 𝘥𝘦 𝘗𝘪𝘯𝘰 𝘺 𝘌𝘹𝘵𝘳𝘢𝘤𝘤𝘪𝘰́𝘯 𝘥𝘦 𝘙𝘦𝘴𝘪𝘯𝘢 𝘥𝘦 𝘱𝘪𝘯𝘰 𝘐𝘈𝘍."
                            class="gallery-image" onclick="openLightbox(this.src, this.alt)">
                        <img src="img/proyecto 2025 3.jpg"
                            alt="𝘗𝘳𝘰𝘺𝘦𝘤𝘵𝘰 𝘔𝘢𝘯𝘦𝘫𝘰 𝘊𝘰𝘮𝘶𝘯𝘪𝘵𝘢𝘳𝘪𝘰 𝘚𝘰𝘴𝘵𝘦𝘯𝘪𝘣𝘭𝘦 𝘥𝘦 𝘉𝘰𝘴𝘲𝘶𝘦𝘴 𝘥𝘦 𝘗𝘪𝘯𝘰 𝘺 𝘌𝘹𝘵𝘳𝘢𝘤𝘤𝘪𝘰́𝘯 𝘥𝘦 𝘙𝘦𝘴𝘪𝘯𝘢 𝘥𝘦 𝘱𝘪𝘯𝘰 𝘐𝘈𝘍."
                            class="gallery-image" onclick="openLightbox(this.src, this.alt)">
                        <img src="img/proyecto 5 2025.jpg"
                            alt="𝘗𝘳𝘰𝘺𝘦𝘤𝘵𝘰 𝘔𝘢𝘯𝘦𝘫𝘰 𝘊𝘰𝘮𝘶𝘯𝘪𝘵𝘢𝘳𝘪𝘰 𝘚𝘰𝘴𝘵𝘦𝘯𝘪𝘣𝘭𝘦 𝘥𝘦 𝘉𝘰𝘴𝘲𝘶𝘦𝘴 𝘥𝘦 𝘗𝘪𝘯𝘰 𝘺 𝘌𝘹𝘵𝘳𝘢𝘤𝘤𝘪𝘰́𝘯 𝘥𝘦 𝘙𝘦𝘴𝘪𝘯𝘢 𝘥𝘦 𝘱𝘪𝘯𝘰 𝘐𝘈𝘍."
                            class="gallery-image" onclick="openLightbox(this.src, this.alt)">
                    </div>
                </div>
                <!-- Casilla 2025 -->
                <div class="bg-white p-4 rounded-lg shadow-md">

                    <div class="gallery-grid">
                        <img src="img/IAF proyecto.jpeg"
                            alt="𝘗𝘳𝘰𝘺𝘦𝘤𝘵𝘰 𝘔𝘢𝘯𝘦𝘫𝘰 𝘊𝘰𝘮𝘶𝘯𝘪𝘵𝘢𝘳𝘪𝘰 𝘚𝘰𝘴𝘵𝘦𝘯𝘪𝘣𝘭𝘦 𝘥𝘦 𝘉𝘰𝘴𝘲𝘶𝘦𝘴 𝘥𝘦 𝘗𝘪𝘯𝘰 𝘺 𝘌𝘹𝘵𝘳𝘢𝘤𝘤𝘪𝘰́𝘯 𝘥𝘦 𝘙𝘦𝘴𝘪𝘯𝘢 𝘥𝘦 𝘱𝘪𝘯𝘰 𝘐𝘈𝘍."
                            class="gallery-image" onclick="openLightbox(this.src, this.alt)">
                        <img src="img/pro 2025.jpg"
                            alt="𝘗𝘳𝘰𝘺𝘦𝘤𝘵𝘰 𝘔𝘢𝘯𝘦𝘫𝘰 𝘊𝘰𝘮𝘶𝘯𝘪𝘵𝘢𝘳𝘪𝘰 𝘚𝘰𝘴𝘵𝘦𝘯𝘪𝘣𝘭𝘦 𝘥𝘦 𝘉𝘰𝘴𝘲𝘶𝘦𝘴 𝘥𝘦 𝘗𝘪𝘯𝘰 𝘺 𝘌𝘹𝘵𝘳𝘢𝘤𝘤𝘪𝘰́𝘯 𝘥𝘦 𝘙𝘦𝘴𝘪𝘯𝘢 𝘥𝘦 𝘱𝘪𝘯𝘰 𝘐𝘈𝘍."
                            class="gallery-image" onclick="openLightbox(this.src, this.alt)">
                        <img src="img/pro IAF 2.jpeg"
                            alt="𝘗𝘳𝘰𝘺𝘦𝘤𝘵𝘰 𝘔𝘢𝘯𝘦𝘫𝘰 𝘊𝘰𝘮𝘶𝘯𝘪𝘵𝘢𝘳𝘪𝘰 𝘚𝘰𝘴𝘵𝘦𝘯𝘪𝘣𝘭𝘦 𝘥𝘦 𝘉𝘰𝘴𝘲𝘶𝘦𝘴 𝘥𝘦 𝘗𝘪𝘯𝘰 𝘺 𝘌𝘹𝘵𝘳𝘢𝘤𝘤𝘪𝘰́𝘯 𝘥𝘦 𝘙𝘦𝘴𝘪𝘯𝘢 𝘥𝘦 𝘱𝘪𝘯𝘰 𝘐𝘈𝘍."
                            class="gallery-image" onclick="openLightbox(this.src, this.alt)">
                        <img src="img/PRO IAF 3.jpeg"
                            alt="𝘗𝘳𝘰𝘺𝘦𝘤𝘵𝘰 𝘔𝘢𝘯𝘦𝘫𝘰 𝘊𝘰𝘮𝘶𝘯𝘪𝘵𝘢𝘳𝘪𝘰 𝘚𝘰𝘴𝘵𝘦𝘯𝘪𝘣𝘭𝘦 𝘥𝘦 𝘉𝘰𝘴𝘲𝘶𝘦𝘴 𝘥𝘦 𝘗𝘪𝘯𝘰 𝘺 𝘌𝘹𝘵𝘳𝘢𝘤𝘤𝘪𝘰́𝘯 𝘥𝘦 𝘙𝘦𝘴𝘪𝘯𝘢 𝘥𝘦 𝘱𝘪𝘯𝘰 𝘐𝘈𝘍."
                            class="gallery-image" onclick="openLightbox(this.src, this.alt)">
                    </div>
                </div>
            </div>
        </section>

        <!-- Sección: Eventos -->
        <section id="eventos" class="gallery-section">
            <h3 class="text-3xl font-bold text-center text-green-800 mb-6">Eventos</h3>
            <div class="grid grid-cols-2 gap-4">
                <!-- Casilla 2024 -->
                <div class="bg-white p-4 rounded-lg shadow-md">
                    <h4 style="text-align: center;" class="text-2xl font-bold text-green-600 mb-4">2024</h4>
                    <div class="gallery-grid">
                        <img src="img/ani 50 event.jpg" alt="Aniversario 50" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/ani 50.jpg" alt="Aniversario 50" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/50. ani.jpg" alt="Aniversario 50" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/50 ani.jpg" alt="Aniversario 50" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                    </div>
                </div>
                <!-- Casilla 2025 -->
                <div style="text-align: center;" class="bg-white p-4 rounded-lg shadow-md">
                    <h4 class="text-2xl font-bold text-green-600 mb-4">2025</h4>
                    <div class="gallery-grid">
                        <img src="img/event 2025 51 aniver.jpg" alt="Aniversario 51" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/evento 51 aniversa.jpg" alt="Aniversario 51" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/evento 2025 51 aniversario.jpg" alt="Aniversario 51" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/evento aniversario 51.jpg" alt="Aniversario 51" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                    </div>
                </div>
            </div>
        </section>

        <!-- Sección: aserradero -->
        <section id="aserradero" class="gallery-section">
            <h3 class="text-3xl font-bold text-center text-green-800 mb-6">Aserradero</h3>
            <div class="grid grid-cols-2 gap-4">
                <!-- Casilla 2024 -->
                <div class="bg-white p-4 rounded-lg shadow-md">

                    <div class="gallery-grid">
                        <img src="img/aserradero 1.jpg" alt="Aserradero" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/aserradero...jpg" alt="Aserradero" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/aserradero..jpg" alt="Aserradero" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/aserradero.....jpg" alt="Aserradero" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                    </div>
                </div>
                <!-- Casilla 2025 -->
                <div class="bg-white p-4 rounded-lg shadow-md">
                    <div class="gallery-grid">
                        <img src="img/aserradero....jpg" alt="Aserradero" class="gallery-image"
                            onclick="openLightbox(this.src, this.alt)">
                        <img src="img/aserra.jpeg" alt="Aserradero" class="gallery-image" onclick="openLightbox(this.src, this.alt)">
                        <video controls>
                            <source src="img/aserradero .2.mp4" type="video/mp4">
                        </video>
                         <img src="img/ase.jpeg" alt="Aserradero" class="gallery-image" onclick="openLightbox(this.src, this.alt)">
                       


                    </div>
                </div>
            </div>
        </section>

    </section>

    <!-- Lightbox -->
    <div id="lightbox" class="lightbox">
        <span onclick="closeLightbox()" class="absolute top-5 right-5 text-white text-2xl cursor-pointer">&times;</span>
        <img id="lightbox-img" src="" alt="">
        <p id="lightbox-caption" class="lightbox-caption"></p>
    </div>

    <!-- Pie de página -->
    <footer class="bg-green-900 text-white py-6 text-center">
        <p>&copy; 2025 FEHCAFOR.</p>
    </footer>

    <script>
        function openLightbox(src, alt) {
            const lightbox = document.getElementById('lightbox');
            const lightboxImg = document.getElementById('lightbox-img');
            const lightboxCaption = document.getElementById('lightbox-caption');
            lightboxImg.src = src;
            lightboxCaption.textContent = alt;
            lightbox.style.display = 'flex';
        }

        function closeLightbox() {
            document.getElementById('lightbox').style.display = 'none';
        }

    </script>
</body>

</html>

<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FEHCAFOR - Enlaces de interes</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        /* CSS adicional */
        body {
            font-family: 'Poppins', sans-serif;
            scroll-behavior: smooth;
        }

        .hero-slider {
            position: relative;
            height: 90vh;
            overflow: hidden;
            animation: fadeIn 4s ease-in-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .slides {
            position: relative;
            width: 100%;
            height: 100%;
        }

        .slide {
            position: absolute;
            width: 100%;
            height: 100%;
            object-fit: cover;
            opacity: 0;
            transition: opacity 4s ease-in-out;
        }

        .slide.active {
            opacity: 1;
        }

        .program {
            animation: slideInUp 0.4s ease-in-out;
        }
        

        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .search-results {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1001;
            animation: zoomIn 0.1s ease-in-out;
        }

        @keyframes zoomIn {
            from {
                transform: scale(0.9);
                opacity: 0;
            }

            to {
                transform: scale(1);
                opacity: 1;
            }
        }

        .results-content {
            max-width: 500px;
            padding: 20px;
            background-color: white;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        .results-content ul {
            padding: 0;
        }

        .results-content ul li {
            list-style: none;
            margin-bottom: 10px;
        }

        .scroll-to-top {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: blue;
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: background 0.4s;
            opacity: 0;
            visibility: hidden;
            z-index: 999;
        }

        .scroll-to-top.show {
            opacity: 1;
            visibility: visible;
        }

        .logo-large {
            width: 130px;
            height: 150px;
            border-radius: 0px;
            object-fit: cover;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .navbar-spaced {
            padding: 1rem 3rem;
        }
      /* Nueva clase para el contenedor fijo del logo */
        .fixed-header {
            position: fixed;
            top: 64px; /* Ajusta según la altura de la barra de navegación (aprox. 64px) */
            width: 100%;
            background-color: #f9f9f9; /* Color de fondo claro para que se vea bien */
            z-index: 40; /* Menor que la barra de navegación */
            padding: 1rem;
            text-align: center;
        }
        
    </style>
</head>

<body class="bg-gray-50">
    <!-- Scroll to Top Button -->
    <button class="scroll-to-top" onclick="window.scrollTo({top: 0, behavior: 'smooth'})"
        aria-label="Ir arriba">↑</button>

    <!-- Barra de navegación -->
    <nav
        class="bg-green-900 bg-opacity-95 backdrop-blur-sm text-white fixed top-0 w-full z-50 flex justify-between items-center navbar-spaced transition-all duration-300">
        <ul class="flex space-x-8">
            <li><a href="inicio.html" class="hover:text-yellow-400 font-semibold transition duration-200">Inicio</a>
            </li>
            <li><a href="quienes-somos.html" class="hover:text-yellow-400 font-semibold transition duration-200">Quiénes
                    Somos</a></li>
            <li><a href="sala-informativa.html" class="hover:text-yellow-400 font-semibold transition duration-200">Sala
                    Informativa</a>
            </li>
            <li><a href="galeria.html" class="hover:text-yellow-400 font-semibold transition duration-200">Galeria</a>
            </li>
            <li><a href="enlaces-interes.html"
                    class="hover:text-yellow-400 font-semibold transition duration-200">Enlaces de Interes</a></li>

            <li><a href="contactos.html"
                    class="hover:text-yellow-400 font-semibold transition duration-200">contactanos</a>
            </li>
        </ul>
    </nav>

    <!-- Sección fija para el logo y texto debajo de la barra de navegación -->
    <div class="bg-white -800 bg-opacity-95 backdrop-blur-sm fixed-header text-white  flex flex-row  items-center justify-center gap-8">
        <img src="img/logo_fehcafor.1.png" alt="Logo Fehcafor" class="logo-large w-50 h-auto"><!-- Reduje el tamaño para que quepa mejor -->
        <div>
            <h1 class="text-3xl font-bold text-green-700 mb-2">FEHCAFOR</h1>
            <p class="text-xl text-green-700"><b>FEDERACIÓN HONDUREÑA DE COOPERATIVAS AGROFORESTALES</b></p>
        </div>
    </div> <br><br><br><br><br><br><br>

 <!-- Sección de enlaces de interés -->
    <section id="enlaces-interes" class="py-20 bg-gray-100">
        <div class="container mx-auto px-6">
            <h2 class="text-4xl font-bold text-center text-black-900 mb-10">Enlaces de interes</h2>
            <div class="flex flex-row justify-center space-x-4 flex-wrap">
                <a href="https://www.facebook.com/institutodeconservacion.icf/?locale=es_LA" class="link-card flex flex-col items-center p-6 bg-white rounded-xl shadow-md hover:bg-blue-100">
                    <svg xmlns="http://www.w3.org/2000/svg" width="50" height="50" viewBox="0 0 24 24" fill="none" stroke="#1033e5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path stroke="none" d="M0 0h24v24H0z" fill="none" />
                        <path d="M7 10v4h3v7h4v-7h3l1 -4h-4v-2a1 1 0 0 1 1 -1h3v-4h-3a5 5 0 0 0 -5 5v2h-3" />
                    </svg>
                    <img src="img/ICF.png" alt="ICF" width="200" height="300" class="mt-2" />
                </a>
                <a href="https://www.facebook.com/UnionEuropeaEnHonduras" class="link-card flex flex-col items-center p-6 bg-white rounded-xl shadow-md hover:bg-blue-100">
                    <svg xmlns="http://www.w3.org/2000/svg" width="50" height="50" viewBox="0 0 24 24" fill="none" stroke="#1033e5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path stroke="none" d="M0 0h24v24H0z" fill="none" />
                        <path d="M7 10v4h3v7h4v-7h3l1 -4h-4v-2a1 1 0 0 1 1 -1h3v-4h-3a5 5 0 0 0 -5 5v2h-3" />
                    </svg>
                    <img src="img/Europeaid.jpg" alt="Unión Europea" width="200" height="300" class="mt-2" />
                </a>
                <a href="https://www.facebook.com/UNFAO" class="link-card flex flex-col items-center p-6 bg-white rounded-xl shadow-md hover:bg-blue-100">
                    <svg xmlns="http://www.w3.org/2000/svg" width="50" height="50" viewBox="0 0 24 24" fill="none" stroke="#1033e5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path stroke="none" d="M0 0h24v24H0z" fill="none" />
                        <path d="M7 10v4h3v7h4v-7h3l1 -4h-4v-2a1 1 0 0 1 1 -1h3v-4h-3a5 5 0 0 0 -5 5v2h-3" />
                    </svg>
                    <img src="img/proyecto faoue.jpg" alt="FAO" width="200" height="300" class="mt-2" />
                </a>
                <a href="https://www.facebook.com/onumujereshn" class="link-card flex flex-col items-center p-6 bg-white rounded-xl shadow-md hover:bg-blue-100">
                    <svg xmlns="http://www.w3.org/2000/svg" width="50" height="50" viewBox="0 0 24 24" fill="none" stroke="#1033e5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path stroke="none" d="M0 0h24v24H0z" fill="none" />
                        <path d="M7 10v4h3v7h4v-7h3l1 -4h-4v-2a1 1 0 0 1 1 -1h3v-4h-3a5 5 0 0 0 -5 5v2h-3" />
                    </svg>
                    <img src="img/Onu mujer.png" alt="ONU Mujeres" width="200" height="300" class="mt-2" />
                </a>
            </div>
        </div>
    </section>

    <!-- Pie de página -->
    <footer class="bg-green-900 text-white py-6 text-center">
        <p>&copy; 2025 FEHCAFOR.</p>
    </footer>

    <script>
        // Scripts... (mantenidos igual)
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FEHCAFOR - Contactos</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        /* CSS adicional */
        body {
            font-family: 'Poppins', sans-serif;
            scroll-behavior: smooth;
        }

        .hero-slider {
            position: relative;
            height: 90vh;
            overflow: hidden;
            animation: fadeIn 4s ease-in-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .slides {
            position: relative;
            width: 100%;
            height: 100%;
        }

        .slide {
            position: absolute;
            width: 100%;
            height: 100%;
            object-fit: cover;
            opacity: 0;
            transition: opacity 4s ease-in-out;
        }

        .slide.active {
            opacity: 1;
        }

        .program {
            animation: slideInUp 0.4s ease-in-out;
        }


        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .search-results {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1001;
            animation: zoomIn 0.1s ease-in-out;
        }

        @keyframes zoomIn {
            from {
                transform: scale(0.9);
                opacity: 0;
            }

            to {
                transform: scale(1);
                opacity: 1;
            }
        }

        .results-content {
            max-width: 500px;
            padding: 20px;
            background-color: white;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        .results-content ul {
            padding: 0;
        }

        .results-content ul li {
            list-style: none;
            margin-bottom: 10px;
        }

        .scroll-to-top {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: blue;
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: background 0.4s;
            opacity: 0;
            visibility: hidden;
            z-index: 999;
        }

        .scroll-to-top.show {
            opacity: 1;
            visibility: visible;
        }

        .logo-large {
            width: 130px;
            height: 150px;
            border-radius: 0px;
            object-fit: cover;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .navbar-spaced {
            padding: 1rem 3rem;
        }

        /* Nueva clase para el contenedor fijo del logo */
        .fixed-header {
            position: fixed;
            top: 64px;
            /* Ajusta según la altura de la barra de navegación (aprox. 64px) */
            width: 100%;
            background-color: #f9f9f9;
            /* Color de fondo claro para que se vea bien */
            z-index: 40;
            /* Menor que la barra de navegación */
            padding: 1rem;
            text-align: center;
        }

        /* Estilos para la sección de contacto */
        .contact-form {
            max-width: 600px;
            margin: 0 auto;
            padding: 2rem;
            background-color: #f9f9f9;
            border-radius: 1rem;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        .contact-form input,
        .contact-form textarea {
            width: 100%;
            padding: 0.75rem;
            margin-bottom: 1rem;
            border: 1px solid #ccc;
            border-radius: 0.5rem;
        }

        /* ... (el resto de tu CSS permanece igual) ... */

        /* Estilos para la sección de contacto */
        .contact-form {
            max-width: 600px;
            margin: 0 auto;
            padding: 2rem;
            background-color: #f9f9f9;
            border-radius: 1rem;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        .contact-form input,
        .contact-form textarea {
            width: 100%;
            padding: 0.75rem;
            margin-bottom: 1rem;
            border: 1px solid #ccc;
            border-radius: 0.5rem;
        }

        .contact-form button {
            background-color: #10B981;
            /* Corregido */
            color: white;
            padding: 0.75rem 1.5rem;
            border-radius: 0.5rem;
            transition: background-color 0.3s;
        }

        .contact-form button:hover {
            background-color: #047857;
            /* Corregido */
        }
    </style>


    </style>
</head>

<body class="bg-gray-50">
    <!-- Scroll to Top Button -->
    <button class="scroll-to-top" onclick="window.scrollTo({top: 0, behavior: 'smooth'})"
        aria-label="Ir arriba">↑</button>

    <!-- Barra de navegación -->
    <nav
        class="bg-green-900 bg-opacity-95 backdrop-blur-sm text-white fixed top-0 w-full z-50 flex justify-between items-center navbar-spaced transition-all duration-300">
        <ul class="flex space-x-8">
            <li><a href="inicio.html" class="hover:text-yellow-400 font-semibold transition duration-200">Inicio</a>
            </li>
            <li><a href="quienes-somos.html" class="hover:text-yellow-400 font-semibold transition duration-200">Quiénes
                    Somos</a></li>
            <li><a href="sala-informativa.html" class="hover:text-yellow-400 font-semibold transition duration-200">Sala
                    Informativa</a>
            </li>
            <li><a href="galeria.html" class="hover:text-yellow-400 font-semibold transition duration-200">Galeria</a>
            </li>
            <li><a href="enlaces-interes.html"
                    class="hover:text-yellow-400 font-semibold transition duration-200">Enlaces de Interes</a></li>

            <li><a href="contactos.html"
                    class="hover:text-yellow-400 font-semibold transition duration-200">contactanos</a>
            </li>
        </ul>
    </nav>

    <!-- Sección fija para el logo y texto debajo de la barra de navegación -->
    <div
        class="bg-white -800 bg-opacity-95 backdrop-blur-sm fixed-header text-white  flex flex-row  items-center justify-center gap-8">
        <img src="img/logo_fehcafor.1.png" alt="Logo Fehcafor"
            class="logo-large w-50 h-auto"><!-- Reduje el tamaño para que quepa mejor -->
        <div>
            <h1 class="text-3xl font-bold text-green-700 mb-2">FEHCAFOR</h1>
            <p class="text-xl text-green-700"><b>FEDERACIÓN HONDUREÑA DE COOPERATIVAS AGROFORESTALES</b></p>
        </div>
    </div> <br><br><br><br><br><br><br>

    <!-- Sección de Contacto -->
    <section id="contacto" class="py-16 bg-gray-100">
        <div class="container mx-auto px-6">
            <h2 class="text-3xl font-bold text-center mb-6">Contacto con FEHCAFOR</h2>
            <div class="contact-form">
                <p class="text-gray-700 mb-4">Envíanos un mensaje o contacta directamente para obtener más información
                    sobre nuestras actividades.</p>
                <form action="https://formspree.io/your-email@example.com" method="POST">
                    <!-- Reemplaza con tu endpoint de formulario -->
                    <input type="text" name="name" placeholder="Tu nombre" required class="mb-4">
                    <input type="email" name="email" placeholder="Tu correo electrónico" required class="mb-4">
                    <textarea name="message" placeholder="Tu mensaje" rows="4" required class="mb-4"></textarea>
                    <button type="submit">Enviar Mensaje</button>
                </form> <br>
                <div class="section-bg text-center">
                    <p><strong>Correo:</strong> <a href="mailto:fehcafor1974@gmail.com"
                            class="text-blue-600 hover:underline">fehcafor1974@gmail.com</a></p>
                    <p><strong>Teléfono:</strong> <a href="tel:+50422270059" class="text-blue-600 hover:underline">+504
                            2227-0059</a></p>
                    <p><strong>Dirección:</strong> <a
                            href="https://www.google.com/maps/search/Colonia+Mayangle+2da+entrada%2C+casa+1659%2C+una+cuadra+Oeste+de+Cruz+Roja+Hondureña%2C+Comayagüela%2C+Honduras"
                            target="_blank" class="text-blue-600 hover:underline">Col- Mayangle. esquina opuesta a Cruz
                            Roja Hondureña, contiguo a Save The Childrens, Casa No. 2211.</a></p>
                    <p class="mt-4">O síguenos en redes para actualizaciones en tiempo real:</p>
                    <a href="https://www.facebook.com/FEHCAFOR" target="_blank"
                        class="text-blue-600 hover:underline">Página de Facebook de FEHCAFOR</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Pie de página -->
    <footer class="bg-green-900 text-white py-6 text-center">
        <p>&copy; 2025 FEHCAFOR.</p>
    </footer>

    <script>
        // Script para scroll suave
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });
    </script>
</body>

</html>

