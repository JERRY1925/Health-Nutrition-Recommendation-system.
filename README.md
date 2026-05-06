<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Health & Nutrition Recommendation System</title>

    <!-- Font Awesome CDN for Social Media Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

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
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

    <style>
      :root {
        --primary-color: #2e7d32;
        --secondary-color: #e8f5e9;
        --text-color: #333;
        --bg-color: #f4f7f6;
        --card-bg: rgba(255, 255, 255, 0.95);
        --female-color: #e91e63;
        --male-color: #1976d2; /* Added Male Color */
      }

      body.dark-mode {
        --primary-color: #81c784;
        --secondary-color: #1b5e20;
        --text-color: #f1f1f1;
        --bg-color: #121212;
        --card-bg: rgba(30, 30, 30, 0.9);
        --female-color: #f48fb1;
        --male-color: #64b5f6; /* Added Male Color Dark Mode */
      }

      body.dark-mode::before {
        filter: brightness(0.4);
      }

      body.dark-mode .form-group input,
      body.dark-mode .form-group select,
      body.dark-mode .form-group textarea {
        background-color: #333;
        color: #fff;
        border-color: #555;
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
        position: relative;
        min-height: 100vh;
        transition:
          background-color 0.3s,
          color 0.3s;
      }

      body::before {
        content: "";
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        z-index: -1;
        background-image:
          linear-gradient(rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.45)),
          url("https://images.unsplash.com/photo-1534438327276-14e5300c3a48?q=80&w=1000&auto=format&fit=crop"),
          url("https://images.unsplash.com/photo-1490645935967-10de6ba17061?q=80&w=1000&auto=format&fit=crop"),
          url("https://images.unsplash.com/photo-1610440042657-612c34d95e9f?q=80&w=1000&auto=format&fit=crop");
        background-position:
          center center,
          left center,
          top right,
          bottom right;
        background-size:
          cover,
          50% 100%,
          50% 50%,
          50% 50%;
        background-repeat: no-repeat;
        transition: filter 0.3s;
      }

      header {
        background-image:
          linear-gradient(rgba(27, 94, 32, 0.6), rgba(0, 0, 0, 0.8)),
          url("https://images.unsplash.com/photo-1498837167333-2f14ac1f8f4b?q=80&w=2000&auto=format&fit=crop");
        background-size: cover;
        background-position: center;
        color: white;
        padding: 60px 20px;
        text-align: center;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
        border-bottom: 4px solid var(--primary-color);
      }

      header h1 {
        margin: 0 0 10px 0;
        font-size: 2.8em;
        text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.8);
      }

      header p {
        font-size: 1.2em;
        font-weight: 500;
        text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.8);
      }

      nav {
        background-color: rgba(34, 34, 34, 0.95);
        backdrop-filter: blur(5px);
        position: sticky;
        top: 0;
        z-index: 1000;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        padding: 15px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.4);
      }

      nav a {
        color: white;
        margin: 5px 12px;
        text-decoration: none;
        font-weight: 600;
        transition: color 0.3s;
        font-size: 0.9em;
      }

      nav a:hover {
        color: #81c784;
      }

      .theme-btn {
        background: transparent;
        color: white;
        border: 1px solid white;
        padding: 5px 15px;
        border-radius: 20px;
        cursor: pointer;
        margin-left: 15px;
        transition: 0.3s;
      }

      .theme-btn:hover {
        background: white;
        color: black;
      }

      .container {
        max-width: 1000px;
        margin: 0 auto;
        padding: 20px;
      }

      .daily-tip {
        text-align: center;
        font-style: italic;
        font-size: 1.1em;
        color: var(--primary-color);
        font-weight: 600;
        padding: 15px;
        background: var(--secondary-color);
        border-radius: 8px;
        margin-bottom: 30px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
      }

      .card {
        background: var(--card-bg);
        backdrop-filter: blur(15px);
        -webkit-backdrop-filter: blur(15px);
        border: 1px solid rgba(255, 255, 255, 0.8);
        padding: 30px;
        margin-bottom: 30px;
        border-radius: 12px;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        transition: transform 0.3s, background-color 0.3s;
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
      .form-group select,
      .form-group textarea {
        width: 100%;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 6px;
        box-sizing: border-box;
        font-size: 16px;
        background-color: #fff;
        font-family: inherit;
        transition: background-color 0.3s, color 0.3s;
      }
      .form-group input[type="file"] {
        padding: 7px 10px;
      }
      .form-group textarea {
        resize: vertical;
      }
      .form-group input:focus,
      .form-group select:focus,
      .form-group textarea:focus {
        outline: none;
        border-color: var(--primary-color);
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

      .btn-female { background-color: var(--female-color); }
      .btn-female:hover { background-color: #c2185b; }
      
      .btn-purple { background-color: #9c27b0; }
      .btn-purple:hover { background-color: #7b1fa2; }
      
      .btn-teal { background-color: #00897b; }
      .btn-teal:hover { background-color: #00695c; }
      
      .btn-orange { background-color: #ff9800; color: #fff; }
      .btn-orange:hover { background-color: #e65100; }

      /* Male Button Styles */
      .btn-male { background-color: var(--male-color); color: white;}
      .btn-male:hover { background-color: #1565c0; }
      
      .btn-darkblue { background-color: #283593; color: white;}
      .btn-darkblue:hover { background-color: #1a237e; }
      
      .btn-lightblue { background-color: #0277bd; color: white;}
      .btn-lightblue:hover { background-color: #01579b; }

      #bmi-result,
      #tdee-result,
      #water-result,
      #mood-result,
      #session-result,
      #bill-result,
      #routine-error {
        margin-top: 20px;
        display: none;
        padding: 15px;
        border-radius: 6px;
        text-align: center;
        font-weight: bold;
        font-size: 1.2em;
        color: #333;
      }

      .booking-ticket {
        background-color: var(--secondary-color);
        border: 2px dashed var(--primary-color);
        border-radius: 8px;
        padding: 20px;
        text-align: left;
        color: #333;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
        position: relative;
        margin-top: 20px;
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
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
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

      .expert-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: 30px;
        margin-top: 30px;
      }

      .expert-member {
        background: #fdfdfd;
        border: 1px solid #eee;
        border-radius: 10px;
        padding: 25px;
        text-align: center;
        transition: transform 0.3s, box-shadow 0.3s;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
      }

      .expert-member:hover {
        transform: translateY(-8px);
        box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
      }

      .expert-member img {
        width: 140px;
        height: 140px;
        border-radius: 50%;
        object-fit: cover;
        margin-bottom: 20px;
        border: 4px solid var(--primary-color);
      }

      .expert-member h3 {
        color: var(--primary-color);
        margin: 10px 0 5px;
        font-size: 1.6em;
      }

      .expert-member p {
        margin: 0 0 12px;
        font-size: 1em;
        color: #666;
      }

      .expert-member strong {
        color: var(--text-color);
        font-weight: 700;
      }

      body.dark-mode .expert-member {
        background-color: #1e1e1e;
        border-color: #444;
      }

      body.dark-mode .expert-member p {
        color: #ccc;
      }

      footer {
        background-color: rgba(34, 34, 34, 0.95);
        color: #bbb;
        text-align: center;
        padding: 30px 20px;
        margin-top: 40px;
      }

      .social-icons {
        margin-top: 15px;
      }

      .social-icons a {
        color: #bbb;
        font-size: 24px;
        margin: 0 12px;
        text-decoration: none;
        transition: color 0.3s, transform 0.3s;
        display: inline-block;
      }

      .social-icons a:hover {
        color: var(--primary-color);
        transform: translateY(-3px);
      }

      .whatsapp-float {
        position: fixed;
        width: 60px;
        height: 60px;
        bottom: 30px;
        right: 30px;
        background-color: #25d366;
        color: #fff;
        border-radius: 50px;
        text-align: center;
        font-size: 30px;
        box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
        z-index: 1000;
        display: flex;
        align-items: center;
        justify-content: center;
        text-decoration: none;
        transition: transform 0.3s;
      }
      .whatsapp-float:hover {
        transform: scale(1.1);
      }

      .call-float {
        position: fixed;
        width: 60px;
        height: 60px;
        bottom: 100px;
        right: 30px;
        background-color: #007bff;
        color: #fff;
        border-radius: 50px;
        text-align: center;
        font-size: 24px;
        box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
        z-index: 1000;
        display: flex;
        align-items: center;
        justify-content: center;
        text-decoration: none;
        transition: transform 0.3s;
      }
      .call-float:hover {
        transform: scale(1.1);
      }

      #scrollToTopBtn {
        position: fixed;
        bottom: 170px;
        right: 35px;
        z-index: 99;
        font-size: 20px;
        border: none;
        outline: none;
        background-color: var(--primary-color);
        color: white;
        cursor: pointer;
        padding: 10px;
        border-radius: 50%;
        width: 50px;
        height: 50px;
        box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
        display: flex;
        align-items: center;
        justify-content: center;
        opacity: 0;
        visibility: hidden;
        transition: opacity 0.3s, visibility 0.3s, transform 0.3s;
      }
      #scrollToTopBtn.show {
        opacity: 1;
        visibility: visible;
      }
      #scrollToTopBtn:hover {
        background-color: #1b5e20;
        transform: translateY(-3px);
      }

      /* --- AI Chatbot Styles --- */
      .chatbot-toggler {
        position: fixed;
        bottom: 30px;
        left: 30px;
        outline: none;
        border: none;
        height: 60px;
        width: 60px;
        background: var(--primary-color);
        color: white;
        border-radius: 50%;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        transition: transform 0.3s ease;
        z-index: 1000;
        font-size: 24px;
      }

      .chatbot-toggler:hover {
        transform: scale(1.1);
        background: #1b5e20;
      }

      .chatbot-window {
        position: fixed;
        bottom: 100px;
        left: 30px;
        width: 350px;
        background: var(--card-bg);
        border-radius: 15px;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        overflow: hidden;
        z-index: 1000;
        transform: scale(0.5);
        opacity: 0;
        pointer-events: none;
        transform-origin: bottom left;
        transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        border: 1px solid rgba(255, 255, 255, 0.2);
        backdrop-filter: blur(15px);
        display: flex;
        flex-direction: column;
      }

      body.show-chatbot .chatbot-window {
        transform: scale(1);
        opacity: 1;
        pointer-events: auto;
      }

      .chat-header {
        background: var(--primary-color);
        color: white;
        padding: 15px 20px;
        display: flex;
        justify-content: space-between;
        align-items: center;
      }

      .chat-header h3 {
        margin: 0;
        font-size: 1.2rem;
        display: flex;
        align-items: center;
        gap: 8px;
      }

      .close-btn {
        background: none;
        border: none;
        color: white;
        font-size: 20px;
        cursor: pointer;
        transition: transform 0.2s;
      }
      
      .close-btn:hover {
        transform: scale(1.2);
      }

      .chat-body {
        height: 350px;
        overflow-y: auto;
        padding: 20px;
        display: flex;
        flex-direction: column;
        gap: 15px;
      }

      .chat-body::-webkit-scrollbar {
        width: 6px;
      }
      .chat-body::-webkit-scrollbar-thumb {
        background: rgba(0,0,0,0.2);
        border-radius: 10px;
      }

      .message {
        max-width: 85%;
        padding: 12px 16px;
        border-radius: 18px;
        font-size: 0.95rem;
        line-height: 1.4;
        animation: fadeIn 0.3s ease;
      }

      @keyframes fadeIn {
        from { opacity: 0; transform: translateY(10px); }
        to { opacity: 1; transform: translateY(0); }
      }

      .message.bot {
        background: #fce4ec;
        color: #880e4f;
        align-self: flex-start;
        border-bottom-left-radius: 4px;
        box-shadow: 0 2px 5px rgba(0,0,0,0.05);
      }

      .message.bot a {
        color: #c2185b;
        font-weight: bold;
        text-decoration: underline;
      }

      .message.user {
        background: var(--primary-color);
        color: white;
        align-self: flex-end;
        border-bottom-right-radius: 4px;
        box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      }

      .typing-indicator {
        display: flex;
        gap: 4px;
        padding: 12px 16px;
        background: #fce4ec;
        border-radius: 18px;
        border-bottom-left-radius: 4px;
        width: fit-content;
        align-self: flex-start;
        box-shadow: 0 2px 5px rgba(0,0,0,0.05);
      }

      .dot {
        width: 6px;
        height: 6px;
        background: #c2185b;
        border-radius: 50%;
        animation: typing 1.4s infinite ease-in-out both;
      }

      .dot:nth-child(1) { animation-delay: -0.32s; }
      .dot:nth-child(2) { animation-delay: -0.16s; }
      .dot:nth-child(3) { animation-delay: 0s; }

      @keyframes typing {
        0%, 80%, 100% { transform: scale(0); opacity: 0.5;}
        40% { transform: scale(1); opacity: 1;}
      }

      .chat-quick-replies {
        display: flex;
        gap: 8px;
        padding: 0 15px 10px 15px;
        overflow-x: auto;
        white-space: nowrap;
      }

      .chat-quick-replies::-webkit-scrollbar {
        display: none;
      }

      .chat-quick-replies span {
        background: rgba(46, 125, 50, 0.1);
        color: var(--primary-color);
        padding: 8px 14px;
        border-radius: 20px;
        font-size: 0.85rem;
        cursor: pointer;
        border: 1px solid var(--primary-color);
        transition: all 0.2s ease;
      }

      .chat-quick-replies span:hover {
        background: var(--primary-color);
        color: white;
      }

      .chat-input-area {
        display: flex;
        padding: 15px;
        background: rgba(0, 0, 0, 0.03);
        border-top: 1px solid rgba(0, 0, 0, 0.08);
      }

      body.dark-mode .chat-input-area {
        background: rgba(255, 255, 255, 0.05);
        border-top: 1px solid rgba(255, 255, 255, 0.1);
      }

      .chat-input-area input {
        flex: 1;
        border: 1px solid #ccc;
        padding: 12px 15px;
        border-radius: 25px;
        outline: none;
        background: var(--card-bg);
        color: var(--text-color);
        font-size: 0.95rem;
        transition: border-color 0.3s;
      }
      
      .chat-input-area input:focus {
        border-color: var(--primary-color);
      }

      .chat-input-area button {
        width: auto;
        background: none;
        color: var(--primary-color);
        border: none;
        font-size: 22px;
        cursor: pointer;
        padding: 0 10px;
        margin-left: 5px;
        transition: transform 0.2s;
      }
      
      .chat-input-area button:hover {
        transform: scale(1.1);
      }

      .chat-status {
        font-size: 0.8rem;
        color: #ff9800;
        padding: 0 15px 5px 15px;
        font-style: italic;
        display: none;
        text-align: center;
      }

      .chat-status.active {
        display: block;
      }

      .chat-input-area button.mic-btn {
        color: #757575;
      }

      .chat-input-area button.mic-btn:hover {
        color: var(--primary-color);
      }

      .chat-input-area button.mic-btn.listening {
        color: #f44336;
        animation: pulseMic 1.2s infinite;
      }

      @keyframes pulseMic {
        0% { transform: scale(1); }
        50% { transform: scale(1.2); }
        100% { transform: scale(1); }
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
      <a href="#bmi-calculator">BMI</a>
      <a href="#tdee-calculator">Calories</a>
      <a href="#water-calculator">Hydration</a>
      <a href="#female-health">Women's Health</a>
      <a href="#mens-health">Men's Health</a>
      <a href="#mood-tracker">Mood</a>
      <a href="#smart-routine">Routine</a>
      <a href="#bill-calculator">Estimator</a>
      <a href="#live-call">Live Call</a>
      <a href="#expert-team">Our Team</a>
      <a href="#registration">Register</a>
      <a href="#book-session">Book</a>
      <button class="theme-btn" onclick="toggleTheme()" id="themeToggleBtn">
        🌙 Dark Mode
      </button>
    </nav>

    <div class="container">
      <div class="daily-tip" id="dailyTipBox">
        Loading today's health tip...
      </div>

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
              standard health metrics like BMI.
            </li>
            <li>
              <strong>Caloric Needs (TDEE):</strong> Discover exactly how much
              fuel your body requires daily.
            </li>
            <li>
              <strong>Hydration Tracker:</strong> Personalized daily water
              intake recommendations.
            </li>
            <li>
              <strong>Women's Health Tools:</strong> Specific features for tracking menstrual cycles, cycle syncing diet/fitness, and estimating pregnancy due dates.
            </li>
            <li>
              <strong>Men's Health Tools:</strong> Specific features for tracking protein/creatine needs, natural testosterone optimization, and heart/prostate health.
            </li>
            <li>
              <strong>Mood Tracker:</strong> Keep a daily pulse on your
              emotional well-being to complement physical health.
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
            <label for="height">Height (in cm):</label>
            <input type="number" id="height" placeholder="e.g., 175" />
          </div>
          <div class="form-group">
            <label for="weight">Weight (in kg):</label>
            <input type="number" id="weight" placeholder="e.g., 70" />
          </div>

          <button onclick="calculateBMI()">Calculate My BMI</button>

          <div id="bmi-result"></div>
        </div>
      </section>

      <section id="tdee-calculator">
        <div class="card">
          <h2>Daily Calorie Needs (TDEE)</h2>
          <p>
            Calculate your <strong>Total Daily Energy Expenditure</strong> to
            find out how many calories you need to maintain your weight.
          </p>

          <div class="form-group">
            <label for="tdee-gender">Gender:</label>
            <select id="tdee-gender">
              <option value="male">Male</option>
              <option value="female">Female</option>
            </select>
          </div>
          <div class="form-group">
            <label for="tdee-age">Age:</label>
            <input type="number" id="tdee-age" placeholder="e.g., 25" />
          </div>
          <div class="form-group">
            <label for="tdee-height">Height (in cm):</label>
            <input type="number" id="tdee-height" placeholder="e.g., 175" />
          </div>
          <div class="form-group">
            <label for="tdee-weight">Weight (in kg):</label>
            <input type="number" id="tdee-weight" placeholder="e.g., 70" />
          </div>
          <div class="form-group">
            <label for="tdee-activity">Activity Level:</label>
            <select id="tdee-activity">
              <option value="1.2">Sedentary (little to no exercise)</option>
              <option value="1.375">
                Lightly active (light exercise 1-3 days/week)
              </option>
              <option value="1.55">
                Moderately active (moderate exercise 3-5 days/week)
              </option>
              <option value="1.725">
                Very active (hard exercise 6-7 days/week)
              </option>
              <option value="1.9">
                Extra active (very hard exercise/physical job)
              </option>
            </select>
          </div>

          <button onclick="calculateTDEE()">Calculate Calories</button>

          <div id="tdee-result"></div>
        </div>
      </section>

      <section id="water-calculator">
        <div class="card">
          <h2>Daily Hydration Goal</h2>
          <p>
            Proper hydration is key to health. Find out how much water you
            should drink daily.
          </p>

          <div class="form-group">
            <label for="water-weight">Weight (in kg):</label>
            <input type="number" id="water-weight" placeholder="e.g., 70" />
          </div>

          <button onclick="calculateWater()">Calculate Water Need</button>

          <div id="water-result"></div>
        </div>
      </section>

      <!-- Female Health Section -->
      <section id="female-health">
        <div class="card" style="border-left: 5px solid var(--female-color);">
          <h2 style="color: var(--female-color); border-bottom-color: #fce4ec;">🌸 Women's Health & Well-being</h2>
          <p>Specialized tools for hormonal tracking, cycle-syncing, and essential mineral goals.</p>

          <!-- 1. Menstrual Tracker -->
          <div style="background: rgba(233, 30, 99, 0.05); padding: 20px; border-radius: 8px; margin-bottom: 20px;">
              <h3 style="color: #c2185b; margin-top: 0;">1. Menstrual & Ovulation Tracker</h3>
              <p style="font-size: 0.9em; color: #555;">Predict your next period and find your most fertile days.</p>
              <div class="form-group">
                <label for="last-period">First day of last period:</label>
                <input type="date" id="last-period" />
              </div>
              <div class="form-group">
                <label for="cycle-length">Average cycle length (days):</label>
                <input type="number" id="cycle-length" placeholder="e.g., 28" value="28" />
              </div>
              <button onclick="calculateCycle()" class="btn-female">Calculate Cycle</button>
              <div id="cycle-result" style="display: none; margin-top: 15px; padding: 15px; border-radius: 6px; background-color: #fce4ec; color: #880e4f; text-align: left; font-size: 1.1em; line-height: 1.8;"></div>
          </div>

          <!-- 2. Cycle Syncing Diet & Fitness -->
          <div style="background: rgba(0, 150, 136, 0.05); padding: 20px; border-radius: 8px; margin-bottom: 20px;">
              <h3 style="color: #00796b; margin-top: 0;">2. Cycle Syncing Guide (Diet & Fitness)</h3>
              <p style="font-size: 0.9em; color: #555;">A woman's metabolism and energy levels change throughout her cycle. Tell us your current cycle day to get specific diet and fitness recommendations.</p>
              <div class="form-group">
                <label for="current-cycle-day">What day of your cycle are you on? (Day 1 = First day of bleeding):</label>
                <input type="number" id="current-cycle-day" placeholder="e.g., 12" min="1" max="40" />
              </div>
              <button onclick="calculateCyclePhase()" class="btn-teal">Get Phase Recommendations</button>
              <div id="cycle-phase-result" style="display: none; margin-top: 15px; padding: 15px; border-radius: 6px; background-color: #e0f2f1; color: #004d40; text-align: left; font-size: 1.05em; line-height: 1.6;"></div>
          </div>

          <!-- 3. Essential Minerals Calculator -->
          <div style="background: rgba(255, 152, 0, 0.05); padding: 20px; border-radius: 8px; margin-bottom: 20px;">
              <h3 style="color: #e65100; margin-top: 0;">3. Women's Daily Iron & Calcium Needs</h3>
              <p style="font-size: 0.9em; color: #555;">Women have highly specific mineral requirements that prevent anemia and osteoporosis. Check your daily targets.</p>
              <div class="form-group">
                <label for="women-age">Your Age:</label>
                <input type="number" id="women-age" placeholder="e.g., 25" min="12" max="100" />
              </div>
              <div class="form-group">
                <label for="women-status">Current Status:</label>
                <select id="women-status">
                  <option value="none">Not Pregnant or Lactating</option>
                  <option value="pregnant">Pregnant</option>
                  <option value="lactating">Breastfeeding (Lactating)</option>
                </select>
              </div>
              <button onclick="calculateMinerals()" class="btn-orange">Calculate Needs</button>
              <div id="minerals-result" style="display: none; margin-top: 15px; padding: 15px; border-radius: 6px; background-color: #fff3e0; color: #e65100; text-align: left; font-size: 1.05em; line-height: 1.6;"></div>
          </div>

          <!-- 4. Pregnancy Due Date Calculator -->
          <div style="background: rgba(156, 39, 176, 0.05); padding: 20px; border-radius: 8px;">
              <h3 style="color: #7b1fa2; margin-top: 0;">4. Pregnancy Due Date Calculator</h3>
              <p style="font-size: 0.9em; color: #555;">Estimate your baby's arrival date based on your Last Menstrual Period (LMP).</p>
              <div class="form-group">
                <label for="lmp-date">First day of last period (LMP):</label>
                <input type="date" id="lmp-date" />
              </div>
              <button onclick="calculateDueDate()" class="btn-purple">Estimate Due Date</button>
              <div id="duedate-result" style="display: none; margin-top: 15px; padding: 15px; border-radius: 6px; background-color: #f3e5f5; color: #4a148c; text-align: center; font-size: 1.1em;"></div>
          </div>
        </div>
      </section>

      <!-- Male Health Section -->
      <section id="mens-health">
        <div class="card" style="border-left: 5px solid var(--male-color);">
          <h2 style="color: var(--male-color); border-bottom-color: #e3f2fd;">💪 Men's Health & Vitality</h2>
          <p>Specialized tools for muscle building, natural testosterone optimization, and men's long-term health.</p>

          <!-- 1. Protein & Creatine Needs -->
          <div style="background: rgba(25, 118, 210, 0.05); padding: 20px; border-radius: 8px; margin-bottom: 20px;">
              <h3 style="color: #1565c0; margin-top: 0;">1. Daily Protein & Creatine Goals</h3>
              <p style="font-size: 0.9em; color: #555;">Optimize your macro intake to build or preserve lean muscle mass.</p>
              <div class="form-group">
                <label for="male-weight">Weight (in kg):</label>
                <input type="number" id="male-weight" placeholder="e.g., 80" />
              </div>
              <div class="form-group">
                <label for="male-goal">Primary Fitness Goal:</label>
                <select id="male-goal">
                  <option value="maintain">Maintain Muscle & General Health</option>
                  <option value="bulk">Bulking (Maximize Muscle Gain)</option>
                  <option value="cut">Cutting (Lose Fat, Preserve Muscle)</option>
                </select>
              </div>
              <button onclick="calculateMaleMacros()" class="btn-male">Calculate Macros</button>
              <div id="male-macro-result" style="display: none; margin-top: 15px; padding: 15px; border-radius: 6px; background-color: #e3f2fd; color: #0d47a1; text-align: left; font-size: 1.05em; line-height: 1.6;"></div>
          </div>

          <!-- 2. Natural Testosterone Guide -->
          <div style="background: rgba(40, 53, 147, 0.05); padding: 20px; border-radius: 8px; margin-bottom: 20px;">
              <h3 style="color: #283593; margin-top: 0;">2. Natural Hormone Optimization Guide</h3>
              <p style="font-size: 0.9em; color: #555;">Testosterone affects mood, muscle mass, and energy. Assess your lifestyle factors.</p>
              <div class="form-group">
                <label for="male-sleep">Average Sleep per night (hours):</label>
                <input type="number" id="male-sleep" placeholder="e.g., 6" min="0" max="24" />
              </div>
              <div class="form-group">
                <label for="male-stress">Stress Level:</label>
                <select id="male-stress">
                  <option value="low">Low (Relaxed)</option>
                  <option value="medium">Medium (Manageable)</option>
                  <option value="high">High (Constantly stressed)</option>
                </select>
              </div>
              <button onclick="calculateTestosteroneTips()" class="btn-darkblue">Get Optimization Plan</button>
              <div id="testosterone-result" style="display: none; margin-top: 15px; padding: 15px; border-radius: 6px; background-color: #e8eaf6; color: #1a237e; text-align: left; font-size: 1.05em; line-height: 1.6;"></div>
          </div>

          <!-- 3. Heart & Prostate Health Check -->
          <div style="background: rgba(2, 119, 189, 0.05); padding: 20px; border-radius: 8px;">
              <h3 style="color: #0277bd; margin-top: 0;">3. Heart & Prostate Health Planner</h3>
              <p style="font-size: 0.9em; color: #555;">Age-based reminders and superfood recommendations for men's long-term wellness.</p>
              <div class="form-group">
                <label for="male-age">Your Age:</label>
                <input type="number" id="male-age" placeholder="e.g., 45" min="18" max="100" />
              </div>
              <button onclick="calculateMaleHealth()" class="btn-lightblue">Check Health Plan</button>
              <div id="male-health-result" style="display: none; margin-top: 15px; padding: 15px; border-radius: 6px; background-color: #e1f5fe; color: #01579b; text-align: left; font-size: 1.05em; line-height: 1.6;"></div>
          </div>
        </div>
      </section>

      <section id="mood-tracker">
        <div class="card">
          <h2>Daily Mood Tracker (AI Friend 🤖)</h2>
          <p>
            Emotional health is so important, my dear. How are you feeling today? Share it with me, I am always here to listen.
          </p>

          <div class="form-group">
            <label for="current-mood">Select your mood:</label>
            <select id="current-mood">
              <option value="" disabled selected>Choose a mood...</option>
              <option value="Happy">Happy 😊</option>
              <option value="Calm">Calm 😌</option>
              <option value="Energetic">Energetic ⚡</option>
              <option value="Stressed">Stressed 😰</option>
              <option value="Tired">Tired 😴</option>
              <option value="Sad">Sad 😢</option>
            </select>
          </div>

          <div class="form-group">
            <label for="mood-notes">Journal Notes (Optional):</label>
            <textarea
              id="mood-notes"
              rows="3"
              placeholder="What is on your mind today, Buddy?"
            ></textarea>
          </div>

          <button onclick="logMood()">Share With Me</button>

          <div id="mood-result"></div>
        </div>
      </section>

      <section id="smart-routine">
        <div class="card">
          <h2>Smart Routine Maker</h2>
          <p>
            Generate a personalized, time-based daily structure optimized for
            your specific health goals.
          </p>

          <div class="form-group">
            <label for="routine-goal">Primary Goal:</label>
            <select id="routine-goal">
              <option value="Weight Loss">Weight Loss & Fat Burning</option>
              <option value="Muscle Gain">Muscle Gain & Strength</option>
              <option value="General Health">General Health & Vitality</option>
              <option value="Better Sleep">Better Sleep & Recovery</option>
            </select>
          </div>
          <div class="form-group">
            <label for="wake-time">Usual Wake-up Time:</label>
            <input type="time" id="wake-time" value="07:00" />
          </div>

          <button onclick="generateRoutine()">Generate My Routine</button>

          <div id="routine-error"></div>
          <div
            id="routine-result"
            class="booking-ticket"
            style="display: none"
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

          <div id="bill-result"></div>
        </div>
      </section>

      <section id="live-call">
        <div class="card">
          <h2>Integrated Live Video Consultation (Google Meet)</h2>
          <p>
            Initiate a direct video call with your assigned health expert. The
            meeting will open securely in a new tab.
          </p>

          <div class="form-group" id="call-setup">
            <label for="expert-select">Select Expert to Call:</label>
            <select id="expert-select">
              <option value="9229666499">
                Srishty Sharma (+91 9229666499)
              </option>
              <option value="7979043452">
                Shalini Sharma (+91 7979043452)
              </option>
              <option value="8389024961">Sahil Sharma (+91 8389024961)</option>
              <option value="6205307607">Krish Sharma (+91 6205307607)</option>
              <option value="9466395875">
                Lakshay Sharma (+91 9466395875)
              </option>
            </select>
            <div class="form-group" style="margin-top: 10px">
              <label for="patient-name-input">Your Name (For the Call):</label>
              <input
                type="text"
                id="patient-name-input"
                placeholder="Enter your name"
                value="Patient"
              />
            </div>

            <div class="form-group" style="margin-top: 10px">
              <label for="call-password-input">Meeting Password:</label>
              <input
                type="password"
                id="call-password-input"
                placeholder="Enter access password"
              />
            </div>
            <button
              id="startCallBtn"
              onclick="startVideoCall()"
              style="margin-top: 15px"
            >
              Start Video Call
            </button>
          </div>

          <div id="video-interface" style="display: none; margin-top: 20px">
            <div
              style="
                background: var(--secondary-color);
                padding: 20px;
                border-radius: 8px;
                border: 1px dashed var(--primary-color);
                text-align: center;
              "
            >
              <h3
                id="call-status"
                style="color: var(--primary-color); margin-top: 0"
              >
                Meeting opening...
              </h3>
              <p style="margin-bottom: 0">
                Google Meet provides its own secure Camera, Microphone, and
                Screen Sharing controls inside the new tab.
              </p>
            </div>

            <button
              onclick="notifyExpert()"
              style="background-color: #25d366; margin-top: 20px; width: 100%"
            >
              📲 Send Meeting Link to Expert (WhatsApp)
            </button>

            <button
              onclick="endVideoCall()"
              style="background-color: #d32f2f; margin-top: 10px; width: 100%"
            >
              Close / Return to Menu
            </button>
          </div>
        </div>
      </section>

      <section id="expert-team">
        <div class="card">
          <h2>Meet Our Expert Health Team</h2>
          <p>
            Our team of certified professionals is here to guide you on your
            health journey. From personalized nutrition to tailored workout
            plans, get the expert support you need before booking your session.
          </p>

          <div class="expert-grid">
            <div class="expert-member">
              <img src="Srishty Sharma.jpg" alt="Srishty Sharma" />
              <h3>Srishty Sharma</h3>
              <p><strong>Registered Dietitian Nutritionist (RDN)</strong></p>
              <p>
                Specializes in holistic diet planning and metabolic health.
                (<strong>Female Well-Being Specialist</strong>)
              </p>
              <p><strong>Phone No:</strong> 9229666499</p>
            </div>

            <div class="expert-member">
              <img src="Shalini Sharma.jpg" alt="Shalini Sharma" />
              <h3>Shalini Sharma</h3>
              <p><strong>Chief Nutritionist & Gynecologist</strong></p>
              <p>
                Specializes in holistic diet planning and metabolic health.
                (<strong> Female Well-Being Specialist</strong>)
              </p>
              <p><strong>Phone No:</strong> 7979043452</p>
            </div>

            <div class="expert-member">
              <img src="Sahil_image.jpeg" alt="Sahil Sharma" />
              <h3>Sahil Sharma</h3>
              <p><strong>Fitness Lead & Specialist</strong></p>
              <p>
                Behaviour health & Motivational strategies for sustainable
                weight management. Focuses on adaptive workout routines and
                functional fitness. (Ex. <strong>Military Physical Health Trainer &
                Mental Health Trainer</strong>)
              </p>
              <p><strong>Phone No:</strong> 8389024961</p>
            </div>

            <div class="expert-member">
              <img src="Krish Sharma.jpg" alt="Krish Sharma" />
              <h3>Krish Sharma</h3>
              <p><strong>Group Fitness Instructor</strong></p>
              <p>
                These instructor is <strong>Motivational</strong>leader who teach orchestrated,
                multi-person exercise classes. He must possess safe technical
                skills across various formats and the dynamic energy to engage a
                roomful of participants simultaneously.
              </p>
              <p><strong>Phone No:</strong> 6205307607</p>
            </div>

            <div class="expert-member">
              <img src="" alt="Lakshay Sharma" />
              <h3>Lakshay Sharma</h3>
              <p><strong>Weight Loss Coach</strong></p>
              <p>
                Focuses on adaptive workout routines and functional fitness.
                (<strong>For Men Health</strong>)
              </p>
              <p><strong>Phone No:</strong> 9466395875</p>
            </div>
          </div>
        </div>
      </section>

      <section id="registration">
        <div class="card">
          <h2>Member Registration Form</h2>
          <p>Join our Health & Nutrition program by filling out the application form below.</p>
          
          <form id="registrationForm" onsubmit="handleRegistration(event)">
            <div class="form-group">
              <label for="reg-name">Full Name *</label>
              <input type="text" id="reg-name" required placeholder="Enter your full name" />
            </div>
            
            <div class="form-group">
              <label for="reg-email">Email Address *</label>
              <input type="email" id="reg-email" required placeholder="Enter your email address" />
            </div>

            <div class="form-group">
              <label for="reg-phone">Phone Number *</label>
              <input type="tel" id="reg-phone" required placeholder="Enter 10-digit number" />
            </div>

            <div class="form-group">
              <label for="reg-dob">Date of Birth *</label>
              <input type="date" id="reg-dob" required />
            </div>

            <div class="form-group">
              <label for="reg-gender">Gender *</label>
              <select id="reg-gender" required>
                <option value="" disabled selected>Select gender...</option>
                <option value="Male">Male</option>
                <option value="Female">Female</option>
                <option value="Other">Other</option>
              </select>
            </div>

            <div class="form-group">
              <label for="reg-photo">Upload Profile Photo (Headshot) *</label>
              <input type="file" id="reg-photo" accept="image/*" required />
            </div>

            <div class="form-group">
              <label for="reg-id">Upload ID Card (Aadhar/PAN/Passport) *</label>
              <input type="file" id="reg-id" accept="image/*, .pdf" required />
            </div>

            <div class="form-group">
              <label for="reg-address">Full Residential Address *</label>
              <textarea id="reg-address" rows="3" required placeholder="Enter your complete address"></textarea>
            </div>

            <button type="submit" id="regSubmitBtn">Submit Registration</button>
            <div id="reg-result" style="display: none; margin-top: 15px; padding: 15px; border-radius: 6px; text-align: center; font-weight: bold;"></div>
          </form>
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
          <p>Examples of healthy routines, Exercise and balanced diets.</p>
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
                target="Junk Food"
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
          <p><strong>Manager:</strong> Sahil Sharma</p>
          <p>
            <strong>Email:</strong>
            <a href="mailto:mr.jerry1925@gmail.com">mr.jerry1925@gmail.com</a>
          </p>

          <p>
            <strong>Phone:</strong>
            <a
              href="tel:+918389024961"
              style="
                color: var(--primary-color);
                text-decoration: none;
                font-weight: bold;
              "
              >+91 8389024961</a
            >
          </p>

          <p>
            <strong>Address:</strong> IIT-Patna, Bihta, Patna, Bihar. India - 800002
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

    <button class="chatbot-toggler" id="chatbotToggler" title="Talk to AI Buddy">🤖</button>

    <div class="chatbot-window">
      <div class="chat-header">
        <h3>AI Health Buddy 🤖</h3>
        <button class="close-btn" id="closeChat">✖</button>
      </div>
      <div class="chat-body" id="chatBox">
        <!-- Initial Greeting for Bot -->
      </div>

      <div class="chat-quick-replies">
        <span onclick="sendQuickReply('I am stressed')">Stressed</span>
        <span onclick="sendQuickReply('I need motivation')">Motivation</span>
        <span onclick="sendQuickReply('Tell me about diet')">Diet Tips</span>
        <span onclick="sendQuickReply('Period pain tips')">Period Cramps</span>
      </div>

      <div id="chatStatus" class="chat-status">I am listening... Speak now.</div>
      
      <div class="chat-input-area">
        <input
          type="text"
          id="chatInput"
          placeholder="Tell me how you feel..."
          autocomplete="off"
        />
        <button id="micBtn" class="mic-btn" title="Click to speak">🎤</button>
        <button id="sendChatBtn" title="Send message">➤</button>
      </div>
    </div>

    <a
      href="https://wa.me/918389024961"
      class="whatsapp-float"
      target="_blank"
      title="Chat with us on WhatsApp"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="35"
        height="35"
        fill="currentColor"
        viewBox="0 0 16 16"
      >
        <path
          d="M13.601 2.326A7.854 7.854 0 0 0 7.994 0C3.627 0 .068 3.558.064 7.926c-.003 1.396.366 2.76 1.057 3.965L0 16l4.204-1.102a7.933 7.933 0 0 0 3.79.965h.004c4.368 0 7.926-3.558 7.93-7.93A7.898 7.898 0 0 0 13.6 2.326zM7.994 14.521a6.573 6.573 0 0 1-3.356-.92l-.24-.144-2.494.654.666-2.433-.156-.251a6.56 6.56 0 0 1-1.007-3.505c0-3.626 2.957-6.584 6.591-6.584a6.56 6.56 0 0 1 4.66 1.931 6.557 6.557 0 0 1 1.928 4.66c-.004 3.639-2.961 6.592-6.592 6.592zm3.615-4.934c-.197-.099-1.17-.578-1.353-.646-.182-.065-.315-.099-.445.099-.133.197-.513.646-.627.775-.114.133-.232.148-.43.05-.197-.1-.836-.308-1.592-.985-.59-.525-.985-1.175-1.103-1.372-.114-.198-.011-.304.088-.403.087-.088.197-.232.296-.346.1-.114.133-.198.198-.33.065-.134.034-.248-.015-.347-.05-.099-.445-1.076-.612-1.47-.16-.389-.323-.335-.445-.34-.114-.004-.247-.007-.38-.007a.729.729 0 0 0-.529.247c-.182.198-.691.677-.691 1.654 0 .977.71 1.916.81 2.049.098.133 1.394 2.132 3.383 2.992.47.205.84.326 1.129.418.475.152.904.129 1.246.08.38-.058 1.171-.48 1.338-.943.164-.464.164-.86.114-.943-.049-.084-.182-.133-.38-.232z"
        />
      </svg>
    </a>

    <a href="tel:+918389024961" class="call-float" title="Call Us Directly">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="28"
        height="28"
        fill="currentColor"
        viewBox="0 0 16 16"
      >
        <path
          fill-rule="evenodd"
          d="M1.885.511a1.745 1.745 0 0 1 2.61.163L6.29 2.98c.329.423.445.974.315 1.494l-.547 2.19a.678.678 0 0 0 .178.643l2.457 2.457a.678.678 0 0 0 .644.178l2.189-.547a1.745 1.745 0 0 1 1.494.315l2.306 1.794c.829.645.905 1.87.163 2.611l-1.034 1.034c-.74.74-1.846 1.065-2.877.702a18.634 18.634 0 0 1-7.01-4.42 18.634 18.634 0 0 1-4.42-7.009c-.362-1.03-.037-2.137.703-2.877L1.885.511z"
        />
      </svg>
    </a>

    <button onclick="scrollToTop()" id="scrollToTopBtn" title="Go to top">
      ▲
    </button>
    <footer>
      <p>
        <strong>© 2026 Health & Nutrition Recommendation System.</strong>
        <p>Designed by Group 165</p>
      </p>
      
      <!-- Social Media Logo Section -->
      <div class="social-icons">
        <a href="#" target="_blank" title="Youtube"><i class="fab fa-youtube"></i></a>
        <a href="#" target="_blank" title="Facebook"><i class="fab fa-facebook-f"></i></a>
        <a href="#" target="_blank" title="Instagram"><i class="fab fa-instagram"></i></a>
        <a href="#" target="_blank" title="Twitter"><i class="fab fa-twitter"></i></a>
        <a href="#" target="_blank" title="LinkedIn"><i class="fab fa-linkedin-in"></i></a>
      </div>
    </footer>

    <script>
      function toggleTheme() {
        const body = document.body;
        const btn = document.getElementById("themeToggleBtn");
        body.classList.toggle("dark-mode");

        if (body.classList.contains("dark-mode")) {
          btn.innerText = "☀️ Light Mode";
        } else {
          btn.innerText = "🌙 Dark Mode";
        }
      }

      window.onscroll = function () {
        const topBtn = document.getElementById("scrollToTopBtn");
        if (
          document.body.scrollTop > 300 ||
          document.documentElement.scrollTop > 300
        ) {
          topBtn.classList.add("show");
        } else {
          topBtn.classList.remove("show");
        }
      };

      function scrollToTop() {
        window.scrollTo({ top: 0, behavior: "smooth" });
      }

      window.onload = function () {
        const tips = [
          "💡 Tip: Drinking a glass of water before meals can aid digestion and prevent overeating.",
          "💡 Tip: Aim for at least 7-8 hours of sleep. Recovery is just as important as the workout!",
          "💡 Tip: Include a source of lean protein in every meal to keep you fuller for longer.",
          "💡 Tip: Take a 5-minute stretching break for every hour you sit at your desk.",
          "💡 Tip: Don't drink your calories! Swap sugary sodas for sparkling water with lemon.",
          "💡 Women's Health Tip: Iron needs increase during your menstrual phase. Try cooking with a cast-iron skillet!",
          "💡 Men's Health Tip: Optimal Vitamin D and Zinc levels are crucial for maintaining healthy testosterone levels natively."
        ];

        const tipElement = document.getElementById("dailyTipBox");
        if (tipElement) {
          tipElement.innerText = tips[Math.floor(Math.random() * tips.length)];
        }
        
        // Initialize chat with time-based greeting
        const initialMsg = `${getTimeGreeting()}, my dear! नमस्ते! 👋 I am your personal AI Buddy. What's on your mind today?`;
        chatBox.appendChild(createChatLi(initialMsg, "bot"));
        speakResponse(initialMsg);
      };

      function calculateBMI() {
        let name = document.getElementById("name").value;
        let heightCm = document.getElementById("height").value;
        let weightKg = document.getElementById("weight").value;
        let resultDiv = document.getElementById("bmi-result");

        if (heightCm === "" || weightKg === "" || heightCm <= 0 || weightKg <= 0) {
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
        let textColor = "#333";

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

      function calculateTDEE() {
        let age = parseInt(document.getElementById("tdee-age").value);
        let height = parseInt(document.getElementById("tdee-height").value);
        let weight = parseInt(document.getElementById("tdee-weight").value);
        let gender = document.getElementById("tdee-gender").value;
        let activity = parseFloat(document.getElementById("tdee-activity").value);
        let resultDiv = document.getElementById("tdee-result");

        if (!age || !height || !weight || age <= 0 || height <= 0 || weight <= 0) {
          resultDiv.style.display = "block";
          resultDiv.style.backgroundColor = "#ffebee";
          resultDiv.style.color = "#c62828";
          resultDiv.innerHTML = "Please fill out all fields with valid numbers.";
          return;
        }

        let bmr = 10 * weight + 6.25 * height - 5 * age;
        bmr = gender === "male" ? bmr + 5 : bmr - 161;
        let tdee = Math.round(bmr * activity);

        resultDiv.style.display = "block";
        resultDiv.style.backgroundColor = "#e8f5e9";
        resultDiv.style.color = "#2e7d32";
        resultDiv.innerHTML = `To maintain your current weight, you need approximately <strong>${tdee} calories</strong> per day.`;
      }

      function calculateWater() {
        let weight = parseFloat(document.getElementById("water-weight").value);
        let resultDiv = document.getElementById("water-result");

        if (!weight || weight <= 0) {
          resultDiv.style.display = "block";
          resultDiv.style.backgroundColor = "#ffebee";
          resultDiv.style.color = "#c62828";
          resultDiv.innerHTML = "Please enter a valid weight.";
          return;
        }

        let liters = (weight * 0.033).toFixed(1);
        let glasses = Math.round(liters * 4);

        resultDiv.style.display = "block";
        resultDiv.style.backgroundColor = "#e8f5e9";
        resultDiv.style.color = "#2e7d32";
        resultDiv.innerHTML = `You should aim to drink about <strong>${liters} Liters</strong> (approx. ${glasses} glasses) of water daily.`;
      }

      // Feature 1: Menstrual Cycle Tracker Logic
      function calculateCycle() {
        const lastPeriodInput = document.getElementById("last-period").value;
        const cycleLength = parseInt(document.getElementById("cycle-length").value);
        const resultDiv = document.getElementById("cycle-result");

        if (!lastPeriodInput || !cycleLength || cycleLength <= 0) {
            resultDiv.style.display = "block";
            resultDiv.innerHTML = "Please enter a valid date and cycle length.";
            return;
        }

        const lastPeriodDate = new Date(lastPeriodInput);
        
        const nextPeriodDate = new Date(lastPeriodDate);
        nextPeriodDate.setDate(lastPeriodDate.getDate() + cycleLength);

        const ovulationDate = new Date(nextPeriodDate);
        ovulationDate.setDate(nextPeriodDate.getDate() - 14);

        const fertileStart = new Date(ovulationDate);
        fertileStart.setDate(ovulationDate.getDate() - 5);
        
        const fertileEnd = new Date(ovulationDate);
        fertileEnd.setDate(ovulationDate.getDate() + 1);

        const options = { weekday: 'short', month: 'short', day: 'numeric' };

        resultDiv.style.display = "block";
        resultDiv.innerHTML = `
            <ul style="list-style-type: none; padding: 0; margin: 0;">
                <li>🩸 <strong>Next Period Expected:</strong> ${nextPeriodDate.toLocaleDateString(undefined, options)}</li>
                <li>🌸 <strong>Estimated Ovulation:</strong> ${ovulationDate.toLocaleDateString(undefined, options)}</li>
                <li>✨ <strong>Fertile Window:</strong> ${fertileStart.toLocaleDateString(undefined, options)} to ${fertileEnd.toLocaleDateString(undefined, options)}</li>
            </ul>
        `;
      }

      // Feature 2: Cycle Syncing Guide
      function calculateCyclePhase() {
        const cycleDay = parseInt(document.getElementById("current-cycle-day").value);
        const resultDiv = document.getElementById("cycle-phase-result");

        if (!cycleDay || cycleDay < 1 || cycleDay > 40) {
            resultDiv.style.display = "block";
            resultDiv.style.backgroundColor = "#ffebee";
            resultDiv.style.color = "#c62828";
            resultDiv.innerHTML = "Please enter a valid cycle day (usually between 1 and 35).";
            return;
        }

        let phaseName, hormones, diet, fitness;

        if (cycleDay >= 1 && cycleDay <= 5) {
            phaseName = "Menstrual Phase (Winter) ❄️";
            hormones = "Estrogen and Progesterone drop.";
            diet = "Focus on <strong>Iron & Zinc-rich foods</strong> to replenish blood (spinach, lentils, dark chocolate, red meat). Drink soothing teas (chamomile/ginger).";
            fitness = "<strong>Rest & Restore:</strong> Gentle walks, Yin yoga, stretching. Avoid high-intensity workouts.";
        } else if (cycleDay >= 6 && cycleDay <= 13) {
            phaseName = "Follicular Phase (Spring) 🌱";
            hormones = "Estrogen starts to rise, boosting energy and mood.";
            diet = "Focus on <strong>fresh, vibrant foods</strong> (salads, lean proteins, fermented foods like yogurt) to metabolize estrogen.";
            fitness = "<strong>High Energy:</strong> Great time for Cardio, HIIT, running, and trying new challenging workouts.";
        } else if (cycleDay >= 14 && cycleDay <= 16) {
            phaseName = "Ovulation Phase (Summer) ☀️";
            hormones = "Estrogen peaks, Testosterone surges slightly.";
            diet = "Focus on <strong>anti-inflammatory & fiber-rich foods</strong> (berries, nuts, cruciferous veggies) to help clear excess hormones.";
            fitness = "<strong>Peak Strength:</strong> Heavy weightlifting, spin classes, high-intensity bootcamps. You have max energy now!";
        } else {
            phaseName = "Luteal Phase (Autumn) 🍂";
            hormones = "Progesterone rises (can cause bloating/PMS). Metabolism speeds up!";
            diet = "Focus on <strong>Complex Carbs & Magnesium</strong> (sweet potatoes, oats, pumpkin seeds) to curb cravings and stabilize mood.";
            fitness = "<strong>Scale it back:</strong> Pilates, moderate strength training, and eventually transitioning to yoga as your period approaches.";
        }

        resultDiv.style.display = "block";
        resultDiv.style.backgroundColor = "#e0f2f1";
        resultDiv.style.color = "#004d40";
        resultDiv.innerHTML = `
            <h4 style="margin-top:0; border-bottom: 1px solid #b2dfdb; padding-bottom: 5px;">${phaseName}</h4>
            <p style="margin-bottom:8px;"><strong>🧬 Hormones:</strong> ${hormones}</p>
            <p style="margin-bottom:8px;"><strong>🥗 Nutrition:</strong> ${diet}</p>
            <p style="margin-bottom:0;"><strong>🧘‍♀️ Fitness:</strong> ${fitness}</p>
        `;
      }

      // Feature 3: Essential Minerals Calculator
      function calculateMinerals() {
        const age = parseInt(document.getElementById("women-age").value);
        const status = document.getElementById("women-status").value;
        const resultDiv = document.getElementById("minerals-result");

        if (!age || age < 10) {
            resultDiv.style.display = "block";
            resultDiv.style.backgroundColor = "#ffebee";
            resultDiv.style.color = "#c62828";
            resultDiv.innerHTML = "Please enter a valid age.";
            return;
        }

        let ironNeeds = 0;
        let calciumNeeds = 0;

        // Calcium Logic
        if (age >= 14 && age <= 18) calciumNeeds = 1300;
        else if (age >= 19 && age <= 50) calciumNeeds = 1000;
        else calciumNeeds = 1200; // 51+ need more calcium for bone density

        // Iron Logic
        if (status === "pregnant") ironNeeds = 27;
        else if (status === "lactating") {
            if (age <= 18) ironNeeds = 10;
            else ironNeeds = 9;
        } 
        else if (age >= 14 && age <= 18) ironNeeds = 15;
        else if (age >= 19 && age <= 50) ironNeeds = 18; // Menstruating years
        else ironNeeds = 8; // Post-menopause

        resultDiv.style.display = "block";
        resultDiv.style.backgroundColor = "#fff3e0";
        resultDiv.style.color = "#e65100";
        resultDiv.innerHTML = `
            <div style="display:flex; justify-content:space-between; border-bottom: 1px solid #ffe0b2; padding-bottom:10px; margin-bottom:10px;">
                <div>
                    <strong>🥩 Daily Iron Goal:</strong><br>
                    <span style="font-size:1.4em; font-weight:bold;">${ironNeeds} mg</span>
                </div>
                <div>
                    <strong>🥛 Daily Calcium Goal:</strong><br>
                    <span style="font-size:1.4em; font-weight:bold;">${calciumNeeds} mg</span>
                </div>
            </div>
            <p style="font-size:0.9em; margin-bottom:5px;"><strong>Iron Sources:</strong> Lentils, Spinach, Tofu, Red Meat, Fortified Cereals. <em>(Pair with Vitamin C for better absorption!)</em></p>
            <p style="font-size:0.9em; margin-bottom:0;"><strong>Calcium Sources:</strong> Milk/Yogurt, Almonds, Chia Seeds, Kale, Fortified Plant Milks.</p>
        `;
      }

      // Feature 4: Pregnancy Due Date Logic
      function calculateDueDate() {
        const lmpInput = document.getElementById("lmp-date").value;
        const resultDiv = document.getElementById("duedate-result");

        if (!lmpInput) {
            resultDiv.style.display = "block";
            resultDiv.innerHTML = "Please enter the date of your last period.";
            return;
        }

        const lmpDate = new Date(lmpInput);
        const dueDate = new Date(lmpDate);
        dueDate.setDate(lmpDate.getDate() + 280);

        const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };

        resultDiv.style.display = "block";
        resultDiv.innerHTML = `👶 <strong>Estimated Due Date (EDD):</strong><br><span style="font-size: 1.2em;">${dueDate.toLocaleDateString(undefined, options)}</span><br><small style="font-size: 0.8em; opacity: 0.8;">*Note: Only ~5% of babies are born exactly on their due date.</small>`;
      }

      /* =========================================
         MALE HEALTH JS LOGIC
         ========================================= */
      
      function calculateMaleMacros() {
        const weight = parseFloat(document.getElementById("male-weight").value);
        const goal = document.getElementById("male-goal").value;
        const resultDiv = document.getElementById("male-macro-result");

        if (!weight || weight <= 0) {
            resultDiv.style.display = "block";
            resultDiv.style.backgroundColor = "#ffebee";
            resultDiv.style.color = "#c62828";
            resultDiv.innerHTML = "Please enter a valid weight in kg.";
            return;
        }

        let proteinFactor = 1.8; // Maintain
        let calOffset = "Maintenance Calories";

        if (goal === "bulk") {
          proteinFactor = 2.2;
          calOffset = "Surplus Calories (+300 to 500 kcal)";
        } else if (goal === "cut") {
          proteinFactor = 2.4; // Higher to preserve muscle
          calOffset = "Deficit Calories (-300 to 500 kcal)";
        }

        const proteinGrams = Math.round(weight * proteinFactor);
        const waterLiters = (weight * 0.04).toFixed(1);

        resultDiv.style.display = "block";
        resultDiv.style.backgroundColor = "#e3f2fd";
        resultDiv.style.color = "#0d47a1";
        resultDiv.innerHTML = `
          <ul style="list-style-type:none; padding:0; margin:0;">
            <li style="margin-bottom:8px;">🥩 <strong>Daily Protein:</strong> ~${proteinGrams}g <em>(Aim for lean Meats, Whey, Eggs, Tofu)</em></li>
            <li style="margin-bottom:8px;">⚡ <strong>Creatine Monohydrate:</strong> 5g / day <em>(Saturates muscles, boosts strength and ATP recovery)</em></li>
            <li style="margin-bottom:8px;">💧 <strong>Daily Hydration:</strong> ${waterLiters} Liters</li>
            <li style="margin-bottom:0px;">🔥 <strong>Target Diet:</strong> ${calOffset}</li>
          </ul>
        `;
      }

      function calculateTestosteroneTips() {
        const sleep = parseFloat(document.getElementById("male-sleep").value);
        const stress = document.getElementById("male-stress").value;
        const resultDiv = document.getElementById("testosterone-result");

        if (!sleep && sleep !== 0) {
            resultDiv.style.display = "block";
            resultDiv.style.backgroundColor = "#ffebee";
            resultDiv.style.color = "#c62828";
            resultDiv.innerHTML = "Please enter your average sleep duration.";
            return;
        }

        let sleepTip = "";
        let stressTip = "";

        if (sleep < 7) {
          sleepTip = "<strong>Sleep Deficit Detected:</strong> Sleeping less than 7 hours can reduce testosterone levels by 10-15%. Aim to add 1-2 hours of sleep per night.";
        } else {
          sleepTip = "<strong>Good Sleep Habits:</strong> You are getting enough sleep, which is critical for peak hormone production overnight.";
        }

        if (stress === "high") {
          stressTip = "<strong>High Cortisol Alert:</strong> Chronic stress elevates cortisol, which directly suppresses testosterone. Consider Ashwagandha, meditation, or therapy.";
        } else if (stress === "medium") {
          stressTip = "<strong>Moderate Stress:</strong> Manageable, but keep an eye on it. Regular weightlifting helps clear cortisol naturally.";
        } else {
          stressTip = "<strong>Low Stress:</strong> Great! Keeping stress low allows your endocrine system to prioritize reproductive hormones.";
        }

        resultDiv.style.display = "block";
        resultDiv.style.backgroundColor = "#e8eaf6";
        resultDiv.style.color = "#1a237e";
        resultDiv.innerHTML = `
          <h4 style="margin-top:0; border-bottom: 1px solid #c5cae9; padding-bottom: 5px;">Your Hormone Optimization Blueprint</h4>
          <p style="margin-bottom:8px;">💤 ${sleepTip}</p>
          <p style="margin-bottom:8px;">🧘‍♂️ ${stressTip}</p>
          <p style="margin-bottom:0;"><strong>Actionable Diet Additions:</strong> Ensure adequate intake of Zinc (oysters, pumpkin seeds), Vitamin D (sunlight, supplements), and Magnesium (spinach, nuts).</p>
        `;
      }

      function calculateMaleHealth() {
        const age = parseInt(document.getElementById("male-age").value);
        const resultDiv = document.getElementById("male-health-result");

        if (!age || age < 18) {
            resultDiv.style.display = "block";
            resultDiv.style.backgroundColor = "#ffebee";
            resultDiv.style.color = "#c62828";
            resultDiv.innerHTML = "Please enter a valid age (18+).";
            return;
        }

        let checks = "<li>Blood Pressure & Cholesterol: Annually</li><li>Testicular Self-Exam: Monthly</li>";
        let dietFocus = "Lean proteins and fibrous vegetables. Limit processed sugars to prevent early insulin resistance.";

        if (age >= 30 && age < 45) {
          checks += "<li>Testosterone Check: Base line screening if feeling lethargic</li><li>Cardiovascular risk assessment: Every 3 years</li>";
          dietFocus = "Focus on Omega-3 fatty acids (Salmon, Walnuts) for heart health. Maintain an active metabolism.";
        } else if (age >= 45) {
          checks += "<li>Prostate-Specific Antigen (PSA) Test: Annually or bi-annually</li><li>Colonoscopy: Baseline at 45, then every 10 years</li><li>Comprehensive Heart Exam: Annually</li>";
          dietFocus = "Focus heavily on <strong>Lycopene</strong> (Cooked Tomatoes, Watermelon) for prostate health, and heart-healthy fats (Olive oil, Avocados).";
        }

        resultDiv.style.display = "block";
        resultDiv.style.backgroundColor = "#e1f5fe";
        resultDiv.style.color = "#01579b";
        resultDiv.innerHTML = `
          <h4 style="margin-top:0; border-bottom: 1px solid #b3e5fc; padding-bottom: 5px;">Health Milestones for Men (${age})</h4>
          <ul style="margin-bottom:10px; padding-left:20px;">
            ${checks}
          </ul>
          <p style="margin-bottom:0;"><strong>🍎 Nutrition Focus:</strong> ${dietFocus}</p>
        `;
      }


      function logMood() {
        const mood = document.getElementById("current-mood").value;
        const notes = document.getElementById("mood-notes").value;
        const resultDiv = document.getElementById("mood-result");

        if (!mood) {
          resultDiv.style.display = "block";
          resultDiv.style.backgroundColor = "#ffebee";
          resultDiv.style.color = "#c62828";
          resultDiv.innerHTML = "Please select a mood to log, sweetheart.";
          return;
        }

        let aiResponse = "";
        let bgColor = "#fce4ec";
        let textColor = "#880e4f";
        let buttonColor = "#e91e63";

        switch (mood) {
          case "Happy":
            aiResponse = "My dear friend, seeing you happy fills my heart with so much joy! Always keep smiling!";
            break;
          case "Calm":
            aiResponse = "That's wonderful, buddy. A calm heart brings peace. Rest well and keep this gentle energy.";
            break;
          case "Energetic":
            aiResponse = "Oh, look at you full of life! Use this beautiful energy to do something you love today!";
            break;
          case "Stressed":
            aiResponse = "Oh buddy, come here and take a deep breath. Everything will be okay. I am right here with you.";
            break;
          case "Tired":
            aiResponse = "You've worked so hard today, my dear. Have some water and lie down. Your health is the most important thing.";
            break;
          case "Sad":
            aiResponse = "Oh, my sweet friend, please don't be sad. Whatever is hurting you, it will pass. I am here for you.";
            break;
        }

        resultDiv.style.display = "block";
        resultDiv.style.backgroundColor = bgColor;
        resultDiv.style.color = textColor;

        const dateStr = new Date().toLocaleDateString();
        
        let htmlContent = `
          <div style="font-size:0.9em; margin-bottom:10px; border-bottom: 1px solid ${textColor}; padding-bottom: 5px;">
            <strong>${dateStr}</strong> - Logged: <strong>${mood}</strong>
          </div>
          <div style="display: flex; align-items: flex-start; gap: 15px; text-align: left; margin-top: 10px;">
            <div style="font-size: 2.5em; line-height: 1;">🤖</div>
            <div>
              <strong style="display: block; margin-bottom: 5px;">Your AI Buddy says:</strong>
              ${aiResponse}
            </div>
          </div>
        `;

        if (notes.trim() !== "") {
          htmlContent += `<div style="font-size: 0.9em; font-weight: normal; font-style: italic; margin-top: 15px; opacity: 0.9;"><strong>Your note:</strong> "${notes}"</div>`;
        }

        htmlContent += `
          <button onclick="openChatWithMood('${mood}')" style="margin-top: 15px; background-color: ${buttonColor}; color: white; padding: 8px 15px; font-size: 0.9em; border-radius: 20px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); border: none; cursor: pointer;">
            🤖 Talk to your AI Buddy
          </button>
        `;

        resultDiv.innerHTML = htmlContent;

        if (typeof speakResponse === "function") {
           speakResponse(aiResponse);
        }

        document.getElementById("current-mood").value = "";
        document.getElementById("mood-notes").value = "";
      }

      function openChatWithMood(mood) {
          document.body.classList.add("show-chatbot");
          setTimeout(() => {
              const message = `I just logged my mood as ${mood}. Can we talk?`;
              document.getElementById("chatInput").value = message;
              handleChat();
          }, 500);
      }

      function generateRoutine() {
        const goal = document.getElementById("routine-goal").value;
        const wakeTimeInput = document.getElementById("wake-time").value;
        const resultDiv = document.getElementById("routine-result");
        const errorDiv = document.getElementById("routine-error");

        resultDiv.style.display = "none";
        errorDiv.style.display = "none";

        if (!wakeTimeInput) {
          errorDiv.style.display = "block";
          errorDiv.style.backgroundColor = "#ffebee";
          errorDiv.style.color = "#c62828";
          errorDiv.innerHTML = "Please enter your usual wake-up time.";
          return;
        }

        let [hours, minutes] = wakeTimeInput.split(":").map(Number);

        const formatTime = (h, m) => {
          let ampm = h >= 12 ? "PM" : "AM";
          let hr12 = h % 12 || 12;
          let minStr = m < 10 ? "0" + m : m;
          return `${hr12}:${minStr} ${ampm}`;
        };

        const addTime = (h, m, hoursToAdd) => {
          let totalMinutes = m + hoursToAdd * 60;
          let newH = (h + Math.floor(totalMinutes / 60)) % 24;
          let newM = totalMinutes % 60;
          return formatTime(newH, newM);
        };

        let htmlContent = `
          <div class="ticket-header">
            <h3>🗓️ Your ${goal} Routine</h3>
            <p style="margin:0;">Optimized for a ${formatTime(hours, minutes)} start</p>
          </div>
          <div class="ticket-body">
        `;

        htmlContent += `<div class="ticket-detail"><span>${formatTime(hours, minutes)}:</span> Wake up & Hydrate (1-2 glasses of water)</div>`;

        if (goal === "Weight Loss") {
          htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 0.5)}:</span> 30-45 min Fasted Cardio (Brisk walk/Jog)</div>`;
          htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 1.5)}:</span> High-protein, low-carb breakfast</div>`;
        } else if (goal === "Muscle Gain") {
          htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 0.5)}:</span> Pre-workout snack & 60 min Strength Training</div>`;
          htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 2)}:</span> Post-workout recovery breakfast (Protein + Carbs)</div>`;
        } else {
          htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 0.5)}:</span> 15 min Light Stretching / Yoga / Meditation</div>`;
          htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 1)}:</span> Well-balanced breakfast</div>`;
        }

        htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 5)}:</span> Balanced Lunch & 10-minute walk</div>`;
        htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 9)}:</span> Afternoon snack (e.g., nuts, fruit) for energy</div>`;

        if (goal === "Better Sleep") {
          htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 12.5)}:</span> Light, easy-to-digest Dinner</div>`;
          htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 14)}:</span> Digital Sunset (No screens, read or relax)</div>`;
        } else {
          htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 13)}:</span> Dinner (High protein, moderate carbs)</div>`;
          htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 14.5)}:</span> Wind down & Evening relaxation</div>`;
        }

        htmlContent += `<div class="ticket-detail"><span>${addTime(hours, minutes, 15.5)}:</span> Target Bedtime (Aim for 8 hours of sleep)</div>`;

        htmlContent += `</div>`;

        resultDiv.innerHTML = htmlContent;
        resultDiv.style.display = "block";
      }

      function calculateBill() {
        let dietQty = parseInt(document.getElementById("diet-plan-qty").value) || 0;
        let workoutQty = parseInt(document.getElementById("workout-plan-qty").value) || 0;
        let resultDiv = document.getElementById("bill-result");

        if (dietQty <= 0 && workoutQty <= 0) {
          resultDiv.style.display = "block";
          resultDiv.style.backgroundColor = "#ffebee";
          resultDiv.style.color = "#c62828";
          resultDiv.innerHTML = "Please enter at least 1 session to calculate.";
          return;
        }

        let subtotal = dietQty * 799 + workoutQty * 1499;
        let cgst = subtotal * 0.09;
        let sgst = subtotal * 0.09;
        let grandTotal = subtotal + cgst + sgst;

        resultDiv.style.display = "block";
        resultDiv.style.backgroundColor = "#e8f5e9";
        resultDiv.style.color = "#2e7d32";

        resultDiv.innerHTML = `
          <div style="text-align: left; max-width: 250px; margin: 0 auto;">
            <p style="margin: 5px 0; display: flex; justify-content: space-between;">
              <span>Subtotal:</span> <span>₹${subtotal.toFixed(2)}</span>
            </p>
            <p style="margin: 5px 0; display: flex; justify-content: space-between;">
              <span>CGST (9%):</span> <span>₹${cgst.toFixed(2)}</span>
            </p>
            <p style="margin: 5px 0; display: flex; justify-content: space-between;">
              <span>SGST (9%):</span> <span>₹${sgst.toFixed(2)}</span>
            </p>
            <hr style="border: 0.5px solid #2e7d32;">
            <p style="margin: 5px 0; display: flex; justify-content: space-between; font-size: 1.2em;">
              <strong>Grand Total:</strong> <strong>₹${grandTotal.toFixed(2)}</strong>
            </p>
          </div>
        `;
      }

      function handleRegistration(event) {
        event.preventDefault();
        
        const btn = document.getElementById("regSubmitBtn");
        const resultDiv = document.getElementById("reg-result");

        btn.innerText = "Processing Details...";
        btn.disabled = true;

        const newMember = {
          name: document.getElementById("reg-name").value,
          email: document.getElementById("reg-email").value,
          phone: document.getElementById("reg-phone").value,
          dob: document.getElementById("reg-dob").value,
          gender: document.getElementById("reg-gender").value,
          address: document.getElementById("reg-address").value,
          registrationDate: new Date().toISOString()
        };

        let existingMembers = JSON.parse(localStorage.getItem("healthAppMembers")) || [];
        existingMembers.push(newMember);
        localStorage.setItem("healthAppMembers", JSON.stringify(existingMembers));

        let adminMessages = JSON.parse(localStorage.getItem("adminMessages")) || [];
        adminMessages.push({
          id: Date.now(),
          type: "New Registration",
          name: newMember.name,
          phone: newMember.phone,
          email: newMember.email,
          date: new Date().toLocaleString()
        });
        localStorage.setItem("adminMessages", JSON.stringify(adminMessages));

        setTimeout(() => {
          resultDiv.style.display = "block";
          resultDiv.style.backgroundColor = "#e8f5e9";
          resultDiv.style.color = "#2e7d32";
          resultDiv.innerHTML = "✅ Registration Successful! Welcome to the Health & Nutrition program. Our team will review your ID and contact you shortly.";

          document.getElementById("registrationForm").reset();
          
          btn.innerText = "Submit Registration";
          btn.disabled = false;
        }, 1500);
      }

      function downloadReceipt() {
        const element = document.getElementById('bookingTicketContent');
        
        const opt = {
          margin:       0.5,
          filename:     'Health_Consultation_Receipt.pdf',
          image:        { type: 'jpeg', quality: 0.98 },
          html2canvas:  { scale: 2, useCORS: true, backgroundColor: '#ffffff' },
          jsPDF:        { unit: 'in', format: 'letter', orientation: 'portrait' }
        };
        
        html2pdf().set(opt).from(element).save();
      }

      function bookSession() {
        let name = document.getElementById("session-name").value;
        let type = document.getElementById("session-type").value;
        let date = document.getElementById("session-date").value;     
        let time = document.getElementById("session-time").value;
        let resultDiv = document.getElementById("session-result");
        let btn = document.getElementById("submitBookingBtn");

        if (name === "" || type === "" || date === "" || time === "") {
          resultDiv.style.display = "block";
          resultDiv.style.backgroundColor = "#ffebee";
          resultDiv.style.color = "#c62828";
          resultDiv.innerHTML = "⚠️ Please fill in all the details to book your session.";
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
              resultDiv.style.backgroundColor = "transparent";
              resultDiv.innerHTML = `
                  <div class="booking-ticket" id="bookingTicketContent" style="background-color:#e8f5e9; padding: 20px; border-radius: 8px;">
                    <div class="ticket-header" style="border-bottom: 2px dashed #2e7d32; padding-bottom: 10px; margin-bottom: 15px;">
                      <h3 style="color:#2e7d32; margin:0 0 10px 0; text-align:center;">🩺 Session Confirmed</h3>
                      <p style="margin:0; text-align:center;">Appointment ID: <strong>${sessionId}</strong></p>
                    </div>
                    <div class="ticket-body" style="font-size: 16px;">
                      <div style="margin-bottom: 8px;"><strong>Patient Name:</strong> ${name}</div>
                      <div style="margin-bottom: 8px;"><strong>Consultation:</strong> ${type}</div>
                      <div style="margin-bottom: 8px;"><strong>Date:</strong> ${date}</div>
                      <div style="margin-bottom: 8px;"><strong>Time:</strong> ${time}</div>
                    </div>
                    <div class="ticket-footer" style="margin-top: 20px; font-style: italic; font-size: 14px; text-align: center; color: #555;">
                      Thank you for prioritizing your health! Your details have been sent to our team. 🍏
                    </div>
                  </div>
                  <button onclick="downloadReceipt()" style="margin-top: 15px; background-color: #1976d2; color: white; padding: 10px; border: none; border-radius: 6px; cursor: pointer;">📥 Download PDF Receipt</button>
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
              alert("Failed to send the booking email. Please check your Console for errors or verify your EmailJS keys.");
              btn.innerText = "Confirm Appointment";
              btn.disabled = false;
            },
          );
      }

      const MY_GOOGLE_MEET_LINK = "https://meet.google.com/fem-kqty-enc";

      function startVideoCall() {
        const passwordInput = document.getElementById("call-password-input").value;
        if (passwordInput !== "Sahil@1925") {
          alert("Access Denied: Incorrect Meeting Password.");
          return;
        }

        const setupDiv = document.getElementById("call-setup");
        const videoInterface = document.getElementById("video-interface");
        const callStatus = document.getElementById("call-status");

        const expertSelect = document.getElementById("expert-select");
        const expertName = expertSelect.options[expertSelect.selectedIndex].text.split(" (")[0];

        setupDiv.style.display = "none";
        videoInterface.style.display = "block";
        callStatus.innerHTML = `Meeting with <strong>${expertName}</strong> opening in a new tab...<br><br><small style="font-size: 0.8em; font-weight: normal; color: #555;">If it didn't open automatically, <a href="${MY_GOOGLE_MEET_LINK}" target="_blank" style="color: var(--primary-color);">click here</a>.</small>`;

        window.open(MY_GOOGLE_MEET_LINK, "_blank");
      }

      function endVideoCall() {
        document.getElementById("video-interface").style.display = "none";
        document.getElementById("call-setup").style.display = "block";
        document.getElementById("call-password-input").value = "";
      }

      function notifyExpert() {
        const expertSelect = document.getElementById("expert-select");
        const expertPhone = expertSelect.value;
        const patientName = document.getElementById("patient-name-input").value || "Patient";

        const message = `Hello Expert, I am ${patientName}. I am ready for our live video consultation on the Health Portal.\n\n📍 *Please join the Google Meet room here:*\n${MY_GOOGLE_MEET_LINK}`;
        const whatsappUrl = `https://wa.me/91${expertPhone}?text=${encodeURIComponent(message)}`;

        window.open(whatsappUrl, "_blank");
      }


      /* =========================================
         ADVANCED AI CHATBOT LOGIC
         ========================================= */
      const chatbotToggler = document.getElementById("chatbotToggler");
      const closeChatBtn = document.getElementById("closeChat");
      const chatBox = document.getElementById("chatBox");
      const chatInput = document.getElementById("chatInput");
      const sendChatBtn = document.getElementById("sendChatBtn");
      const micBtn = document.getElementById("micBtn");
      const chatStatus = document.getElementById("chatStatus");

      let userName = ""; // Memory to remember the user's name

      chatbotToggler.addEventListener("click", () => document.body.classList.toggle("show-chatbot"));
      closeChatBtn.addEventListener("click", () => document.body.classList.remove("show-chatbot"));

      // Function to get time-based greeting
      function getTimeGreeting() {
        const hour = new Date().getHours();
        if (hour < 12) return "Good morning";
        if (hour < 18) return "Good afternoon";
        return "Good evening";
      }

      // Enhanced Friendly Dual-Language Dictionary with Arrays for Randomized Responses
      const botResponses = {
        "overwhelmed": [
          "Oh honey, it is completely normal to feel overwhelmed. घबराने की कोई बात नहीं है। Take a deep breath. We will figure this out together. What is bothering you?",
          "I hear you, my dear. Sometimes everything just feels like too much. Come sit with me. Let's tackle it one step at a time."
        ],
        "stress": [
          "Stress is so hard on your beautiful body. तनाव तुम्हारी सेहत के लिए अच्छा नहीं है। Would you like to talk about what's causing it?",
          "I can feel the tension in your words. Please remember to pause and breathe. You are stronger than whatever is stressing you right now."
        ],
        "sad": [
          "Oh, my sweet friend, please don't cry. मेरे प्यारे बच्चे, उदास मत हो। I am sending you a big warm virtual hug. It will be okay.",
          "I'm so sorry you're feeling down. I am right here for you. Do you want to talk about what made you sad?"
        ],
        "उदास": [
          "मेरे प्यारे दोस्त, उदास मत हो। मैं हमेशा तुम्हारी बात सुनने के लिए यहाँ हूँ। सब ठीक हो जाएगा।"
        ],
        "happy": [
          "Seeing you happy makes me the happiest! तुम्हें खुश देखकर मैं बहुत खुश हूँ! Tell me all about what's making you smile!",
          "That is wonderful news! It is so good to feel that joyful energy. Share your joy with me!"
        ],
        "diet": [
          "Eating right is an act of self-love! Remember to include lots of colorful veggies and stay hydrated. Need a specific diet plan? Our experts can help!",
          "A healthy diet nourishes both the body and the mind. Try to focus on whole grains and lean proteins today. You can calculate your TDEE above!"
        ],
        "water": [
          "Hydration is key! You should drink about 35ml of water per kg of body weight. Have you had a glass of water recently?",
          "Water flushes out toxins and keeps your skin glowing. Go grab a glass of water right now, I'll wait!"
        ],
        "sleep": [
          "Your brain needs rest to heal. Try to get 7-8 hours of sleep tonight, and turn off your screens an hour before bed. Sweet dreams!",
          "A good routine always includes deep sleep. If you're having trouble sleeping, try some light stretching or meditation."
        ],
        "workout": [
          "Movement is medicine! Even a 20-minute walk can do wonders for your physical and mental health.",
          "Exercise releases happy hormones! If you need a proper routine, you can use our Smart Routine Maker above."
        ],
        "motivation": [
          "It's okay if you're tired today, my love. Just take a tiny step. I am so proud of you already.",
          "You don't have to be perfect, you just have to keep trying. I believe in you completely!"
        ],
        "bmi": [
          "BMI is just a number! It does not define how wonderful you are. You can check it in the BMI section above.",
          "You can calculate your BMI on this page, but remember, true health is about how you feel, not just a number on a scale."
        ],
        "period": [
          "Heat pads and warm chamomile tea can do wonders for period cramps! Make sure you are resting. Do you need a consultation with our Gynecologist, Dr. Shalini?",
          "I'm sorry you're in pain, honey. Gentle stretches and staying hydrated can help with menstrual discomfort. Use the Cycle Syncing tool above to see what foods might help today!"
        ],
        "cramps": [
          "Heat pads and warm chamomile tea can do wonders for period cramps! Make sure you are resting.",
          "I'm sorry you're in pain, honey. Gentle stretches and staying hydrated can help with menstrual discomfort. Take it easy today!"
        ],
        "pcos": [
          "PCOS can be tough to manage, but diet and lifestyle changes make a huge difference. Focus on anti-inflammatory foods and stable blood sugar. Dr. Shalini is an expert in this area if you need to talk to someone!",
          "I hear you. Managing PCOS requires patience. Focusing on protein, healthy fats, and stress reduction can really help balance those hormones."
        ],
        "iron": [
          "Iron is so important for women's health! Spinach, lentils, and red meat are great sources. Did you check out our new Mineral Calculator?",
          "If you are feeling fatigued, you might need more iron. Make sure you pair iron-rich foods with Vitamin C (like lemon or tomatoes) to absorb it better!"
        ],
        "bloating": [
          "Bloating is very common, especially during the luteal phase of your cycle. Peppermint tea and avoiding excess salt might give you some relief.",
          "I know bloating is uncomfortable. Try a gentle walk and drink plenty of water. It helps flush out excess sodium!"
        ],
        "hello": [
          "Hello there! नमस्ते! How can I help you today?",
          "Hi! So good to see you. How are you feeling today?"
        ],
        "hi": [
          "Hi there! How is your day going?",
          "Hello! I am ready to listen if you need to talk."
        ]
      };

      let availableVoices = [];
      function populateVoices() {
        availableVoices = window.speechSynthesis.getVoices();
      }
      populateVoices();
      if (speechSynthesis.onvoiceschanged !== undefined) {
        speechSynthesis.onvoiceschanged = populateVoices;
      }

      const speakResponse = (text) => {
        if (!('speechSynthesis' in window)) return;
        const cleanText = text.replace(/<[^>]*>?/gm, ''); // strip HTML
        const utterance = new SpeechSynthesisUtterance(cleanText);

        let femaleVoice = availableVoices.find(voice => 
          (voice.lang.includes('hi-IN') || voice.lang.includes('en-IN')) && 
          (voice.name.includes('Female') || voice.name.includes('Google हिन्दी') || voice.name.includes('Swara') || voice.name.includes('Aditi'))
        );

        if (!femaleVoice) femaleVoice = availableVoices.find(v => v.lang.includes('hi-IN'));
        if (!femaleVoice) femaleVoice = availableVoices.find(v => v.name.includes('Female') || v.name.includes('Zira') || v.name.includes('Samantha'));

        if (femaleVoice) {
          utterance.voice = femaleVoice;
          utterance.lang = femaleVoice.lang;
        } else {
          utterance.lang = 'en-IN'; 
        }

        utterance.pitch = 1.0; 
        utterance.rate = 1.0; // Slower or Faster the Speed, more comforting
        window.speechSynthesis.speak(utterance);
      };

      const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
      if (SpeechRecognition) {
        const recognition = new SpeechRecognition();
        recognition.continuous = false;
        recognition.interimResults = false;
        recognition.lang = 'en-IN'; 

        recognition.onstart = () => {
          micBtn.classList.add('listening');
          chatStatus.classList.add('active');
          window.speechSynthesis.cancel(); 
        };

        recognition.onresult = (event) => {
          const transcript = event.results[0][0].transcript;
          chatInput.value = transcript;
          handleChat();
        };

        recognition.onerror = (event) => {
          console.error("Speech recognition error", event.error);
          micBtn.classList.remove('listening');
          chatStatus.classList.remove('active');
        };

        recognition.onend = () => {
          micBtn.classList.remove('listening');
          chatStatus.classList.remove('active');
        };

        micBtn.addEventListener('click', () => {
          if (micBtn.classList.contains('listening')) {
            recognition.stop();
          } else {
            recognition.start();
          }
        });
      } else {
        micBtn.style.display = "none";
        console.log("Speech Recognition not supported in this browser.");
      }

      const createChatLi = (message, className) => {
        const chatElement = document.createElement("div");
        chatElement.classList.add("message", className);
        chatElement.innerHTML = message;
        return chatElement;
      };

      const showTypingIndicator = () => {
        const typingHTML = `
          <div class="dot"></div>
          <div class="dot"></div>
          <div class="dot"></div>
        `;
        const typingElement = document.createElement("div");
        typingElement.classList.add("typing-indicator");
        typingElement.id = "typingIndicator";
        typingElement.innerHTML = typingHTML;
        chatBox.appendChild(typingElement);
        chatBox.scrollTo(0, chatBox.scrollHeight);
      };

      const removeTypingIndicator = () => {
        const indicator = document.getElementById("typingIndicator");
        if (indicator) indicator.remove();
      };

      const generateResponse = (userMessage) => {
        const lowerCaseMsg = userMessage.toLowerCase();
        let response = "";
        
        // 1. Name Memory Checking
        if (lowerCaseMsg.includes("my name is ") || lowerCaseMsg.includes("i am ")) {
          const words = lowerCaseMsg.split(" ");
          // Extract the last word as the name
          userName = words[words.length - 1].charAt(0).toUpperCase() + words[words.length - 1].slice(1);
          response = `It is so lovely to meet you, ${userName}! How can I help you feel your best today?`;
        } 
        else {
          // 2. Keyword Matching
          let foundMatch = false;
          for (let key in botResponses) {
            if (lowerCaseMsg.includes(key)) {
              // Pick a random response from the array
              const responseArray = botResponses[key];
              response = responseArray[Math.floor(Math.random() * responseArray.length)];
              foundMatch = true;
              break;
            }
          }

          // 3. Default Fallback
          if (!foundMatch) {
            const defaults = [
              "Thank you for sharing that with me. I'm always here cheering for you.",
              "I see. Could you tell me a little bit more about that?",
              "I'm just an AI, but I care about your well-being. How does that make you feel?",
              "For specific medical advice, please <a href='#book-session'>book a consultation</a> with our experts. But I am always here to listen!"
            ];
            response = defaults[Math.floor(Math.random() * defaults.length)];
          }
        }

        // Add user's name if we know it and it's not already in the string
        if (userName && !response.includes(userName) && Math.random() > 0.5) {
            response = response.replace("my dear", userName).replace("friend", userName);
        }

        showTypingIndicator();

        // Calculate a smart delay based on how long the bot's response is (feels more human)
        const delay = Math.min(Math.max(1000, response.length * 25), 3000);

        setTimeout(() => {
          removeTypingIndicator();
          chatBox.appendChild(createChatLi(response, "bot"));
          chatBox.scrollTo(0, chatBox.scrollHeight);
          
          speakResponse(response);
        }, delay);
      };

      const handleChat = (message = null) => {
        const userMessage = message || chatInput.value.trim();
        if (!userMessage) return;

        chatInput.value = "";
        chatBox.appendChild(createChatLi(userMessage, "user"));
        chatBox.scrollTo(0, chatBox.scrollHeight);

        generateResponse(userMessage);
      };

      const sendQuickReply = (text) => {
        handleChat(text);
      };

      sendChatBtn.addEventListener("click", () => handleChat());
      chatInput.addEventListener("keydown", (e) => {
        if (e.key === "Enter") {
          e.preventDefault();
          handleChat();
        }
      });
    </script>
  </body>
</html>
