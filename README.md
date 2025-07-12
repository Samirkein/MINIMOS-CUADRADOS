<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SERVIMEX - Soluciones Industriales</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        header {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 1rem 0;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 2rem;
            font-weight: bold;
            color: white;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            transition: all 0.3s ease;
            padding: 0.5rem 1rem;
            border-radius: 25px;
        }

        .nav-links a:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        main {
            margin-top: 80px;
        }

        .hero {
            text-align: center;
            padding: 4rem 0;
            color: white;
            background: linear-gradient(135deg, rgba(102, 126, 234, 0.9), rgba(118, 75, 162, 0.9)), 
                        url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 600"><defs><pattern id="mining" patternUnits="userSpaceOnUse" width="100" height="100"><rect width="100" height="100" fill="%23f0f0f0"/><circle cx="50" cy="50" r="20" fill="%23e0e0e0"/></pattern></defs><rect width="1200" height="600" fill="url(%23mining)"/></svg>');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(135deg, rgba(102, 126, 234, 0.8), rgba(118, 75, 162, 0.8));
            z-index: 1;
        }

        .hero-content {
            position: relative;
            z-index: 2;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
        }

        .hero-text {
            text-align: left;
        }

        .hero-visual {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 2rem;
        }

        .location-card {
            background: rgba(255, 255, 255, 0.95);
            color: #333;
            padding: 1.5rem;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            max-width: 300px;
        }

        .location-header {
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            color: white;
            padding: 0.8rem 1.2rem;
            border-radius: 10px;
            margin-bottom: 1rem;
            font-weight: bold;
            text-align: center;
        }

        .arequipa-map {
            background: #e8f4fd;
            padding: 1.5rem;
            border-radius: 10px;
            margin-bottom: 1rem;
            text-align: center;
            border: 2px solid #667eea;
        }

        .map-title {
            font-weight: bold;
            color: #2c3e50;
            margin-bottom: 1rem;
        }

        .map-districts {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 0.5rem;
            font-size: 0.9rem;
        }

        .district {
            background: #667eea;
            color: white;
            padding: 0.3rem 0.6rem;
            border-radius: 5px;
            text-align: center;
        }

        .district.highlight {
            background: #ff6b6b;
            animation: pulse 2s infinite;
        }

        .workers-image {
            width: 100%;
            height: 200px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.2rem;
            text-align: center;
            padding: 1rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        @media (max-width: 768px) {
            .hero-content {
                grid-template-columns: 1fr;
                text-align: center;
            }
            
            .hero-text {
                text-align: center;
            }
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.3);
            animation: fadeInUp 1s ease-out;
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
            animation: fadeInUp 1s ease-out 0.3s both;
        }

        .cta-button {
            display: inline-block;
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
            color: white;
            padding: 1rem 2rem;
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            animation: fadeInUp 1s ease-out 0.6s both;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
        }

        .section {
            padding: 4rem 0;
            background: white;
            margin: 2rem 0;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        .section h2 {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 3rem;
            color: #2c3e50;
            position: relative;
        }

        .section h2::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            border-radius: 2px;
        }

        .experience-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .stat-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            transform: translateY(0);
            transition: transform 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-5px);
        }

        .stat-number {
            font-size: 3rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        .stat-label {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .service-card {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            border: 1px solid #eee;
        }

        .service-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
        }

        .service-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            color: #667eea;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 80px;
        }

        .service-icon svg {
            width: 60px;
            height: 60px;
            fill: #667eea;
        }

        .service-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: #2c3e50;
        }

        .service-card p {
            color: #666;
            line-height: 1.6;
        }

        .vision-mission {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 3rem;
            margin-top: 2rem;
        }

        .vision-card, .mission-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 2.5rem;
            border-radius: 15px;
            text-align: center;
        }

        .vision-card h3, .mission-card h3 {
            font-size: 1.8rem;
            margin-bottom: 1rem;
        }

        .values-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .value-item {
            background: #f8f9fa;
            padding: 1.5rem;
            border-radius: 10px;
            text-align: center;
            border-left: 4px solid #667eea;
        }

        .value-item h4 {
            color: #2c3e50;
            margin-bottom: 0.5rem;
        }

        footer {
            background: #2c3e50;
            color: white;
            text-align: center;
            padding: 2rem 0;
            margin-top: 3rem;
        }

        .sectors-section {
            background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
            color: white;
            padding: 4rem 0;
            margin: 2rem 0;
            border-radius: 20px;
        }

        .sectors-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .sector-item {
            background: rgba(255, 255, 255, 0.1);
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            transition: transform 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .sector-item:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.15);
        }

        .cleaning-services {
            margin-top: 1.5rem;
            display: flex;
            flex-direction: column;
            gap: 0.8rem;
        }

        .cleaning-item {
            display: flex;
            align-items: center;
            gap: 0.8rem;
            padding: 0.5rem;
            background: #f8f9fa;
            border-radius: 8px;
            border-left: 3px solid #667eea;
            transition: all 0.3s ease;
        }

        .cleaning-item:hover {
            background: #e9ecef;
            transform: translateX(5px);
        }

        .cleaning-icon {
            font-size: 1.2rem;
            min-width: 24px;
        }

        .expanded-card {
            grid-column: span 2;
        }

        @media (max-width: 968px) {
            .expanded-card {
                grid-column: span 1;
            }
        }
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .hero p {
                font-size: 1.1rem;
            }
            
            .nav-links {
                display: none;
            }
            
            .services-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <header>
        <nav class="container">
            <div class="logo">SERVIMEX</div>
            <ul class="nav-links">
                <li><a href="#inicio">Inicio</a></li>
                <li><a href="#servicios">Servicios</a></li>
                <li><a href="#nosotros">Nosotros</a></li>
                <li><a href="#contacto">Contacto</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section class="hero" id="inicio">
            <div class="container">
                <div class="hero-content">
                    <div class="hero-text">
                        <h1>SERVIMEX</h1>
                        <p>Soluciones industriales con más de 15 años de experiencia en minería, pesquería, agroindustrial, energía y alimentaria. Planificamos y ejecutamos proyectos eléctricos, mecánicos, civiles e ingenierías con valor agregado.</p>
                        <a href="#servicios" class="cta-button">Descubre Nuestros Servicios</a>
                    </div>
                    <div class="hero-visual">
                        <div class="location-card">
                            <div class="location-header">
                                (PAMPA MALAMBRICA)<br>
                                Nuevo Ilo Mz. 15 Lt. 18
                            </div>
                            <div class="arequipa-map">
                                <div class="map-title">AREQUIPA</div>
                                <div class="map-districts">
                                    <div class="district">GENERAL SÁNCHEZ CERRO</div>
                                    <div class="district highlight">PUNO</div>
                                    <div class="district">MOQUEGUA</div>
                                    <div class="district">TACNA</div>
                                    <div class="district">ILO</div>
                                </div>
                            </div>
                        </div>
                        <div class="workers-image">
                            <div>
                                <strong>Personal Especializado</strong><br>
                                Equipo de profesionales capacitados en seguridad industrial y protocolos de calidad para proyectos mineros e industriales
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class="section" id="experiencia">
            <div class="container">
                <h2>Nuestra Experiencia</h2>
                <div class="experience-stats">
                    <div class="stat-card">
                        <div class="stat-number">15+</div>
                        <div class="stat-label">Años de Experiencia</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">5+</div>
                        <div class="stat-label">Sectores Industriales</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">100%</div>
                        <div class="stat-label">Compromiso con la Calidad</div>
                    </div>
                </div>
            </div>
        </section>

        <section class="section" id="servicios">
            <div class="container">
                <h2>Nuestros Servicios</h2>
                <div class="services-grid">
                    <div class="service-card">
                        <div class="service-icon">
                            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M12 2L2 7V10C2 16 6 20.5 12 22C18 20.5 22 16 22 10V7L12 2Z" stroke="#667eea" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                                <path d="M8 11L11 14L16 9" stroke="#667eea" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                            </svg>
                        </div>
                        <h3>Obras Civiles en General</h3>
                        <p>Construcción integral incluyendo zapatas, vigas, columnas, tarrajeo, pisos, losas. Especialistas en remodelación y ampliación de estructuras.</p>
                    </div>
                    <div class="service-card">
                        <div class="service-icon">
                            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M14.7 6.3C15.1 5.9 15.1 5.3 14.7 4.9C14.3 4.5 13.7 4.5 13.3 4.9L12 6.2L10.7 4.9C10.3 4.5 9.7 4.5 9.3 4.9C8.9 5.3 8.9 5.9 9.3 6.3L10.6 7.6L9.3 8.9C8.9 9.3 8.9 9.9 9.3 10.3C9.7 10.7 10.3 10.7 10.7 10.3L12 9L13.3 10.3C13.7 10.7 14.3 10.7 14.7 10.3C15.1 9.9 15.1 9.3 14.7 8.9L13.4 7.6L14.7 6.3Z" fill="#667eea"/>
                                <path d="M3 15H21V17H3V15Z" fill="#667eea"/>
                                <path d="M5 19H19V21H5V19Z" fill="#667eea"/>
                                <path d="M12 12V22" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                                <path d="M8 12V22" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                                <path d="M16 12V22" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                            </svg>
                        </div>
                        <h3>Metal Mecánica</h3>
                        <p>Servicios especializados en estructuras metálicas, fabricación de piezas mecánicas y soluciones industriales personalizadas.</p>
                    </div>
                    <div class="service-card">
                        <div class="service-icon">
                            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M12 22C17.5228 22 22 17.5228 22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22Z" stroke="#667eea" stroke-width="2"/>
                                <path d="M8 12L11 15L16 9" stroke="#667eea" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                                <path d="M12 6V2" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                                <path d="M12 22V18" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                                <path d="M4.93 4.93L7.76 7.76" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                                <path d="M16.24 16.24L19.07 19.07" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                            </svg>
                        </div>
                        <h3>Gestión Ambiental</h3>
                        <p>Implementación de sistemas de gestión ambiental, responsabilidad social empresarial y desarrollo sostenible.</p>
                    </div>
                    <div class="service-card expanded-card">
                        <div class="service-icon">
                            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M12 2L13.09 8.26L19 7L14.74 12.26L21 13.09L14.74 18.35L19 17L13.09 15.74L12 22L10.91 15.74L5 17L9.26 11.74L3 10.91L9.26 5.65L5 7L10.91 8.26L12 2Z" stroke="#667eea" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                                <circle cx="12" cy="12" r="3" stroke="#667eea" stroke-width="2"/>
                            </svg>
                        </div>
                        <h3>Limpieza en General</h3>
                        <p>Servicios de limpieza especializados para instalaciones industriales con personal capacitado y equipos de alta tecnología.</p>
                        <div class="cleaning-services">
                            <div class="cleaning-item">
                                <span class="cleaning-icon">🏭</span>
                                <span>Limpieza de plantas industriales</span>
                            </div>
                            <div class="cleaning-item">
                                <span class="cleaning-icon">🔧</span>
                                <span>Limpieza de plantas concentradoras</span>
                            </div>
                            <div class="cleaning-item">
                                <span class="cleaning-icon">🧪</span>
                                <span>Limpieza de tanques y tuberías de ácido</span>
                            </div>
                            <div class="cleaning-item">
                                <span class="cleaning-icon">⚡</span>
                                <span>Limpieza de relaves</span>
                            </div>
                            <div class="cleaning-item">
                                <span class="cleaning-icon">🌊</span>
                                <span>Limpieza de sumideros</span>
                            </div>
                            <div class="cleaning-item">
                                <span class="cleaning-icon">💧</span>
                                <span>Succión de pozo y trampa de agua</span>
                            </div>
                        </div>
                    </div>
                    <div class="service-card">
                        <div class="service-icon">
                            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M21 16V8C21 5.79086 19.2091 4 17 4H7C4.79086 4 3 5.79086 3 8V16C3 18.2091 4.79086 20 7 20H17C19.2091 20 21 18.2091 21 16Z" stroke="#667eea" stroke-width="2"/>
                                <path d="M7 8H17" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                                <path d="M7 12H17" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                                <path d="M7 16H13" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                                <circle cx="17" cy="16" r="1" fill="#667eea"/>
                            </svg>
                        </div>
                        <h3>Bienes y Servicios en Fibra de Vidrio (FRP)</h3>
                        <p>Fabricación de láminas de piso, tanques, canaletas, paredes. Servicios de aislamiento de metal y concreto con fibra de vidrio.</p>
                    </div>
                    <div class="service-card">
                        <div class="service-icon">
                            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M9 11H15L13 13.5L11 16M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#667eea" stroke-width="2"/>
                                <path d="M12 8V12" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                                <path d="M10.5 8.5L13.5 11.5" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                                <path d="M13.5 8.5L10.5 11.5" stroke="#667eea" stroke-width="2" stroke-linecap="round"/>
                            </svg>
                        </div>
                        <h3>Investigación</h3>
                        <p>Desarrollo de soluciones innovadoras, estudios especializados y proyectos de investigación para la industria.</p>
                    </div>
                </div>
            </div>
        </section>

        <section class="sectors-section">
            <div class="container">
                <h2>Sectores que Atendemos</h2>
                <div class="sectors-grid">
                    <div class="sector-item">
                        <div class="sector-icon">⛏️</div>
                        <h4>Minería</h4>
                    </div>
                    <div class="sector-item">
                        <div class="sector-icon">🐟</div>
                        <h4>Pesquería</h4>
                    </div>
                    <div class="sector-item">
                        <div class="sector-icon">🌾</div>
                        <h4>Agroindustrial</h4>
                    </div>
                    <div class="sector-item">
                        <div class="sector-icon">⚡</div>
                        <h4>Energía</h4>
                    </div>
                    <div class="sector-item">
                        <div class="sector-icon">🍽️</div>
                        <h4>Alimentaria</h4>
                    </div>
                </div>
            </div>
        </section>

        <section class="section" id="nosotros">
            <div class="container">
                <h2>Visión y Misión</h2>
                <div class="vision-mission">
                    <div class="vision-card">
                        <h3>Nuestra Visión</h3>
                        <p>Ser la organización líder a nivel nacional en el rubro de proyectos en minería e industria, con capacidad de trabajar con calidad, seguridad, responsabilidad social y ambiental en todas nuestras operaciones.</p>
                    </div>
                    <div class="mission-card">
                        <h3>Nuestra Misión</h3>
                        <p>Somos un equipo humano innovador comprometido con la mejora continua en nuestros servicios en minería e industria, generando valor a nuestros clientes y colaboradores.</p>
                    </div>
                </div>

                <h2 style="margin-top: 4rem;">Nuestros Valores</h2>
                <div class="values-list">
                    <div class="value-item">
                        <h4>Respeto y Reconocimiento</h4>
                        <p>Valoramos a cada persona y reconocemos sus contribuciones</p>
                    </div>
                    <div class="value-item">
                        <h4>Mejora Continua y Calidad</h4>
                        <p>Buscamos constantemente la excelencia en todo lo que hacemos</p>
                    </div>
                    <div class="value-item">
                        <h4>Responsabilidad Social y Ambiental</h4>
                        <p>Comprometidos con el desarrollo sostenible y el cuidado del medio ambiente</p>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <footer id="contacto">
        <div class="container">
            <h3>SERVIMEX</h3>
            <p>Más de 15 años construyendo el futuro industrial</p>
            <p>&copy; 2024 SERVIMEX. Todos los derechos reservados.</p>
        </div>
    </footer>

    <script>
        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Add animation on scroll
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver(function(entries) {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.animation = 'fadeInUp 0.6s ease-out forwards';
                }
            });
        }, observerOptions);

        document.querySelectorAll('.service-card, .stat-card, .value-item').forEach(el => {
            observer.observe(el);
        });
    </script>
</body>
</html>
