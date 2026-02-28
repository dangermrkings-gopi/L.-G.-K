<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Book a Meeting | Appointment System</title>
    <style>
        /* --- CSS: Beautiful Styling & Animations --- */
        :root {
            --primary: #6366f1;
            --secondary: #a855f7;
            --bg: #0f172a;
            --text: #f8fafc;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--bg);
            color: var(--text);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            overflow-x: hidden;
        }

        /* Animated Background Gradient */
        .container {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            padding: 2.5rem;
            border-radius: 20px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
            width: 100%;
            max-width: 400px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            animation: fadeIn 1s ease-out;
        }

        /* Text Animation */
        h2 {
            text-align: center;
            font-size: 2rem;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 1.5rem;
            animation: slideDown 0.8s ease-out;
        }

        .input-group {
            margin-bottom: 1.2rem;
            animation: fadeInUp 0.5s ease-out forwards;
            opacity: 0;
        }

        label { display: block; margin-bottom: 5px; font-size: 0.9rem; color: #94a3b8; }

        input, select {
            width: 100%;
            padding: 12px;
            background: rgba(15, 23, 42, 0.8);
            border: 1px solid #334155;
            border-radius: 8px;
            color: white;
            box-sizing: border-box;
            transition: all 0.3s ease;
        }

        input:focus { border-color: var(--primary); outline: none; box-shadow: 0 0 10px rgba(99, 102, 241, 0.3); }

        button {
            width: 100%;
            padding: 12px;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            border: none;
            border-radius: 8px;
            color: white;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
            margin-top: 10px;
        }

        button:hover { transform: translateY(-2px); box-shadow: 0 10px 15px -3px rgba(99, 102, 241, 0.4); }

        /* Status Message */
        #status { text-align: center; margin-top: 1rem; font-size: 0.9rem; display: none; }

        /* Keyframes */
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes slideDown { from { transform: translateY(-30px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }
        @keyframes fadeInUp { from { transform: translateY(20px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }

        /* Delay for items */
        .input-group:nth-child(2) { animation-delay: 0.2s; }
        .input-group:nth-child(3) { animation-delay: 0.4s; }
        .input-group:nth-child(4) { animation-delay: 0.6s; }
    </style>
</head>
<body>

    <div class="container">
        <h2>Schedule Meeting</h2>
        
        <form id="appointmentForm">
            <div class="input-group">
                <label>Full Name</label>
                <input type="text" id="userName" placeholder="Enter your name" required>
            </div>

            <div class="input-group">
                <label>Select Date</label>
                <input type="date" id="appDate" required>
            </div>

            <div class="input-group">
                <label>Meeting Type</label>
                <select id="meetType">
                    <option value="Consultation">Consultation</option>
                    <option value="Project Update">Project Update</option>
                    <option value="General">General Inquiry</option>
                </select>
            </div>

            <button type="submit" id="submitBtn">Book Appointment</button>
        </form>

        <div id="status"></div>
    </div>

    <script>
        // --- JAVASCRIPT: Logic (The "Backend" Simulation) ---
        const form = document.getElementById('appointmentForm');
        const status = document.getElementById('status');

        form.addEventListener('submit', function(e) {
            e.preventDefault();
            
            // 1. Capture Data (Frontend)
            const data = {
                name: document.getElementById('userName').value,
                date: document.getElementById('appDate').value,
                type: document.getElementById('meetType').value
            };

            // 2. Simulate Backend Processing (Logic)
            const btn = document.getElementById('submitBtn');
            btn.innerText = "Processing...";
            btn.disabled = true;

            setTimeout(() => {
                // Logic: Success response
                status.style.display = "block";
                status.style.color = "#4ade80";
                status.innerText = `Success! Appointment booked for ${data.name} on ${data.date}.`;
                
                // Clear Form
                form.reset();
                btn.innerText = "Book Appointment";
                btn.disabled = false;

                // Log "Backend" data to console
                console.log("Data saved to database:", data);
            }, 1500);
        });
    </script>
</body>
</html>
