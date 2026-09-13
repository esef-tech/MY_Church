<template>
  <!--
    Bethel Church — About Page Replica
    A self-contained Vue 3 + Tailwind CSS component.
    Sections: Hero Banner, Secondary Navbar, Mission, Who We Are, History Timeline, More About Bethel.
    No footer included.
  -->
  <div id="top" class="bethel-about font-sans text-neutral-900 antialiased">
    <!-- ====================== HERO BANNER ====================== -->
    <section class="hero-banner relative flex min-h-[60vh] items-center md:min-h-[70vh]">
      <div class="mx-auto w-full max-w-[1360px] px-6 md:px-10">
        <h1
          class="hero-title font-serif font-light leading-[1.05] tracking-tight text-white"
        >
          About KKPC A/G
        </h1>
      </div>
    </section>

    <!-- ====================== SECONDARY NAVBAR ====================== -->
    <nav
      id="secondary-navbar"
      class="sticky top-0 z-40 border-b border-neutral-200 bg-white/95 backdrop-blur"
    >
      <div class="mx-auto flex w-full max-w-[1360px] items-center justify-between px-6 py-4 md:px-10">
        <a href="#top" class="secondary-nav-logo font-serif text-lg tracking-wide text-neutral-900">
          Introduction
        </a>
        <div class="hidden items-center gap-8 md:flex">
          <a v-for="link in navLinks" :key="link.href" :href="link.href"
            class="nav-link text-sm font-medium uppercase tracking-wider text-neutral-700 transition-colors hover:text-amber-700">
            {{ link.label }}
          </a>
        </div>
        <!-- Mobile select -->
        <select
          v-model="activeSection"
          class="rounded border border-neutral-300 bg-white px-3 py-1.5 text-sm md:hidden"
          @change="scrollToSection"
        >
          <option v-for="link in navLinks" :key="link.href" :value="link.href">
            {{ link.label }}
          </option>
        </select>
        <a href="#top" class="back-to-top ml-2 hidden md:inline-flex" aria-label="Back to top">
          <svg class="h-5 w-5 text-neutral-700" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18" />
          </svg>
        </a>
      </div>
    </nav>

    <!-- ====================== MISSION SECTION ====================== -->
    <section id="mission" class="section bg-light-tan">
      <div class="container mx-auto max-w-[1100px] px-6 py-20 text-center md:py-28">
        <h6 class="heading-caps font-serif text-base font-light uppercase tracking-[0.25em] text-amber-800 md:text-lg">
          KKPC A/G's  Mission is Revival
        </h6>
        <div class="mt-6">
          <h2 class="mission-line font-serif text-2xl font-light uppercase leading-snug tracking-wide text-neutral-800 md:text-3xl lg:text-4xl">
            —The Personal, Regional, and Global Expansion
          </h2>
          <h2 class="mission-line mt-2 font-serif text-2xl font-light uppercase leading-snug tracking-wide text-neutral-800 md:text-3xl lg:text-4xl">
            Of&nbsp;God's Kingdom Through&nbsp;His Manifest Presence.
          </h2>
        </div>
      </div>
    </section>

    <!-- ====================== WHO WE ARE SECTION ====================== -->
    <section id="about" class="section bg-white-smoke">
      <div class="container mx-auto max-w-[1360px] px-6 py-20 md:px-10 md:py-28">
        <div class="grid items-center gap-10 md:grid-cols-2 md:gap-16">
          <!-- Image -->
          <div class="image-wrapper order-1">
            <img
              src="https://cdn.prod.website-files.com/613a860b6005a3bcb87aca81/62138be54ea9b286ac0bbd85_bethhel.jpg"
              alt="Bethel is a congregation rooted in the Love of God."
              class="w-full rounded-sm object-cover shadow-lg"
              loading="lazy"
            />
          </div>
          <!-- Text -->
          <div class="grid-text-block order-2">
            <h6 class="heading-caps mb-2 font-serif text-sm font-medium uppercase tracking-[0.3em] text-amber-800">
              About
            </h6>
            <h2 class="who-we-are-title font-serif text-4xl font-light leading-tight text-neutral-900 md:text-5xl">
              Who We Are
            </h2>
            <div class="mt-6 space-y-4 text-base leading-relaxed text-neutral-700 md:text-lg">
              <p>
                KKPC is a praying ministry located in Tucson, AZ. Our prayer force is on standby 24 hours a day waiting for your call to support your prayer needs now.. The Lord has given us a mandate to be a resource center to impact cities and nations. We believe we're on the edge of the greatest revival of all time.
              </p>
              <p>
                We are a vibrant family of hope-filled believers who deeply experience the love and presence of God and partner with Jesus to express the joy and power of His kingdom in every area of life. At the center of our gatherings is a pursuit of God's presence, where our hearts are transformed and launched into our destinies. We are excited to run with you and pursue God's presence until the earth looks like heaven.
              </p>
              <p>
                We welcome you to join us in this adventure!
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ====================== HISTORY / TIMELINE SECTION ====================== -->
    <section id="history" class="section bg-white">
      <div class="container mx-auto max-w-[1360px] px-6 py-20 md:px-10 md:py-28">
        <h6 class="heading-caps mb-2 font-serif text-sm font-medium uppercase tracking-[0.3em] text-amber-800">
          History
        </h6>
        <h2 class="mb-16 font-serif text-3xl font-light leading-tight text-neutral-900 md:text-4xl lg:text-5xl">
          A History of God's Faithfulness
        </h2>

        <!-- Timeline -->
        <div class="timeline-wrapper relative">
          <!-- center vertical line -->
          <div class="timeline-line absolute left-4 top-0 h-full w-px bg-neutral-300 md:left-1/2 md:-translate-x-1/2"></div>

          <div
            v-for="(entry, i) in timeline"
            :key="entry.decade"
            class="timeline-entry relative mb-12 pl-12 md:pl-0"
            :class="{ 'md:text-right md:pl-0 md:pr-[52%]': i % 2 === 0, 'md:pl-[52%]': i % 2 === 1 }"
          >
            <!-- connector + dot -->
            <div
              class="timeline-connector absolute left-4 top-2 -translate-x-1/2 md:left-1/2"
            >
              <div class="timeline-dot h-3 w-3 rounded-full border-2 border-amber-700 bg-white"></div>
            </div>

            <!-- card -->
            <div class="timeline-card rounded-sm bg-neutral-50 p-6 shadow-sm md:p-8">
              <h3 class="timeline-decade font-serif text-2xl font-light uppercase tracking-wide text-amber-800 md:text-3xl">
                {{ entry.decade }}
              </h3>
              <div class="mt-4 space-y-4">
                <div v-for="item in entry.items" :key="item.year" class="text-left md:inline-block">
                  <h5 class="timeline-year font-serif text-lg font-medium text-neutral-900">
                    {{ item.year }}
                  </h5>
                  <p class="l2 mt-1 text-sm leading-relaxed text-neutral-600 md:text-base">
                    {{ item.text }}
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ====================== MORE ABOUT KKPC A/G SECTION ====================== -->
    <section id="other-beliefs" class="section bg-white-smoke">
      <div class="container mx-auto max-w-[1360px] px-6 py-20 md:px-10 md:py-28">
        <h4 class="mb-12 font-serif text-2xl font-medium uppercase tracking-[0.15em] text-neutral-900 md:text-3xl">
          More About KKPC A/G
        </h4>
        <div class="grid gap-6 md:grid-cols-3">
          <div
            v-for="card in moreCards"
            :key="card.title"
            class="flex-card group flex flex-col justify-between rounded-sm bg-white p-8 shadow-sm transition-shadow hover:shadow-md"
          >
            <div>
              <h5 class="mb-3 font-serif text-xl font-medium text-neutral-900 md:text-2xl">
                {{ card.title }}
              </h5>
              <p class="text-sm leading-relaxed text-neutral-600 md:text-base">
                {{ card.text }}
              </p>
            </div>
            <a
              href="#"
              class="bethel-button mt-6 inline-block self-start border border-neutral-900 px-6 py-2.5 text-xs font-medium uppercase tracking-widest text-neutral-900 transition-colors hover:bg-neutral-900 hover:text-white"
            >
              Learn More
            </a>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface NavLink {
  label: string
  href: string
}

