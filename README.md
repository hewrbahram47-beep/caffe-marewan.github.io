<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <!-- iOS Status Bar Color -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="theme-color" content="#6B4423">
    <title>قەهوەخانەی شەقڵاوە | هەولێر - شەقڵاوە - بازاڕی شەقڵاوە</title>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+Arabic:wght@400;600;700;800&family=Vazirmatn:wght@400;600;700;800&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent; /* Remove iOS tap highlight */
        }

        :root {
            --primary: #6B4423;
            --primary-light: #8B5A2B;
            --secondary: #D4A574;
            --accent: #C4A77D;
            --dark: #2C1810;
            --light: #FDF8F3;
            --cream: #F5E6D3;
            --success: #4A7C59;
            --text: #3D2914;
        }

        html {
            -webkit-text-size-adjust: 100%; /* Prevent iOS font scaling */
            height: 100%;
        }

        body {
            font-family: 'Vazirmatn', 'Noto Sans Arabic', -apple-system, BlinkMacSystemFont, sans-serif;
            background: var(--light);
            color: var(--text);
            line-height: 1.8;
            overflow-x: hidden;
            -webkit-font-smoothing: antialiased; /* Better font rendering on iOS */
            -moz-osx-font-smoothing: grayscale;
            min-height: 100%;
        }

        /* iOS Safe Area Support */
        .safe-area-top {
            padding-top: env(safe-area-inset-top);
        }
        
        .safe-area-bottom {
            padding-bottom: env(safe-area-inset-bottom);
        }

        /* Header - Fixed iOS position:fixed issues */
        .header {
            background: linear-gradient(135deg, var(--dark) 0%, var(--primary) 100%);
            color: white;
            padding: 1rem;
            padding-top: max(1rem, env(safe-area-inset-top));
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(0,0,0,0.3);
            transform: translateZ(0); /* iOS GPU acceleration */
            -webkit-transform: translateZ(0);
            will-change: transform;
        }

        .header-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.4rem;
            font-weight: 800;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .logo-icon {
            font-size: 1.8rem;
        }

        .location-badge {
            background: rgba(255,255,255,0.15);
            padding: 0.4rem 0.8rem;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 600;
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px); /* iOS prefix */
            border: 1px solid rgba(255,255,255,0.2);
        }

        /* Hero Section - Adjusted for iOS safe area */
        .hero {
            margin-top: calc(60px + env(safe-area-inset-top));
            background: linear-gradient(135deg, var(--dark) 0%, var(--primary) 50%, var(--primary-light) 100%);
            color: white;
            padding: 3rem 1.5rem;
            padding-top: calc(3rem + env(safe-area-inset-top));
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 1px, transparent 1px);
            background-size: 20px 20px;
            opacity: 0.3;
        }

        .hero-title {
            font-size: 2rem;
            font-weight: 800;
            margin-bottom: 0.5rem;
            position: relative;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            line-height: 1.3;
        }

        .hero-subtitle {
            font-size: 1.1rem;
            opacity: 0.95;
            margin-bottom: 1.5rem;
            font-weight: 600;
        }

        .hero-location {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            background: rgba(255,255,255,0.2);
            padding: 0.6rem 1.2rem;
            border-radius: 30px;
            font-size: 0.9rem;
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.3);
        }

        /* Navigation - iOS scroll fix */
        .nav-container {
            background: white;
            padding: 1rem;
            position: sticky;
            top: calc(60px + env(safe-area-inset-top));
            z-index: 999;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            overflow-x: auto;
            -webkit-overflow-scrolling: touch; /* Smooth iOS scrolling */
            scrollbar-width: none;
            -ms-overflow-style: none;
        }

        .nav-container::-webkit-scrollbar {
            display: none;
        }

        .nav {
            display: flex;
            gap: 0.5rem;
            min-width: max-content;
        }

        .nav-btn {
            background: var(--cream);
            border: none;
            padding: 0.7rem 1.2rem;
            border-radius: 25px;
            font-family: inherit;
            font-size: 0.9rem;
            font-weight: 600;
            color: var(--text);
            cursor: pointer;
            transition: all 0.3s;
            white-space: nowrap;
            -webkit-appearance: none; /* Remove iOS default button styling */
            appearance: none;
            touch-action: manipulation; /* Improve touch response */
        }

        .nav-btn.active, .nav-btn:hover {
            background: var(--primary);
            color: white;
            transform: translateY(-2px);
            -webkit-transform: translateY(-2px);
        }

        .nav-btn:active {
            transform: scale(0.95);
            -webkit-transform: scale(0.95);
        }

        /* Menu Sections */
        .menu-section {
            padding: 2rem 1rem;
            max-width: 800px;
            margin: 0 auto;
            display: none; /* Changed from hidden class approach */
        }

        .menu-section.active {
            display: block;
            animation: fadeIn 0.5s ease-in;
            -webkit-animation: fadeIn 0.5s ease-in;
        }

        .section-title {
            font-size: 1.5rem;
            font-weight: 800;
            color: var(--primary);
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding-bottom: 0.5rem;
            border-bottom: 3px solid var(--secondary);
        }

        .menu-grid {
            display: grid;
            gap: 1rem;
        }

        .menu-item {
            background: white;
            border-radius: 16px;
            padding: 1rem;
            display: flex;
            gap: 1rem;
            box-shadow: 0 4px 15px rgba(0,0,0,0.08);
            transition: transform 0.3s, box-shadow 0.3s;
            -webkit-transition: -webkit-transform 0.3s, box-shadow 0.3s;
            border: 1px solid var(--cream);
            cursor: pointer;
            -webkit-tap-highlight-color: rgba(0,0,0,0.05);
        }

        .menu-item:active {
            transform: scale(0.98);
            -webkit-transform: scale(0.98);
        }

        .item-image {
            width: 90px;
            height: 90px;
            border-radius: 12px;
            object-fit: cover;
            flex-shrink: 0;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            background: var(--cream); /* Fallback while loading */
        }

        .item-details {
            flex: 1;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            min-width: 0; /* iOS flexbox fix */
        }

        .item-header {
            display: flex;
            justify-content: space-between;
            align-items: start;
            gap: 0.5rem;
        }

        .item-name {
            font-weight: 700;
            font-size: 1.1rem;
            color: var(--dark);
            line-height: 1.4;
        }

        .item-price {
            background: var(--primary);
            color: white;
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-weight: 700;
            font-size: 0.9rem;
            white-space: nowrap;
            flex-shrink: 0;
        }

        .item-desc {
            font-size: 0.85rem;
            color: #666;
            margin-top: 0.3rem;
            line-height: 1.4;
        }

        /* Reservation Section */
        .reservation-section {
            background: linear-gradient(135deg, var(--cream) 0%, white 100%);
            padding: 2rem 1rem;
            margin: 2rem 1rem;
            border-radius: 20px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.1);
        }

        .reservation-title {
            font-size: 1.4rem;
            font-weight: 800;
            color: var(--primary);
            text-align: center;
            margin-bottom: 1.5rem;
        }

        .form-group {
            margin-bottom: 1rem;
        }

        .form-label {
            display: block;
            font-weight: 600;
            margin-bottom: 0.4rem;
            color: var(--text);
            font-size: 0.95rem;
        }

        .form-input {
            width: 100%;
            padding: 0.9rem 1rem;
            border: 2px solid var(--cream);
            border-radius: 12px;
            font-family: inherit;
            font-size: 1rem;
            background: white;
            transition: border-color 0.3s;
            -webkit-transition: border-color 0.3s;
            -webkit-appearance: none; /* Remove iOS default styling */
            appearance: none;
            outline: none;
        }

        .form-input:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(107, 68, 35, 0.1);
        }

        /* iOS Date/Time input fixes */
        input[type="date"],
        input[type="time"] {
            -webkit-appearance: none;
            appearance: none;
            min-height: 44px; /* iOS touch target */
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
        }

        .submit-btn {
            width: 100%;
            background: linear-gradient(135deg, #25D366 0%, #128C7E 100%);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 12px;
            font-family: inherit;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            margin-top: 1rem;
            box-shadow: 0 4px 15px rgba(37, 211, 102, 0.3);
            transition: transform 0.3s;
            -webkit-transition: -webkit-transform 0.3s;
            -webkit-appearance: none;
            appearance: none;
            touch-action: manipulation;
        }

        .submit-btn:active {
            transform: scale(0.98);
            -webkit-transform: scale(0.98);
        }

        /* Info Section */
        .info-section {
            background: var(--dark);
            color: white;
            padding: 2rem 1rem;
            padding-bottom: calc(2rem + env(safe-area-inset-bottom));
            margin-top: 2rem;
        }

        .info-grid {
            display: grid;
            gap: 1.5rem;
            max-width: 800px;
            margin: 0 auto;
        }

        .info-card {
            background: rgba(255,255,255,0.1);
            padding: 1.2rem;
            border-radius: 12px;
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.1);
        }

        .info-label {
            font-size: 0.85rem;
            opacity: 0.8;
            margin-bottom: 0.3rem;
        }

        .info-value {
            font-size: 1.1rem;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            line-height: 1.4;
        }

        /* Floating WhatsApp Button - Fixed for iOS */
        .whatsapp-float {
            position: fixed;
            bottom: calc(20px + env(safe-area-inset-bottom));
            left: 20px;
            background: #25D366;
            color: white;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            box-shadow: 0 4px 20px rgba(37, 211, 102, 0.4);
            z-index: 1000;
            text-decoration: none;
            animation: pulse 2s infinite;
            -webkit-animation: pulse 2s infinite;
            transform: translateZ(0);
            -webkit-transform: translateZ(0);
            will-change: transform;
            cursor: pointer;
            -webkit-tap-highlight-color: transparent;
        }

        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(37, 211, 102, 0.7); }
            70% { box-shadow: 0 0 0 15px rgba(37, 211, 102, 0); }
            100% { box-shadow: 0 0 0 0 rgba(37, 211, 102, 0); }
        }

        @-webkit-keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(37, 211, 102, 0.7); }
            70% { box-shadow: 0 0 0 15px rgba(37, 211, 102, 0); }
            100% { box-shadow: 0 0 0 0 rgba(37, 211, 102, 0); }
        }

        /* Footer */
        .footer {
            background: var(--dark);
            color: rgba(255,255,255,0.6);
            text-align: center;
            padding: 1.5rem;
            padding-bottom: calc(1.5rem + env(safe-area-inset-bottom) + 80px); /* Extra space for WhatsApp button */
            font-size: 0.85rem;
        }

        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); -webkit-transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); -webkit-transform: translateY(0); }
        }

        @-webkit-keyframes fadeIn {
            from { opacity: 0; -webkit-transform: translateY(10px); }
            to { opacity: 1; -webkit-transform: translateY(0); }
        }

        /* iOS-specific fixes */
        @supports (-webkit-touch-callout: none) {
            /* CSS specific to iOS devices */
            .hero {
                background-attachment: scroll; /* Fixed background causes issues on iOS */
            }
            
            .menu-item {
                transform: translateZ(0); /* Force GPU acceleration */
            }
        }

        /* Prevent callout menu on iOS */
        a, button {
            -webkit-touch-callout: none;
            -webkit-user-select: none;
            user-select: none;
        }

        /* Allow text selection in inputs */
        input, textarea {
            -webkit-user-select: auto;
            user-select: auto;
        }
    </style>
