
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Global Click Counter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        #clickButton {
            background-color: red;
            color: white;
            border: none;
            padding: 20px 40px;
            font-size: 24px;
            cursor: pointer;
            border-radius: 10px;
        }
        #clickButton:active {
            background-color: darkred;
        }
        #counters {
            margin-top: 20px;
            text-align: center;
        }
        .counter {
            font-size: 20px;
            margin: 10px;
        }
    </style>
</head>
<body>
    <button id="clickButton">Click Me!</button>
    <div id="counters">
        <div class="counter">Total Clicks: <span id="totalClicks">0</span></div>
        <div class="counter">Your Clicks: <span id="yourClicks">0</span></div>
    </div>

    <script>
        // Set initial values for counters
        let yourClicks = 0;
        let totalClicks = 0;

        // Load the total clicks from a backend API (simulated here with localStorage)
        if (localStorage.getItem('totalClicks')) {
            totalClicks = parseInt(localStorage.getItem('totalClicks'));
            document.getElementById('totalClicks').innerText = totalClicks;
        }

        // Add click event listener to the button
        document.getElementById('clickButton').addEventListener('click', () => {
            // Increment user's click count
            yourClicks++;
            document.getElementById('yourClicks').innerText = yourClicks;

            // Increment total click count
            totalClicks++;
            document.getElementById('totalClicks').innerText = totalClicks;

            // Save the total clicks count (in real-world use, you would save this to a backend)
            localStorage.setItem('totalClicks', totalClicks);
        });
    </script>
</body>
</html>
