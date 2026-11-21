<script setup>
import { ref } from 'vue'

const activeFilter = ref('All')

const projects = [
  {
    title: 'GoodBow Online Learning Platform',
    category: 'Software',
    role: 'Junior Full-Stack Engineer (Apprentice)',
    description:
      'Built a web platform connecting students with teachers for paid 1-on-1 coaching, managing team workflows with Scrum and Kanban boards.',
    tags: ['Python', 'Django / DRF', 'Scrum', 'Kanban'],
    link: 'https://github.com'
  },
  {
    title: 'Front-Office & Guest Operations',
    category: 'Operations',
    role: 'Front Desk Attendant — Central Inn Entebbe (2012–Present)',
    description:
      '10+ years managing multi-line communications, guest check-ins/check-outs, reservations, mail/deliveries, and cross-departmental coordination.',
    tags: ['Guest Relations', 'Scheduling', 'MS Office (ICDL)', 'Admin'],
    link: '#contact'
  },
  {
    title: 'Print & Brand Collateral Designs',
    category: 'Design',
    role: 'Freelance Graphic Designer',
    description:
      'Designed promotional flyers, bi-fold brochures, business cards, and event banners tailored for local hospitality and business clients.',
    tags: ['CorelDraw', 'Print Layout', 'Brand Identity'],
    link: '#contact'
  },
  {
    title: 'Personal Developer & Admin Portfolio',
    category: 'Software',
    role: 'Creator & Developer',
    description:
      'Responsive single-page portfolio built with Vite and Vue.js, automated for continuous deployment on GitHub Pages.',
    tags: ['Vue.js', 'Vite', 'CSS3', 'GitHub Pages'],
    link: 'https://github.com'
  }
]

const filteredProjects = () => {
  if (activeFilter.value === 'All') return projects
  return projects.filter((p) => p.category === activeFilter.value)
}
</script>

<template>
  <div class="page">
    <header class="navbar">
      <div class="container nav-content">
        <a href="#" class="logo">Francis<span>.dev</span></a>
        <nav class="nav-links">
          <a href="#about">About</a>
          <a href="#skills">Skills</a>
          <a href="#projects">Work</a>
          <a href="#contact" class="btn-small">Contact</a>
        </nav>
      </div>
    </header>

    <section class="hero">
      <div class="container">
        <p class="badge">Entebbe, Uganda • Open to Opportunities</p>
        <h1>Hi, I'm <span class="highlight">Francis Murungi</span></h1>
        <p class="subtitle">
          Front Desk &amp; Operations Specialist with <strong>10+ years</strong> of hospitality
          experience, paired with <strong>Full-Stack Web Development</strong> (Python/Django,
          Vue.js) and <strong>CorelDraw</strong> graphic design.
        </p>
        <div class="hero-actions">
          <a href="#projects" class="btn-primary">View My Work</a>
          <a href="#contact" class="btn-secondary">Get in Touch</a>
        </div>
      </div>
    </section>

    <section id="about" class="section">
      <div class="container">
        <h2 class="section-title">Experience &amp; Education</h2>
        <div class="timeline">
          <div class="card">
            <span class="date">2012 – Present</span>
            <h3>Front Desk Attendant — Central Inn Entebbe</h3>
            <p>
              Manage front-office operations, multi-line phone and email communications, guest
              reservations, mail/delivery logistics, and team coordination.
            </p>
          </div>
          <div class="card">
            <span class="date">2023</span>
            <h3>Junior Full-Stack Engineer (Apprenticeship) — GoodBow</h3>
            <p>
              Developed features for an online coaching platform and tracked sprint deliverables
              using Kanban boards inside an Agile Scrum workflow.
            </p>
          </div>
          <div class="card">
            <span class="date">2018 – 2023</span>
            <h3>Certifications &amp; Technical Training</h3>
            <ul>
              <li><strong>Software Engineering Certificate</strong> — Refactory UG, Muyenga (2023)</li>
              <li><strong>ICDL Certification</strong> — Engage Consults (2023)</li>
              <li><strong>National Certificate in Computer Engineering</strong> — MTAC Nakawa (2018–2020)</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <section id="skills" class="section alt-bg">
      <div class="container">
        <h2 class="section-title">Core Skills</h2>
        <div class="skills-grid">
          <div class="card">
            <h3>Front Office &amp; Admin</h3>
            <p>Customer Service, Scheduling, Multi-line Phones, Mail &amp; Logistics, MS Office (ICDL)</p>
          </div>
          <div class="card">
            <h3>Software Engineering</h3>
            <p>Python, Django, Django REST Framework (DRF), Vue.js, Git &amp; GitHub, HTML/CSS</p>
          </div>
          <div class="card">
            <h3>Design &amp; Workflow</h3>
            <p>CorelDraw Graphic Design, Agile Project Management (Scrum &amp; Kanban), Problem-Solving</p>
          </div>
        </div>
      </div>
    </section>

    <section id="projects" class="section">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title">Featured Work &amp; Experience</h2>
          <div class="filters">
            <button
              v-for="cat in ['All', 'Operations', 'Software', 'Design']"
              :key="cat"
              :class="['filter-btn', { active: activeFilter === cat }]"
              @click="activeFilter = cat"
            >
              {{ cat }}
            </button>
          </div>
        </div>

        <div class="projects-grid">
          <article v-for="project in filteredProjects()" :key="project.title" class="card project-card">
            <span class="category-tag">{{ project.category }}</span>
            <h3>{{ project.title }}</h3>
            <p class="role">{{ project.role }}</p>
            <p>{{ project.description }}</p>
            <div class="tags">
              <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
            <a :href="project.link" target="_blank" rel="noopener" class="card-link">
              Learn More →
            </a>
          </article>
        </div>
      </div>
    </section>

    <section id="contact" class="section alt-bg">
      <div class="container contact-box">
        <h2 class="section-title">Let's Work Together</h2>
        <p>
          Available for Front Desk / Administrative roles, Junior Full-Stack projects, and
          CorelDraw design work in Entebbe, Kampala, or remotely.
        </p>
        <div class="contact-details">
          <a href="mailto:francis_951@live.com" class="btn-primary">francis_951@live.com</a>
          <p class="phone">📞 +256 784 688 102 / +256 755 676 978</p>
          <p class="location">📍 Entebbe, Uganda</p>
        </div>
      </div>
    </section>

    <footer class="footer">
      <div class="container">
        <p>© {{ new Date().getFullYear() }} Francis Murungi. Built with Vite &amp; Vue.js.</p>
      </div>
    </footer>
  </div>
