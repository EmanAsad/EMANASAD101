<template>
  <section id="education" class="section">
    <div class="container">
      <h2 class="section-title fade-in">Education</h2>
      <div class="education-card fade-in">
        <div class="education-icon">
          <i class="fas fa-graduation-cap"></i>
        </div>
        <h3 class="education-degree">Bachelor of Science in Computer Science</h3>
        <p class="education-school">Pakistan Institute of Engineering and Applied Sciences (PIEAS)</p>
        <p class="education-year">2021 - 2025</p>
        <div class="education-courses">
          <span class="course-tag">Data Structures & Algorithms</span>
          <span class="course-tag">Object-Oriented Programming</span>
          <span class="course-tag">Database Systems</span>
          <span class="course-tag">Software Engineering</span>
          <span class="course-tag">Computer Networks</span>
          <span class="course-tag">Operating Systems</span>
          <span class="course-tag">Machine Learning</span>
          <span class="course-tag">Artificial Intelligence</span>
          <span class="course-tag">Web Technologies</span>
          <span class="course-tag">Computer Graphics</span>
          <span class="course-tag">Discrete Mathematics</span>
          <span class="course-tag">Linear Algebra</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Education",
};
</script>

<style scoped>
.section {
  padding: 60px 0;
}
.section-title {
  font-size: 2rem;
  margin-bottom: 1.5rem;
  text-align: center;
  color: var(--primary-color);
}
.education-card {
  background: white;
  border-radius: 15px;
  padding: 2rem;
  box-shadow: var(--shadow);
  text-align: center;
}
.education-icon {
  font-size: 2.5rem;
  color: var(--primary-color);
  margin-bottom: 1rem;
}
.education-degree {
  font-size: 1.5rem;
  font-weight: bold;
  color: var(--text-primary);
}
.education-school,
.education-year {
  font-size: 1.1rem;
  color: var(--text-secondary);
  margin: 0.3rem 0;
}
.education-courses {
  margin-top: 1.5rem;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 0.5rem;
}
.course-tag {
  background: var(--primary-color);
  color: white;
  padding: 0.4rem 0.8rem;
  border-radius: 20px;
  font-size: 0.9rem;
}
.fade-in {
  animation: fadeIn 1s ease forwards;
  opacity: 0;
}
@keyframes fadeIn {
  to {
    opacity: 1;
  }
}
</style>
