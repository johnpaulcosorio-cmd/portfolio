<script setup>
import { ref, reactive } from 'vue'

const profile = {
  name: 'John Paul C. Osorio',
  role: 'Executive Assistant & AI Automation Specialist',
  tagline: 'Non-voice executive support and AI automation — backed by a web developer who can fix the tech too',
  niche: 'Executive Support · AI Automation',
  location: 'Mabini, Davao de Oro, PH',
  email: 'johnpaulcosorio13@gmail.com',
  phone: '0945-893-6495',
  status: 'Open to work',
}

const services = [
  { index: '01', category: 'Support',  name: 'Executive Assistance',    detail: 'Inbox management, calendar scheduling, and coordination' },
  { index: '02', category: 'Support',  name: 'Admin & Office Ops',     detail: 'Document formatting, file organization, and general office support' },
  { index: '03', category: 'Data',     name: 'Data Management',       detail: 'Data entry, spreadsheet cleanup, trackers, dashboards, and recurring reports' },
  { index: '04', category: 'AI',       name: 'AI Automation (Non-Voice)', detail: 'Workflow automation, AI-assisted documents, prompts, and integrations — no calls' },
  { index: '05', category: 'Dev',      name: 'Web Development',        detail: 'Technical edge — Laravel, Vue 3, React, Figma-to-code' },
]

const experience = [
  {
    dateStart: 'AY 2023',
    dateEnd: '2024',
    role: 'Executive Assistant, Events Management',
    org: 'Desiniano — Events Management, USeP',
    bullets: [
      "Assisted in leading the Events Management unit's team, supporting coordination among members.",
      "Assisted in organizing and coordinating events and schedules to support the team's planning and logistics.",
    ],
  },
  {
    dateStart: 'AY 2024',
    dateEnd: '2025',
    role: 'Vice President, Events Management',
    org: 'Desiniano — Events Management, USeP',
    bullets: [
      "Led the Events Management unit's team, guiding members and delegating tasks to ensure smooth execution.",
      'Organized and coordinated events and schedules, keeping planning, logistics, and timelines on track.',
    ],
  },
  {
    dateStart: 'JUN 2025',
    dateEnd: 'DEC 2025',
    role: 'Full-Stack Developer (OJT)',
    org: 'ITPR 401 (IT Practicum) — Corporate Enterprise Development Unit (CEDU), USeP Tagum-Mabini Campus',
    bullets: [
      'Contributed to full-stack development tasks involving front-end implementation, back-end integration, and system debugging.',
      'Collaborated with the CEDU team on user-focused system design and functionality testing.',
    ],
  }
]

// Add your projects here. Each entry can include:
// { title, type, year, description, features: [], stack: [], image: '/screenshots/...' }
const projects = [
  {
    title: 'Inbox & Email Template Pack',
    type: 'Mock project',
    year: '2026',
    description: 'Ready-to-use email templates for common EA workflows — scheduling requests, follow-ups, and status updates — written to sound like you, not a bot.',
    features: ['Five core templates', 'Subject-line and sign-off conventions', 'Merge-field placeholders'],
    stack: ['Gmail', 'ChatGPT-assisted drafting'],
    images: ['/screenshots/1.png', '/screenshots/2.png'],
  },
  {
    title: 'AI Automation Concept — Lead Enrichment',
    type: 'Mock project',
    year: '2026',
    description: 'An automation concept: collect, clean, and enrich lead lists, then draft personalized outreach — built on n8n workflows.',
    features: ['Data cleanup pipeline', 'Prompt templates for personalization', 'Review-before-send guardrails'],
    stack: ['n8n', 'ChatGPT API', 'Google Sheets'],
    images: ['/screenshots/3.png', '/screenshots/4.png'],
  },
  {
    title: 'Email & Calendar Management System',
    type: 'Mock project',
    year: '2026',
    description: 'A sample setup for running an executive\'s inbox and calendar — labeling rules, calendar color codes, scheduling buffers, and a weekly planning block.',
    features: ['Inbox labels and filter rules', 'Calendar color-coding and buffers', 'Weekly planning template'],
    stack: ['Gmail', 'Google Calendar', 'Notion'],
    images: ['/screenshots/5.png', '/screenshots/1.png'],
  },
]

const galleryIndex = reactive({})
const lightboxOpen = ref(false)
const lightboxProject = ref(null)
const lightboxImage = ref('')

function projectImages(p) {
  return p.images || []
}

function galleryGo(p, dir) {
  const idx = galleryIndex[p.title] || 0
  const imgs = projectImages(p)
  if (!imgs.length) return
  const next = (idx + dir + imgs.length) % imgs.length
  galleryIndex[p.title] = next
}

