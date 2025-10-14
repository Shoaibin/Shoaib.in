<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Navia Mart - Online Shopping</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* CSS Variables for Colors */
        :root {
            --navia-blue: #2874f0;
            --navia-light-blue: #f1f8ff;
            --navia-yellow: #ffe500;
            --navia-orange: #ff9f00;
            --navia-green: #26a541;
            --white: #ffffff;
            --light-gray: #f5f5f5;
            --gray: #878787;
            --dark-gray: #212121;
            --green: #388e3c;
            --red: #ff6161;
        }

        /* Global Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--light-gray);
            color: var(--dark-gray);
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        a {
            text-decoration: none;
            color: inherit;
        }

        button {
            cursor: pointer;
            border: none;
            outline: none;
        }

        /* Header Styles */
        header {
            background-color: var(--navia-blue);
            color: var(--white);
            box-shadow: 0 1px 4px rgba(0, 0, 0, 0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .header-top {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 10px 0;
        }

        .logo {
            display: flex;
            align-items: center;
            font-size: 24px;
            font-weight: bold;
        }

        .logo-icon {
            background: linear-gradient(135deg, var(--navia-blue), var(--navia-green));
            color: var(--white);
            width: 36px;
            height: 36px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 10px;
            font-weight: bold;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        }

        .search-bar {
            flex: 1;
            max-width: 500px;
            margin: 0 20px;
            position: relative;
        }

        .search-bar input {
            width: 100%;
            padding: 10px 15px;
            border-radius: 4px;
            border: none;
            font-size: 14px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        .search-bar button {
            position: absolute;
            right: 0;
            top: 0;
            height: 100%;
            background-color: var(--navia-blue);
            color: var(--white);
            padding: 0 15px;
            border: none;
            border-radius: 0 4px 4px 0;
        }

        .search-suggestions {
            position: absolute;
            top: 100%;
            left: 0;
            right: 0;
            background-color: var(--white);
            color: var(--dark-gray);
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            border-radius: 0 0 4px 4px;
            display: none;
            z-index: 1001;
            max-height: 300px;
            overflow-y: auto;
        }

        .search-suggestions.active {
            display: block;
        }

        .suggestion-item {
            padding: 10px 15px;
            border-bottom: 1px solid var(--light-gray);
            cursor: pointer;
            display: flex;
            align-items: center;
        }

        .suggestion-item:hover {
            background-color: var(--light-gray);
        }

        .suggestion-item img {
            width: 40px;
            height: 40px;
            object-fit: contain;
            margin-right: 10px;
            border-radius: 4px;
        }

        .header-actions {
            display: flex;
            align-items: center;
        }

        .header-action {
            margin-left: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            font-size: 12px;
            cursor: pointer;
            position: relative;
            transition: transform 0.2s;
        }

        .header-action:hover {
            transform: translateY(-2px);
        }

        .header-action i {
            font-size: 18px;
            margin-bottom: 2px;
        }

        .cart-count, .wishlist-count {
            background-color: var(--navia-orange);
            color: var(--white);
            border-radius: 50%;
            width: 18px;
            height: 18px;
            font-size: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            position: absolute;
            top: -5px;
            right: -5px;
        }

        .cart-wrapper, .wishlist-wrapper {
            position: relative;
        }

        /* Navigation */
        nav {
            background-color: var(--white);
            box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1);
        }

        .nav-links {
            display: flex;
            list-style: none;
            padding: 10px 0;
            overflow-x: auto;
        }

        .nav-links::-webkit-scrollbar {
            display: none;
        }

        .nav-link {
            padding: 8px 15px;
            white-space: nowrap;
            font-size: 14px;
            font-weight: 500;
            transition: color 0.3s;
        }

        .nav-link:hover {
            color: var(--navia-blue);
        }

        /* Page Navigation */
        .page-navigation {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
            padding: 10px 0;
        }

        .back-btn, .home-btn {
            background-color: var(--navia-blue);
            color: var(--white);
            padding: 8px 15px;
            border-radius: 4px;
            font-size: 14px;
            font-weight: 500;
            display: flex;
            align-items: center;
            margin-right: 10px;
            transition: background-color 0.3s;
        }

        .back-btn:hover, .home-btn:hover {
            background-color: #1c6ae4;
        }

        .back-btn i, .home-btn i {
            margin-right: 5px;
        }

        .page-title {
            font-size: 22px;
            font-weight: 600;
        }

        /* Main Content */
        .main-content {
            padding: 20px 0;
            min-height: calc(100vh - 200px);
        }

        /* Page Sections */
        .page {
            display: none;
        }

        .page.active {
            display: block;
            animation: fadeIn 0.5s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Banner Slider */
        .banner-slider {
            position: relative;
            height: 280px;
            margin-bottom: 20px;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        .banner-slide {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0;
            transition: opacity 0.5s ease-in-out;
            background-size: cover;
            background-position: center;
        }

        .banner-slide.active {
            opacity: 1;
        }

        .banner-slide-1 {
            background: linear-gradient(135deg, var(--navia-blue), #4a90e2);
        }

        .banner-slide-2 {
            background: linear-gradient(135deg, var(--navia-orange), #ffb74d);
        }

        .banner-slide-3 {
            background: linear-gradient(135deg, var(--navia-green), #4caf50);
        }

        .banner-content {
            position: absolute;
            top: 50%;
            left: 50px;
            transform: translateY(-50%);
            color: var(--white);
            max-width: 50%;
        }

        .banner-content h2 {
            font-size: 32px;
            margin-bottom: 10px;
        }

        .banner-content p {
            font-size: 16px;
            margin-bottom: 20px;
        }

        .banner-btn {
            background-color: var(--white);
            color: var(--navia-blue);
            padding: 10px 20px;
            border-radius: 4px;
            font-weight: 600;
            display: inline-block;
            transition: transform 0.3s;
        }

        .banner-btn:hover {
            transform: translateY(-2px);
        }

        .slider-dots {
            position: absolute;
            bottom: 15px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
        }

        .dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background-color: rgba(255, 255, 255, 0.5);
            margin: 0 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .dot.active {
            background-color: var(--white);
        }

        /* Categories Section */
        .section-title {
            font-size: 22px;
            margin: 30px 0 15px;
            font-weight: 600;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .view-all {
            font-size: 14px;
            color: var(--navia-blue);
            font-weight: 500;
        }

        .categories {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            gap: 15px;
            margin-bottom: 30px;
        }

        .category {
            background-color: var(--white);
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
        }

        .category:hover {
            transform: translateY(-5px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
        }

        .category-icon {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background-color: var(--navia-light-blue);
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 10px;
            font-size: 24px;
            color: var(--navia-blue);
        }

        .category-name {
            font-size: 14px;
            font-weight: 500;
        }

        /* Products Section */
        .products {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 20px;
        }

        .product-card {
            background-color: var(--white);
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            position: relative;
            animation: slideUp 0.5s ease-out;
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .product-image {
            height: 180px;
            background-color: var(--light-gray);
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            position: relative;
        }

        .product-image img {
            width: 100%;
            height: 100%;
            object-fit: contain;
            transition: transform 0.3s;
            padding: 10px;
        }

        .product-card:hover .product-image img {
            transform: scale(1.05);
        }

        .product-info {
            padding: 15px;
        }

        .product-title {
            font-size: 14px;
            margin-bottom: 8px;
            height: 40px;
            overflow: hidden;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
        }

        .product-price {
            display: flex;
            align-items: center;
            margin-bottom: 8px;
        }

        .current-price {
            font-size: 18px;
            font-weight: 600;
            color: var(--dark-gray);
            margin-right: 8px;
        }

        .original-price {
            font-size: 14px;
            color: var(--gray);
            text-decoration: line-through;
        }

        .discount {
            color: var(--green);
            font-size: 13px;
            font-weight: 500;
            margin-left: 8px;
        }

        .product-rating {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }

        .rating-stars {
            color: var(--navia-orange);
            margin-right: 5px;
        }

        .rating-count {
            font-size: 12px;
            color: var(--gray);
        }

        .out-of-stock {
            position: absolute;
            top: 10px;
            left: 10px;
            background-color: var(--red);
            color: var(--white);
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 12px;
            font-weight: 500;
        }

        .product-actions {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
        }

        .add-to-cart, .wishlist, .buy-now {
            background-color: var(--navia-blue);
            color: var(--white);
            padding: 8px 12px;
            border-radius: 4px;
            font-size: 12px;
            font-weight: 500;
            transition: background-color 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .add-to-cart:hover, .wishlist:hover, .buy-now:hover {
            background-color: #1c6ae4;
        }

        .wishlist {
            background-color: transparent;
            color: var(--gray);
            border: 1px solid var(--gray);
        }

        .wishlist:hover {
            background-color: var(--light-gray);
            color: var(--dark-gray);
        }

        .wishlist.active {
            color: var(--red);
            border-color: var(--red);
            background-color: rgba(255, 97, 97, 0.1);
        }

        .buy-now {
            background-color: var(--navia-orange);
            width: 100%;
            margin-top: 8px;
        }

        .buy-now:hover {
            background-color: #e59400;
        }

        /* Checkout Page */
        .checkout-container {
            display: grid;
            grid-template-columns: 1fr 350px;
            gap: 30px;
        }

        .checkout-section {
            background-color: var(--white);
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
        }

        .checkout-title {
            font-size: 18px;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid var(--light-gray);
        }

        .address-form {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group.full-width {
            grid-column: 1 / -1;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-size: 14px;
            font-weight: 500;
        }

        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 14px;
        }

        .form-group textarea {
            height: 80px;
            resize: vertical;
        }

        .saved-addresses {
            margin-top: 20px;
        }

        .address-card {
            border: 1px solid #ddd;
            border-radius: 4px;
            padding: 15px;
            margin-bottom: 10px;
            cursor: pointer;
            transition: border-color 0.3s;
        }

        .address-card:hover {
            border-color: var(--navia-blue);
        }

        .address-card.selected {
            border-color: var(--navia-blue);
            background-color: var(--navia-light-blue);
        }

        .address-name {
            font-weight: 600;
            margin-bottom: 5px;
        }

        .payment-methods {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            gap: 10px;
        }

        .payment-method {
            border: 1px solid #ddd;
            border-radius: 4px;
            padding: 15px;
            text-align: center;
            cursor: pointer;
            transition: border-color 0.3s;
        }

        .payment-method:hover {
            border-color: var(--navia-blue);
        }

        .payment-method.selected {
            border-color: var(--navia-blue);
            background-color: var(--navia-light-blue);
        }

        .payment-icon {
            font-size: 24px;
            margin-bottom: 8px;
            color: var(--navia-blue);
        }

        .order-summary-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
            padding-bottom: 10px;
            border-bottom: 1px solid var(--light-gray);
        }

        .order-total {
            display: flex;
            justify-content: space-between;
            font-size: 18px;
            font-weight: 600;
            margin-top: 15px;
            padding-top: 15px;
            border-top: 1px solid var(--light-gray);
        }

        .place-order-btn {
            width: 100%;
            background-color: var(--navia-orange);
            color: var(--white);
            padding: 12px;
            border-radius: 4px;
            font-size: 16px;
            font-weight: 600;
            margin-top: 20px;
            transition: background-color 0.3s;
        }

        .place-order-btn:hover {
            background-color: #e59400;
        }

        /* Cart Page */
        .cart-items {
            background-color: var(--white);
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
        }

        .cart-item {
            display: flex;
            padding: 15px 0;
            border-bottom: 1px solid var(--light-gray);
        }

        .cart-item:last-child {
            border-bottom: none;
        }

        .cart-item-image {
            width: 100px;
            height: 100px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 15px;
        }

        .cart-item-image img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
        }

        .cart-item-details {
            flex: 1;
        }

        .cart-item-title {
            font-size: 16px;
            margin-bottom: 5px;
        }

        .cart-item-price {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 10px;
        }

        .cart-item-actions {
            display: flex;
            align-items: center;
        }

        .quantity-control {
            display: flex;
            align-items: center;
            margin-right: 15px;
        }

        .quantity-btn {
            width: 30px;
            height: 30px;
            background-color: var(--light-gray);
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            border-radius: 4px;
        }

        .quantity-input {
            width: 40px;
            height: 30px;
            text-align: center;
            border: 1px solid #ddd;
            margin: 0 5px;
            border-radius: 4px;
        }

        .remove-item {
            color: var(--red);
            cursor: pointer;
            font-size: 14px;
        }

        .cart-summary {
            background-color: var(--white);
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
            margin-top: 20px;
        }

        .proceed-to-checkout {
            width: 100%;
            background-color: var(--navia-orange);
            color: var(--white);
            padding: 12px;
            border-radius: 4px;
            font-size: 16px;
            font-weight: 600;
            margin-top: 15px;
        }

        /* Footer */
        footer {
            background-color: var(--dark-gray);
            color: var(--white);
            padding: 40px 0 20px;
            margin-top: 40px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
            margin-bottom: 30px;
        }

        .footer-column h3 {
            font-size: 16px;
            margin-bottom: 15px;
            color: var(--gray);
            text-transform: uppercase;
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 10px;
        }

        .footer-links a {
            color: var(--white);
            font-size: 14px;
            transition: color 0.3s;
        }

        .footer-links a:hover {
            color: var(--navia-blue);
        }

        .footer-bottom {
            border-top: 1px solid #424242;
            padding-top: 20px;
            text-align: center;
            font-size: 14px;
            color: var(--gray);
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 2000;
            align-items: center;
            justify-content: center;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background-color: var(--white);
            border-radius: 8px;
            width: 90%;
            max-width: 400px;
            padding: 30px;
            position: relative;
            animation: modalFadeIn 0.3s;
        }

        @keyframes modalFadeIn {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .close-modal {
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 20px;
            cursor: pointer;
            color: var(--gray);
        }

        .modal-title {
            font-size: 22px;
            margin-bottom: 20px;
            text-align: center;
        }

        .submit-btn {
            width: 100%;
            background-color: var(--navia-blue);
            color: var(--white);
            padding: 12px;
            border-radius: 4px;
            font-size: 16px;
            font-weight: 600;
            margin-top: 10px;
            transition: background-color 0.3s;
        }

        .submit-btn:hover {
            background-color: #1c6ae4;
        }

        .form-footer {
            text-align: center;
            margin-top: 15px;
            font-size: 14px;
        }

        .form-footer a {
            color: var(--navia-blue);
            font-weight: 500;
        }

        /* Toast Notification */
        .toast {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: var(--green);
            color: var(--white);
            padding: 12px 20px;
            border-radius: 4px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            z-index: 3000;
            display: flex;
            align-items: center;
            transform: translateY(100px);
            opacity: 0;
            transition: transform 0.3s, opacity 0.3s;
        }

        .toast.active {
            transform: translateY(0);
            opacity: 1;
        }

        .toast i {
            margin-right: 8px;
        }

        /* Responsive Styles */
        @media (max-width: 768px) {
            .header-top {
                flex-wrap: wrap;
            }
            
            .search-bar {
                order: 3;
                max-width: 100%;
                margin: 10px 0 0;
            }
            
            .banner-content {
                max-width: 70%;
                left: 20px;
            }
            
            .banner-content h2 {
                font-size: 24px;
            }
            
            .categories {
                grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
            }
            
            .products {
                grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
            }
            
            .checkout-container {
                grid-template-columns: 1fr;
            }
            
            .address-form {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 480px) {
            .header-action span {
                display: none;
            }
            
            .banner-content {
                max-width: 80%;
            }
            
            .banner-content h2 {
                font-size: 20px;
            }
            
            .banner-content p {
                font-size: 14px;
            }
            
            .categories {
                grid-template-columns: repeat(3, 1fr);
            }
            
            .products {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .cart-item {
                flex-direction: column;
            }
            
            .cart-item-image {
                width: 100%;
                height: 150px;
                margin-right: 0;
                margin-bottom: 10px;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container">
            <div class="header-top">
                <a href="#" class="logo" id="home-link">
                    <div class="logo-icon">N</div>
                    <span>Navia Mart</span>
                </a>
                
                <div class="search-bar">
                    <input type="text" placeholder="Search for products, brands and more" id="search-input">
                    <button><i class="fas fa-search"></i></button>
                    <div class="search-suggestions" id="search-suggestions">
                        <!-- Search suggestions will be populated by JavaScript -->
                    </div>
                </div>
                
                <div class="header-actions">
                    <div class="header-action" id="login-btn">
                        <i class="far fa-user"></i>
                        <span>Login</span>
                    </div>
                    <div class="header-action wishlist-wrapper" id="wishlist-btn">
                        <i class="far fa-heart"></i>
                        <span>Wishlist</span>
                        <div class="wishlist-count">0</div>
                    </div>
                    <div class="header-action cart-wrapper" id="cart-btn">
                        <i class="fas fa-shopping-cart"></i>
                        <span>Cart</span>
                        <div class="cart-count">0</div>
                    </div>
                </div>
            </div>
        </div>
        
        <nav>
            <div class="container">
                <ul class="nav-links">
                    <li><a href="#" class="nav-link" data-category="all">Top Offers</a></li>
                    <li><a href="#" class="nav-link" data-category="Mobiles">Mobiles</a></li>
                    <li><a href="#" class="nav-link" data-category="Electronics">Electronics</a></li>
                    <li><a href="#" class="nav-link" data-category="Fashion">Fashion</a></li>
                    <li><a href="#" class="nav-link" data-category="Home">Home & Kitchen</a></li>
                    <li><a href="#" class="nav-link" data-category="Appliances">Appliances</a></li>
                    <li><a href="#" class="nav-link" data-category="Beauty">Beauty</a></li>
                    <li><a href="#" class="nav-link" data-category="Grocery">Grocery</a></li>
                </ul>
            </div>
        </nav>
    </header>

    <!-- Main Content -->
    <main class="main-content">
        <div class="container">
            <!-- Home Page -->
            <div class="page active" id="home-page">
                <!-- Banner Slider -->
                <div class="banner-slider">
                    <div class="banner-slide banner-slide-1 active">
                        <div class="banner-content">
                            <h2>Biggest Sale Ever!</h2>
                            <p>Up to 70% off on electronics, fashion, home appliances and more</p>
                            <a href="#" class="banner-btn">Shop Now</a>
                        </div>
                    </div>
                    <div class="banner-slide banner-slide-2">
                        <div class="banner-content">
                            <h2>New Smartphones</h2>
                            <p>Latest models with amazing features and discounts</p>
                            <a href="#" class="banner-btn">Explore</a>
                        </div>
                    </div>
                    <div class="banner-slide banner-slide-3">
                        <div class="banner-content">
                            <h2>Festive Season Offers</h2>
                            <p>Special discounts and cashback on all products</p>
                            <a href="#" class="banner-btn">Grab Now</a>
                        </div>
                    </div>
                    
                    <div class="slider-dots">
                        <div class="dot active" data-slide="0"></div>
                        <div class="dot" data-slide="1"></div>
                        <div class="dot" data-slide="2"></div>
                    </div>
                </div>
                
                <!-- Categories Section -->
                <h2 class="section-title">Shop By Category</h2>
                <div class="categories">
                    <div class="category" data-category="Mobiles">
                        <div class="category-icon">
                            <i class="fas fa-mobile-alt"></i>
                        </div>
                        <div class="category-name">Mobiles</div>
                    </div>
                    <div class="category" data-category="Electronics">
                        <div class="category-icon">
                            <i class="fas fa-laptop"></i>
                        </div>
                        <div class="category-name">Electronics</div>
                    </div>
                    <div class="category" data-category="Fashion">
                        <div class="category-icon">
                            <i class="fas fa-tshirt"></i>
                        </div>
                        <div class="category-name">Fashion</div>
                    </div>
                    <div class="category" data-category="Home">
                        <div class="category-icon">
                            <i class="fas fa-home"></i>
                        </div>
                        <div class="category-name">Home</div>
                    </div>
                    <div class="category" data-category="Furniture">
                        <div class="category-icon">
                            <i class="fas fa-couch"></i>
                        </div>
                        <div class="category-name">Furniture</div>
                    </div>
                    <div class="category" data-category="Sports">
                        <div class="category-icon">
                            <i class="fas fa-dumbbell"></i>
                        </div>
                        <div class="category-name">Sports</div>
                    </div>
                    <div class="category" data-category="Books">
                        <div class="category-icon">
                            <i class="fas fa-book"></i>
                        </div>
                        <div class="category-name">Books</div>
                    </div>
                    <div class="category" data-category="Automotive">
                        <div class="category-icon">
                            <i class="fas fa-car"></i>
                        </div>
                        <div class="category-name">Automotive</div>
                    </div>
                </div>
                
                <!-- Top Offers Section -->
                <h2 class="section-title">
                    Top Offers
                    <a href="#" class="view-all" id="view-all-offers">View All</a>
                </h2>
                <div class="products" id="products-container">
                    <!-- Products will be populated by JavaScript -->
                </div>
                
                <!-- Mobile Phones Section -->
                <h2 class="section-title">
                    Mobile Phones
                    <a href="#" class="view-all" id="view-all-mobiles">View All</a>
                </h2>
                <div class="products" id="mobile-products-container">
                    <!-- Mobile products will be populated by JavaScript -->
                </div>
            </div>

            <!-- Products Page -->
            <div class="page" id="products-page">
                <div class="page-navigation">
                    <button class="back-btn" id="products-back-btn"><i class="fas fa-arrow-left"></i> Back</button>
                    <button class="home-btn" id="products-home-btn"><i class="fas fa-home"></i> Home</button>
                    <div class="page-title" id="products-page-title">All Products</div>
                </div>
                <div class="products" id="all-products-container">
                    <!-- All products will be populated by JavaScript -->
                </div>
            </div>

            <!-- Product Detail Page -->
            <div class="page" id="product-detail-page">
                <div class="page-navigation">
                    <button class="back-btn" id="detail-back-btn"><i class="fas fa-arrow-left"></i> Back</button>
                    <button class="home-btn" id="detail-home-btn"><i class="fas fa-home"></i> Home</button>
                    <div class="page-title">Product Details</div>
                </div>
                <!-- Product details will be populated by JavaScript -->
            </div>

            <!-- Cart Page -->
            <div class="page" id="cart-page">
                <div class="page-navigation">
                    <button class="back-btn" id="cart-back-btn"><i class="fas fa-arrow-left"></i> Back</button>
                    <button class="home-btn" id="cart-home-btn"><i class="fas fa-home"></i> Home</button>
                    <div class="page-title">My Cart</div>
                </div>
                <div class="cart-items" id="cart-items-container">
                    <!-- Cart items will be populated by JavaScript -->
                </div>
                <div class="cart-summary">
                    <div class="order-summary-item">
                        <span>Total Items:</span>
                        <span id="cart-total-items">0</span>
                    </div>
                    <div class="order-summary-item">
                        <span>Subtotal:</span>
                        <span id="cart-subtotal">₹0</span>
                    </div>
                    <div class="order-summary-item">
                        <span>Shipping:</span>
                        <span>FREE</span>
                    </div>
                    <div class="order-total">
                        <span>Total:</span>
                        <span id="cart-total">₹0</span>
                    </div>
                    <button class="proceed-to-checkout" id="proceed-to-checkout">Proceed to Checkout</button>
                </div>
            </div>

            <!-- Wishlist Page -->
            <div class="page" id="wishlist-page">
                <div class="page-navigation">
                    <button class="back-btn" id="wishlist-back-btn"><i class="fas fa-arrow-left"></i> Back</button>
                    <button class="home-btn" id="wishlist-home-btn"><i class="fas fa-home"></i> Home</button>
                    <div class="page-title">My Wishlist</div>
                </div>
                <div class="products" id="wishlist-products-container">
                    <!-- Wishlist products will be populated by JavaScript -->
                </div>
            </div>

            <!-- Checkout Page -->
            <div class="page" id="checkout-page">
                <div class="page-navigation">
                    <button class="back-btn" id="checkout-back-btn"><i class="fas fa-arrow-left"></i> Back</button>
                    <button class="home-btn" id="checkout-home-btn"><i class="fas fa-home"></i> Home</button>
                    <div class="page-title">Checkout</div>
                </div>
                <div class="checkout-container">
                    <div class="checkout-left">
                        <div class="checkout-section">
                            <h3 class="checkout-title">Delivery Address</h3>
                            <div class="address-form">
                                <div class="form-group">
                                    <label for="full-name">Full Name</label>
                                    <input type="text" id="full-name" required>
                                </div>
                                <div class="form-group">
                                    <label for="phone">Phone Number</label>
                                    <input type="tel" id="phone" required>
                                </div>
                                <div class="form-group full-width">
                                    <label for="address">Address</label>
                                    <textarea id="address" required></textarea>
                                </div>
                                <div class="form-group">
                                    <label for="city">City</label>
                                    <input type="text" id="city" required>
                                </div>
                                <div class="form-group">
                                    <label for="state">State</label>
                                    <input type="text" id="state" required>
                                </div>
                                <div class="form-group">
                                    <label for="pincode">Pincode</label>
                                    <input type="text" id="pincode" required>
                                </div>
                            </div>
                        </div>
                        
                        <div class="checkout-section">
                            <h3 class="checkout-title">Payment Method</h3>
                            <div class="payment-methods">
                                <div class="payment-method" data-method="card">
                                    <div class="payment-icon">
                                        <i class="far fa-credit-card"></i>
                                    </div>
                                    <div>Credit/Debit Card</div>
                                </div>
                                <div class="payment-method" data-method="upi">
                                    <div class="payment-icon">
                                        <i class="fas fa-mobile-alt"></i>
                                    </div>
                                    <div>UPI</div>
                                </div>
                                <div class="payment-method" data-method="cod">
                                    <div class="payment-icon">
                                        <i class="fas fa-money-bill-wave"></i>
                                    </div>
                                    <div>Cash on Delivery</div>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="checkout-right">
                        <div class="checkout-section">
                            <h3 class="checkout-title">Order Summary</h3>
                            <div id="checkout-order-summary">
                                <!-- Order summary will be populated by JavaScript -->
                            </div>
                            <div class="order-total">
                                <span>Total:</span>
                                <span id="checkout-total">₹0</span>
                            </div>
                            <button class="place-order-btn" id="place-order-btn">Place Order</button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Order Confirmation Page -->
            <div class="page" id="order-confirmation-page">
                <div class="page-navigation">
                    <button class="home-btn" id="confirmation-home-btn"><i class="fas fa-home"></i> Home</button>
                    <div class="page-title">Order Confirmation</div>
                </div>
                <div class="checkout-section" style="text-align: center; padding: 40px;">
                    <i class="fas fa-check-circle" style="font-size: 60px; color: var(--green); margin-bottom: 20px;"></i>
                    <h2 style="margin-bottom: 10px;">Order Placed Successfully!</h2>
                    <p style="margin-bottom: 20px; color: var(--gray);">Thank you for your purchase. Your order has been confirmed.</p>
                    <p style="margin-bottom: 30px; font-weight: 600;">Order ID: #NAVIA123456</p>
                    <button class="submit-btn" id="continue-shopping-btn">Continue Shopping</button>
                </div>
            </div>
        </div>
    </main>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>About</h3>
                    <ul class="footer-links">
                        <li><a href="#">Contact Us</a></li>
                        <li><a href="#">About Us</a></li>
                        <li><a href="#">Careers</a></li>
                        <li><a href="#">Navia Mart Stories</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Help</h3>
                    <ul class="footer-links">
                        <li><a href="#">Payments</a></li>
                        <li><a href="#">Shipping</a></li>
                        <li><a href="#">Cancellation & Returns</a></li>
                        <li><a href="#">FAQ</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Policy</h3>
                    <ul class="footer-links">
                        <li><a href="#">Return Policy</a></li>
                        <li><a href="#">Terms Of Use</a></li>
                        <li><a href="#">Security</a></li>
                        <li><a href="#">Privacy</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Social</h3>
                    <ul class="footer-links">
                        <li><a href="#">Facebook</a></li>
                        <li><a href="#">Twitter</a></li>
                        <li><a href="#">YouTube</a></li>
                        <li><a href="#">Instagram</a></li>
                    </ul>
                </div>
            </div>
            
            <div class="footer-bottom">
                <p>&copy; 2023 Navia Mart. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <!-- Login Modal -->
    <div class="modal" id="login-modal">
        <div class="modal-content">
            <span class="close-modal" id="close-login-modal">&times;</span>
            <h2 class="modal-title">Login</h2>
            <form id="login-form">
                <div class="form-group">
                    <label for="login-email">Email</label>
                    <input type="email" id="login-email" required>
                </div>
                <div class="form-group">
                    <label for="login-password">Password</label>
                    <input type="password" id="login-password" required>
                </div>
                <button type="submit" class="submit-btn">Login</button>
            </form>
            <div class="form-footer">
                <p>New to Navia Mart? <a href="#" id="show-signup">Create an account</a></p>
            </div>
        </div>
    </div>

    <!-- Signup Modal -->
    <div class="modal" id="signup-modal">
        <div class="modal-content">
            <span class="close-modal" id="close-signup-modal">&times;</span>
            <h2 class="modal-title">Sign Up</h2>
            <form id="signup-form">
                <div class="form-group">
                    <label for="signup-name">Full Name</label>
                    <input type="text" id="signup-name" required>
                </div>
                <div class="form-group">
                    <label for="signup-email">Email</label>
                    <input type="email" id="signup-email" required>
                </div>
                <div class="form-group">
                    <label for="signup-password">Password</label>
                    <input type="password" id="signup-password" required>
                </div>
                <div class="form-group">
                    <label for="signup-confirm-password">Confirm Password</label>
                    <input type="password" id="signup-confirm-password" required>
                </div>
                <button type="submit" class="submit-btn">Sign Up</button>
            </form>
            <div class="form-footer">
                <p>Already have an account? <a href="#" id="show-login">Login</a></p>
            </div>
        </div>
    </div>

    <!-- Toast Notification -->
    <div class="toast" id="toast">
        <i class="fas fa-check-circle"></i>
        <span id="toast-message">Product added to cart!</span>
    </div>

    <script>
        // Dummy product data with reliable image URLs
        const products = [
            {
                id: 1,
                name: "Samsung Galaxy S23 Ultra 5G",
                price: 124999,
                originalPrice: 139999,
                image: "https://images.unsplash.com/photo-1610945265064-0e34e5519bbf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8c2Ftc3VuZyUyMHBob25lfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60",
                rating: 4.5,
                reviews: 1245,
                category: "Mobiles",
                inStock: true,
                description: "The Samsung Galaxy S23 Ultra 5G features a 6.8-inch Dynamic AMOLED 2X display, Snapdragon 8 Gen 2 processor, and a 200MP main camera. With up to 1TB storage and S Pen support, it's the ultimate productivity and creativity device."
            },
            {
                id: 2,
                name: "Apple iPhone 14 Pro Max",
                price: 139900,
                originalPrice: 149900,
                image: "https://images.unsplash.com/photo-1592750475338-74b7b21085ab?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8aXBob25lfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60",
                rating: 4.7,
                reviews: 1890,
                category: "Mobiles",
                inStock: true,
                description: "iPhone 14 Pro Max features the Always-On display, the Dynamic Island, and an innovative 48MP Main camera. Powered by the A16 Bionic chip, it offers exceptional battery life and cutting-edge performance."
            },
            {
                id: 3,
                name: "Sony WH-1000XM4 Wireless Headphones",
                price: 24990,
                originalPrice: 29990,
                image: "https://images.unsplash.com/photo-1583394838336-acd977736f90?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8aGVhZHBob25lc3xlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60",
                rating: 4.6,
                reviews: 876,
                category: "Electronics",
                inStock: true,
                description: "Industry-leading noise cancellation with Dual Noise Sensor technology. Up to 30-hour battery life with quick charging. Touch sensor controls to pause/play/skip tracks, control volume, activate your voice assistant, and answer phone calls."
            },
            {
                id: 4,
                name: "Nike Air Max 270 React",
                price: 12995,
                originalPrice: 15995,
                image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8bmlrZSUyMHNob2VzfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60",
                rating: 4.3,
                reviews: 542,
                category: "Fashion",
                inStock: false,
                description: "The Nike Air Max 270 React SE combines a full-length React foam midsole with a large Max Air unit for all-day comfort. The sleek design and breathable upper make it perfect for everyday wear."
            },
            {
                id: 5,
                name: "MacBook Air M2",
                price: 114990,
                originalPrice: 119990,
                image: "https://images.unsplash.com/photo-1541807084-5c52b6b3adef?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NHx8bGFwdG9wfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60",
                rating: 4.8,
                reviews: 932,
                category: "Electronics",
                inStock: true,
                description: "MacBook Air with M2 chip features an all-new design, more powerful performance, and up to 18 hours of battery life. With a 13.6-inch Liquid Retina display, 1080p FaceTime HD camera, and MagSafe charging, it's the perfect laptop for work and play."
            },
            {
                id: 6,
                name: "Samsung 55 inch 4K Smart TV",
                price: 52999,
                originalPrice: 64999,
                image: "https://images.unsplash.com/photo-1593359677879-a4bb92f829d1?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8dHZ8ZW58MHx8MHx8fDA%3D&auto=format&fit=crop&w=500&q=60",
                rating: 4.4,
                reviews: 623,
                category: "Electronics",
                inStock: true,
                description: "Crystal 4K UHD Processor optimizes content to 4K for sharp details and vibrant colors. HDR enhances contrast for accurate colors and details. Smart TV with streaming services and voice assistants built-in."
            },
            {
                id: 7,
                name: "OnePlus Nord CE 3 Lite 5G",
                price: 19999,
                originalPrice: 22999,
                image: "https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8c21hcnRwaG9uZXxlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60",
                rating: 4.2,
                reviews: 1123,
                category: "Mobiles",
                inStock: true,
                description: "OnePlus Nord CE 3 Lite 5G features a 120Hz display, Snapdragon 695 processor, and a 108MP main camera. With 67W fast charging and a 5000mAh battery, it offers excellent performance at an affordable price."
            },
            {
                id: 8,
                name: "Adidas Ultraboost 22 Running Shoes",
                price: 17999,
                originalPrice: 19999,
                image: "https://images.unsplash.com/photo-1606107557195-0e29a4b5b4aa?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NXx8c2hvZXN8ZW58MHx8MHx8fDA%3D&auto=format&fit=crop&w=500&q=60",
                rating: 4.5,
                reviews: 387,
                category: "Fashion",
                inStock: true,
                description: "Ultraboost 22 shoes combine responsive cushioning and a flexible fit for a comfortable run. The Primeblue upper contains at least 50% Parley Ocean Plastic. Stretchweb outsole flexes naturally for an energized ride."
            },
            {
                id: 9,
                name: "Canon EOS R5 Mirrorless Camera",
                price: 289999,
                originalPrice: 329999,
                image: "https://images.unsplash.com/photo-1502920917128-1aa500764cbd?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8Y2FtZXJhfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60",
                rating: 4.7,
                reviews: 342,
                category: "Electronics",
                inStock: true,
                description: "The Canon EOS R5 features a 45MP full-frame CMOS sensor, 8K video recording, and advanced autofocus system. With in-body image stabilization and dual pixel CMOS AF, it's perfect for professional photography and videography."
            },
            {
                id: 10,
                name: "Dyson V11 Cordless Vacuum Cleaner",
                price: 49990,
                originalPrice: 59990,
                image: "https://images.unsplash.com/photo-1558618047-3c8c76ca7d13?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8dmFjdXVtJTIwY2xlYW5lcnxlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60",
                rating: 4.6,
                reviews: 567,
                category: "Appliances",
                inStock: true,
                description: "The Dyson V11 cordless vacuum cleaner features powerful suction, intelligent cleaning modes, and up to 60 minutes of fade-free power. With a LCD screen that shows performance in real-time, it's the ultimate cleaning tool."
            },
            {
                id: 11,
                name: "Apple Watch Series 8",
                price: 45900,
                originalPrice: 49900,
                image: "https://images.unsplash.com/photo-1579586337278-3f436f4bcfd2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8YXBwbGUlMjB3YXRjaHxlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60",
                rating: 4.5,
                reviews: 892,
                category: "Electronics",
                inStock: true,
                description: "Apple Watch Series 8 features temperature sensing, crash detection, and advanced health monitoring. With a larger display and faster charging, it helps you stay connected, active, and healthy."
            },
            {
                id: 12,
                name: "Samsung Galaxy Watch 5",
                price: 27999,
                originalPrice: 32999,
                image: "https://images.unsplash.com/photo-1551816230-ef5deaed4a26?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8c21hcnR3YXRjaHxlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=500&q=60",
                rating: 4.3,
                reviews: 456,
                category: "Electronics",
                inStock: true,
                description: "Samsung Galaxy Watch 5 features advanced health monitoring, GPS tracking, and long battery life. With a durable design and comprehensive fitness tracking, it's your perfect workout partner."
            }
        ];

        // Dummy search suggestions
        const searchSuggestions = [
            "Samsung Galaxy S23",
            "iPhone 14 Pro Max",
            "MacBook Air M2",
            "Sony Headphones",
            "Nike Shoes",
            "Adidas Ultraboost",
            "OnePlus Nord",
            "Samsung TV",
            "Canon Camera",
            "Dyson Vacuum",
            "Apple Watch",
            "Samsung Watch",
            "Mobile Phones",
            "Laptops",
            "Headphones",
            "Smart Watches"
        ];

        // DOM Elements
        const searchInput = document.getElementById('search-input');
        const searchSuggestionsEl = document.getElementById('search-suggestions');
        const productsContainer = document.getElementById('products-container');
        const mobileProductsContainer = document.getElementById('mobile-products-container');
        const allProductsContainer = document.getElementById('all-products-container');
        const wishlistProductsContainer = document.getElementById('wishlist-products-container');
        const productDetailPage = document.getElementById('product-detail-page');
        const cartItemsContainer = document.getElementById('cart-items-container');
        const checkoutOrderSummary = document.getElementById('checkout-order-summary');
        const loginBtn = document.getElementById('login-btn');
        const loginModal = document.getElementById('login-modal');
        const closeLoginModal = document.getElementById('close-login-modal');
        const signupModal = document.getElementById('signup-modal');
        const closeSignupModal = document.getElementById('close-signup-modal');
        const showSignup = document.getElementById('show-signup');
        const showLogin = document.getElementById('show-login');
        const loginForm = document.getElementById('login-form');
        const signupForm = document.getElementById('signup-form');
        const bannerSlides = document.querySelectorAll('.banner-slide');
        const dots = document.querySelectorAll('.dot');
        const cartCount = document.querySelector('.cart-count');
        const wishlistCount = document.querySelector('.wishlist-count');
        const cartBtn = document.getElementById('cart-btn');
        const wishlistBtn = document.getElementById('wishlist-btn');
        const homeLink = document.getElementById('home-link');
        const proceedToCheckout = document.getElementById('proceed-to-checkout');
        const placeOrderBtn = document.getElementById('place-order-btn');
        const continueShoppingBtn = document.getElementById('continue-shopping-btn');
        const viewAllOffers = document.getElementById('view-all-offers');
        const viewAllMobiles = document.getElementById('view-all-mobiles');
        const productsPageTitle = document.getElementById('products-page-title');
        const toast = document.getElementById('toast');
        const toastMessage = document.getElementById('toast-message');
        const pages = document.querySelectorAll('.page');
        const navLinks = document.querySelectorAll('.nav-link');
        const categories = document.querySelectorAll('.category');

        // Back and Home buttons
        const productsBackBtn = document.getElementById('products-back-btn');
        const productsHomeBtn = document.getElementById('products-home-btn');
        const detailBackBtn = document.getElementById('detail-back-btn');
        const detailHomeBtn = document.getElementById('detail-home-btn');
        const cartBackBtn = document.getElementById('cart-back-btn');
        const cartHomeBtn = document.getElementById('cart-home-btn');
        const wishlistBackBtn = document.getElementById('wishlist-back-btn');
        const wishlistHomeBtn = document.getElementById('wishlist-home-btn');
        const checkoutBackBtn = document.getElementById('checkout-back-btn');
        const checkoutHomeBtn = document.getElementById('checkout-home-btn');
        const confirmationHomeBtn = document.getElementById('confirmation-home-btn');

        // App State
        let cart = [];
        let wishlist = [];
        let currentPage = 'home-page';
        let currentCategory = 'all';
        let selectedPaymentMethod = null;
        let previousPage = 'home-page';

        // Initialize the app
        document.addEventListener('DOMContentLoaded', function() {
            renderProducts();
            startBannerSlider();
            setupEventListeners();
            updateCartCount();
            updateWishlistCount();
        });

        // Render products
        function renderProducts() {
            // Clear containers
            productsContainer.innerHTML = '';
            mobileProductsContainer.innerHTML = '';
            allProductsContainer.innerHTML = '';
            
            // Render all products
            products.forEach(product => {
                const productCard = createProductCard(product);
                productsContainer.appendChild(productCard);
                
                // Render only mobile products in mobile section
                if (product.category === 'Mobiles') {
                    const mobileProductCard = createProductCard(product);
                    mobileProductsContainer.appendChild(mobileProductCard);
                }
                
                // Render all products in all products container
                const allProductCard = createProductCard(product);
                allProductsContainer.appendChild(allProductCard);
            });
        }

        // Create product card HTML
        function createProductCard(product) {
            const discount = Math.round(((product.originalPrice - product.price) / product.originalPrice) * 100);
            const isInWishlist = wishlist.some(item => item.id === product.id);
            
            const productCard = document.createElement('div');
            productCard.className = 'product-card';
            productCard.setAttribute('data-id', product.id);
            productCard.innerHTML = `
                ${!product.inStock ? '<div class="out-of-stock">Out of Stock</div>' : ''}
                <div class="product-image">
                    <img src="${product.image}" alt="${product.name}" onerror="this.src='https://via.placeholder.com/200x200/cccccc/969696?text=Product+Image'">
                </div>
                <div class="product-info">
                    <div class="product-title">${product.name}</div>
                    <div class="product-price">
                        <span class="current-price">₹${product.price.toLocaleString()}</span>
                        <span class="original-price">₹${product.originalPrice.toLocaleString()}</span>
                        <span class="discount">${discount}% off</span>
                    </div>
                    <div class="product-rating">
                        <div class="rating-stars">
                            ${generateStarRating(product.rating)}
                        </div>
                        <div class="rating-count">(${product.reviews.toLocaleString()})</div>
                    </div>
                    <div class="product-actions">
                        <button class="add-to-cart" ${!product.inStock ? 'disabled' : ''}>
                            <i class="fas fa-shopping-cart"></i> Add to Cart
                        </button>
                        <button class="wishlist ${isInWishlist ? 'active' : ''}">
                            <i class="${isInWishlist ? 'fas' : 'far'} fa-heart"></i>
                        </button>
                    </div>
                    <button class="buy-now" ${!product.inStock ? 'disabled' : ''}>
                        <i class="fas fa-bolt"></i> Buy Now
                    </button>
                </div>
            `;
            
            // Add event listeners to buttons
            const addToCartBtn = productCard.querySelector('.add-to-cart');
            const wishlistBtn = productCard.querySelector('.wishlist');
            const buyNowBtn = productCard.querySelector('.buy-now');
            
            addToCartBtn.addEventListener('click', function() {
                if (product.inStock) {
                    addToCart(product);
                    showToast('Product added to cart!');
                }
            });
            
            wishlistBtn.addEventListener('click', function() {
                toggleWishlist(product, wishlistBtn);
            });
            
            buyNowBtn.addEventListener('click', function() {
                if (product.inStock) {
                    addToCart(product);
                    navigateToPage('cart-page');
                }
            });
            
            // Add click event to product card to view details
            productCard.addEventListener('click', function(e) {
                if (!e.target.closest('button')) {
                    showProductDetail(product);
                }
            });
            
            return productCard;
        }

        // Generate star rating HTML
        function generateStarRating(rating) {
            let stars = '';
            const fullStars = Math.floor(rating);
            const hasHalfStar = rating % 1 !== 0;
            
            for (let i = 0; i < fullStars; i++) {
                stars += '<i class="fas fa-star"></i>';
            }
            
            if (hasHalfStar) {
                stars += '<i class="fas fa-star-half-alt"></i>';
            }
            
            const emptyStars = 5 - Math.ceil(rating);
            for (let i = 0; i < emptyStars; i++) {
                stars += '<i class="far fa-star"></i>';
            }
            
            return stars;
        }

        // Show product detail page
        function showProductDetail(product) {
            const discount = Math.round(((product.originalPrice - product.price) / product.originalPrice) * 100);
            const isInWishlist = wishlist.some(item => item.id === product.id);
            
            productDetailPage.innerHTML = `
                <div class="product-detail">
                    <div class="checkout-section">
                        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 30px;">
                            <div class="product-image" style="height: 400px;">
                                <img src="${product.image}" alt="${product.name}" style="max-width: 100%; max-height: 100%; object-fit: contain;" onerror="this.src='https://via.placeholder.com/400x400/cccccc/969696?text=Product+Image'">
                            </div>
                            <div class="product-info">
                                <h1 style="font-size: 24px; margin-bottom: 10px;">${product.name}</h1>
                                <div class="product-rating" style="margin-bottom: 15px;">
                                    <div class="rating-stars">
                                        ${generateStarRating(product.rating)}
                                    </div>
                                    <div class="rating-count">${product.rating} (${product.reviews.toLocaleString()} reviews)</div>
                                </div>
                                <div class="product-price" style="margin-bottom: 20px;">
                                    <span class="current-price" style="font-size: 28px;">₹${product.price.toLocaleString()}</span>
                                    <span class="original-price" style="font-size: 18px;">₹${product.originalPrice.toLocaleString()}</span>
                                    <span class="discount" style="font-size: 16px;">${discount}% off</span>
                                </div>
                                <div style="margin-bottom: 20px;">
                                    <h3 style="margin-bottom: 10px;">Description</h3>
                                    <p>${product.description}</p>
                                </div>
                                <div class="product-actions" style="margin-top: 30px;">
                                    <button class="add-to-cart" style="padding: 12px 20px; font-size: 16px;" ${!product.inStock ? 'disabled' : ''}>
                                        <i class="fas fa-shopping-cart"></i> Add to Cart
                                    </button>
                                    <button class="wishlist ${isInWishlist ? 'active' : ''}" style="padding: 12px 20px; font-size: 16px; margin-left: 10px;">
                                        <i class="${isInWishlist ? 'fas' : 'far'} fa-heart"></i> ${isInWishlist ? 'Remove from Wishlist' : 'Add to Wishlist'}
                                    </button>
                                    <button class="buy-now" style="padding: 12px 20px; font-size: 16px; margin-top: 10px; width: 100%;" ${!product.inStock ? 'disabled' : ''}>
                                        <i class="fas fa-bolt"></i> Buy Now
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            `;
            
            // Add event listeners to buttons
            const addToCartBtn = productDetailPage.querySelector('.add-to-cart');
            const wishlistBtn = productDetailPage.querySelector('.wishlist');
            const buyNowBtn = productDetailPage.querySelector('.buy-now');
            
            addToCartBtn.addEventListener('click', function() {
                if (product.inStock) {
                    addToCart(product);
                    showToast('Product added to cart!');
                }
            });
            
            wishlistBtn.addEventListener('click', function() {
                toggleWishlist(product, wishlistBtn);
                // Update button text
                const isInWishlist = wishlist.some(item => item.id === product.id);
                wishlistBtn.innerHTML = `<i class="${isInWishlist ? 'fas' : 'far'} fa-heart"></i> ${isInWishlist ? 'Remove from Wishlist' : 'Add to Wishlist'}`;
                wishlistBtn.classList.toggle('active', isInWishlist);
            });
            
            buyNowBtn.addEventListener('click', function() {
                if (product.inStock) {
                    addToCart(product);
                    navigateToPage('cart-page');
                }
            });
            
            navigateToPage('product-detail-page');
        }

        // Banner slider functionality
        let currentSlide = 0;
        let slideInterval;
        
        function startBannerSlider() {
            slideInterval = setInterval(() => {
                // Hide current slide
                bannerSlides[currentSlide].classList.remove('active');
                dots[currentSlide].classList.remove('active');
                
                // Move to next slide
                currentSlide = (currentSlide + 1) % bannerSlides.length;
                
                // Show next slide
                bannerSlides[currentSlide].classList.add('active');
                dots[currentSlide].classList.add('active');
            }, 5000);
        }

        // Dot click functionality
        dots.forEach(dot => {
            dot.addEventListener('click', function() {
                clearInterval(slideInterval);
                
                const slideIndex = parseInt(this.getAttribute('data-slide'));
                
                // Hide current slide
                bannerSlides[currentSlide].classList.remove('active');
                dots[currentSlide].classList.remove('active');
                
                // Show selected slide
                currentSlide = slideIndex;
                bannerSlides[currentSlide].classList.add('active');
                dots[currentSlide].classList.add('active');
                
                // Restart the slider
                startBannerSlider();
            });
        });

        // Search functionality
        searchInput.addEventListener('input', function() {
            const query = this.value.toLowerCase();
            
            if (query.length > 0) {
                const filteredSuggestions = searchSuggestions.filter(suggestion => 
                    suggestion.toLowerCase().includes(query)
                );
                
                displaySearchSuggestions(filteredSuggestions);
            } else {
                searchSuggestionsEl.classList.remove('active');
            }
        });

        // Display search suggestions
        function displaySearchSuggestions(suggestions) {
            searchSuggestionsEl.innerHTML = '';
            
            if (suggestions.length > 0) {
                suggestions.forEach(suggestion => {
                    const suggestionItem = document.createElement('div');
                    suggestionItem.className = 'suggestion-item';
                    
                    // Find matching product for image
                    const matchingProduct = products.find(p => 
                        p.name.toLowerCase().includes(suggestion.toLowerCase())
                    );
                    
                    suggestionItem.innerHTML = `
                        ${matchingProduct ? `<img src="${matchingProduct.image}" alt="${suggestion}" onerror="this.style.display='none'">` : ''}
                        <span>${suggestion}</span>
                    `;
                    
                    suggestionItem.addEventListener('click', function() {
                        searchInput.value = suggestion;
                        searchSuggestionsEl.classList.remove('active');
                        // In a real app, you would redirect to search results page
                        navigateToPage('products-page');
                        productsPageTitle.textContent = `Search Results for "${suggestion}"`;
                    });
                    
                    searchSuggestionsEl.appendChild(suggestionItem);
                });
                
                searchSuggestionsEl.classList.add('active');
            } else {
                searchSuggestionsEl.classList.remove('active');
            }
        }

        // Hide search suggestions when clicking outside
        document.addEventListener('click', function(e) {
            if (!searchInput.contains(e.target) && !searchSuggestionsEl.contains(e.target)) {
                searchSuggestionsEl.classList.remove('active');
            }
        });

        // Cart functionality
        function addToCart(product) {
            const existingItem = cart.find(item => item.id === product.id);
            
            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({
                    ...product,
                    quantity: 1
                });
            }
            
            updateCartCount();
            renderCartItems();
        }
        
        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCartCount();
            renderCartItems();
        }
        
        function updateCartCount() {
            const totalItems = cart.reduce((total, item) => total + item.quantity, 0);
            cartCount.textContent = totalItems;
        }
        
        function renderCartItems() {
            cartItemsContainer.innerHTML = '';
            
            if (cart.length === 0) {
                cartItemsContainer.innerHTML = `
                    <div style="text-align: center; padding: 40px;">
                        <i class="fas fa-shopping-cart" style="font-size: 60px; color: var(--gray); margin-bottom: 20px;"></i>
                        <h3 style="margin-bottom: 10px;">Your cart is empty</h3>
                        <p style="color: var(--gray);">Add some products to your cart</p>
                    </div>
                `;
                return;
            }
            
            cart.forEach(item => {
                const cartItem = document.createElement('div');
                cartItem.className = 'cart-item';
                cartItem.innerHTML = `
                    <div class="cart-item-image">
                        <img src="${item.image}" alt="${item.name}" onerror="this.src='https://via.placeholder.com/100x100/cccccc/969696?text=Product+Image'">
                    </div>
                    <div class="cart-item-details">
                        <div class="cart-item-title">${item.name}</div>
                        <div class="cart-item-price">₹${item.price.toLocaleString()}</div>
                        <div class="cart-item-actions">
                            <div class="quantity-control">
                                <button class="quantity-btn decrease" data-id="${item.id}">-</button>
                                <input type="text" class="quantity-input" value="${item.quantity}" readonly>
                                <button class="quantity-btn increase" data-id="${item.id}">+</button>
                            </div>
                            <div class="remove-item" data-id="${item.id}">Remove</div>
                        </div>
                    </div>
                `;
                
                cartItemsContainer.appendChild(cartItem);
            });
            
            updateCartSummary();
        }
        
        function updateCartSummary() {
            const totalItems = cart.reduce((total, item) => total + item.quantity, 0);
            const subtotal = cart.reduce((total, item) => total + (item.price * item.quantity), 0);
            
            document.getElementById('cart-total-items').textContent = totalItems;
            document.getElementById('cart-subtotal').textContent = `₹${subtotal.toLocaleString()}`;
            document.getElementById('cart-total').textContent = `₹${subtotal.toLocaleString()}`;
        }
        
        function updateCheckoutSummary() {
            checkoutOrderSummary.innerHTML = '';
            
            cart.forEach(item => {
                const summaryItem = document.createElement('div');
                summaryItem.className = 'order-summary-item';
                summaryItem.innerHTML = `
                    <span>${item.name} (x${item.quantity})</span>
                    <span>₹${(item.price * item.quantity).toLocaleString()}</span>
                `;
                checkoutOrderSummary.appendChild(summaryItem);
            });
            
            const subtotal = cart.reduce((total, item) => total + (item.price * item.quantity), 0);
            
            const shippingItem = document.createElement('div');
            shippingItem.className = 'order-summary-item';
            shippingItem.innerHTML = `
                <span>Shipping</span>
                <span>FREE</span>
            `;
            checkoutOrderSummary.appendChild(shippingItem);
            
            document.getElementById('checkout-total').textContent = `₹${subtotal.toLocaleString()}`;
        }

        // Wishlist functionality
        function toggleWishlist(product, buttonElement) {
            const existingIndex = wishlist.findIndex(item => item.id === product.id);
            
            if (existingIndex !== -1) {
                // Remove from wishlist
                wishlist.splice(existingIndex, 1);
                if (buttonElement) {
                    buttonElement.classList.remove('active');
                    buttonElement.querySelector('i').classList.remove('fas');
                    buttonElement.querySelector('i').classList.add('far');
                }
                showToast('Product removed from wishlist!');
            } else {
                // Add to wishlist
                wishlist.push(product);
                if (buttonElement) {
                    buttonElement.classList.add('active');
                    buttonElement.querySelector('i').classList.remove('far');
                    buttonElement.querySelector('i').classList.add('fas');
                }
                showToast('Product added to wishlist!');
            }
            
            updateWishlistCount();
            renderWishlistItems();
        }
        
        function updateWishlistCount() {
            wishlistCount.textContent = wishlist.length;
        }
        
        function renderWishlistItems() {
            wishlistProductsContainer.innerHTML = '';
            
            if (wishlist.length === 0) {
                wishlistProductsContainer.innerHTML = `
                    <div style="text-align: center; padding: 40px;">
                        <i class="far fa-heart" style="font-size: 60px; color: var(--gray); margin-bottom: 20px;"></i>
                        <h3 style="margin-bottom: 10px;">Your wishlist is empty</h3>
                        <p style="color: var(--gray);">Add some products to your wishlist</p>
                    </div>
                `;
                return;
            }
            
            wishlist.forEach(product => {
                const productCard = createProductCard(product);
                wishlistProductsContainer.appendChild(productCard);
            });
        }

        // Navigation functionality
        function navigateToPage(pageId) {
            // Store current page as previous page
            previousPage = currentPage;
            
            // Hide all pages
            pages.forEach(page => {
                page.classList.remove('active');
            });
            
            // Show the selected page
            document.getElementById(pageId).classList.add('active');
            currentPage = pageId;
        }

        function goBack() {
            navigateToPage(previousPage);
        }

        // Toast notification
        function showToast(message) {
            toastMessage.textContent = message;
            toast.classList.add('active');
            
            setTimeout(() => {
                toast.classList.remove('active');
            }, 3000);
        }

        // Setup event listeners
        function setupEventListeners() {
            // Login modal
            loginBtn.addEventListener('click', function() {
                loginModal.classList.add('active');
            });
            
            closeLoginModal.addEventListener('click', function() {
                loginModal.classList.remove('active');
            });
            
            // Signup modal
            showSignup.addEventListener('click', function(e) {
                e.preventDefault();
                loginModal.classList.remove('active');
                signupModal.classList.add('active');
            });
            
            closeSignupModal.addEventListener('click', function() {
                signupModal.classList.remove('active');
            });
            
            showLogin.addEventListener('click', function(e) {
                e.preventDefault();
                signupModal.classList.remove('active');
                loginModal.classList.add('active');
            });
            
            // Close modals when clicking outside
            window.addEventListener('click', function(e) {
                if (e.target === loginModal) {
                    loginModal.classList.remove('active');
                }
                if (e.target === signupModal) {
                    signupModal.classList.remove('active');
                }
            });
            
            // Form submissions
            loginForm.addEventListener('submit', function(e) {
                e.preventDefault();
                const email = document.getElementById('login-email').value;
                const password = document.getElementById('login-password').value;
                
                // In a real app, you would send this to a server
                console.log('Login attempt:', { email, password });
                showToast('Login successful!');
                loginModal.classList.remove('active');
            });
            
            signupForm.addEventListener('submit', function(e) {
                e.preventDefault();
                const name = document.getElementById('signup-name').value;
                const email = document.getElementById('signup-email').value;
                const password = document.getElementById('signup-password').value;
                const confirmPassword = document.getElementById('signup-confirm-password').value;
                
                if (password !== confirmPassword) {
                    alert('Passwords do not match!');
                    return;
                }
                
                // In a real app, you would send this to a server
                console.log('Signup attempt:', { name, email, password });
                showToast('Account created successfully!');
                signupModal.classList.remove('active');
            });
            
            // Navigation
            homeLink.addEventListener('click', function(e) {
                e.preventDefault();
                navigateToPage('home-page');
            });
            
            cartBtn.addEventListener('click', function(e) {
                e.preventDefault();
                navigateToPage('cart-page');
            });
            
            wishlistBtn.addEventListener('click', function(e) {
                e.preventDefault();
                navigateToPage('wishlist-page');
            });
            
            // Back and Home buttons
            productsBackBtn.addEventListener('click', goBack);
            productsHomeBtn.addEventListener('click', function() {
                navigateToPage('home-page');
            });
            
            detailBackBtn.addEventListener('click', goBack);
            detailHomeBtn.addEventListener('click', function() {
                navigateToPage('home-page');
            });
            
            cartBackBtn.addEventListener('click', goBack);
            cartHomeBtn.addEventListener('click', function() {
                navigateToPage('home-page');
            });
            
            wishlistBackBtn.addEventListener('click', goBack);
            wishlistHomeBtn.addEventListener('click', function() {
                navigateToPage('home-page');
            });
            
            checkoutBackBtn.addEventListener('click', goBack);
            checkoutHomeBtn.addEventListener('click', function() {
                navigateToPage('home-page');
            });
            
            confirmationHomeBtn.addEventListener('click', function() {
                navigateToPage('home-page');
            });
            
            // Cart functionality
            proceedToCheckout.addEventListener('click', function() {
                if (cart.length === 0) {
                    showToast('Your cart is empty!');
                    return;
                }
                updateCheckoutSummary();
                navigateToPage('checkout-page');
            });
            
            // Checkout functionality
            placeOrderBtn.addEventListener('click', function() {
                const fullName = document.getElementById('full-name').value;
                const phone = document.getElementById('phone').value;
                const address = document.getElementById('address').value;
                const city = document.getElementById('city').value;
                const state = document.getElementById('state').value;
                const pincode = document.getElementById('pincode').value;
                
                if (!fullName || !phone || !address || !city || !state || !pincode) {
                    showToast('Please fill all the address fields!');
                    return;
                }
                
                if (!selectedPaymentMethod) {
                    showToast('Please select a payment method!');
                    return;
                }
                
                // In a real app, you would process the order here
                console.log('Order placed:', {
                    address: { fullName, phone, address, city, state, pincode },
                    paymentMethod: selectedPaymentMethod,
                    cart
                });
                
                navigateToPage('order-confirmation-page');
                
                // Clear cart after order
                cart = [];
                updateCartCount();
            });
            
            continueShoppingBtn.addEventListener('click', function() {
                navigateToPage('home-page');
            });
            
            // View all links
            viewAllOffers.addEventListener('click', function(e) {
                e.preventDefault();
                navigateToPage('products-page');
                productsPageTitle.textContent = 'Top Offers';
            });
            
            viewAllMobiles.addEventListener('click', function(e) {
                e.preventDefault();
                navigateToPage('products-page');
                productsPageTitle.textContent = 'Mobile Phones';
                currentCategory = 'Mobiles';
                filterProductsByCategory();
            });
            
            // Category navigation
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    const category = this.getAttribute('data-category');
                    
                    if (category === 'all') {
                        navigateToPage('home-page');
                    } else {
                        navigateToPage('products-page');
                        productsPageTitle.textContent = this.textContent;
                        currentCategory = category;
                        filterProductsByCategory();
                    }
                });
            });
            
            categories.forEach(category => {
                category.addEventListener('click', function() {
                    const categoryName = this.getAttribute('data-category');
                    navigateToPage('products-page');
                    productsPageTitle.textContent = this.querySelector('.category-name').textContent;
                    currentCategory = categoryName;
                    filterProductsByCategory();
                });
            });
            
            // Payment method selection
            document.querySelectorAll('.payment-method').forEach(method => {
                method.addEventListener('click', function() {
                    document.querySelectorAll('.payment-method').forEach(m => {
                        m.classList.remove('selected');
                    });
                    this.classList.add('selected');
                    selectedPaymentMethod = this.getAttribute('data-method');
                });
            });
            
            // Cart item quantity controls
            document.addEventListener('click', function(e) {
                if (e.target.classList.contains('decrease')) {
                    const productId = parseInt(e.target.getAttribute('data-id'));
                    const item = cart.find(item => item.id === productId);
                    
                    if (item && item.quantity > 1) {
                        item.quantity -= 1;
                        renderCartItems();
                        updateCartCount();
                    }
                }
                
                if (e.target.classList.contains('increase')) {
                    const productId = parseInt(e.target.getAttribute('data-id'));
                    const item = cart.find(item => item.id === productId);
                    
                    if (item) {
                        item.quantity += 1;
                        renderCartItems();
                        updateCartCount();
                    }
                }
                
                if (e.target.classList.contains('remove-item')) {
                    const productId = parseInt(e.target.getAttribute('data-id'));
                    removeFromCart(productId);
                    showToast('Product removed from cart!');
                }
            });
        }
        
        // Filter products by category
        function filterProductsByCategory() {
            const filteredProducts = currentCategory === 'all' 
                ? products 
                : products.filter(product => product.category === currentCategory);
            
            allProductsContainer.innerHTML = '';
            
            filteredProducts.forEach(product => {
                const productCard = createProductCard(product);
                allProductsContainer.appendChild(productCard);
            });
        }
    </script>
</body>
</html>
