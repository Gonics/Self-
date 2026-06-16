<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gaurav Kushwaha - Portfolio</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* CSS Variables for theming */
        :root {
            --primary-color: #4e73df;
            --secondary-color: #1cc88a;
            --dark-bg: #1a1a1a;
            --light-bg: #f8f9fa;
            --text-dark: #333;
            --text-light: #fff;
            --accent-color: #ffc107;
            --shadow: 0px 10px 30px rgba(0, 0, 0, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* Global Styling */
        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Poppins', sans-serif;
            color: var(--text-dark);
            background: linear-gradient(to bottom, var(--light-bg), #e9ecef);
            transition: background 0.3s ease, color 0.3s ease;
        }

        body.dark-mode {
            background: linear-gradient(to bottom, #1e1e1e, #2d2d2d);
            color: var(--text-light);
        }

        /* Header & Navbar */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(0, 0, 0, 0.95);
            z-index: 1000;
            padding: 15px 0;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        nav {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 30px;
            flex-wrap: wrap;
        }

        nav a {
            color: #fff;
            text-decoration: none;
            font-weight: 600;
            text-transform: uppercase;
            font-size: 0.9rem;
            transition: color 0.3s ease;
            position: relative;
        }

        nav a:hover {
            color: var(--secondary-color);
        }

        nav a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--secondary-color);
            transition: width 0.3s ease;
        }

        nav a:hover::after {
            width: 100%;
        }

        .theme-toggle {
            background: none;
            border: none;
            color: #fff;
            font-size: 1.5rem;
            cursor: pointer;
            transition: color 0.3s ease;
        }

        .theme-toggle:hover {
            color: var(--secondary-color);
        }

        /* Hero Section */
        .hero {
            position: relative;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            text-align: center;
            overflow: hidden;
            margin-top: 60px;
        }

        .hero-slider {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: -1;
            display: flex;
            transition: transform 0.8s ease;
        }

        .hero-slider img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            opacity: 0.6;
            flex-shrink: 0;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.4);
            z-index: 1;
        }

        .hero-content {
            position: relative;
            z-index: 2;
            animation: fadeInUp 1s ease-in-out;
        }

        .hero h1 {
            font-size: clamp(2.5rem, 5vw, 4.5rem);
            font-weight: 700;
            margin-bottom: 15px;
            text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.5);
        }

        .hero .subtitle {
            font-size: clamp(1rem, 3vw, 1.5rem);
            font-weight: 300;
            margin-bottom: 30px;
            text-shadow: 1px 1px 5px rgba(0, 0, 0, 0.5);
        }

        .hero .profession {
            font-size: 1.2rem;
            color: var(--secondary-color);
            font-weight: 600;
            margin-bottom: 30px;
            text-shadow: 1px 1px 5px rgba(0, 0, 0, 0.5);
        }

        .hero-buttons {
            display: flex;
            gap: 15px;
            justify-content: center;
            flex-wrap: wrap;
        }

        .cta-button {
            padding: 12px 30px;
            border: none;
            border-radius: 50px;
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: #fff;
            font-weight: 600;
            font-size: 1rem;
            cursor: pointer;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(78, 115, 223, 0.4);
        }

        .cta-button-secondary {
            background: transparent;
            border: 2px solid #fff;
        }

        .cta-button-secondary:hover {
            background: #fff;
            color: var(--primary-color);
        }

        .slide-controls {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 15px;
            z-index: 2;
        }

        .slide-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.5);
            cursor: pointer;
            transition: background 0.3s ease;
        }

        .slide-dot.active {
            background: var(--secondary-color);
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Sections */
        section {
            padding: 80px 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        section h2 {
            text-align: center;
            font-size: 2.8rem;
            color: var(--primary-color);
            margin-bottom: 50px;
            position: relative;
            font-weight: 700;
        }

        section h2::after {
            content: '';
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
            position: absolute;
            bottom: -20px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 2px;
        }

        body.dark-mode section {
            background: rgba(30, 30, 30, 0.8);
        }

        /* About Section */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            align-items: center;
            background: rgba(255, 255, 255, 0.95);
            padding: 40px;
            border-radius: 15px;
            box-shadow: var(--shadow);
        }

        body.dark-mode .about-content {
            background: rgba(50, 50, 50, 0.9);
        }

        .about-text h3 {
            font-size: 1.8rem;
            color: var(--primary-color);
            margin-bottom: 20px;
            font-weight: 700;
        }

        .about-text p {
            font-size: 1.05rem;
            line-height: 1.8;
            margin-bottom: 15px;
            color: #555;
        }

        body.dark-mode .about-text p {
            color: #ccc;
        }

        .about-image {
            text-align: center;
        }

        .about-image img {
            width: 100%;
            max-width: 300px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease;
        }

        .about-image img:hover {
            transform: scale(1.05);
        }

        /* Skills Section */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 25px;
            margin-top: 40px;
        }

        .skill-card {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: #fff;
            padding: 30px;
            border-radius: 12px;
            text-align: center;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.15);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
        }

        .skill-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(78, 115, 223, 0.3);
        }

        .skill-card i {
            font-size: 3rem;
            margin-bottom: 15px;
            display: block;
        }

        .skill-card h3 {
            font-size: 1.3rem;
            font-weight: 700;
            margin-bottom: 10px;
        }

        .skill-card p {
            font-size: 0.9rem;
            opacity: 0.95;
        }

        /* Experience Timeline */
        .timeline {
            position: relative;
            padding: 20px 0;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 4px;
            height: 100%;
            background: linear-gradient(180deg, var(--primary-color), var(--secondary-color));
        }

        .timeline-item {
            margin-bottom: 50px;
            position: relative;
        }

        .timeline-item:nth-child(even) .timeline-content {
            margin-left: 0;
            margin-right: auto;
            text-align: right;
        }

        .timeline-item:nth-child(odd) .timeline-content {
            margin-left: auto;
            margin-right: 0;
        }

        .timeline-item:nth-child(even) .timeline-dot {
            right: auto;
            left: 50%;
            transform: translateX(-50%);
        }

        .timeline-item:nth-child(odd) .timeline-dot {
            left: auto;
            right: 50%;
            transform: translateX(50%);
        }

        .timeline-dot {
            position: absolute;
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            border: 4px solid var(--light-bg);
            border-radius: 50%;
            top: 0;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            box-shadow: 0 0 0 4px rgba(78, 115, 223, 0.1);
            z-index: 1;
        }

        body.dark-mode .timeline-dot {
            border-color: #2d2d2d;
        }

        .timeline-content {
            width: 45%;
            background: rgba(255, 255, 255, 0.95);
            padding: 25px;
            border-radius: 12px;
            box-shadow: var(--shadow);
            transition: transform 0.3s ease;
        }

        body.dark-mode .timeline-content {
            background: rgba(50, 50, 50, 0.9);
        }

        .timeline-content:hover {
            transform: translateY(-5px);
        }

        .timeline-content h3 {
            font-size: 1.3rem;
            color: var(--primary-color);
            margin-bottom: 8px;
            font-weight: 700;
        }

        .timeline-content .year {
            color: var(--secondary-color);
            font-weight: 600;
            font-size: 0.95rem;
        }

        .timeline-content p {
            color: #666;
            margin-top: 10px;
            line-height: 1.6;
        }

        body.dark-mode .timeline-content p {
            color: #aaa;
        }

        @media (max-width: 768px) {
            .timeline::before {
                left: 20px;
            }

            .timeline-item:nth-child(even) .timeline-content,
            .timeline-item:nth-child(odd) .timeline-content {
                width: calc(100% - 80px);
                margin-left: 80px !important;
                margin-right: 0 !important;
                text-align: left !important;
            }

            .timeline-item:nth-child(even) .timeline-dot,
            .timeline-item:nth-child(odd) .timeline-dot {
                left: 0 !important;
                right: auto !important;
                transform: translateX(0) !important;
            }
        }

        /* Projects Section */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
            margin-top: 40px;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 12px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
        }

        body.dark-mode .project-card {
            background: rgba(50, 50, 50, 0.9);
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.2);
        }

        .project-image {
            width: 100%;
            height: 200px;
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: #fff;
        }

        .project-content {
            padding: 25px;
        }

        .project-content h3 {
            font-size: 1.4rem;
            color: var(--primary-color);
            margin-bottom: 12px;
            font-weight: 700;
        }

        .project-content p {
            color: #666;
            line-height: 1.6;
            margin-bottom: 15px;
        }

        body.dark-mode .project-content p {
            color: #aaa;
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 15px;
        }

        .tag {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: #fff;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }

        /* Contact Section */
        .contact-container {
            background: rgba(255, 255, 255, 0.95);
            padding: 60px 40px;
            border-radius: 15px;
            box-shadow: var(--shadow);
            text-align: center;
        }

        body.dark-mode .contact-container {
            background: rgba(50, 50, 50, 0.9);
        }

        .contact-container p {
            font-size: 1.1rem;
            color: #666;
            margin-bottom: 40px;
            line-height: 1.8;
        }

        body.dark-mode .contact-container p {
            color: #aaa;
        }

        .contact-buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            margin-bottom: 40px;
        }

        .contact-button {
            padding: 15px 30px;
            border: none;
            border-radius: 50px;
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: #fff;
            font-weight: 600;
            font-size: 1rem;
            cursor: pointer;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }

        .contact-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(78, 115, 223, 0.4);
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 25px;
            flex-wrap: wrap;
        }

        .social-link {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            text-decoration: none;
            font-size: 1.5rem;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .social-link:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(78, 115, 223, 0.4);
        }

        /* Footer */
        footer {
            background: #222;
            padding: 40px 20px;
            text-align: center;
            color: #fff;
            border-top: 2px solid var(--primary-color);
        }

        footer p {
            margin: 10px 0;
        }

        footer .year {
            color: var(--secondary-color);
            font-weight: 600;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .about-content {
                grid-template-columns: 1fr;
                gap: 30px;
            }

            .skills-grid {
                grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
                gap: 15px;
            }

            .skill-card {
                padding: 20px;
            }

            .skill-card i {
                font-size: 2.5rem;
            }

            .skill-card h3 {
                font-size: 1.1rem;
            }

            section h2 {
                font-size: 2rem;
            }

            .contact-buttons {
                flex-direction: column;
            }

            .contact-button {
                width: 100%;
                justify-content: center;
            }

            nav {
                gap: 15px;
                padding: 10px;
            }

            nav a {
                font-size: 0.75rem;
            }
        }

        /* Scroll animations */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.6s ease, transform 0.6s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>

