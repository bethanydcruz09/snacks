<!DOCTYPE html>
<html>
    <head>
        <title>Ordering</title>
    </head>
    <body>
        <h1 style="text-align:center">Welcome to my webpage</h1>
        <div class="body">
            <h4>Choose a snack:</h4>
            <select id="snacks" onchange="total()">
                <option value="None" data-price="0.00">None</option>
                <option value="Cupcake" data-price="1.50">Cupcake ($1.50)</option>
                <option value="Chocolate" data-price="2.00">Chocolate ($2.00)</option>
                <option value="Cookies" data-price="2.50">Cookies ($2.50)</option>
                <option value="Gummy bears" data-price="3.00">Gummy bears ($3.00)</option>
            </select>
            <h4>Choose a drink:</h4>
            <select id="drinks" onchange="total()">
                <option value="None" data-price="0.00">None</option>
                <option value="Smoothie" data-price="0.50">Smoothie ($0.50)</option>
                <option value="Tea" data-price="1.00">Tea ($1.00)</option>
                <option value="Milkshake" data-price="1.50">Milkshake ($1.50)</option>
                <option value="Lemonade" data-price="2.00">Lemonade ($2.00)</option>
            </select>
            <p id="price">Total Price: $0.00</p>
            <button onclick="warnings()"><strong>Submit</strong></button>
        </div>
        <style>
            .body { text-align: center; width: 300px; background-color: Pink; padding: 20px 5px 20px 5px; margin: 0 auto; }
            .body button { color: LightYellow; }


        </style>
        <script>
    let formattedPrice = "0.00"; // Global variable
    
    function total() {
        const dropdown1 = document.querySelector('#snacks');
        const dropdown2 = document.querySelector('#drinks');
        const selectedOption1 = dropdown1.options[dropdown1.selectedIndex];
        const selectedOption2 = dropdown2.options[dropdown2.selectedIndex];
        const snackPrice = selectedOption1.getAttribute("data-price");
        const drinkPrice = selectedOption2.getAttribute("data-price");
        const actualPrice1 = parseFloat(snackPrice);
        const actualPrice2 = parseFloat(drinkPrice);
        const preprice = actualPrice1 + actualPrice2;

        formattedPrice = preprice.toFixed(2); // Update global variable

        document.getElementById("price").textContent = "Total Price: $" + formattedPrice;
    }

    function warnings() {
        alert("Your information has been submitted.");
        window.location.href = "checkout.html?formattedPrice=" + encodeURIComponent(formattedPrice);
    }
</script>
    </body>
</html>