</template>

<style>
:root {
  --bg: #0f172a;
  --card: #1e293b;
  --text: #f8fafc;
  --muted: #94a3b8;
  --accent: #38bdf8;
  --border: #334155;
}
* { box-sizing: border-box; margin: 0; padding: 0; }
html {
  scroll-behavior: smooth;
  font-family: system-ui, -apple-system, sans-serif;
  background: var(--bg);
  color: var(--text);
  line-height: 1.6;
}
.container { max-width: 1000px; margin: 0 auto; padding: 0 1.25rem; }
.navbar {
  position: sticky; top: 0; z-index: 10;
  background: rgba(15, 23, 42, 0.92);
  border-bottom: 1px solid var(--border);
}
.nav-content { display: flex; justify-content: space-between; align-items: center; height: 64px; }
.logo { font-weight: 700; font-size: 1.25rem; color: var(--text); text-decoration: none; }
.logo span, .highlight, .date, .category-tag, .card-link { color: var(--accent); }
.nav-links { display: flex; gap: 1.25rem; align-items: center; }
.nav-links a { color: var(--muted); text-decoration: none; font-size: 0.95rem; }
.nav-links a:hover { color: var(--text); }
.hero { padding: 5rem 0 4rem; text-align: center; }
.badge {
  display: inline-block; padding: 0.35rem 0.85rem; border-radius: 999px;
  background: rgba(56, 189, 248, 0.12); color: var(--accent);
  font-size: 0.85rem; margin-bottom: 1rem;
}
.hero h1 { font-size: clamp(2rem, 5vw, 3.25rem); margin-bottom: 1rem; }
.subtitle { max-width: 680px; margin: 0 auto 2rem; color: var(--muted); font-size: 1.1rem; }
.hero-actions, .filters { display: flex; gap: 0.75rem; justify-content: center; flex-wrap: wrap; }
.btn-primary, .btn-secondary, .btn-small {
  display: inline-block; padding: 0.7rem 1.4rem; border-radius: 8px;
  font-weight: 600; text-decoration: none;
}
.btn-small { padding: 0.4rem 0.9rem; background: var(--accent); color: #0f172a !important; }
.btn-primary { background: var(--accent); color: #0f172a; }
.btn-secondary { border: 1px solid var(--border); color: var(--text); }
.section { padding: 4rem 0; }
.alt-bg { background: rgba(30, 41, 59, 0.45); }
.section-title { font-size: 1.75rem; margin-bottom: 1.5rem; }
.section-header {
  display: flex; justify-content: space-between; align-items: center;
  flex-wrap: wrap; gap: 1rem; margin-bottom: 1.75rem;
}
.section-header .section-title { margin-bottom: 0; }
.timeline, .skills-grid, .projects-grid { display: grid; gap: 1.25rem; }
.skills-grid { grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); }
.projects-grid { grid-template-columns: repeat(auto-fit, minmax(290px, 1fr)); }
.card {
  background: var(--card); border: 1px solid var(--border);
  border-radius: 12px; padding: 1.5rem;
}
.card h3 { margin-bottom: 0.4rem; }
.card p, .card li { color: var(--muted); font-size: 0.95rem; }
.card ul { padding-left: 1.2rem; margin-top: 0.5rem; }
.date, .category-tag { display: inline-block; font-size: 0.8rem; font-weight: 600; margin-bottom: 0.35rem; }
.filter-btn {
  background: var(--card); color: var(--muted); border: 1px solid var(--border);
  padding: 0.4rem 0.9rem; border-radius: 8px; cursor: pointer; font-size: 0.85rem;
}
.filter-btn.active { background: var(--accent); color: #0f172a; border-color: var(--accent); font-weight: 600; }
.role { font-size: 0.85rem !important; color: #cbd5e1 !important; margin-bottom: 0.6rem; }
.tags { display: flex; flex-wrap: wrap; gap: 0.4rem; margin: 1rem 0; }
.tag {
  background: var(--bg); color: var(--muted); font-size: 0.75rem;
  padding: 0.25rem 0.6rem; border-radius: 6px; border: 1px solid var(--border);
}
.card-link { text-decoration: none; font-weight: 600; font-size: 0.9rem; }
.contact-box { text-align: center; max-width: 600px; }
.contact-details { margin-top: 1.5rem; display: flex; flex-direction: column; align-items: center; gap: 0.75rem; }
.footer {
  text-align: center; padding: 2rem 0; border-top: 1px solid var(--border);
  color: var(--muted); font-size: 0.85rem;
}
</style>