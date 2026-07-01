<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SAVORA - Savor Your Beauty</title>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400..700;1,400..700&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #8e6f54;
            --primary-light: #f5f0eb;
            --accent: #d4af37;
            --text-dark: #2c2520;
            --text-muted: #70645c;
            --bg-main: #faf8f5;
            --bg-card: #ffffff;
            --border-color: #eae3db;
            --success: #2e7d32;
            --shadow: 0 4px 20px rgba(142, 111, 84, 0.08);
            --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Plus Jakarta Sans', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-main);
            color: var(--text-dark);
            line-height: 1.6;
            padding-bottom: 80px;
        }

        /* Utility classes */
        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header & Navigation */
        header {
            background-color: var(--bg-card);
            border-bottom: 1px solid var(--border-color);
            padding: 30px 0 20px 0;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0,0,0,0.02);
        }

        .shop-brand h1 {
            font-family: 'Playfair Display', serif;
            font-size: 2.5rem;
            font-weight: 700;
            letter-spacing: 2px;
            color: var(--primary);
            text-transform: uppercase;
            margin-bottom: 4px;
        }

        .shop-brand p {
            font-size: 0.95rem;
            color: var(--text-muted);
            font-style: italic;
            letter-spacing: 1px;
        }

        .shop-info-bar {
            background-color: var(--primary-light);
            color: var(--primary);
            font-size: 0.8rem;
            font-weight: 600;
            padding: 6px 20px;
            text-align: center;
            letter-spacing: 0.5px;
        }

        /* Category Filter Slider */
        .category-container {
            padding: 20px 0;
            background-color: var(--bg-main);
            position: sticky;
            top: 115px;
            z-index: 99;
        }

        .category-slider {
            display: flex;
            gap: 10px;
            overflow-x: auto;
            scrollbar-width: none; /* Firefox */
            padding: 5px 20px;
        }

        .category-slider::-webkit-scrollbar {
            display: none; /* Chrome/Safari */
        }

        .category-btn {
            background-color: var(--bg-card);
            border: 1px solid var(--border-color);
            color: var(--text-muted);
            padding: 10px 22px;
            border-radius: 30px;
            font-size: 0.9rem;
            font-weight: 600;
            cursor: pointer;
            white-space: nowrap;
            transition: var(--transition);
            box-shadow: 0 2px 5px rgba(0,0,0,0.02);
        }

        .category-btn.active, .category-btn:hover {
            background-color: var(--primary);
            color: white;
            border-color: var(--primary);
        }

        /* Product Grid */
        .products-section {
            margin-top: 10px;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
        }

        @media (min-width: 768px) {
            .products-grid {
                grid-template-columns: repeat(3, 1fr);
                gap: 25px;
            }
        }

        @media (min-width: 1024px) {
            .products-grid {
                grid-template-columns: repeat(4, 1fr);
            }
        }

        .product-card {
            background-color: var(--bg-card);
            border-radius: 16px;
            border: 1px solid var(--border-color);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            transition: var(--transition);
            position: relative;
            box-shadow: var(--shadow);
        }

        .product-card:hover {
            transform: translateY(-4px);
        }

        .product-img-wrapper {
            position: relative;
            width: 100%;
            padding-top: 110%; /* Slightly taller portrait aspect ratio */
            background-color: #fcfbf9;
            overflow: hidden;
            border-bottom: 1px solid var(--border-color);
        }

        .product-img-wrapper img {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }

        .product-card:hover .product-img-wrapper img {
            transform: scale(1.04);
        }

        .product-details {
            padding: 15px;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }

        .product-category {
            font-size: 0.75rem;
            text-transform: uppercase;
            color: var(--accent);
            font-weight: 700;
            margin-bottom: 4px;
            letter-spacing: 0.5px;
        }

        .product-name {
            font-size: 1rem;
            font-weight: 600;
            color: var(--text-dark);
            margin-bottom: 6px;
            line-height: 1.3;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
            height: 2.6rem;
        }

        .product-desc {
            font-size: 0.8rem;
            color: var(--text-muted);
            margin-bottom: 12px;
            display: -webkit-box;
            -webkit-line-clamp: 1;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }

        .product-meta {
            margin-top: auto;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .product-price {
            font-size: 1.15rem;
            font-weight: 700;
            color: var(--primary);
        }

        .add-to-cart-btn {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 12px;
            border-radius: 10px;
            font-weight: 600;
            font-size: 0.9rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            transition: var(--transition);
            width: 100%;
        }

        .add-to-cart-btn:strong {
            background-color: #735942;
        }

        /* Floating Actions Area */
        .floating-actions {
            position: fixed;
            bottom: 24px;
            right: 24px;
            display: flex;
            flex-direction: column;
            gap: 14px;
            z-index: 1000;
        }

        .floating-btn {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-decoration: none;
            box-shadow: 0 4px 15px rgba(0,0,0,0.15);
            cursor: pointer;
            border: none;
            position: relative;
            transition: var(--transition);
        }

        .floating-btn:hover {
            transform: scale(1.08);
        }

        .whatsapp-btn {
            background-color: #25D366;
        }

        .cart-btn {
            background-color: var(--primary);
        }

        .cart-count {
            position: absolute;
            top: -2px;
            right: -2px;
            background-color: var(--accent);
            color: var(--text-dark);
            font-size: 0.75rem;
            font-weight: 700;
            width: 22px;
            height: 22px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            border: 2px solid white;
        }

        /* Sliding Drawer / Modal Framework */
        .drawer-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.4);
            backdrop-filter: blur(4px);
            z-index: 2000;
            opacity: 0;
            visibility: hidden;
            transition: var(--transition);
        }

        .drawer-overlay.active {
            opacity: 1;
            visibility: visible;
        }

        .drawer {
            position: fixed;
            top: 0;
            right: -100%;
            width: 100%;
            max-width: 460px;
            height: 100%;
            background-color: var(--bg-card);
            z-index: 2001;
            box-shadow: -5px 0 25px rgba(0,0,0,0.15);
            transition: right 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            display: flex;
            flex-direction: column;
        }

        .drawer.active {
            right: 0;
        }

        .drawer-header {
            padding: 20px;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: var(--primary-light);
        }

        .drawer-header h2 {
            font-family: 'Playfair Display', serif;
            font-size: 1.4rem;
            color: var(--primary);
        }

        .close-btn {
            background: none;
            border: none;
            font-size: 1.5rem;
            color: var(--text-muted);
            cursor: pointer;
            padding: 5px;
        }

        .drawer-body {
            flex-grow: 1;
            overflow-y: auto;
            padding: 20px;
        }

        /* Cart View items UI */
        .cart-empty-msg {
            text-align: center;
            padding: 40px 20px;
            color: var(--text-muted);
        }

        .cart-empty-msg svg {
            margin-bottom: 15px;
            color: var(--border-color);
        }

        .cart-item {
            display: flex;
            gap: 15px;
            padding-bottom: 15px;
            margin-bottom: 15px;
            border-bottom: 1px solid var(--border-color);
            align-items: center;
        }

        .cart-item-img {
            width: 70px;
            height: 75px;
            object-fit: cover;
            border-radius: 8px;
            border: 1px solid var(--border-color);
        }

        .cart-item-details {
            flex-grow: 1;
        }

        .cart-item-name {
            font-size: 0.95rem;
            font-weight: 600;
            margin-bottom: 4px;
        }

        .cart-item-price {
            font-size: 0.9rem;
            color: var(--primary);
            font-weight: 700;
            margin-bottom: 8px;
        }

        .cart-item-actions {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .quantity-control {
            display: flex;
            align-items: center;
            border: 1px solid var(--border-color);
            border-radius: 6px;
            background-color: var(--bg-main);
        }

        .qty-btn {
            background: none;
            border: none;
            width: 32px;
            height: 32px;
            font-size: 1.1rem;
            cursor: pointer;
            color: var(--text-dark);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .qty-val {
            width: 30px;
            text-align: center;
            font-size: 0.9rem;
            font-weight: 600;
        }

        .remove-item-btn {
            background: none;
            border: none;
            color: #d32f2f;
            cursor: pointer;
            font-size: 0.85rem;
            font-weight: 500;
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .drawer-footer {
            padding: 20px;
            border-top: 1px solid var(--border-color);
            background-color: #fdfcfb;
        }

        .total-row {
            display: flex;
            justify-content: space-between;
            font-size: 1.2rem;
            font-weight: 700;
            margin-bottom: 15px;
            color: var(--text-dark);
        }

        .checkout-btn {
            background-color: var(--primary);
            color: white;
            border: none;
            width: 100%;
            padding: 15px;
            border-radius: 12px;
            font-weight: 600;
            font-size: 1rem;
            cursor: pointer;
            transition: var(--transition);
        }

        /* Form Controls Setup */
        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 6px;
            color: var(--text-dark);
        }

        .form-group input, .form-group textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            font-size: 0.95rem;
            background-color: var(--bg-main);
            outline: none;
            transition: var(--transition);
        }

        .form-group input:focus, .form-group textarea:focus {
            border-color: var(--primary);
            background-color: white;
            box-shadow: 0 0 0 3px rgba(142, 111, 84, 0.15);
        }

        .back-to-cart-btn {
            background: none;
            border: none;
            color: var(--text-muted);
            font-weight: 600;
            font-size: 0.9rem;
            cursor: pointer;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        /* Success screen modal overlay overrides */
        .success-panel {
            text-align: center;
            padding: 30px 10px;
        }

        .success-icon {
            width: 70px;
            height: 70px;
            background-color: rgba(46, 125, 50, 0.1);
            color: var(--success);
            border-radius: 50%;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
        }

        .success-panel h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.6rem;
            margin-bottom: 10px;
            color: var(--text-dark);
        }

        .success-panel p {
            color: var(--text-muted);
            font-size: 0.95rem;
            margin-bottom: 25px;
        }

        .wa-confirm-btn {
            background-color: #25D366;
            color: white;
            text-decoration: none;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            padding: 14px;
            border-radius: 10px;
            font-weight: 600;
            box-shadow: 0 4px 12px rgba(37, 211, 102, 0.2);
            margin-bottom: 12px;
        }

        .close-success-btn {
            background-color: var(--primary-light);
            color: var(--primary);
            border: none;
            display: block;
            width: 100%;
            padding: 12px;
            border-radius: 10px;
            font-weight: 600;
            cursor: pointer;
        }

        /* CSS Animation Framework Elements */
        @keyframes pop {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }

        .cart-pop {
            animation: pop 0.3s ease-in-out;
        }
    </style>
</head>
<body>

    <!-- Upper Info Notification Strip -->
    <div class="shop-info-bar">
        📍 Location: Dawlatpur, Narayanganj, Bangladesh | Fast Home Delivery
    </div>

    <!-- Website Header Panel -->
    <header>
        <div class="container">
            <div class="shop-brand">
                <h1>SAVORA</h1>
                <p>Savor Your Beauty</p>
            </div>
        </div>
    </header>

    <!-- Horizontal Carousel Category Filter Block -->
    <div class="category-container">
        <div class="category-slider" id="categorySlider">
            <button class="category-btn active" onclick="filterCategory('all')">All Products</button>
            <button class="category-btn" onclick="filterCategory('Cosmetics')">Cosmetics</button>
            <button class="category-btn" onclick="filterCategory('Beauty')">Beauty</button>
            <button class="category-btn" onclick="filterCategory('Skin care')">Skin care</button>
        </div>
    </div>

    <!-- Main Content Grid Area -->
    <main class="container products-section">
        <div class="products-grid" id="productsGrid">
            <!-- JavaScript dynamically will inject item assets structured cards here -->
        </div>
    </main>

    <!-- Global Floating Action Anchor Nodes -->
    <div class="floating-actions">
        <!-- Floating WhatsApp Live Chat Link -->
        <a href="https://wa.me/966558704371" class="floating-btn whatsapp-btn" target="_blank" aria-label="Chat on WhatsApp" title="Chat with us">
            <svg width="28" height="28" fill="currentColor" viewBox="0 0 16 16">
                <path d="M13.601 2.326A7.854 7.854 0 0 0 7.994 0C3.627 0 .068 3.558.064 7.926c0 1.399.366 2.76 1.057 3.965L0 16l4.204-1.102a7.933 7.933 0 0 0 3.79.965h.004c4.368 0 7.926-3.558 7.93-7.93A7.898 7.898 0 0 0 13.6 2.326zM7.994 14.521a6.573 6.573 0 0 1-3.356-.92l-.24-.144-2.494.654.666-2.433-.156-.251a6.56 6.56 0 0 1-1.007-3.505c1.1-4.2 4.566-7.46 8.854-7.46 4.175 0 7.57 3.394 7.575 7.577-.005 4.177-3.4 7.578-7.575 7.578zM11.569 9.43c-.195-.1-.154-.195-.454-.34s-1.457-.718-1.682-.8c-.225-.084-.388-.124-.55.124-.162.248-.625.8-.765.957-.14.157-.28.177-.475.082-.195-.1-.82-.304-1.56-.963-.574-.513-.96-1.148-1.072-1.34-.113-.192-.012-.296.086-.392.088-.086.195-.228.293-.34.1-.114.133-.192.198-.321.065-.13.033-.245-.017-.34-.05-.1-.425-1.024-.582-1.405-.154-.373-.324-.323-.454-.33-.118-.006-.254-.007-.39-.007s-.357.05-.544.254c-.188.203-.72.704-.72 1.718 0 1.013.738 1.992.84 2.13.101.137 1.452 2.217 3.518 3.102.492.211.875.338 1.174.433.496.158.948.135 1.304.083.397-.058 1.206-.494 1.377-1.03.17-.535.17-1.024.12-1.119-.049-.095-.175-.145-.37-.245z"/>
            </svg>
        </a>
        <!-- Sticky Cart Icon Action Launcher -->
        <button class="floating-btn cart-btn" id="floatingCartBtn" onclick="toggleDrawer('cartDrawer')" aria-label="View Shopping Cart">
            <svg width="24" height="24" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"/>
            </svg>
            <span class="cart-count" id="cartBadgeCount">0</span>
        </button>
    </div>

    <!-- UI Overlay Backdrop Core system -->
    <div class="drawer-overlay" id="drawerOverlay" onclick="closeAllDrawers()"><