interface TimelineItem {
  year: string
  text: string
}

interface TimelineEntry {
  decade: string
  items: TimelineItem[]
}

const navLinks: NavLink[] = [
  { label: 'Mission', href: '#mission' },
  { label: 'About', href: '#about' },
  { label: 'History', href: '#history' },
  { label: 'Beliefs', href: '#other-beliefs' },
]

const activeSection = ref('#mission')

function scrollToSection() {
  if (activeSection.value) {
    const el = document.querySelector(activeSection.value)
    if (el) el.scrollIntoView({ behavior: 'smooth' })
  }
}

const timeline: TimelineEntry[] = [
  {
    decade: "1950's",
    items: [
      {
        year: '1952',
        text: "KKPC A/G started their first gathering by Robert Doherty in a private home. This intimate gathering was the foundation of a global movement.",
      },
      {
        year: '1954',
        text: "Under Pastor Doherty's leadership, the church outgrew their home and moved to a new location on Magnolia Avenue.",
      },
    ],
  },
  {
    decade: "1960's",
    items: [
      {
        year: '1964',
        text: 'KKPC A/G acquired and dedicated a new facility on Bechelli Lane to house the growing congregation.',
      },
      {
        year: '1966',
        text: 'Reverend Vic Trimer becomes the pastor of KKPC A/G.',
      },
      {
        year: '1968',
        text: "M. Earl and Darliene Johnson became the pastors of KKPC A/G. Earl is the father of Senior Leader Bill Johnson.",
      },
    ],
  },
  {
    decade: "1980's",
    items: [
      {
        year: '1984',
        text: "Ray and Rebecca Larson were called to pastor KKPC A/G. The church grew to an estimated attendance of 2,000 and relocated to its present site (College View Road).",
      },
      {
        year: '1988',
        text: "KKPC A/G established King's Kids Christian School out of a desire to disciple children in the way of the Lord. Ray Larson, senior pastor at that time, led the school during its first years. The school was located at the former church site on Bechelli Lane. The school later is renamed KKPC A/G Christian School.",
      },
    ],
  },
  {
    decade: "1990's",
    items: [
      {
        year: '1995',
        text: 'KKPC A/G completed construction of the College View Campus facilities.',
      },
      {
        year: '1996',
        text: 'Bill and Beni Johnson became the pastors of KKPC A/G.',
      },
      {
        year: '1997',
        text: 'KKPC A/G opened the Transformation Center, which annually gives over 11,000 hours of ministry towards inner healing and personal transformation.',
      },
      {
        year: '1998',
        text: 'Kris and Kathy Vallotton became the Senior Associate Pastors of KKPC A/G. KKPC A/G School of Supernatural Ministry (BSSM) founded with 37 students. It now hosts over 2,000 students annually from 64 countries.',
      },
      {
        year: '1999',
        text: "Jesus Culture (KKPC A/G's youth ministry at the time) hosted their first conference. KKPC A/G completed the construction of the Alabaster Prayer House.",
      },
    ],
  },
  {
    decade: "2000's",
    items: [
      {
        year: '2001',
        text: 'Danny and Sheri Silk moved to Redding to become a part of the Bethel Senior Team.',
      },
      {
        year: '2008',
        text: 'KKPC A/G.TV established. Online streaming now reaches over 412,800 users internationally.',
      },
      {
        year: '2009',
        text: 'KKPC A/G Music was founded by Brian and Jenn Johnson to steward songs coming out of KKPC A/G. KKPC A/G Music now reaches 2 million+ monthly listeners and over 4 million through social media. KKPC A/G Church started leasing the Twin View Campus location. KKPC A/G Church acquired the Caterpillar Road facility. This now houses KKPC A/G Media, Human Resources, and Advancement.',
      },
    ],
  },
  {
    decade: "2010's",
    items: [
      {
        year: '2011',
        text: 'BSSM established the City Project Team. Since 2015, over 12,000 hours are given annually towards practical city improvement projects. KKPC A/G Church started leasing the Redding Civic Auditorium to create space for larger conferences and growing enrollment at BSSM. Eric and Candace Johnson become the Senior Pastors of KKPC A/G.',
      },
      {
        year: '2012',
        text: 'KKPC A/G acquired the Lake Blvd facility, home to many KKPC A/G ministry offices and the Transformation Center. KKPC A/G Church purchased the Collyer property, preparing for the future expansion of KKPC A/G.',
      },
      {
        year: '2013',
        text: 'Jesus Culture moved to Sacramento, CA and started their own church.',
      },
      {
        year: '2016',
        text: 'KKPC A/G Conservatory of the Arts founded to train and equip professional actors, musical theater performers, and dancers.',
      },
      {
        year: '2017',
        text: 'KKPC A/G School of Technology founded to equip kingdom-minded believers for in-demand IT careers. KKPC A/G Collyer Campus Expansion Project: Redding Planning Commission approved plan development and Environmental Impact Report. Redding City Council approved KKPC A/G to apply for development of a new church and school campus facilities.',
      },
      {
        year: '2018',
        text: "KKPC A/G's first global campaign, Arise & Build, launches.",
      },
    ],
  },
  {
    decade: "2020's",
    items: [
      {
        year: '2020',
        text: 'BSSM Online launches.',
      },
      {
        year: '2021',
        text: 'August 8 KKPC A/G breaks ground on the new Collyer Campus and site work begins. Dann Farrelly installed as Lead Pastor of KKPC A/G Redding after Eric and Candace leave, planting STUDIO Greenville in South Carolina.',
      },
      {
        year: '2022',
        text: 'KKPC A/G College established, bringing together KKPC A/G School of Technology, KKPC A/G Conservatory of the Arts, and KKPC A/G Music College.',
      },
    ],
  },
]

