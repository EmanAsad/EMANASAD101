<template>
  <section id="about" class="section">
    <div class="container">
      <div class="section-header">
        <h2 class="heading-2 text-center">About Me</h2>
        <p class="text-center text-secondary mb-4">
          Get to know more about who I am, what I do, and my current skills
        </p>
      </div>

      <div class="about-content">
        <div class="about-text">
          <div class="about-intro">
            <h3 class="heading-3 mb-2">Frontend Developer & Problem Solver</h3>
            <p class="mb-3">
              I'm a passionate frontend developer with {{ yearsOfExperience }} year of experience creating 
              engaging and responsive web applications. I love turning complex problems into simple, 
              beautiful, and intuitive designs.
            </p>
            <p class="mb-3">
              My journey in web development started with curiosity about how websites work, and it has 
              evolved into a deep passion for creating exceptional user experiences. I believe that 
              great design is not just about how it looks, but how it works.
            </p>
            <p class="mb-4">
              When I'm not coding, you'll find me exploring new technologies, contributing to open-source 
              projects, or sharing knowledge with the developer community through blog posts and mentoring.
            </p>
          </div>

          <div class="about-highlights">
            <div class="highlight-grid">
              <div class="highlight-item" v-for="highlight in highlights" :key="highlight.id">
                <div class="highlight-icon">
                  <i :class="highlight.icon"></i>
                </div>
                <div class="highlight-content">
                  <h4>{{ highlight.title }}</h4>
                  <p>{{ highlight.description }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="about-stats">
          <div class="stats-grid">
            <div class="stat-item" v-for="stat in stats" :key="stat.id">
              <div class="stat-number">
                <span ref="statNumbers">{{ displayedStats[stat.id] || 0 }}</span>
                <span class="stat-suffix">{{ stat.suffix }}</span>
              </div>
              <div class="stat-label">{{ stat.label }}</div>
            </div>
          </div>

          <div class="about-cta">
            <p class="mb-3">
              Interested in working together? Let's discuss your next project.
            </p>
            <div class="cta-buttons">
              <a href="#contact" class="btn primary">
                <i class="fas fa-paper-plane"></i>
                Let's Talk
              </a>
              <a href="/src/assets/Eman Asad.pdf" target="_blank" class="btn secondary" download>
                <i class="fas fa-download"></i>
                Download CV
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'About',
  data() {
    return {
      yearsOfExperience: new Date().getFullYear() - 2024, // Started in 2020
      displayedStats: {},
      highlights: [
        {
          id: 1,
          icon: 'fas fa-code',
          title: 'Clean Code',
          description: 'Writing maintainable, scalable, and well-documented code following best practices.'
        },
        {
          id: 2,
          icon: 'fas fa-mobile-alt',
          title: 'Responsive Design',
          description: 'Creating seamless experiences across all devices and screen sizes.'
        },
        {
          id: 3,
          icon: 'fas fa-rocket',
          title: 'Performance',
          description: 'Optimizing applications for speed, accessibility, and user experience.'
        },
        {
          id: 4,
          icon: 'fas fa-users',
          title: 'Collaboration',
          description: 'Working effectively with designers, developers, and stakeholders.'
        }
      ],
      stats: [
        { id: 'projects', number: 50, suffix: '+', label: 'Projects Completed' },
        { id: 'clients', number: 25, suffix: '+', label: 'Happy Clients' },
        { id: 'experience', number: this.yearsOfExperience, suffix: '+', label: 'Years Experience' },
        { id: 'technologies', number: 15, suffix: '+', label: 'Technologies' }
      ]
    }
  },
  mounted() {
    this.observeStats()
  },
  methods: {
    observeStats() {
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach(entry => {
            if (entry.isIntersecting) {
              this.animateStats()
              observer.unobserve(entry.target)
            }
          })
        },
        { threshold: 0.5 }
      )

      const statsSection = this.$el.querySelector('.stats-grid')
      if (statsSection) {
        observer.observe(statsSection)
      }
    },
    animateStats() {
      this.stats.forEach(stat => {
        this.animateNumber(stat.id, 0, stat.number, 2000)
      })
    },
    animateNumber(statId, start, end, duration) {
      const range = end - start
      const startTime = Date.now()
      
      const timer = setInterval(() => {
        const elapsed = Date.now() - startTime
        const progress = Math.min(elapsed / duration, 1)
        
        // Easing function for smooth animation
        const easedProgress = progress < 0.5 
          ? 2 * progress * progress 
          : -1 + (4 - 2 * progress) * progress
        
        const current = Math.floor(start + (range * easedProgress))
        this.$set(this.displayedStats, statId, current)
        
        if (progress >= 1) {
          clearInterval(timer)
          this.$set(this.displayedStats, statId, end)
        }
      }, 16) // ~60fps
    }
  }
}
</script>

<style scoped lang="scss">
@use "@/assets/styles/variables.scss" as *;

.section {
  padding: 6rem 0;
  background: var(--bg-secondary);
}

.section-header {
  margin-bottom: 4rem;
}

.about-content {
  display: grid;
  grid-template-columns: 1fr;
  gap: 4rem;
  align-items: start;

  @media (min-width: 1024px) {
    grid-template-columns: 1fr 400px;
    gap: 6rem;
  }
}

.about-text {
  .about-intro {
    font-size: 1.125rem;
    line-height: 1.7;
    color: var(--text-secondary);
  }
}

.highlight-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5rem;
  margin-top: 3rem;

  @media (min-width: 768px) {
    grid-template-columns: repeat(2, 1fr);
  }
}

.highlight-item {
  display: flex;
  gap: 1rem;
  padding: 1.5rem;
  background: white;
  border-radius: 0.75rem;
  box-shadow: var(--shadow);
  transition: transform 0.3s ease;

  &:hover {
    transform: translateY(-5px);
  }
}

.highlight-icon {
  flex-shrink: 0;
  width: 50px;
  height: 50px;
  background: var(--gradient);
  border-radius: 0.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 1.25rem;
}

.highlight-content {
  h4 {
    font-size: 1.125rem;
    font-weight: 600;
    margin-bottom: 0.5rem;
    color: var(--text-primary);
  }

  p {
    color: var(--text-secondary);
    font-size: 0.9rem;
    line-height: 1.5;
  }
}

.about-stats {
  position: sticky;
  top: 2rem;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
  margin-bottom: 3rem;
}

.stat-item {
  text-align: center;
  padding: 2rem 1rem;
  background: white;
  border-radius: 1rem;
  box-shadow: var(--shadow);
  transition: transform 0.3s ease;

  &:hover {
    transform: translateY(-5px);
  }
}

.stat-number {
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--primary-color);
  line-height: 1;
  margin-bottom: 0.5rem;

  .stat-suffix {
    font-size: 1.5rem;
    margin-left: 0.25rem;
  }
}

.stat-label {
  font-size: 0.9rem;
  color: var(--text-secondary);
  font-weight: 500;
}

.about-cta {
  text-align: center;
  padding: 2rem;
  background: white;
  border-radius: 1rem;
  box-shadow: var(--shadow);

  p {
    color: var(--text-secondary);
    margin-bottom: 1.5rem;
  }
}

.cta-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

@media (max-width: 1023px) {
  .about-stats {
    position: static;
  }
  
  .stats-grid {
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
  }

  .stat-item {
    padding: 1.5rem 0.5rem;
  }

  .stat-number {
    font-size: 2rem;
  }
}

@media (max-width: 767px) {
  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>