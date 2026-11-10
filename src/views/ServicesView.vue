<script setup lang="ts">
import { ref } from 'vue';

const EMAIL = 'amalia@bands.management';
const addr = ref<HTMLAnchorElement | null>(null);
const copyLabel = ref('Copy');
async function copyMail() {
  try {
    await navigator.clipboard.writeText(EMAIL);
    copyLabel.value = 'Copied';
    setTimeout(() => (copyLabel.value = 'Copy'), 1600);
  } catch {
    if (!addr.value) return;
    const range = document.createRange();
    range.selectNodeContents(addr.value);
    const sel = window.getSelection();
    sel?.removeAllRanges();
    sel?.addRange(range);
    copyLabel.value = 'Selected';
  }
}

const mail = (subject: string) => `mailto:${EMAIL}?subject=${encodeURIComponent(subject)}`;

// Simple line icons (24×24, drawn with stroke)
const icons: Record<string, string> = {
  calendar: '<rect x="3.5" y="5" width="17" height="15" rx="2"/><path d="M3.5 10h17M8 3v4M16 3v4"/><path d="M8 14h3"/>',
  question: '<path d="M4 5.5h16v10H10l-4 3.5v-3.5H4z"/><path d="M10 9a2 2 0 1 1 2.8 1.8c-.5.3-.8.7-.8 1.2"/><circle cx="12" cy="13.6" r=".4" class="fill"/>',
  compass: '<circle cx="12" cy="12" r="8.5"/><path d="M15.5 8.5l-2 5-5 2 2-5z"/>',
  search: '<circle cx="10.5" cy="10.5" r="6"/><path d="M15 15l5 5"/>',
  target: '<circle cx="12" cy="12" r="8.5"/><circle cx="12" cy="12" r="5"/><circle cx="12" cy="12" r="1.5" class="fill"/>',
  video: '<rect x="3" y="6" width="18" height="12" rx="3"/><path d="M10.5 9.5v5l4-2.5z" class="fill"/>',
  chart: '<path d="M4 20h16"/><path d="M7 16v-4M12 16V8M17 16v-7"/>',
  doc: '<path d="M6 3.5h8l4 4V20.5H6z"/><path d="M14 3.5v4h4M9 12h6M9 15.5h6"/>',
  folder: '<path d="M3.5 7V18.5h17V8.5h-8l-2-2h-7z"/><path d="M8 13h8"/>',
  browser: '<rect x="3" y="4.5" width="18" height="15" rx="2"/><path d="M3 9h18"/><circle cx="6" cy="6.8" r=".5" class="fill"/><circle cx="8" cy="6.8" r=".5" class="fill"/>'
};

const ratios: Record<string, number> = { meta: 155 / 160, facebook: 808 / 160, instagram: 217 / 160, youtube: 716 / 160, 'google-ads': 427 / 160 };

const stats = [
  { n: '10', unit: 'years', text: 'working with bands and artists' },
  { n: '7', unit: 'years', text: 'running Meta ad campaigns' },
  { n: '15+', unit: 'artists', text: 'worked with internationally' },
  { n: '20+', unit: 'release campaigns', text: 'planned and run for my artists' }
];

interface Item {
  icon: string;
  title: string;
  text: string;
  links?: { label: string; href: string }[];
}

interface Group {
  id: string;
  label: string;
  title: string;
  short: string;
  photo: { src: string; alt: string; w: number; h: number };
  intro: string;
  facts: string[];
  platforms?: { name: string; file: string; h: number }[];
  items: Item[];
  steps: { title: string; text: string }[];
  cta: { label: string; href: string };
}