function openLightbox(p, img) {
  lightboxProject.value = p
  lightboxImage.value = img
  lightboxOpen.value = true
}

function closeLightbox() {
  lightboxOpen.value = false
  lightboxProject.value = null
  lightboxImage.value = ''
}

function lightboxGo(dir) {
  if (!lightboxProject.value) return
  const imgs = projectImages(lightboxProject.value)
  const idx = imgs.indexOf(lightboxImage.value)
  if (idx === -1) return
  const next = (idx + dir + imgs.length) % imgs.length
  lightboxImage.value = imgs[next]
  galleryIndex[lightboxProject.value.title] = next
}

const catColors = { Support: '#e8500a', Data: '#0e9f8a', AI: '#8b5cf6', Dev: '#2563eb' }

const toolGroups = [
  { name: 'Office & Productivity', tools: ['Google Workspace', 'MS 365', 'Notion', 'Trello', 'Zoom'] },
  { name: 'Data, AI & Automation', tools: ['Excel', 'Google Sheets', 'ChatGPT', 'Claude', 'n8n'] },
  { name: 'Design & Dev Edge', tools: ['Canva', 'Figma', 'Adobe Photoshop', 'Vue 3', 'Laravel', 'Tailwind CSS'] },
]

// Add real client testimonials here — { quote, name, role }. The section hides until filled.
const testimonials = []

const education = {
  degree: 'Bachelor of Science in Information Technology',
  org: 'University of Southeastern Philippines, Tagum-Mabini Campus',
  dateStart: 'AUG 2022',
  dateEnd: 'JUNE 2026',
  thesis: '"GADConnect: A Progressive Web Application for Gender-Responsive Profiling and Project Evaluation." Focused on full-stack web development, database management, UI/UX design, and hardware-software integration.',
}

const trainings = [
  { name: 'Career Pathing: A Preparatory Challenge for a Healthy Job-Seeking Mindset', org: 'USeP', date: 'AUG 2025' },
  { name: 'Drafting Research Articles and Technical Reports', org: 'USeP', date: 'JUN 2025' },
  { name: 'Patent-Search and Patent-Drafting Workshop', org: 'USeP', date: 'JUN 2025' },
  { name: 'DICT Cybersecurity Awareness Seminar', org: 'USeP', date: 'APR 2025' },
  { name: 'Blockchain and Web Deployment (ICT Con 2024)', org: 'City Hall of Tagum', date: 'OCT 2024' },
  { name: 'DICT Girls in ICT Career Talk', org: 'USeP', date: 'APR 2024' },
  { name: 'DICT Cybersecurity Seminar', org: 'USeP', date: 'MAR 2024' },
]

const references = [
  { name: 'Engr. Editha L. Hebron, PhD', role: 'Department Head, CTET-USeP', email: 'e.hebron@usep.edu.ph' },
  { name: 'Luchi A. Dela Cruz, MIT', role: 'Instructor, CTET-USeP', email: 'l.delacruz@usep.edu.ph' },
  { name: 'Fraulein B. Silva, PhDc', role: 'Coordinator / Asst. Prof. II, CAC-USeP', email: 'f.silva@usep.edu.ph' },
]

// TODO: replace the placeholder URLs below with your real profile links.
const socials = [
  { name: 'Facebook', url: 'https://www.facebook.com/profile.php?id=61591871669494', path: 'M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z' },
  { name: 'Instagram', url: 'https://instagram.com/', path: 'M12 0C8.74 0 8.333.015 7.053.072 5.775.132 4.905.333 4.14.63c-.789.306-1.459.717-2.126 1.384S.935 3.35.63 4.14C.333 4.905.131 5.775.072 7.053.012 8.333 0 8.74 0 12s.015 3.667.072 4.947c.06 1.277.261 2.148.558 2.913.306.788.717 1.459 1.384 2.126.667.666 1.336 1.079 2.126 1.384.766.296 1.636.499 2.913.558C8.333 23.988 8.74 24 12 24s3.667-.015 4.947-.072c1.277-.06 2.148-.262 2.913-.558.788-.306 1.459-.718 2.126-1.384.666-.667 1.079-1.335 1.384-2.126.296-.765.499-1.636.558-2.913.06-1.28.072-1.687.072-4.947s-.015-3.667-.072-4.947c-.06-1.277-.262-2.149-.558-2.913-.306-.789-.718-1.459-1.384-2.126C21.319 1.347 20.651.935 19.86.63c-.765-.297-1.636-.499-2.913-.558C15.667.012 15.26 0 12 0zm0 2.16c3.203 0 3.585.016 4.85.071 1.17.055 1.805.249 2.227.415.562.217.96.477 1.382.896.419.42.679.819.896 1.381.164.422.36 1.057.413 2.227.057 1.266.07 1.646.07 4.85s-.015 3.585-.074 4.85c-.061 1.17-.256 1.805-.421 2.227-.224.562-.479.96-.899 1.382-.419.419-.824.679-1.38.896-.42.164-1.065.36-2.235.413-1.274.057-1.649.07-4.859.07-3.211 0-3.586-.015-4.859-.074-1.171-.061-1.816-.256-2.236-.421-.569-.224-.96-.479-1.379-.899-.421-.419-.69-.824-.9-1.38-.165-.42-.359-1.065-.42-2.235-.045-1.26-.061-1.649-.061-4.844 0-3.196.016-3.586.061-4.861.061-1.17.255-1.814.42-2.234.21-.57.479-.96.9-1.381.419-.419.81-.689 1.379-.898.42-.166 1.051-.361 2.221-.421 1.275-.045 1.65-.06 4.859-.06l.045.03zm0 3.678c-3.405 0-6.162 2.76-6.162 6.162 0 3.405 2.76 6.162 6.162 6.162 3.405 0 6.162-2.76 6.162-6.162 0-3.405-2.76-6.162-6.162-6.162zM12 16c-2.21 0-4-1.79-4-4s1.79-4 4-4 4 1.79 4 4-1.79 4-4 4zm7.846-10.405c0 .795-.646 1.44-1.44 1.44-.795 0-1.44-.646-1.44-1.44 0-.794.646-1.439 1.44-1.439.793-.001 1.44.645 1.44 1.439z' },
]

