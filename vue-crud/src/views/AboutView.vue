<template>
  <div class="about">
    <div class="container">
      <h1>This is an About Page</h1>
      <p>Welcome to the about page. Here you can learn more about us and what we do.</p>
    </div>
  </div>
</template>

<style>
/* Global Styles */
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  color: #333;
}

.about {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

.container {
  text-align: center;
  background: #fff;
  padding: 40px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Header Styles */
h1 {
  font-size: 2.5rem;
  margin-bottom: 20px;
  color: #333;
}

/* Paragraph Styles */
p {
  font-size: 1.125rem;
  line-height: 1.6;
  color: #666;
}

/* Media Queries */
@media (max-width: 1024px) {
  .container {
    padding: 30px;
  }
  
  h1 {
    font-size: 2rem;
  }
  
  p {
    font-size: 1rem;
  }
}

@media (max-width: 768px) {
  .about {
    padding: 10px;
  }
  
  .container {
    padding: 20px;
  }
  
  h1 {
    font-size: 1.75rem;
  }
  
  p {
    font-size: 0.875rem;
  }
}

@media (max-width: 480px) {
  h1 {
    font-size: 1.5rem;
  }
  
  p {
    font-size: 0.75rem;
  }
}
</style>
  