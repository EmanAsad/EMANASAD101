<template>
  <nav class="navbar" :class="{ 'scrolled': isScrolled }">
    <div class="container">
      <div class="nav-content">
        <!-- Logo -->
        <div class="logo">
          <a href="#home" class="logo-link">
            <span class="logo-text">Eman</span>
          </a>
        </div>

<!-- Desktop Navigation -->
<ul class="nav-links hide-mobile" v-show="!mobileMenuOpen">
  <li><a href="#home" @click="setActiveLink('home')" :class="{ active: activeLink === 'home' }">Home</a></li>
  <li><a href="#about" @click="setActiveLink('about')" :class="{ active: activeLink === 'about' }">About</a></li>
  <li><a href="#skills" @click="setActiveLink('skills')" :class="{ active: activeLink === 'skills' }">Skills</a></li>
  <li><a href="#experience" @click="setActiveLink('experience')" :class="{ active: activeLink === 'experience' }">Experience</a></li>
  <li><a href="#projects" @click="setActiveLink('projects')" :class="{ active: activeLink === 'projects' }">Projects</a></li>
  <li><a href="#contact" @click="setActiveLink('contact')" :class="{ active: activeLink === 'contact' }">Contact</a></li>
</ul>

<!-- Mobile Menu Button -->
<button class="mobile-menu-btn hide-desktop" @click="toggleMobileMenu" :class="{ active: mobileMenuOpen }">
  <span></span>
  <span></span>
  <span></span>
</button>
      </div>

      <!-- Mobile Navigation -->
      <div class="mobile-nav" :class="{ active: mobileMenuOpen }">
        <ul class="mobile-nav-links">
          <li><a href="#home" @click="closeMobileMenu">Home</a></li>
          <li><a href="#about" @click="closeMobileMenu">About</a></li>
          <li><a href="#skills" @click="closeMobileMenu">Skills</a></li>
          <li><a href="#experience" @click="closeMobileMenu">Experience</a></li>
          <li><a href="#projects" @click="closeMobileMenu">Projects</a></li>
          <li><a href="#contact" @click="closeMobileMenu">Contact</a></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      isScrolled: false,
      mobileMenuOpen: false,
      activeLink: 'home'
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll)
    this.observeSections()
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      this.isScrolled = window.scrollY > 50
    },
    toggleMobileMenu() {
      this.mobileMenuOpen = !this.mobileMenuOpen
    },
    closeMobileMenu() {
      this.mobileMenuOpen = false
    },
    setActiveLink(link) {
      this.activeLink = link
    },
    observeSections() {
      const sections = ['home', 'about', 'skills', 'experience', 'projects', 'contact']
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach(entry => {
            if (entry.isIntersecting) {
              this.activeLink = entry.target.id
            }
          })
        },
        { threshold: 0.6 }
      )

      sections.forEach(section => {
        const element = document.getElementById(section)
        if (element) observer.observe(element)
      })
    }
  }
}
</script>

<style scoped lang="scss">
@use "@/assets/styles/variables.scss" as *;

.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid transparent;
  transition: all 0.3s ease;

  &.scrolled {
    background: rgba(255, 255, 255, 0.98);
    border-bottom-color: var(--border-color);
    box-shadow: var(--shadow);
  }
}

.nav-content {
  display: flex;
  align-items: center;
  justify-content: center;
}
.logo-text {
  font-size: 1.75rem;
  font-weight: 700;
  background: var(--gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.nav-links {
  display: flex;
  list-style: none;
  gap: 2rem;

  a {
    text-decoration: none;
    color: var(--text-primary);
    font-weight: 500;
    position: relative;
    transition: color 0.3s ease;

    &:hover,
    &.active {
      color: var(--primary-color);
    }

    &::after {
      content: '';
      position: absolute;
      bottom: -4px;
      left: 0;
      width: 0;
      height: 2px;
      background: var(--gradient);
      transition: width 0.3s ease;
    }

    &:hover::after,
    &.active::after {
      width: 100%;
    }
  }
}

.mobile-menu-btn {
  display: flex;
  flex-direction: column;
  gap: 4px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 8px;

  span {
    width: 25px;
    height: 3px;
    background: var(--text-primary);
    transition: all 0.3s ease;
  }

  &.active {
    span:nth-child(1) {
      transform: rotate(45deg) translate(6px, 6px);
    }
    span:nth-child(2) {
      opacity: 0;
    }
    span:nth-child(3) {
      transform: rotate(-45deg) translate(6px, -6px);
    }
  }
}

.mobile-nav {
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background: rgba(255, 255, 255, 0.98);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid var(--border-color);
  transform: translateY(-100%);
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;

  &.active {
    transform: translateY(0);
    opacity: 1;
    visibility: visible;
  }
}

.mobile-nav-links {
  list-style: none;
  padding: 1rem 0;

  li {
    padding: 0.75rem 0;
  }

  a {
    text-decoration: none;
    color: var(--text-primary);
    font-weight: 500;
    font-size: 1.1rem;
    transition: color 0.3s ease;

    &:hover {
      color: var(--primary-color);
    }
  }
}
</style>