const navLinks = [
  { href: '#services', label: 'Services' },
  { href: '#experience', label: 'Experience' },
  { href: '#projects', label: 'Work Samples' },
  { href: '#education', label: 'Education' },
  { href: '#contact', label: 'Contact' },
]

const titleBlock = [
  { k: 'Name', v: profile.name },
  { k: 'Role', v: 'Executive Assistant · AI Automation' },
  { k: 'Sheet', v: '01 / 01' },
  { k: 'Rev', v: 'A' },
  { k: 'Date', v: 'Nov 2026' },
]

const year = new Date().getFullYear()
</script>

<template>
  <div class="site">
    <nav>
      <div class="wrap nav-row">
        <a href="#top" class="brand">Osorio<span class="brand-dot">.</span></a>
        <div class="links">
          <a v-for="l in navLinks" :key="l.href" :href="l.href">{{ l.label }}</a>
        </div>
        <a class="nav-cta" href="#contact">Let's talk</a>
      </div>
    </nav>

    <header id="top" class="hero">
      <div class="wrap">
        <div class="hero-copy">
          <div class="eyebrow mono-label">Open to non-voice Executive Assistant &amp; AI Automation roles</div>
          <h1 class="display">John Paul<br /><em>C. Osorio</em></h1>
          <p class="hero-role">{{ profile.role }}</p>
          <p class="hero-sub">
            Web developer turned virtual assistant — everything I do is
            non-voice: inbox, calendar, spreadsheet, and busywork off an
            executive's plate, plus AI automations that save hours every
            week. My dev background means I can fix the tools I support,
            not just use them.
          </p>
          <div class="hero-actions">
            <a class="btn btn-primary" href="#projects">View work samples</a>
          </div>
          <div class="hero-meta mono-label">
            <span>{{ profile.status }}</span>
            <span class="sep"></span>
            <span>{{ profile.location }}</span>
            <span class="sep"></span>
            <a :href="`mailto:${profile.email}`">{{ profile.email }}</a>
          </div>
        </div>
      </div>
    </header>

    <!-- Section backgrounds alternate: 0 (base) / 1 (alt) / 0 / 1 / 0 / 1 -->
    <section id="services" class="section">
      <div class="wrap">
        <div class="section-head">
          <div class="mono-label" style="color: var(--accent)">01 — Services</div>
          <h2 class="display">Services offered</h2>
          <p class="section-note">Everything below is non-voice work I can start on Monday — inbox to automation.</p>
        </div>
        <div class="cap-grid">
          <article class="cap-card" v-for="c in services" :key="c.index">
            <div class="cap-top">
              <span class="cap-index mono-label">{{ c.index }}</span>
              <span class="cap-cat mono-label" :style="{ color: catColors[c.category] }">{{ c.category }}</span>
            </div>
            <h3>{{ c.name }}</h3>
            <p>{{ c.detail }}</p>
          </article>
        </div>
      </div>
    </section>

    <section id="experience" class="section section-alt">
      <div class="wrap">
        <div class="section-head">
          <div class="mono-label" style="color: var(--accent)">02 — Experience</div>
          <h2 class="display">Where I've been</h2>
          <p class="section-note">Roles that shaped how I build, collaborate, and deliver.</p>
        </div>
        <div class="exp-list">
          <article class="exp-item" v-for="e in experience" :key="e.role">
            <div class="exp-date mono-label">
              <span>{{ e.dateStart }}</span>
              <span class="exp-sep">to</span>
              <span>{{ e.dateEnd }}</span>
            </div>
            <div class="exp-body">
              <h3>{{ e.role }}</h3>
              <div class="exp-org mono-label">{{ e.org }}</div>
              <ul>
                <li v-for="b in e.bullets" :key="b">{{ b }}</li>
              </ul>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section id="projects" class="section">
      <div class="wrap">
        <div class="section-head">
          <div class="mono-label" style="color: var(--accent)">03 — Work samples</div>
          <h2 class="display">Sample deliverables</h2>
          <p class="section-note">Mock projects showing the kind of work I deliver — real client samples on request.</p>
        </div>

        <div v-if="projects.length" class="project-grid">
          <article class="project-card" v-for="p in projects" :key="p.title">
            <div class="project-gallery" v-if="projectImages(p).length">
              <div class="gallery-viewport" @click="openLightbox(p, projectImages(p)[galleryIndex[p.title] || 0])">
                <img :src="projectImages(p)[galleryIndex[p.title] || 0]" :alt="`${p.title} — image ${(galleryIndex[p.title] || 0) + 1}`" />
                <button v-if="projectImages(p).length > 1" class="gallery-arrow gallery-prev" @click.stop="galleryGo(p, -1)" aria-label="Previous">
                  <svg viewBox="0 0 24 24" width="20" height="20" fill="currentColor"><path d="M15.41 7.41L14 6l-6 6 6 6 1.41-1.41L10.83 12l4.58-4.59z"/></svg>
                </button>
                <button v-if="projectImages(p).length > 1" class="gallery-arrow gallery-next" @click.stop="galleryGo(p, 1)" aria-label="Next">
                  <svg viewBox="0 0 24 24" width="20" height="20" fill="currentColor"><path d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6z"/></svg>
                </button>
                <div class="gallery-hint">Click to expand</div>
              </div>
              <div v-if="projectImages(p).length > 1" class="gallery-dots">
                <button v-for="(img, i) in projectImages(p)" :key="i" class="gallery-dot" :class="{ active: (galleryIndex[p.title] || 0) === i }" @click="galleryIndex[p.title] = i" :aria-label="`Image ${i + 1}`"></button>
              </div>
            </div>
            <div class="project-media project-media-empty" v-else>
              <span class="mono-label">{{ p.type || 'Project' }}</span>
            </div>
            <div class="project-body">
              <div class="project-meta mono-label">
                <span>{{ p.type }}</span>
                <span>{{ p.year }}</span>
              </div>
              <h3>{{ p.title }}</h3>
              <p>{{ p.description }}</p>
              <ul class="project-features" v-if="p.features && p.features.length">
                <li v-for="f in p.features" :key="f">{{ f }}</li>
              </ul>
              <div class="stack-row" v-if="p.stack && p.stack.length">
                <span class="chip chip-sm" v-for="s in p.stack" :key="s">{{ s }}</span>
              </div>
            </div>
          </article>
        </div>

        <div v-else class="project-empty">
          <div class="project-empty-mark mono-label">Reserved</div>
          <h3 class="display">New builds are on the way.</h3>
          <p>This space is reserved for selected projects. Add entries to the <code>projects</code> array in <code>src/App.vue</code> to populate it.</p>
        </div>
      </div>
    </section>

    <section id="education" class="section section-alt">
      <div class="wrap">
        <div class="section-head">
          <div class="mono-label" style="color: var(--accent)">04 — Education</div>
          <h2 class="display">Credentials</h2>
        </div>
        <article class="edu-card">
          <div class="edu-main">
            <h3>{{ education.degree }}</h3>
            <div class="edu-org mono-label">{{ education.org }}</div>
            <p class="edu-thesis">{{ education.thesis }}</p>
          </div>
          <div class="edu-date mono-label">
            <span>{{ education.dateStart }}</span>
            <span class="to">to</span>
            <span>{{ education.dateEnd }}</span>
          </div>
        </article>
      </div>
    </section>

    <section id="trainings" class="section">
      <div class="wrap">
        <div class="section-head">
          <div class="mono-label" style="color: var(--accent)">05 — Trainings</div>
          <h2 class="display">Always learning</h2>
          <p class="section-note">Logged as attended, not claimed as expertise.</p>
        </div>
        <div class="train-list">
          <div class="train-item" v-for="t in trainings" :key="t.name">
            <span class="train-name">{{ t.name }}</span>
            <span class="train-meta mono-label">{{ t.org }} · {{ t.date }}</span>
          </div>
        </div>
      </div>
    </section>

    <section id="references" class="section section-alt">
      <div class="wrap">
        <div class="section-head">
          <div class="mono-label">06 — Testimonials &amp; references</div>
          <h2 class="display">Kind words &amp; people who can vouch</h2>
        </div>
        <div v-if="testimonials.length" class="ref-grid testi-grid">
          <article class="ref-card" v-for="t in testimonials" :key="t.name">
            <div class="ref-tag mono-label">“</div>
            <p class="quote">{{ t.quote }}</p>
            <h3>{{ t.name }}</h3>
            <div class="ref-role">{{ t.role }}</div>
          </article>
        </div>
        <div class="ref-grid">
          <article class="ref-card" v-for="r in references" :key="r.email">
            <div class="ref-tag mono-label">Ref.</div>
            <h3>{{ r.name }}</h3>
            <div class="ref-role">{{ r.role }}</div>
            <a class="ref-email mono-label" :href="`mailto:${r.email}`">{{ r.email }}</a>
          </article>
        </div>
      </div>
    </section>

    <footer id="contact">
      <div class="wrap footer-inner">
        <div class="mono-label">Contact</div>
        <h2 class="display">Let's work together.</h2>
        <p>
          Open to non-voice executive assistant, admin, data, and AI
          automation roles — fully remote, PH timezone. My web dev background means I can
          support the technical side too.
        </p>
        <div class="social-row">
          <a v-for="s in socials" :key="s.name" class="social-link" :href="s.url" :aria-label="s.name" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24" width="17" height="17" fill="currentColor" aria-hidden="true"><path :d="s.path" /></svg>
          </a>
        </div>
        <div class="email-row">
          <a :href="`mailto:${profile.email}`" class="email-link">
            <svg viewBox="0 0 24 24" width="16" height="16" fill="currentColor" aria-hidden="true"><path d="M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>
            <span>{{ profile.email }}</span>
          </a>
        </div>
      </div>

      <div class="wrap title-block">
        <div class="tb-cell" v-for="t in titleBlock" :key="t.k">
          <span class="tb-k mono-label">{{ t.k }}</span>
          <span class="tb-v">{{ t.v }}</span>
        </div>
      </div>
      <div class="wrap footer-bottom mono-label">
        <span>© {{ year }} {{ profile.name }}</span>
      </div>
    </footer>

    <div v-if="lightboxOpen" class="lightbox" @click="closeLightbox">
      <button class="lightbox-close" @click="closeLightbox" aria-label="Close">
        <svg viewBox="0 0 24 24" width="24" height="24" fill="currentColor"><path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/></svg>
      </button>
      <div class="lightbox-content" @click.stop>
        <img :src="lightboxImage" :alt="lightboxProject?.title" />
        <button class="lightbox-arrow lightbox-prev" @click="lightboxGo(-1)" aria-label="Previous">
          <svg viewBox="0 0 24 24" width="28" height="28" fill="currentColor"><path d="M15.41 7.41L14 6l-6 6 6 6 1.41-1.41L10.83 12l4.58-4.59z"/></svg>
        </button>
        <button class="lightbox-arrow lightbox-next" @click="lightboxGo(1)" aria-label="Next">
          <svg viewBox="0 0 24 24" width="28" height="28" fill="currentColor"><path d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6z"/></svg>
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* ---- nav ---- */
nav {
  position: sticky;
  top: 0;
  z-index: 50;
  backdrop-filter: blur(14px);
  background: rgba(244, 239, 230, 0.8);
  border-bottom: 1px solid var(--line);
}
.nav-row {
  height: 68px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
}
.brand {
  font-family: 'Fraunces', serif;
  font-size: 22px;
  font-weight: 600;
  color: var(--ink);
  letter-spacing: -0.01em;
}
.brand-dot { color: var(--accent); }
.links { display: flex; gap: 28px; }
.links a {
  font-size: 14px;
  color: var(--ink-soft);
}
.links a:hover { color: var(--accent); }
.nav-cta {
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--ink);
  border: 1px solid var(--line-strong);
  padding: 9px 16px;
}
.nav-cta:hover { background: var(--ink); color: var(--bg); border-color: var(--ink); }
@media (max-width: 820px) {
  .links { display: none; }
  .nav-cta { display: none; }
}

