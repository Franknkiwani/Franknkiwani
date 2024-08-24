<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Example</title>
    <style>
        body {
            background-color: #FF4D4D;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            height: 100vh;
            justify-content: flex-start;
            font-family: Arial, sans-serif;
        }
        .button {
            width: 90%;
            max-width: 400px;
            padding: 10px;
            border: none;
            color: white;
            font-size: 16px;
            cursor: pointer;
            text-align: center;
            border-radius: 20px;
            margin-bottom: 10px;
        }
        .balance-button {
            background-color: #28a745; /* Green */
        }
        .redeem-button {
            background-color: #6f42c1; /* Purple */
        }
        .container {
            width: 90%;
            border: 2px solid #4CAF50;
            border-radius: 10px;
            background: #fff;
            padding: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            margin: 20px auto;
            max-width: 600px;
        }
        .title {
            text-align: center;
            font-size: 24px;
            color: #4CAF50;
            margin-bottom: 20px;
        }
        .button-earn {
            display: block;
            width: 100%;
            height: 30px;
            border: none;
            color: #fff;
            font-size: 16px;
            font-weight: bold;
            text-align: center;
            line-height: 40px;
            margin-bottom: 10px;
            cursor: pointer;
            transition: background 0.3s;
            border-radius: 25px;
        }
        .button-earn:hover {
            opacity: 0.9;
        }
        .earn-click {
            background: #2196F3; /* Blue */
        }
        .earn-video {
            background: #FF5722; /* Orange */
        }
        .earn-checkin {
            background: #4CAF50; /* Green */
        }
        .popup {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            justify-content: center;
            align-items: center;
        }
        .popup-content {
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            width: 80%;
            max-width: 400px;
            text-align: center;
            position: relative;
        }
        .popup input {
            width: calc(100% - 22px);
            padding: 10px;
            margin-bottom: 10px;
            border: 2px solid #4CAF50;
            border-radius: 5px;
        }
        .popup button {
            background-color: #4CAF50;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
        }
        .popup button:hover {
            background-color: #45a049;
        }
        .popup-close {
            background: #FF5722;
        }
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        background-color: white;
        .product-container  {
            width: 90%;
            border: 2px solid #4CAF50;
            border-radius: 10px;
            background: #fff;
            padding: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            margin: 20px auto;
            max-width: 600px;
        }

        .product-image {
            width: 100%;
            height: 30%; /* 50% of the container height for the image */
            overflow: hidden;
            border-radius: 25px;
        }

        .product-image img {
            width: 100%;
            height: 50%;
            object-fit: cover;
            display: block;
        }

        .product-info {
            padding: 5px 10px; /* Reduced padding for compact fit */
            text-align: center;
            height: 25%; /* 25% of the container height for text */
        }

        .product-title {
            font-size: 18px; /* Smaller font size for title */
            color: #333;
            margin-bottom: 3px;
        }

        .product-price {
            font-size: 16px; /* Smaller font size for price */
            color: #28a745;
        }

        .exchange-button {
            display: block;
            width: 30%;
            height: 15%; /* 15% of the container height for the button */
            padding: 8px 0;
            font-size: 14px; /* Smaller font size for the button */
            color: #fff;
            background-color: #007BFF;
            border: none;
            cursor: pointer;
            text-align: center;
            text-decoration: none;
            transition: background-color 0.3s ease;
            border-radius: 25px;
        }

        .exchange-button:hover {
            background-color: #0056b3;
        }
        .button-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 10px;
            width: 100%; /* Ensures the container spans the full width of the parent */
        }

        .prev-button,
        .next-button,
        .exchange-button {
            flex: 1;
            background-color: #007BFF;
            color: #fff;
            padding: 8px 16px;
            border-radius: 25px;
            border: none;
            cursor: pointer;
            font-size: 14px;
            text-align: center;
            transition: background-color 0.3s ease;
            margin: 0 5px; /* Small margin between buttons */
        }

        .prev-button,
        .next-button {
            background-color: #6c757d;
        }

        .prev-button:hover,
        .next-button:hover {
            background-color: #5a6268;
        }

        .exchange-button:hover {
            background-color: #0056b3;
        }
        /* Confirmation Popup CSS */
        .confirmation-popup {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            justify-content: center;
            align-items: center;
            z-index: 999;
        }

        .confirmation-content {
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            width: 80%;
            max-width: 400px;
            text-align: left;
            position: relative;
        }

        .confirmation-content h3 {
            color: #333;
            margin-bottom: 15px;
            text-align: center;
        }

        .input-group {
            margin-bottom: 15px;
        }

        .input-group label {
            font-size: 14px;
            color: #555;
            display: block;
            margin-bottom: 5px;
        }

        .input-group input {
            width: calc(100% - 20px);
            padding: 8px;
            font-size: 14px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        /* New Styles */
        header {
            background-color: #333; /* Dark background color for the header */
            padding: 5px;
            width: 97%;
            color: white; /* Text color to stand out on dark background */
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: fixed;
            top: 0;
            left: 0;
            z-index: 1000; /* Ensure header is on top of other elements */
        }
        h1 {
            font-size: 20px;
            margin: 0;
        }
        .profile-icon {
            width: 30px;
            height: 30px;
            background-color: #555;
            border-radius: 50%;
            cursor: pointer;
        }
        .sidebar {
            position: fixed;
            top: 0;
            right: 0;
            width: 300px;
            height: 100%;
            background-color: #444;
            color: white;
            transform: translateX(100%);
            transition: transform 0.3s ease;
            padding: 20px;
           box-shadow: -2px 0 5px rgba(0, 0, 0, 0.3);
            z-index: 1000; /* Ensure sidebar is on top of other elements */
        }
        .sidebar.show {
            transform: translateX(0);
        }
        .sidebar-option {
            border: 1px solid #666;
            margin: 10px 0;
            padding: 10px;
            text-align: center;
            cursor: pointer;
            border-radius: 5px;
        }
        .sidebar-option:hover {
            background-color: #555;
        }
        .popup {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 300px;
            background-color: #fff;
            color: #000;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
            display: none;
            flex-direction: column;
            align-items: center;
            border-radius: 10px;
            z-index: 1000; /* Ensure popup is on top of other elements */
        }
        .popup.show {
            display: flex;
        }
        .popup button {
            margin-top: 10px;
            padding: 10px;
            background-color: #007bff;
            border: none;
            color: white;
            border-radius: 5px;
            cursor: pointer;
        }
</style>
    </style>
  <header>
    <div id="headerText">Cash Gaming</div>
    <div class="profile-icon" onclick="toggleSidebar()">
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQXRrCyofXrO8T_-T_Z4X_k3eDyjVj6hIaj8g&usqp=CAU" alt="Profile Icon" style="width: 100%; height: 100%; border-radius: 50%;">
    </div>
</header>
    <div id="sidebar" class="sidebar">
        <div class="close-sidebar" onclick="toggleSidebar()">×</div>
        <div class="sidebar-option" onclick="contactUs()">CONTACT US</div>
        <div class="sidebar-option" onclick="donate()">DONATE</div>
        <div class="sidebar-option" onclick="buyApp()">BUY THIS APP</div>
        <div class="sidebar-option" onclick="collab()">COLLAB</div>
    </div>
    <div id="popup" class="popup">
        <div class="close-popup" onclick="closePopup()">×</div>
        <h2>Cash Gaming</h2>
        <p>150k Monthly Users</p>
        <p>25k Users Online</p>
        <p>Prize: $999</p>
        <button onclick="completePurchase()">Complete</button>
    </div>
<body>
 <button class="button balance-button" id="itpizza">$0.000 POINTS</button>
    <button class="button redeem-button" id="redeemButton">REDEEM CODES</button>
        <button class="button balance-button" id="balanceButton">$0.000 POINTS</button>
    <div class="container">
        <div class="title">Earn Now</div>
        <button class="button-earn earn-click" id="clickToEarn">Click to Earn $0.001 Points</button>
        <button class="button-earn earn-video" id="watchVideo">Watch Video and Earn $0.050 Points</button>
        <button class="button-earn earn-checkin" id="dailyCheckIn">Daily Check-In and Earn $0.100 Points</button>
         <div class="product-container">
    <div class="product-image">
        <img src="https://via.placeholder.com/1200x500" alt="Product Image">
    </div>
    <div class="product-info">
        <div class="product-title">Product Title</div>
        <div class="product-price">$0.000</div>
    </div>
    <div class="button-container">
        <button class="prev-button">Previous</button>
        <a href="#" class="exchange-button">Exchange Now</a>
        <button class="next-button">Next</button>
    </div>
</div>
    <div class="popup" id="redeemPopup">
        <div class="popup-content">
            <h2>Redeem Code</h2>
            <input type="text" id="redeemCode" placeholder="Enter your code here">
            <button id="redeemSubmit">Submit</button>
            <button class="popup-close" id="popupClose">Close</button>
        </div>
    </div>
    <!-- Confirmation Popup HTML -->
<div class="confirmation-popup" id="confirmationPopup">
    <div class="confirmation-content">
        <h3>Confirm Your Purchase</h3>
        <div class="input-group">
            <label for="productName">Product Name:</label>
            <input type="text" id="productName" readonly>
        </div>
        <div class="input-group">
            <label for="productPrice">Product Price:</label>
            <input type="text" id="productPrice" readonly>
        </div>
        <div class="input-group">
            <label for="currentBalance">Your Current Balance:</label>
            <input type="text" id="currentBalance" readonly>
        </div>
        <div class="input-group">
            <label for="purchaseDate">Date and Time:</label>
            <input type="text" id="purchaseDate" readonly>
        </div>
        <div class="input-group">
            <label for="userName">Your Name (Optional):</label>
            <input type="text" id="userName" placeholder="Enter your name">
        </div>
        <div class="input-group">
            <label for="userAddress">Your Address (Optional):</label>
            <input type="text" id="userAddress" placeholder="Enter your address">
        </div>
        <button id="completePurchase">Complete</button>
    </div>
</div>
<script>
    document.addEventListener('DOMContentLoaded', () => {
        const balanceButton = document.getElementById('balanceButton');
        const redeemButton = document.getElementById('redeemButton');
        const redeemPopup = document.getElementById('redeemPopup');
        const popupClose = document.getElementById('popupClose');
        const redeemSubmit = document.getElementById('redeemSubmit');
        const redeemCode = document.getElementById('redeemCode');
        const clickToEarn = document.getElementById('clickToEarn');
        const watchVideo = document.getElementById('watchVideo');
        const dailyCheckIn = document.getElementById('dailyCheckIn');

        // Initialize points and counters
        let points = parseFloat(localStorage.getItem('points')) || 0;
        let clickCount = parseInt(localStorage.getItem('clickCount')) || 0;
        let lastVideoTime = parseInt(localStorage.getItem('lastVideoTime')) || 0;
        let lastCheckInDate = localStorage.getItem('lastCheckInDate') || '';

        // Update balance button
        balanceButton.textContent = `$${points.toFixed(3)} POINTS`;

        // Check if video can be watched again
        const currentTime = new Date().getTime();
        const oneHour = 60 * 60 * 1000; // 1 hour in milliseconds
        if (currentTime - lastVideoTime < oneHour) {
            watchVideo.disabled = true;
        }

        // Check if daily check-in can be done again
        const today = new Date().toISOString().split('T')[0]; // Current date in YYYY-MM-DD format
        if (lastCheckInDate === today) {
            dailyCheckIn.disabled = true;
        }

        // Show popup
        redeemButton.addEventListener('click', () => {
            redeemPopup.style.display = 'flex';
        });

        // Close popup
        popupClose.addEventListener('click', () => {
            redeemPopup.style.display = 'none';
        });

        // Redeem code
        redeemSubmit.addEventListener('click', () => {
            const code = redeemCode.value.trim();
            const validCodes = {
                'cash': 0.500,
                'frank': 10.000
            };
            if (validCodes[code] && !localStorage.getItem(`redeemed-${code}`)) {
                points += validCodes[code];
                localStorage.setItem('points', points);
                localStorage.setItem(`redeemed-${code}`, 'true');
                balanceButton.textContent = `$${points.toFixed(3)} POINTS`;
                alert('Code redeemed successfully!');
            } else {
                alert('Invalid or already used code.');
            }
            redeemCode.value = '';
            redeemPopup.style.display = 'none';
        });

        // Click to earn
        clickToEarn.addEventListener('click', () => {
            clickCount++;
            points += 0.001;
            localStorage.setItem('points', points);
            balanceButton.textContent = `$${points.toFixed(3)} POINTS`;

            // Redirect after every 10 clicks
            if (clickCount >= 10) {
                localStorage.setItem('clickCount', 0); // Reset click count
                window.location.href = 'https://ooptorsaja.net/4/7165724';
            } else {
                localStorage.setItem('clickCount', clickCount);
            }
        });

        // Watch video
        watchVideo.addEventListener('click', () => {
            const currentTime = new Date().getTime();
            const oneHour = 60 * 60 * 1000; // 1 hour in milliseconds

            if (currentTime - lastVideoTime > oneHour || !lastVideoTime) {
                window.open('https://youtu.be/kRA-4cosIfM?si=x6tg_Yv2CwLIeZUi', '_blank');
                points += 0.050;
                localStorage.setItem('points', points);
                balanceButton.textContent = `$${points.toFixed(3)} POINTS`;
                localStorage.setItem('lastVideoTime', currentTime);
                watchVideo.disabled = true;
            } else {
                alert('You can only watch the video once every hour.');
            }
        });

        // Daily check-in
        dailyCheckIn.addEventListener('click', () => {
            const today = new Date().toISOString().split('T')[0]; // Current date in YYYY-MM-DD format

            if (lastCheckInDate !== today) {
                points += 0.100;
                localStorage.setItem('points', points);
                balanceButton.textContent = `$${points.toFixed(3)} POINTS`;
                localStorage.setItem('lastCheckInDate', today);
                alert('Daily check-in successful! You have earned 0.100 points.');
                dailyCheckIn.disabled = true;
            } else {
                alert('You have already checked in today.');
            }
        });
    });
    document.addEventListener('DOMContentLoaded', () => {
    const balanceButton = document.getElementById('balanceButton');
    const exchangeButtons = document.querySelectorAll('.exchange-button');

    // Initialize points from localStorage
    let points = parseFloat(localStorage.getItem('points')) || 0;

    // Update balance button
    balanceButton.textContent = `$${points.toFixed(3)} POINTS`;

    // Function to handle product exchange
    exchangeButtons.forEach(button => {
        button.addEventListener('click', (event) => {
            event.preventDefault();
            
            // Get the product price from the corresponding product container
            const productContainer = button.closest('.product-container');
            const productPrice = parseFloat(productContainer.querySelector('.product-price').textContent.replace('$', '')) || 0;

            // Check if the user has enough points
            if (points >= productPrice) {
                points -= productPrice;
                localStorage.setItem('points', points);
                balanceButton.textContent = `$${points.toFixed(3)} POINTS`;
                alert('Product exchanged successfully!');
            } else {
                alert('You do not have enough points to exchange for this product.');
            }
        });
    });
});
    document.addEventListener('DOMContentLoaded', () => {
        const products = [
    {
        title: 'Cash and Nico Comic Book',
        price: 20.000,
        image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSzVWhVL-ljFT0eZStcmls1lt7D610hxeAZTweelcY4-kfeM7HX8q8R4yc&s=10'
    },
    {
        title: 'Collab with Cash and Nico',
        price: 10.000,
        image: 'https://static.wikia.nocookie.net/cash-nico/images/7/70/1717880934022.png/revision/latest?cb=20240608210923'
    },
    {
        title: 'Mia Face Reveal',
        price: 5.000,
        image: 'https://i.ytimg.com/vi/kRA-4cosIfM/hq720.jpg?sqp=-oaymwEhCK4FEIIDSFryq4qpAxMIARUAAAAAGAElAADIQj0AgKJD&rs=AOn4CLCgr6K0BDYmZbPSCLrnxDqYOlkDdQ'
    }
];

        let currentIndex = 0;

        const productImage = document.querySelector('.product-image img');
        const productTitle = document.querySelector('.product-title');
        const productPrice = document.querySelector('.product-price');

        function updateProductDisplay() {
            const product = products[currentIndex];
            productImage.src = product.image;
            productTitle.textContent = product.title;
            productPrice.textContent = `$${product.price.toFixed(3)}`;
        }

        document.querySelector('.prev-button').addEventListener('click', () => {
            if (currentIndex > 0) {
                currentIndex--;
                updateProductDisplay();
            }
        });

        document.querySelector('.next-button').addEventListener('click', () => {
            if (currentIndex < products.length - 1) {
                currentIndex++;
                updateProductDisplay();
            }
        });

        // Initialize with the first product
        updateProductDisplay();
    });
    // Confirmation Popup JavaScript
document.addEventListener('DOMContentLoaded', () => {
    const exchangeButtons = document.querySelectorAll('.exchange-button');
    const confirmationPopup = document.getElementById('confirmationPopup');
    const productNameField = document.getElementById('productName');
    const productPriceField = document.getElementById('productPrice');
    const currentBalanceField = document.getElementById('currentBalance');
    const purchaseDateField = document.getElementById('purchaseDate');
    const completePurchaseButton = document.getElementById('completePurchase');

    exchangeButtons.forEach(button => {
        button.addEventListener('click', (event) => {
            event.preventDefault();
            
            const productContainer = button.closest('.product-container');
            const productPrice = parseFloat(productContainer.querySelector('.product-price').textContent.replace('$', '')) || 0;
            const productName = productContainer.querySelector('.product-title').textContent;
            let points = parseFloat(localStorage.getItem('points')) || 0;

            // Check if the user has enough points
            if (points >= productPrice) {
                // Show the confirmation popup
                confirmationPopup.style.display = 'flex';

                // Set the fields in the popup
                productNameField.value = productName;
                productPriceField.value = `$${productPrice.toFixed(3)}`;
                currentBalanceField.value = `$${points.toFixed(3)} POINTS`;

                const currentDateTime = new Date().toLocaleString();
                purchaseDateField.value = currentDateTime;

                completePurchaseButton.addEventListener('click', () => {
                    const userName = document.getElementById('userName').value;
                    const userAddress = document.getElementById('userAddress').value;

                    const mailtoLink = `mailto:cashmarco2000@gmail.com?subject=Purchase Confirmation&body=Product Name: ${productName}%0D%0AProduct Price: $${productPrice.toFixed(3)}%0D%0AUser Balance: $${points.toFixed(3)}%0D%0APurchase Date and Time: ${currentDateTime}%0D%0AUser Name: ${userName || 'N/A'}%0D%0AUser Address: ${userAddress || 'N/A'}`;
                    
                    window.location.href = mailtoLink;

                    confirmationPopup.style.display = 'none';
                });
            } else {
                alert('You do not have enough points to exchange for this product.');
            }
        });
    });
});
document.addEventListener('DOMContentLoaded', () => {
    const sidebar = document.getElementById('sidebar');

    // Function to toggle the sidebar
    function toggleSidebar() {
        sidebar.classList.toggle('show');
    }

    // Close sidebar when clicking the close button
    document.querySelector('.close-sidebar').addEventListener('click', toggleSidebar);

    // Open sidebar when clicking the profile icon
    document.querySelector('.profile-icon').addEventListener('click', toggleSidebar);
});
// Redirect to email client
    function contactUs() {
        window.location.href = 'mailto:cashmarco@gmail.com';
    }
    document.addEventListener('DOMContentLoaded', () => {
        const headerText = document.getElementById('headerText');
        const messages = [
            'Use code 123',
            'Use code cash100',
            'Use code cashblox360'
            // Add more messages here as needed
        ];

        let messageIndex = 0;

        function changeHeaderText() {
            headerText.textContent = messages[messageIndex];
            messageIndex = (messageIndex + 1) % messages.length;
        }

        setInterval(changeHeaderText, 3000); // Change text every second
    });
</script>
</body>
</html>
