document.addEventListener('DOMContentLoaded', () => {
    // Simulación de una foto actual del huerto
    const currentGardenPhoto = document.getElementById('current-garden-photo');
    const lastUpdateDate = document.getElementById('last-update-date');

    // Puedes cambiar esta URL por una URL real de webcam o una imagen que se actualice
    currentGardenPhoto.src = 'placeholder-huerto.jpg'; // Placeholder
    lastUpdateDate.textContent = new Date().toLocaleDateString('es-ES', { day: 'numeric', month: 'long', year: 'numeric' }) + ' ' + new Date().toLocaleTimeString('es-ES', { hour: '2-digit', minute: '2-digit' });

    // Función para manejar la compra (AHORA MUESTRA LA FACTURA)
    window.handlePurchase = () => {
        startAppleAnimation(); // Inicia la animación al hacer clic en comprar
        mostrarFactura(); // Muestra la factura después de la animación
    };

    // NUEVA FUNCIÓN: Mostrar la factura
    window.mostrarFactura = () => {
        const facturaOverlay = document.getElementById('factura-overlay');
        if (facturaOverlay) {
            facturaOverlay.style.display = 'flex'; // Cambia a 'flex' para centrar el contenido
        }
    };

    // NUEVA FUNCIÓN: Cerrar la factura
    window.cerrarFactura = () => {
        const facturaOverlay = document.getElementById('factura-overlay');
        if (facturaOverlay) {
            facturaOverlay.style.display = 'none';
        }
    };

    // Datos simulados para las entradas del diario
    const entradasDiario = {
        tiempo: `
            <div class="entrada-item">
                <h3>El tiempo en el huerto: Soleado y con brisa</h3>
                <span class="fecha">25 de Octubre de 2025, 12:30 PM</span>
                <p>Hoy tenemos un día espléndido en el huerto. Temperatura actual: 22°C. Sensación térmica ideal para nuestras plantas. Viento suave del sur a 10 km/h, perfecto para la polinización.</p>
                <p>Pronóstico para mañana: Se esperan algunas nubes por la mañana, pero el sol predominará por la tarde. ¡Condiciones óptimas para el crecimiento!</p>
            </div>
        `,
        tienda: `
              <div class="entrada-item">
                <h3>Notas del agricultor: Cuidado de los manzanos</h3>
                <span class="fecha">24 de Octubre de 2025</span>
                <p>¡Qué alegría ver cómo nuestras manzanas están cogiendo ese color rojo intenso! Hoy hemos estado revisando cada manzano, asegurándonos de que no haya plagas y de que reciban la cantidad de agua necesaria. Este año prometen una cosecha excepcional.</p>
                <p>Aquí os dejo una pequeña foto de lo que he encontrado hoy:</p>
                <div class="image-container">
                    <img id="apple-tree-img" src="arbol_de_manzanas.png" alt="Manzanas en el árbol">
                    <div id="falling-apple" class="falling-apple"></div>
                    <img id="juice-bottle-img" src="botella_de_jugo.png" alt="Botella de jugo de manzana">
                </div>
                <p>Y para refrescarnos después de un largo día en el huerto, nada como un delicioso jugo de manzana. ¡Fresco, natural y directo de nuestras mejores manzanas!</p>
                <p>Refrescante y delicioso, proveniente de lo mejor de nuestro huerto. ¡Puro sabor natural!</p>
                <button class="buy-button" onclick="handlePurchase()">Comprar Jugo de Manzana</button>
            </div>
            
            <div class="entrada-item">
                <h3>Preparando la tierra para los nuevos árboles de manzana</h3>
                <span class="fecha">22 de Octubre de 2025</span>
                <p>Hemos estado enriqueciendo la tierra con compost orgánico. Es fundamental para que nuestros futuros manzanos crezcan fuertes y llenos de sabor. ¡Mucha paciencia y dedicación en cada paso!</p>
            </div>
        `,
        recoleccion: `
            <div class="entrada-item">
                <h3>La recolección de esta semana: Manzanas</h3>
                <span class="fecha">23 de Octubre de 2025</span>
                <p>Esta semana hemos tenido una recolección abundante de manzana, que irán directamente a vuestros jugos. ¡Están en su punto óptimo de maduración, llenas de dulzura!</p>
                <video controls src="Secuencia 01.mp4" poster="portada_del_video.png">Tu navegador no soporta el elemento de video.</video>
                <p>También hemos cosechado unas manzanas increíbles. Crujientes y con un color vibrante.</p>
                <img src="manzana_recoletadas.png" alt="Manzanas recién recolectadas">
            </div>
            <div class="entrada-item">
                <h3>Preparativos para la cosecha de manzanas</h3>
                <span class="fecha">18 de Octubre de 2025</span>
                <p>Aunque no es para jugo directamente, nuestras manzanas de mesa están casi listas. Un buen indicador de la salud general de nuestro huerto.</p>
            </div>
        `
    };

    const contenidoEntrada = document.getElementById('contenido-entrada');
    
    // Nueva función para el autoplay del video
    function autoPlayVideo() {
        // Busca el primer elemento <video> dentro del contenido de la entrada.
        const videoElement = contenidoEntrada.querySelector('video');
        if (videoElement) {
            // El atributo 'autoplay' puede ser bloqueado por los navegadores.
            // Para asegurar la reproducción, usamos el método 'play()'
            // y añadimos 'muted' para cumplir con las políticas de autoplay de la mayoría de los navegadores.
            videoElement.muted = true; // El video debe estar silenciado para el autoplay
            videoElement.play()
                .catch(error => {
                    // Si falla (ej. por políticas de navegador), al menos queda el botón de play
                    console.warn("Autoplay falló (esto es común en navegadores). El usuario tendrá que presionar play.", error);
                    // Opcional: mostrar un mensaje al usuario.
                });
        }
    }

    // Función para mostrar el contenido de una entrada
    window.mostrarEntrada = (tipo) => {
        if (entradasDiario[tipo]) {
            contenidoEntrada.innerHTML = entradasDiario[tipo];
            
            // CAMBIO CLAVE: Llama a la función de autoplay si la entrada es 'recoleccion'
            if (tipo === 'recoleccion') {
                // Pequeño retraso para asegurar que el DOM se actualice antes de buscar el video
                setTimeout(autoPlayVideo, 50); 
            }
        } else {
            contenidoEntrada.innerHTML = `<p>No hay entradas para "${tipo}" en este momento.</p>`;
        }
    };

    function startAppleAnimation() {
        const appleTree = document.getElementById('apple-tree-img');
        const juiceBottle = document.getElementById('juice-bottle-img');
        const fallingApple = document.getElementById('falling-apple');

        // Resetear la posición de la manzana para que se pueda animar múltiples veces
        fallingApple.style.display = 'none';
        fallingApple.style.transform = 'translate(0, 0)';
        fallingApple.style.opacity = '1';

        setTimeout(() => {
            if (!appleTree || !juiceBottle || !fallingApple) {
                console.warn('Elementos de animación no encontrados. Asegúrate de que las IDs son correctas y los elementos existen.');
                return;
            }

            const treeRect = appleTree.getBoundingClientRect();
            const bottleRect = juiceBottle.getBoundingClientRect();
            const containerRect = fallingApple.parentElement.getBoundingClientRect(); // El contenedor de las imágenes

            // Posición inicial de la manzana (arriba del árbol, centrada)
            // Calculamos la posición relativa dentro del contenedor `image-container`
            const startX = (treeRect.left - containerRect.left) + (treeRect.width / 2) - (fallingApple.offsetWidth / 2);
            const startY = (treeRect.top - containerRect.top);

            fallingApple.style.left = `${startX}px`;
            fallingApple.style.top = `${startY}px`;
            fallingApple.style.display = 'block';

            // Posición final de la manzana (arriba de la botella, centrada)
            // Calculamos la posición relativa dentro del contenedor `image-container`
            const endX = (bottleRect.left - containerRect.left) + (bottleRect.width / 2) - (fallingApple.offsetWidth / 2);
            const endY = (bottleRect.top - containerRect.top) + (bottleRect.height / 4); // Cae hacia el cuello de la botella (ajustar si es necesario)


            // Calcular el desplazamiento (delta) desde la posición inicial a la final
            const deltaX = endX - startX;
            const deltaY = endY - startY;

            // Duración de la animación en milisegundos
            const animationDuration = 1500; // Un poco más rápido para una caída directa

            // Animar la caída
            fallingApple.animate([
                { transform: 'translate(0, 0)', opacity: 1 },
                { transform: `translate(${deltaX}px, ${deltaY}px)`, opacity: 0.5 }
            ], {
                duration: animationDuration,
                easing: 'ease-in',
                fill: 'forwards'
            }).onfinish = () => {
                fallingApple.style.display = 'none'; // Ocultar la manzana al final
                fallingApple.style.transform = 'translate(0,0)'; // Reiniciar posición para futuras animaciones
                fallingApple.style.opacity = '1';
            };
        }, 50);
    }
});