/* ---- buttons ---- */
.btn {
  font-family: 'JetBrains Mono', monospace;
  font-size: 13px;
  letter-spacing: 0.02em;
  padding: 13px 22px;
  border: 1px solid transparent;
  display: inline-block;
}
.btn-primary { background: linear-gradient(100deg, var(--accent), #f0641e); color: #fff; }
.btn-primary:hover { background: linear-gradient(100deg, var(--accent-dark), var(--accent)); }
.btn-ghost { color: var(--ink); border-color: var(--line-strong); }
.btn-ghost:hover { border-color: var(--ink); }
.btn-light { background: var(--bg); color: var(--ink); }
.btn-outline-light { color: var(--bg); border-color: rgba(244, 239, 230, 0.35); }
.btn-outline-light:hover { border-color: var(--bg); }

/* ---- hero ---- */
.hero {
  padding: 120px 0 96px;
  position: relative;
  overflow: hidden;
  background: var(--bg-2);
}
.hero::before {
  content: '';
  position: absolute;
  top: -140px;
  right: -100px;
  width: 520px;
  height: 520px;
  background: radial-gradient(closest-side, rgba(232, 80, 10, 0.16), rgba(245, 158, 11, 0.07) 55%, transparent);
  pointer-events: none;
}
.hero::after {
  content: '';
  position: absolute;
  bottom: -180px;
  left: -140px;
  width: 460px;
  height: 460px;
  background: radial-gradient(closest-side, rgba(139, 92, 246, 0.1), transparent);
  pointer-events: none;
}
.hero-copy {
  max-width: 720px;
}
.eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  color: var(--accent);
  margin-bottom: 22px;
}
.display {
  font-family: 'Inter', system-ui, sans-serif;
  font-weight: 600;
  font-size: clamp(44px, 7vw, 76px);
  line-height: 1.1;
  letter-spacing: -0.01em;
  color: var(--ink);
  margin: 0;
}
.display em {
  font-style: italic;
  display: inline-block;
  padding-right: 0.06em;
  color: var(--accent);
}
h1.display { margin-bottom: 18px; line-height: 1.1; }
.hero-role {
  font-family: 'JetBrains Mono', monospace;
  font-size: 13px;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--ink-soft);
  margin: 0 0 20px;
}
.hero-sub {
  max-width: 58ch;
  font-size: 17px;
  line-height: 1.75;
  color: var(--ink-soft);
  margin: 0 0 36px;
}
.hero-actions { display: flex; gap: 12px; flex-wrap: wrap; margin-bottom: 28px; }
.hero-meta {
  display: flex;
  align-items: center;
  gap: 14px;
  flex-wrap: wrap;
  color: var(--muted);
  font-size: 11px;
}
.hero-meta .sep { width: 4px; height: 4px; border-radius: 50%; background: var(--line-strong); }
.hero-meta a:hover { color: var(--accent); }


