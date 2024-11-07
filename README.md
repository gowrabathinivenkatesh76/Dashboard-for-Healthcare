<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Healthcare Management App</title>
    <style>
        /* Global Styles */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        header {
            background-color: #4CAF50;
            color: white;
            padding: 1em;
            text-align: center;
        }

        nav ul {
            list-style-type: none;
            padding: 0;
        }

        nav ul li {
            display: inline;
            margin: 0 15px;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
            font-weight: bold;
        }

        main {
            padding: 2em;
        }

        h2 {
            color: #4CAF50;
        }

        /* Form and Input Styles */
        form {
            background-color: #f4f4f4;
            padding: 1.5em;
            margin-top: 1em;
            border-radius: 8px;
        }

        input,
        button {
            width: 100%;
            padding: 0.8em;
            margin-bottom: 1em;
            font-size: 1rem;
            border-radius: 4px;
            border: 1px solid #ccc;
        }

        button {
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
        }

        button:hover {
            background-color: #45a049;
        }

        /* List Styles */
        ul,
        #condition-list {
            padding-left: 1.5em;
        }

        ul li {
            list-style-type: disc;
        }

        /* Accessibility considerations */
        a:focus,
        button:focus,
        input:focus {
            outline: 3px solid #0056b3;
        }

        footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 1em;
            position: fixed;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>

<body>
    <header>
        <h1>Healthcare Management</h1>
        <nav>
            <ul>
                <li><a href="#dashboard">Dashboard</a></li>
                <li><a href="#medications">Medications</a></li>
                <li><a href="#conditions">Conditions</a></li>
                <li><a href="#messages">Messages</a></li>
                <li><a href="#profile">Profile</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section id="dashboard">
            <h2>Welcome, User</h2>
            <p>Here you can track your health conditions, medications, and communicate with your healthcare providers.</p>
        </section>

        <section id="medications">
            <h2>Medication Tracker</h2>
            <form id="medication-form">
                <label for="medication-name">Medication Name</label>
                <input type="text" id="medication-name" placeholder="Enter Medication Name" required>
                <label for="dose">Dose</label>
                <input type="text" id="dose" placeholder="Enter Dose" required>
                <label for="time">Time to Take</label>
                <input type="time" id="time" required>
                <button type="submit">Add Medication</button>
            </form>
            <h3>Your Medications:</h3>
            <ul id="medication-list"></ul>
        </section>

        <section id="conditions">
            <h2>Your Health Conditions</h2>
            <div id="condition-list">
                <button id="add-condition">Add Condition</button>
                <!-- Dynamically generated list of conditions -->
            </div>
        </section>

        <section id="messages">
            <h2>Messages with Healthcare Providers</h2>
            <div id="messages-list">
                <button id="new-message">New Message</button>
                <!-- Dynamically generated messages -->
            </div>
        </section>

        <section id="profile">
            <h2>Profile Settings</h2>
            <form id="profile-form">
                <label for="name">Full Name</label>
                <input type="text" id="name" placeholder="Enter your name">
                <label for="dob">Date of Birth</label>
                <input type="date" id="dob">
                <button type="submit">Save Changes</button>
            </form>
        </section>
    </main>

    <footer>
        <p>&copy; 2024 Healthcare Management. All Rights Reserved.</p>
    </footer>

    <script>
        // Medication Tracker Functionality
        document.getElementById('medication-form').addEventListener('submit', function (event) {
            event.preventDefault();

            const medicationName = document.getElementById('medication-name').value;
            const dose = document.getElementById('dose').value;
            const time = document.getElementById('time').value;

            if (medicationName && dose && time) {
                const medicationItem = document.createElement('li');
                medicationItem.textContent = `${medicationName} - ${dose} at ${time}`;
                document.getElementById('medication-list').appendChild(medicationItem);
            }

            // Clear the form inputs
            document.getElementById('medication-form').reset();
        });

        // Condition Management
        document.getElementById('add-condition').addEventListener('click', function () {
            const newCondition = prompt("Enter your health condition:");
            if (newCondition) {
                const conditionItem = document.createElement('p');
                conditionItem.textContent = newCondition;
                document.getElementById('condition-list').appendChild(conditionItem);
            }
        });

        // Profile Form Submission
        document.getElementById('profile-form').addEventListener('submit', function (event) {
            event.preventDefault();

            const name = document.getElementById('name').value;
            const dob = document.getElementById('dob').value;

            if (name && dob) {
                alert('Profile updated successfully');
            }
        });
    </script>
</body>

</html>
