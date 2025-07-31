<template>
  <!-- Projects Section -->
  <section id="projects" class="section" style="background: var(--bg-secondary);">
    <div class="container">
      <h2 class="section-title fade-in">Featured Projects</h2>
      <div class="projects-grid">
        <div class="project-card fade-in" v-for="(project, index) in projects" :key="index">
          <div class="project-header">
            <h3 class="project-title">{{ project.title }}</h3>
            <p class="project-type">{{ project.type }}</p>
          </div>
          <div class="project-content">
            <p class="project-description">{{ project.description }}</p>
            <div class="project-tech">
              <span class="tech-tag" v-for="(tech, i) in project.technologies" :key="i">{{ tech }}</span>
            </div>
            <div class="project-links">
              <a
                v-for="(link, i) in project.links"
                :key="i"
                :href="link.url"
                class="project-link"
                target="_blank"
                rel="noopener"
              >
                <i :class="link.icon"></i> {{ link.text }}
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
  name: "Projects",
  data() {
    return {
      projects: [
        {
          title: "Skin Cancer Detection System",
          type: "Final Year Project | AI/ML",
          description:
            "Advanced web application leveraging deep learning algorithms for early detection and classification of skin cancer. Features real-time image analysis, accuracy metrics, and user-friendly interface for medical professionals.",
          technologies: ["Python", "TensorFlow", "OpenCV", "Flask", "JavaScript", "HTML/CSS"],
          links: [
            { text: "View Code", url: "#", icon: "fab fa-github" },
            { text: "Live Demo", url: "#", icon: "fas fa-external-link-alt" }
          ]
        },
        {
          title: "AI Cartoon Generator",
          type: "Codeknitters Internship | Computer Vision",
          description:
            "High-fidelity cartoon visual generator that transforms real human images into artistic cartoon representations using DCTNet architecture. Integrated with PhotoLab's pipeline for seamless user experience.",
          technologies: ["DCTNet", "Python", "OpenCV", "PIL", "NumPy"],
          links: [
            { text: "View Code", url: "#", icon: "fab fa-github" },
            { text: "Demo", url: "#", icon: "fas fa-external-link-alt" }
          ]
        },
        {
          title: "Clinic Management System",
          type: "Freelance Project | Full-Stack",
          description:
            "Comprehensive React-based clinic management system featuring appointment scheduling, patient records management, billing integration, and real-time notifications. Streamlined UI designed for healthcare professionals.",
          technologies: ["React.js", "Node.js", "Express.js", "MongoDB", "CSS3", "REST API"],
          links: [
            { text: "View Code", url: "#", icon: "fab fa-github" },
            { text: "Live Site", url: "#", icon: "fas fa-external-link-alt" }
          ]
        },
        {
          title: "AI Emoji Classifier",
          type: "Research Project | Machine Learning",
          description:
            "Intelligent emoji generation and classification system using SDXL models. Experiments with different diffusion techniques to create contextually appropriate emojis based on text input and emotional analysis.",
          technologies: ["SDXL", "Python", "Hugging Face", "PyTorch", "Transformers"],
          links: [
            { text: "View Code", url: "#", icon: "fab fa-github" },
            { text: "Experiment", url: "#", icon: "fas fa-flask" }
          ]
        },
        {
          title: "E-Commerce Solutions",
          type: "Client Work | WordPress Development",
          description:
            "Custom WordPress eCommerce websites for various industries including CNC machining and laser cutting businesses. Features responsive design, SEO optimization, payment integration, and mobile-first approach.",
          technologies: ["WordPress", "WooCommerce", "PHP", "JavaScript", "SCSS", "SEO"],
          links: [
            { text: "View Sites", url: "#", icon: "fas fa-globe" },
            { text: "Case Study", url: "#", icon: "fas fa-chart-line" }
          ]
        },
        {
          title: "Portfolio Website",
          type: "Personal Project | Vue.js",
          description:
            "Modern, responsive portfolio website built with Vue.js featuring smooth animations, contemporary design, and optimal performance. Showcases projects, skills, and professional experience with interactive elements.",
          technologies: ["Vue.js", "HTML5", "SCSS", "JavaScript", "CSS Animations"],
          links: [
            { text: "Live Site", url: "https://emanasad.github.io/EMANASAD/", icon: "fas fa-external-link-alt" },
            { text: "Source Code", url: "https://github.com/EmanAsad", icon: "fab fa-github" }
          ]
        }
      ]
    };
  }
};
</script>

<style scoped lang="scss">
@use "@/assets/styles/variables.scss" as *;

.projects-grid {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}
.project-card {
  background: white;
  padding: 2rem;
  border-radius: 15px;
  box-shadow: var(--shadow);
}
.project-title {
  color: var(--primary-color);
  margin: 0;
}
.project-type {
  font-size: 1rem;
  color: var(--text-secondary);
}
.project-description {
  margin: 1rem 0;
  color: var(--text-secondary);
}
.project-tech {
  margin-bottom: 1rem;
}
.tech-tag {
  background: var(--primary-color);
  color: white;
  padding: 0.3rem 0.7rem;
  border-radius: 10px;
  font-size: 0.85rem;
  margin: 0.2rem;
  display: inline-block;
}
.project-link {
  margin-right: 1rem;
  text-decoration: none;
  color: var(--primary-color);
  font-weight: 600;
}
.project-link i {
  margin-right: 0.4rem;
}
</style>
