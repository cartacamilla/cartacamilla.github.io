---
layout: default
title: Contact
permalink: /contact/
---
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="{{ "./css/styles.css" | relative_url }}">
  <title>Contact</title>
  
</head>
<body>
  <header>
    <h1>Contact Me!</h1>
  </header>
  <section>
    <p>I'd love to hear from you!</p>
    <p>Feel free to reach out with any questions or project inquiries.</p>
    <form action="https://formspree.io/f/xvggpkvz" method="POST">
      <label for="name">Name:</label>
      <input type="text" id="name" name="name" required>
      <label for="email">Email:</label>
      <input type="email" id="email" name="email" required>
      <label for="message">Message:</label>
      <textarea id="message" name="message" required></textarea>
      <button type="submit">Send</button>
    </form>
  </section>
</body>
</html>
