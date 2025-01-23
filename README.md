<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Financial System - Investment Platform</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
        }
        .container {
            max-width: 800px;
            margin: 20px auto;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1, h2 {
            text-align: center;
            color: #333;
        }
        .section {
            margin-bottom: 30px;
        }
        .balance {
            font-size: 24px;
            color: green;
            text-align: center;
        }
        .form-group {
            margin-bottom: 15px;
        }
        .form-group label {
            display: block;
            font-weight: bold;
        }
        .form-group input, .form-group select {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        .btn {
            display: inline-block;
            padding: 10px 20px;
            color: #fff;
            background-color: #007bff;
            border: none;
            border-radius: 4px;
            text-align: center;
            cursor: pointer;
        }
        .btn:hover {
            background-color: #0056b3;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }
        table, th, td {
            border: 1px solid #ddd;
        }
        th, td {
            padding: 10px;
            text-align: center;
        }
        .logo {
            text-align: center;
            margin-bottom: 20px;
        }
        .logo img {
            width: 150px;
        }
    </style>
    <script>
        let balance = 999520; // Initial balance in euros

        // Update balance daily with 2% interest
        function calculateDailyInterest() {
            const dailyInterest = balance * 0.02;
            balance += dailyInterest;
            document.getElementById('balance').innerText = `Balance: €${balance.toFixed(2)}`;
        }

        // Convert currency
        function convertCurrency() {
            const amount = parseFloat(document.getElementById('amount').value);
            const currency = document.getElementById('currency').value;
            let rate = 1;

            // Example rates (replace with API integration for real-time rates)
            if (currency === 'USD') rate = 1.1;
            else if (currency === 'JPY') rate = 140;
            else if (currency === 'GBP') rate = 0.85;

            const converted = amount * rate;
            document.getElementById('conversionResult').innerText = `Converted Amount: ${converted.toFixed(2)} ${currency}`;
        }

        // Simulate adding investment funds
        function addFunds() {
            const investment = parseFloat(document.getElementById('investmentAmount').value);
            if (investment > 0) {
                balance += investment;
                document.getElementById('balance').innerText = `Balance: €${balance.toFixed(2)}`;
                alert('Investment added successfully!');
            } else {
                alert('Please enter a valid investment amount.');
            }
        }

        // Simulate withdrawal functionality
        function withdrawFunds(method) {
            const amount = parseFloat(prompt("Enter amount to withdraw (€):"));
            if (amount > 0 && amount <= balance) {
                balance -= amount;
                document.getElementById('balance').innerText = `Balance: €${balance.toFixed(2)}`;
                alert(`Withdrawal of €${amount} via ${method} successful!`);
            } else {
                alert('Invalid withdrawal amount.');
            }
        }

        // Simulate daily interest calculation every 24 hours (86400000 ms)
        setInterval(calculateDailyInterest, 86400000);
    </script>
</head>
<body>
    <div class="container">
        <div class="logo">
            <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/8a/OpenAI_Logo.svg/1200px-OpenAI_Logo.svg.png" alt="ChatGPT Logo">
        </div>

        <h1>Financial Investment Platform</h1>

        <!-- Account Balance Section -->
        <div class="section">
            <h2>Account Balance</h2>
            <p class="balance" id="balance">Balance: €999,520.00</p>
        </div>

        <!-- Add Funds Section -->
        <div class="section">
            <h2>Add Investment Funds</h2>
            <div class="form-group">
                <label for="investmentAmount">Amount to Invest (€):</label>
                <input type="number" id="investmentAmount" placeholder="Enter amount">
            </div>
            <button class="btn" onclick="addFunds()">Add Funds</button>
        </div>

        <!-- Currency Conversion Section -->
        <div class="section">
            <h2>Currency Conversion</h2>
            <div class="form-group">
                <label for="amount">Amount (€):</label>
                <input type="number" id="amount" placeholder="Enter amount">
            </div>
            <div class="form-group">
                <label for="currency">Convert to:</label>
                <select id="currency">
                    <option value="USD">USD</option>
                    <option value="JPY">JPY</option>
                    <option value="GBP">GBP</option>
                </select>
            </div>
            <button class="btn" onclick="convertCurrency()">Convert</button>
            <p id="conversionResult"></p>
        </div>

        <!-- Withdrawal Options Section -->
        <div class="section">
            <h2>Withdraw Funds</h2>
            <button class="btn" onclick="withdrawFunds('PayPal')">Withdraw via PayPal</button>
            <button class="btn" onclick="withdrawFunds('RIB')">Withdraw via RIB</button>
            <button class="btn" onclick="withdrawFunds('Bitcoin')">Withdraw via Bitcoin</button>
        </div>

        <!-- Registration Section -->
        <div class="section">
            <h2>Join and Invest</h2>
            <div class="form-group">
                <label for="email">Email Address:</label>
                <input type="email" id="email" placeholder="Enter your email">
            </div>
            <button class="btn" onclick="alert('Registration successful!')">Register</button>
        </div>

        <!-- Daily Interest Simulation Info -->
        <div class="section">
            <h2>Daily Interest</h2>
            <p>Your balance increases by 2% daily automatically.</p>
        </div>
    </div>
</body>
</html>