<!-- Header & Navigation -->
<header>
    <nav>
        <a href="#about">About</a>
        <a href="#skills">Skills</a>
        <a href="#experience">Experience</a>
        <a href="#projects">Projects</a>
        <a href="#contact">Contact</a>
        <button class="theme-toggle" id="themeToggle">
            <i class="fas fa-moon"></i>
        </button>
    </nav>
</header>

<!-- Hero Section -->
<section class="hero">
    <div class="hero-slider">
        <img src="IMG_20240622_144329~3.jpg" alt="Slide 1">
        <img src="1712304352256 (1)~3.jpg" alt="Slide 2">
        <img src="IMG_20241220_115255281_HDR_AE~2.jpg" alt="Slide 3">
    </div>
    <div class="hero-content">
        <h1>Gaurav Kushwaha</h1>
        <p class="profession">Electronics Engineering Student</p>
        <p class="subtitle">Tech Enthusiast | Systems Software | Full-Stack Developer</p>
        <div class="hero-buttons">
            <a href="#contact" class="cta-button">Get In Touch</a>
            <a href="#projects" class="cta-button cta-button-secondary">View My Work</a>
        </div>
    </div>
    <div class="slide-controls">
        <div class="slide-dot active" onclick="goToSlide(0)"></div>
        <div class="slide-dot" onclick="goToSlide(1)"></div>
        <div class="slide-dot" onclick="goToSlide(2)"></div>
    </div>
