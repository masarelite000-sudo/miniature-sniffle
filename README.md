<!DOCTYPE html>
<html>

<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>JSFiddle 7804yt2L</title>

  <style>
    
  </style>

  
</head>
<body>
  <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MaSAR Elite Services - مسار النخبة</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;900&family=Poppins:wght@300;400;600;800&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

    <style>
        /* Always Light Mode Palette */
        :root {
            --bg-color: #f8f9fc;
            --header-bg: rgba(255, 255, 255, 0.9);
            --text-main: #1a1a1a;
            --text-muted: #555555;
            --card-bg: #ffffff;
            --card-border: rgba(128, 0, 32, 0.15);
            --accent-burgundy: #800020;
            --accent-gold: #d4af37;
            --shadow-color: rgba(0, 0, 0, 0.08);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', 'Cairo', sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            overflow-x: hidden;
        }

        body.rtl {
            direction: rtl;
            text-align: right;
        }

        /* 3D Loading Screen with Three.js */
        #loader {
            position: fixed;
            width: 100vw;
            height: 100vh;
            background: #ffffff;
            z-index: 99999;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            transition: opacity 0.6s ease;
        }

        #loader-canvas {
            width: 150px;
            height: 150px;
            margin-bottom: 15px;
        }

        .loader-text {
            color: var(--accent-burgundy);
            font-weight: 700;
            font-size: 1.1rem;
            letter-spacing: 1px;
            animation: pulseText 1.5s infinite alternate;
        }

        @keyframes pulseText {
            0% { opacity: 0.4; }
            100% { opacity: 1; }
        }

        #canvas-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
            opacity: 0.6;
        }

        /* Header Navigation */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 12px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: var(--header-bg);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(0,0,0,0.06);
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(0,0,0,0.04);
        }

        .logo-box {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-symbol {
            width: 42px;
            height: 42px;
            background: var(--accent-burgundy);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #fff;
            font-weight: 900;
            font-size: 1.2rem;
            box-shadow: 0 4px 10px rgba(128,0,32,0.3);
        }

        .logo-text h2 {
            font-size: 1.1rem;
            color: var(--accent-burgundy);
            font-weight: 800;
            line-height: 1.2;
        }

        .logo-text span {
            font-size: 0.75rem;
            color: var(--text-muted);
            letter-spacing: 0.5px;
            font-weight: 600;
        }

        .nav-actions {
            display: flex;
            align-items: center;
            gap: 8px;
            flex-wrap: wrap;
        }

        .btn-sm {
            padding: 7px 14px;
            font-size: 0.8rem;
            border-radius: 20px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 6px;
            border: none;
        }

        .map-btn {
            background: rgba(212, 175, 55, 0.15);
            border: 1px solid var(--accent-gold) !important;
            color: #b89728;
        }

        .map-btn:hover {
            background: var(--accent-gold);
            color: #000;
        }

        .lang-btn {
            background: rgba(128, 0, 32, 0.08);
            border: 1px solid var(--accent-burgundy);
            color: var(--accent-burgundy);
        }

        .lang-btn:hover {
            background: var(--accent-burgundy);
            color: #fff;
        }

        .btn-whatsapp {
            background: #25D366;
            color: #fff;
            box-shadow: 0 4px 12px rgba(37, 211, 102, 0.3);
        }

        .btn-whatsapp:hover {
            transform: translateY(-2px);
            background: #20ba5a;
        }

        /* Hero Section */
        .hero {
            min-height: 85vh;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 110px 5% 40px;
            gap: 30px;
            position: sticky;
            top: 80px;
            z-index: 10;
        }

        .hero-details {
            max-width: 600px;
        }

        .hero-badge {
            display: inline-block;
            background: rgba(128, 0, 32, 0.1);
            color: var(--accent-burgundy);
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 0.82rem;
            font-weight: 700;
            margin-bottom: 15px;
            border: 1px solid rgba(128, 0, 32, 0.2);
        }

        .hero-details h1 {
            font-size: 2.5rem;
            line-height: 1.25;
            margin-bottom: 15px;
            font-weight: 800;
            color: var(--accent-burgundy);
        }

        .hero-details p {
            color: var(--text-muted);
            font-size: 0.95rem;
            margin-bottom: 25px;
            line-height: 1.6;
        }

        .hero-3d-wrapper {
            width: 320px;
            height: 320px;
        }

        #hero-3d-canvas {
            width: 100%;
            height: 100%;
        }

        /* Services Section */
        .services-section {
            padding: 40px 5%;
            text-align: center;
            position: relative;
            background: var(--bg-color);
            z-index: 20;
        }

        .section-title {
            font-size: 1.8rem;
            font-weight: 800;
            color: var(--accent-burgundy);
            margin-bottom: 30px;
            text-transform: uppercase;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }

        .card-3d {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            padding: 24px 18px;
            border-radius: 16px;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-align: center;
            cursor: pointer;
            box-shadow: 0 8px 25px var(--shadow-color);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .card-3d:hover {
            transform: translateY(-6px);
            border-color: var(--accent-burgundy);
            box-shadow: 0 14px 35px rgba(128, 0, 32, 0.15);
        }

        .card-icon {
            font-size: 2.3rem;
            margin-bottom: 12px;
            color: var(--accent-burgundy);
        }

        .card-3d h3 {
            font-size: 1.05rem;
            margin-bottom: 8px;
            color: var(--text-main);
            font-weight: 700;
        }

        .card-3d p {
            color: var(--text-muted);
            font-size: 0.82rem;
            line-height: 1.45;
            margin-bottom: 15px;
        }

        .card-btn-group {
            display: flex;
            gap: 8px;
            justify-content: center;
        }

        .action-tag {
            font-size: 0.75rem;
            padding: 5px 10px;
            border-radius: 8px;
            font-weight: 600;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 4px;
        }

        .tag-wa {
            background: rgba(37, 211, 102, 0.12);
            color: #128C7E;
            border: 1px solid rgba(37, 211, 102, 0.3);
        }

        .tag-map {
            background: rgba(212, 175, 55, 0.12);
            color: #9c7c1b;
            border: 1px solid rgba(212, 175, 55, 0.3);
        }

        /* Popup Modal for Service Click */
        #service-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(5px);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 10000;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
        }

        #service-modal.active {
            opacity: 1;
            visibility: visible;
        }

        .modal-content {
            background: #ffffff;
            width: 90%;
            max-width: 400px;
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
            position: relative;
            transform: scale(0.9);
            transition: transform 0.3s ease;
        }

        #service-modal.active .modal-content {
            transform: scale(1);
        }

        .modal-content h3 {
            color: var(--accent-burgundy);
            font-size: 1.3rem;
            margin-bottom: 10px;
        }

        .modal-content p {
            color: var(--text-muted);
            font-size: 0.88rem;
            margin-bottom: 20px;
        }

        .modal-close {
            position: absolute;
            top: 15px;
            right: 15px;
            background: none;
            border: none;
            font-size: 1.2rem;
            cursor: pointer;
            color: #888;
        }

        .modal-buttons {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .modal-btn {
            padding: 10px;
            border-radius: 10px;
            font-weight: 600;
            text-decoration: none;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            font-size: 0.9rem;
        }

        .btn-modal-wa {
            background: #25D366;
            color: #fff;
        }

        .btn-modal-map {
            background: #f4b400;
            color: #000;
        }

        /* Contact Section */
        .contact-section {
            padding: 40px 5%;
            background: #f1f3f8;
            border-top: 1px solid #e2e8f0;
            margin-top: 30px;
            text-align: center;
            position: relative;
            z-index: 20;
        }

        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .contact-card {
            background: #ffffff;
            border: 1px solid #e2e8f0;
            padding: 16px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            gap: 12px;
            text-decoration: none;
            box-shadow: 0 4px 12px rgba(0,0,0,0.03);
            transition: all 0.3s ease;
        }

        .contact-card:hover {
            border-color: var(--accent-burgundy);
            transform: translateY(-2px);
        }

        .contact-card i {
            font-size: 1.4rem;
            color: var(--accent-burgundy);
        }

        .contact-info h4 {
            font-size: 0.82rem;
            color: var(--accent-burgundy);
            margin-bottom: 2px;
        }

        .contact-info p {
            font-size: 0.78rem;
            color: var(--text-muted);
            word-break: break-all;
        }

        footer {
            background: #ffffff;
            padding: 20px;
            text-align: center;
            color: var(--text-muted);
            font-size: 0.8rem;
            border-top: 1px solid #e2e8f0;
            position: relative;
            z-index: 20;
        }

        @media(max-width: 768px) {
            .hero {
                flex-direction: column;
                text-align: center;
                position: relative;
                top: 0;
            }
        }
    </style>
</head>
<body>

    <div id="loader">
        <canvas id="loader-canvas"></canvas>
        <div class="loader-text" id="loader-txt">Loading MaSAR Elite...</div>
    </div>

    <canvas id="canvas-bg"></canvas>

    <header>
        <div class="logo-box">
            <div class="logo-symbol">M</div>
            <div class="logo-text">
                <h2>مسار النخبة</h2>
                <span>MaSAR Elite SERVICES</span>
            </div>
        </div>

        <div class="nav-actions">
            <a href="https://maps.app.goo.gl/CgLLuTe28hNPKzKKA?g_st=iwb" target="_blank" class="btn-sm map-btn">
                <i class="fa-solid fa-location-dot"></i> <span id="lbl-location">Location</span>
            </a>
            <button class="btn-sm lang-btn" onclick="toggleLanguage()">
                <i class="fa-solid fa-globe"></i> AR / EN
            </button>
            <a href="https://wa.me/966530499933" target="_blank" class="btn-sm btn-whatsapp">
                <i class="fa-brands fa-whatsapp"></i> WhatsApp
            </a>
        </div>
    </header>

    <section class="hero">
        <div class="hero-details">
            <span class="hero-badge" id="lbl-badge">Your Vision, Our Expertise</span>
            <h1 id="lbl-herotitle">مسار النخبة — خدمات متكاملة والاستشارات</h1>
            <p id="lbl-herodesc">نقدم حلول متكاملة للتصميم والطباعة والخدمات الإلكترونية للأفراد والشركات بأعلى مستويات الجودة والإتقان.</p>
            <a href="https://wa.me/966530499933" target="_blank" class="btn-sm btn-whatsapp" style="padding: 10px 22px; font-size: 0.9rem;">
                <i class="fa-brands fa-whatsapp"></i> <span id="lbl-herobtn">تواصل معنا عبر الواتساب</span>
            </a>
        </div>
        <div class="hero-3d-wrapper">
            <canvas id="hero-3d-canvas"></canvas>
        </div>
    </section>

    <section class="services-section">
        <h2 class="section-title" id="lbl-servicestitle">OUR PROFESSIONAL SERVICES — خدماتنا</h2>
        
        <div class="services-grid" id="services-grid-container">
            </div>
    </section>

    <div id="service-modal">
        <div class="modal-content">
            <button class="modal-close" onclick="closeModal()"><i class="fa-solid fa-xmark"></i></button>
            <h3 id="modal-title">Service Details</h3>
            <p id="modal-desc">Choose how you want to proceed with this service.</p>
            <div class="modal-buttons">
                <a id="modal-wa-link" href="#" target="_blank" class="modal-btn btn-modal-wa">
                    <i class="fa-brands fa-whatsapp"></i> Order / Inquire on WhatsApp
                </a>
                <a href="https://maps.app.goo.gl/CgLLuTe28hNPKzKKA?g_st=iwb" target="_blank" class="modal-btn btn-modal-map">
                    <i class="fa-solid fa-location-dot"></i> Visit Location on Map
                </a>
            </div>
        </div>
    </div>

    <section class="contact-section">
        <h2 class="section-title" style="font-size: 1.4rem;" id="lbl-contacttitle">CONTACT INFORMATION — معلومات التواصل</h2>
        <div class="contact-grid">
            <a href="https://wa.me/966530499933" target="_blank" class="contact-card">
                <i class="fa-brands fa-whatsapp"></i>
                <div class="contact-info">
                    <h4>Mobile / WhatsApp</h4>
                    <p>966 530499933</p>
                </div>
            </a>
            <a href="tel:0112031595" class="contact-card">
                <i class="fa-solid fa-phone"></i>
                <div class="contact-info">
                    <h4>Office Phone</h4>
                    <p>011 203 1595</p>
                </div>
            </a>
            <a href="https://maps.app.goo.gl/CgLLuTe28hNPKzKKA?g_st=iwb" target="_blank" class="contact-card">
                <i class="fa-solid fa-map-location-dot"></i>
                <div class="contact-info">
                    <h4>Location Map</h4>
                    <p>Riyadh, K.S.A</p>
                </div>
            </a>
            <a href="https://instagram.com/Drkattan101010" target="_blank" class="contact-card">
                <i class="fa-brands fa-instagram"></i>
                <div class="contact-info">
                    <h4>Instagram</h4>
                    <p>@Drkattan101010</p>
                </div>
            </a>
        </div>
    </section>

    <footer>
        <p>© 2026 MaSAR Elite Services (مسار النخبة). All Rights Reserved.</p>
    </footer>

    <script>
        // Data for Services (General public version)
        const servicesData = [
            {
                icon: "fa-trophy",
                en: { title: "Commemorative Plaques & Awards", desc: "Honor achievements with premium custom-crafted plaques and awards." },
                ar: { title: "دروع و جوائز تذكارية", desc: "تكريم الإنجازات والمعالم بدروع فاخرة مخصصة حسب الطلب." }
            },
            {
                icon: "fa-gift",
                en: { title: "Promotional Gifts & Giveaways", desc: "Strengthen client relationships with unique corporate gifts." },
                ar: { title: "هدايا دعائية وإعلانية", desc: "تعزيز علاقات العملاء بهدايا مؤسسية ومنتجات ترويجية فريدة." }
            },
            {
                icon: "fa-laptop-code",
                en: { title: "Website Design & Development", desc: "Establish a powerful online presence with responsive websites." },
                ar: { title: "تصميم وتطوير المواقع", desc: "إنشاء حضور قوي عبر الإنترنت بمواقع حديثة ومتجاوبة." }
            },
            {
                icon: "fa-print",
                en: { title: "Banner Printing", desc: "Catch attention with durable, vibrant large-format banners." },
                ar: { title: "طباعة البنرات الإعلانية", desc: "جذب الانتباه ببنرات كبيرة الحجم متينة وعالية الجودة." }
            },
            {
                icon: "fa-scroll",
                en: { title: "Roll-Up Banner Printing", desc: "Portable and sleek pull-up banners for exhibitions and offices." },
                ar: { title: "طباعة رول أب", desc: "بنرات رول أب سهلة الحمل وأنيقة للمعارض والمكاتب." }
            },
            {
                icon: "fa-file-contract",
                en: { title: "Professional CV / Resume Writing", desc: "Stand out with expert ATS-optimized CVs and resumes." },
                ar: { title: "كتابة السيرة الذاتية ATS", desc: "التميز بسيرة ذاتية احترافية محسنة لأنظمة الفرز." }
            },
            {
                icon: "fa-book-journal-whills",
                en: { title: "Research & Academic Writing Support", desc: "Expert assistance with academic research and professional formatting." },
                ar: { title: "دعم الأبحاث والحلول الأكاديمية", desc: "مساعدة خبيرة في كتابة الأبحاث وتنسيقها للجميع." }
            },
            {
                icon: "fa-file-powerpoint",
                en: { title: "Corporate Presentation Design", desc: "Transform complex data into persuasive PowerPoint slides." },
                ar: { title: "تصميم العروض التقديمية", desc: "تحويل البيانات المعقدة إلى عروض بوربوينت مذهلة." }
            },
            {
                icon: "fa-user-check",
                en: { title: "Professional Registration Services", desc: "Complete digital enrollment and registration assistance for all clients." },
                ar: { title: "خدمات التسجيل الإلكتروني", desc: "دعم ومساعدة كاملة في التسجيل والمعاملات الرقمية للجميع." }
            },
            {
                icon: "fa-landmark",
                en: { title: "Najiz Portal Services", desc: "Execution of electronic legal and judicial services via Najiz." },
                ar: { title: "خدمات ناجز", desc: "إنجاز ومتابعة الخدمات العدلية والقانونية عبر منصة ناجز." }
            },
            {
                icon: "fa-id-card",
                en: { title: "Absher Portal Services", desc: "Saudi government electronic transactions and identity processing." },
                ar: { title: "خدمات أبشر", desc: "إنجاز المعاملات الحكومية السعودية والخدمات الإلكترونية." }
            },
            {
                icon: "fa-briefcase",
                en: { title: "General Electronic Services", desc: "Comprehensive corporate and administrative electronic solutions." },
                ar: { title: "خدمات عامة وإلكترونية", desc: "حلول إلكترونية إدارية ومؤسسية شاملة ومتكاملة." }
            },
            {
                icon: "fa-copy",
                en: { title: "Photocopying & Binding", desc: "High-speed photocopying, document scanning, and book binding." },
                ar: { title: "تصوير / نسخ / تجليد", desc: "خدمات تصوير مستندات سريعة، مسح ضوئي وتجليد الكتب." }
            },
            {
                icon: "fa-palette",
                en: { title: "Color Printing & Document Notes", desc: "High-resolution color printing for booklets, reports & documents." },
                ar: { title: "طباعة ملون ومستندات", desc: "طباعة ملونة عالية الدقة للملفات والتقارير والمستندات." }
            },
            {
                icon: "fa-chart-line",
                en: { title: "Market Research & Consulting", desc: "Feasibility studies, data analysis, and professional consulting." },
                ar: { title: "أبحاث تسويقية واستشارات", desc: "دراسات الجدوى، التحليل التسويقي والاستشارات المهنية." }
            },
            {
                icon: "fa-language",
                en: { title: "All Language Translation", desc: "Certified professional translation services across all languages." },
                ar: { title: "ترجمة جميع اللغات", desc: "خدمات ترجمة معتمدة واحترافية لمختلف لغات العالم." }
            }
        ];

        let currentLang = 'en';

        // Render Services
        function renderServices() {
            const container = document.getElementById('services-grid-container');
            container.innerHTML = '';
            servicesData.forEach((serv) => {
                const langData = serv[currentLang];
                const card = document.createElement('div');
                card.className = 'card-3d';
                card.onclick = () => openServiceModal(langData.title);
                card.innerHTML = `
                    <div>
                        <i class="fa-solid ${serv.icon} card-icon"></i>
                        <h3>${langData.title}</h3>
                        <p>${langData.desc}</p>
                    </div>
                    <div class="card-btn-group">
                        <span class="action-tag tag-wa"><i class="fa-brands fa-whatsapp"></i> WhatsApp</span>
                        <span class="action-tag tag-map"><i class="fa-solid fa-location-dot"></i> Location</span>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        // Modal Functionality
        function openServiceModal(serviceName) {
            const modal = document.getElementById('service-modal');
            document.getElementById('modal-title').innerText = serviceName;
            document.getElementById('modal-desc').innerText = currentLang === 'en' 
                ? `Would you like to order "${serviceName}" via WhatsApp or check our office location?`
                : `هل ترغب في طلب خدمة "${serviceName}" عبر الواتساب أم زيارة موقعنا على الخريطة؟`;
            
            const waMsg = encodeURIComponent(`Hello MaSAR Elite, I am interested in: ${serviceName}. Please provide details.`);
            document.getElementById('modal-wa-link').href = `https://wa.me/966530499933?text=${waMsg}`;
            
            modal.classList.add('active');
        }

        function closeModal() {
            document.getElementById('service-modal').classList.remove('active');
        }

        // Language Toggle
        function toggleLanguage() {
            currentLang = currentLang === 'en' ? 'ar' : 'en';
            if(currentLang === 'ar') {
                document.body.classList.add('rtl');
                document.getElementById('lbl-location').innerText = "الموقع";
                document.getElementById('lbl-badge').innerText = "رؤيتكم، خبرتنا — نقدم الجودة المتميزة";
                document.getElementById('lbl-herotitle').innerText = "مسار النخبة — خدمات متكاملة والاستشارات";
                document.getElementById('lbl-herodesc').innerText = "نقدم حلول متكاملة للتصميم والطباعة والخدمات الإلكترونية للأفراد والشركات بأعلى مستويات الجودة والإتقان.";
                document.getElementById('lbl-herobtn').innerText = "تواصل معنا عبر الواتساب";
                document.getElementById('lbl-servicestitle').innerText = "خدماتنا الاحترافية — OUR SERVICES";
                document.getElementById('lbl-contacttitle').innerText = "معلومات التواصل — CONTACT INFORMATION";
                document.getElementById('loader-txt').innerText = "جاري التحميل...";
            } else {
                document.body.classList.remove('rtl');
                document.getElementById('lbl-location').innerText = "Location";
                document.getElementById('lbl-badge').innerText = "Your Vision, Our Expertise";
                document.getElementById('lbl-herotitle').innerText = "MaSAR Elite — Services & Consulting";
                document.getElementById('lbl-herodesc').innerText = "We offer complete design, printing, and digital solutions for individuals, professionals, and businesses.";
                document.getElementById('lbl-herobtn').innerText = "Contact Us on WhatsApp";
                document.getElementById('lbl-servicestitle').innerText = "OUR PROFESSIONAL SERVICES — خدماتنا";
                document.getElementById('lbl-contacttitle').innerText = "CONTACT INFORMATION — معلومات التواصل";
                document.getElementById('loader-txt').innerText = "Loading MaSAR Elite...";
            }
            renderServices();
        }

        // Hide Loader
        window.addEventListener('load', () => {
            setTimeout(() => {
                document.getElementById('loader').style.opacity = '0';
                setTimeout(() => document.getElementById('loader').style.display = 'none', 600);
            }, 600);
            renderServices();
        });

        // 3D Loader Ring Animation (Three.js)
        const lScene = new THREE.Scene();
        const lCamera = new THREE.PerspectiveCamera(75, 1, 0.1, 1000);
        const lRenderer = new THREE.WebGLRenderer({ canvas: document.getElementById('loader-canvas'), alpha: true, antialias: true });
        lRenderer.setSize(150, 150);

        const lGeo = new THREE.TorusGeometry(0.8, 0.25, 16, 100);
        const lMat = new THREE.MeshStandardMaterial({ color: 0x800020, roughness: 0.3, metalness: 0.2 });
        const lMesh = new THREE.Mesh(lGeo, lMat);
        lScene.add(lMesh);

        lScene.add(new THREE.AmbientLight(0xffffff, 1));
        lCamera.position.z = 3;

        function animateLoader() {
            requestAnimationFrame(animateLoader);
            lMesh.rotation.x += 0.02;
            lMesh.rotation.y += 0.03;
            lRenderer.render(lScene, lCamera);
        }
        animateLoader();

        // Background 3D Objects Animation
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ canvas: document.getElementById('canvas-bg'), alpha: true, antialias: true });
        renderer.setSize(window.innerWidth, window.innerHeight);

        const group = new THREE.Group();
        scene.add(group);

        const geoBox = new THREE.BoxGeometry(0.7, 0.9, 0.15);
        const matBox = new THREE.MeshStandardMaterial({ color: 0x800020, roughness: 0.4 });

        for(let i=0; i<20; i++) {
            const mesh = new THREE.Mesh(geoBox, matBox);
            mesh.position.set((Math.random()-0.5)*14, (Math.random()-0.5)*10, (Math.random()-0.5)*8);
            mesh.rotation.set(Math.random()*Math.PI, Math.random()*Math.PI, 0);
            group.add(mesh);
        }

        scene.add(new THREE.AmbientLight(0xffffff, 0.9));
        camera.position.z = 5;

        function animate() {
            requestAnimationFrame(animate);
            group.rotation.y += 0.002;
            renderer.render(scene, camera);
        }
        animate();

        // Hero 3D Spinning Shape with Mouse and Scroll Movement
        const hScene = new THREE.Scene();
        const hCamera = new THREE.PerspectiveCamera(75, 1, 0.1, 1000);
        const hRenderer = new THREE.WebGLRenderer({ canvas: document.getElementById('hero-3d-canvas'), alpha: true, antialias: true });
        hRenderer.setSize(320, 320);

        const hGeo = new THREE.IcosahedronGeometry(1.2, 0);
        const hMat = new THREE.MeshStandardMaterial({ color: 0xd4af37, wireframe: true, roughness: 0.2 });
        const hMesh = new THREE.Mesh(hGeo, hMat);
        hScene.add(hMesh);

        hScene.add(new THREE.AmbientLight(0xffffff, 1));
        hCamera.position.z = 3.5;

        let mouseX = 0;
        let mouseY = 0;
        let targetX = 0;
        let targetY = 0;

        document.addEventListener('mousemove', (event) => {
            mouseX = (event.clientX / window.innerWidth) - 0.5;
            mouseY = (event.clientY / window.innerHeight) - 0.5;
        });

        window.addEventListener('scroll', () => {
            let scrollY = window.scrollY;
            hMesh.position.y = -(scrollY * 0.0015);
        });

        function animateH() {
            requestAnimationFrame(animateH);
            
            targetX += (mouseX - targetX) * 0.05;
            targetY += (mouseY - targetY) * 0.05;

            hMesh.rotation.x = targetY * 2 + 1;
            hMesh.rotation.y = targetX * 2 + 1;
            hMesh.rotation.z += 0.005;

            hRenderer.render(hScene, hCamera);
        }
        animateH();

        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });
    </script>
