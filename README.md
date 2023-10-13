# InshutiMall
This is online Mall
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Online Store</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 1rem;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            padding: 2rem;
        }
        .product {
            background-color: #fff;
            border: 1px solid #ddd;
            padding: 1rem;
            margin: 1rem;
            text-align: center;
        }
        button {
            background-color: #007bff;
            color: #fff;
            border: none;
            padding: 0.5rem 1rem;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .cart {
            text-align: center;
            margin: 2rem;
        }
    </style>
</head>
<body>
    <header>
        <h1>Simple Online Store</h1>
    </header>
    <div class="container">
        <div class="product">
            <h2>Product 1</h2>
            <p>Price: $10</p>
            <button onclick="addToCart(1)">Add to Cart</button>
        </div>
        <div class="product">
            <h2>Product 2</h2>
            <p>Price: $15</p>
            <button onclick="addToCart(2)">Add to Cart</button>
        </div>
        <div class="product">
            <h2>Product 3</h2>
            <p>Price: $20</p>
            <button onclick="addToCart(3)">Add to Cart</button>
        </div>
        <div class="cart">
            <h2>Shopping Cart</h2>
            <ul id="cartItems">
                <!-- Cart items will be displayed here dynamically using JavaScript -->
            </ul>
            <p>Total: $<span id="cartTotal">0</span></p>
        </div>
    </div>

    <script>
        let cart = {};
        const productPrices = {
            1: 10,
            2: 15,
            3: 20
        };

        function addToCart(productId) {
            if (cart[productId]) {
                cart[productId]++;
            } else {
                cart[productId] = 1;
            }

            displayCart();
        }

        function displayCart() {
            const cartItems = document.getElementById('cartItems');
            const cartTotal = document.getElementById('cartTotal');
            let cartHtml = '';
            let total = 0;

            for (const productId in cart) {
                const quantity = cart[productId];
                const price = productPrices[productId];
                total += price * quantity;
                cartHtml += `<li>Product ${productId} x ${quantity}</li>`;
            }

            cartItems.innerHTML = cartHtml;
            cartTotal.textContent = total;
        }
    </script>
</body>
</html>
