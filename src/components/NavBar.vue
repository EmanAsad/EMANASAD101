<template>
  <nav class="navbar" :class="{ 'scrolled': isScrolled }">
    <div class="container">
      <div class="nav-content">
        <!-- Desktop Navigation -->
        <ul class="nav-links">
          <li><a href="#home" @click="setActiveLink('home')" :class="{ active: activeLink === 'home' }">Home</a></li>
          <li><a href="#about" @click="setActiveLink('about')" :class="{ active: activeLink === 'about' }">About</a></li>
          <li><a href="#skills" @click="setActiveLink('skills')" :class="{ active: activeLink === 'skills' }">Skills</a></li>
          <li><a href="#experience" @click="setActiveLink('experience')" :class="{ active: activeLink === 'experience' }">Experience</a></li>
          <li><a href="#projects" @click="setActiveLink('projects')" :class="{ active: activeLink === 'projects' }">Projects</a></li>
          <li><a href="#contact" @click="setActiveLink('contact')" :class="{ active: activeLink === 'contact' }">Contact</a></li>
        </ul>

        <!-- Logo -->
        <div class="logo">
          <a href="#home" class="logo-link">
            <span class="logo-text">Eman</span>
          </a>
        </div>

        <!-- Mobile Menu Button -->
        <button class="mobile-menu-btn" @click="toggleMobileMenu" :class="{ active: mobileMenuOpen }">
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

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.nav-content {
  display: flex;
  align-items: center;
  height: 70px;
  position: relative;

  // Desktop layout: nav-links left, logo right
  @media (min-width: 769px) {
    justify-content: space-between;
  }

  // Mobile layout: logo left, menu button right
  @media (max-width: 768px) {
    justify-content: space-between;
  }
}

.logo {
  // Desktop: logo on the right
  @media (min-width: 769px) {
    order: 2;
  }
  
  // Mobile: logo on the left
  @media (max-width: 768px) {
    order: 1;
  }
}

.logo-link {
  text-decoration: none;
  display: inline-block;
  transition: transform 0.3s ease;

  &:hover {
    transform: scale(1.05);
  }
}

.logo-text {
  font-size: 1.75rem;
  font-weight: 700;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: -0.5px;
}

// Desktop Navigation
.nav-links {
  list-style: none;
  gap: 2.5rem;
  margin: 0;
  padding: 0;
  
  // Desktop: show and position on left
  @media (min-width: 769px) {
    display: flex;
    order: 1;
  }

  // Mobile: completely hide
  @media (max-width: 768px) {
    display: none;
  }

  a {
    text-decoration: none;
    color: var(--text-primary);
    font-weight: 500;
    font-size: 0.95rem;
    position: relative;
    transition: all 0.3s ease;
    padding: 0.5rem 0;

    &:hover,
    &.active {
      color: var(--primary-color);
    }

    &::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 0;
      height: 2px;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      transition: width 0.3s ease;
    }

    &:hover::after,
    &.active::after {
      width: 100%;
    }
  }
}

// Mobile Menu Button
.mobile-menu-btn {
  flex-direction: column;
  gap: 4px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 8px;
  z-index: 1001;
  
  // Desktop: completely hide
  @media (min-width: 769px) {
    display: none;
  }

  // Mobile: show and position on right
  @media (max-width: 768px) {
    display: flex;
    order: 2;
  }

  span {
    width: 25px;
    height: 3px;
    background: var(--text-primary);
    transition: all 0.3s ease;
    border-radius: 2px;
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

// Mobile Navigation Menu
.mobile-nav {
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background: rgba(255, 255, 255, 0.98);
  backdrop-filter: blur(15px);
  border-bottom: 1px solid var(--border-color);
  transform: translateY(-100%);
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);

  // Desktop: completely hide
  @media (min-width: 769px) {
    display: none;
  }

  &.active {
    transform: translateY(0);
    opacity: 1;
    visibility: visible;
  }
}

.mobile-nav-links {
  list-style: none;
  padding: 1rem 0;
  margin: 0;

  li {
    padding: 0;
    border-bottom: 1px solid rgba(0, 0, 0, 0.05);

    &:last-child {
      border-bottom: none;
    }
  }

  a {
    text-decoration: none;
    color: var(--text-primary);
    font-weight: 500;
    font-size: 1.1rem;
    transition: all 0.3s ease;
    display: block;
    padding: 1rem 1.5rem;
    position: relative;

    &:hover {
      color: var(--primary-color);
      background: rgba(102, 126, 234, 0.05);
      transform: translateX(5px);
    }

    &::before {
      content: '';
      position: absolute;
      left: 0;
      top: 0;
      bottom: 0;
      width: 0;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      transition: width 0.3s ease;
    }

    &:hover::before {
      width: 4px;
    }
  }
}

// Smooth animations
* {
  box-sizing: border-box;
}
</style>