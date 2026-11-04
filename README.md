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
                <!-- 1. Nombre Principal (Obligatorio) -->
                <div>
                    <label class="block font-fantasy text-shire-wood text-lg mb-2" for="guest-name">
                        <i class="fas fa-user-edit text-shire-ruby mr-2"></i> ¡Que estallen las presentaciones! Escribe aquí tu nombre completo. (*)
                    </label>
                    <input type="text" id="guest-name" name="guest_name" required placeholder="Ej: Frodo Bolsón" class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold">
                </div>

                <!-- 2. Confirmación de Asistencia (Obligatorio) -->
                <div>
                    <label class="block font-fantasy text-shire-wood text-lg mb-2">
                        <i class="fas fa-check-circle text-shire-ruby mr-2"></i> Las estrellas presagian una gran reunión. ¿Acudirás a la llamada cuando se enciendan las almenaras, o rehuirás la celebración? (*)
                    </label>
                    <div class="space-y-3">
                        <label class="flex items-start gap-3 p-3 bg-white/80 border-2 border-shire-parchmentBorder rounded-lg cursor-pointer hover:border-shire-gold transition-colors">
                            <input type="radio" name="attendance" value="Si" required class="mt-1.5 text-shire-gold focus:ring-shire-gold">
                            <span><strong>Sí, asistiré:</strong> Un mago nunca llega tarde, ni pronto; llega exactamente cuando se lo propone. ¡Allí estaré!</span>
                        </label>
                        <label class="flex items-start gap-3 p-3 bg-white/80 border-2 border-shire-parchmentBorder rounded-lg cursor-pointer hover:border-shire-gold transition-colors">
                            <input type="radio" name="attendance" value="No" required class="mt-1.5 text-shire-gold focus:ring-shire-gold">
                            <span><strong>No podré asistir:</strong> Mis pasos me llevan por senderos urgentes y oscuros lejos de aquí, pero os deseo toda la felicidad en vuestro viaje.</span>
                        </label>
                    </div>
                </div>

                <!-- 3. Acompañantes Adultos (Opcional) -->
                <div>
                    <label class="block font-fantasy text-shire-wood text-lg mb-2" for="companions">
                        <i class="fas fa-users text-shire-ruby mr-2"></i> ¿Asistirán contigo otros aliados en esta celebración, o vaga tu alma en el aislamiento de un errante de las tierras salvajes? Dinos sus nombres.
                    </label>
                    <input type="text" id="companions" name="companions" placeholder="Ej: Aragorn y Legolas" class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold">
                </div>

                <!-- 4. Niños (Opcional) -->
                <div>
                    <label class="block font-fantasy text-shire-wood text-lg mb-2" for="children">
                        <i class="fas fa-child text-shire-ruby mr-2"></i> ¿Te acompañan pequeños medianos en esta jornada? Desvela sus nombres y los inviernos que han contemplado.
                    </label>
                    <input type="text" id="children" name="children" placeholder="Ej: Andrés - 7 años" class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold">
                </div>

                <!-- 5. Menú y Alergias (Obligatorio el selector) -->
                <div>
                    <label class="block font-fantasy text-shire-wood text-lg mb-2" for="diet">
                        <i class="fas fa-utensils text-shire-ruby mr-2"></i> Hay venenos sutiles que nublan el festín y hierbas que no todos los estómagos toleran. Dinos si tenéis alguna preferencia o si algún alimento os causa debilidad: (*)
                    </label>
                    
                    <select id="diet" name="diet" required class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold">
                        <option value="" disabled selected>Selecciona tu tipo de menú...</option>
                        <option value="Estándar">Menú Estándar de La Comarca</option>
                        <option value="Vegetariano">Menú Vegetariano de Rivendel</option>
                        <option value="Vegano">Menú Vegano de Lorien</option>
                        <option value="Alergias">Alergias / Intolerancias (Especificar abajo)</option>
                    </select>

                    <div id="allergies-container" class="mt-3 hidden">
                        <label for="allergies-details" class="block font-fantasy text-shire-wood text-sm mb-1">
                            <i class="fas fa-exclamation-triangle text-shire-ruby mr-1"></i> Especifica tus alergias o intolerancias: (*)
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

                <!-- 6. Autobús / Caravana (Obligatorio) -->
                <div>
                    <label class="block font-fantasy text-shire-wood text-lg mb-3">
                        <i class="fas fa-bus text-shire-ruby mr-2"></i> Los caballos no bastarán para trasladar a todo el ejército desde el santuario hasta el gran salón de banquetes. Una gran caravana de hierro será dispuesta para el traslado. ¿Os uniréis a ella o confiaréis vuestro viaje a vuestra propia montura? (*)
                    </label>

                    <div class="space-y-3">
                        <label class="flex items-start gap-3 p-3 bg-white/80 border-2 border-shire-parchmentBorder rounded-lg cursor-pointer hover:border-shire-gold transition-colors">
                            <input type="radio" name="bus_option" value="No" required class="mt-1.5 text-shire-gold focus:ring-shire-gold">
                            <span><strong>No precisaré caravana:</strong> No, mi buen amigo. Seguiré mi propio camino, como un auténtico montaraz (no, gracias).</span>
                        </label>
                        <label class="flex items-start gap-3 p-3 bg-white/80 border-2 border-shire-parchmentBorder rounded-lg cursor-pointer hover:border-shire-gold transition-colors">
                            <input type="radio" name="bus_option" value="Solo ida" required class="mt-1.5 text-shire-gold focus:ring-shire-gold">
                            <span><strong>Solo ida:</strong> Iré en la caravana hacia el banquete, pero tengo mis propios planes para el final de los festejos.</span>
                        </label>
                        <label class="flex items-start gap-3 p-3 bg-white/80 border-2 border-shire-parchmentBorder rounded-lg cursor-pointer hover:border-shire-gold transition-colors">
                            <input type="radio" name="bus_option" value="Solo vuelta" required class="mt-1.5 text-shire-gold focus:ring-shire-gold">
                            <span><strong>Solo vuelta:</strong> Llegaré al templo por mis propios medios, pero cuando la noche caiga y el cansancio pese, me uniré a vuestra caravana.</span>
                        </label>
                        <label class="flex items-start gap-3 p-3 bg-white/80 border-2 border-shire-parchmentBorder rounded-lg cursor-pointer hover:border-shire-gold transition-colors">
                            <input type="radio" name="bus_option" value="Ida y vuelta" required class="mt-1.5 text-shire-gold focus:ring-shire-gold">
                            <span><strong>Ida y vuelta:</strong> ¡Contad conmigo para todo el viaje! No pienso perderme ni un solo tramo de esta gran aventura.</span>
                        </label>
                    </div>
                </div>

                <!-- 7. Hotel (Fechas) - Opcional -->
                <div>
                    <label class="block font-fantasy text-shire-wood text-lg mb-2">
                        <i class="fas fa-hotel text-shire-ruby mr-2"></i> ¿Vas a necesitar habitación en la posada del banquete? Tras tantos brindis y bailes, hasta el más sabio de los magos necesita un buen jergón donde caer rendido. Dinos si te quedarás a pasar la noche en los aposentos del propio recinto o si tu camino te llevará de vuelta a casa antes del amanecer.
                    </label>
                    
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                        <div>
                            <label for="date-from" class="block font-fantasy text-shire-wood text-sm mb-1">Llegada al festín:</label>
                            <input 
                                type="date" 
                                id="date-from" 
                                name="date_from"
                                min="2027-05-03"
                                max="2027-05-29"
                                class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold"
                            >
                        </div>
                        <div>
                            <label for="date-to" class="block font-fantasy text-shire-wood text-sm mb-1">Regreso al hogar:</label>
                            <input 
                                type="date" 
                                id="date-to" 
                                name="date_to"
                                min="2027-05-30"
                                max="2027-06-07"
                                class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold"
                            >
                        </div>
                    </div>
                </div>

                <!-- 8. Canción (Opcional) -->
                <div>
                    <label class="block font-fantasy text-shire-wood text-lg mb-2" for="song-request">
                        <i class="fas fa-music text-shire-ruby mr-2"></i> Ni los elfos en sus bosques ni los enanos en sus salones celebran sin música. Escribe aquí un tema que sacudirá la Tierra Media.
                    </label>
                    <input type="text" id="song-request" name="song_request" placeholder="Ej: Ave Maria / Torero / Ops I did it again / YMCM / Breaking Free..." class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold">
                </div>

                <!-- 9. Mensaje (Opcional) -->
                <div>
                    <label class="block font-fantasy text-shire-wood text-lg mb-2" for="message">
                        <i class="fas fa-scroll text-shire-ruby mr-2"></i> Palabras o Bendiciones para los Novios:
                    </label>
                    <textarea id="message" name="message" rows="3" placeholder="Escribe aquí tu mensaje de buenos augurios..." class="w-full bg-white/80 border-2 border-shire-parchmentBorder rounded-lg px-4 py-3 text-shire-wood font-body text-lg focus:outline-none focus:border-shire-gold"></textarea>
                </div>
                
                <label class="block font-fantasy text-shire-wood text-xs mb-2"> * Campo obligatorio </label>

                <!-- Botón Enviar -->
                <div class="text-center pt-4">
                    <button type="submit" class="wax-seal text-white font-fantasy text-xl px-10 py-4 rounded-full transition duration-300 transform inline-flex items-center space-x-3 cursor-pointer hover:scale-105">
                        <i class="fas fa-stamp text-2xl"></i>
                        <span>Sellar Decreto de Asistencia</span>
                    </button>
                </div>
            </form>

            <!-- Mensaje de éxito -->
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
