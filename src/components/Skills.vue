<template>
  <section id="skills" class="section dark">
    <div class="container">
      <div class="section-header">
        <h2 class="heading-2 text-center">Skills & Technologies</h2>
        <p class="text-center mb-4" style="color: rgba(255, 255, 255, 0.8)">
          Here are the technologies and tools I work with to bring ideas to life
        </p>
      </div>

      <div class="skills-content">
        <!-- Technical Skills -->
        <div class="skills-category">
          <h3 class="category-title">
            <i class="fas fa-code"></i>
            Frontend Development
          </h3>
          <div class="skills-grid">
            <div 
              class="skill-card" 
              v-for="skill in frontendSkills" 
              :key="skill.id"
              @mouseenter="skill.isHovered = true"
              @mouseleave="skill.isHovered = false"
            >
              <div class="skill-icon">
                <i :class="skill.icon" :style="{ color: skill.color }"></i>
              </div>
              <div class="skill-info">
                <h4>{{ skill.name }}</h4>
                <div class="skill-level">
                  <div class="skill-bar">
                    <div 
                      class="skill-progress" 
                      :style="{ 
                        width: (skill.isVisible ? skill.level : 0) + '%',
                        backgroundColor: skill.color 
                      }"
                    ></div>
                  </div>
                  <span class="skill-percentage">{{ skill.level }}%</span>
                </div>
                <p class="skill-description">{{ skill.description }}</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Tools & Technologies -->
        <div class="skills-category">
          <h3 class="category-title">
            <i class="fas fa-tools"></i>
            Tools & Technologies
          </h3>
          <div class="tools-grid">
            <div 
              class="tool-item" 
              v-for="tool in tools" 
              :key="tool.id"
              :title="tool.name"
            >
              <div class="tool-icon">
                <i :class="tool.icon" :style="{ color: tool.color }"></i>
              </div>
              <span class="tool-name">{{ tool.name }}</span>
            </div>
          </div>
        </div>

        <!-- Soft Skills -->
        <div class="skills-category">
          <h3 class="category-title">
            <i class="fas fa-lightbulb"></i>
            Core Strengths
          </h3>
          <div class="soft-skills-grid">
            <div 
              class="soft-skill-card" 
              v-for="skill in softSkills" 
              :key="skill.id"
            >
              <div class="soft-skill-icon">
                <i :class="skill.icon"></i>
              </div>
              <h4>{{ skill.name }}</h4>
              <p>{{ skill.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      frontendSkills: [
        {
          id: 1,
          name: 'Vue.js',
          icon: 'fab fa-vuejs',
          color: '#4FC08D',
          level: 90,
          isVisible: false,
          isHovered: false,
          description: 'Advanced knowledge in Vue 3, Composition API, and ecosystem'
        },
        {
          id: 2,
          name: 'JavaScript',
          icon: 'fab fa-js-square',
          color: '#F7DF1E',
          level: 85,
          isVisible: false,
          isHovered: false,
          description: 'ES6+, async/await, modules, and modern JavaScript patterns'
        },
        {
          id: 3,
          name: 'HTML5',
          icon: 'fab fa-html5',
          color: '#E34F26',
          level: 95,
          isVisible: false,
          isHovered: false,
          description: 'Semantic markup, accessibility, and web standards'
        },
        {
          id: 4,
          name: 'CSS3',
          icon: 'fab fa-css3-alt',
          color: '#1572B6',
          level: 88,
          isVisible: false,
          isHovered: false,
          description: 'Flexbox, Grid, animations, and responsive design'
        },
        {
          id: 5,
          name: 'React',
          icon: 'fab fa-react',
          color: '#61DAFB',
          level: 75,
          isVisible: false,
          isHovered: false,
          description: 'Hooks, context API, and component-based architecture'
        },
        {
          id: 6,
          name: 'TypeScript',
          icon: 'fas fa-code',
          color: '#3178C6',
          level: 80,
          isVisible: false,
          isHovered: false,
          description: 'Type safety, interfaces, and large-scale application development'
        }
      ],
      tools: [
        { id: 1, name: 'Git', icon: 'fab fa-git-alt', color: '#F05032' },
        { id: 2, name: 'Webpack', icon: 'fab fa-webpack', color: '#8DD6F9' },
        { id: 3, name: 'Vite', icon: 'fas fa-bolt', color: '#646CFF' },
        { id: 4, name: 'SASS', icon: 'fab fa-sass', color: '#CF649A' },
        { id: 5, name: 'Node.js', icon: 'fab fa-node-js', color: '#339933' },
        { id: 6, name: 'NPM', icon: 'fab fa-npm', color: '#CB3837' },
        { id: 7, name: 'Figma', icon: 'fab fa-figma', color: '#F24E1E' },
        { id: 8, name: 'VS Code', icon: 'fas fa-code', color: '#007ACC' }
      ],
      softSkills: [
        {
          id: 1,
          name: 'Problem Solving',
          icon: 'fas fa-puzzle-piece',
          description: 'Breaking down complex problems into manageable solutions'
        },
        {
          id: 2,
          name: 'Team Collaboration',
          icon: 'fas fa-users',
          description: 'Working effectively with cross-functional teams'
        },
        {
          id: 3,
          name: 'Communication',
          icon: 'fas fa-comments',
          description: 'Clear technical communication with stakeholders'
        },
        {
          id: 4,
          name: 'Continuous Learning',
          icon: 'fas fa-graduation-cap',
          description: 'Staying updated with latest technologies and trends'
        }
      ]
    }
  },
  mounted() {
    this.observeSkills()
  },
  methods: {
    observeSkills() {
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach(entry => {
            if (entry.isIntersecting) {
              // Animate skill bars
              setTimeout(() => {
                this.frontendSkills.forEach(skill => {
                  skill.isVisible = true
                })
              }, 200)
              observer.unobserve(entry.target)
            }
          })
        },
        { threshold: 0.3 }
      )

      const skillsSection = this.$el.querySelector('.skills-grid')
      if (skillsSection) {
        observer.observe(skillsSection)
      }
    }
  }
}
</script>