.stack-strip {
  margin-top: 56px;
  padding-top: 24px;
  border-top: 1px solid var(--line);
  display: flex;
  align-items: center;
  gap: 18px;
  flex-wrap: wrap;
}
.strip-label { color: var(--muted); }
.chips { display: flex; flex-wrap: wrap; gap: 8px; }
.chip {
  font-family: 'JetBrains Mono', monospace;
  font-size: 11.5px;
  letter-spacing: 0.04em;
  color: var(--ink-soft);
  border: 1px solid var(--line-strong);
  padding: 7px 13px;
  background: var(--card);
}
.chip-sm { font-size: 11px; padding: 5px 10px; }

/* ---- sections ---- */
.section { padding: 96px 0; }
.section-alt { background: var(--bg-2); }
.section-head { margin-bottom: 48px; max-width: 640px; }
.section-head .mono-label { color: var(--ink); display: block; margin-bottom: 14px; }
.section-head h2 { margin: 0 0 12px; font-size: clamp(30px, 4vw, 44px); }
.section-note { margin: 0; color: var(--ink-soft); font-size: 15px; line-height: 1.7; }

/* ---- capabilities ---- */
.cap-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
@media (max-width: 900px) { .cap-grid { grid-template-columns: repeat(2, 1fr); } }
@media (max-width: 600px) { .cap-grid { grid-template-columns: 1fr; } }
.cap-card {
  background: var(--card);
  padding: 22px;
  transition: box-shadow 0.25s;
}
.cap-card:hover {
  box-shadow: var(--shadow);
}
.cap-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 18px;
}
.cap-index { color: var(--muted); }
.cap-cat { color: var(--accent); }
.cap-card h3 {
  margin: 0 0 8px;
  font-family: 'Fraunces', serif;
  font-weight: 500;
  font-size: 19px;
  color: var(--ink);
}
.cap-card p { margin: 0; font-size: 13.5px; color: var(--ink-soft); line-height: 1.6; }

