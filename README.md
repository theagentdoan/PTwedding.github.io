<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Our Wedding</title>
    <style>
        body {
            font-family: 'Georgia', serif;
            text-align: center;
            padding: 20px;
            background: linear-gradient(to bottom, #ffecd2, #fcb69f);
            color: #5a3e36;
        }
        h1, h2, h3 {
            font-family: 'Dancing Script', cursive;
        }
        #countdown {
            font-size: 28px;
            font-weight: bold;
            background: rgba(255, 255, 255, 0.7);
            padding: 10px;
            border-radius: 10px;
            display: inline-block;
            margin-top: 20px;
        }
        #rsvpForm {
            background: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 10px;
            display: inline-block;
            margin-top: 20px;
        }
        input, button {
            margin: 10px;
            padding: 10px;
            font-size: 16px;
            border-radius: 5px;
        }
        button {
            background: #d46a6a;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background: #b85757;
        }
        #rsvpMessage {
            margin-top: 20px;
            font-weight: bold;
            font-size: 18px;
        }
    </style>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&display=swap" rel="stylesheet">
</head>
<body>
    <h1>Welcome to Our Wedding Website</h1>
    <h2>Save the Date!</h2>
    <h3>Thành Phú & Ngọc Tuyền</h3>
    <h2>Countdown to Our Big Day</h2>
    <div id="countdown"></div>
    <h2>RSVP</h2>
    <form id="rsvpForm">
        <label for="name">Your Name:</label>
        <input type="text" id="name" required>
        <br>
        <label>
            <input type="checkbox" id="attending"> I will be attending
        </label>
        <br>
        <button type="submit">Submit RSVP</button>
    </form>
    <div id="rsvpMessage"></div>
    <script>
        // Wedding Countdown Timer
        function startCountdown() {
            const weddingDate = new Date('2025-06-15T00:00:00').getTime();
            const countdownElement = document.getElementById('countdown');

            function updateCountdown() {
                const now = new Date().getTime();
                const timeLeft = weddingDate - now;
                
                if (timeLeft < 0) {
                    countdownElement.innerHTML = 'The wedding day is here!';
                    return;
                }
                
                const days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
                const hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
                const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);
                
                countdownElement.innerHTML = `${days}d ${hours}h ${minutes}m ${seconds}s`;
            }
            
            setInterval(updateCountdown, 1000);
            updateCountdown();
        }

        document.addEventListener('DOMContentLoaded', startCountdown);

        // RSVP Form Submission
        function handleRSVP(event) {
            event.preventDefault();
            const name = document.getElementById('name').value;
            const attending = document.getElementById('attending').checked;
            const message = attending ? `Thank you for RSVPing, ${name}! We can't wait to see you!` : `Sorry to hear you can't make it, ${name}.`;
            document.getElementById('rsvpMessage').innerText = message;
        }

        document.addEventListener('DOMContentLoaded', function() {
            document.getElementById('rsvpForm').addEventListener('submit', handleRSVP);
        });
    </script>
</body>
</html>