<style scoped lang="scss">
@use "@/assets/styles/variables.scss" as *;

.section {
  padding: 6rem 0;
  background: var(--bg-dark);
  color: white;
}

.section-header {
  margin-bottom: 4rem;
}

.skills-content {
  display: flex;
  flex-direction: column;
  gap: 4rem;
}

.skills-category {
  .category-title {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    font-size: 1.5rem;
    font-weight: 600;
    margin-bottom: 2rem;
    color: white;

    i {
      color: var(--accent-color);
    }
  }
}

.skills-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5rem;

  @media (min-width: 768px) {
    grid-template-columns: repeat(2, 1fr);
  }

  @media (min-width: 1024px) {
    grid-template-columns: repeat(3, 1fr);
  }
}

.skill-card {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 1rem;
  padding: 1.5rem;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);

  &:hover {
    transform: translateY(-5px);
    background: rgba(255, 255, 255, 0.08);
    border-color: rgba(255, 255, 255, 0.2);
  }
}

.skill-icon {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  text-align: center;
}

.skill-info {
  h4 {
    font-size: 1.25rem;
    font-weight: 600;
    margin-bottom: 1rem;
    text-align: center;
  }
}

.skill-level {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1rem;
}

.skill-bar {
  flex: 1;
  height: 6px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 3px;
  overflow: hidden;
}

.skill-progress {
  height: 100%;
  border-radius: 3px;
  transition: width 1.5s ease-in-out;
  position: relative;

  &::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(
      90deg,
      transparent,
      rgba(255, 255, 255, 0.3),
      transparent
    );
    animation: shimmer 2s infinite;
  }
}

@keyframes shimmer {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}

.skill-percentage {
  font-size: 0.875rem;
  font-weight: 600;
  min-width: 35px;
}

.skill-description {
  font-size: 0.875rem;
  color: rgba(255, 255, 255, 0.7);
  text-align: center;
  line-height: 1.4;
}

.tools-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 1rem;
}

.tool-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  padding: 1.5rem 1rem;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 0.75rem;
  transition: all 0.3s ease;
  cursor: pointer;

  &:hover {
    transform: translateY(-3px);
    background: rgba(255, 255, 255, 0.08);
    border-color: rgba(255, 255, 255, 0.2);
  }
}

.tool-icon {
  font-size: 2rem;
}

.tool-name {
  font-size: 0.875rem;
  font-weight: 500;
  text-align: center;
}

.soft-skills-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5rem;

  @media (min-width: 768px) {
    grid-template-columns: repeat(2, 1fr);
  }

  @media (min-width: 1024px) {
    grid-template-columns: repeat(4, 1fr);
  }
}

.soft-skill-card {
  text-align: center;
  padding: 2rem 1.5rem;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 1rem;
  transition: all 0.3s ease;

  &:hover {
    transform: translateY(-5px);
    background: rgba(255, 255, 255, 0.08);
    border-color: rgba(255, 255, 255, 0.2);
  }
}

.soft-skill-icon {
  font-size: 2.5rem;
  color: var(--accent-color);
  margin-bottom: 1rem;
}

.soft-skill-card h4 {
  font-size: 1.125rem;
  font-weight: 600;
  margin-bottom: 0.75rem;
}

.soft-skill-card p {
  font-size: 0.875rem;
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.5;
}
</style>