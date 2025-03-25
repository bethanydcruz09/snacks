<!DOCTYPE html>
<head>

</head>

<body>
    <h1 style="text-align:center">Welcome to my webpage</h1>
    <form id = "test">
        <h4>Choose a snack:</h4>
        <break></break>     
        <select id = "snacks" onchange="total()">
            <option value="None" data-price="0.00">None</option>
            <option value="Chips" data-price="1.50">Chips ($1.50)</option>
            <option value="Cookies" data-price="2.50">Cookies ($2.50)</option>
            <option value="Chocolate" data-price="3.00">Chocolate ($3.00)</option>
            <option value="Popcorn" data-price="2.00">Popcorn ($2.00)</option>
        </select>
        <h4>Choose a drink:</h4>
        <break></break>
        <select id = "drinks" onchange="total()">
            <option value="None" data-price="0.00">None</option>
            <option value="Water" data-price="1.50">Water ($1.50)</option>
            <option value="Pepsi" data-price="1.00">Pepsi ($1.00)</option>
            <option value="Lemonade" data-price="2.00">Lemonade ($2.00)</option>
            <option value="Coca Cola" data-price="0.50">Coca Cola ($0.50)</option>
        </select>
        <p id = "price">Total Price: $0.00</p>
    </form>
    <style>
        form{
            text-align: center;
            width: 250px;
            background-color: pink;
            /*top right bottom left*/
            padding: 15px 5px 15px 5px; 
            margin: 0 auto;
        }
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
</html>
