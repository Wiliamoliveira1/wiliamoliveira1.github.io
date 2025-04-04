<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BiofabricaRobot - Robô SCARA para Biofabricação</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #8a2be2;
            --secondary: #00ffff;
            --accent: #ff00ff;
            --dark: #1a1a2e;
            --light: #f8f9fa;
        }
        
        body {
            background: linear-gradient(135deg, var(--primary), var(--dark));
            color: var(--light);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            line-height: 1.6;
        }
        
        header {
            background: rgba(0, 0, 0, 0.85);
            padding: 1.5rem;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        h1 {
            margin: 0;
            font-size: 2.2rem;
            background: linear-gradient(to right, var(--accent), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 1px;
        }
        
        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1.5rem;
        }
        
        .product-display {
            display: grid;
            grid-template-columns: 1fr;
            gap: 2rem;
        }
        
        @media (min-width: 992px) {
            .product-display {
                grid-template-columns: 1.5fr 1fr;
            }
        }
        
        .carousel {
            background: rgba(0, 0, 0, 0.7);
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4);
            position: relative;
            height: 400px;
        }
        
        .carousel-inner {
            display: flex;
            transition: transform 0.5s ease;
            height: 100%;
        }
        
        .carousel-item {
            min-width: 100%;
            height: 100%;
        }
        
        .carousel-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .carousel-control {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(0, 0, 0, 0.5);
            color: white;
            border: none;
            padding: 1rem;
            cursor: pointer;
            z-index: 10;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s;
        }
        
        .carousel-control:hover {
            background: var(--accent);
        }
        
        .prev {
            left: 1rem;
        }
        
        .next {
            right: 1rem;
        }
        
        .product-info {
            background: rgba(0, 0, 0, 0.7);
            border-radius: 12px;
            padding: 2rem;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4);
        }
        
        .price-section {
            text-align: center;
            margin-bottom: 2rem;
            padding-bottom: 1.5rem;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .price {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--secondary);
            margin: 0.5rem 0;
        }
        
        .price small {
            font-size: 1rem;
            color: rgba(255, 255, 255, 0.7);
        }
        
        .highlight-badge {
            display: inline-block;
            background: var(--accent);
            color: white;
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.9rem;
            margin-bottom: 1rem;
            font-weight: 600;
        }
        
        .features-list {
            margin: 1.5rem 0;
        }
        
        .features-list li {
            margin-bottom: 0.8rem;
            position: relative;
            padding-left: 1.8rem;
        }
        
        .features-list li:before {
            content: "✓";
            color: var(--secondary);
            position: absolute;
            left: 0;
            font-weight: bold;
        }
        
        .btn {
            display: inline-block;
            background: linear-gradient(135deg, var(--accent), var(--primary));
            color: white;
            padding: 1rem 2rem;
            border: none;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            text-align: center;
            text-decoration: none;
            transition: all 0.3s;
            box-shadow: 0 4px 15px rgba(138, 43, 226, 0.4);
            width: 100%;
            margin-top: 1rem;
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(138, 43, 226, 0.6);
        }
        
        .btn i {
            margin-left: 0.5rem;
        }
        
        .tabs-section {
            background: rgba(0, 0, 0, 0.7);
            border-radius: 12px;
            margin-top: 2rem;
            padding: 1.5rem;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4);
        }
        
        .tabs {
            display: flex;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 1.5rem;
        }
        
        .tab-btn {
            padding: 0.8rem 1.5rem;
            background: none;
            border: none;
            color: rgba(255, 255, 255, 0.7);
            font-weight: 600;
            cursor: pointer;
            position: relative;
            transition: all 0.3s;
        }
        
        .tab-btn.active {
            color: var(--secondary);
        }
        
        .tab-btn.active:after {
            content: '';
            position: absolute;
            bottom: -1px;
            left: 0;
            width: 100%;
            height: 2px;
            background: var(--secondary);
        }
        
        .tab-content {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .specs-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 1.5rem;
        }
        
        .spec-item {
            background: rgba(255, 255, 255, 0.05);
            padding: 1rem;
            border-radius: 8px;
        }
        
        .spec-item h4 {
            margin-top: 0;
            color: var(--secondary);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            padding-bottom: 0.5rem;
        }
        
        footer {
            text-align: center;
            padding: 2rem;
            background: rgba(0, 0, 0, 0.8);
            margin-top: 3rem;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Animations */
        .pulse {
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
    </style>
</head>
<body>
    <header>
        <h1>BiofabricaRobot</h1>
    </header>
    
    <div class="container">
        <div class="product-display">
            <!-- Carrossel de Fotos -->
            <div class="carousel">
                <div class="carousel-inner">
                    <div class="carousel-item">
                        <img src="https://source.unsplash.com/random/800x500/?robot,scara" alt="Robô SCARA">
                    </div>
                    <div class="carousel-item">
                        <img src="https://source.unsplash.com/random/800x500/?3dprinter" alt="Tecnologia de Impressão">
                    </div>
                    <div class="carousel-item">
                        <img src="https://source.unsplash.com/random/800x500/?bioprinting" alt="Biofabricação">
                    </div>
                </div>
                <button class="carousel-control prev" onclick="moveSlide(-1)">❮</button>
                <button class="carousel-control next" onclick="moveSlide(1)">❯</button>
            </div>
            
            <!-- Informações do Produto -->
            <div class="product-info">
                <div class="price-section">
                    <span class="highlight-badge pulse">Tecnologia Avançada</span>
                    <h2>Robô SCARA para Biofabricação</h2>
                    <div class="price">R$ 250.000,00 <small>à vista</small></div>
                    <p>ou 12x de R$ 22.500,00 sem juros</p>
                </div>
                
                <div class="features-list">
                    <h3>Principais Recursos:</h3>
                    <ul>
                        <li>Alta precisão de repetição (0.031 mm)</li>
                        <li>Melt Electrowriting (MEW)</li>
                        <li>Biompressão 3D e eletrofiação</li>
                        <li>Interface web integrada</li>
                        <li>Controle via gamepad</li>
                        <li>Open Source (FluidNC)</li>
                    </ul>
                </div>
                
                <a href="#contact" class="btn">Solicitar Orçamento <i class="fas fa-paper-plane"></i></a>
            </div>
        </div>
        
        <!-- Abas de Detalhes -->
        <div class="tabs-section">
            <div class="tabs">
                <button class="tab-btn active" onclick="openTab('tab1', this)">Especificações</button>
                <button class="tab-btn" onclick="openTab('tab2', this)">Aplicações</button>
                <button class="tab-btn" onclick="openTab('tab3', this)">Sobre o Projeto</button>
            </div>
            
            <div id="tab1" class="tab-content active">
                <div class="specs-grid">
                    <div class="spec-item">
                        <h4>Hardware</h4>
                        <p><strong>Microcontrolador:</strong> 32bits </p>
                        <p><strong>Drivers:</strong> Avançado</p>
                        <p><strong>Encoders:</strong> 14 bits</p>
                    </div>
                    <div class="spec-item">
                        <h4>Desempenho</h4>
                        <p><strong>Área de trabalho:</strong> 800mm</p>
                        <p><strong>Precisão:</strong> 0.031mm</p>
                        <p><strong>Velocidade:</strong> 200mm/s</p>
                    </div>
                    <div class="spec-item">
                        <h4>Conexões</h4>
                        <p><strong>WiFi:</strong> 802.11 b/g/n</p>
                        <p><strong>CANbus:</strong> Integrado</p>
                        <p><strong>USB:</strong> Tipo C</p>
                    </div>
                    <div class="spec-item">
                        <h4>Energia</h4>
                        <p><strong>Alimentação:</strong> 24VDC</p>
                        <p><strong>Consumo:</strong> 150W</p>
                        <p><strong>Autonomia:</strong> 8h</p>
                    </div>
                </div>
            </div>
            
            <div id="tab2" class="tab-content">
                <h3>Aplicações Avançadas</h3>
                <p>O BiofabricaRobot é SCARA (Selective Compliance Assembly Robot Arm) é um robô industrial com braço articulado que imita o movimento do braço humano. É um robô de montagem de conformidade seletiva, 
versátil e pode ser utilizado em diversas aplicações de biofabricação:</p>
                
                <div class="specs-grid">
                    <div class="spec-item">
                        <h4><i class="fas fa-biohazard"></i> Engenharia Tecidual</h4>
                        <p>Fabricação de scaffolds para regeneração de tecidos com alta precisão.</p>
                    </div>
                    <div class="spec-item">
                        <h4><i class="fas fa-flask"></i> Pesquisa Biomédica</h4>
                        <p>Desenvolvimento de modelos celulares 3D para testes de drogas.</p>
                    </div>
                    <div class="spec-item">
                        <h4><i class="fas fa-robot"></i> Automação Laboratorial</h4>
                        <p>Integração com sistemas automatizados para alta produtividade.</p>
                    </div>
                    <div class="spec-item">
                        <h4><i class="fas fa-graduation-cap"></i> Educação</h4>
                        <p>Ferramenta didática para ensino de biofabricação e robótica.</p>
                    </div>
                </div>
            </div>
            
            <div id="tab3" class="tab-content">
                <h3>Tecnologia Open Source</h3>
                <p>O BiofabricaRobot que permite total customização:</p>
                
                <div class="specs-grid">
                    <div class="spec-item">
                        <h4><i class="fab fa-github"></i> Robô</h4>
                        <p>Sistema robótico modular para automação de tarefas complexas com alta flexibilidade.</p>
                    </div>
                    <div class="spec-item">
                        <h4><i class="fas fa-code"></i> FluidNC</h4>
                        <p>Controlador CNC de código aberto para operações de alta precisão.</p>
                    </div>
                </div>
                
                <h3 style="margin-top: 2rem;">Vantagens do Open Source</h3>
                <ul class="features-list">
                    <li>Total transparência no funcionamento</li>
                    <li>Customização ilimitada</li>
                    <li>Comunidade ativa de desenvolvedores</li>
                    <li>Atualizações constantes</li>
                    <li>Redução de custos com licenças</li>
                </ul>
            </div>
        </div>
        
        <!-- Seção de Contato -->
        <div id="contact" class="tabs-section" style="margin-top: 2rem;">
            <h2 style="text-align: center; margin-bottom: 1.5rem;">Entre em Contato</h2>
            <form style="max-width: 600px; margin: 0 auto;">
                <div style="margin-bottom: 1rem;">
                    <label style="display: block; margin-bottom: 0.5rem;">Nome</label>
                    <input type="text" style="width: 100%; padding: 0.8rem; border-radius: 8px; border: none; background: rgba(255,255,255,0.1); color: white;">
                </div>
                <div style="margin-bottom: 1rem;">
                    <label style="display: block; margin-bottom: 0.5rem;">Email</label>
                    <input type="email" style="width: 100%; padding: 0.8rem; border-radius: 8px; border: none; background: rgba(255,255,255,0.1); color: white;">
                </div>
                <div style="margin-bottom: 1.5rem;">
                    <label style="display: block; margin-bottom: 0.5rem;">Mensagem</label>
                    <textarea rows="4" style="width: 100%; padding: 0.8rem; border-radius: 8px; border: none; background: rgba(255,255,255,0.1); color: white;"></textarea>
                </div>
                <button type="submit" class="btn">Enviar Mensagem <i class="fas fa-paper-plane"></i></button>
            </form>
        </div>
    </div>
    
    <footer>
        <p>© 2025 Biofabricarobot - Todos os direitos reservados</p>
        <p style="margin-top: 0.5rem; font-size: 0.9rem; color: rgba(255,255,255,0.6);">
            Desenvolvido com ❤️ para a biofabricação
        </p>
    </footer>

    <script>
        // Carrossel
        let currentSlide = 0;
        const slides = document.querySelectorAll('.carousel-item');
        const totalSlides = slides.length;
        
        function moveSlide(direction) {
            currentSlide += direction;
            if (currentSlide >= totalSlides) currentSlide = 0;
            if (currentSlide < 0) currentSlide = totalSlides - 1;
            
            document.querySelector('.carousel-inner').style.transform = `translateX(-${currentSlide * 100}%)`;
        }
        
        // Auto-rotate carousel
        setInterval(() => moveSlide(1), 5000);
        
        // Tabs
        function openTab(tabId, element) {
            // Remove active class from all tabs and contents
            document.querySelectorAll('.tab-btn').forEach(tab => {
                tab.classList.remove('active');
            });
            document.querySelectorAll('.tab-content').forEach(content => {
                content.classList.remove('active');
            });
            
            // Add active class to clicked tab and corresponding content
            element.classList.add('active');
            document.getElementById(tabId).classList.add('active');
        }
    </script>
</body>
</html>
