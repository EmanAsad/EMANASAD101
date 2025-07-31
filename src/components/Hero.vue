<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <div class="text-section">
          <h1 class="name fade-in">Eman Asad</h1>
          <p class="job-title fade-in">MERN Stack Developer & AI Enthusiast</p>
          <p class="description fade-in">
            Passionate developer crafting modern web apps & intelligent solutions through the MERN stack & AI technologies.
          </p>
          <div class="social-links fade-in">
            <a href="https://github.com/yourgithub" target="_blank" class="social-icon">
              <i class="fab fa-github"></i>
            </a>
            <a href="https://linkedin.com/in/yourlinkedin" target="_blank" class="social-icon">
              <i class="fab fa-linkedin"></i>
            </a>
            <a href="mailto:youremail@example.com" target="_blank" class="social-icon">
              <i class="fas fa-envelope"></i>
            </a>
          </div>
          <a href="#contact" class="btn fade-in">Contact Me</a>
        </div>

        <div class="image-section fade-in">
          <img :src="heroImage" alt="Hero Image" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import heroImage from '@/assets/hero-img.png'

export default {
  name: 'Hero',
  data() {
    return {
      heroImage
    }
  }
}
</script>

<style scoped lang="scss">
@use "@/assets/styles/variables.scss" as *;

.hero {
  padding: 6rem 0;
  background: var(--bg-primary);
  color: var(--text-primary);
}

.hero-content {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 2rem;
}

.text-section {
  flex: 1 1 400px;

  .name {
    font-size: 3rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
  }

  .job-title {
    font-size: 1.5rem;
    font-weight: 500;
    margin-bottom: 1rem;
    color: var(--text-secondary);
  }

  .description {
    font-size: 1.125rem;
    line-height: 1.6;
    margin-bottom: 1.5rem;
  }

  .social-links {
    display: flex;
    gap: 1rem;
    margin-bottom: 1.5rem;

    .social-icon {
      font-size: 1.5rem;
      color: var(--text-primary);
      transition: color 0.3s ease;

      &:hover {
        color: var(--primary-color);
      }
    }
  }

  .btn {
    padding: 0.75rem 2rem;
    background: var(--primary-color);
    color: white;
    border: none;
    border-radius: 0.5rem;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.3s ease;

    &:hover {
      background: var(--secondary-color);
    }
  }
}

.image-section {
  flex: 1 1 400px;
  text-align: center;

  img {
    max-width: 100%;
    border-radius: 1rem;
  }
}
</style>
