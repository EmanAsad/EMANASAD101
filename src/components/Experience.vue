<template>
  <!-- Experience Section -->
  <section id="experience" class="section">
    <div class="container">
      <h2 class="section-title fade-in">Experience</h2>
      <div class="experience-timeline">
        <div class="timeline-item fade-in">
          <div class="timeline-content">
            <h3 class="experience-title">AI Intern</h3>
            <p class="experience-company">Codeknitters | 2024</p>
            <div class="experience-description">
              <p>• Developed high-fidelity cartoon visuals from real human images using DCTNet</p>
              <p>• Enhanced background removal capabilities by integrating MODNet into PhotoLab's pipeline</p>
              <p>• Generated and classified AI-based emojis through experimentation with SDXL models</p>
              <p>• Created AI-generated artwork from real-world images using Dreamlike Diffusion model</p>
              <p>• Collaborated on data preprocessing and model optimization to improve project efficiency</p>
            </div>
          </div>
          <div class="timeline-dot"></div>
        </div>

        <div class="timeline-item fade-in">
          <div class="timeline-content">
            <h3 class="experience-title">Frontend Developer</h3>
            <p class="experience-company">Freelance | 2023</p>
            <div class="experience-description">
              <p>• Developed React-based clinic management system with streamlined UI and appointment scheduling</p>
              <p>• Built and customized WordPress eCommerce websites, improving customer engagement</p>
              <p>• Designed responsive WordPress sites for CNC machining and laser cutting businesses</p>
              <p>• Implemented AI-driven solutions to streamline operations and deliver intelligent web features</p>
            </div>
          </div>
          <div class="timeline-dot"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Experience'
}
</script>

<style scoped lang="scss">
@use "@/assets/styles/variables.scss" as *;

.section {
  padding: 6rem 0;
  background: var(--bg-secondary);
}

.section-title {
  font-size: 2rem;
  font-weight: 600;
  margin-bottom: 2rem;
  color: var(--text-primary);
}

.experience-timeline {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.timeline-item {
  background: white;
  padding: 1.5rem;
  border-radius: 0.75rem;
  box-shadow: var(--shadow);
  position: relative;
}

.timeline-dot {
  position: absolute;
  left: -10px;
  top: 1.5rem;
  width: 12px;
  height: 12px;
  background: var(--primary-color);
  border-radius: 50%;
}

.experience-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: var(--text-primary);
}

.experience-company {
  font-size: 1rem;
  font-weight: 500;
  margin-bottom: 1rem;
  color: var(--text-secondary);
}

.experience-description p {
  margin-bottom: 0.5rem;
  color: var(--text-secondary);
  font-size: 0.9rem;
}
</style>
