<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Comradeloli - морская вселенная Сони</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(to bottom, #0a1a2a, #0d2b42, #134d6b);
            color: #e0f7ff;
            overflow-x: hidden;
            min-height: 100vh;
            position: relative;
        }
        
        /* Морские пузыри */
        .bubble {
            position: absolute;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            animation: floatUp linear infinite;
            z-index: -1;
        }
        
        @keyframes floatUp {
            0% {
                transform: translateY(100vh) scale(0);
                opacity: 0;
            }
            10% {
                opacity: 0.5;
            }
            90% {
                opacity: 0.5;
            }
            100% {
                transform: translateY(-100px) scale(1.2);
                opacity: 0;
            }
        }
        
        /* Рыбки */
        .fish {
            position: absolute;
            font-size: 2rem;
            animation: swim linear infinite;
            z-index: -1;
            filter: drop-shadow(0 0 3px rgba(0, 255, 255, 0.5));
        }
        
        @keyframes swim {
            0% {
                transform: translateX(-100px) scaleX(1);
            }
            49% {
                transform: translateX(calc(100vw + 100px)) scaleX(1);
            }
            50% {
                transform: translateX(calc(100vw + 100px)) scaleX(-1);
            }
            99% {
                transform: translateX(-100px) scaleX(-1);
            }
            100% {
                transform: translateX(-100px) scaleX(1);
            }
        }
        
        /* Основной контейнер */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 1;
        }
        
        /* Заголовок */
        header {
            text-align: center;
            padding: 40px 20px;
            position: relative;
        }
        
        .logo {
            font-size: 3.5rem;
            margin-bottom: 10px;
            color: #4fc3f7;
            text-shadow: 0 0 15px rgba(79, 195, 247, 0.7);
            letter-spacing: 2px;
        }
        
        .subtitle {
            font-size: 1.2rem;
            color: #80deea;
            margin-bottom: 30px;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            line-height: 1.6;
        }
        
        /* Кнопки ссылок */
        .links {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 20px;
            margin: 40px 0;
        }
        
        .link-btn {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 15px 25px;
            background: linear-gradient(135deg, #0066cc, #0099cc);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 102, 204, 0.4);
            border: 2px solid rgba(255, 255, 255, 0.1);
        }
        
        .link-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 102, 204, 0.6);
            background: linear-gradient(135deg, #0099cc, #00bcd4);
        }
        
        .link-btn i {
            font-size: 1.5rem;
        }
        
        /* Информация о Соне */
        .info-section {
            background: rgba(10, 30, 50, 0.7);
            border-radius: 20px;
            padding: 40px;
            margin: 50px 0;
            border: 1px solid rgba(64, 224, 208, 0.3);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
        }
        
        .info-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, #00bcd4, #0066cc);
        }
        
        .info-title {
            font-size: 2.2rem;
            color: #4fc3f7;
            margin-bottom: 25px;
            text-align: center;
        }
        
        .info-text {
            font-size: 1.3rem;
            line-height: 1.8;
            margin-bottom: 25px;
            text-align: center;
            color: #bbdefb;
        }
        
        .quote {
            font-style: italic;
            font-size: 1.5rem;
            text-align: center;
            padding: 25px;
            margin: 30px 0;
            border-left: 5px solid #00bcd4;
            background: rgba(0, 188, 212, 0.1);
            border-radius: 0 15px 15px 0;
        }
        
        /* Марианская впадина */
        .trench-section {
            margin: 80px 0;
            position: relative;
        }
        
        .section-title {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 40px;
            color: #00bcd4;
            text-shadow: 0 0 10px rgba(0, 188, 212, 0.5);
        }
        
        .trench-container {
            display: flex;
            min-height: 800px;
            position: relative;
        }
        
        .depth-scale {
            width: 100px;
            background: linear-gradient(to bottom, #0066cc, #003366, #000033, #000011);
            border-radius: 10px;
            padding: 20px 10px;
            position: relative;
            box-shadow: 5px 0 15px rgba(0, 0, 0, 0.5);
            margin-right: 30px;
            flex-shrink: 0;
        }
        
        .depth-marker {
            position: absolute;
            left: 0;
            width: 100%;
            text-align: center;
            color: #e0f7ff;
            font-weight: bold;
            padding: 5px;
            border-top: 1px dashed rgba(255, 255, 255, 0.2);
        }
        
        .depth-label {
            background: rgba(0, 0, 0, 0.5);
            padding: 5px 10px;
            border-radius: 5px;
            font-size: 0.9rem;
        }
        
        .trench-content {
            flex-grow: 1;
            background: rgba(0, 20, 40, 0.7);
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            position: relative;
            overflow: hidden;
        }
        
        .depth-level {
            margin-bottom: 100px;
            padding: 25px;
            border-radius: 15px;
            background: rgba(0, 40, 80, 0.5);
            border-left: 5px solid #0097a7;
            position: relative;
            transition: transform 0.3s ease;
        }
        
        .depth-level:hover {
            transform: translateX(10px);
            background: rgba(0, 60, 120, 0.6);
        }
        
        .depth-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .depth-name {
            font-size: 1.8rem;
            color: #00bcd4;
        }
        
        .depth-value {
            font-size: 1.5rem;
            font-weight: bold;
            color: #80deea;
        }
        
        .animals {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-top: 20px;
        }
        
        .animal {
            background: rgba(0, 150, 200, 0.2);
            padding: 15px;
            border-radius: 10px;
            width: calc(33.333% - 14px);
            min-width: 200px;
            border: 1px solid rgba(0, 188, 212, 0.3);
        }
        
        .animal-name {
            font-size: 1.3rem;
            color: #4fc3f7;
            margin-bottom: 8px;
        }
        
        .animal-desc {
            font-size: 1rem;
            color: #bbdefb;
            line-height: 1.5;
        }
        
        /* Секретная пасхалка */
        .easter-egg {
            text-align: center;
            margin: 60px 0;
            padding: 30px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            border: 1px dashed rgba(255, 255, 255, 0.2);
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .easter-egg:hover {
            background: rgba(0, 0, 0, 0.5);
            border: 1px dashed rgba(255, 255, 255, 0.4);
        }
        
        .easter-title {
            font-size: 1.8rem;
            color: #ff9800;
            margin-bottom: 15px;
        }
        
        .easter-text {
            font-size: 1.2rem;
            color: #ffcc80;
            line-height: 1.6;
            display: none;
        }
        
        /* Футер */
        footer {
            text-align: center;
            padding: 40px 20px;
            margin-top: 60px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: #80deea;
            font-size: 1.1rem;
        }
        
        .domain {
            color: #4fc3f7;
            font-weight: bold;
            font-size: 1.3rem;
            letter-spacing: 1px;
        }
        
        /* Адаптивность */
        @media (max-width: 992px) {
            .trench-container {
                flex-direction: column;
            }
            
            .depth-scale {
                width: 100%;
                height: 100px;
                margin-right: 0;
                margin-bottom: 30px;
                background: linear-gradient(to right, #0066cc, #003366, #000033, #000011);
                padding: 10px 20px;
            }
            
            .depth-marker {
                width: auto;
                left: auto;
                top: 0;
                transform: translateX(-50%);
                border-top: none;
                border-left: 1px dashed rgba(255, 255, 255, 0.2);
            }
            
            .animal {
                width: calc(50% - 10px);
            }
        }
        
        @media (max-width: 768px) {
            .logo {
                font-size: 2.5rem;
            }
            
            .links {
                flex-direction: column;
                align-items: center;
            }
            
            .link-btn {
                width: 100%;
                max-width: 300px;
                justify-content: center;
            }
            
            .animal {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <!-- Морские пузыри -->
    <div id="bubbles-container"></div>
    
    <!-- Рыбки -->
    <div id="fish-container"></div>
    
    <div class="container">
        <!-- Заголовок -->
        <header>
            <h1 class="logo">comradeloli</h1>
            <p class="subtitle">Морская вселенная Комраделоли, где глубины интернета встречаются с океанскими безднами</p>
        </header>
        
        <!-- Кнопки ссылок -->
        <div class="links">
            <a href="https://www.donationalerts.com/r/comradeloli" class="link-btn" target="_blank">
                <i class="fas fa-donate"></i>
                <span>Донат</span>
            </a>
            <a href="https://t.me/comradeloli" class="link-btn" target="_blank">
                <i class="fab fa-telegram"></i>
                <span>Телеграмм</span>
            </a>
            <a href="https://fetta.app/u/Comradeloli" class="link-btn" target="_blank">
                <i class="fas fa-star"></i>
                <span>Фетта</span>
            </a>
        </div>
        
        <!-- Информация о Соне -->
        <section class="info-section">
            <h2 class="info-title">О Соне (Comradeloli)</h2>
            <p class="info-text">
                Я Комраделоля/Комраде/или просто Софья. Мне 17, но на самом деле мне уже как 97 лет. 
                Мы должны были дойти до Берлина, но после 26 апреля все как в тумане... и я как-то очутилась здесь.
            </p>
            <div class="quote">"Люблю рыбок. На стримах мы проходим всякие игры, косплеим, завозим в тф2"</div>
            <p class="info-text">
                Присоединяйтесь к подводному миру стримов, где мы исследуем глубины игровых вселенных, 
                перевоплощаемся в любимых персонажей и наслаждаемся компанией как рыбки в коралловом рифе.
            </p>
        </section>
        
        <!-- Марианская впадина -->
        <section class="trench-section">
            <h2 class="section-title">Марианская впадина: Глубины как метафора</h2>
            <div class="trench-container">
                <div class="depth-scale" id="depth-scale">
                    <!-- Маркеры глубины будут добавлены через JS -->
                </div>
                
                <div class="trench-content">
                    <div class="depth-level" style="margin-top: 0;">
                        <div class="depth-header">
                            <h3 class="depth-name">Эпипелагическая зона</h3>
                            <div class="depth-value">0-200 м</div>
                        </div>
                        <p>Солнечная зона, где обитают самые известные и красочные обитатели океана.</p>
                        <div class="animals">
                            <div class="animal">
                                <div class="animal-name">Дельфин</div>
                                <div class="animal-desc">Умные и социальные млекопитающие, любящие играть и общаться.</div>
                            </div>
                            <div class="animal">
                                <div class="animal-name">Клоунская рыба</div>
                                <div class="animal-desc">Яркие рыбки, живущие в симбиозе с актиниями.</div>
                            </div>
                            <div class="animal">
                                <div class="animal-name">Черепаха</div>
                                <div class="animal-desc">Древние морские путешественники, символизирующие мудрость.</div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="depth-level">
                        <div class="depth-header">
                            <h3 class="depth-name">Мезопелагическая зона</h3>
                            <div class="depth-value">200-1000 м</div>
                        </div>
                        <p>Сумеречная зона, куда проникает лишь слабый солнечный свет.</p>
                        <div class="animals">
                            <div class="animal">
                                <div class="animal-name">Гигантский кальмар</div>
                                <div class="animal-desc">Загадочные глубоководные существа, редко попадающиеся на глаза.</div>
                            </div>
                            <div class="animal">
                                <div class="animal-name">Удильщик</div>
                                <div class="animal-desc">Хищник со светящейся приманкой для завлечения добычи.</div>
                            </div>
                            <div class="animal">
                                <div class="animal-name">Глубоководный осьминог</div>
                                <div class="animal-desc">Умные моллюски, приспособившиеся к жизни в темноте.</div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="depth-level">
                        <div class="depth-header">
                            <h3 class="depth-name">Батипелагическая зона</h3>
                            <div class="depth-value">1000-4000 м</div>
                        </div>
                        <p>Полная темнота, высокое давление и низкая температура.</p>
                        <div class="animals">
                            <div class="animal">
                                <div class="animal-name">Рыба-капля</div>
                                <div class="animal-desc">Желеобразная рыба, идеально приспособленная к высокому давлению.</div>
                            </div>
                            <div class="animal">
                                <div class="animal-name">Гренландская акула</div>
                                <div class="animal-desc">Долгожители, живущие до 400 лет в холодных глубинах.</div>
                            </div>
                            <div class="animal">
                                <div class="animal-name">Глубоководный удильщик</div>
                                <div class="animal-desc">Страшные на вид, но удивительно адаптированные хищники.</div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="depth-level">
                        <div class="depth-header">
                            <h3 class="depth-name">Абиссопелагическая зона</h3>
                            <div class="depth-value">4000-6000 м</div>
                        </div>
                        <p>Бездна, где обитают самые необычные и причудливые формы жизни.</p>
                        <div class="animals">
                            <div class="animal">
                                <div class="animal-name">Абиссобротула</div>
                                <div class="animal-desc">Редкая глубоководная рыба, живущая на самом дне.</div>
                            </div>
                            <div class="animal">
                                <div class="animal-name">Глубоководный морской черт</div>
                                <div class="animal-desc">Хищник с огромным ртом и светящейся приманкой.</div>
                            </div>
                            <div class="animal">
                                <div class="animal-name">Псевдолипарис</div>
                                <div class="animal-desc">Рыба, способная выдерживать экстремальное давление.</div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="depth-level">
                        <div class="depth-header">
                            <h3 class="depth-name">Ультраабиссальная зона</h3>
                            <div class="depth-value">6000-11000 м</div>
                        </div>
                        <p>Марианская впадина - самое глубокое место на Земле, символ неизведанного.</p>
                        <div class="animals">
                            <div class="animal">
                                <div class="animal-name">Марианский морской слизень</div>
                                <div class="animal-desc">Существо, приспособившееся к жизни на максимальной глубине.</div>
                            </div>
                            <div class="animal">
                                <div class="animal-name">Амфиподы</div>
                                <div class="animal-desc">Мелкие ракообразные, выживающие в экстремальных условиях.</div>
                            </div>
                            <div class="animal">
                                <div class="animal-name">Фораминиферы</div>
                                <div class="animal-desc">Микроскопические организмы, обитающие даже на дне впадины.</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Пасхалка -->
        <div class="easter-egg" id="easterEgg">
            <h3 class="easter-title">Морская тайна</h3>
            <p class="easter-text" id="easterText">
                Кстати, тот самый WshirikW когда-то оставил след в глубинах этого сайта. 
                Говорят, он был одним из первых исследователей этих вод, но теперь его знают лишь старые карты и легенды. 
                Возможно, он все еще где-то здесь, в самых темных глубинах интернета...
            </p>
            <p><i class="fas fa-anchor"></i> Нажмите, чтобы раскрыть тайну <i class="fas fa-anchor"></i></p>
        </div>
        
        <!-- Футер -->
        <footer>
            <p>Погрузитесь в глубины контента с <span class="domain">comradeloli</span></p>
            <p>© 2023 Морская вселенная Комраделоли. Все глубины защищены.</p>
        </footer>
    </div>

    <script>
        // Создание морских пузырей
        function createBubbles() {
            const bubblesContainer = document.getElementById('bubbles-container');
            const bubbleCount = 30;
            
            for (let i = 0; i < bubbleCount; i++) {
                const bubble = document.createElement('div');
                bubble.classList.add('bubble');
                
                // Случайные размеры и позиции
                const size = Math.random() * 60 + 10;
                const left = Math.random() * 100;
                const duration = Math.random() * 20 + 10;
                const delay = Math.random() * 20;
                
                bubble.style.width = `${size}px`;
                bubble.style.height = `${size}px`;
                bubble.style.left = `${left}%`;
                bubble.style.animationDuration = `${duration}s`;
                bubble.style.animationDelay = `${delay}s`;
                
                bubblesContainer.appendChild(bubble);
            }
        }
        
        // Создание рыбок
        function createFish() {
            const fishContainer = document.getElementById('fish-container');
            const fishTypes = ['🐠', '🐡', '🐟', '🐬', '🦈', '🐋', '🦑', '🐙'];
            const fishCount = 12;
            
            for (let i = 0; i < fishCount; i++) {
                const fish = document.createElement('div');
                fish.classList.add('fish');
                
                // Случайные параметры
                const fishType = fishTypes[Math.floor(Math.random() * fishTypes.length)];
                const size = Math.random() * 2 + 1;
                const top = Math.random() * 80 + 10;
                const duration = Math.random() * 30 + 20;
                const delay = Math.random() * 20;
                
                fish.textContent = fishType;
                fish.style.fontSize = `${size}rem`;
                fish.style.top = `${top}%`;
                fish.style.animationDuration = `${duration}s`;
                fish.style.animationDelay = `${delay}s`;
                
                fishContainer.appendChild(fish);
            }
        }
        
        // Создание шкалы глубины
        function createDepthScale() {
            const depthScale = document.getElementById('depth-scale');
            const depths = [
                {name: "Поверхность", value: "0 м"},
                {name: "Солнечная зона", value: "200 м"},
                {name: "Сумеречная зона", value: "1000 м"},
                {name: "Темная зона", value: "4000 м"},
                {name: "Абиссаль", value: "6000 м"},
                {name: "Ультраабиссаль", value: "11000 м"}
            ];
            
            depths.forEach((depth, index) => {
                const marker = document.createElement('div');
                marker.classList.add('depth-marker');
                
                // Распределяем маркеры равномерно по высоте
                const top = (index / (depths.length - 1)) * 100;
                marker.style.top = `${top}%`;
                
                const label = document.createElement('div');
                label.classList.add('depth-label');
                label.innerHTML = `<strong>${depth.name}</strong><br>${depth.value}`;
                
                marker.appendChild(label);
                depthScale.appendChild(marker);
            });
        }
        
        // Обработка пасхалки
        function setupEasterEgg() {
            const easterEgg = document.getElementById('easterEgg');
            const easterText = document.getElementById('easterText');
            
            easterEgg.addEventListener('click', function() {
                if (easterText.style.display === 'block') {
                    easterText.style.display = 'none';
                } else {
                    easterText.style.display = 'block';
                    // Добавляем случайную рыбку в честь открытия пасхалки
                    const fishTypes = ['🐠', '🐡', '🐟', '🐬', '🦈', '🐋', '🦑', '🐙'];
                    const randomFish = fishTypes[Math.floor(Math.random() * fishTypes.length)];
                    
                    const newFish = document.createElement('div');
                    newFish.classList.add('fish');
                    newFish.textContent = randomFish;
                    newFish.style.fontSize = '2.5rem';
                    newFish.style.top = '50%';
                    newFish.style.animationDuration = '25s';
                    newFish.style.animationDelay = '0s';
                    newFish.style.zIndex = '10';
                    
                    document.getElementById('fish-container').appendChild(newFish);
                    
                    // Удаляем рыбку после завершения анимации
                    setTimeout(() => {
                        newFish.remove();
                    }, 25000);
                }
            });
        }
        
        // Инициализация при загрузке страницы
        document.addEventListener('DOMContentLoaded', function() {
            createBubbles();
            createFish();
            createDepthScale();
            setupEasterEgg();
            
            // Плавная прокрутка для якорей
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function(e) {
                    e.preventDefault();
                    
                    const targetId = this.getAttribute('href');
                    if (targetId === '#') return;
                    
                    const targetElement = document.querySelector(targetId);
                    if (targetElement) {
                        window.scrollTo({
                            top: targetElement.offsetTop - 80,
                            behavior: 'smooth'
                        });
                    }
                });
            });
        });
    </script>
</body>
</html>
