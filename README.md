# Vaayu-putra
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Drone Motor Selection</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Drone Motor Selection Guide</h1>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#process">Motor Selection Process</a></li>
                <li><a href="#carbon-fiber">Carbon Fiber Details</a></li>
                <li><a href="#simulation">Simulation Video</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <section id="home">
            <h2>Welcome</h2>
            <p>Learn how to select the right motor for your carbon fiber drone.</p>
        </section>
        <section id="process">
            <h2>Motor Selection Process</h2>
            <p>Use the form below to calculate the required kv rating based on your drone's weight and power requirements.</p>
            <form id="motor-form">
                <label for="weight">Drone Weight (grams):</label>
                <input type="number" id="weight" required>
                
                <label for="voltage">Battery Voltage (V):</label>
                <input type="number" id="voltage" required>
                
                <label for="thrust">Desired Thrust (grams):</label>
                <input type="number" id="thrust" required>
                
                <button type="submit">Calculate kv Rating</button>
            </form>
            <div id="result"></div>
        </section>
        <section id="carbon-fiber">
            <h2>Carbon Fiber Details</h2>
            <p>Carbon fiber is known for its high strength-to-weight ratio. For calculations, the density of carbon fiber is approximately 1.6 g/cm³.</p>
        </section>
        <section id="simulation">
            <h2>Simulation Video</h2>
            <video controls>
                <source src="simulation.mp4" type="video/mp4">
                Your browser does not support the video tag.
            </video>
        </section>
        <section id="contact">
            <h2>Contact Us</h2>
            <form id="contact-form">
                <label for="name">Name:</label>
                <input type="text" id="name" required>
                
                <label for="email">Email:</label>
                <input type="email" id="email" required>
                
                <label for="message">Message:</label>
                <textarea id="message" required></textarea>
                
                <button type="submit">Send</button>
            </form>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 Drone Motor Selection</p>
    </footer>
    <script src="scripts.js"></script>
</body>
</html>


body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

header {
    background-color: #333;
    color: white;
    padding: 10px 0;
    text-align: center;
}

nav ul {
    list-style: none;
    margin: 0;
    padding: 0;
}

nav ul li {
    display: inline;
    margin-right: 15px;
}

nav ul li a {
    color: white;
    text-decoration: none;
}

main {
    padding: 20px;
}

section {
    margin-bottom: 20px;
}

h2 {
    border-bottom: 2px solid #333;
    padding-bottom: 5px;
}

form {
    display: flex;
    flex-direction: column;
}

label {
    margin: 5px 0;
}

input, textarea {
    padding: 8px;
    margin-bottom: 10px;
}

button {
    padding: 10px;
    background-color: #333;
    color: white;
    border: none;
    cursor: pointer;
}

button:hover {
    background-color: #555;
}

video {
    max-width: 100%;
    height: auto;
}

footer {
    background-color: #333;
    color: white;
    text-align: center;
    padding: 10px 0;
}

document.getElementById('motor-form').addEventListener('submit', function(e) {
    e.preventDefault();
    
    // Get values from form
    const weight = parseFloat(document.getElementById('weight').value);
    const voltage = parseFloat(document.getElementById('voltage').value);
    const thrust = parseFloat(document.getElementById('thrust').value);

    // Calculate required kv rating
    if (weight > 0 && voltage > 0 && thrust > 0) {
        const requiredThrust = thrust; // in grams
        const power = requiredThrust * 9.81 / 1000; // Convert grams to kg and multiply by g (9.81 m/s^2)
        const kvRating = power / (voltage * 0.1); // Example calculation (simplified)
        
        // Display result
        document.getElementById('result').innerHTML = `<p>Estimated kv Rating: ${kvRating.toFixed(2)} RPM/V</p>`;
    } else {
        document.getElementById('result').innerHTML = `<p>Please enter valid numbers.</p>`;
    }
});