/* ---- experience ---- */
.exp-list { display: flex; flex-direction: column; }
.exp-item {
  display: grid;
  grid-template-columns: 150px 1fr;
  gap: 32px;
  padding: 34px 0;
  border-top: 1px solid var(--line);
}
.exp-item:last-child { border-bottom: 1px solid var(--line); }
@media (max-width: 700px) { .exp-item { grid-template-columns: 1fr; gap: 12px; } }
.exp-date {
  color: var(--accent);
  display: flex;
  flex-direction: column;
  gap: 2px;
  padding-top: 4px;
}
.exp-date .exp-sep { color: var(--muted); font-size: 10px; text-transform: none; letter-spacing: 0; }
.exp-body h3 {
  margin: 0 0 6px;
  font-family: 'Fraunces', serif;
  font-weight: 500;
  font-size: 22px;
  color: var(--ink);
}
.exp-org { color: var(--muted); margin-bottom: 14px; font-size: 11px; }
.exp-body ul { margin: 0; padding-left: 18px; color: var(--ink-soft); font-size: 14.5px; line-height: 1.8; }
.exp-body li { margin-bottom: 4px; }

/* ---- projects ---- */
.project-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}
@media (max-width: 800px) { .project-grid { grid-template-columns: 1fr; } }

.project-card {
  background: transparent;
  overflow: hidden;
}
.project-gallery {
  background: linear-gradient(180deg, #1a1814 0%, #252018 100%);
  padding: 24px;
  border-radius: 20px;
}
.gallery-viewport {
  position: relative;
  aspect-ratio: 16 / 10;
  border-radius: 14px;
  overflow: hidden;
  background: #1a1814;
  cursor: pointer;
}
.gallery-viewport:hover {
  box-shadow: 0 0 0 2px rgba(232, 80, 10, 0.3);
}
.gallery-viewport img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
.gallery-hint {
  position: absolute;
  bottom: 12px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 11px;
  color: rgba(255, 255, 255, 0.4);
  letter-spacing: 0.08em;
  text-transform: uppercase;
  pointer-events: none;
}
.gallery-arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.6);
  backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.15);
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 2;
}
.gallery-arrow:hover { background: rgba(0, 0, 0, 0.8); }
.gallery-prev { left: 10px; }
.gallery-next { right: 10px; }
.gallery-dots {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-top: 16px;
}
.gallery-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.15);
  border: none;
  cursor: pointer;
}
.gallery-dot:hover { background: rgba(255, 255, 255, 0.4); }
.gallery-dot.active {
  background: var(--accent);
  box-shadow: 0 0 8px rgba(232, 80, 10, 0.4);
}

