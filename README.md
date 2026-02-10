<index.html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Coffee Bar</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:"Segoe UI", Arial, sans-serif;}
body{ background:#f6efe8; color:#3b2a24; }

/* HEADER */
.header{ background:#3b2a24; color:#fff; padding:18px 30px; display:flex; justify-content:space-between; align-items:center; }
.logo{ font-size:22px; font-weight:bold; }
.nav a{ margin-left:25px; cursor:pointer; font-weight:500; }
.cart{ position:relative; font-size:20px; cursor:pointer; }
.cart span{ position:absolute; top:-8px; right:-10px; background:#c89b6d; color:#3b2a24; font-size:12px; padding:2px 6px; border-radius:50%; }

/* SECTIONS */
.section{ display:none; }
.container{ max-width:1200px; margin:40px auto; padding:0 20px; }

/* LANDING */
.landing{ display:flex; gap:50px; align-items:center; }
.landing-text{ width:50%; }
.landing-text h1{ font-size:44px; }
.landing-text p{ margin:18px 0; color:#5a463d; }
.shop-btn{ padding:14px 36px; border:none; background:#c89b6d; color:#3b2a24; font-weight:bold; border-radius:30px; cursor:pointer; }
.landing img{ width:50%; border-radius:18px; }

/* PRODUCTS */
.products{ display:flex; gap:20px; overflow-x:auto; }
.product{ min-width:220px; background:#fff; border-radius:18px; box-shadow:0 8px 20px rgba(0,0,0,0.08); }
.product img{ width:100%; height:180px; object-fit:cover; border-radius:18px 18px 0 0; }
.product-info{ padding:18px; }
.desc{ font-size:13px; color:#6a574d; }
.price{ color:#c89b6d; font-weight:bold; margin:8px 0; }
.buy-btn{ width:100%; padding:10px; border:none; background:#3b2a24; color:#fff; border-radius:25px; cursor:pointer; }

/* CART */
.cart-panel{ margin-top:30px; background:#fff; padding:25px; border-radius:18px; }
.cart-item{ display:flex; gap:10px; border-bottom:1px dashed #c89b6d; padding:10px 0; }
.cart-item img{ width:60px; height:60px; border-radius:10px; }
.quantity button{ padding:2px 8px; background:#c89b6d; border:none; border-radius:5px; cursor:pointer; }
.total{ text-align:right; margin-top:10px; font-weight:bold; }

/* DASHBOARD */
.dashboard-grid{ display:grid; grid-template-columns:repeat(auto-fit,minmax(200px,1fr)); gap:20px; }
.dash-card{ background:#fff; padding:30px; border-radius:18px; text-align:center; box-shadow:0 8px 20px rgba(0,0,0,0.08); }
.dash-card h3{ color:#c89b6d; }

/* RECEIPT */
#receiptModal{ display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.5); justify-content:center; align-items:center; }
#receiptModal > div{ background:#fff; padding:30px; border-radius:15px; max-width:400px; width:90%; text-align:left; position:relative; }
#receiptModal span{ position:absolute; top:10px; right:15px; font-size:20px; cursor:pointer; }
#receiptContent p{ margin:5px 0; }

@media(max-width:900px){ .landing{ flex-direction:column; } .landing-text,.landing img{ width:100%; text-align:center; } }
</style>
</head>
<body>

<!-- HEADER -->
<div class="header">
    <div class="logo">☕ Coffee Bar</div>
    <div class="nav">
        <a onclick="showSection('landing')">Home</a>
        <a onclick="showSection('shop')">Menu</a>
        <a onclick="showSection('dashboard')">Dashboard</a>
    </div>
    <div class="cart" onclick="showSection('checkout')">🛒 <span id="cartCount">0</span></div>
</div>

<!-- LANDING -->
<div class="section" id="landing">
<div class="container landing">
    <div class="landing-text">
        <h1>Your Daily Coffee Ritual</h1>
        <p>Fresh coffee, pastries, and cakes made with love ☕</p>
        <button class="shop-btn" onclick="showSection('shop')">View Menu</button>
    </div>
    <img src="https://images.unsplash.com/photo-1509042239860-f550ce710b93">
</div>
</div>

<!-- SHOP -->
<div class="section" id="shop">
<div class="container">

<!-- Coffee Products -->
<h2>☕ Coffee</h2>
<div class="products">
    <div class="product">
        <img src="https://images.unsplash.com/photo-1511920170033-f8396924c348">
        <div class="product-info">
            <h4>Espresso</h4>
            <p class="desc">Strong and bold espresso shot.</p>
            <div class="price">₱120</div>
            <button class="buy-btn" onclick="addToCart('Espresso',120,'https://images.unsplash.com/photo-1511920170033-f8396924c348')">Add</button>
        </div>
    </div>
    <div class="product">
        <img src="https://images.unsplash.com/photo-1509042239860-f550ce710b93">
        <div class="product-info">
            <h4>Cappuccino</h4>
            <p class="desc">Espresso with steamed milk foam.</p>
            <div class="price">₱150</div>
            <button class="buy-btn" onclick="addToCart('Cappuccino',150,'https://images.unsplash.com/photo-1509042239860-f550ce710b93')">Add</button>
        </div>
    </div>
    <div class="product">
        <img src="https://images.unsplash.com/photo-1565958011703-44d1b1d4b14d">
        <div class="product-info">
            <h4>Latte</h4>
            <p class="desc">Smooth espresso with steamed milk.</p>
            <div class="price">₱160</div>
            <button class="buy-btn" onclick="addToCart('Latte',160,'https://images.unsplash.com/photo-1565958011703-44d1b1d4b14d')">Add</button>
        </div>
    </div>
    <div class="product">
        <img src="https://images.unsplash.com/photo-1509042239860-f550ce710b93">
        <div class="product-info">
            <h4>Americano</h4>
            <p class="desc">Espresso diluted with hot water.</p>
            <div class="price">₱130</div>
            <button class="buy-btn" onclick="addToCart('Americano',130,'https://images.unsplash.com/photo-1509042239860-f550ce710b93')">Add</button>
        </div>
    </div>
</div>

<!-- Pastry Products -->
<h2>🥐 Pastry</h2>
<div class="products">
    <div class="product">
        <img src="https://images.unsplash.com/photo-1608198093002-ad4e005484ec">
        <div class="product-info">
            <h4>Butter Croissant</h4>
            <p class="desc">Flaky buttery croissant.</p>
            <div class="price">₱95</div>
            <button class="buy-btn" onclick="addToCart('Butter Croissant',95,'https://images.unsplash.com/photo-1608198093002-ad4e005484ec')">Add</button>
        </div>
    </div>
    <div class="product">
        <img src="https://images.unsplash.com/photo-1603079841841-7f3c3c6b8f6b">
        <div class="product-info">
            <h4>Cinnamon Roll</h4>
            <p class="desc">Soft roll with cinnamon sugar glaze.</p>
            <div class="price">₱120</div>
            <button class="buy-btn" onclick="addToCart('Cinnamon Roll',120,'https://images.unsplash.com/photo-1603079841841-7f3c3c6b8f6b')">Add</button>
        </div>
    </div>
    <div class="product">
        <img src="https://images.unsplash.com/photo-1617196031394-40b6ff5d1256">
        <div class="product-info">
            <h4>Cheese Danish</h4>
            <p class="desc">Soft pastry with creamy cheese filling.</p>
            <div class="price">₱110</div>
            <button class="buy-btn" onclick="addToCart('Cheese Danish',110,'https://images.unsplash.com/photo-1617196031394-40b6ff5d1256')">Add</button>
        </div>
    </div>
    <div class="product">
        <img src="https://images.unsplash.com/photo-1617196031394-40b6ff5d1256">
        <div class="product-info">
            <h4>Chocolate Croissant</h4>
            <p class="desc">Flaky croissant filled with chocolate.</p>
            <div class="price">₱130</div>
            <button class="buy-btn" onclick="addToCart('Chocolate Croissant',130,'https://images.unsplash.com/photo-1617196031394-40b6ff5d1256')">Add</button>
        </div>
    </div>
</div>

<!-- Cake Products -->
<h2>🍰 Cake</h2>
<div class="products">
    <div class="product">
        <img src="https://images.unsplash.com/photo-1578985545062-69928b1d9587">
        <div class="product-info">
            <h4>Chocolate Cake</h4>
            <p class="desc">Moist chocolate cake with frosting.</p>
            <div class="price">₱180</div>
            <button class="buy-btn" onclick="addToCart('Chocolate Cake',180,'https://images.unsplash.com/photo-1578985545062-69928b1d9587')">Add</button>
        </div>
    </div>
    <div class="product">
        <img src="https://images.unsplash.com/photo-1614707267537-b85aaf00c4b7">
        <div class="product-info">
            <h4>Red Velvet</h4>
            <p class="desc">Soft red velvet with cream cheese frosting.</p>
            <div class="price">₱200</div>
            <button class="buy-btn" onclick="addToCart('Red Velvet',200,'https://images.unsplash.com/photo-1614707267537-b85aaf00c4b7')">Add</button>
        </div>
    </div>
</div>

<div class="cart-panel">
    <h3>Your Cart</h3>
    <div id="cartItems"></div>
    <div class="total" id="total">Total: ₱0</div>
    <button class="shop-btn" onclick="showSection('checkout')">Checkout</button>
</div>

</div>
</div>

<!-- CHECKOUT -->
<div class="section" id="checkout">
<div class="container">
<h2>Checkout</h2>
<div class="cart-panel">

<h3>Payment Method</h3>
<div class="payment-options" style="margin-bottom:15px;">
    <label><input type="radio" name="payment" value="GCash" checked> GCash</label>
    <label><input type="radio" name="payment" value="Card"> Card</label>
    <label><input type="radio" name="payment" value="Cash"> Cash</label>
</div>

<h3>Order Summary</h3>
<div id="checkoutItems"></div>
<div class="total" id="checkoutTotal">Total: ₱0</div>
<button class="shop-btn" onclick="placeOrder()">Place Order</button>
</div>
</div>
</div>

<!-- SUCCESS -->
<div class="section" id="success">
<div class="container" style="text-align:center;">
    <h1>✅ Order Successful</h1>
    <p>Your coffee is being prepared ☕</p>
    <button class="shop-btn" onclick="showSection('landing')">Home</button>
</div>
</div>

<!-- DASHBOARD -->
<div class="section" id="dashboard">
<div class="container">
<h2>📊 Dashboard</h2>
<div class="dashboard-grid">
    <div class="dash-card"><h3>Total Sales</h3><p id="dashSales">₱0</p></div>
    <div class="dash-card"><h3>Total Orders</h3><p id="dashOrders">0</p></div>
</div>
</div>
</div>

<!-- RECEIPT -->
<div id="receiptModal">
  <div>
    <span onclick="closeReceipt()">×</span>
    <h2 style="text-align:center;">🧾 Receipt</h2>
    <div id="receiptContent"></div>
    <h3 id="receiptTotal" style="text-align:right;"></h3>
    <button class="shop-btn" style="width:100%;margin-top:20px;" onclick="closeReceipt()">Close</button>
  </div>
</div>

<script>
let cart=[];
let totalSales=0;
let totalOrders=0;

showSection('landing');

function showSection(id){
    document.querySelectorAll('.section').forEach(s=>s.style.display="none");
    document.getElementById(id).style.display="block";
    if(id==="checkout") loadCheckout();
    if(id==="dashboard") updateDashboard();
}

function addToCart(name, price, img){
    let item = cart.find(i=>i.name===name);
    if(item){ item.qty++; } 
    else{ cart.push({name,price,img,qty:1}); }
    updateCart();
}

function updateCart(){
    let html="";
    let total=0;
    cart.forEach(i=>{
        total+=i.price*i.qty;
        html+=`
        <div class="cart-item">
            <img src="${i.img}">
            <div>
                <strong>${i.name}</strong><br>
                ₱${i.price} x ${i.qty}
            </div>
        </div>`;
    });
    document.getElementById("cartItems").innerHTML=html;
    document.getElementById("total").innerText="Total: ₱"+total;
    document.getElementById("cartCount").innerText=cart.reduce((a,b)=>a+b.qty,0);
}

function loadCheckout(){
    let html="";
    let total=0;
    cart.forEach(i=>{
        total+=i.price*i.qty;
        html+=`<p>${i.name} x ${i.qty} - ₱${i.price*i.qty}</p>`;
    });
    document.getElementById("checkoutItems").innerHTML=html;
    document.getElementById("checkoutTotal").innerText="Total: ₱"+total;
}

function placeOrder(){
    let orderTotal = cart.reduce((a,b)=>a+(b.price*b.qty),0);
    totalSales += orderTotal;
    totalOrders++;

    // Get selected payment method
    let paymentMethod = document.querySelector('input[name="payment"]:checked').value;

    // Generate receipt
    let receiptHTML = '';
    cart.forEach(i=>{
        receiptHTML += `<p>${i.name} x ${i.qty} - ₱${i.price*i.qty}</p>`;
    });
    receiptHTML += `<p><strong>Payment Method:</strong> ${paymentMethod}</p>`;

    document.getElementById("receiptContent").innerHTML = receiptHTML;
    document.getElementById("receiptTotal").innerText = "Total: ₱"+orderTotal;
    document.getElementById("receiptModal").style.display="flex";

    // Clear cart
    cart=[];
    updateCart();
    showSection('success');
}

function closeReceipt(){
    document.getElementById("receiptModal").style.display="none";
}

function updateDashboard(){
    document.getElementById("dashSales").innerText="₱"+totalSales;
    document.getElementById("dashOrders").innerText=totalOrders;
}
</script>

</body>
</html>