</section>

<!-- About Section -->
<section id="about">
    <h2>About Me</h2>
    <div class="about-content">
        <div class="about-text">
            <h3>Hello! I'm Gaurav</h3>
            <p>I'm an Electronics Engineering student with a passion for building innovative technology solutions. My journey spans across systems software, web development, and embedded systems.</p>
            <p>I love exploring new technologies and applying them to solve real-world problems. When I'm not coding or studying circuits, you'll find me tinkering with new projects or learning something new.</p>
            <p>My expertise includes C++, web development, electronics, and competitive programming. I'm always eager to collaborate and learn from the developer community.</p>
        </div>
        <div class="about-image">
            <img src="IMG_20240730_134827203_HDR_AE~2.jpg" alt="Profile Picture">
        </div>
    </div>
</section>

<!-- Skills Section -->
<section id="skills">
    <h2>Skills & Expertise</h2>
    <div class="skills-grid">
        <div class="skill-card">
            <i class="fas fa-code"></i>
            <h3>C++</h3>
            <p>Advanced programming with OOP, STL, and competitive programming</p>
        </div>
        <div class="skill-card">
            <i class="fas fa-globe"></i>
            <h3>Web Development</h3>
            <p>HTML, CSS, JavaScript, and modern web frameworks</p>
        </div>
        <div class="skill-card">
            <i class="fas fa-microchip"></i>
            <h3>Electronics</h3>
            <p>Circuit design, microcontrollers, and embedded systems</p>
        </div>
        <div class="skill-card">
            <i class="fas fa-certificate"></i>
            <h3>Competitive Programming</h3>
            <p>Data structures, algorithms, and problem solving</p>
        </div>
        <div class="skill-card">
            <i class="fas fa-tools"></i>
            <h3>Systems & Tools</h3>
            <p>Git, Linux, debugging, and software development practices</p>
        </div>
        <div class="skill-card">
            <i class="fas fa-layer-group"></i>
            <h3>Full Stack Development</h3>
            <p>Frontend and backend development with modern technologies</p>
        </div>
    </div>