const groups: Group[] = [
  {
    id: 'consulting',
    label: 'Consulting',
    title: 'Consulting & coaching',
    short: '1:1 sessions, Q&A, audits',
    photo: { src: '/img/me/benthos-sony.jpg', alt: 'Amalia with Benthos outside Sony Music', w: 640, h: 800 },
    intro:
      'One-to-one sessions for bands and artists. Bring your questions, your plans or your problems, and leave with clear next steps.',
    facts: ['45-minute video call', 'Written recap within 48 hours'],
    items: [
      { icon: 'calendar', title: 'Release & campaign mentoring', text: 'Regular sessions while you plan and run a release or a tour: timeline, assets, budget, what to do this week and what can wait.' },
      { icon: 'question', title: 'Music industry Q&A', text: 'Ask anything about how the industry works: labels, distribution, PROs, booking agents, PR, festivals, contracts and funding.' },
      { icon: 'compass', title: 'Coaching & next steps', text: 'An honest look at where you are and where you want to be, with clear next steps, improvements and the right partners to approach.' },
      { icon: 'search', title: 'Audits', text: 'A review of your socials, your music and release strategy or your brand: what works, what doesn’t and what to change first.' }
    ],
    steps: [
      { title: 'Book your session', text: 'Pick the type of session. Questions first? Email me before you book.' },
      { title: '45-minute call', text: 'We get straight to work on your questions, plans and next steps.' },
      { title: 'Your recap', text: 'Within 48 hours you get a bespoke document with takeaways, feedback and everything we covered.' }
    ],
    cta: { label: 'Book a consultation', href: mail('Consultation') }
  },
  {
    id: 'marketing',
    label: 'Digital marketing',
    title: 'Ad campaigns',
    short: 'Meta and YouTube ads',
    photo: { src: '/img/me/voyager-euroblast.jpg', alt: 'Amalia backstage with Voyager at Euroblast', w: 900, h: 600 },
    intro:
      'Seven years of running Meta campaigns for music. I keep up with every change to the platform and the algorithm, so your budget goes where it works.',
    facts: ['Checked and optimised daily', 'Updates and analytics throughout'],
    platforms: [
      { name: 'Meta', file: 'meta', h: 40 },
      { name: 'Facebook', file: 'facebook', h: 21 },
      { name: 'Instagram', file: 'instagram', h: 40 },
      { name: 'YouTube', file: 'youtube', h: 22 },
      { name: 'Google Ads', file: 'google-ads', h: 30 }
    ],
    items: [
      { icon: 'target', title: 'Meta ads: Facebook & Instagram', text: 'Campaigns for streams, awareness, ticket sales, pre-saves and merch, built per market and audience, with ad copy written in the language of the audience you’re targeting.' },
      { icon: 'video', title: 'YouTube ads', text: 'Video campaigns to grow views and subscribers around a single, a music video or a tour announcement.' },
      { icon: 'chart', title: 'Strategy & reporting', text: 'Audience research and budget planning before launch, then regular updates and analytics while the campaign runs.' }
    ],
    steps: [
      { title: 'Brief', text: 'Your goal, release or tour dates, markets and budget.' },
      { title: 'Launch', text: 'I research the audience, write the ads and set up the campaign.' },
      { title: 'Daily optimisation', text: 'I check the campaign every day and adjust it whenever it needs it.' },
      { title: 'Updates & analytics', text: 'You get updates and results as the campaign goes, not just at the end.' }
    ],
    cta: { label: 'Start a campaign', href: mail('Ad campaign') }
  },
  {
    id: 'writing',
    label: 'Press & assets',
    title: 'Press, EPKs & websites',
    short: 'Press releases, EPKs, sites',
    photo: { src: '/img/me/benthos-insideout.jpg', alt: 'Amalia with Benthos and the InsideOut Music team', w: 900, h: 600 },
    intro: 'The materials that get you taken seriously by press, bookers, labels and festivals.',
    facts: ['Free 10-minute kick-off call after booking', 'In English and Italian'],
    items: [
      { icon: 'doc', title: 'Press releases', text: 'Release and tour announcements written for press and webzines, in Italian and English.' },
      { icon: 'folder', title: 'EPKs', text: 'An electronic press kit with your bio, music, videos, photos, press quotes and live history, ready to send with every pitch. Made from the point of view of someone who works in the industry, so it shows exactly what bookers, labels and press look for and care about most.' },
      { icon: 'browser', title: 'Websites', text: 'A clean, fast band or artist website that is easy to update, with your music, shows, merch and contacts in one place. I code them myself, including this one.', links: [{ label: 'This website', href: 'https://amaliacicala.com/' }, { label: 'Benthos', href: 'https://benthos-band.com/' }, { label: 'ProAudio Italia', href: 'https://www.proaudioitalia.it/' }] }
    ],
    steps: [
      { title: 'Book the service', text: 'Choose a press release, an EPK or a website.' },
      { title: '10-minute call', text: 'A free short call to understand exactly what you need.' },
      { title: 'I write or build it', text: 'Your press release, EPK or website, ready to use.' }
    ],
    cta: { label: 'Order press materials', href: mail('Press release / EPK / website') }
  }
];

