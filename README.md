<!DOCTYPE html>
<html lang="es" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Santiago & Jenifer - Un Viaje Inesperado | Boda en La Comarca</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700;900&family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400&family=MedievalSharp&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        shire: {
                            dark: '#1b120c',
                            wood: '#2b1e16',
                            woodlight: '#3d2b1f',
                            parchment: '#f4ebd9',
                            parchmentDark: '#e5d3b3',
                            parchmentBorder: '#c4aa78',
                            green: '#1e3323',
                            greenLight: '#2d4a32',
                            gold: '#c5a059',
                            goldBright: '#e5be6b',
                            ruby: '#7a1c1c'
                        }
                    },
                    fontFamily: {
                        heading: ['Cinzel', 'serif'],
                        fantasy: ['MedievalSharp', 'cursive'],
                        body: ['Cormorant Garamond', 'serif']
                    }
                }
            }
        }
    </script>

    <style>
        /* Custom Parchment Background Texture Effect */
        .bg-parchment-texture {
            background-color: #f4ebd9;
            background-image: 
                radial-gradient(circle at 50% 50%, rgba(244, 235, 217, 0.9), rgba(229, 211, 179, 0.95)),
                url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.8' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)' opacity='0.08'/%3E%3C/svg%3E");
        }

        .bg-parchment-card {
            background-color: #f8f3e6;
            box-shadow: inset 0 0 30px rgba(139, 94, 60, 0.15), 0 10px 25px rgba(0,0,0,0.3);
            border: 2px solid #c4aa78;
        }

        .wood-border {
            border: 8px solid #2b1e16;
            outline: 2px solid #c5a059;
            outline-offset: -5px;
        }

        /* Gold gradient text */
        .text-gold-gradient {
            background: linear-gradient(135deg, #e5be6b 0%, #c5a059 50%, #997433 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* Glowing Ring effect */
        .ring-glow {
            box-shadow: 0 0 20px rgba(229, 190, 107, 0.6), inset 0 0 15px rgba(229, 190, 107, 0.4);
        }

        /* Leaf float animation */
        @keyframes floatLeaf {
            0% { transform: translateY(-10px) rotate(0deg) translateX(0); opacity: 0; }
            20% { opacity: 0.8; }
            100% { transform: translateY(100vh) rotate(360deg) translateX(50px); opacity: 0; }
        }

        .leaf-particle {
            position: fixed;
            pointer-events: none;
            z-index: 40;
            animation: floatLeaf 12s linear infinite;
        }

        /* Wax seal button effect */
        .wax-seal {
            background: radial-gradient(circle, #a82424 0%, #7a1c1c 70%, #4a0f0f 100%);
            box-shadow: 0 4px 10px rgba(0,0,0,0.5), inset 0 2px 3px rgba(255,255,255,0.3);
        }
        
        .wax-seal:hover {
            transform: scale(1.05);
            box-shadow: 0 6px 15px rgba(0,0,0,0.6), inset 0 2px 5px rgba(255,255,255,0.4);
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 10px;
        }
        ::-webkit-scrollbar-track {
            background: #1b120c;
        }
        ::-webkit-scrollbar-thumb {
            background: #c5a059;
            border-radius: 5px;
            border: 2px solid #1b120c;
        }

        /* Winding Path SVG Line Animation */
        .path-line {
            stroke-dasharray: 8;
            animation: dash 30s linear infinite;
        }
        @keyframes dash {
            to {
                stroke-dashoffset: -1000;
            }
        }
    </style>
</head>
<body class="bg-shire-dark text-shire-wood font-body antialiased overflow-x-hidden selection:bg-shire-gold selection:text-shire-dark">

    <div id="leaves-container"></div>

    <!-- Elemento Audio con la URL de la canción de fondo -->
    <audio id="wedding-music" loop>
        <!-- Reemplaza la URL entre comillas con el enlace directo MP3 de tu canción favorita -->
        <source id="audio-source" src="https://mp3tourl.com/audio/1791366443143-7129d727-ef02-4a6a-8a9a-4df7a5648d80.m4a" type="audio/mpeg">
        Tu navegador no soporta el reproductor de audio.
    </audio>

       <div class="fixed top-4 right-4 z-50">
        <button id="sound-toggle" onclick="toggleAudio()" class="bg-shire-wood/90 text-shire-gold border border-shire-gold px-4 py-2 rounded-full shadow-lg hover:bg-shire-woodlight transition flex items-center space-x-2 backdrop-blur-sm">
            <i id="sound-icon" class="fas fa-volume-mute text-lg"></i>
            <span id="sound-text" class="font-fantasy text-xs hidden sm:inline">Música de La Comarca</span>
        </button>
    </div>

    <!-- HEADER ADAPTADO CON OBJECT-FIT: COVER -->
<header class="relative w-full h-screen flex flex-col items-center justify-center text-center overflow-hidden">

        <img src="https://lh3.googleusercontent.com/d/1GQFrrvmTYZVgaRx1JsRZX6rTECwt8shb" alt="Santiago y Jenifer" class="absolute inset-0 w-768px h-full object-[center_60%] object-cover sm:object-cover sm:object-[center_10%] sm:w-full z-0">

        <!-- Capa de oscurecimiento (Overlay) para que el texto resalte -->
        <div class="absolute inset-0 bg-shire-dark/25 z-0"></div>

        <!-- Elven Rune / Vignette Border -->
        <div class="absolute inset-0 border-[12px] border-shire-gold/30 pointer-events-none z-10"></div>
        <div class="absolute inset-4 border border-shire-gold/50 pointer-events-none z-10"></div>

        <div class="relative z-20 max-w-4xl mx-auto px-6 space-y-6 transform transition-all duration-1000">

        <div class="inline-block mb-2">

<div class="h-[2vh] sm:h-[5vh]"></div>
            <span class="text-shire-gold text-3xl sm:text-3xl font-fantasy">
                🍃 ᚨᛗᛁᚷᛟ ᛗᛁᛟ 🍃 
            </span>
        </div>

<div class="h-[30vh] sm:h-[38vh]"></div>
        <h1 class="font-heading text-4xl sm:text-3xl md:text-4xl lg:text-6xl font-extrabold text-gold-gradient tracking-wide leading-tight drop-shadow-lg">
            Santiago
            <span class="font-fantasy text-shire-parchment text-3xl sm:text-5xl">&</span>
            Jenifer
        </h1>

        <h2 class="font-fantasy text-xl sm:text-2xl text-shire-parchment italic">
            "Un Viaje Inesperado: La Boda"
        </h2>

    </div>

    <div class="relative z-10 max-w-4xl mx-auto">

        <h1 class="font-heading text-4xl sm:text-3xl md:text-4xl lg:text-4xl font-extrabold text-gold-gradient tracking-wide leading-tight drop-shadow-lg">
            <span class="font-fantasy text-shire-parchment text-2xl sm:text-2xl">
                29 DE MAYO DE 2027
            </span>
        </h1>

        <p class="text-shire-parchmentDark text-lg sm:text-xl font-semibold tracking-wider">
            • MOTRIL & SALOBREÑA •
        </p>

        <!-- Cuenta regresiva -->
        <div id="countdown" class="grid grid-cols-4 gap-2 sm:gap-4 max-w-lg mx-auto pt-6">

            <div class="bg-shire-wood/80 border border-shire-gold/60 p-1 rounded-lg backdrop-blur-md">
                <span id="days" class="font-heading text-1xl sm:text-1xl font-bold text-shire-gold block">00</span>
                <span class="font-fantasy text-xs sm:text-sm text-shire-parchment uppercase">Días</span>
            </div>

            <div class="bg-shire-wood/80 border border-shire-gold/60 p-1 rounded-lg backdrop-blur-md">
                <span id="hours" class="font-heading text-1xl sm:text-1xl font-bold text-shire-gold block">00</span>
                <span class="font-fantasy text-xs sm:text-sm text-shire-parchment uppercase">Horas</span>
            </div>

            <div class="bg-shire-wood/80 border border-shire-gold/60 p-1 rounded-lg backdrop-blur-md">
                <span id="minutes" class="font-heading text-1xl sm:text-1xl font-bold text-shire-gold block">00</span>
                <span class="font-fantasy text-xs sm:text-sm text-shire-parchment uppercase">Minutos</span>
            </div>

            <div class="bg-shire-wood/80 border border-shire-gold/60 p-1 rounded-lg backdrop-blur-md">
                <span id="seconds" class="font-heading text-1xl sm:text-1xl font-bold text-shire-gold block">00</span>
                <span class="font-fantasy text-xs sm:text-sm text-shire-parchment uppercase">Segundos</span>
            </div>

        </div>

        <!-- Botón para continuar -->
        <div class="pt-8">
            <a href="#nuestro-camino"
                class="inline-flex flex-col items-center text-shire-gold hover:text-white transition group">
                <span class="font-fantasy text-sm mb-2 group-hover:translate-y-1 transition-transform">
                    Comenzar el Viaje
                </span>
                <i class="fas fa-chevron-down text-2xl animate-bounce"></i>
            </a>
        </div>

    </div>
    </header>

 <section id="nuestro-camino" class="py-20 px-4 sm:px-8 bg-parchment-texture relative">
        <div class="max-w-6xl mx-auto">
            
            <div class="text-center mb-16 space-y-3">
                <p class="font-fantasy text-shire-ruby text-lg">El Mapa del Viajero</p>
                <h2 class="font-heading text-3xl sm:text-5xl font-bold text-shire-wood uppercase tracking-wider">
                    Nuestro Camino por la Tierra Media
                </h2>
                <div class="w-24 h-1 bg-shire-gold mx-auto"></div>
                <p class="text-lg max-w-2xl mx-auto italic text-shire-woodlight">
                    "Un viaje de mil leguas comienza con un solo paso. Haz clic en cada hito del mapa para rememorar nuestros pasajes e historia."
                </p>
            </div>

            <!-- Winding Path Timeline Container -->
            <div class="relative">
                
                <!-- Timeline Stops List -->
                <div class="space-y-16 relative z-10">
                    
                   

                    <!-- Stop 1 (Hobbiton Gallery: 4 photos) -->
                    <div class="flex flex-col md:flex-row items-center gap-8 bg-parchment-card p-6 sm:p-8 rounded-xl border-2 border-shire-parchmentBorder hover:border-shire-gold transition shadow-xl group">
                        <div class="w-full md:w-1/2 grid grid-cols-2 gap-2">
                            <img src="https://lh3.googleusercontent.com/d/1I7xEkVJErLTK1mnZbNeQ2LAXPAzQjHjf" alt="La Comarca 1" class="w-full h-32 object-cover rounded-lg border border-shire-wood cursor-pointer hover:scale-105 transition" onclick="openModal('https://lh3.googleusercontent.com/d/1I7xEkVJErLTK1mnZbNeQ2LAXPAzQjHjf', 'Llegada a La Comarca', 'Las icónicas puertas redondas y el calor de las chimeneas.')">
                            <img src="https://lh3.googleusercontent.com/d/1p1pv6yKxbE7OA2wYtZej-Crwmsk6LpF5" alt="La Comarca 2" class="w-full h-32 object-cover rounded-lg border border-shire-wood cursor-pointer hover:scale-105 transition" onclick="openModal('https://lh3.googleusercontent.com/d/1p1pv6yKxbE7OA2wYtZej-Crwmsk6LpF5', 'Llegada a La Comarca', 'Ataviados con los mejores ropajes comarcales.')">
                            <img src="https://lh3.googleusercontent.com/d/14z-Hz1N6Pq7AjScWc_1UfodeicJhSDY4" alt="La Comarca 3" class="w-full h-32 object-cover rounded-lg border border-shire-wood cursor-pointer hover:scale-105 transition" onclick="openModal('https://lh3.googleusercontent.com/d/14z-Hz1N6Pq7AjScWc_1UfodeicJhSDY4', 'Llegada a La Comarca', 'Preparando los festejos y banquetes.')">
                            <img src="https://lh3.googleusercontent.com/d/1HnGTE7eCrznN8MDxsC8mw5AEff7HEiTd" alt="La Comarca 4" class="w-full h-32 object-cover rounded-lg border border-shire-wood cursor-pointer hover:scale-105 transition" onclick="openModal('https://lh3.googleusercontent.com/d/1HnGTE7eCrznN8MDxsC8mw5AEff7HEiTd', 'Llegada a La Comarca', 'A través del portal redondo donde nace la historia.')">
                        </div>

                        <div class="w-full md:w-1/2 space-y-4">
                            <div class="flex items-center space-x-3">
                                <span class="w-10 h-10 rounded-full bg-shire-gold text-shire-dark font-fantasy font-bold flex items-center justify-center text-xl shadow-md">1</span>
                                <h3 class="font-heading text-2xl font-bold text-shire-wood">El mundo no está en los libros y mapas. ¡Está ahí fuera!</h3>
                            </div>
                            <p class="text-lg text-shire-woodlight leading-relaxed">
                                Nuestra historia comenzó a escribirse en 2022, allá en las tierras de Atenas. Juntos navegamos por decenas de islas griegas, conocimos a gentes venidas de todos los rincones de Europa y sumamos valiosos aliados a nuestra compañía. Al fin, decidimos compartir el mismo hogar... Sí, fue una época inolvidable, repleta de encuentros, de grandes planes y de gyros (¡y pobre de aquel que lo pronuncie "yairo", por la barba de Durin!).
                            </p>
                       
                        </div>
                    </div>


  <div class="relative">
                
                <!-- Timeline Stops List -->
                <div class="space-y-16 relative z-10">
                               

                    <!-- Stop 1 (Hobbiton Gallery: 4 photos) -->
                    <div class="flex flex-col md:flex-row items-center gap-8 bg-parchment-card p-6 sm:p-8 rounded-xl border-2 border-shire-parchmentBorder hover:border-shire-gold transition shadow-xl group">
                        <div class="w-full md:w-1/2 grid grid-cols-2 gap-2">
                            <img src="https://lh3.googleusercontent.com/d/1zVbHNJ5GXOyyJCQX1mASLS1U62c7aIBA" alt="La Comarca 1" class="w-full h-32 object-cover rounded-lg border border-shire-wood cursor-pointer hover:scale-105 transition" onclick="openModal('https://lh3.googleusercontent.com/d/1zVbHNJ5GXOyyJCQX1mASLS1U62c7aIBA', 'Llegada a La Comarca', 'Las icónicas puertas redondas y el calor de las chimeneas.')">
                            <img src="https://lh3.googleusercontent.com/d/1gHRfaApvqoZnfEYVo4gfcfTLfb_W5htd" alt="La Comarca 2" class="w-full h-32 object-cover rounded-lg border border-shire-wood cursor-pointer hover:scale-105 transition" onclick="openModal('https://lh3.googleusercontent.com/d/1gHRfaApvqoZnfEYVo4gfcfTLfb_W5htd', 'Llegada a La Comarca', 'Ataviados con los mejores ropajes comarcales.')">
                            <img src="https://lh3.googleusercontent.com/d/1nIRvizLGZ6VYe9jnspeIygQeaGptRdhb" alt="La Comarca 3" class="w-full h-32 object-cover rounded-lg border border-shire-wood cursor-pointer hover:scale-105 transition" onclick="openModal('https://lh3.googleusercontent.com/d/1nIRvizLGZ6VYe9jnspeIygQeaGptRdhb', 'Llegada a La Comarca', 'Preparando los festejos y banquetes.')">
                            <img src="https://lh3.googleusercontent.com/d/1ZA7GpkQqoZdAChnsNISetpiS7Nll_Zq2" alt="La Comarca 4" class="w-full h-32 object-cover rounded-lg border border-shire-wood cursor-pointer hover:scale-105 transition" onclick="openModal('https://lh3.googleusercontent.com/d/1ZA7GpkQqoZdAChnsNISetpiS7Nll_Zq2', 'Llegada a La Comarca', 'A través del portal redondo donde nace la historia.')">
                        </div>

                        <div class="w-full md:w-1/2 space-y-4">
                            <div class="flex items-center space-x-3">
                                <span class="w-10 h-10 rounded-full bg-shire-gold text-shire-dark font-fantasy font-bold flex items-center justify-center text-xl shadow-md">1</span>
                                <h3 class="font-heading text-2xl font-bold text-shire-wood">Hito I:«El mundo no está en los libros y mapas. ¡Está ahí fuera!»</h3>
                            </div>
                            <p class="text-lg text-shire-woodlight leading-relaxed">
                                "Nuestra historia comenzó a escribirse en 2022, allá en las tierras de Atenas. Juntos navegamos por decenas de islas griegas, conocimos a gentes venidas de todos los rincones de Europa y sumamos valiosos aliados a nuestra compañía. Al fin, decidimos compartir el mismo hogar... Sí, fue una época inolvidable, repleta de encuentros, de grandes planes y de gyros (¡y pobre de aquel que lo pronuncie "yairo", por la barba de Durin!)."
                            </p>
                                                 </div>
                    </div>

  <div class="relative">
                
                <!-- Timeline Stops List -->
                <div class="space-y-16 relative z-10">
                    
                   

                    <!-- Stop 5 (Hobbiton Gallery: 4 photos) -->
                    <div class="flex flex-col md:flex-row items-center gap-8 bg-parchment-card p-6 sm:p-8 rounded-xl border-2 border-shire-parchmentBorder hover:border-shire-gold transition shadow-xl group">
                        <div class="w-full md:w-1/2 grid grid-cols-2 gap-2">
                            <img src="https://lh3.googleusercontent.com/d/1zVbHNJ5GXOyyJCQX1mASLS1U62c7aIBA" alt="La Comarca 1" class="w-full h-32 object-cover rounded-lg border border-shire-wood cursor-pointer hover:scale-105 transition" onclick="openModal('https://lh3.googleusercontent.com/d/1zVbHNJ5GXOyyJCQX1mASLS1U62c7aIBA', 'Llegada a La Comarca', 'Las icónicas puertas redondas y el calor de las chimeneas.')">
                            <img src="https://lh3.googleusercontent.com/d/1gHRfaApvqoZnfEYVo4gfcfTLfb_W5htd" alt="La Comarca 2" class="w-full h-32 object-cover rounded-lg border border-shire-wood cursor-pointer hover:scale-105 transition" onclick="openModal('https://lh3.googleusercontent.com/d/1gHRfaApvqoZnfEYVo4gfcfTLfb_W5htd', 'Llegada a La Comarca', 'Ataviados con los mejores ropajes comarcales.')">
                            <img src="https://lh3.googleusercontent.com/d/1nIRvizLGZ6VYe9jnspeIygQeaGptRdhb" alt="La Comarca 3" class="w-full h-32 object-cover rounded-lg border border-shire-wood cursor-pointer hover:scale-105 transition" onclick="openModal('https://lh3.googleusercontent.com/d/1nIRvizLGZ6VYe9jnspeIygQeaGptRdhb', 'Llegada a La Comarca', 'Preparando los festejos y banquetes.')">
                            <img src="https://lh3.googleusercontent.com/d/1ZA7GpkQqoZdAChnsNISetpiS7Nll_Zq2" alt="La Comarca 4" class="w-full h-32 object-cover rounded-lg border border-shire-wood cursor-pointer hover:scale-105 transition" onclick="openModal('https://lh3.googleusercontent.com/d/1ZA7GpkQqoZdAChnsNISetpiS7Nll_Zq2', 'Llegada a La Comarca', 'A través del portal redondo donde nace la historia.')">
                        </div>

                        <div class="w-full md:w-1/2 space-y-4">
                            <div class="flex items-center space-x-3">
                                <span class="w-10 h-10 rounded-full bg-shire-gold text-shire-dark font-fantasy font-bold flex items-center justify-center text-xl shadow-md">5</span>
                                <h3 class="font-heading text-2xl font-bold text-shire-wood">Hito V: Llegada a La Comarca</h3>
                            </div>
                            <p class="text-lg text-shire-woodlight leading-relaxed">
                                ¡Por fin en Hobbiton! Entre agujeros hobbit, puertas redondas rojas y verdes, cervezas de la Taberna del Dragón Verde y sonrisas complices. Aquí juramos celebrar el amor con comida, música y risas infinitas.
                            </p>
                            <button onclick="openModal('https://lh3.googleusercontent.com/d/1zVbHNJ5GXOyyJCQX1mASLS1U62c7aIBA', 'Llegada a La Comarca', '¡Por fin en Hobbiton! Entre agujeros hobbit, puertas redondas rojas y verdes, cervezas y sonrisas complices.')" class="font-fantasy text-sm text-shire-ruby hover:text-shire-gold transition flex items-center space-x-2">
                                <i class="fas fa-camera font-bold"></i>
                                <span>Ver Galería Completa de Hobbiton</span>
                            </button>
                        </div>
                    </div>

                    <!-- Stop 6 -->
                    <div class="flex flex-col md:flex-row-reverse items-center gap-8 bg-parchment-card p-6 sm:p-8 rounded-xl border-2 border-shire-parchmentBorder hover:border-shire-gold transition shadow-xl group">
                        <div class="w-full md:w-1/2 overflow-hidden rounded-lg border-4 border-shire-wood cursor-pointer" onclick="openModal('https://lh3.googleusercontent.com/d/1X9x2dbw8tLLj0NqNDfVUMWqGX6o1By9q', 'Hechizo de Amor', 'Con sombreros mágicos y alegría en el corazón, sellamos nuestra unión bajo un verdadero conjuro de amor eterno.')">
                            <img src="https://lh3.googleusercontent.com/d/1X9x2dbw8tLLj0NqNDfVUMWqGX6o1By9q" alt="Hechizo de Amor" class="w-full h-64 sm:h-80 object-cover group-hover:scale-105 transition duration-500">
                        </div>
                        <div class="w-full md:w-1/2 space-y-4">
                            <div class="flex items-center space-x-3">
                                <span class="w-10 h-10 rounded-full bg-shire-gold text-shire-dark font-fantasy font-bold flex items-center justify-center text-xl shadow-md">6</span>
                                <h3 class="font-heading text-2xl font-bold text-shire-wood">Hito VI: Hechizo de Amor</h3>
                            </div>
                            <p class="text-lg text-shire-woodlight leading-relaxed">
                                Ni la magia de Gandalf ni los elixires más potentes pueden superar la chispa que encendió nuestros corazones. Con un beso sellamos la promesa de nuestro próximo gran capítulo.
                            </p>
                            <button onclick="openModal('https://lh3.googleusercontent.com/d/1X9x2dbw8tLLj0NqNDfVUMWqGX6o1By9q', 'Hechizo de Amor', 'Con sombreros mágicos y alegría en el corazón, sellamos nuestra unión bajo un verdadero conjuro de amor eterno.')" class="font-fantasy text-sm text-shire-ruby hover:text-shire-gold transition flex items-center space-x-2">
                                <i class="fas fa-magic"></i>
                                <span>Ver Pergamino Extendido</span>
                            </button>
                        </div>
                    </div>

                </div>
            </div>

        </div>
    </section>

    <section id="lugares" class="py-20 px-4 sm:px-8 bg-shire-wood text-shire-parchment relative overflow-hidden">
        <!-- Background Elven Ornament Overlay -->
        <div class="absolute -top-12 -left-12 opacity-10 text-9xl pointer-events-none">🌿</div>
        <div class="absolute -bottom-12 -right-12 opacity-10 text-9xl pointer-events-none">🍃</div>

        <div class="max-w-6xl mx-auto">
            
            <div class="text-center mb-16 space-y-3">
                <p class="font-fantasy text-shire-gold text-lg">Guía de Destinos</p>
                <h2 class="font-heading text-3xl sm:text-5xl font-bold text-gold-gradient uppercase tracking-wider">
                    Los Lugares del Reino
                </h2>
                <div class="w-24 h-1 bg-shire-gold mx-auto"></div>
                <p class="text-lg max-w-2xl mx-auto italic text-shire-parchmentDark">
                    Dos enclaves sagrados para dos momentos inolvidables de la jornada.
                </p>
            </div>

            <div class="grid md:grid-cols-2 gap-10">
                
                <!-- Ceremony Card -->
                <div class="bg-shire-woodlight/80 border-2 border-shire-gold rounded-xl p-8 space-y-6 shadow-2xl relative flex flex-col justify-between hover:border-white transition">
                    <div class="space-y-4">
                        <div class="flex items-center justify-between border-b border-shire-gold/30 pb-4">
                            <span class="font-fantasy text-shire-gold text-sm tracking-widest uppercase">Etapa I • La Ceremonia</span>
                            <i class="fas fa-church text-shire-gold text-2xl"></i>
                        </div>
                        <h3 class="font-heading text-2xl sm:text-3xl font-bold text-white">Iglesia del Cerro de Motril</h3>
                        <p class="text-shire-gold font-fantasy">Santuario de Nuestra Señora de la Cabeza</p>
                        
                        <div class="space-y-3 text-shire-parchmentDark text-lg">
                            <p class="flex items-center space-x-3">
                                <i class="far fa-clock text-shire-gold w-6"></i>
                                <span>29 de Mayo de 2027</span>
                            </p>
                            <p class="flex items-center space-x-3">
                                <i class="fas fa-map-marker-alt text-shire-gold w-6"></i>
                                <span>Cerro de la Virgen, Motril, Granada</span>
                            </p>
                            <p class="pt-2 text-base italic leading-relaxed text-shire-parchment/80">
                                En lo alto de la colina de Motril, donde la brisa del mar abraza las piedras históricas, nos daremos el "Sí, quiero" bajo la bendición sagrada.
                            </p>
                        </div>
                    </div>

                    <div class="pt-6">
                        <a href="https://maps.google.com/?q=Iglesia+del+Cerro+de+Motril" target="_blank" class="w-full bg-shire-gold hover:bg-shire-goldBright text-shire-dark font-fantasy font-bold py-3 px-6 rounded-lg transition text-center flex items-center justify-center space-x-2 shadow-lg">
                            <i class="fas fa-compass"></i>
                            <span>Mapa del Navegante (Google Maps)</span>
                        </a>
                    </div>
                </div>

                <!-- Feast Card -->
                <div class="bg-shire-woodlight/80 border-2 border-shire-gold rounded-xl p-8 space-y-6 shadow-2xl relative flex flex-col justify-between hover:border-white transition">
                    <div class="space-y-4">
                        <div class="flex items-center justify-between border-b border-shire-gold/30 pb-4">
                            <span class="font-fantasy text-shire-gold text-sm tracking-widest uppercase">Etapa II • El Banquete</span>
                            <i class="fas fa-glass-cheers text-shire-gold text-2xl"></i>
                        </div>
                        <h3 class="font-heading text-2xl sm:text-3xl font-bold text-white">Hotel Salobreña</h3>
                        <p class="text-shire-gold font-fantasy">Festín y Gran Baile de La Comarca</p>
                        
                        <div class="space-y-3 text-shire-parchmentDark text-lg">
                            <p class="flex items-center space-x-3">
                                <i class="far fa-clock text-shire-gold w-6"></i>
                                <span>A continuación de la Ceremonia</span>
                            </p>
                            <p class="flex items-center space-x-3">
                                <i class="fas fa-map-marker-alt text-shire-gold w-6"></i>
                                <span>Carretera N-340, Km 323, Salobreña, Granada</span>
                            </p>
                            <p class="pt-2 text-base italic leading-relaxed text-shire-parchment/80">
                                Frente al acantilado y el mar Mediterráneo, disfrutaremos del banquete de Hobbits y Elfos, música, bailes hasta el amanecer y muchas sorpresas.
                            </p>
                        </div>
                    </div>

                    <div class="pt-6">
                        <a href="https://maps.google.com/?q=Hotel+Salobrena" target="_blank" class="w-full bg-shire-gold hover:bg-shire-goldBright text-shire-dark font-fantasy font-bold py-3 px-6 rounded-lg transition text-center flex items-center justify-center space-x-2 shadow-lg">
                            <i class="fas fa-compass"></i>
                            <span>Mapa del Navegante (Google Maps)</span>
                        </a>
                    </div>
                </div>

            </div>

        </div>
    </section>

    <section id="rsvp" class="py-20 px-4 sm:px-8 bg-parchment-texture relative">
        <div class="max-w-3xl mx-auto">
            
            <div class="text-center mb-12 space-y-3">
                <p class="font-fantasy text-shire-ruby text-lg">Decreto Real de Asistencia</p>
                <h2 class="font-heading text-3xl sm:text-5xl font-bold text-shire-wood uppercase tracking-wider">
                    Confirma tu Asistencia
                </h2>
                <div class="w-24 h-1 bg-shire-gold mx-auto"></div>
                <p class="text-lg italic text-shire-woodlight">
                    "Por favor, envía tu paloma mensajera antes del 1 de Abril de 2027"
                </p>
            </div>

            <!-- Scroll Form Card -->
            <div class="bg-parchment-card p-6 sm:p-10 rounded-2xl border-4 border-shire-parchmentBorder shadow-2xl relative">
                
                <form id="rsvp-form" onsubmit="handleRSVP(event)" class="space-y-6">
                    <div>
                        <label class="block font-fantasy text-shire-wood text-lg mb-2" for="guest-name">
                            <i class="fas fa-user-edit text-shire-ruby mr-2"></i> ¡Que estallen las presentaciones! Escribe aquí tu nombre completo.
                        </label>
                        <input type="text" id="guest-name" required placeholder="Ej: Frodo Bolsón" class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold">
                    </div>

                    <div class="grid sm:grid-cols-1 gap-6">
                        <div>
                            <label class="block font-fantasy text-shire-wood text-lg mb-2">
                                <i class="fas fa-check-circle text-shire-ruby mr-2"></i> Las estrellas presagian una gran reunión. ¿Acudirás a la llamada cuando se enciendan las almenaras, o rehuirás la celebración?
                            </label>
<label class="flex items-start gap-3 p-3 bg-white/80 border-2 border-shire-parchmentBorder rounded-lg cursor-pointer hover:border-shire-gold transition-colors">
        <input type="radio" name="attendance" value="Si" required class="mt-1.5 text-shire-gold focus:ring-shire-gold">
        <span><strong>Sí, asistiré:</strong> Un mago nunca llega tarde, ni pronto; llega exactamente cuando se lo propone. ¡Allí estaré!</span>
    </label>

    <!-- Opción No -->
<div style="margin-top: 10px;"></div>
    <label class="flex items-start gap-3 p-3 bg-white/80 border-2 border-shire-parchmentBorder rounded-lg cursor-pointer hover:border-shire-gold transition-colors">
        <input type="radio" name="attendance" value="No" required class="mt-1.5 text-shire-gold focus:ring-shire-gold">
        <span><strong>No podré asistir:</strong> Mis pasos me llevan por senderos urgentes y oscuros lejos de aquí, pero os deseo toda la felicidad en vuestro viaje.</span>
    </label>
                            </select>
                        </div>

                    <div>
                        <label class="block font-fantasy text-shire-wood text-lg mb-2" for="guest-name">
                            <i class="fas fa-user-edit text-shire-ruby mr-2"></i> Ningún guerrero debería cabalgar solo hacia los momentos que definen la historia. ¿Te acompañan otros espíritus afines en esta jornada? Dinos sus nombres.
                        </label>
                        <input type="text" id="guest-name" required placeholder="Ej: Aragon y Samsagaz Gamyi" class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold">
                    </div>
                    <div>
                        <label class="block font-fantasy text-shire-wood text-lg mb-2" for="guest-name">
                            <i class="fas fa-user-edit text-shire-ruby mr-2"></i> ¿Te acompañan pequeños medianos en esta jornada? Desvela sus nombres y los inviernos que han contemplado
                        </label>
                        <input type="text" id="guest-name" required placeholder=" Ej: Andrés - 7 años" class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold">
                    </div>

<div>
    <label class="block font-fantasy text-shire-wood text-lg mb-2">
        <i class="fas fa-utensils text-shire-ruby mr-2"></i> Hay venenos sutiles que nublan el festín y hierbas que no todos los estómagos toleran. Dinos si tenéis alguna preferencia o si algún alimento os causa debilidad, pues no querríamos que vuestro cuerpo mutara en extraña criatura el día del juramento.</label>
    
    <select id="diet" class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold">
        <option value="Estándar">Menú Estándar de La Comarca</option>
        <option value="Vegetariano">Menú Vegetariano de Rivendel</option>
        <option value="Vegano">Menú Vegano de Lorien</option>
        <option value="Alergias">Alergias / Intolerancias </option>
    </select>

    <!-- Contenedor del cuadro de texto de alergias (oculto por defecto) -->
    <div id="allergies-container" class="mt-3 hidden">
        <label for="allergies-details" class="block font-fantasy text-shire-wood text-sm mb-1">
            <i class="fas fa-exclamation-triangle text-shire-ruby mr-1"></i> Especifica tus alergias o intolerancias:
        </label>
        <textarea 
            id="allergies-details" 
            name="allergies_details" 
            rows="3" 
            placeholder="Ejemplo: Intolerancia a la lactosa, alergia a los frutos secos..." 
            class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-2 text-shire-wood font-body text-base focus:outline-none focus:border-shire-gold placeholder:text-shire-wood/50 resize-y"
        ></textarea>
    </div>
</div>
                    </div>

<div>
    <label class="block font-fantasy text-shire-wood text-lg mb-3">
        <i class="fas fa-bus text-shire-ruby mr-2"></i> Los caballos no bastarán para trasladar a todo el ejército desde el santuario hasta el gran salón de banquetes. Una gran caravana de hierro será dispuesta para el traslado. ¿Os uniréis a ella o confiaréis vuestro viaje a vuestra propia montura?
    </label>

    <div class="space-y-3">
        <!-- Opción 1: No asistir -->
        <label class="flex items-start gap-3 p-3 bg-white/80 border-2 border-shire-parchmentBorder rounded-lg cursor-pointer hover:border-shire-gold transition-colors">
            <input type="radio" name="attendance" value="No" required class="mt-1.5 text-shire-gold focus:ring-shire-gold">
            <span><strong>No asistiré:</strong> No, mi buen amigo. Seguiré mi propio camino, como un auténtico montaraz (no, gracias).</span>
        </label>

        <!-- Opción 2: Solo ida -->
        <label class="flex items-start gap-3 p-3 bg-white/80 border-2 border-shire-parchmentBorder rounded-lg cursor-pointer hover:border-shire-gold transition-colors">
            <input type="radio" name="attendance" value="Solo ida" required class="mt-1.5 text-shire-gold focus:ring-shire-gold">
            <span><strong>Solo ida:</strong> Iré en la caravana hacia el banquete, pero tengo mis propios planes para el final de los festejos.</span>
        </label>

        <!-- Opción 3: Solo vuelta -->
        <label class="flex items-start gap-3 p-3 bg-white/80 border-2 border-shire-parchmentBorder rounded-lg cursor-pointer hover:border-shire-gold transition-colors">
            <input type="radio" name="attendance" value="Solo vuelta" required class="mt-1.5 text-shire-gold focus:ring-shire-gold">
            <span><strong>Solo vuelta:</strong> Llegaré al templo por mis propios medios, pero cuando la noche caiga y el cansancio pese, me uniré a vuestra caravana.</span>
        </label>

        <!-- Opción 4: Ida y vuelta -->
        <label class="flex items-start gap-3 p-3 bg-white/80 border-2 border-shire-parchmentBorder rounded-lg cursor-pointer hover:border-shire-gold transition-colors">
            <input type="radio" name="attendance" value="Ida y vuelta" required class="mt-1.5 text-shire-gold focus:ring-shire-gold">
            <span><strong>Ida y vuelta:</strong> ¡Contad conmigo para todo el viaje! No pienso perderme ni un solo tramo de esta gran aventura.</span>
        </label>
    </div>
</div>

<div>
    <label class="block font-fantasy text-shire-wood text-lg mb-2">
        <i class="fas fa-hotel text-shire-ruby mr-2"></i> ¿Vas a necesitar habitación en el hotel del banquete? Tras tantos brindis y bailes, hasta el más sabio de los magos necesita un buen jergón donde caer rendido. Dinos si te quedarás a pasar la noche en los aposentos del propio recinto o si tu camino te llevará de vuelta a casa antes del amanecer.
    </label>
    
    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
        <!-- Fecha de inicio (Desde) -->
        <div>
            <label for="date-from" class="block font-fantasy text-shire-wood text-sm mb-1">Llegada al festín:</label>
            <input 
                type="date" 
                id="date-from" 
                name="date_from"
                class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold"
            >
        </div>

        <!-- Fecha de fin (Hasta) -->
        <div>
            <label for="date-to" class="block font-fantasy text-shire-wood text-sm mb-1">Regreso al hogar:</label>
            <input 
                type="date" 
                id="date-to" 
                name="date_to"
                class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold"
            >
        </div>
    </div>
</div>

                    <div>
                        <label class="block font-fantasy text-shire-wood text-lg mb-2" for="song-request">
                            <i class="fas fa-music text-shire-ruby mr-2"></i> Ni los elfos en sus bosques ni los enanos en sus salones celebran sin música. Escribe aquí un tema que sacudirá la Tierra Media.
                        </label>
                        <input type="text" id="song-request" placeholder="Ej: Cantos de los Enanos / Pop de los 80" class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold">
                    </div>

                    <div>
                        <label class="block font-fantasy text-shire-wood text-lg mb-2" for="message">
                            <i class="fas fa-scroll text-shire-ruby mr-2"></i> Palabras o Bendiciones para los Novios:
                        </label>
                        <textarea id="message" rows="3" placeholder="Escribe aquí tu mensaje de buenos augurios..." class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold"></textarea>
                    </div>

                    <div class="text-center pt-4">
                        <button type="submit" class="wax-seal text-white font-fantasy text-xl px-10 py-4 rounded-full transition duration-300 transform inline-flex items-center space-x-3 cursor-pointer">
                            <i class="fas fa-stamp text-2xl"></i>
                            <span>Sellar Decreto de Asistencia</span>
                        </button>
                    </div>
                </form>

                <!-- Confirmation Scroll Output -->
                <div id="rsvp-success" class="hidden text-center space-y-6 py-8">
                    <div class="w-20 h-20 wax-seal rounded-full flex items-center justify-center mx-auto text-white text-3xl shadow-xl">
                        ✓
                    </div>
                    <h3 class="font-heading text-3xl text-shire-wood font-bold">¡Decreto Sellado con Éxito!</h3>
                    <p class="text-xl text-shire-woodlight italic max-w-lg mx-auto">
                        Tus datos han sido registrados en el Libro de la Comarca. Santiago y Jenifer aguardan con ilusión tu llegada.
                    </p>
                    <button onclick="resetForm()" class="font-fantasy text-sm text-shire-ruby hover:underline">
                        Enviar otra respuesta
                    </button>
                </div>

            </div>

        </div>
    </section>

    <section class="py-20 px-4 sm:px-8 bg-shire-wood text-shire-parchment relative">
        <div class="max-w-5xl mx-auto space-y-16">
            
            <!-- Travel Tips -->
            <div>
                <div class="text-center mb-10 space-y-2">
                    <p class="font-fantasy text-shire-gold">Consejos de La Comarca</p>
                    <h2 class="font-heading text-3xl font-bold uppercase text-gold-gradient">Guía para Viajeros</h2>
                    <div class="w-16 h-1 bg-shire-gold mx-auto"></div>
                </div>

                <div class="grid md:grid-cols-3 gap-6">
                    <div class="bg-shire-woodlight p-3 rounded-lg border border-shire-gold/40 text-center space-y-3">
                        <i class="fas fa-user-ninja text-3xl text-shire-gold"></i>
                        <h4 class="font-fantasy text-xl text-white">Código de Vestimenta</h4>
                        <p class="text-shire-parchmentDark text-base">
                            Elegancia Comarcal / Fantástica Formal. Trajes elegantes, vestidos de fiesta con toques de fantasía o detalles botánicos son más que bienvenidos.
                        </p>
                    </div>

                    <div class="bg-shire-woodlight p-6 rounded-lg border border-shire-gold/40 text-center space-y-3">
                        <i class="fas fa-bed text-3xl text-shire-gold"></i>
                        <h4 class="font-fantasy text-xl text-white">Alojamiento</h4>
                        <p class="text-shire-parchmentDark text-base">
                            Recomendamos reservar estancia en el propio **Hotel Salobreña** o en hoteles/hostales en Motril para mayor comodidad tras el baile.
                        </p>
                    </div>

                    <div class="bg-shire-woodlight p-6 rounded-lg border border-shire-gold/40 text-center space-y-3">
                        <i class="fas fa-bus text-3xl text-shire-gold"></i>
                        <h4 class="font-fantasy text-xl text-white">Transporte</h4>
                        <p class="text-shire-parchmentDark text-base">
                            Habrá servicio de autobús desde la Iglesia del Cerro hasta el Hotel Salobreña para quienes prefieran no conducir.
                        </p>
                    </div>
                </div>
            </div>

            <!-- Wedding Registry Gift Section -->
            <div class="bg-shire-woodlight/60 border-2 border-shire-gold p-8 sm:p-12 rounded-2xl text-center space-y-6 max-w-3xl mx-auto backdrop-blur-sm">
                <i class="fas fa-coins text-4xl text-shire-gold"></i>
                <h3 class="font-heading text-3xl font-bold text-white">El Cofre del Tesoro</h3>
                <p class="text-lg text-shire-parchmentDark leading-relaxed">
                    El mejor regalo es vuestra presencia en nuestro Gran Viaje. No obstante, si deseáis colaborar con monedas de oro para nuestra expedición de luna de miel:
                </p>
                
                <div class="bg-shire-dark/80 p-4 rounded-xl border border-shire-gold/50 inline-block">
                    <p class="font-fantasy text-shire-gold text-sm uppercase mb-1">IBAN / Cuenta Corriente</p>
                    <p id="iban-code" class="font-mono text-xl text-white font-bold tracking-wider select-all">ES00 0000 0000 0000 0000 0000</p>
                </div>

                <div>
                    <button onclick="copyIBAN()" class="bg-shire-gold hover:bg-shire-goldBright text-shire-dark font-fantasy font-bold px-6 py-2 rounded-full transition text-sm">
                        <i class="fas fa-copy mr-1"></i> Copiar Código IBAN
                    </button>
                    <span id="copy-msg" class="block text-xs text-shire-gold mt-2 hidden">¡Copiado al portapapeles!</span>
                </div>
            </div>

        </div>
    </section>

    <div id="photo-modal" class="fixed inset-0 bg-black/90 z-50 hidden flex items-center justify-center p-4 backdrop-blur-md">
        <div class="bg-parchment-card max-w-3xl w-full p-6 sm:p-8 rounded-2xl border-4 border-shire-gold relative space-y-4">
            <button onclick="closeModal()" class="absolute top-4 right-4 text-shire-wood text-3xl hover:text-shire-ruby transition">
                &times;
            </button>
            <div class="overflow-hidden rounded-xl border-2 border-shire-wood">
                <img id="modal-img" src="" alt="Vista ampliada" class="w-full max-h-[60vh] object-contain bg-black">
            </div>
            <h3 id="modal-title" class="font-heading text-2xl font-bold text-shire-wood"></h3>
            <p id="modal-desc" class="text-lg text-shire-woodlight italic leading-relaxed"></p>
        </div>
    </div>

    <footer class="bg-shire-dark border-t border-shire-gold/30 py-8 text-center text-shire-parchmentDark space-y-3">
        <p class="font-fantasy text-lg text-shire-gold">
            Santiago & Jenifer • 29 de Mayo de 2027
        </p>
        <p class="text-xs text-shire-parchmentDark/60">
            "No todos los que vagan están perdidos."
        </p>
    </footer>

    <script>
        const weddingDate = new Date("May 29, 2027 12:00:00").getTime();

        function updateCountdown() {
            const now = new Date().getTime();
            const difference = weddingDate - now;

            if (difference > 0) {
                const days = Math.floor(difference / (1000 * 60 * 60 * 24));
                const hours = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
                const seconds = Math.floor((difference % (1000 * 60)) / 1000);

                document.getElementById("days").innerText = days < 10 ? "0" + days : days;
                document.getElementById("hours").innerText = hours < 10 ? "0" + hours : hours;
                document.getElementById("minutes").innerText = minutes < 10 ? "0" + minutes : minutes;
                document.getElementById("seconds").innerText = seconds < 10 ? "0" + seconds : seconds;
            }
        }
        setInterval(updateCountdown, 1000);
        updateCountdown();

        // =========================================================================
        // LÍNEA EXACTA PARA CAMBIAR LA CANCIÓN DE FONDO EN EL CÓDIGO JAVASCRIPT:
        // =========================================================================
        let audioUrl = 'https://mp3tourl.com/audio/1791366443143-7129d727-ef02-4a6a-8a9a-4df7a5648d80.m4a';
        // Solo debes reemplazar la URL entre comillas simples '...' por el enlace de tu MP3 favorito.

        let isPlaying = false;

        function toggleAudio() {
            const audioElement = document.getElementById('wedding-music');
            const soundIcon = document.getElementById('sound-icon');
            const soundText = document.getElementById('sound-text');

            if (!isPlaying) {
                audioElement.play().then(() => {
                    isPlaying = true;
                    soundIcon.className = 'fas fa-volume-up text-lg text-shire-gold';
                    soundText.innerText = 'Música Activada';
                }).catch(err => {
                    console.error("Error reproduciendo el audio:", err);
                });
            } else {
                audioElement.pause();
                isPlaying = false;
                soundIcon.className = 'fas fa-volume-mute text-lg';
                soundText.innerText = 'Música de La Comarca';
            }
        }

        function changeAudioUrl() {
            const input = document.getElementById('custom-audio-input').value;
            if (input) {
                const audioElement = document.getElementById('wedding-music');
                const sourceElement = document.getElementById('audio-source');
                sourceElement.src = input;
                audioElement.load();
                if (isPlaying) {
                    audioElement.play();
                }
            }
        }

        function createLeaves() {
            const container = document.getElementById('leaves-container');
            const leafIcons = ['🍃', '🌿', '🍁'];
            for (let i = 0; i < 9; i++) {
                let leaf = document.createElement('div');
                leaf.className = 'leaf-particle';
                leaf.innerText = leafIcons[Math.floor(Math.random() * leafIcons.length)];
                leaf.style.left = Math.random() * 100 + 'vw';
                leaf.style.animationDuration = (8 + Math.random() * 10) + 's';
                leaf.style.animationDelay = (Math.random() * 5) + 's';
                leaf.style.fontSize = (15 + Math.random() * 15) + 'px';
                container.appendChild(leaf);
            }
        }
        createLeaves();

        function openModal(imgSrc, title, desc) {
            document.getElementById('modal-img').src = imgSrc;
            document.getElementById('modal-title').innerText = title;
            document.getElementById('modal-desc').innerText = desc;
            document.getElementById('photo-modal').classList.remove('hidden');
        }

        function closeModal() {
            document.getElementById('photo-modal').classList.add('hidden');
        }

        async function handleRSVP(event) {
            event.preventDefault();
            const name = document.getElementById('guest-name').value;
            const attendance = document.getElementById('attendance').value;
            const diet = document.getElementById('diet').value;
            const song = document.getElementById('song-request').value;
            const message = document.getElementById('message').value;

            const rsvpData = { name, attendance, diet, song, message, date: new Date().toISOString() };
            
// Enviar datos a Formspree
try {
  const response = await fetch('https://formspree.io/f/mljggpgz', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'Accept': 'application/json'
    },
    body: JSON.stringify(rsvpData)
  });

  if (response.ok) {
    // Guardar copia local opcionalmente
    let currentData = JSON.parse(localStorage.getItem('wedding_rsvp_santiago_jenifer') || '[]');
    currentData.push(rsvpData);
    localStorage.setItem('wedding_rsvp_santiago_jenifer', JSON.stringify(currentData));

    // Mostrar mensaje de éxito
    document.getElementById('rsvp-form').classList.add('hidden');
    document.getElementById('rsvp-success').classList.remove('hidden');
  } else {
    alert('Hubo un problema al enviar tu respuesta. Por favor, inténtalo de nuevo.');
  }
} catch (error) {
  alert('Error de red. Por favor, verifica tu conexión e inténtalo más tarde.');
}
        }

        function resetForm() {
            document.getElementById('rsvp-form').reset();
            document.getElementById('rsvp-form').classList.remove('hidden');
            document.getElementById('rsvp-success').classList.add('hidden');
        }

        function copyIBAN() {
            const iban = document.getElementById('iban-code').innerText;
            const textarea = document.createElement('textarea');
            textarea.value = iban;
            document.body.appendChild(textarea);
            textarea.select();
            document.execCommand('copy');
            document.body.removeChild(textarea);

            const msg = document.getElementById('copy-msg');
            msg.classList.remove('hidden');
            setTimeout(() => msg.classList.add('hidden'), 3000);
        }

document.addEventListener('DOMContentLoaded', () => {
    const dietSelect = document.getElementById('diet');
    const allergiesContainer = document.getElementById('allergies-container');
    const allergiesInput = document.getElementById('allergies-details');

    function toggleAllergiesInput() {
        if (dietSelect.value === 'Alergias') {
            allergiesContainer.classList.remove('hidden');
            allergiesInput.focus(); // Pone el foco directamente en el cuadro de texto
        } else {
            allergiesContainer.classList.add('hidden');
            allergiesInput.value = ''; // Opcional: limpia el campo si eligen otra opción
        }
    }

    // Escuchar cambios en el selector
    dietSelect.addEventListener('change', toggleAllergiesInput);

    // Comprobar estado inicial (por si la página se recarga con la opción seleccionada)
    toggleAllergiesInput();
});
    </script>
</body>
</html>
