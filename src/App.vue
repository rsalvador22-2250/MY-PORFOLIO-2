<template>
  <div :class="['app', { 'dark-mode': isDarkMode }]">
    
    <!-- ========== DARK MODE TOGGLE ========== -->
    <button class="dark-mode-toggle" @click="toggleDarkMode">
      <i :class="isDarkMode ? 'fas fa-sun' : 'fas fa-moon'"></i>
    </button>

    <!-- ========== NAVIGATION BAR ========== -->
    <nav class="navbar">
      <div class="nav-container">
        <a href="#" class="logo">
          {{ name }}
        </a>
        <div class="nav-links">
          <a href="#" class="nav-link">Home</a>
          <a href="#projects" class="nav-link">Projects</a>
          <a href="#skills" class="nav-link">Skills</a>
          <a href="#about" class="nav-link">About Me</a>
        </div>
      </div>
    </nav>

    <!-- ========== HERO SECTION WITH PROFILE PICTURE ========== -->
    <section class="hero">
      <div class="hero-bg"></div>
      <div class="hero-content">
        
        <!-- ========== PROFILE PICTURE ========== -->
        <div class="profile-container">
          <div class="profile-frame">
            <div class="profile-glow"></div>
            <img src="/2BY2(1).png" alt="Rio Salvador" class="profile-img" @error="handleImageError">
            <div class="profile-badge">
              <i class="fas fa-check-circle"></i>
            </div>
          </div>
        </div>
        
        <div class="hero-badge">
          <span class="dot"></span>
          Available for Work
        </div>
        <h1 class="hero-title">Hi, I'm <span class="gradient-text">{{ name }}</span></h1>
        <p class="hero-subtitle">{{ tagline }}</p>
        <a href="#projects" class="hero-btn">
          View Projects
          <span class="btn-arrow">→</span>
        </a>
      </div>
      <div class="scroll-indicator">
        <div class="mouse"></div>
      </div>
    </section>

    <!-- ========== PROJECTS SECTION - 2x2 GRID ========== -->
    <section id="projects" class="projects">
      <div class="container">
        <div class="section-header">
          <span class="section-tag">Live Deployment</span>
          <h2 class="section-title">My Production Systems</h2>
          <div class="section-line"></div>
        </div>
        
        <div class="projects-grid-2x2">
          
          <!-- SASO System - Card 1 -->
          <div class="project-card">
            <div class="card-image saso">
              <i class="fas fa-shield-alt"></i>
            </div>
            <div class="card-content">
              <div class="card-header">
                <h3 class="card-title">SASO System</h3>
                <span class="live-badge">● LIVE</span>
              </div>
              <p class="card-desc">Secure authentication system with role-based access control and encrypted credentials.</p>
              <div class="card-tags">
                <span>Vue.js</span>
                <span>Authentication</span>
                <span>Security</span>
              </div>
              <a href="https://sasosystem-cca.vercel.app/login.html" target="_blank" class="card-btn">
                Live Demo →
              </a>
            </div>
          </div>

          <!-- Clinic System - Card 2 -->
          <div class="project-card">
            <div class="card-image clinic">
              <i class="fas fa-hospital-user"></i>
            </div>
            <div class="card-content">
              <div class="card-header">
                <h3 class="card-title">Clinic System</h3>
                <span class="live-badge">● LIVE</span>
              </div>
              <p class="card-desc">Complete medical records management with real-time analytics and report generation.</p>
              <div class="card-tags">
                <span>Vue.js</span>
                <span>Medical Records</span>
                <span>Analytics</span>
              </div>
              <a href="https://clinic-system-cca.vercel.app/login.html" target="_blank" class="card-btn">
                Live Demo →
              </a>
            </div>
          </div>

          <!-- Future Project 1 - Card 3 -->
          <div class="project-card">
            <div class="card-image future">
              <i class="fas fa-robot"></i>
            </div>
            <div class="card-content">
              <div class="card-header">
                <h3 class="card-title">AI Assistant</h3>
                <span class="coming-badge">● COMING SOON</span>
              </div>
              <p class="card-desc">Intelligent AI-powered assistant for automated customer support and task management.</p>
              <div class="card-tags">
                <span>Vue.js</span>
                <span>OpenAI</span>
                <span>AI</span>
              </div>
              <button class="card-btn-disabled" disabled>
                Coming Soon →
              </button>
            </div>
          </div>

          <!-- Future Project 2 - Card 4 -->
          <div class="project-card">
            <div class="card-image future2">
              <i class="fas fa-chart-line"></i>
            </div>
            <div class="card-content">
              <div class="card-header">
                <h3 class="card-title">Analytics Dashboard</h3>
                <span class="coming-badge">● COMING SOON</span>
              </div>
              <p class="card-desc">Real-time analytics dashboard with advanced data visualization and reporting tools.</p>
              <div class="card-tags">
                <span>Vue.js</span>
                <span>Chart.js</span>
                <span>Analytics</span>
              </div>
              <button class="card-btn-disabled" disabled>
                Coming Soon →
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ========== SKILLS SECTION ========== -->
    <section id="skills" class="skills">
      <div class="container">
        <h2 class="skills-title">My Skills</h2>
        <div class="skills-grid">
          <div v-for="(skill, index) in skills" :key="skill.name" class="skill-card" :style="{ animationDelay: index * 0.05 + 's' }">
            <i :class="skill.icon" class="skill-icon"></i>
            <p class="skill-name">{{ skill.name }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- ========== ABOUT ME SECTION ========== -->
    <section id="about" class="about">
      <div class="container">
        <div class="section-header">
          <span class="section-tag">Get to Know Me</span>
          <h2 class="section-title">About <span class="gradient-text">Me</span></h2>
          <div class="section-line"></div>
        </div>
        
        <div class="about-wrapper">
          <div class="about-left">
            <div class="about-card">
              <div class="about-icon">
                <i class="fas fa-user-astronaut"></i>
              </div>
              <h3 class="about-name">{{ name }}</h3>
              <p class="about-role">Vue.js Developer</p>
              <div class="about-badges">
                <span class="badge">3+ Years Experience</span>
                <span class="badge">2+ Projects</span>
                <span class="badge">12+ Clients</span>
              </div>
            </div>
          </div>
          
          <div class="about-right">
            <div class="about-bio">
              <p class="bio-text">
                I'm a passionate <strong>Vue.js developer</strong> dedicated to building secure and scalable web applications. 
                With expertise in modern web technologies, I create solutions that make a difference.
              </p>
              <p class="bio-text">
                My journey in web development started 3 years ago, and since then I've worked on various projects 
                ranging from authentication systems to medical record management platforms.
              </p>
              <div class="bio-highlights">
                <div class="highlight-item">
                  <i class="fas fa-code"></i>
                  <span>Clean Code</span>
                </div>
                <div class="highlight-item">
                  <i class="fas fa-mobile-alt"></i>
                  <span>Responsive Design</span>
                </div>
                <div class="highlight-item">
                  <i class="fas fa-lock"></i>
                  <span>Security Focused</span>
                </div>
                <div class="highlight-item">
                  <i class="fas fa-rocket"></i>
                  <span>Fast Performance</span>
                </div>
              </div>
            </div>
          </div>
        </div>
        
        <!-- Contact Info -->
        <div class="contact-info-wrapper">
          <div class="contact-item">
            <i class="fas fa-envelope"></i>
            <span>rio.salvador@example.com</span>
          </div>
          <div class="contact-item">
            <i class="fas fa-map-marker-alt"></i>
            <span>Manila, Philippines</span>
          </div>
          <div class="contact-item">
            <i class="fab fa-github"></i>
            <span>github.com/rsalvador22-2250</span>
          </div>
        </div>
      </div>
    </section>

    <!-- ========== FOOTER ========== -->
    <footer class="footer">
      <div class="footer-content">
        <p>&copy; 2024 {{ name }}. Built with Vue.js</p>
        <div class="footer-badge">
          <span class="dot"></span>
          Available for Work
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      isDarkMode: false,
      name: 'Rio Salvador',
      tagline: 'Building secure and scalable web applications with Vue.js',
      skills: [
        { name: 'Vue.js', icon: 'fab fa-vuejs' },
        { name: 'JavaScript', icon: 'fab fa-js' },
        { name: 'HTML5', icon: 'fab fa-html5' },
        { name: 'CSS3', icon: 'fab fa-css3' },
        { name: 'Git', icon: 'fab fa-git-alt' },
        { name: 'REST API', icon: 'fas fa-cloud' }
      ]
    }
  },
  methods: {
    toggleDarkMode() {
      this.isDarkMode = !this.isDarkMode
      localStorage.setItem('darkMode', this.isDarkMode)
    },
    handleImageError(e) {
      console.log('Image not found, using fallback')
      e.target.src = 'https://ui-avatars.com/api/?name=Rio+Salvador&background=667eea&color=fff&size=200&bold=true'
    }
  },
  mounted() {
    const savedMode = localStorage.getItem('darkMode')
    if (savedMode === 'true') {
      this.isDarkMode = true
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  transition: background 0.3s ease, color 0.3s ease;
}

/* ========== DARK MODE TOGGLE BUTTON ========== */
.dark-mode-toggle {
  position: fixed;
  bottom: 30px;
  right: 30px;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea, #764ba2);
  border: none;
  color: white;
  font-size: 24px;
  cursor: pointer;
  z-index: 1000;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  transition: all 0.3s ease;
  animation: fadeInUp 0.6s ease;
}

.dark-mode-toggle:hover {
  transform: scale(1.1);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
}

/* ========== PROFILE PICTURE STYLES ========== */
.profile-container {
  margin-bottom: 30px;
  animation: fadeInUp 0.6s ease;
}

.profile-frame {
  position: relative;
  width: 150px;
  height: 150px;
  margin: 0 auto;
  border-radius: 50%;
}

.profile-glow {
  position: absolute;
  inset: -10px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea, #764ba2, #f093fb);
  opacity: 0.7;
  filter: blur(15px);
  animation: glowPulse 3s ease-in-out infinite;
}

@keyframes glowPulse {
  0%, 100% {
    opacity: 0.5;
    transform: scale(1);
  }
  50% {
    opacity: 0.8;
    transform: scale(1.05);
  }
}

.profile-img {
  position: relative;
  width: 150px;
  height: 150px;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid white;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s ease;
}

.profile-img:hover {
  transform: scale(1.05);
}

.profile-badge {
  position: absolute;
  bottom: 5px;
  right: 5px;
  background: #22c55e;
  width: 35px;
  height: 35px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 3px solid white;
  animation: pulseDot 2s ease-in-out infinite;
}

.profile-badge i {
  color: white;
  font-size: 18px;
}

/* ========== 2x2 GRID PROJECTS SECTION ========== */
.projects-grid-2x2 {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 32px;
  max-width: 1000px;
  margin: 0 auto;
}

@media (max-width: 768px) {
  .projects-grid-2x2 {
    grid-template-columns: 1fr;
    gap: 24px;
  }
}

.project-card {
  border-radius: 16px;
  overflow: hidden;
  transition: all 0.4s ease;
  animation: fadeInUp 0.6s ease backwards;
}

.project-card:nth-child(1) { animation-delay: 0.1s; }
.project-card:nth-child(2) { animation-delay: 0.2s; }
.project-card:nth-child(3) { animation-delay: 0.3s; }
.project-card:nth-child(4) { animation-delay: 0.4s; }

.project-card:hover {
  transform: translateY(-10px);
}

.card-image {
  height: 180px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.5s ease;
}

.project-card:hover .card-image {
  transform: scale(1.05);
}

.card-image.saso {
  background: linear-gradient(135deg, #2563eb, #06b6d4);
}

.card-image.clinic {
  background: linear-gradient(135deg, #059669, #10b981);
}

.card-image.future {
  background: linear-gradient(135deg, #9333ea, #ec4899);
}

.card-image.future2 {
  background: linear-gradient(135deg, #f59e0b, #ef4444);
}

.card-image i {
  font-size: 70px;
  color: white;
}

.card-content {
  padding: 24px;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
  flex-wrap: wrap;
  gap: 8px;
}

.card-title {
  font-size: 22px;
  font-weight: bold;
  transition: color 0.3s ease;
}

.live-badge {
  background: rgba(16, 185, 129, 0.2);
  color: #059669;
  padding: 4px 12px;
  border-radius: 50px;
  font-size: 12px;
  font-weight: bold;
}

.coming-badge {
  background: rgba(245, 158, 11, 0.2);
  color: #f59e0b;
  padding: 4px 12px;
  border-radius: 50px;
  font-size: 12px;
  font-weight: bold;
}

.card-desc {
  line-height: 1.6;
  margin-bottom: 20px;
  transition: color 0.3s ease;
}

.card-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 20px;
}

.card-tags span {
  padding: 4px 12px;
  border-radius: 50px;
  font-size: 12px;
  transition: all 0.3s ease;
}

.card-btn {
  display: block;
  text-align: center;
  background: #2563eb;
  color: white;
  padding: 12px;
  border-radius: 8px;
  text-decoration: none;
  font-weight: bold;
  transition: all 0.3s ease;
  cursor: pointer;
  border: none;
  width: 100%;
}

.card-btn:hover {
  background: #1d4ed8;
  transform: scale(1.02);
}

.card-btn-disabled {
  display: block;
  text-align: center;
  background: #9ca3af;
  color: white;
  padding: 12px;
  border-radius: 8px;
  font-weight: bold;
  width: 100%;
  border: none;
  cursor: not-allowed;
}

/* ========== LIGHT MODE ========== */
.app .navbar {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
}

.app .logo {
  background: linear-gradient(135deg, #9333ea, #ec4899);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.app .nav-link {
  color: #374151;
}

.app .hero {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.app .projects {
  background: #f3f4f6;
}

.app .project-card {
  background: white;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
}

.app .card-title {
  color: #1f2937;
}

.app .card-desc {
  color: #6b7280;
}

.app .card-tags span {
  background: #e5e7eb;
  color: #374151;
}

.app .skills {
  background: white;
}

.app .skills-title {
  color: #1f2937;
}

.app .skill-card {
  background: #f3f4f6;
}

.app .skill-name {
  color: #374151;
}

.app .about {
  background: white;
}

.app .about-card {
  background: #f3f4f6;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
}

.app .footer {
  background: #1f2937;
  color: white;
}

/* ========== DARK MODE ========== */
.app.dark-mode .navbar {
  background: rgba(15, 15, 26, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.3);
}

.app.dark-mode .nav-link {
  color: #e5e5e5;
}

.app.dark-mode .hero {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
}

.app.dark-mode .projects {
  background: #1a1a2e;
}

.app.dark-mode .section-title {
  color: white;
}

.app.dark-mode .section-tag {
  color: #a855f7;
}

.app.dark-mode .project-card {
  background: #24243e;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
}

.app.dark-mode .card-title {
  color: white;
}

.app.dark-mode .card-desc {
  color: #a0aec0;
}

.app.dark-mode .card-tags span {
  background: rgba(168, 85, 247, 0.2);
  color: #c084fc;
}

.app.dark-mode .skills {
  background: #0f0f1a;
}

.app.dark-mode .skills-title {
  color: white;
}

.app.dark-mode .skill-card {
  background: #1a1a2e;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.app.dark-mode .skill-name {
  color: #e5e5e5;
}

.app.dark-mode .about {
  background: #0f0f1a;
}

.app.dark-mode .about-card {
  background: #1a1a2e;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.app.dark-mode .about-name,
.app.dark-mode .about-role,
.app.dark-mode .bio-text {
  color: #e5e5e5;
}

.app.dark-mode .badge {
  background: #24243e;
  color: #c084fc;
}

.app.dark-mode .highlight-item {
  background: #1a1a2e;
  color: #e5e5e5;
}

.app.dark-mode .contact-item {
  color: #a0aec0;
}

.app.dark-mode .footer {
  background: #0a0a0f;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
}

.app.dark-mode .profile-img {
  border-color: #1a1a2e;
}

.app.dark-mode .profile-badge {
  border-color: #1a1a2e;
}

/* ========== NAVIGATION ========== */
.navbar {
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 1000;
  animation: slideDown 0.6s ease;
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 16px 24px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-size: 24px;
  font-weight: bold;
  text-decoration: none;
  transition: transform 0.3s ease;
}

.logo:hover {
  transform: scale(1.05);
}

.nav-links {
  display: flex;
  gap: 32px;
}

.nav-link {
  text-decoration: none;
  font-weight: 500;
  position: relative;
  transition: color 0.3s ease;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(135deg, #9333ea, #ec4899);
  transition: width 0.3s ease;
}

.nav-link:hover::after {
  width: 100%;
}

/* ========== HERO SECTION ========== */
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  position: relative;
  overflow: hidden;
  padding: 0 24px;
}

.hero-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle at 20% 50%, rgba(255, 255, 255, 0.1), transparent 50%),
              radial-gradient(circle at 80% 80%, rgba(255, 255, 255, 0.1), transparent 50%);
  animation: pulse 4s ease-in-out infinite;
}

.hero-content {
  position: relative;
  z-index: 10;
  animation: fadeInUp 0.8s ease;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  padding: 8px 20px;
  border-radius: 50px;
  color: white;
  font-size: 14px;
  font-weight: 500;
  margin-bottom: 24px;
}

.dot {
  width: 8px;
  height: 8px;
  background: #22c55e;
  border-radius: 50%;
  display: inline-block;
  animation: pulseDot 2s ease-in-out infinite;
}

.hero-title {
  font-size: 56px;
  font-weight: bold;
  color: white;
  margin-bottom: 16px;
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 40px;
  }
}

.gradient-text {
  background: linear-gradient(135deg, #fbbf24, #f97316);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  display: inline-block;
  animation: shimmer 2s ease-in-out infinite;
}

.hero-subtitle {
  font-size: 20px;
  color: rgba(255, 255, 255, 0.9);
  max-width: 600px;
  margin: 0 auto 32px;
  line-height: 1.6;
}

.hero-btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: white;
  color: #667eea;
  padding: 12px 32px;
  border-radius: 50px;
  text-decoration: none;
  font-weight: bold;
  transition: all 0.3s ease;
}

.hero-btn:hover {
  transform: translateY(-3px);
  gap: 12px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
}

.scroll-indicator {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  animation: bounce 2s ease-in-out infinite;
}

.mouse {
  width: 26px;
  height: 42px;
  border: 2px solid rgba(255, 255, 255, 0.5);
  border-radius: 20px;
  position: relative;
}

.mouse::before {
  content: '';
  position: absolute;
  top: 8px;
  left: 50%;
  transform: translateX(-50%);
  width: 4px;
  height: 8px;
  background: white;
  border-radius: 2px;
  animation: scroll 1.5s ease-in-out infinite;
}

/* ========== PROJECTS SECTION ========== */
.projects {
  padding: 80px 0;
  transition: background 0.3s ease;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
}

.section-header {
  text-align: center;
  margin-bottom: 48px;
  animation: fadeInUp 0.6s ease;
}

.section-tag {
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 2px;
  font-size: 14px;
  display: inline-block;
  margin-bottom: 8px;
}

.section-title {
  font-size: 36px;
  font-weight: bold;
  margin-top: 8px;
  transition: color 0.3s ease;
}

.section-line {
  width: 60px;
  height: 3px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  margin: 16px auto;
  border-radius: 3px;
}

/* ========== SKILLS SECTION ========== */
.skills {
  padding: 80px 0;
  transition: background 0.3s ease;
}

.skills-title {
  font-size: 36px;
  font-weight: bold;
  text-align: center;
  margin-bottom: 48px;
  animation: fadeInUp 0.6s ease;
  transition: color 0.3s ease;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 20px;
}

.skill-card {
  padding: 20px;
  border-radius: 12px;
  text-align: center;
  transition: all 0.3s ease;
  animation: fadeInUp 0.5s ease backwards;
  cursor: pointer;
}

.skill-card:hover {
  transform: translateY(-5px);
  background: linear-gradient(135deg, #667eea, #764ba2);
}

.skill-card:hover .skill-icon {
  color: white;
  transform: scale(1.1);
}

.skill-card:hover .skill-name {
  color: white;
}

.skill-icon {
  font-size: 40px;
  color: #667eea;
  margin-bottom: 10px;
  transition: all 0.3s ease;
  display: inline-block;
}

.skill-name {
  font-weight: 600;
  transition: color 0.3s ease;
}

/* ========== ABOUT SECTION ========== */
.about {
  padding: 80px 0;
  transition: background 0.3s ease;
}

.about-wrapper {
  display: grid;
  grid-template-columns: 1fr 1.5fr;
  gap: 50px;
  max-width: 1000px;
  margin: 0 auto 50px;
}

.about-card {
  text-align: center;
  padding: 40px 30px;
  border-radius: 24px;
  transition: all 0.3s ease;
}

.about-card:hover {
  transform: translateY(-5px);
}

.about-icon {
  font-size: 60px;
  color: #667eea;
  margin-bottom: 20px;
}

.about-name {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 8px;
}

.about-role {
  color: #667eea;
  margin-bottom: 20px;
}

.about-badges {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 10px;
  margin-top: 20px;
}

.badge {
  padding: 6px 14px;
  background: #e5e7eb;
  border-radius: 50px;
  font-size: 12px;
  font-weight: 500;
}

.about-bio {
  padding: 20px;
}

.bio-text {
  font-size: 16px;
  line-height: 1.8;
  margin-bottom: 20px;
}

.bio-highlights {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 15px;
  margin-top: 30px;
}

.highlight-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 12px 16px;
  background: #f3f4f6;
  border-radius: 12px;
  font-size: 14px;
  font-weight: 500;
}

.highlight-item i {
  color: #667eea;
  font-size: 18px;
}

.contact-info-wrapper {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 30px;
  margin-top: 40px;
  padding-top: 30px;
  border-top: 1px solid rgba(0, 0, 0, 0.1);
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 14px;
}

.contact-item i {
  width: 20px;
  color: #667eea;
}

/* ========== FOOTER ========== */
.footer {
  padding: 24px;
  text-align: center;
  transition: background 0.3s ease;
  animation: fadeInUp 0.6s ease;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 16px;
}

.footer-badge {
  display: flex;
  align-items: center;
  gap: 8px;
  background: rgba(255, 255, 255, 0.1);
  padding: 6px 16px;
  border-radius: 50px;
  font-size: 12px;
  font-weight: 500;
}

/* ========== ANIMATIONS ========== */
@keyframes slideDown {
  from { transform: translateY(-100%); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}

@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes pulse {
  0%, 100% { opacity: 0.5; }
  50% { opacity: 1; }
}

@keyframes pulseDot {
  0%, 100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.5; transform: scale(1.2); }
}

@keyframes shimmer {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.8; }
}

@keyframes bounce {
  0%, 100% { transform: translateX(-50%) translateY(0); }
  50% { transform: translateX(-50%) translateY(10px); }
}

@keyframes scroll {
  0% { opacity: 1; transform: translateX(-50%) translateY(0); }
  100% { opacity: 0; transform: translateX(-50%) translateY(15px); }
}

@media (max-width: 968px) {
  .about-wrapper {
    grid-template-columns: 1fr;
    gap: 30px;
  }
  
  .bio-highlights {
    grid-template-columns: 1fr;
  }
  
  .contact-info-wrapper {
    flex-direction: column;
    align-items: center;
    gap: 15px;
  }
}

@media (max-width: 768px) {
  .footer-content {
    flex-direction: column;
    text-align: center;
  }
  
  .nav-links {
    gap: 16px;
  }
  
  .profile-frame {
    width: 120px;
    height: 120px;
  }
  
  .profile-img {
    width: 120px;
    height: 120px;
  }
}
</style>