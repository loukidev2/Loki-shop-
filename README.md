# Loki-shop-
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LOKI_SHOP - Anime T-Shirts</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #111;
      color: #fff;
      margin: 0;
      padding: 0;
    }
    header {
      background-color: #c00;
      padding: 20px;
      text-align: center;
      font-size: 2rem;
      font-weight: bold;
    }
    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      padding: 20px;
    }
    .product {
      background-color: #222;
      border-radius: 8px;
      padding: 10px;
      text-align: center;
    }
    .product img {
      max-width: 100%;
      border-radius: 8px;
    }
    .product h3 {
      color: #e00;
    }
    .product button {
      margin-top: 10px;
      padding: 10px;
      background-color: #c00;
      border: none;
      color: white;
      cursor: pointer;
      border-radius: 5px;
    }
    .cart {
      padding: 20px;
      background-color: #111;
    }
    .cart h2 {
      color: #e00;
    }
  </style>
</head>
<body>
  <header>LOKI_SHOP - Anime T-Shirts</header>  <section class="products" id="product-list">
    <!-- Products inserted by JS -->
  </section>  <section class="cart">
    <h2>Shopping Cart</h2>
    <ul id="cart-items"></ul>
    <p>Total: $<span id="cart-total">0</span></p>
  </section>  <script>
    const products = [
      { id: 1, name: 'Naruto Tee', price: 20, image: 'https://via.placeholder.com/250x300?text=Naruto' },
      { id: 2, name: 'Attack on Titan Tee', price: 25, image: 'https://via.placeholder.com/250x300?text=AOT' },
      { id: 3, name: 'One Piece Tee', price: 22, image: 'https://via.placeholder.com/250x300?text=One+Piece' }
    ];

    const productList = document.getElementById('product-list');
    const cartItems = document.getElementById('cart-items');
    const cartTotal = document.getElementById('cart-total');
    let cart = [];

    function renderProducts() {
      products.forEach(product => {
        const div = document.createElement('div');
        div.className = 'product';
        div.innerHTML = `
          <img src="${product.image}" alt="${product.name}" />
          <h3>${product.name}</h3>
          <p>$${product.price}</p>
          <button onclick="addToCart(${product.id})">Add to Cart</button>
        `;
        productList.appendChild(div);
      });
    }

    function addToCart(id) {
      const product = products.find(p => p.id === id);
      cart.push(product);
      renderCart();
    }

    function renderCart() {
      cartItems.innerHTML = '';
      let total = 0;
      cart.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.name} - $${item.price}`;
        cartItems.appendChild(li);
        total += item.price;
      });
      cartTotal.textContent = total;
    }

    renderProducts();
  </script></body>
</html>
