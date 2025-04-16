<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>TechNest - Home</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; padding: 0; }
    header { background-color: #111; color: #fff; padding: 1rem; text-align: center; }
    nav a { color: #fff; margin: 0 1rem; text-decoration: none; }
    .hero { background: #eee; padding: 3rem 1rem; text-align: center; }
    .products { display: flex; flex-wrap: wrap; justify-content: center; gap: 2rem; padding: 2rem; }
    .product { border: 1px solid #ccc; padding: 1rem; width: 200px; text-align: center; }
    .cart { position: fixed; top: 1rem; right: 1rem; background: #fff; padding: 1rem; border: 1px solid #ccc; }
    .checkout { padding: 2rem; }
    footer { background: #111; color: #fff; text-align: center; padding: 1rem; margin-top: 2rem; }
    button { padding: 0.5rem 1rem; margin-top: 0.5rem; cursor: pointer; }
  </style>
</head>
<body>
  <header>
    <h1>TechNest</h1>
    <nav>
      <a href="#home">Home</a>
      <a href="#products">Products</a>
      <a href="#checkout">Checkout</a>
    </nav>
  </header>  <section class="hero" id="home">
    <h2>Welcome to TechNest</h2>
    <p>Your favorite online gadget store</p>
  </section>  <section class="products" id="products">
    <div class="product">
      <h3>Smart Watch</h3>
      <p>$49.99</p>
      <button onclick="addToCart('Smart Watch', 49.99)">Add to Cart</button>
    </div>
    <div class="product">
      <h3>Bluetooth Speaker</h3>
      <p>$29.99</p>
      <button onclick="addToCart('Bluetooth Speaker', 29.99)">Add to Cart</button>
    </div>
    <div class="product">
      <h3>Wireless Earbuds</h3>
      <p>$39.99</p>
      <button onclick="addToCart('Wireless Earbuds', 39.99)">Add to Cart</button>
    </div>
  </section>  <div class="cart" id="cart">
    <h3>Cart</h3>
    <ul id="cart-items"></ul>
    <p>Total: $<span id="total">0.00</span></p>
  </div>  <section class="checkout" id="checkout">
    <h2>Checkout</h2>
    <form onsubmit="submitOrder(event)">
      <label>Name:<br><input type="text" required /></label><br><br>
      <label>Email:<br><input type="email" required /></label><br><br>
      <label>Address:<br><textarea required></textarea></label><br><br>
      <button type="submit">Place Order</button>
    </form>
  </section>  <footer>
    <p>&copy; 2025 TechNest. All rights reserved.</p>
  </footer>  <script>
    const cart = [];

    function addToCart(product, price) {
      cart.push({ product, price });
      renderCart();
    }

    function renderCart() {
      const cartItems = document.getElementById('cart-items');
      cartItems.innerHTML = '';
      let total = 0;
      cart.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.product} - $${item.price.toFixed(2)}`;
        cartItems.appendChild(li);
        total += item.price;
      });
      document.getElementById('total').textContent = total.toFixed(2);
    }

    function submitOrder(event) {
      event.preventDefault();
      alert('Order placed successfully!');
      cart.length = 0;
      renderCart();
    }
  </script></body>
</html>
