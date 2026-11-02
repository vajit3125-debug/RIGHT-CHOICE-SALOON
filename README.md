# RIGHT-CHOICE-SALOON
import React, { useState } from "react";
import "./App.css";

function App() {
  const [name, setName] = useState("");
  const [phone, setPhone] = useState("");
  const [service, setService] = useState("Haircut");
  const [date, setDate] = useState("");
  const [message, setMessage] = useState("");

  function bookAppointment(e) {
    e.preventDefault();

    setMessage(
      Thank you ${name}! Your ${service} appointment is requested for ${date}. We will contact you at ${phone}.
    );
  }

  return (
    <div className="app">
      <header>
        <h1>RIGHT CHOICE SALOON</h1>
        <p>Your Style, Our Responsibility</p>
        <nav>
          <a href="#home">Home</a>
          <a href="#services">Services</a>
          <a href="#booking">Booking</a>
        </nav>
      </header>

      <section id="home" className="hero">
        <h2>Look Smart. Feel Confident.</h2>
        <p>
          Welcome to Right Choice Saloon.
          Experience the best grooming and styling.
        </p>
        <a className="btn" href="#booking">
          Book Appointment
        </a>
      </section>

      <section id="services">
        <h2>Our Services</h2>
        <div className="services">
          <div className="service">
            <h3>Haircut</h3>
            <p>₹150</p>
          </div>
          <div className="service">
            <h3>Hair Styling</h3>
            <p>₹200</p>
          </div>
          <div className="service">
            <h3>Beard Trimming</h3>
            <p>₹100</p>
          </div>
          <div className="service">
            <h3>Facial</h3>
            <p>₹400</p>
          </div>
        </div>
      </section>

      <section id="booking">
        <h2>Book Your Appointment</h2>

        <form onSubmit={bookAppointment}>
          <input
            type="text"
            placeholder="Enter Your Name"
            value={name}
            onChange={(e) => setName(e.target.value)}
            required
          />

          <input
            type="tel"
            placeholder="Enter Mobile Number"
            value={phone}
            onChange={(e) => setPhone(e.target.value)}
            pattern="[0-9]{10}"
            required
          />

          <select
            value={service}
            onChange={(e) => setService(e.target.value)}
          >
            <option>Haircut</option>
            <option>Hair Styling</option>
            <option>Beard Trimming</option>
            <option>Facial</option>
          </select>

          <input
            type="date"
            value={date}
            onChange={(e) => setDate(e.target.value)}
            min={new Date().toLocaleDateString("en-CA")}
            required
          />

          <button type="submit">Book Now</button>
        </form>

        {message && <p className="success">{message}</p>}
      </section>

      <footer>
        <p>© 2026 RIGHT CHOICE SALOON</p>
        <p>Thank You For Visiting Us!</p>
      </footer>
    </div>
  );
}

export default App;