</body>
</html>

  <script>
    // মাউস মুভমেন্ট এবং স্ক্রল পজিশন ট্র্যাক করার জন্য ভেরিয়েবল
let mouseX = 0;
let mouseY = 0;
let targetX = 0;
let targetY = 0;

// মাউস মুভ করলে পজিশন সেভ করা
document.addEventListener('mousemove', (event) => {
    mouseX = (event.clientX / window.innerWidth) - 0.5;
    mouseY = (event.clientY / window.innerHeight) - 0.5;
});

// স্ক্রল করলে শেপটি নিচের দিকে বা স্ক্রলের সাথে মুভ করানো
window.addEventListener('scroll', () => {
    let scrollY = window.scrollY;
    hMesh.position.y = -(scrollY * 0.002); // স্ক্রল করার সাথে সাথে নিচে নামবে
});

// অ্যানিমেশন লুপে স্মুথ মুভমেন্ট যোগ করা
function animateH() {
    requestAnimationFrame(animateH);
    
    // স্মুথ ট্রানজিশনের জন্য লেপ (Lerp) ক্যালকুলেশন
    targetX += (mouseX - targetX) * 0.05;
    targetY += (mouseY - targetY) * 0.05;

    // মাউস ও অটো রোটেশন একসাথে কাজ করবে
    hMesh.rotation.x = targetY * 2 + 1;
    hMesh.rotation.y = targetX * 2 + 1;
    
    // নিজস্ব স্পিন বজায় রাখা
    hMesh.rotation.z += 0.005;

    hRenderer.render(hScene, hCamera);
}
animateH();
  </script>
</body>
</html>