.lightbox {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.9);
  backdrop-filter: blur(8px);
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 40px;
}
.lightbox-close {
  position: absolute;
  top: 24px;
  right: 24px;
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.lightbox-close:hover { background: rgba(255, 255, 255, 0.2); }
.lightbox-content {
  position: relative;
  max-width: 90vw;
  max-height: 85vh;
}
.lightbox-content img {
  max-width: 100%;
  max-height: 85vh;
  object-fit: contain;
  border-radius: 12px;
  box-shadow: 0 32px 80px rgba(0, 0, 0, 0.6);
}
.lightbox-arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 56px;
  height: 56px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.lightbox-arrow:hover { background: rgba(255, 255, 255, 0.2); }
.lightbox-prev { left: -70px; }
.lightbox-next { right: -70px; }
@media (max-width: 900px) {
  .lightbox { padding: 20px; }
  .lightbox-close { top: 16px; right: 16px; width: 40px; height: 40px; }
  .lightbox-prev { left: -50px; }
  .lightbox-next { right: -50px; }
  .lightbox-arrow { width: 44px; height: 44px; }
}
.project-media-empty {
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: 1px solid var(--line);
  background: linear-gradient(135deg, #f4e3d0 0%, #e9d6bd 100%);
}
.project-media-empty .mono-label { color: var(--muted); }
.project-body { padding: 22px; }
.project-meta {
  display: flex;
  justify-content: space-between;
  color: var(--muted);
  margin-bottom: 12px;
}
.project-body h3 {
  margin: 0 0 10px;
  font-family: 'Fraunces', serif;
  font-weight: 500;
  font-size: 22px;
  color: var(--ink);
}
.project-body > p { margin: 0 0 16px; font-size: 14px; color: var(--ink-soft); line-height: 1.7; }
.project-features {
  margin: 0 0 18px;
  padding-left: 18px;
  color: var(--ink-soft);
  font-size: 13.5px;
  line-height: 1.7;
}
.stack-row { display: flex; flex-wrap: wrap; gap: 8px; }

.project-empty {
  background: var(--card);
  padding: 64px 32px;
  text-align: center;
}
.project-empty-mark { color: var(--accent); margin-bottom: 16px; }
.project-empty h3 { margin: 0 0 12px; font-size: clamp(26px, 3.5vw, 36px); }
.project-empty p { margin: 0 auto; max-width: 46ch; color: var(--ink-soft); font-size: 14.5px; line-height: 1.7; }
.project-empty code {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.9em;
  background: var(--bg-2);
  padding: 2px 6px;
  border: 1px solid var(--line);
}

/* ---- education ---- */
.edu-card {
  background: var(--card);
  padding: 32px;
  display: flex;
  justify-content: space-between;
  gap: 32px;
  flex-wrap: wrap;
}
.edu-main { max-width: 640px; }
.edu-main h3 {
  margin: 0 0 8px;
  font-family: 'Fraunces', serif;
  font-weight: 500;
  font-size: 24px;
  color: var(--ink);
}
.edu-org { color: var(--muted); margin-bottom: 16px; font-size: 11px; }
.edu-thesis { margin: 0; font-size: 14px; line-height: 1.75; color: var(--ink-soft); }
.edu-date {
  color: var(--accent);
  display: flex;
  flex-direction: column;
  gap: 2px;
  white-space: nowrap;
  padding-top: 4px;
}
.edu-date .to { color: var(--muted); font-size: 10px; text-transform: none; letter-spacing: 0; }

/* ---- trainings ---- */
.train-list {
  display: grid;
  grid-template-columns: 1fr 1fr;
  column-gap: 48px;
}
@media (max-width: 700px) { .train-list { grid-template-columns: 1fr; } }
.train-item {
  display: flex;
  flex-direction: column;
  gap: 6px;
  padding: 18px 0;
  border-top: 1px solid var(--line);
}
.train-name { font-size: 14.5px; color: var(--ink); line-height: 1.5; }
.train-meta { color: var(--muted); font-size: 11px; }

/* ---- references ---- */
.ref-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; }
@media (max-width: 820px) { .ref-grid { grid-template-columns: 1fr; } }
.ref-card {
  background: var(--card);
  padding: 22px;
}
.ref-tag { color: var(--accent); margin-bottom: 14px; }
.ref-card h3 { margin: 0 0 4px; font-family: 'Fraunces', serif; font-weight: 500; font-size: 17px; color: var(--ink); }
.ref-role { font-size: 13px; color: var(--ink-soft); margin-bottom: 12px; }
.ref-email { color: var(--muted); }
.ref-email:hover { color: var(--accent); }

.quote { margin: 0 0 14px; font-size: 14px; line-height: 1.7; color: var(--ink-soft); font-style: italic; }
.testi-grid { margin-bottom: 24px; }

.social-row { display: flex; justify-content: center; gap: 16px; margin-top: 32px; }
.social-link {
  width: 44px;
  height: 44px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border: 1px solid rgba(244, 239, 230, 0.2);
  color: var(--bg);
  border-radius: 50%;
}
.social-link:hover {
  background: var(--bg);
  color: var(--ink);
  border-color: var(--bg);
}
.email-row {
  margin-top: 24px;
  display: flex;
  justify-content: center;
}
.email-link {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  color: #fff;
  text-decoration: none;
  font-size: 15px;
  font-weight: 500;
  font-family: 'JetBrains Mono', monospace;
  user-select: text;
  -webkit-user-select: text;
}
.email-link:hover {
  color: var(--accent);
}


/* ---- footer ---- */
footer { background: var(--ink); color: var(--bg); padding: 96px 0 0; }
.footer-inner { text-align: center; padding-bottom: 72px; }
.footer-inner .mono-label { color: var(--accent); display: block; margin-bottom: 16px; }
.footer-inner h2 {
  margin: 0 0 18px;
  font-size: clamp(34px, 5.4vw, 56px);
  line-height: 1.35;
  display: inline-block;
  padding-right: 0.06em;
  padding-bottom: 0.04em;
  background: linear-gradient(100deg, #ffd9a0, #ff9e6d 55%, #ff7a9e);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
}
.footer-inner p { max-width: 46ch; margin: 0 auto 32px; color: rgba(244, 239, 230, 0.72); font-size: 15px; line-height: 1.7; }
.footer-actions { display: flex; justify-content: center; gap: 12px; flex-wrap: wrap; }
.title-block {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  border-top: 1px solid rgba(244, 239, 230, 0.16);
}
@media (max-width: 700px) { .title-block { grid-template-columns: repeat(2, 1fr); } }
.tb-cell {
  border-right: 1px solid rgba(244, 239, 230, 0.1);
  padding: 18px 20px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.tb-cell:last-child { border-right: none; }
.tb-k { color: rgba(244, 239, 230, 0.5); }
.tb-v { font-family: 'JetBrains Mono', monospace; font-size: 12.5px; color: var(--bg); }
.footer-bottom {
  display: flex;
  justify-content: space-between;
  gap: 16px;
  flex-wrap: wrap;
  padding: 20px 0 28px;
  color: rgba(244, 239, 230, 0.5);
}
</style>