const moreCards = [
  {
    title: 'Our Beliefs',
    text: 'Read our cornerstones, statement of faith, and more.',
  },
  {
    title: 'Core Values',
    text: "Explore KKPC A/G Church's core values.",
  },
  {
    title: 'Rediscover KKPC A/G',
    text: 'Learn answers to common questions about KKPC A/G.',
  },
]
</script>

<style scoped>
/* ----------------------------------------------------------------
   KKPC A/G Church — About Page styles
   Color palette (replicated from kkpcag.com/about):
     - Charcoal/black hero background (#1a1a1a)
     - Light tan / cream sections (#f4eee5)
     - White-smoke sections (#f7f5f1)
     - Amber/copper accent (#9a6a3a)
   Fonts: serif fallbacks mirroring "Ivy Presto" + "Exo".
---------------------------------------------------------------- */

.bethel-about {
  --bethel-charcoal: #1a1a1a;
  --bethel-tan: #f4eee5;
  --bethel-smoke: #f7f5f1;
  --bethel-amber: #9a6a3a;
  font-family: 'Exo', 'Inter', system-ui, -apple-system, sans-serif;
}

.font-serif {
  font-family: 'IvyPresto', 'Playfair Display', 'Cormorant Garamond',
    Georgia, 'Times New Roman', serif;
}