</section>

<!-- Experience Section -->
<section id="experience">
    <h2>My Journey</h2>
    <div class="timeline">
        <div class="timeline-item">
            <div class="timeline-dot">📚</div>
            <div class="timeline-content">
                <h3>High School Excellence</h3>
                <span class="year">Class 1-12</span>
                <p>Developed strong foundation in mathematics, science, and early programming concepts. Participated in various academic competitions and science fairs.</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">🎓</div>
            <div class="timeline-content">
                <h3>Engineering Education</h3>
                <span class="year">Current</span>
                <p>Pursuing Bachelor's degree in Electronics Engineering. Learning advanced concepts in circuits, microcontrollers, signal processing, and digital systems design.</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">💡</div>
            <div class="timeline-content">
                <h3>Skill Development</h3>
                <span class="year">Ongoing</span>
                <p>Continuously learning web development, competitive programming, and systems software. Building projects that combine electronics knowledge with software engineering.</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">🚀</div>
            <div class="timeline-content">
                <h3>Future Goals</h3>
                <span class="year">Upcoming</span>
                <p>Aspire to work on IoT solutions, embedded systems, and innovative tech projects. Goal to become a full-stack engineer with expertise in both hardware and software.</p>
            </div>
        </div>
    </div>
</section>

<!-- Projects Section -->
<section id="projects">
    <h2>Featured Projects</h2>
    <div class="projects-grid">
        <div class="project-card">
            <div class="project-image">💻</div>
            <div class="project-content">
                <h3>Portfolio Website</h3>
                <p>A modern, responsive portfolio website showcasing my skills and projects with smooth animations and dark mode support.</p>
                <div class="project-tags">
                    <span class="tag">HTML</span>
                    <span class="tag">CSS</span>
                    <span class="tag">JavaScript</span>
                </div>
            </div>
        </div>
        <div class="project-card">
            <div class="project-image">⚙️</div>
            <div class="project-content">
                <h3>Embedded Systems Project</h3>
                <p>A hands-on project involving microcontroller programming and circuit design for real-world applications.</p>
                <div class="project-tags">
                    <span class="tag">C++</span>
                    <span class="tag">Arduino</span>
                    <span class="tag">Electronics</span>
                </div>
            </div>
        </div>
        <div class="project-card">
            <div class="project-image">📊</div>
            <div class="project-content">
                <h3>Algorithm Visualizer</h3>
                <p>An interactive web application that visualizes popular algorithms and data structures with step-by-step explanations.</p>
                <div class="project-tags">
                    <span class="tag">JavaScript</span>
                    <span class="tag">Web Design</span>
                    <span class="tag">Algorithms</span>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- Contact Section -->
