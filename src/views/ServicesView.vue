<script setup lang="ts">
import { RouterLink } from 'vue-router';

const groups = [
  {
    id: 'consulting',
    label: 'Consulting',
    title: 'Consulting & coaching',
    intro:
      'One-to-one support for bands and artists, from a single call to ongoing guidance through a release. Bring your questions, your plans or your problems.',
    items: [
      {
        title: 'Release & campaign mentoring',
        text: 'Regular 1:1 calls while you plan and run a release or a tour: timeline, assets, budget, what to do this week and what can wait.'
      },
      {
        title: 'Music industry Q&A',
        text: 'Ask anything about how the industry works: labels, distribution, PROs, booking agents, PR, festivals, contracts and funding.'
      },
      {
        title: 'Coaching & next steps',
        text: 'An honest look at where you are and where you want to be, with clear next steps, improvements and the right partners to approach.'
      },
      {
        title: 'Audits',
        text: 'A written review of your socials, your music and release strategy or your brand, with what works, what doesn’t and what to change first.'
      }
    ]
  },
  {
    id: 'marketing',
    label: 'Digital marketing',
    title: 'Ad campaigns',
    intro:
      'Ten years of running Meta campaigns for music. I keep up with every change to the platform and the algorithm, so your budget goes where it works.',
    items: [
      {
        title: 'Meta ads: Facebook & Instagram',
        text: 'Campaigns for streams, awareness, ticket sales, pre-saves and merch, built per market and audience, with copy in English, Italian or German.'
      },
      {
        title: 'YouTube ads',
        text: 'Video campaigns to grow views and subscribers around a single, a music video or a tour announcement.'
      },
      {
        title: 'Strategy & reporting',
        text: 'Audience research and budget planning before launch, then clear reports on what each euro did and what to change.'
      }
    ]
  },
  {
    id: 'writing',
    label: 'Press & assets',
    title: 'Press, EPKs & websites',
    intro: 'The materials that get you taken seriously by press, bookers, labels and festivals.',
    items: [
      {
        title: 'Press releases',
        text: 'Release and tour announcements written for press and webzines, in Italian and English.'
      },
      {
        title: 'EPKs',
        text: 'An electronic press kit with your bio, music, videos, photos, press quotes and live history, ready to send with every pitch.'
      },
      {
        title: 'Websites',
        text: 'A clean, fast band or artist website that is easy to update, with your music, shows, merch and contacts in one place.'
      }
    ]
  }
];

const steps = [
  { title: 'Get in touch', text: 'Tell me who you are, what you’re working on and what you need.' },
  { title: 'Intro call', text: 'A short free call to see if and how I can help.' },
  { title: 'Proposal', text: 'A clear plan with what’s included, timing and price.' },
  { title: 'Work together', text: 'Calls, campaigns or deliverables, with updates as we go.' }
];
</script>

<template>
  <header class="block photos-head" aria-labelledby="services-h">
    <div class="wrap">
      <div class="sec-head">
        <p class="label">Services</p>
        <div>
          <h1 id="services-h" class="page-h">Work with me</h1>
          <p class="intro">
            Consulting, digital marketing and press materials for bands and artists, especially in metal and heavy music.
            Independent or signed, starting out or touring. Based in Milan, working remotely worldwide, in English and Italian.
          </p>
          <nav class="svc-jump" aria-label="Services on this page">
            <a v-for="g in groups" :key="g.id" :href="`#${g.id}`">{{ g.title }}</a>
          </nav>
        </div>
      </div>
    </div>
  </header>

  <section v-for="g in groups" :id="g.id" :key="g.id" class="block offer" :aria-labelledby="`${g.id}-h`">
    <div class="wrap">
      <div class="sec-head">
        <p class="label">{{ g.label }}</p>
        <div>
          <h2 :id="`${g.id}-h`">{{ g.title }}</h2>
          <p class="intro">{{ g.intro }}</p>
        </div>
      </div>
      <ul :class="['offer-list', `n${g.items.length}`]">
        <li v-for="item in g.items" :key="item.title">
          <h3>{{ item.title }}</h3>
          <p>{{ item.text }}</p>
        </li>
      </ul>
    </div>
  </section>

  <section class="block offer" aria-labelledby="how-h">
    <div class="wrap">
      <div class="sec-head">
        <p class="label">How it works</p>
        <div>
          <h2 id="how-h">From first message to results</h2>
          <p class="intro">Every project is quoted individually, so you only pay for what you need.</p>
        </div>
      </div>
      <ol class="steps">
        <li v-for="(s, i) in steps" :key="s.title">
          <span class="step-n">{{ String(i + 1).padStart(2, '0') }}</span>
          <h3>{{ s.title }}</h3>
          <p>{{ s.text }}</p>
        </li>
      </ol>
      <div class="btns services-cta">
        <RouterLink class="btn solid" :to="{ path: '/', hash: '#contact' }">Get in touch</RouterLink>
        <RouterLink class="btn" :to="{ path: '/', hash: '#roster' }">See who I work with</RouterLink>
      </div>
    </div>
  </section>
</template>