const artists = ['Benthos', 'Earthside', 'Einar Solberg', 'Caligula’s Horse', 'Textures', 'Voyager', 'Unprocessed', 'Leprous', 'Margin Code', 'Omens Before Hysteria', 'Furor Gallico'];
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
            <a v-for="g in groups" :key="g.id" :href="`#${g.id}`">
              <span class="jump-icon" aria-hidden="true"><svg viewBox="0 0 24 24" v-html="icons[g.items[0].icon]"></svg></span>
              <span class="jump-t"><b>{{ g.title }}</b><small>{{ g.short }}</small></span>
              <span class="jump-arrow" aria-hidden="true">↓</span>
            </a>
          </nav>
        </div>
      </div>
      <ul class="stats">
        <li v-for="s in stats" :key="s.unit + s.text">
          <span class="stat-n">{{ s.n }}</span>
          <span class="stat-t"><b>{{ s.unit }}</b>{{ s.text }}</span>
        </li>
      </ul>
    </div>
  </header>

  <section class="block marquee-block" aria-label="Artists I’ve worked with">
    <p class="marquee-label wrap">Artists I’ve worked with</p>
    <div class="marquee" aria-hidden="true">
      <div class="marquee-track">
        <span v-for="n in 2" :key="n" class="marquee-set">
          <span v-for="a in artists" :key="a + n">{{ a }}<i>•</i></span>
        </span>
      </div>
    </div>
    <p class="sr-only">{{ artists.join(', ') }}</p>
  </section>

  <section v-for="g in groups" :id="g.id" :key="g.id" class="block offer" :aria-labelledby="`${g.id}-h`">
    <div class="wrap">
      <div class="sec-head">
        <div class="rail">
          <p class="label">{{ g.label }}</p>
          <figure class="rail-photo"><img :src="g.photo.src" :alt="g.photo.alt" :width="g.photo.w" :height="g.photo.h" loading="lazy" /></figure>
        </div>
        <div>
          <h2 :id="`${g.id}-h`">{{ g.title }}</h2>
          <p class="intro">{{ g.intro }}</p>
          <ul class="facts">
            <li v-for="f in g.facts" :key="f">{{ f }}</li>
          </ul>
          <div v-if="g.platforms" class="platforms">
            <span class="platforms-label">Platforms</span>
            <ul class="logos" aria-label="Platforms">
              <li v-for="pl in g.platforms" :key="pl.file">
                <span
                  class="logo"
                  role="img"
                  :aria-label="pl.name"
                  :style="{ '--logo': `url(/img/logos/${pl.file}.png)`, height: pl.h + 'px', aspectRatio: String(ratios[pl.file]) }"
                ></span>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <ul :class="['offer-list', `n${g.items.length}`]">
        <li v-for="item in g.items" :key="item.title">
          <span class="offer-icon" aria-hidden="true"><svg viewBox="0 0 24 24" v-html="icons[item.icon]"></svg></span>
          <h3>{{ item.title }}</h3>
          <p>{{ item.text }}</p>
          <ul v-if="item.links" class="built">
            <li v-for="l in item.links" :key="l.label"><a :href="l.href" target="_blank" rel="noopener">{{ l.label }} ↗</a></li>
          </ul>
        </li>
      </ul>

      <div class="how">
        <h3 class="sub-sm">How it works</h3>
        <ol :class="['steps', `n${g.steps.length}`]">
          <li v-for="(s, i) in g.steps" :key="s.title">
            <span class="step-n">{{ String(i + 1).padStart(2, '0') }}</span>
            <h4>{{ s.title }}</h4>
            <p>{{ s.text }}</p>
          </li>
        </ol>
        <div class="btns services-cta">
          <a class="btn solid" :href="g.cta.href">{{ g.cta.label }}</a>
          <a class="btn" :href="mail('Question')">Ask a question first</a>
        </div>
      </div>
    </div>
  </section>

  <section class="contact" aria-labelledby="svc-contact-h">
    <div class="wrap">
      <p class="label">Contact</p>
      <h2 id="svc-contact-h" class="contact-h">Questions about a service? <em>Ask me first.</em></h2>
      <p class="based">Based in Milan, Italy · Working worldwide in English and Italian</p>
      <div class="mail">
        <a ref="addr" class="addr" :href="mail('Question')">{{ EMAIL }}</a>
        <button class="copy" type="button" @click="copyMail">{{ copyLabel }}</button>
      </div>
    </div>
  </section>
</template>