</head>
<body>

    <!-- Header -->
    <header class="header">
        <div class="header-content">
            <div class="logo">
                <span class="logo-icon">☕</span>
                <span>قەهوەخانەی شەقڵاوە</span>
            </div>
            <div class="location-badge">بازاڕی شەقڵاوە</div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <h1 class="hero-title">بەخێربێن بۆ قەهوەخانەی شەقڵاوە</h1>
        <p class="hero-subtitle">باشترین قەهوە و چای کوردی لە ناوچەی شەقڵاوە</p>
        <div class="hero-location">
            <span>📍</span>
            <span>هەولێر - شەقڵاوە - بازاڕی شەقڵاوە</span>
        </div>
    </section>

    <!-- Navigation -->
    <div class="nav-container">
        <nav class="nav">
            <button class="nav-btn active" onclick="showSection('hot', this)">☕ قەهوەی گەرم</button>
            <button class="nav-btn" onclick="showSection('cold', this)">🧊 قەهوەی سارد</button>
            <button class="nav-btn" onclick="showSection('tea', this)">🫖 چای</button>
            <button class="nav-btn" onclick="showSection('desserts', this)">🍰 شیرینی</button>
        </nav>
    </div>

    <!-- Hot Coffee Section -->
    <section id="hot" class="menu-section active">
        <h2 class="section-title">☕ قەهوەی گەرم</h2>
        <div class="menu-grid">
            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/static.vecteezy.com/4961b07cd766805f0e2b1a3e644d8c347c691fb2.jpg" alt="Espresso" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">ئێسپرێسۆ</div>
                            <div class="item-desc">قەهوەی ئیتاڵی بەهێم</div>
                        </div>
                        <div class="item-price">٢,٠٠٠ دینار</div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/www.nespresso.com/8089c3b1a6acae103b91e14139df52c3467edb14.jpg" alt="Cappuccino" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">کاپوتشینۆ</div>
                            <div class="item-desc">قەهوە بە شیر و فوم</div>
                        </div>
                        <div class="item-price">٣,٥٠٠ دینار</div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/dynamic-media-cdn.tripadvisor.com/9bd0e855aa2ef278e632071b100d354b9c3780cc.jpg" alt="Latte" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">لاتێ</div>
                            <div class="item-desc">قەهوە بە شیر بە ئاراستەی لاتێ ئارت</div>
                        </div>
                        <div class="item-price">٤,٠٠٠ دینار</div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/cdn.shopify.com/4794d298db82bf9381254ef52b284cee10cebcca.webp" alt="Arabic Coffee" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">قەهوەی عەرەبی</div>
                            <div class="item-desc">قەهوەی کوردی-عەرەبی بە هەل</div>
                        </div>
                        <div class="item-price">٢,٥٠٠ دینار</div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/pontevecchiosrl.it/d14d5dc005a75a02a252a006080011221a2fc695.jpg" alt="Americano" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">ئەمریکانۆ</div>
                            <div class="item-desc">ئێسپرێسۆ بە ئاو</div>
                        </div>
                        <div class="item-price">٢,٥٠٠ دینار</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Cold Coffee Section -->
    <section id="cold" class="menu-section">
        <h2 class="section-title">🧊 قەهوەی سارد</h2>
        <div class="menu-grid">
            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/d2wqffb2bc8st5.cloudfront.net/d940ed3446006ffe94c3075efcccc0b0e09691ee.jpg" alt="Iced Coffee" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">ئایس کافی</div>
                            <div class="item-desc">قەهوەی سارد بە شیر</div>
                        </div>
                        <div class="item-price">٤,٥٠٠ دینار</div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/c8.alamy.com/cded8fade9eb598b1b68cb567dbcb7b22a36fc2d.jpg" alt="Cold Brew" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">کۆڵد برو</div>
                            <div class="item-desc">قەهوەی دێم بە سارد</div>
                        </div>
                        <div class="item-price">٥,٠٠٠ دینار</div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/media.shafaq.com/f5757a11a071d470ad960e08e561d3a3b02042af.webp" alt="Frappe" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">فراپێ</div>
                            <div class="item-desc">قەهوەی بەستوو یۆنانی</div>
                        </div>
                        <div class="item-price">٤,٠٠٠ دینار</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Tea Section -->
    <section id="tea" class="menu-section">
        <h2 class="section-title">🫖 چای</h2>
        <div class="menu-grid">
            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/www.shutterstock.com/dc564544b87593588a1ae31b8f0e5a9c4a92597d.jpg" alt="Kurdish Tea" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">چای کوردی</div>
                            <div class="item-desc">چای ڕەنگی کوردی بە نارنج</div>
                        </div>
                        <div class="item-price">١,٥٠٠ دینار</div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/d2wqffb2bc8st5.cloudfront.net/a0ae3a48a12ee5e4512cf2ec21cc7446971a517f.jpg" alt="Herbal Tea" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">چای دەمک</div>
                            <div class="item-desc">چای گیاکی بۆ دڵنیایی</div>
                        </div>
                        <div class="item-price">٢,٠٠٠ دینار</div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/d2wqffb2bc8st5.cloudfront.net/d940ed3446006ffe94c3075efcccc0b0e09691ee.jpg" alt="Green Tea" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">چای سەوز</div>
                            <div class="item-desc">چای سەوزی بەهێم</div>
                        </div>
                        <div class="item-price">٢,٠٠٠ دینار</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Desserts Section -->
    <section id="desserts" class="menu-section">
        <h2 class="section-title">🍰 شیرینی و خۆراک</h2>
        <div class="menu-grid">
            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/freshaprilflours.com/e7861b0c0fb172b9a29ab0de4f68fb730175d7a5.jpg" alt="Cheesecake" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">چیزکێک</div>
                            <div class="item-desc">چیزکێکی کریمی</div>
                        </div>
                        <div class="item-price">٥,٠٠٠ دینار</div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/emberfoods.vn/cf9a64b335293b324c72f5be478b248dc27a2af6.jpg" alt="Croissant" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">کرواسان</div>
                            <div class="item-desc">نانە فرەنسی بە کرەم</div>
                        </div>
                        <div class="item-price">٣,٠٠٠ دینار</div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/www.shutterstock.com/cdfd4466d1b51c3fa4488dffc317e17cef34b967.jpg" alt="Chocolate Croissant" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">کرواسانی شۆکۆلات</div>
                            <div class="item-desc">کرواسان بە شۆکۆلاتی بلژێر</div>
                        </div>
                        <div class="item-price">٣,٥٠٠ دینار</div>
                    </div>
                </div>
            </div>

            <div class="menu-item">
                <img src="https://kimi-web-img.moonshot.cn/img/inbloombakery.com/6b5f93c2a08d886902a51133156ff1fce5f7d32c.jpg" alt="Coffee Cheesecake" class="item-image">
                <div class="item-details">
                    <div class="item-header">
                        <div>
                            <div class="item-name">چیزکێکی قەهوە</div>
                            <div class="item-desc">چیزکێک بە تامی قەهوە</div>
                        </div>
                        <div class="item-price">٥,٥٠٠ دینار</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Reservation Section -->
    <section class="reservation-section">
        <h2 class="reservation-title">📅 حجزکردنی مێز</h2>
        <form id="reservationForm" onsubmit="sendToWhatsApp(event)">
            <div class="form-group">
                <label class="form-label">ناوی تەواو *</label>
                <input type="text" class="form-input" id="name" placeholder="ناوی خۆت بنووسە" required autocomplete="name">
            </div>
            
            <div class="form-row">
                <div class="form-group">
                    <label class="form-label">ژمارەی مۆبایل *</label>
                    <input type="tel" class="form-input" id="phone" placeholder="٠٧٥٠xxxxxxx" required autocomplete="tel" pattern="[0-9]*" inputmode="numeric">
                </div>
                <div class="form-group">
                    <label class="form-label">ژمارەی کەسەکان *</label>
                    <input type="number" class="form-input" id="people" placeholder="چەند کەس؟" min="1" max="20" required inputmode="numeric">
                </div>
            </div>

            <div class="form-row">
                <div class="form-group">
                    <label class="form-label">بەروار *</label>
                    <input type="date" class="form-input" id="date" required>
                </div>
                <div class="form-group">
                    <label class="form-label">کات *</label>
                    <input type="time" class="form-input" id="time" required>
                </div>
            </div>

            <div class="form-group">
                <label class="form-label">تایبەتمەندی (ئارەزوومەندانە)</label>
                <input type="text" class="form-input" id="notes" placeholder="تایبەتمەندی تایبەت...">
            </div>

            <button type="submit" class="submit-btn">
                <span>📱</span>
                <span>ناردن بۆ واتسئاپ</span>
            </button>
        </form>
    </section>

    <!-- Info Section -->
    <section class="info-section">
        <div class="info-grid">
            <div class="info-card">
                <div class="info-label">ناونیشان</div>
                <div class="info-value">
                    <span>📍</span>
                    <span>هەولێر - شەقڵاوە - بازاڕی شەقڵاوە</span>
                </div>
            </div>
            <div class="info-card">
                <div class="info-label">کاتەکانی کارکردن</div>
                <div class="info-value">
                    <span>🕐</span>
                    <span>٨:٠٠ بەیانی - ١١:٥٥ شەو</span>
                </div>
            </div>
            <div class="info-card">
                <div class="info-label">پەیوەندی</div>
                <div class="info-value">
                    <span>📞</span>
                    <span>٠٧٥٠٤٦٦٦٦٩٨</span>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <p>© ٢٠٢٦ قەهوەخانەی شەقڵاوە - هەولێر</p>
        <p style="margin-top: 0.5rem;">باشترین قەهوە لە ناوچەی شەقڵاوە</p>
    </footer>

    <!-- Floating WhatsApp -->
    <a href="https://wa.me/9647504666698" class="whatsapp-float" target="_blank" rel="noopener noreferrer">
        💬
    </a>

    <script>
        // iOS-safe navigation
        function showSection(sectionId, clickedBtn) {
            // Hide all sections
            document.querySelectorAll('.menu-section').forEach(section => {
                section.classList.remove('active');
            });
            
            // Show selected section
            const selected = document.getElementById(sectionId);
            if (selected) {
                selected.classList.add('active');
            }
            
            // Update nav buttons
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            if (clickedBtn) {
                clickedBtn.classList.add('active');
            }
            
            // Smooth scroll to top of menu on iOS
            window.scrollTo({ top: 400, behavior: 'smooth' });
        }

        // Set today's date as minimum - iOS compatible
        document.addEventListener('DOMContentLoaded', function() {
            const today = new Date().toISOString().split('T')[0];
            const dateInput = document.getElementById('date');
            if (dateInput) {
                dateInput.min = today;
                dateInput.value = today;
            }
        });

        // WhatsApp Integration with iOS handling
        function sendToWhatsApp(e) {
            e.preventDefault();
            e.stopPropagation(); // Prevent double firing on iOS
            
            const name = document.getElementById('name').value;
            const phone = document.getElementById('phone').value;
            const people = document.getElementById('people').value;
            const date = document.getElementById('date').value;
            const time = document.getElementById('time').value;
            const notes = document.getElementById('notes').value;
            
            const message = `*داواکاری حجزکردن - قەهوەخانەی شەقڵاوە*%0A%0A` +
                `👤 ناو: ${name}%0A` +
                `📱 ژمارەی مۆبایل: ${phone}%0A` +
                `👥 ژمارەی کەسەکان: ${people}%0A` +
                `📅 بەروار: ${date}%0A` +
                `🕐 کات: ${time}%0A` +
                `📝 تایبەتمەندی: ${notes || 'نییە'}%0A%0A` +
                `لە ڕێگەی وێبسایتەوە نێردراوە`;
            
            const whatsappURL = `https://wa.me/9647504666698?text=${message}`;
            
            // iOS-compatible window opening
            const newWindow = window.open(whatsappURL, '_blank');
            
            // Fallback for iOS if popup blocked
            if (!newWindow || newWindow.closed || typeof newWindow.closed === 'undefined') {
                window.location.href = whatsappURL;
            }
        }

        // Prevent iOS double-tap zoom
        let lastTouchEnd = 0;
        document.addEventListener('touchend', function (event) {
            const now = (new Date()).getTime();
            if (now - lastTouchEnd <= 300) {
                event.preventDefault();
            }
            lastTouchEnd = now;
        }, false);

        // iOS viewport height fix
        function setVH() {
            let vh = window.innerHeight * 0.01;
            document.documentElement.style.setProperty('--vh', `${vh}px`);
        }
        setVH();
        window.addEventListener('resize', setVH);
    </script>

</body>
</html>
