<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lure Kings - Premium Fishing Lures</title>
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
            background-color: #f4f4f4;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        header {
            background: linear-gradient(135deg, #2c5aa0, #1e3d72);
            color: white;
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: #fff;
        }
        
        .tagline {
            font-size: 0.9rem;
            opacity: 0.9;
            margin-top: 5px;
        }
        
        nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }
        
        nav a {
            color: white;
            text-decoration: none;
            transition: color 0.3s;
            font-weight: 500;
        }
        
        nav a:hover {
            color: #ffd700;
        }
        
        .cart-icon {
            position: relative;
            cursor: pointer;
            padding: 10px;
            background: rgba(255,255,255,0.1);
            border-radius: 5px;
            transition: background 0.3s;
        }
        
        .cart-icon:hover {
            background: rgba(255,255,255,0.2);
        }
        
        .cart-count {
            position: absolute;
            top: -5px;
            right: -5px;
            background: #ff4444;
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
            font-weight: bold;
        }
        
        .hero {
            background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 400"><rect fill="%23006994" width="1200" height="400"/><path fill="%23004d6b" d="M0 300h1200v100H0z"/></svg>');
            background-size: cover;
            background-position: center;
            color: white;
            text-align: center;
            padding: 4rem 0;
        }
        
        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }
        
        .hero p {
            font-size: 1.2rem;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
        }
        
        .products {
            padding: 3rem 0;
            background: white;
        }
        
        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }
        
        .product-card {
            background: white;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            overflow: hidden;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.15);
        }
        
        .product-image {
            height: 200px;
            background: linear-gradient(45deg, #f0f0f0, #e0e0e0);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: #666;
        }
        
        .product-info {
            padding: 1.5rem;
        }
        
        .product-name {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
            color: #2c5aa0;
        }
        
        .product-price {
            font-size: 1.4rem;
            font-weight: bold;
            color: #e74c3c;
            margin-bottom: 1rem;
        }
        
        .add-to-cart {
            width: 100%;
            padding: 12px;
            background: linear-gradient(135deg, #2c5aa0, #1e3d72);
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: bold;
            transition: background 0.3s, transform 0.2s;
        }
        
        .add-to-cart:hover {
            background: linear-gradient(135deg, #1e3d72, #2c5aa0);
            transform: translateY(-2px);
        }
        
        .cart-sidebar {
            position: fixed;
            top: 0;
            right: -400px;
            width: 400px;
            height: 100vh;
            background: white;
            box-shadow: -2px 0 10px rgba(0,0,0,0.1);
            transition: right 0.3s;
            z-index: 1000;
            overflow-y: auto;
        }
        
        .cart-sidebar.open {
            right: 0;
        }
        
        .cart-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 999;
            display: none;
        }
        
        .cart-overlay.show {
            display: block;
        }
        
        .cart-header {
            background: #2c5aa0;
            color: white;
            padding: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .close-cart {
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
        }
        
        .cart-content {
            padding: 1rem;
        }
        
        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
            border-bottom: 1px solid #eee;
        }
        
        .cart-item-info {
            flex: 1;
        }
        
        .cart-item-name {
            font-weight: bold;
            margin-bottom: 0.5rem;
        }
        
        .cart-item-price {
            color: #e74c3c;
            font-weight: bold;
        }
        
        .quantity-controls {
            display: flex;
            align-items: center;
            gap: 10px;
            margin: 10px 0;
        }
        
        .quantity-btn {
            background: #2c5aa0;
            color: white;
            border: none;
            width: 30px;
            height: 30px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }
        
        .quantity-btn:hover {
            background: #1e3d72;
        }
        
        .remove-item {
            background: #e74c3c;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 3px;
            cursor: pointer;
            font-size: 0.8rem;
        }
        
        .remove-item:hover {
            background: #c0392b;
        }
        
        .cart-total {
            background: #f8f9fa;
            padding: 1rem;
            margin: 1rem 0;
            border-radius: 5px;
            text-align: center;
        }
        
        .total-amount {
            font-size: 1.5rem;
            font-weight: bold;
            color: #2c5aa0;
        }
        
        .payment-section {
            background: #f8f9fa;
            padding: 1.5rem;
            margin-top: 1rem;
            border-radius: 8px;
            border: 2px solid #2c5aa0;
        }
        
        .payment-title {
            color: #2c5aa0;
            font-size: 1.3rem;
            font-weight: bold;
            margin-bottom: 1rem;
            text-align: center;
        }
        
        .payment-info {
            background: white;
            padding: 1rem;
            border-radius: 5px;
            margin-bottom: 1rem;
        }
        
        .payment-method {
            margin-bottom: 1rem;
            padding: 1rem;
            background: #fff;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        
        .payment-method h4 {
            color: #2c5aa0;
            margin-bottom: 0.5rem;
        }
        
        .bank-details {
            font-family: 'Courier New', monospace;
            background: #f0f0f0;
            padding: 0.8rem;
            border-radius: 3px;
            margin: 0.5rem 0;
        }
        
        .instructions {
            background: #e8f4fd;
            padding: 1rem;
            border-left: 4px solid #2c5aa0;
            margin: 1rem 0;
        }
        
        .instructions h4 {
            color: #2c5aa0;
            margin-bottom: 0.5rem;
        }
        
        .order-form {
            background: white;
            padding: 1rem;
            border-radius: 5px;
            margin-top: 1rem;
        }
        
        .form-group {
            margin-bottom: 1rem;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 0.3rem;
            font-weight: bold;
            color: #333;
        }
        
        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 1rem;
        }
        
        .form-group textarea {
            height: 80px;
            resize: vertical;
        }
        
        .submit-order {
            width: 100%;
            background: linear-gradient(135deg, #27ae60, #2ecc71);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 5px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.3s;
        }
        
        .submit-order:hover {
            background: linear-gradient(135deg, #2ecc71, #27ae60);
        }
        
        .empty-cart {
            text-align: center;
            color: #666;
            font-style: italic;
            padding: 2rem;
        }
        
        footer {
            background: #2c5aa0;
            color: white;
            text-align: center;
            padding: 2rem 0;
        }
        
        @media (max-width: 768px) {
            .cart-sidebar {
                width: 100%;
                right: -100%;
            }
            
            .hero h1 {
                font-size: 2rem;
            }
            
            .header-content {
                flex-direction: column;
                gap: 1rem;
            }
            
            nav ul {
                gap: 1rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <div class="header-content">
                <div>
                    <div class="logo">Lure Kings</div>
                    <div class="tagline">Australian Owned and Operated</div>
                </div>
                <nav>
                    <ul>
                        <li><a href="#all">All Lures</a></li>
                        <li><a href="#jigs">Jigs</a></li>
                        <li><a href="#plastics">Soft Plastics</a></li>
                        <li><a href="#topwaters">Topwaters</a></li>
                        <li><a href="#spinnerbaits">Spinnerbaits</a></li>
                    </ul>
                </nav>
                <div class="cart-icon" onclick="toggleCart()">
                    🛒 Cart
                    <span class="cart-count" id="cartCount">0</span>
                </div>
            </div>
        </div>
    </header>

    <section class="hero">
        <div class="container">
            <h1>Premium Fishing Lures</h1>
            <p>Serious value for serious anglers</p>
        </div>
    </section>

    <section class="products">
        <div class="container">
            <h2 style="text-align: center; color: #2c5aa0; margin-bottom: 2rem;">Our Premium Collection</h2>
            <div class="product-grid" id="productGrid">
                <!-- Products will be populated by JavaScript -->
            </div>
        </div>
    </section>

    <!-- Cart Overlay -->
    <div class="cart-overlay" id="cartOverlay" onclick="closeCart()"></div>
    
    <!-- Cart Sidebar -->
    <div class="cart-sidebar" id="cartSidebar">
        <div class="cart-header">
            <h3>Shopping Cart</h3>
            <button class="close-cart" onclick="closeCart()">×</button>
        </div>
        <div class="cart-content">
            <div id="cartItems"></div>
            <div class="cart-total">
                <div class="total-amount">Total: $<span id="cartTotal">0.00</span></div>
            </div>
            
            <!-- Payment Section -->
            <div class="payment-section" id="paymentSection" style="display: none;">
                <div class="payment-title">💳 Complete Your Order</div>
                
                <div class="payment-method">
                    <h4>🏦 Bank Transfer (Preferred)</h4>
                    <div class="bank-details">
                        <strong>Bank:</strong> Commonwealth Bank<br>
                        <strong>Account Name:</strong> Lure Kings Pty Ltd<br>
                        <strong>BSB:</strong> 062-001<br>
                        <strong>Account Number:</strong> 1234 5678<br>
                        <strong>Reference:</strong> Your Order ID
                    </div>
                </div>
                
                <div class="payment-method">
                    <h4>💰 PayPal</h4>
                    <div class="bank-details">
                        <strong>PayPal Email:</strong> payments@lurekings.com.au<br>
                        <strong>Please include:</strong> Your order details in the payment note
                    </div>
                </div>
                
                <div class="instructions">
                    <h4>📋 Payment Instructions:</h4>
                    <ol>
                        <li>Fill out the order form below</li>
                        <li>Click "Submit Order" to get your Order ID</li>
                        <li>Make payment using your preferred method above</li>
                        <li>Include your Order ID in the payment reference</li>
                        <li>We'll process your order within 24 hours</li>
                    </ol>
                </div>
                
                <div class="order-form">
                    <h4 style="color: #2c5aa0; margin-bottom: 1rem;">📝 Order Details</h4>
                    <div class="form-group">
                        <label for="customerName">Full Name *</label>
                        <input type="text" id="customerName" required>
                    </div>
                    <div class="form-group">
                        <label for="customerEmail">Email Address *</label>
                        <input type="email" id="customerEmail" required>
                    </div>
                    <div class="form-group">
                        <label for="customerPhone">Phone Number</label>
                        <input type="tel" id="customerPhone">
                    </div>
                    <div class="form-group">
                        <label for="shippingAddress">Shipping Address *</label>
                        <textarea id="shippingAddress" placeholder="Enter your full shipping address..." required></textarea>
                    </div>
                    <div class="form-group">
                        <label for="orderNotes">Order Notes (Optional)</label>
                        <textarea id="orderNotes" placeholder="Any special instructions or comments..."></textarea>
                    </div>
                    <button class="submit-order" onclick="submitOrder()">
                        🚀 Submit Order & Get Order ID
                    </button>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <div class="container">
            <p>&copy; 2025 Lure Kings. All rights reserved. | Australian Owned and Operated</p>
        </div>
    </footer>

    <script>
        // Sample product data
        const products = [
            { id: 1, name: "Thunder Jig - Gold", price: 15.99, category: "jigs", emoji: "🎣" },
            { id: 2, name: "Spinner Pro - Silver", price: 18.50, category: "spinnerbaits", emoji: "🌪️" },
            { id: 3, name: "Soft Worm - Green", price: 12.75, category: "plastics", emoji: "🐛" },
            { id: 4, name: "Popper King - Red", price: 22.00, category: "topwaters", emoji: "💥" },
            { id: 5, name: "Deep Diver - Blue", price: 19.99, category: "jigs", emoji: "🏊" },
            { id: 6, name: "Surface Splasher", price: 16.25, category: "topwaters", emoji: "💦" },
            { id: 7, name: "Grub Tail - Pink", price: 11.50, category: "plastics", emoji: "🪱" },
            { id: 8, name: "Bass Buster Spinner", price: 24.99, category: "spinnerbaits", emoji: "⚡" }
        ];

        let cart = [];

        // Initialize the store
        function initStore() {
            displayProducts();
            updateCartDisplay();
        }

        // Display products
        function displayProducts() {
            const productGrid = document.getElementById('productGrid');
            productGrid.innerHTML = products.map(product => `
                <div class="product-card">
                    <div class="product-image">${product.emoji}</div>
                    <div class="product-info">
                        <div class="product-name">${product.name}</div>
                        <div class="product-price">$${product.price.toFixed(2)}</div>
                        <button class="add-to-cart" onclick="addToCart(${product.id})">
                            Add to Cart
                        </button>
                    </div>
                </div>
            `).join('');
        }

        // Add product to cart
        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const existingItem = cart.find(item => item.id === productId);
            
            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({ ...product, quantity: 1 });
            }
            
            updateCartDisplay();
            
            // Visual feedback
            const button = event.target;
            const originalText = button.textContent;
            button.textContent = 'Added!';
            button.style.background = '#27ae60';
            setTimeout(() => {
                button.textContent = originalText;
                button.style.background = '';
            }, 1000);
        }

        // Update cart display
        function updateCartDisplay() {
            const cartCount = document.getElementById('cartCount');
            const cartItems = document.getElementById('cartItems');
            const cartTotal = document.getElementById('cartTotal');
            const paymentSection = document.getElementById('paymentSection');
            
            const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
            const totalPrice = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            
            cartCount.textContent = totalItems;
            cartTotal.textContent = totalPrice.toFixed(2);
            
            if (cart.length === 0) {
                cartItems.innerHTML = '<div class="empty-cart">Your cart is empty</div>';
                paymentSection.style.display = 'none';
            } else {
                cartItems.innerHTML = cart.map(item => `
                    <div class="cart-item">
                        <div class="cart-item-info">
                            <div class="cart-item-name">${item.name}</div>
                            <div class="cart-item-price">$${item.price.toFixed(2)} each</div>
                            <div class="quantity-controls">
                                <button class="quantity-btn" onclick="changeQuantity(${item.id}, -1)">-</button>
                                <span>Qty: ${item.quantity}</span>
                                <button class="quantity-btn" onclick="changeQuantity(${item.id}, 1)">+</button>
                            </div>
                        </div>
                        <button class="remove-item" onclick="removeFromCart(${item.id})">Remove</button>
                    </div>
                `).join('');
                paymentSection.style.display = 'block';
            }
        }

        // Change quantity
        function changeQuantity(productId, change) {
            const item = cart.find(item => item.id === productId);
            if (item) {
                item.quantity += change;
                if (item.quantity <= 0) {
                    removeFromCart(productId);
                } else {
                    updateCartDisplay();
                }
            }
        }

        // Remove from cart
        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCartDisplay();
        }

        // Toggle cart
        function toggleCart() {
            const cartSidebar = document.getElementById('cartSidebar');
            const cartOverlay = document.getElementById('cartOverlay');
            
            cartSidebar.classList.toggle('open');
            cartOverlay.classList.toggle('show');
        }

        // Close cart
        function closeCart() {
            const cartSidebar = document.getElementById('cartSidebar');
            const cartOverlay = document.getElementById('cartOverlay');
            
            cartSidebar.classList.remove('open');
            cartOverlay.classList.remove('show');
        }

        // Submit order
        function submitOrder() {
            const name = document.getElementById('customerName').value;
            const email = document.getElementById('customerEmail').value;
            const phone = document.getElementById('customerPhone').value;
            const address = document.getElementById('shippingAddress').value;
            const notes = document.getElementById('orderNotes').value;
            
            if (!name || !email || !address) {
                alert('Please fill in all required fields (Name, Email, and Shipping Address)');
                return;
            }
            
            // Generate order ID
            const orderId = 'LK' + Date.now().toString().slice(-8);
            
            // Create order summary
            const orderSummary = {
                orderId: orderId,
                customer: { name, email, phone, address },
                items: cart,
                total: cart.reduce((sum, item) => sum + (item.price * item.quantity), 0),
                notes: notes,
                date: new Date().toLocaleString()
            };
            
            // Create order confirmation message
            const itemsList = cart.map(item => 
                `• ${item.name} - Qty: ${item.quantity} - $${(item.price * item.quantity).toFixed(2)}`
            ).join('\n');
            
            const confirmationMessage = `
🎣 ORDER CONFIRMATION - LURE KINGS

Order ID: ${orderId}
Date: ${orderSummary.date}

Customer Details:
Name: ${name}
Email: ${email}
Phone: ${phone || 'Not provided'}

Shipping Address:
${address}

Items Ordered:
${itemsList}

Total Amount: $${orderSummary.total.toFixed(2)}

Payment Instructions:
1. Transfer $${orderSummary.total.toFixed(2)} to:
   BSB: 062-001
   Account: 1234 5678
   Reference: ${orderId}

2. Or PayPal: payments@lurekings.com.au
   (Include Order ID: ${orderId})

${notes ? `\nSpecial Instructions:\n${notes}` : ''}

We'll process your order within 24 hours of payment confirmation.
Thank you for choosing Lure Kings!
            `;
            
            alert(confirmationMessage);
            
            // Clear cart and form
            cart = [];
            updateCartDisplay();
            document.getElementById('customerName').value = '';
            document.getElementById('customerEmail').value = '';
            document.getElementById('customerPhone').value = '';
            document.getElementById('shippingAddress').value = '';
            document.getElementById('orderNotes').value = '';
            
            closeCart();
        }

        // Initialize the store when page loads
        document.addEventListener('DOMContentLoaded', initStore);
    </script>
</body>
</html>
