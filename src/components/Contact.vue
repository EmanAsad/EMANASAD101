<template>
  <section id="contact" class="section contact">
    <div class="container">
      <div class="contact-content">
        <h2 class="section-title fade-in">Let's Connect</h2>
        <p class="fade-in description">
          I'm always excited to discuss new opportunities, collaborate on innovative projects, 
          or simply connect with fellow tech enthusiasts. Let's build something amazing together!
        </p>

        <div class="contact-links">
          <a href="mailto:emanasad@example.com" class="contact-link fade-in">
            <i class="fas fa-envelope"></i> Email Me
          </a>
          <a href="tel:+923253828772" class="contact-link fade-in">
            <i class="fas fa-phone"></i> Call Me
          </a>
          <a href="https://github.com/EmanAsad" class="contact-link fade-in" target="_blank">
            <i class="fab fa-github"></i> GitHub
          </a>
          <a href="https://emanasad.github.io/EMANASAD/" class="contact-link fade-in" target="_blank">
            <i class="fas fa-globe"></i> Website
          </a>
          <a href="#" class="contact-link fade-in">
            <i class="fab fa-linkedin"></i> LinkedIn
          </a>
        </div>

        <div class="location-box fade-in">
          <h4><i class="fas fa-map-marker-alt"></i> Location</h4>
          <p>H13, Islamabad, Pakistan</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// No script logic needed for this component
</script>

<style scoped>
.section {
  padding: 4rem 2rem;
}

.contact-content {
  text-align: center;
}

.section-title {
  font-size: 2.5rem;
  color: var(--primary-color);
  margin-bottom: 1rem;
}

.description {
  font-size: 1.2rem;
  color: var(--text-secondary);
  margin-bottom: 2rem;
}

.contact-links {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 3rem;
}

.contact-link {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 1.1rem;
  padding: 0.75rem 1.5rem;
  background: var(--primary-color);
  color: white;
  text-decoration: none;
  border-radius: 8px;
  transition: background 0.3s;
}

.contact-link:hover {
  background: var(--button-color);
  color: var(--text-primary);
}

.location-box {
  background: white;
  padding: 2rem;
  border-radius: 15px;
  box-shadow: var(--shadow);
  color: var(--text-secondary);
}

.location-box h4 {
  color: var(--primary-color);
  margin-bottom: 0.5rem;
  font-size: 1.25rem;
}

/* Simple fade-in animation */
.fade-in {
  opacity: 0;
  animation: fadeIn 1s ease-in forwards;
}

@keyframes fadeIn {
  to {
    opacity: 1;
  }
}
</style>