.font-sans {
  font-family: 'Exo', 'Inter', system-ui, -apple-system, sans-serif;
}

/* Hero banner — dark charcoal background */
.hero-banner {
  background-color: var(--bethel-charcoal);
  background-image: linear-gradient(
      to bottom,
      rgba(0, 0, 0, 0.55) 0%,
      rgba(0, 0, 0, 0.85) 100%
    ),
    url('https://cdn.prod.website-files.com/613a860b6005a3bcb87aca81/62138be54ea9b286ac0bbd85_bethhel.jpg');
  background-size: cover;
  background-position: center;
}

.hero-title {
  font-size: clamp(3rem, 9vw, 8rem);
  letter-spacing: -0.02em;
}

/* Section backgrounds */
.bg-light-tan {
  background-color: var(--bethel-tan);
}

.bg-white-smoke {
  background-color: var(--bethel-smoke);
}

.bg-white {
  background-color: #ffffff;
}

/* Section spacing */
.section {
  width: 100%;
}

/* Mission heading caps accent */
.heading-caps {
  color: var(--bethel-amber);
}

.mission-line {
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}

.mission-line:last-of-type {
  display: block;
  text-align: center;
}

/* Timeline */
.timeline-wrapper {
  position: relative;
  padding-top: 1rem;
}

.timeline-line {
  z-index: 0;
}

.timeline-dot {
  box-shadow: 0 0 0 4px var(--bethel-tan);
}

/* Timeline entry alternating layout on md+ */
.timeline-entry:nth-child(even) .timeline-card {
  text-align: left;
}

.timeline-card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.timeline-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.08);
}

.timeline-year {
  color: var(--bethel-amber);
}

/* Button */
.bethel-button {
  letter-spacing: 0.15em;
}

/* Secondary navbar link hover */
.nav-link {
  position: relative;
}

.nav-link::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -4px;
  width: 0;
  height: 1px;
  background-color: var(--bethel-amber);
  transition: width 0.25s ease;
}

.nav-link:hover::after {
  width: 100%;
}

/* Responsive timeline tweaks */
@media (min-width: 768px) {
  .timeline-entry .timeline-card {
    display: inline-block;
    text-align: left;
    width: 100%;
    max-width: 460px;
  }

  .timeline-entry:nth-child(odd) .timeline-card {
    margin-right: auto;
  }

  .timeline-entry:nth-child(even) .timeline-card {
    margin-left: auto;
  }
}

/* Smooth scrolling for anchor links */
html {
  scroll-behavior: smooth;
}
</style>
