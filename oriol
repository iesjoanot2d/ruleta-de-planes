<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ruleta de Planes Especiales</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="icon" type="image/x-icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>🎁</text></svg>">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --casa-color: #ffb6c1;
            --casa-color-dark: #e8a4af;
            --fuera-color: #98fb98;
            --fuera-color-dark: #7ae87a;
            --text-color: #333;
            --light-bg: #f9f9f9;
            --shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            --border-radius: 16px;
            --bg-color: #f5e9d8;
        }
        
        body {
            background: var(--bg-color);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            color: var(--text-color);
        }
        
        .container {
            max-width: 800px;
            width: 100%;
            background-color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            overflow: hidden;
            padding: 30px;
            text-align: center;
            border: 2px solid #e8d4b9;
        }
        
        header {
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 2px solid #eee;
        }
        
        h1 {
            color: #8b5a2b;
            margin-bottom: 10px;
            font-size: 2.2rem;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
        }
        
        .subtitle {
            color: #a1887f;
            font-size: 1.1rem;
        }
        
        /* Pantallas */
        .screen {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .screen.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Botones de selección */
        .selection-buttons {
            display: flex;
            justify-content: center;
            gap: 25px;
            margin-top: 40px;
            flex-wrap: wrap;
        }
        
        .selection-btn {
            padding: 25px 40px;
            border: none;
            border-radius: var(--border-radius);
            font-size: 1.4rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-width: 220px;
            box-shadow: var(--shadow);
            border: 3px solid transparent;
        }
        
        .selection-btn i {
            font-size: 2.5rem;
            margin-bottom: 15px;
        }
        
        .selection-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
            border-color: rgba(255, 255, 255, 0.5);
        }
        
        .casa-btn {
            background: linear-gradient(135deg, var(--casa-color), #ffccd5);
            color: #7d4a4a;
        }
        
        .casa-btn:hover {
            background: linear-gradient(135deg, var(--casa-color-dark), #ffb3c1);
        }
        
        .fuera-btn {
            background: linear-gradient(135deg, var(--fuera-color), #c6f6d5);
            color: #3a6b3a;
        }
        
        .fuera-btn:hover {
            background: linear-gradient(135deg, var(--fuera-color-dark), #9ae6b4);
        }
        
        /* Ruleta */
        .wheel-container {
            position: relative;
            width: 320px;
            height: 320px;
            margin: 40px auto;
        }
        
        .wheel {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            position: relative;
            overflow: hidden;
            box-shadow: 
                0 0 20px rgba(0, 0, 0, 0.1),
                inset 0 0 20px rgba(0, 0, 0, 0.05);
            border: 10px solid #8b5a2b;
            background: #f8f3e9;
        }
        
        .wheel-item {
            position: absolute;
            width: 50%;
            height: 50%;
            transform-origin: bottom right;
            left: 0;
            top: 0;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 10px;
            text-align: center;
            font-weight: bold;
            color: white;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
            overflow: hidden;
            border-right: 2px solid rgba(255, 255, 255, 0.3);
        }
        
        .wheel-item::after {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 0;
            height: 0;
            border-left: 20px solid transparent;
            border-right: 20px solid white;
            border-top: 20px solid transparent;
            border-bottom: 20px solid white;
            opacity: 0.7;
        }
        
        .wheel-center {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #8b5a2b, #d4a574);
            border-radius: 50%;
            z-index: 10;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 2.5rem;
            box-shadow: 
                0 0 20px rgba(139, 90, 43, 0.3),
                inset 0 0 10px rgba(255, 255, 255, 0.2);
            border: 6px solid #f8f3e9;
        }
        
        .pointer {
            position: absolute;
            top: -25px;
            left: 50%;
            transform: translateX(-50%);
            width: 50px;
            height: 50px;
            z-index: 20;
            color: #e53e3e;
            font-size: 3rem;
            text-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
            filter: drop-shadow(0 4px 6px rgba(0, 0, 0, 0.2));
        }
        
        .spin-btn {
            margin-top: 30px;
            padding: 18px 50px;
            background: linear-gradient(135deg, #8b5a2b, #d4a574);
            color: white;
            border: none;
            border-radius: 50px;
            font-size: 1.3rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 
                0 4px 15px rgba(139, 90, 43, 0.2),
                0 6px 20px rgba(0, 0, 0, 0.1);
            letter-spacing: 1px;
            border: 3px solid #f8f3e9;
        }
        
        .spin-btn:hover {
            background: linear-gradient(135deg, #7a4a23, #c49564);
            transform: translateY(-3px) scale(1.05);
            box-shadow: 
                0 6px 20px rgba(139, 90, 43, 0.3),
                0 8px 25px rgba(0, 0, 0, 0.15);
        }
        
        .spin-btn:disabled {
            background: linear-gradient(135deg, #a1887f, #bcaaa4);
            cursor: not-allowed;
            transform: none;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }
        
        /* Resultado */
        .result-container {
            margin-top: 40px;
            padding: 40px 30px;
            border-radius: var(--border-radius);
            animation: pulse 2s infinite alternate;
            min-height: 300px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, rgba(255, 255, 255, 0.9), rgba(248, 243, 233, 0.9));
            border: 3px solid;
        }
        
        @keyframes pulse {
            0% { 
                box-shadow: 0 0 0 0 rgba(139, 90, 43, 0.4),
                          0 0 30px rgba(139, 90, 43, 0.1);
            }
            100% { 
                box-shadow: 0 0 0 20px rgba(139, 90, 43, 0),
                          0 0 40px rgba(139, 90, 43, 0.2);
            }
        }
        
        .result-icon {
            font-size: 6rem;
            margin-bottom: 25px;
            filter: drop-shadow(0 4px 6px rgba(0, 0, 0, 0.2));
        }
        
        .result-title {
            font-size: 2.8rem;
            margin-bottom: 15px;
            color: #8b5a2b;
            line-height: 1.2;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.1);
        }
        
        .result-plan-name {
            font-size: 3.5rem;
            color: #e53e3e;
            margin: 20px 0;
            line-height: 1.1;
            text-align: center;
            padding: 10px 20px;
            background: rgba(255, 255, 255, 0.7);
            border-radius: 20px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            border: 3px dashed;
        }
        
        /* Mensaje cuando se acaban los planes */
        .no-plans-message {
            font-size: 3.5rem;
            color: #8b5a2b;
            margin: 30px 0;
            line-height: 1.2;
            text-align: center;
            padding: 30px;
            background: linear-gradient(135deg, rgba(255, 182, 193, 0.2), rgba(152, 251, 152, 0.2));
            border-radius: 25px;
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);
            border: 4px dashed #8b5a2b;
            animation: float 3s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        
        .no-plans-icon {
            font-size: 5rem;
            margin-bottom: 20px;
            color: #e53e3e;
        }
        
        .result-buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 50px;
            flex-wrap: wrap;
        }
        
        .action-btn {
            padding: 20px 45px;
            border: none;
            border-radius: 50px;
            font-size: 1.3rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            min-width: 220px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            border: 3px solid transparent;
        }
        
        .retry-btn {
            background: linear-gradient(135deg, #ed8936, #f6ad55);
            color: white;
        }
        
        .retry-btn:hover {
            background: linear-gradient(135deg, #dd6b20, #ed8936);
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 6px 20px rgba(237, 137, 54, 0.3);
            border-color: rgba(255, 255, 255, 0.5);
        }
        
        .accept-btn {
            background: linear-gradient(135deg, #48bb78, #68d391);
            color: white;
        }
        
        .accept-btn:hover {
            background: linear-gradient(135deg, #38a169, #48bb78);
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 6px 20px rgba(72, 187, 120, 0.3);
            border-color: rgba(255, 255, 255, 0.5);
        }
        
        .back-btn {
            background: linear-gradient(135deg, #a0aec0, #cbd5e0);
            color: white;
            margin-top: 25px;
            padding: 15px 35px;
        }
        
        .back-btn:hover {
            background: linear-gradient(135deg, #718096, #a0aec0);
            transform: translateY(-3px);
        }
        
        /* Contador de planes usados */
        .used-plans-counter {
            background: linear-gradient(135deg, #f8f3e9, #f5e9d8);
            border-radius: 25px;
            padding: 12px 25px;
            margin-top: 20px;
            font-size: 1rem;
            color: #8b5a2b;
            display: inline-block;
            border: 2px solid #e8d4b9;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
        }
        
        /* Footer */
        footer {
            margin-top: 40px;
            padding-top: 20px;
            border-top: 2px solid #e8d4b9;
            color: #a1887f;
            font-size: 0.9rem;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .container {
                padding: 20px;
            }
            
            h1 {
                font-size: 1.8rem;
            }
            
            .selection-buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .selection-btn {
                width: 100%;
                max-width: 280px;
                padding: 20px 30px;
            }
            
            .wheel-container {
                width: 280px;
                height: 280px;
            }
            
            .result-plan-name {
                font-size: 2.5rem;
            }
            
            .no-plans-message {
                font-size: 2.5rem;
                padding: 20px;
            }
            
            .result-buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .action-btn {
                width: 100%;
                max-width: 280px;
                padding: 18px 35px;
            }
            
            .pointer {
                font-size: 2.5rem;
                top: -20px;
            }
            
            .wheel-center {
                width: 70px;
                height: 70px;
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1><i class="fas fa-gift"></i> Ruleta de Planes Especiales</h1>
            <p class="subtitle">Elige un tipo de plan y deja que la ruleta decida la aventura de hoy</p>
        </header>
        
        <!-- Pantalla de selección inicial -->
        <div id="selection-screen" class="screen active">
            <h2>¿Qué tipo de plan prefieres hoy?</h2>
            <div class="selection-buttons">
                <button id="casa-btn" class="selection-btn casa-btn">
                    <i class="fas fa-home"></i>
                    Planes en Casa
                </button>
                <button id="fuera-btn" class="selection-btn fuera-btn">
                    <i class="fas fa-tree"></i>
                    Planes Fuera de Casa
                </button>
            </div>
            <p class="subtitle" style="margin-top: 40px;">
                ¡Elige una categoría y gira la ruleta para descubrir tu plan especial!
            </p>
        </div>
        
        <!-- Pantalla de la ruleta -->
        <div id="wheel-screen" class="screen">
            <h2 id="wheel-title">Gira la ruleta para tu plan</h2>
            <div class="wheel-container">
                <div class="pointer">▼</div>
                <div id="wheel" class="wheel"></div>
                <div class="wheel-center">
                    <i class="fas fa-heart"></i>
                </div>
            </div>
            <div id="used-plans-info" class="used-plans-counter" style="display: none;">
                Planes usados: <span id="used-count">0</span>/<span id="total-count">0</span>
            </div>
            <button id="spin-btn" class="spin-btn">¡Girar la ruleta!</button>
            <button id="back-to-selection" class="spin-btn back-btn">Volver a elegir</button>
        </div>
        
        <!-- Pantalla de resultado -->
        <div id="result-screen" class="screen">
            <div id="result-container" class="result-container">
                <!-- Aquí va el resultado normal o el mensaje de "Propón tú el plan" -->
                <div id="normal-result">
                    <div id="result-icon" class="result-icon">🎉</div>
                    <h2 class="result-title">¡Plan seleccionado!</h2>
                    <h3 id="result-plan-name" class="result-plan-name"></h3>
                </div>
                <div id="no-plans-result" style="display: none;">
                    <div class="no-plans-icon">💡</div>
                    <div class="no-plans-message">¡Propón tú el plan!</div>
                    <p style="font-size: 1.5rem; color: #8b5a2b; margin-top: 20px;">
                        Has agotado todos los planes de esta categoría.<br>
                        ¡Ahora es tu turno de sorprender con una idea nueva!
                    </p>
                </div>
            </div>
            
            <div id="used-plans-result" class="used-plans-counter">
                Planes usados en esta sesión: <span id="used-count-result">0</span>
            </div>
            
            <div class="result-buttons">
                <button id="retry-btn" class="action-btn retry-btn">
                    <i class="fas fa-redo"></i> Probar otro plan
                </button>
                <button id="accept-btn" class="action-btn accept-btn">
                    <i class="fas fa-check-circle"></i> Aceptar este plan
                </button>
            </div>
            <button id="back-to-wheel" class="spin-btn back-btn">Volver a la ruleta</button>
        </div>
        
        <footer>
            <p>Hecho con <i class="fas fa-heart" style="color: #e53e3e;"></i> para crear momentos especiales</p>
            <p style="margin-top: 5px;">Cada giro es una nueva aventura</p>
        </footer>
    </div>

    <script>
        // Datos de los planes
        const plans = {
            casa: [
                { name: "Hacer galletas", icon: "🍪", color: "#FF6B6B" },
                { name: "Ver una peli juntos", icon: "🎬", color: "#4ECDC4" },
                { name: "Tarde de Videojuegos o juegos de mesa", icon: "🎮", color: "#FFD166" },
                { name: "Dibujarnos el uno al otro", icon: "🎨", color: "#06D6A0" },
                { name: "Crear figuras de plastelina", icon: "🧱", color: "#118AB2" },
                { name: "Escribir juntos una carta para abrirla dentro de un año", icon: "✉️", color: "#EF476F" },
                { name: "Cantar en karaoke", icon: "🎤", color: "#9D4EDD" },
                { name: "Hacer una pizza casera", icon: "🍕", color: "#FF9E00" }
            ],
            fuera: [
                { name: "Ir a jugar al billar", icon: "🎱", color: "#FF6B6B" },
                { name: "Ir al cine a ver una peli", icon: "🎥", color: "#4ECDC4" },
                { name: "Ir a dar un paseo", icon: "🚶‍♂️", color: "#FFD166" },
                { name: "Ir al museo de las ilusiones", icon: "🖼️", color: "#06D6A0" },
                { name: "Ir a ver el atardecer", icon: "🌅", color: "#118AB2" },
                { name: "Ir a hacernos fotos", icon: "📸", color: "#EF476F" },
                { name: "Competición de a ver quién saca la mejor foto", icon: "🏆", color: "#9D4EDD" },
                { name: "Cenita romántica", icon: "🍷", color: "#FF9E00" },
                { name: "Ruta en bici", icon: "🚴‍♂️", color: "#457B9D" },
                { name: "Picnic en la playa", icon: "🏖️", color: "#F4A261" }
            ]
        };

        // Variables de estado
        let currentCategory = "";
        let currentPlans = [];
        let availablePlans = [];
        let usedPlans = [];
        let selectedPlan = null;
        let wheelSpinning = false;
        let lastTargetRotation = 0;

        // Elementos del DOM
        const selectionScreen = document.getElementById('selection-screen');
        const wheelScreen = document.getElementById('wheel-screen');
        const resultScreen = document.getElementById('result-screen');
        const casaBtn = document.getElementById('casa-btn');
        const fueraBtn = document.getElementById('fuera-btn');
        const wheel = document.getElementById('wheel');
        const spinBtn = document.getElementById('spin-btn');
        const backToSelectionBtn = document.getElementById('back-to-selection');
        const resultIcon = document.getElementById('result-icon');
        const resultPlanName = document.getElementById('result-plan-name');
        const retryBtn = document.getElementById('retry-btn');
        const acceptBtn = document.getElementById('accept-btn');
        const backToWheelBtn = document.getElementById('back-to-wheel');
        const wheelTitle = document.getElementById('wheel-title');
        const usedPlansInfo = document.getElementById('used-plans-info');
        const usedCount = document.getElementById('used-count');
        const totalCount = document.getElementById('total-count');
        const usedCountResult = document.getElementById('used-count-result');
        const usedPlansResult = document.getElementById('used-plans-result');
        const normalResult = document.getElementById('normal-result');
        const noPlansResult = document.getElementById('no-plans-result');

        // Inicializar la ruleta
        function initWheel(category) {
            currentCategory = category;
            currentPlans = plans[category];
            usedPlans = [];
            availablePlans = [...currentPlans];
            lastTargetRotation = 0;
            
            updateUsedPlansCounter();
            
            wheel.innerHTML = '';
            wheel.style.transition = 'none';
            wheel.style.transform = 'rotate(0deg)';
            
            // Forzar reflow para resetear animaciones
            void wheel.offsetWidth;
            
            // Configurar título
            wheelTitle.textContent = category === 'casa' ? 'Planes en Casa' : 'Planes Fuera de Casa';
            
            // Calcular ángulo para cada segmento
            const anglePerItem = 360 / currentPlans.length;
            
            // Crear segmentos de la ruleta
            currentPlans.forEach((plan, index) => {
                const segment = document.createElement('div');
                segment.className = 'wheel-item';
                segment.dataset.index = index;
                segment.title = plan.name;
                
                // Posicionar el segmento
                const rotateAngle = index * anglePerItem;
                segment.style.transform = `rotate(${rotateAngle}deg)`;
                segment.style.background = `linear-gradient(135deg, ${plan.color}, ${darkenColor(plan.color, 20)})`;
                
                wheel.appendChild(segment);
            });
            
            // Restaurar transición
            wheel.style.transition = 'transform 3s cubic-bezier(0.17, 0.67, 0.22, 0.99)';
            
            // Mostrar info de planes usados
            usedPlansInfo.style.display = 'block';
            
            // Resetear botón de girar
            spinBtn.disabled = false;
            spinBtn.textContent = '¡Girar la ruleta!';
        }

        // Función para oscurecer color
        function darkenColor(color, percent) {
            let r = parseInt(color.slice(1, 3), 16);
            let g = parseInt(color.slice(3, 5), 16);
            let b = parseInt(color.slice(5, 7), 16);
            
            r = Math.floor(r * (100 - percent) / 100);
            g = Math.floor(g * (100 - percent) / 100);
            b = Math.floor(b * (100 - percent) / 100);
            
            return `#${r.toString(16).padStart(2, '0')}${g.toString(16).padStart(2, '0')}${b.toString(16).padStart(2, '0')}`;
        }

        // Actualizar contador de planes usados
        function updateUsedPlansCounter() {
            usedCount.textContent = usedPlans.length;
            totalCount.textContent = currentPlans.length;
            usedCountResult.textContent = usedPlans.length;
            
            usedPlansResult.style.display = usedPlans.length > 0 ? 'block' : 'none';
        }

        // Girar la ruleta
        function spinWheel() {
            if (wheelSpinning || availablePlans.length === 0) return;
            
            wheelSpinning = true;
            spinBtn.disabled = true;
            spinBtn.textContent = 'Girando...';
            
            // Si no quedan planes disponibles, mostrar mensaje especial
            if (availablePlans.length === 0) {
                showNoPlansMessage();
                return;
            }
            
            // Elegir un plan aleatorio
            const randomIndex = Math.floor(Math.random() * availablePlans.length);
            const selectedPlanObj = availablePlans[randomIndex];
            
            // Encontrar índice original
            const originalIndex = currentPlans.findIndex(plan => plan.name === selectedPlanObj.name);
            
            // Mover de disponibles a usados
            availablePlans.splice(randomIndex, 1);
            usedPlans.push(selectedPlanObj);
            
            // Calcular ángulo para la animación
            const anglePerItem = 360 / currentPlans.length;
            
            // 5 vueltas completas + posición del segmento + mitad del segmento + extra
            const fullRotations = 5;
            const segmentCenter = (originalIndex * anglePerItem) + (anglePerItem / 2);
            const extraDegrees = 30;
            
            // Calculamos la rotación total sumando a la rotación anterior
            const additionalRotation = (fullRotations * 360) + segmentCenter + extraDegrees;
            lastTargetRotation += additionalRotation;
            
            // Aplicar animación
            wheel.style.transform = `rotate(${lastTargetRotation}deg)`;
            
            // Después de la animación, mostrar resultado
            setTimeout(() => {
                selectedPlan = selectedPlanObj;
                showResult();
                wheelSpinning = false;
                
                updateUsedPlansCounter();
                
                // Si no quedan planes, mostrar mensaje especial en el botón
                if (availablePlans.length === 0) {
                    spinBtn.disabled = true;
                    spinBtn.textContent = '¡Todos los planes usados!';
                } else {
                    spinBtn.disabled = false;
                    spinBtn.textContent = '¡Girar la ruleta!';
                }
            }, 3000);
        }

        // Mostrar resultado normal
        function showResult() {
            // Mostrar resultado normal y ocultar mensaje especial
            normalResult.style.display = 'block';
            noPlansResult.style.display = 'none';
            
            wheelScreen.classList.remove('active');
            resultScreen.classList.add('active');
            
            resultIcon.textContent = selectedPlan.icon;
            resultPlanName.textContent = selectedPlan.name;
            
            const resultContainer = document.getElementById('result-container');
            resultContainer.style.backgroundColor = `${selectedPlan.color}15`;
            resultContainer.style.borderColor = selectedPlan.color;
            resultPlanName.style.borderColor = selectedPlan.color;
        }

        // Mostrar mensaje cuando no hay planes
        function showNoPlansMessage() {
            // Mostrar mensaje especial y ocultar resultado normal
            normalResult.style.display = 'none';
            noPlansResult.style.display = 'block';
            
            wheelScreen.classList.remove('active');
            resultScreen.classList.add('active');
            
            const resultContainer = document.getElementById('result-container');
            resultContainer.style.backgroundColor = 'rgba(139, 90, 43, 0.1)';
            resultContainer.style.borderColor = '#8b5a2b';
            
            wheelSpinning = false;
            updateUsedPlansCounter();
        }

        // Volver a girar
        function retrySpin() {
            // Si no quedan planes, mostrar mensaje especial
            if (availablePlans.length === 0) {
                showNoPlansMessage();
                return;
            }
            
            // Primero volver a la pantalla de la ruleta
            resultScreen.classList.remove('active');
            wheelScreen.classList.add('active');
            
            // Pequeña pausa para que la transición se complete
            setTimeout(() => {
                if (availablePlans.length > 0 && !wheelSpinning) {
                    spinWheel();
                }
            }, 50);
        }

        // Aceptar plan
        function acceptPlan() {
            let message;
            
            if (availablePlans.length === 0 && usedPlans.length === currentPlans.length) {
                // Si se acepta cuando no hay planes
                message = `¡Excelente idea!\n\n¡Propón tú un plan original y sorprende!\n\n¡Que tengáis un día maravilloso! ❤️`;
            } else {
                // Resultado normal
                message = `¡Plan aceptado!\n\n"${selectedPlan.name}"\n\n¡Que tengáis un día maravilloso! ❤️`;
            }
            
            alert(message);
            
            // Reiniciar todo
            usedPlans = [];
            availablePlans = [...currentPlans];
            lastTargetRotation = 0;
            updateUsedPlansCounter();
            
            // Resetear ruleta
            wheel.style.transition = 'none';
            wheel.style.transform = 'rotate(0deg)';
            
            // Forzar reflow
            void wheel.offsetWidth;
            
            // Restaurar transición
            wheel.style.transition = 'transform 3s cubic-bezier(0.17, 0.67, 0.22, 0.99)';
            
            // Volver a inicio
            resultScreen.classList.remove('active');
            selectionScreen.classList.add('active');
            
            // Resetear botón
            spinBtn.disabled = false;
            spinBtn.textContent = '¡Girar la ruleta!';
        }

        // Event Listeners
        casaBtn.addEventListener('click', () => {
            initWheel('casa');
            selectionScreen.classList.remove('active');
            wheelScreen.classList.add('active');
        });

        fueraBtn.addEventListener('click', () => {
            initWheel('fuera');
            selectionScreen.classList.remove('active');
            wheelScreen.classList.add('active');
        });

        spinBtn.addEventListener('click', spinWheel);
        
        backToSelectionBtn.addEventListener('click', () => {
            wheelScreen.classList.remove('active');
            selectionScreen.classList.add('active');
        });

        retryBtn.addEventListener('click', retrySpin);
        
        acceptBtn.addEventListener('click', acceptPlan);
        
        backToWheelBtn.addEventListener('click', () => {
            resultScreen.classList.remove('active');
            wheelScreen.classList.add('active');
        });

        // Inicializar
        initWheel('casa');
    </script>
</body>
</html>
