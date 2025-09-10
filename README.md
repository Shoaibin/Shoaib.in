
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TechBazaar - Flipkart Affiliate Store</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f8f9fa;
            color: #212121;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }
        
        /* Header Styles */
        header {
            background: linear-gradient(to right, #2874f0, #1360ef);
            padding: 15px 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .header-content {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .logo {
            display: flex;
            align-items: center;
        }
        
        .logo-text {
            color: white;
            font-size: 24px;
            font-weight: bold;
        }
        
        .logo-text span {
            color: #ffe500;
        }
        
        .search-bar {
            display: flex;
            align-items: center;
            background: white;
            border-radius: 4px;
            overflow: hidden;
            flex: 0 1 500px;
        }
        
        .search-bar input {
            border: none;
            padding: 12px 20px;
            font-size: 16px;
            width: 100%;
            outline: none;
        }
        
        .search-bar button {
            background: none;
            border: none;
            padding: 10px 20px;
            color: #2874f0;
            cursor: pointer;
            font-size: 18px;
        }
        
        .header-actions {
            display: flex;
            align-items: center;
            gap: 20px;
        }
        
        .header-action {
            color: white;
            text-decoration: none;
            display: flex;
            flex-direction: column;
            align-items: center;
            font-size: 14px;
        }
        
        .header-action i {
            font-size: 20px;
            margin-bottom: 4px;
        }
        
        /* Navigation */
        nav {
            background-color: white;
            padding: 15px 0;
            box-shadow: 0 1px 1px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }
        
        .nav-items {
            display: flex;
            justify-content: center;
            list-style: none;
            gap: 30px;
        }
        
        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            cursor: pointer;
            transition: transform 0.3s;
        }
        
        .nav-item:hover {
            transform: translateY(-3px);
        }
        
        .nav-item i {
            font-size: 22px;
            color: #2874f0;
            margin-bottom: 5px;
        }
        
        .nav-item span {
            font-size: 14px;
            font-weight: 500;
            text-align: center;
        }
        
        /* Hero Banner */
        .hero-banner {
            background: linear-gradient(to right, #6a11cb, #2575fc);
            border-radius: 10px;
            padding: 40px;
            margin: 20px 0;
            color: white;
            text-align: center;
        }
        
        .hero-banner h1 {
            font-size: 36px;
            margin-bottom: 15px;
        }
        
        .hero-banner p {
            font-size: 18px;
            margin-bottom: 25px;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .cta-button {
            display: inline-block;
            background: #ffe500;
            color: #2874f0;
            padding: 12px 30px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            font-size: 18px;
            transition: all 0.3s;
        }
  .cta-button:hover {
            background: #ffd000;
            transform: scale(1.05);
        }
        
        /* Products Section */
        .section-title {
            text-align: center;
            font-size: 28px;
            margin: 40px 0 20px;
            color: #2874f0;
            position: relative;
        }
        
        .section-title:after {
            content: '';
            display: block;
            width: 80px;
            height: 4px;
            background: #ffe500;
            margin: 10px auto;
            border-radius: 2px;
        }
        
        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 25px;
            margin: 30px 0;
        }
        
        .product-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.15);
        }
        
        .product-image {
            height: 200px;
            width: 100%;
            object-fit: contain;
            padding: 20px;
            background: #f5f7fa;
        }
        
        .product-info {
            padding: 20px;
        }
        
        .product-title {
            font-size: 16px;
            font-weight: 600;
            margin-bottom: 10px;
            height: 40px;
            overflow: hidden;
        }
        
        .product-price {
            font-size: 20px;
            font-weight: bold;
            color: #388e3c;
            margin-bottom: 15px;
        }
        
        .product-rating {
            color: #ff9f00;
            margin-bottom: 15px;
        }
        
        .buy-button {
            display: block;
            background: #2874f0;
            color: white;
            text-align: center;
            padding: 12px;
            border-radius: 5px;
            text-decoration: none;
            font-weight: 600;
            transition: background 0.3s;
        }
        
        .buy-button:hover {
            background: #1360ef;
        }
        
        /* Features Section */
        .features {
            display: flex;
            justify-content: space-between;
            margin: 40px 0;
            gap: 20px;
        }
        
        .feature {
            flex: 1;
            background: white;
            padding: 25px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }
        
        .feature i {
            font-size: 40px;
            color: #2874f0;
            margin-bottom: 15px;
        }
        
        .feature h3 {
            font-size: 20px;
            margin-bottom: 10px;
        }
        
        /* Footer */
        footer {
            background: #1a1a2a;
            color: white;
            padding: 50px 0 20px;
            margin-top: 50px;
        }
        
        .footer-content {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 30px;
        }
        
        .footer-column {
            flex: 1;
            min-width: 200px;
        }
        
        .footer-column h3 {
            font-size: 18px;
            margin-bottom: 20px;
            color: #ffe500;
        }
        
        .footer-column ul {
            list-style: none;
        }
        
        .footer-column li {
            margin-bottom: 12px;
        }
        
        .footer-column a {
            text-decoration: none;
            color: #ccc;
            transition: color 0.3s;
        }
        
        .footer-column a:hover {
            color: #ffe500;
        }
        
        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 15px;
        }
        
        .social-links a {
            display: inline-block;
            width: 40px;
            height: 40px;
            background: #333;
            border-radius: 50%;
            text-align: center;
            line-height: 40px;
            color: white;
            transition: background 0.3s;
        }
        
        .social-links a:hover {
            background: #2874f0;
        }
        
        .copyright {
            text-align: center;
            padding-top: 30px;
            margin-top: 30px;
            border-top: 1px solid #333;
            color: #ccc;
            font-size: 14px;
        }
        
        /* Affiliate Disclosure */
        .affiliate-disclosure {
            background: #ffe500;
            padding: 15px;
            border-radius: 5px;
            margin: 20px 0;
            text-align: center;
            font-size: 14px;
            color: #333;
        }
  /* Responsive Design */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }
            
            .search-bar {
                width: 100%;
            }
            
            .nav-items {
                flex-wrap: wrap;
                gap: 15px;
            }
            
            .features {
                flex-direction: column;
            }
            
            .product-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        
        @media (max-width: 480px) {
            .product-grid {
                grid-template-columns: 1fr;
            }
            
            .nav-items {
                gap: 10px;
            }
            
            .nav-item {
                flex: 0 0 calc(50% - 10px);
            }
            
            .hero-banner h1 {
                font-size: 28px;
            }
            
            .hero-banner p {
                font-size: 16px;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <div class="logo-text">Tech<span>Bazaar</span></div>
                </div>
                
                <div class="search-bar">
                    <input type="text" placeholder="Search for products, brands and more">
                    <button><i class="fas fa-search"></i></button>
                </div>
                
                <div class="header-actions">
                    <a href="#" class="header-action">
                        <i class="fas fa-user"></i>
                        <span>Account</span>
                    </a>
                    <a href="#" class="header-action">
                        <i class="fas fa-shopping-cart"></i>
                        <span>Cart</span>
                    </a>
                </div>
            </div>
        </div>
    </header>
    
    <!-- Navigation -->
    <nav>
        <div class="container">
            <ul class="nav-items">
                <li class="nav-item">
                    <i class="fas fa-mobile-alt"></i>
                    <span>Mobiles</span>
                </li>
                <li class="nav-item">
                    <i class="fas fa-laptop"></i>
                    <span>Laptops</span>
                </li>
                <li class="nav-item">
                    <i class="fas fa-tv"></i>
                    <span>TVs</span>
                </li>
                <li class="nav-item">
                    <i class="fas fa-headphones"></i>
                    <span>Audio</span>
                </li>
                <li class="nav-item">
                    <i class="fas fa-camera"></i>
                    <span>Cameras</span>
                </li>
                <li class="nav-item">
                    <i class="fas fa-tshirt"></i>
                    <span>Fashion</span>
                </li>
            </ul>
        </div>
    </nav>
    
    <!-- Main Content -->
    <main class="container">
        <!-- Hero Banner -->
        <div class="hero-banner">
            <h1>Great Savings & Free Delivery</h1>
            <p>Shop from our wide selection of products and get the best deals with fast delivery. All purchases are handled through our trusted partner Flipkart.</p>
            <a href="#products" class="cta-button">Shop Now</a>
        </div>
        
        <!-- Affiliate Disclosure -->
        <div class="affiliate-disclosure">
            <p><strong>Disclosure:</strong> We are a participant in the Flipkart Affiliate Program, which allows us to earn fees by linking to Flipkart.com. Product prices and availability are accurate as of the date/time indicated and are subject to change.</p>
        </div>
        
        <!-- Products Section -->
        <h2 class="section-title" id="products">Featured Products</h2>
        
        <div class="product-grid">
            <!-- Product 1 -->
            <div class="product-card">
                <img src="https://images.unsplash.com/photo-1598327105666-5b89351aff97?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" alt="Smartphone" class="product-image">
                <div class="product-info">
                    <div class="product-title">Premium Smartphone 128GB</div>
                    <div class="product-price">₹24,999</div>
                    <div class="product-rating">
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star-half-alt"></i>
                    </div>
                    <a href="https://www.flipkart.com/" class="buy-button">Buy on Flipkart</a>
                </div>
            </div>
            
            <!-- Product 2 -->
            <div class="product-card">
                <img src="https://images.unsplash.com/photo-1496181133206-80ce9b88a853?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" alt="Laptop" class="product-image">
                <div class="product-info">
                    <div class="product-title">Ultra Slim Laptop 15.6"</div>
                    <div class="product-price">₹65,999</div>
                    <div class="product-rating">
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="far fa-star"></i>
                    </div>
                    <a href="https://www.flipkart.com/" class="buy-button">Buy on Flipkart</a>
                </div>
            </div>
            
            <!-- Product 3 -->
            <div class="product-card">
                <img src="https://images.unsplash.com/photo-1546868871-7041f2a55e12?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" alt="Smart Watch" class="product-image">
                <div class="product-info">
                    <div class="product-title">Smart Watch Fitness Tracker</div>
                    <div class="product-price">₹3,499</div>
                    <div class="product-rating">
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                    </div>
                    <a href="https://www.flipkart.com/" class="buy-button">Buy on Flipkart</a>
                </div>
            </div>
            
            <!-- Product 4 -->
            <div class="product-card">
                <img src="https://images.unsplash.com/photo-1505740420928-5e560c06d30e?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" alt="Headphones" class="product-image">
                <div class="product-info">
                    <div class="product-title">Wireless Noise Cancelling Headphones</div>
                    <div class="product-price">₹8,999</div>
                    <div class="product-rating">
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star-half-alt"></i>
                    </div>
                    <a href="https://www.flipkart.com/" class="buy-button">Buy on Flipkart</a>
                </div>
            </div><!-- Product 5 -->
            <div class="product-card">
                <img src="https://images.unsplash.com/photo-1564466809058-b5a9c85aaf2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" alt="Camera" class="product-image">
                <div class="product-info">
                    <div class="product-title">DSLR Camera 24MP</div>
                    <div class="product-price">₹45,999</div>
                    <div class="product-rating">
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="far fa-star"></i>
                    </div>
                    <a href="https://www.flipkart.com/" class="buy-button">Buy on Flipkart</a>
                </div>
            </div>
            
            <!-- Product 6 -->
            <div class="product-card">
                <img src="https://images.unsplash.com/photo-1572569511254-d8f925fe2cbb?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" alt="Smart TV" class="product-image">
                <div class="product-info">
                    <div class="product-title">55 inch Smart 4K TV</div>
                    <div class="product-price">₹54,999</div>
                    <div class="product-rating">
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star-half-alt"></i>
                    </div>
                    <a href="https://www.flipkart.com/" class="buy-button">Buy on Flipkart</a>
                </div>
            </div>
        </div>
        
        <!-- Features Section -->
        <div class="features">
            <div class="feature">
                <i class="fas fa-truck"></i>
                <h3>Free Delivery</h3>
                <p>Enjoy free delivery on orders above ₹499</p>
            </div>
            <div class="feature">
                <i class="fas fa-shield-alt"></i>
                <h3>Secure Payments</h3>
                <p>100% secure and safe payment methods</p>
            </div>
            <div class="feature">
                <i class="fas fa-undo"></i>
                <h3>Easy Returns</h3>
                <p>10-day easy return policy on most items</p>
            </div>
        </div>
    </main>
    
    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>About Us</h3>
                    <ul>
                        <li><a href="#">Contact Us</a></li>
                        <li><a href="#">About Us</a></li>
                        <li><a href="#">Careers</a></li>
                        <li><a href="#">Blog</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Help</h3>
                    <ul>
                        <li><a href="#">Payments</a></li>
                        <li><a href="#">Shipping</a></li>
                        <li><a href="#">Cancellation & Returns</a></li>
                        <li><a href="#">FAQ</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Policy</h3>
                    <ul>
                        <li><a href="#">Return Policy</a></li>
                        <li><a href="#">Terms Of Use</a></li>
                        <li><a href="#">Security</a></li>
                        <li><a href="#">Privacy</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Follow Us</h3>
                    <div class="social-links">
                        <a href="#"><i class="fab fa-facebook-f"></i></a>
                        <a href="#"><i class="fab fa-twitter"></i></a>
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fab fa-youtube"></i></a>
                    </div>
                </div>
            </div>
 <div class="copyright">
                <p>© 2023 TechBazaar. All rights reserved.</p>
                <p>This site contains affiliate links to Flipkart. We may earn a commission for purchases made through these links.</p>
            </div>
        </div>
    </footer>

    <script>
        // Simple JavaScript for interactive elements
        document.addEventListener('DOMContentLoaded', function() {
            // Add to Cart functionality
            const buyButtons = document.querySelectorAll('.buy-button');
            buyButtons.forEach(button => {
                button.addEventListener('click', function(e) {
                    e.preventDefault();
                    const productName = this.closest('.product-card').querySelector('.product-title').textContent;
                    alert(`Redirecting to Flipkart to purchase: ${productName}`);
                    window.location.href = "https://www.flipkart.com/";
                });
            });
            
            // Search functionality
            const searchInput = document.querySelector('.search-bar input');
            const searchButton = document.querySelector('.search-bar button');
            
            searchButton.addEventListener('click', function() {
                if (searchInput.value.trim() !== '') {
                    alert(`Searching for: ${searchInput.value}`);
                }
            });
            
            searchInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter' && searchInput.value.trim() !== '') {
                    alert(`Searching for: ${searchInput.value}`);
                }
            });
            
            // Navigation smooth scroll
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    document.querySelector(this.getAttribute('href')).scrollIntoView({
                        behavior: 'smooth'
                    });
                });
            });
        });
    </script>
</body>
</html>
