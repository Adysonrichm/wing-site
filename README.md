<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>FlavorRush Wings</title>

<style>
body {
  margin: 0;
  font-family: Arial;
  background: #111;
  color: white;
}

header {
  padding: 15px;
  text-align: center;
  background: black;
  font-size: 22px;
  font-weight: bold;
}

.menu {
  padding: 15px;
}

.card {
  background: #1c1c1c;
  border-radius: 12px;
  padding: 12px;
  margin-bottom: 12px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  transition: 0.2s;
}

.card:hover {
  transform: scale(1.02);
}

.card img {
  width: 60px;
  border-radius: 10px;
}

.info {
  flex: 1;
  margin-left: 10px;
}

button {
  background: #ff5a00;
  border: none;
  color: white;
  padding: 8px 12px;
  border-radius: 6px;
}

.cart-btn {
  position: fixed;
  bottom: 20px;
  right: 20px;
  background: #ff5a00;
  padding: 12px;
  border-radius: 50%;
}

.cart-panel {
  position: fixed;
  bottom: -100%;
  left: 0;
  width: 100%;
  background: #222;
  padding: 20px;
  transition: 0.3s;
}

.cart-panel.active {
  bottom: 0;
}

</style>
</head>

<body>

<header>🔥 FlavorRush Wings</header>

<div class="menu">

  <div class="card">
    <img src="https://source.unsplash.com/100x100/?chicken-wings">
    <div class="info">
      <div>10pc Wings</div>
      <small>$10</small>
    </div>
    <button onclick="add('10pc Wings',10)">Add</button>
  </div>

  <div class="card">
    <img src="https://source.unsplash.com/100x100/?fries">
    <div class="info">
      <div>Fries</div>
      <small>$4</small>
    </div>
    <button onclick="add('Fries',4)">Add</button>
  </div>

  <div class="card">
    <img src="https://source.unsplash.com/100x100/?soda">
    <div class="info">
      <div>Drink</div>
      <small>$2</small>
    </div>
    <button onclick="add('Drink',2)">Add</button>
  </div>

</div>

<button class="cart-btn" onclick="toggleCart()">🛒</button>

<div class="cart-panel" id="cartPanel">
  <h3>Your Cart</h3>
  <div id="cartItems"></div>
  <h4>Total: $<span id="total">0</span></h4>
  <button onclick="checkout()">Checkout</button>
</div>

<script>
let cart = {};
let total = 0;

function add(name, price) {
  if (!cart[name]) {
    cart[name] = {price: price, qty: 1};
  } else {
    cart[name].qty++;
  }
  total += price;
  updateCart();
}

function updateCart() {
  let html = "";
  for (let item in cart) {
    html += `<div>${item} x${cart[item].qty}</div>`;
  }
  document.getElementById("cartItems").innerHTML = html;
  document.getElementById("total").innerText = total;
}

function toggleCart() {
  document.getElementById("cartPanel").classList.toggle("active");
}

function checkout() {
  alert("Order placed! 🔥");
}
</script>

</body>
</html>
