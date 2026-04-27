# <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ChemLab Supplies - Mobile Chemical Shop</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* Mobile-First Header */
        .header {
            background: rgba(255, 255, 255, 0.98);
            backdrop-filter: blur(20px);
            box-shadow: 0 4px 30px rgba(0,0,0,0.2);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            padding: 1rem 1rem;
        }

        .nav-container {
            max-width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.4rem;
            font-weight: 700;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .mobile-menu {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .btn {
            padding: 0.8rem 1.2rem;
            border: none;
            border-radius: 25px;
            font-weight: 500;
            text-decoration: none;
            transition: all 0.3s ease;
            cursor: pointer;
            font-size: 0.85rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            touch-action: manipulation;
        }

        .btn-primary {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            min-width: 120px;
            justify-content: center;
        }

        .btn-primary:hover, .btn-primary:active {
            transform: scale(0.98);
            box-shadow: 0 8px 20px rgba(102, 126, 234, 0.4);
        }

        .btn-outline {
            background: transparent;
            color: #667eea;
            border: 2px solid #667eea;
            min-width: 120px;
            justify-content: center;
        }

        .btn-outline:hover, .btn-outline:active {
            background: #667eea;
            color: white;
            transform: scale(0.98);
        }

        .cart-icon {
            position: relative;
            padding: 0.8rem;
            min-width: auto;
        }

        .cart-count {
            position: absolute;
            top: -5px;
            right: -5px;
            background: #ff4757;
            color: white;
            border-radius: 50%;
            width: 22px;
            height: 22px;
            font-size: 0.75rem;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
        }

        /* Main Content */
        .main-container {
            padding: 90px 1rem 2rem;
            max-width: 100%;
        }

        .hero {
            text-align: center;
            color: white;
            margin-bottom: 3rem;
            padding: 2rem 0;
        }

        .hero h1 {
            font-size: 2.2rem;
            font-weight: 700;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .hero p {
            font-size: 1.1rem;
            margin-bottom: 2rem;
            opacity: 0.95;
        }

        /* Safety Warning */
        .safety-warning {
            background: linear-gradient(45deg, #ff6b6b, #ff8e8e);
            color: white;
            padding: 1.5rem;
            border-radius: 15px;
            margin-bottom: 2rem;
            text-align: center;
            box-shadow: 0 8px 25px rgba(255, 107, 107, 0.3);
        }

        /* Products Section */
        .products-section {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 2rem 1.5rem;
            box-shadow: 0 15px 35px rgba(0,0,0,0.15);
            margin-bottom: 2rem;
        }

        .section-title {
            font-size: 1.8rem;
            text-align: center;
            margin-bottom: 2rem;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .products-grid {
            display: flex;
            flex-direction: column;
            gap: 1.2rem;
        }

        .product-card {
            background: white;
            border-radius: 15px;
            padding: 1.5rem;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            border: 1px solid rgba(102, 126, 234, 0.15);
            position: relative;
            overflow: hidden;
        }

        .product-card:hover, .product-card:active {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
        }

        .product-category {
            font-size: 0.75rem;
            color: #667eea;
            font-weight: 600;
            padding: 0.4rem 0.8rem;
            background: rgba(102, 126, 234, 0.1);
            border-radius: 15px;
            display: inline-block;
            margin-bottom: 0.8rem;
        }

        .product-image {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 1rem;
        }

        .product-name {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: #2c3e50;
            line-height: 1.3;
        }

        .product-price {
            font-size: 1.4rem;
            font-weight: 700;
            color: #27ae60;
            margin-bottom: 1rem;
        }

        .product-description {
            color: #666;
            font-size: 0.9rem;
            margin-bottom: 1rem;
            line-height: 1.5;
        }

        .restricted-badge {
            background: #ff6b6b;
            color: white;
            padding: 0.4rem 0.8rem;
            border-radius: 10px;
            font-size: 0.75rem;
            margin-bottom: 1rem;
            text-align: center;
        }

        /* Owner Controls */
        .owner-controls {
            display: none;
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 1500;
        }

        .owner-controls.show {
            display: block;
        }

        .control-btn {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            box-shadow: 0 8px 25px rgba(0,0,0,0.3);
        }

        /* Modals - Mobile Optimized */
        .modal {
            display: none;
            position: fixed;
            z-index: 2000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.7);
            backdrop-filter: blur(10px);
            padding: 1rem;
            overflow-y: auto;
        }

        .modal-content {
            background: white;
            margin: 2rem auto;
            padding: 2rem;
            border-radius: 20px;
            width: 100%;
            max-width: 95vw;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 25px 50px rgba(0,0,0,0.4);
            animation: modalSlideIn 0.4s ease;
        }

        @keyframes modalSlideIn {
            from { transform: translateY(-30px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .close {
            color: #aaa;
            float: right;
            font-size: 2rem;
            font-weight: bold;
            cursor: pointer;
            touch-action: manipulation;
        }

        .close:hover, .close:active {
            color: #333;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
            color: #333;
            font-size: 0.95rem;
        }

        .form-group input,
        .form-group select {
            width: 100%;
            padding: 1rem;
            border: 2px solid #e1e5e9;
            border-radius: 12px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus,
        .form-group select:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .age-verification {
            display: flex;
            align-items: flex-start;
            gap: 0.8rem;
            margin: 1rem 0;
            padding: 1rem;
            background: rgba(102, 126, 234, 0.1);
            border-radius: 12px;
        }

        .age-verification input[type="checkbox"] {
            width: auto;
            margin: 0;
            transform: scale(1.2);
        }

        /* Cart Items */
        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem;
            border-bottom: 1px solid #eee;
            gap: 1rem;
        }

        .cart-item:last-child {
            border-bottom: none;
        }

        .quantity-controls {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .qty-btn {
            width: 35px;
            height: 35px;
            border: 2px solid #ddd;
            background: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.1rem;
            cursor: pointer;
        }

        /* Owner Product Edit Form */
        .product-edit-form {
            display: grid;
            gap: 1rem;
        }

        .price-controls {
            display: flex;
            gap: 0.5rem;
            align-items: center;
        }

        .price-btn {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            font-size: 1rem;
            font-weight: 600;
        }

        .price-up {
            background: #27ae60;
            color: white;
            border: 2px solid #27ae60;
        }

        .price-down {
            background: #e74c3c;
            color: white;
            border: 2px solid #e74c3c;
        }

        /* Responsive for larger screens */
        @media (min-width: 768px) {
            .products-grid {
                display: grid;
                grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
                gap: 1.5rem;
            }
            
            .hero h1 {
                font-size: 3rem;
            }
            
            .main-container {
                padding: 100px 2rem 2rem;
            }
        }

        /* Scroll to top */
        .scroll-top {
            position: fixed;
            bottom: 90px;
            right: 20px;
            background: #667eea;
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            font-size: 1.2rem;
            cursor: pointer;
            display: none;
            z-index: 1000;
            transition: all 0.3s ease;
        }

        .scroll-top.show {
            display: flex;
            align-items: center;
            justify-content: center;
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header class="header">
        <div class="nav-container">
            <div class="logo">
                <i class="fas fa-flask"></i> ChemLab
            </div>
            <div class="mobile-menu">
                <a href="#" class="btn btn-outline" onclick="openModal('customerLoginModal')">
                    <i class="fas fa-user"></i>
                </a>
                <a href="#" class="btn btn-primary" onclick="openModal('ownerLoginModal')">
                    <i class="fas fa-crown"></i>
                </a>
                <a href="#" class="btn btn-outline cart-icon" onclick="openModal('cartModal')">
                    <i class="fas fa-shopping-cart"></i>
                    <span class="cart-count" id="cartCount">0</span>
                </a>
            </div>
        </div>
    </header>

    <!-- Scroll to Top -->
    <button class="scroll-top" id="scrollTop" onclick="scrollToTop()">
        <i class="fas fa-chevron-up"></i>
    </button>

    <!-- Main Content -->
    <div class="main-container">
        <div class="hero">
            <h1>ChemLab Supplies</h1>
            <p>Premium chemicals & lab equipment<br>for educational institutions</p>
        </div>

        <div class="safety-warning">
            <i class="fas fa-exclamation-triangle" style="font-size: 1.8rem; margin-bottom: 0.8rem;"></i>
            <h3>⚠️ SAFETY FIRST</h3>
            <p>Age 18+ verification required for hazardous chemicals</p>
        </div>

        <div class="products-section">
            <h2 class="section-title">Our Products</h2>
            <div class="products-grid" id="productsGrid"></div>
        </div>
    </div>

    <!-- Customer Login Modal -->
    <div id="customerLoginModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeAllModals()">&times;</span>
            <h2><i class="fas fa-user"></i> Customer Login</h2>
            <form id="customerLoginForm">
                <div class="form-group">
                    <label>Email</label>
                    <input type="email" id="customerEmail" required>
                </div>
                <div class="form-group">
                    <label>Password</label>
                    <input type="password" id="customerPassword" required>
                </div>
                <div class="age-verification">
                    <input type="checkbox" id="ageVerification" required>
                    <label style="font-size: 0.9rem;">I am 18+ and authorized to purchase chemicals</label>
                </div>
                <button type="submit" class="btn btn-primary" style="width: 100%;">Login</button>
            </form>
        </div>
    </div>

    <!-- Owner Login Modal -->
    <div id="ownerLoginModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeAllModals()">&times;</span>
            <h2><i class="fas fa-crown"></i> Owner Login</h2>
            <form id="ownerLoginForm">
                <div class="form-group">
                    <label>Admin Email</label>
                    <input type="email" id="ownerEmail" placeholder="admin@chemlab.com" required>
                </div>
                <div class="form-group">
                    <label>Password</label>
                    <input type="password" id="ownerPassword" placeholder="admin123" required>
                </div>
                <button type="submit" class="btn btn-primary" style="width: 100%;">Access Dashboard</button>
            </div>
        </div>
    </div>

    <!-- Cart Modal -->
    <div id="cartModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeAllModals()">&times;</span>
            <h2><i class="fas fa-shopping-cart"></i> Shopping Cart</h2>
            <div id="cartItems"></div>
            <div style="margin-top: 2rem; padding-top: 2rem; border-top: 2px solid #eee;">
                <h3 style="text-align: center;">Total: $<span id="cartTotal">0.00</span></h3>
                <button class="btn btn-primary" style="width: 100%; margin-top: 1rem;" onclick="checkout()">Checkout</button>
            </div>
        </div>
    </div>

    <!-- Owner Controls -->
    <div class="owner-controls" id="ownerControls">
        <button class="btn control-btn btn-primary" onclick="openModal('addProductModal')" title="Add Product">
            <i class="fas fa-plus"></i>
        </button>
        <button class="btn control-btn btn-primary" onclick="toggleEditMode()" title="Edit Mode">
            <i class="fas fa-edit"></i>
        </button>
    </div>

    <!-- Add Product Modal -->
    <div id="addProductModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeAllModals()">&times;</span>
            <h2><i class="fas fa-plus"></i> Add New Product</h2>
            <form id="addProductForm" class="product-edit-form">
                <div class="form-group">
                    <label>Product Name</label>
                    <input type="text" id="newProductName" required>
                </div>
                <div class="form-group">
                    <label>Category</label>
                    <select id="newProductCategory" required>
                        <option value="">Select Category</option>
                        <option>Basic Glassware</option>
                        <option>Heating Equipment</option>
                        <option>Measuring Instruments</option>
                        <option>Safety Equipment</option>
                        <option>Acids</option>
                        <option>Bases</option>
                        <option>Salts</option>
                        <option>Indicators</option>
                        <option>Organic Chemicals</option>
                        <option>Special Chemicals</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Price ($)</label>
                    <div class="price-controls">
                        <button type="button" class="price-btn price-down" onclick="adjustPrice(-1)">-</button>
                        <input type="number" id="newProductPrice" step="0.01" min="0" style="flex: 1; text-align: center;" required>
                        <button type="button" class="price-btn price-up" onclick="adjustPrice(1)">+</button>
                    </div>
                </div>
                <div class="form-group">
                    <label>Description</label>
                    <textarea id="newProductDesc" rows="3" style="resize: vertical;"></textarea>
                </div>
                <div class="form-group">
                    <label>Emoji/Icon</label>
                    <input type="text" id="newProductImage" maxlength="2" placeholder="🧪">
                </div>
                <div class="form-group">
                    <label>
                        <input type="checkbox" id="isRestricted"> Age Restricted
                    </label>
                </div>
                <button type="submit" class="btn btn-primary" style="width: 100%;">Add Product</button>
            </form>
        </div>
    </div>

    <script>
        // Complete Product Database
        let products = [
            // Basic Glassware
            { id: 1, name: 'Beaker 500ml', category: 'Basic Glassware', price: 12.99, description: 'Borosilicate glass', image: '🧪', restricted: false },
            { id: 2, name: 'Conical Flask 250ml', category: 'Basic Glassware', price: 9.99, description: 'Erlenmeyer flask', image: '🔬', restricted: false },
            { id: 3, name: 'Volumetric Flask 100ml', category: 'Basic Glassware', price: 15.99, description: 'Class A precision', image: '📏', restricted: false },
            { id: 4, name: 'Test Tube Pack (12)', category: 'Basic Glassware', price: 8.99, description: 'Borosilicate 15ml', image: '🧪', restricted: false },
            { id: 5, name: 'Burette 50ml', category: 'Basic Glassware', price: 28.99, description: 'Precision ground', image: '💉', restricted: false },

            // Heating Equipment
            { id: 6, name: 'Bunsen Burner', category: 'Heating Equipment', price: 25.99, description: 'Gas/propane compatible', image: '🔥', restricted: false },
            { id: 7, name: 'Tripod Stand', category: 'Heating Equipment', price: 18.99, description: 'Stainless steel', image: '🪑', restricted: false },
            { id: 8, name: 'Wire Gauze', category: 'Heating Equipment', price: 6.99, description: 'Asbestos free', image: '🔳', restricted: false },

            // Chemicals - Acids
            { id: 9, name: 'HCl 1M 500ml', category: 'Acids', price: 15.99, description: 'Hydrochloric Acid', image: '💧', restricted: true },
            { id: 10, name: 'H₂SO₄ 1M 500ml', category: 'Acids', price: 18.99, description: 'Sulfuric Acid', image: '🧪', restricted: true },
            { id: 11, name: 'HNO₃ 1M 500ml', category: 'Acids', price: 22.99, description: 'Nitric Acid', image: '⚗️', restricted: true },

            // Bases
            { id: 12, name: 'NaOH 1M 500ml', category: 'Bases', price: 14.99, description: 'Sodium Hydroxide', image: '🧪', restricted: true },
            { id: 13, name: 'NH₄OH 500ml', category: 'Bases', price: 16.99, description: 'Ammonium Hydroxide', image: '💨', restricted: true },

            // Salts & Indicators
            { id: 14, name: 'CuSO₄ 500g', category: 'Salts', price: 19.99, description: 'Copper Sulfate', image: '🔷', restricted: true },
            { id: 15, name: 'KMnO₄ 100g', category: 'Salts', price: 29.99, description: 'Potassium Permanganate', image: '🟣', restricted: true },
            { id: 16, name: 'Phenolphthalein 25ml', category: 'Indicators', price: 8.99, description: 'pH indicator', image: '🎨', restricted: false },
            { id: 17, name: 'Litmus Paper', category: 'Indicators', price: 7.99, description: 'Red & Blue pack', image: '📄', restricted: false }
        ];

        let cart = [];
        let isLoggedIn = false;
        let isOwnerLoggedIn = false;
        let editMode = false;
        let currentUser = null;
        let editingProductId = null;

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            renderProducts();
            setupEventListeners();
            updateScrollButton();
        });

        function renderProducts() {
            const grid = document.getElementById('productsGrid');
            grid.innerHTML = products.map(product => {
                const isRestricted = product.restricted && !isLoggedIn;
                return `
                    <div class="product-card" data-id="${product.id}">
                        <div class="product-category">${product.category}</div>
                        <div class="product-image">${product.image}</div>
                        <h3 class="product-name">${product.name}</h3>
                        <p class="product-description">${product.description}</p>
                        <div class="product-price">$${product.price.toFixed(2)}</div>
                        ${product.restricted ? '<div class="restricted-badge">🔒 Age Restricted</div>' : ''}
                        
                        ${editMode && isOwnerLoggedIn ? `
                            <div style="display: flex; gap: 0.5rem; margin-top: 1rem;">
                                <button class="btn" style="flex: 1; background: #f39c12; border-color: #f39c12; font-size: 0.8rem;" 
                                        onclick="editProduct(${product.id})">
                                    <i class="fas fa-edit"></i> Edit
                                </button>
                                <button class="btn" style="flex: 1; background: #e74c3c; border-color: #e74c3c; font-size: 0.8rem;" 
                                        onclick="deleteProduct(${product.id})">
                                    <i class="fas fa-trash"></i>
                                </button>
                            </div>
                        ` : ''}
                        
                        <button class="btn btn-primary" style="width: 100%; margin-top: 0.5rem;" 
                                onclick="addToCart(${product.id})"
                                ${isRestricted ? 'disabled' : ''}>
                            ${isRestricted ? 'Login Required' : 'Add to Cart'}
                        </button>
                    </div>
                `;
            }).join('');
        }

        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const existingItem = cart.find(item => item.id === productId);
            
            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({ ...product, quantity: 1 });
            }
            
            updateCartUI();
            showToast(`${product.name} added to cart!`);
        }

        function updateCartUI() {
            const count = cart.reduce((sum, item) => sum + item.quantity, 0);
            document.getElementById('cartCount').textContent = count;
        }

        function renderCart() {
            const cartItems = document.getElementById('cartItems');
            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            
            document.getElementById('cartTotal').textContent = total.toFixed(2);
            
            if (cart.length === 0) {
                cartItems.innerHTML = '<p style="text-align: center; color: #666; padding: 2rem;">Your cart is empty</p>';
                return;
            }
            
            cartItems.innerHTML = cart.map(item => `
                <div class="cart-item">
                    <div>
                        <div style="font-weight: 600;">${item.name}</div>
                        <div>$${item.price.toFixed(2)}</div>
                    </div>
                    <div class="quantity-controls">
                        <button class="qty-btn" onclick="updateQuantity(${item.id}, -1)">−</button>
                        <span style="min-width: 25px; text-align: center; font-weight: 600;">${item.quantity}</span>
                        <button class="qty-btn" onclick="updateQuantity(${item.id}, 1)">+</button>
                        <button class="qty-btn" style="background: #e74c3c; color: white; border-color: #e74c3c;" 
                                onclick="removeFromCart(${item.id})">×</button>
                    </div>
                </div>
            `).join('');
        }

        function updateQuantity(productId, change) {
            const item = cart.find(item => item.id === productId);
            if (item) {
                item.quantity += change;
                if (item.quantity <= 0) {
                    removeFromCart(productId);
                } else {
                    renderCart();
                    updateCartUI();
                }
            }
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            renderCart();
            updateCartUI();
        }

        function checkout() {
            if (cart.length === 0) return showToast('Cart is empty!');
            if (!isLoggedIn) return showToast('Please login first!');
            
            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            showToast(`Order placed! Total: $${total.toFixed(2)}`);
            cart = [];
            closeAllModals();
            updateCartUI();
        }

        // Owner Functions
        function toggleEditMode() {
            editMode = !editMode;
            renderProducts();
            showToast(editMode ? 'Edit mode ON' : 'Edit mode OFF');
        }

        function editProduct(productId) {
            const product = products.find(p => p.id === productId);
            if (!product) return;
            
            editingProductId = productId;
            document.getElementById('newProductName').value = product.name;
            document.getElementById('newProductCategory').value = product.category;
            document.getElementById('newProductPrice').value = product.price;
            document.getElementById('newProductDesc').value = product.description;
            document.getElementById('newProductImage').value = product.image;
            document.getElementById('isRestricted').checked = product.restricted;
            document.querySelector('#addProductModal h2').innerHTML = '<i class="fas fa-edit"></i> Edit Product';
            openModal('addProductModal');
        }

        function deleteProduct(productId) {
            if (confirm('Delete this product?')) {
                products = products.filter(p => p.id !== productId);
                renderProducts();
                showToast('Product deleted!');
            }
        }

        function adjustPrice(change) {
            const priceInput = document.getElementById('newProductPrice');
            const currentPrice = parseFloat(priceInput.value) || 0;
            priceInput.value = Math.max(0, currentPrice + change).toFixed(2);
        }

        // Modal Functions
        function openModal(modalId) {
            closeAllModals();
            document.getElementById(modalId).style.display = 'block';
            document.body.style.overflow = 'hidden';
        }

        function closeAllModals() {
            document.querySelectorAll('.modal').forEach(modal => {
                modal.style.display = 'none';
            });
            document.body.style.overflow = 'auto';
            // Reset add product form
            if (editingProductId) {
                document.getElementById('addProductForm').reset();
                document.querySelector('#addProductModal h2').innerHTML = '<i class="fas fa-plus"></i> Add New Product';
                editingProductId = null;
            }
        }

        function showToast(message) {
            const toast = document.createElement('div');
            toast.style.cssText = `
                position: fixed;
                top: 20px;
                right: 20px;
                background: #27ae60;
                color: white;
                padding: 1rem 1.5rem;
                border-radius: 25px;
                z-index: 3000;
                font-weight: 500;
                box-shadow: 0 10px 30px rgba(39, 174, 96, 0.4);
                transform: translateX(400px);
                transition: transform 0.3s ease;
            `;
            toast.textContent = message;
            document.body.appendChild(toast);
            
            setTimeout(() => toast.style.transform = 'translateX(0)', 100);
            setTimeout(() => {
                toast.style.transform = 'translateX(400px)';
                setTimeout(() => document.body.removeChild(toast), 300);
            }, 3000);
        }

        function setupEventListeners() {
            // Customer Login
            document.getElementById('customerLoginForm').addEventListener('submit', (e) => {
                e.preventDefault();
                if (document.getElementById('ageVerification').checked) {
                    isLoggedIn = true;
                    currentUser = { type: 'customer' };
                    closeAllModals();
                    renderProducts();
                    showToast('✅ Login successful! Age verified.');
                } else {
                    showToast('⚠️ Please verify your age');
                }
            });

            // Owner Login
            document.getElementById('ownerLoginForm').addEventListener('submit', (e) => {
                e.preventDefault();
                const email = document.getElementById('ownerEmail').value;
                const password = document.getElementById('ownerPassword').value;
                
                if (email === 'admin@chemlab.com' && password === 'admin123') {
                    isOwnerLoggedIn = true;
                    currentUser = { type: 'owner', email };
                    closeAllModals();
                    document.getElementById('ownerControls').classList.add('show');
                    showToast('👑 Owner access granted!');
                } else {
                    showToast('❌ Invalid credentials');
                }
            });

            // Add/Edit Product
            document.getElementById('addProductForm').addEventListener('submit', (e) => {
                e.preventDefault();
                const productData = {
                    id: editingProductId || Date.now(),
                    name: document.getElementById('newProductName').value,
                    category: document.getElementById('newProductCategory').value,
                    price: parseFloat(document.getElementById('newProductPrice').value),
                    description: document.getElementById('newProductDesc').value || 'New product',
                    image: document.getElementById('newProductImage').value || '🧪',
                    restricted: document.getElementById('isRestricted').checked
                };

                if (editingProductId) {
                    const index = products.findIndex(p => p.id === editingProductId);
                    products[index] = productData;
                    showToast('Product updated!');
                } else {
                    products.push(productData);
                    showToast('Product added!');
                }

                editingProductId = null;
                renderProducts();
                closeAllModals();
            });

            // Cart modal
            document.getElementById('cartModal').addEventListener('click', (e) => {
                if (e.target.id === 'cartModal') renderCart();
            });
        }

        // UI Utilities
        function scrollToTop() {
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function updateScrollButton() {
            const scrollBtn = document.getElementById('scrollTop');
            window.addEventListener('scroll', () => {
                scrollBtn.classList.toggle('show', window.scrollY > 300);
            });
        }

        // Touch/swipe support for modals
        document.addEventListener('touchstart', handleTouch, { passive: false });
        let touchStartY = 0;

        function handleTouch(e) {
            touchStartY = e.touches[0].clientY;
        }

        document.addEventListener('touchmove', (e) => {
            if (!touchStartY) return;
            const touchY = e.touches[0].clientY;
            const deltaY = touchStartY - touchY;
            
            if (deltaY > 100) {
                closeAllModals();
            }
        }, { passive: false });

        // Prevent zoom on input focus (iOS)
        document.addEventListener('touchstart', function() {}, true);
    </script>
</body>
</html>