<section id="contact">
    <div class="contact-container">
        <h2>Let's Connect</h2>
        <p>I'm always interested in hearing about new opportunities and connecting with fellow tech enthusiasts. Feel free to reach out through any of the channels below!</p>
        <div class="contact-buttons">
            <a href="mailto:official.gauravkushwaha@gmail.com" class="contact-button">
                <i class="fas fa-envelope"></i> Email Me
            </a>
            <a href="#projects" class="contact-button">
                <i class="fas fa-file-download"></i> Download Resume
            </a>
        </div>
        <div class="social-links">
            <a href="https://www.instagram.com/gaurav.kushwaha._?igsh=dzFmMHQ5emZldzk2" class="social-link" title="Instagram">
                <i class="fab fa-instagram"></i>
            </a>
            <a href="https://www.linkedin.com/in/gauravkushwaha" class="social-link" title="LinkedIn">
                <i class="fab fa-linkedin"></i>
            </a>
            <a href="https://github.com/gonics" class="social-link" title="GitHub">
                <i class="fab fa-github"></i>
            </a>
            <a href="https://twitter.com" class="social-link" title="Twitter">
                <i class="fab fa-twitter"></i>
            </a>
        </div>
    </div>
</section>

<!-- Footer -->
<footer>
    <p>&copy; <span class="year">2025</span> Gaurav Kushwaha. All rights reserved.</p>
    <p>Thank you for visiting! 🙏</p>
</footer>

<script>
    // Slider functionality
    let currentSlide = 0;
    const slides = document.querySelectorAll('.hero-slider img');
    const dots = document.querySelectorAll('.slide-dot');
    const slider = document.querySelector('.hero-slider');

    function updateSlider() {
        slider.style.transform = `translateX(-${currentSlide * 100}%)`;
        dots.forEach((dot, index) => {
            dot.classList.toggle('active', index === currentSlide);
        });
    }

    function goToSlide(index) {
        currentSlide = index;
        updateSlider();
    }

    function nextSlide() {
        currentSlide = (currentSlide + 1) % slides.length;
        updateSlider();
    }

    // Auto-advance slider every 5 seconds
    setInterval(nextSlide, 5000);

    // Theme toggle
    const themeToggle = document.getElementById('themeToggle');
    const html = document.documentElement;

    // Check for saved theme preference or default to light mode
    const currentTheme = localStorage.getItem('theme') || 'light';
    if (currentTheme === 'dark') {
        document.body.classList.add('dark-mode');
        themeToggle.innerHTML = '<i class="fas fa-sun"></i>';
    }

    themeToggle.addEventListener('click', () => {
        document.body.classList.toggle('dark-mode');
        const theme = document.body.classList.contains('dark-mode') ? 'dark' : 'light';
        localStorage.setItem('theme', theme);
        themeToggle.innerHTML = theme === 'dark' ? '<i class="fas fa-sun"></i>' : '<i class="fas fa-moon"></i>';
    });

    // Fade-in animation on scroll
    const observerOptions = {
        threshold: 0.1,
        rootMargin: '0px 0px -100px 0px'
    };

    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('visible');
            }
        });
    }, observerOptions);

    // Observe all skill cards and project cards
    document.querySelectorAll('.skill-card, .project-card, .timeline-item, .about-content').forEach(el => {
        el.classList.add('fade-in');
        observer.observe(el);
    });

    // Smooth scroll behavior for navigation links
    document.querySelectorAll('nav a[href^="#"]').forEach(link => {
        link.addEventListener('click', (e) => {
            const href = link.getAttribute('href');
            if (href !== '#') {
                e.preventDefault();
                const target = document.querySelector(href);
                if (target) {
                    const offsetTop = target.offsetTop - 80;
                    window.scrollTo({
                        top: offsetTop,
                        behavior: 'smooth'
                    });
                }
            }
        });
    });
</script>

</body>
</html>
