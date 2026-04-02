<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Health & Nutrition Recommendation System</title>

    <script
      type="text/javascript"
      src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"
    ></script>
    <script type="text/javascript">
      (function () {
        emailjs.init({
          publicKey: "JxdpHOwUN2MISI3HU",
        });
      })();
    </script>

    <style>
      :root {
        --primary-color: #2e7d32;
        --secondary-color: #e8f5e9;
        --text-color: #333;
        --bg-color: #f4f7f6;
      }

      html {
        scroll-behavior: smooth;
      }

      body {
        font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
        margin: 0;
        background-color: var(--bg-color);
        color: var(--text-color);
        line-height: 1.6;
      }

      header {
        background: linear-gradient(135deg, #1b5e20, #4caf50);
        color: white;
        padding: 40px 20px;
        text-align: center;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      }

      header h1 {
        margin: 0 0 10px 0;
        font-size: 2.5em;
      }

      nav {
        background-color: #222;
        position: sticky;
        top: 0;
        z-index: 1000;
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        padding: 15px;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
      }

      nav a {
        color: white;
        margin: 0 15px;
        text-decoration: none;
        font-weight: 600;
        transition: color 0.3s;
      }

      nav a:hover {
        color: #81c784;
      }

      .container {
        max-width: 1000px;
        margin: 0 auto;
        padding: 20px;
      }

      .card {
        background: white;
        padding: 30px;
        margin-bottom: 30px;
        border-radius: 12px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
        transition: transform 0.3s;
      }

      .card:hover {
        transform: translateY(-5px);
      }

      h2 {
        color: var(--primary-color);
        border-bottom: 2px solid var(--secondary-color);
        padding-bottom: 10px;
        margin-top: 0;
      }

      .form-group {
        margin-bottom: 15px;
      }
      .form-group label {
        display: block;
        font-weight: bold;
        margin-bottom: 5px;
      }
      .form-group input,
      .form-group select {
        width: 100%;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 6px;
        box-sizing: border-box;
        font-size: 16px;
      }

      button {
        background-color: var(--primary-color);
        color: white;
        padding: 12px 20px;
        border: none;
        border-radius: 6px;
        cursor: pointer;
        font-size: 16px;
        font-weight: bold;
        width: 100%;
        transition: background-color 0.3s;
      }

      button:hover {
        background-color: #1b5e20;
      }

      button:disabled {
        background-color: #9e9e9e;
        cursor: not-allowed;
      }

      #bmi-result,
      #session-result,
      #bill-result {
        margin-top: 20px;
        display: none;
      }

      .booking-ticket {
        background-color: var(--secondary-color);
        border: 2px dashed var(--primary-color);
        border-radius: 8px;
        padding: 20px;
        text-align: left;
        color: var(--text-color);
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
        position: relative;
      }

      .ticket-header {
        text-align: center;
        border-bottom: 1px dashed #ccc;
        padding-bottom: 15px;
        margin-bottom: 15px;
      }

      .ticket-header h3 {
        margin: 0 0 5px 0;
        color: var(--primary-color);
        font-size: 1.5em;
      }

      .ticket-detail {
        margin-bottom: 10px;
        font-size: 16px;
        display: flex;
        justify-content: space-between;
        border-bottom: 1px solid #c8e6c9;
        padding-bottom: 5px;
      }

      .ticket-detail:last-child {
        border-bottom: none;
      }

      .ticket-detail span {
        font-weight: bold;
        color: var(--primary-color);
      }

      .ticket-footer {
        text-align: center;
        margin-top: 15px;
        font-style: italic;
        color: #555;
        font-size: 0.9em;
      }

      .gallery-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 20px;
      }

      .gallery-grid div {
        background: #eee;
        height: 200px;
        border-radius: 8px;
        display: flex;
        align-items: center;
        justify-content: center;
        color: #777;
        font-style: italic;
        overflow: hidden;
      }

      .gallery-grid img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: transform 0.3s;
      }

      .gallery-grid img:hover {
        transform: scale(1.1);
      }

      footer {
        background-color: #222;
        color: #bbb;
        text-align: center;
        padding: 20px;
        margin-top: 40px;
      }
    </style>
  </head>

  <body>
    <header>
      <h1>Health & Nutrition Recommendation System</h1>
      <p>Your Personal AI Companion for Health Well-Being</p>
    </header>

    <nav>
      <a href="#introduction">Introduction</a>
      <a href="#about">About</a>
      <a href="#features">Features</a>
      <a href="#bmi-calculator">BMI Calculator</a>
      <a href="#bill-calculator">Bill Estimator</a>
      <a href="#book-session">Book a Session</a>
      <a href="#gallery">Gallery</a>
      <a href="#contact">Contact</a>
    </nav>

    <div class="container">
      <section id="introduction">
        <div class="card">
          <h2>Introduction</h2>
          <p>
            Hello Everybody, we are all members of Capstone Project, Group No.
            165, our names are <strong>Sahil Sharma</strong>,
            <strong>Shalini Sharma</strong>, <strong>Lakshay Sharma</strong>,
            <strong>Krish Sharma</strong>, and <strong>Srishty Sharma</strong>.
            We are pursuing <strong>Bachelor of Science</strong> in
            <strong>Computer Science & Data Analytics</strong> from IIT Patna.
            Welcome to our first website! This project represents our initial
            steps into combining web development with health-focused technology.
            We hope you enjoy exploring it. 😊😊
          </p>
        </div>
      </section>

      <section id="about">
        <div class="card">
          <h2>About the System</h2>
          <p>
            The Health & Nutrition system is designed to help address the modern
            obesity epidemic using accessible technology. Nutrition is the study
            of how food affects the body, serving as a pillar of health, growth,
            and disease prevention.
          </p>
          <p>
            A balanced diet rich in fruits, vegetables, lean proteins, and whole
            grains provides essential macronutrients (Energy) and micronutrients
            (vitamins/minerals) to reduce risks of chronic illnesses like
            diabetes and heart disease.
          </p>
        </div>
      </section>

      <section id="features">
        <div class="card">
          <h2>Key Features</h2>
          <ul>
            <li>
              <strong>Obesity Detection:</strong> Mathematical assessment using
              standard health metrics.
            </li>
            <li>
              <strong>BMI Calculator:</strong> Instant feedback on your current
              body mass index.
            </li>
            <li>
              <strong>Self-Balancing Diet Plans:</strong> Guidelines for
              maintaining caloric equilibrium.
            </li>
            <li>
              <strong>Smart Routine Making:</strong> Structural advice for daily
              health habits.
            </li>
          </ul>
        </div>
      </section>

      <section id="bmi-calculator">
        <div class="card">
          <h2>Interactive BMI Calculator</h2>
          <p>
            Enter your details below to calculate your Body Mass Index (BMI).
          </p>

          <div class="form-group">
            <label for="name">Name:</label>
            <input type="text" id="name" placeholder="Enter your name" />
          </div>
          <div class="form-group">
            <label for="age">Age:</label>
            <input type="number" id="age" placeholder="Enter your age" />
          </div>
          <div class="form-group">
            <label for="height">Height (in cm):</label>
            <input type="number" id="height" placeholder="e.g., 175" />
          </div>
          <div class="form-group">
            <label for="weight">Weight (in kg):</label>
            <input type="number" id="weight" placeholder="e.g., 70" />
          </div>

          <button onclick="calculateBMI()">Calculate My BMI</button>

          <div
            id="bmi-result"
            style="
              padding: 15px;
              border-radius: 6px;
              text-align: center;
              font-weight: bold;
              font-size: 1.2em;
            "
          ></div>
        </div>
      </section>

      <section id="bill-calculator">
        <div class="card">
          <h2>Consultation Bill Estimator</h2>
          <p>Estimate the cost of your selected health packages.</p>

          <div class="form-group">
            <label for="diet-plan-qty"
              >Diet Planning Sessions (₹799 each):</label
            >
            <input
              type="number"
              id="diet-plan-qty"
              placeholder="e.g., 1"
              min="0"
            />
          </div>
          <div class="form-group">
            <label for="workout-plan-qty"
              >Workout Routine Sessions (₹1499 each):</label
            >
            <input
              type="number"
              id="workout-plan-qty"
              placeholder="e.g., 2"
              min="0"
            />
          </div>

          <button onclick="calculateBill()">Calculate Total Bill</button>

          <div
            id="bill-result"
            style="
              padding: 15px;
              border-radius: 6px;
              text-align: center;
              font-weight: bold;
              font-size: 1.2em;
            "
          ></div>
        </div>
      </section>
      <section id="book-session">
        <div class="card">
          <h2>Book a Consultation Session</h2>
          <p>
            Ready to take the next step? Book a personalized session with a
            health expert to discuss your diet and routine.
          </p>

          <div class="form-group">
            <label for="session-name">Full Name:</label>
            <input
              type="text"
              id="session-name"
              placeholder="Enter your name"
            />
          </div>
          <div class="form-group">
            <label for="session-type">Session Type:</label>
            <select id="session-type">
              <option value="" disabled selected>Select a goal...</option>
              <option value="Diet Planning">Diet Planning & Nutrition</option>
              <option value="Workout Routine Making">
                Workout Routine Making
              </option>
              <option value="Weight Loss Consultation">
                Weight Loss Consultation
              </option>
              <option value="General Health Checkup">
                General Health Checkup
              </option>
            </select>
          </div>
          <div class="form-group">
            <label for="session-date">Preferred Date:</label>
            <input type="date" id="session-date" />
          </div>
          <div class="form-group">
            <label for="session-time">Preferred Time:</label>
            <input type="time" id="session-time" />
          </div>

          <button id="submitBookingBtn" onclick="bookSession()">
            Confirm Appointment
          </button>

          <div id="session-result"></div>
        </div>
      </section>

      <section id="gallery">
        <div class="card">
          <h2>Gallery</h2>
          <p>Examples of healthy routines and balanced diets.</p>
          <div class="gallery-grid">
            <div>
              <a href="https://www.healthyfood.com/" target="_blank">
                <img
                  src="https://images.unsplash.com/photo-1490645935967-10de6ba17061?auto=format&fit=crop&w=500&q=60"
                  alt="Healthy Food"
                />
              </a>
            </div>

            <div>
              <a href="https://myyogateacher.com/" target="_blank">
                <img
                  src="https://images.unsplash.com/photo-1571019614242-c5c5dee9f50b?auto=format&fit=crop&w=500&q=60"
                  alt="Exercise"
                />
              </a>
            </div>

            <div>
              <a
                href="https://www.pexels.com/search/junk%20food/"
                target="_blank"
              >
                <img
                  src="https://images.unsplash.com/photo-1505252585461-04db1eb84625?auto=format&fit=crop&w=500&q=60"
                  alt="Nutrition"
                />
              </a>
            </div>
          </div>
        </div>
      </section>

      <section id="contact">
        <div class="card">
          <h2>Contact Me</h2>
          <p><strong>Name:</strong> Sahil Sharma</p>
          <p>
            <strong>Email:</strong>
            <a href="mailto:mr.jerry1925@gmail.com">mr.jerry1925@gmail.com</a>
          </p>

          <p><strong>Phone:</strong> +91 8389024961</p>
          <p>
            <strong>Address:</strong> Kankarbagh, Patna, Bihar. India - 800002
          </p>
          <br />
          <button
            onclick="
              alert(
                'Thank you for getting in touch, Sahil will contact you soon!',
              )
            "
          >
            Send a Message
          </button>
        </div>
      </section>
    </div>

    <footer>
      <p>
        © 2026 Health & Nutrition Recommendation System. Designed by Group 165.
      </p>
    </footer>

    <script>
      function calculateBMI() {
        let name = document.getElementById("name").value;
        let heightCm = document.getElementById("height").value;
        let weightKg = document.getElementById("weight").value;
        let resultDiv = document.getElementById("bmi-result");

        if (
          heightCm === "" ||
          weightKg === "" ||
          heightCm <= 0 ||
          weightKg <= 0
        ) {
          resultDiv.style.display = "block";
          resultDiv.style.backgroundColor = "#ffebee";
          resultDiv.style.color = "#c62828";
          resultDiv.innerHTML = "Please enter valid height and weight values.";
          return;
        }

        let heightM = heightCm / 100;
        let bmi = (weightKg / (heightM * heightM)).toFixed(1);

        let category = "";
        let bgColor = "";
        let textColor = "#fff";

        if (bmi < 18.5) {
          category = "Underweight";
          bgColor = "#ffb74d";
        } else if (bmi >= 18.5 && bmi <= 24.9) {
          category = "Normal weight";
          bgColor = "#4caf50";
        } else if (bmi >= 25 && bmi <= 29.9) {
          category = "Overweight";
          bgColor = "#ff9800";
        } else {
          category = "Obese";
          bgColor = "#f44336";
        }

        let greeting = name ? `Hi ${name}, ` : "";
        resultDiv.style.display = "block";
        resultDiv.style.backgroundColor = bgColor;
        resultDiv.style.color = textColor;
        resultDiv.innerHTML = `${greeting}Your BMI is <strong>${bmi}</strong>. This is considered: <strong>${category}</strong>.`;
      }

      // NEW FIXED BILL ESTIMATOR LOGIC
      function calculateBill() {
        let dietQty =
          parseInt(document.getElementById("diet-plan-qty").value) || 0;
        let workoutQty =
          parseInt(document.getElementById("workout-plan-qty").value) || 0;
        let resultDiv = document.getElementById("bill-result");

        if (dietQty <= 0 && workoutQty <= 0) {
          resultDiv.style.display = "block";
          resultDiv.style.backgroundColor = "#ffebee";
          resultDiv.style.color = "#c62828";
          resultDiv.innerHTML = "Please enter at least 1 session to calculate.";
          return;
        }

        // Calculate Subtotal using the correct variables
        let subtotal = dietQty * 799 + workoutQty * 1499;

        // Calculate 28% GST
        let gst = subtotal * 0.28;

        // Calculate Grand Total
        let grandTotal = subtotal + gst;

        resultDiv.style.display = "block";
        resultDiv.style.backgroundColor = "#e8f5e9";
        resultDiv.style.color = "#2e7d32";

        // Outputting the Subtotal, GST, and Grand Total with the Rupee (₹) symbol
        resultDiv.innerHTML = `
          <div style="text-align: left; max-width: 250px; margin: 0 auto;">
            <p style="margin: 5px 0; display: flex; justify-content: space-between;">
              <span>Subtotal:</span> <span>₹${subtotal.toFixed(2)}</span>
            </p>
            <p style="margin: 5px 0; display: flex; justify-content: space-between;">
              <span>GST (28%):</span> <span>₹${gst.toFixed(2)}</span>
            </p>
            <hr style="border: 0.5px solid #2e7d32;">
            <p style="margin: 5px 0; display: flex; justify-content: space-between; font-size: 1.2em;">
              <strong>Grand Total:</strong> <strong>₹${grandTotal.toFixed(2)}</strong>
            </p>
          </div>
        `;
      }
      // END BILL ESTIMATOR LOGIC

      function bookSession() {
        let name = document.getElementById("session-name").value;
        let type = document.getElementById("session-type").value;
        let date = document.getElementById("session-date").value;
        let time = document.getElementById("session-time").value;
        let resultDiv = document.getElementById("session-result");
        let btn = document.getElementById("submitBookingBtn");

        if (name === "" || type === "" || date === "" || time === "") {
          resultDiv.style.display = "block";
          resultDiv.innerHTML = `
            <div style="background-color: #ffebee; color: #c62828; padding: 15px; border-radius: 6px; text-align: center; font-weight: bold;">
              ⚠️ Please fill in all the details to book your session.
            </div>`;
          return;
        }

        let sessionId = "HLTH-" + Math.floor(Math.random() * 10000) + 90000;

        btn.innerText = "Sending Booking...";
        btn.disabled = true;

        let templateParams = {
          patient_name: name,
          session_type: type,
          session_date: date,
          session_time: time,
          session_id: sessionId,
          to_email: "mr.jerry1925@gmail.com",
        };

        emailjs
          .send("service_ngrycoo", "template_fmuqbeb", templateParams)
          .then(
            function (response) {
              console.log("SUCCESS!", response.status, response.text);

              resultDiv.style.display = "block";
              resultDiv.innerHTML = `
                  <div class="booking-ticket">
                    <div class="ticket-header">
                      <h3>🩺 Session Confirmed & Emailed!</h3>
                      <p style="margin:0;">Appointment ID: <strong>${sessionId}</strong></p>
                    </div>
                    <div class="ticket-body">
                      <div class="ticket-detail"><span>Patient Name:</span> ${name}</div>
                      <div class="ticket-detail"><span>Consultation:</span> ${type}</div>
                      <div class="ticket-detail"><span>Date:</span> ${date}</div>
                      <div class="ticket-detail"><span>Time:</span> ${time}</div>
                    </div>
                    <div class="ticket-footer">
                      Thank you for prioritizing your health! Your details have been sent to our team. 🍏
                    </div>
                  </div>
                `;

              document.getElementById("session-name").value = "";
              document.getElementById("session-type").value = "";
              document.getElementById("session-date").value = "";
              document.getElementById("session-time").value = "";
              btn.innerText = "Confirm Appointment";
              btn.disabled = false;
            },
            function (error) {
              console.log("FAILED...", error);
              alert(
                "Failed to send the booking email. Please check your Console for errors or verify your EmailJS keys.",
              );
              btn.innerText = "Confirm Appointment";
              btn.disabled = false;
            },
          );
      }
    </script>
  </body>
</html>
