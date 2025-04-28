# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!

---

## 🎉 Now Go Make It Fun!

Remember – this isn't just code. It's your **first step toward creating magical user experiences**. So play around, break stuff (then fix it), and most of all, have FUN! 😄

Happy Coding! 💻✨  
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>JavaScript Event Handling & Interactive Elements</title>
  <link rel="stylesheet" href="style.css"> <!-- Link to the CSS file -->
</head>
<body>

  <!-- Button Section -->
  <button id="clickButton">Click Me!</button>
  <button id="hoverButton">Hover Over Me!</button>
  <button id="secretButton">Double Click or Long Press Me!</button>

  <p id="clickMessage"></p>

  <!-- Image Gallery Section -->
  <div id="imageGallery">
    <img id="galleryImage" src="image1.jpg" alt="Image Gallery">
    <button id="nextImageButton">Next Image</button>
  </div>

  <!-- Form Section -->
  <form id="myForm">
    <input type="text" id="requiredField" placeholder="Enter something..." required>
    <input type="email" id="emailField" placeholder="Enter your email" required>
    <input type="password" id="passwordField" placeholder="Enter a password" required>
    <button type="submit">Submit</button>
  </form>

  <script src="script.js"></script> <!-- Link to the JavaScript file -->
</body>
</html>
/* style.css */
button {
  padding: 10px;
  margin: 10px;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background-color: lightblue;
}

button:active {
  background-color: lightgreen;
}

#galleryImage {
  width: 300px;
  height: auto;
  display: block;
  margin-bottom: 10px;
}
// script.js
// 1. Event Handling

// Button click
document.getElementById('clickButton').addEventListener('click', function() {
  document.getElementById('clickMessage').innerText = 'You clicked the button!';
});

// Hover effect
document.getElementById('hoverButton').addEventListener('mouseover', function() {
  this.style.backgroundColor = 'lightblue';
});
document.getElementById('hoverButton').addEventListener('mouseout', function() {
  this.style.backgroundColor = '';
});

// Keypress detection
document.addEventListener('keypress', function(event) {
  document.getElementById('clickMessage').innerText = `You pressed: ${event.key}`;
});

// Secret action for double-click or long press
let pressTimer;
document.getElementById('secretButton').addEventListener('mousedown', function() {
  pressTimer = setTimeout(function() {
    alert('You performed a long press!');
  }, 1000);
});

document.getElementById('secretButton').addEventListener('dblclick', function() {
  alert('You double-clicked!');
});

document.getElementById('secretButton').addEventListener('mouseup', function() {
  clearTimeout(pressTimer);
});

// 2. Interactive Elements

// Button that changes text or color
document.getElementById('clickButton').addEventListener('click', function() {
  this.innerText = 'You changed the button text!';
  this.style.backgroundColor = 'yellow';
});

// Image Gallery
let currentImage = 1;
document.getElementById('nextImageButton').addEventListener('click', function() {
  currentImage++;
  if (currentImage > 3) currentImage = 1;
  document.getElementById('galleryImage').src = `image${currentImage}.jpg`;
});

// 3. Form Validation

// Required field check
document.getElementById('myForm').addEventListener('submit', function(event) {
  if (document.getElementById('requiredField').value === '') {
    alert('Required field is empty!');
    event.preventDefault();
  }
});

// Email validation
document.getElementById('myForm').addEventListener('submit', function(event) {
  let email = document.getElementById('emailField').value;
  let emailPattern = /^[^@]+@[^@]+\.[^@]+$/;
  if (!emailPattern.test(email)) {
    alert('Please enter a valid email address!');
    event.preventDefault();
  }
});

// Password rules check (min 8 characters)
document.getElementById('myForm').addEventListener('submit', function(event) {
  let password = document.getElementById('passwordField').value;
  if (password.length < 8) {
    alert('Password must be at least 8 characters!');
    event.preventDefault();
  }
});

// Bonus: Real-time password feedback
document.getElementById('passwordField').addEventListener('input', function() {
  let feedback = document.getElementById('passwordFeedback');
  if (this.value.length >= 8) {
    feedback.innerText = 'Strong password';
    feedback.style.color = 'green';
  } else {
    feedback.innerText = 'Password too short';
    feedback.style.color = 'red';
  }
});
