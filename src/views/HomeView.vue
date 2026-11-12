<script setup lang="ts">
import { ref } from 'vue';
import { RouterLink } from 'vue-router';

const openCases = ref([false, false]);
const toggleCase = (i: number) => {
  openCases.value[i] = !openCases.value[i];
};
const addr = ref<HTMLAnchorElement | null>(null);
const copyLabel = ref('Copy');
const EMAIL = 'info@amaliacicala.com';

const services = [
  { hash: '#consulting', title: 'Consulting & coaching', short: '1:1 sessions, Q&A, audits', icon: '<rect x="3.5" y="5" width="17" height="15" rx="2"/><path d="M3.5 10h17M8 3v4M16 3v4"/><path d="M8 14h3"/>' },
  { hash: '#marketing', title: 'Ad campaigns', short: 'Meta and YouTube ads', icon: '<circle cx="12" cy="12" r="8.5"/><circle cx="12" cy="12" r="5"/><circle cx="12" cy="12" r="1.5" class="fill"/>' },
  { hash: '#writing', title: 'Press, EPKs & websites', short: 'Press releases, EPKs, sites', icon: '<path d="M6 3.5h8l4 4V20.5H6z"/><path d="M14 3.5v4h4M9 12h6M9 15.5h6"/>' }
];

type LinkKind = 'web' | 'listen' | 'patreon';
const linkLabels: Record<LinkKind, string> = { web: 'their website', listen: 'Spotify', patreon: 'Patreon' };
const spotify = (id: string) => ({ kind: 'listen' as const, href: `https://open.spotify.com/artist/${id}` });
const web = (href: string) => ({ kind: 'web' as const, href });
const manager = { role: 'Manager', roleClass: 'lead' };
const team = { role: 'Co-manager', roleClass: 'co' };

const artists = [
  { name: 'Benthos', genre: 'Progressive metal, mathcore', country: 'ITA', ...manager, links: [web('https://benthos-band.com/'), spotify('0A7v88d7h8uYeGaBhflb45')] },
  { name: 'Earthside', genre: 'Progressive metal, post-rock, cinematic rock', country: 'USA', ...team, links: [web('https://www.earthsideband.com/'), spotify('6mRDRKsNautYuxybddnvgg')] },
  { name: 'Einar Solberg', genre: 'Progressive rock, orchestral, solo artist', country: 'NOR', ...team, links: [web('https://einarsolberg.com/'), spotify('20xK8nEhn71rTjjBNoR5nv')] },
  { name: 'Caligula\'s Horse', genre: 'Progressive metal', country: 'AUS', ...team, links: [web('https://www.caligulashorse.com/'), spotify('6Zd7AjXsoLaweP9FHyudVC')] },
  { name: 'Textures', genre: 'Progressive metal', country: 'NED', ...team, links: [web('https://texturesband.com/'), spotify('6v9XKyEf4HKmUMr3D6weIO')] },
  { name: 'Voyager', genre: 'Progressive metal, synth-pop (Eurovision 2023)', country: 'AUS', ...team, links: [web('https://www.voyagerau.com/'), spotify('16fltNcwTM5V9rnxIlcha4')] },
  { name: 'Unprocessed', genre: 'Progressive metalcore, modern metal', country: 'GER', ...team, links: [web('https://www.unprocessed.band/'), spotify('13GH7wviJQ9gfZmr1pXHS4')] },
  { name: 'Leprous', genre: 'Progressive metal', country: 'NOR', role: 'Patreon', roleClass: 'sage', links: [{ kind: 'patreon' as const, href: 'https://www.patreon.com/Leprous' }] }
];

function selectAddress() {
  if (!addr.value) return;
  const range = document.createRange();
  range.selectNodeContents(addr.value);
  const sel = window.getSelection();
  sel?.removeAllRanges();
  sel?.addRange(range);
  copyLabel.value = 'Selected';
}

async function copyMail() {
  try {
    await navigator.clipboard.writeText(EMAIL);
    copyLabel.value = 'Copied';
    setTimeout(() => (copyLabel.value = 'Copy'), 1600);
  } catch {
    selectAddress();
  }
}
</script>

<template>
  <header class="hero" id="top">
    <div class="wrap">
      <h1><span class="ln1">Amalia</span> <span class="ln2">Cicala</span></h1>
      <div class="hero-body">
        <div class="hero-text">
          <p class="hero-lede">I manage and market progressive and heavy bands, from long-term strategy and release plans to label relations and touring.</p>
          <div class="roles" aria-label="Disciplines"><span>Artist Management</span><span>Music Marketing</span><span>Touring</span><span>Photography</span></div>
          <p class="now">Based in <b>Milan</b>, working worldwide. Currently <b>Artist Manager at BANDS Management</b>, with artists from Italy, the USA, Norway, Australia, the Netherlands and Germany.</p>
          <div class="btns">
            <a class="btn solid" href="#roster">See who I work with</a>
            <a class="btn" href="#contact">Get in touch</a>
          </div>
        </div>
        <img class="portrait" src="/img/me/download.jpg" alt="Amalia Cicala at Download Festival" width="900" height="645">
      </div>
    </div>
  </header>

  <section class="block" id="about" aria-labelledby="about-h">
    <div class="wrap">
      <div class="sec-head">
        <div class="rail"><p class="label">What I do</p><figure class="rail-photo"><img src="/img/me/backstage-wide.jpg" alt="Amalia backstage with Benthos after a show" loading="lazy" width="900" height="600"></figure></div>
        <div>
          <h2 id="about-h">One person across the whole release cycle</h2>
          <p class="intro">Management comes first: finding the opportunities, planning each release and pushing it with the label and PR. From there I cover the marketing, the tour and the merch, so everything tells the same story.</p>
        </div>
      </div>
      <div class="services">
        <div class="svc"><h3>Artist management</h3><p>Finding opportunities, planning and managing releases, ideas and strategy for growth, and liaising with labels and PR.</p></div>
        <div class="svc"><h3>Marketing &amp; socials</h3><p>Marketing and social plans for every release and tour, and Meta campaigns for streams, awareness, tickets and merch, in English, Italian and German.</p></div>
        <div class="svc"><h3>Booking &amp; touring</h3><p>Booking festivals, shows and tours, then tour managing them: advancing, budgets, routing, travel, carnets and customs.</p></div>
        <div class="svc"><h3>Content &amp; merch</h3><p>Release copy, newsletters, captions, short-form video and graphics. Merch, physical releases and stock planning.</p></div>
      </div>
    </div>
  </section>

  <section class="block" id="roster" aria-labelledby="roster-h">
    <div class="wrap">
      <div class="sec-head">
        <div class="rail"><p class="label">Artists</p><figure class="rail-photo"><img src="/img/me/benthos-unprocessed-wall.jpg" alt="Amalia in front of Benthos and Unprocessed posters on a festival wall" loading="lazy" width="640" height="1138"><figcaption>Benthos and Unprocessed, side by side</figcaption></figure></div>
        <div>
          <h2 id="roster-h">Who I work with</h2>
          <p class="intro">Benthos I manage on my own, covering management, marketing, booking and tour management. The other artists I co-manage as part of the <a class="agency" href="https://bands.management" target="_blank" rel="noopener"><b>BANDS Management</b></a> team, working with them day to day on releases, campaigns, touring and merch. With the team I also run Leprous' Patreon.</p>
          <div class="photo-row">
            <figure><img src="/img/me/voyager-euroblast.jpg" alt="Amalia backstage with Voyager at Euroblast" loading="lazy" width="900" height="600"><figcaption>Voyager, Euroblast</figcaption></figure>
            <figure><img src="/img/me/earthside-2.jpg" alt="Amalia backstage with Earthside" loading="lazy" width="900" height="600"><figcaption>Earthside</figcaption></figure>
            <figure><img src="/img/me/unprocessed-festival.jpg" alt="Amalia with Unprocessed and the team at a festival" loading="lazy" width="900" height="600"><figcaption>Unprocessed</figcaption></figure>
          </div>
        </div>
      </div>
      <div class="legend" aria-hidden="true"><span class="pill lead">Manager</span><span>sole management</span><span class="pill co">Co-manager</span><span>BANDS team</span><span class="pill sage">Patreon</span><span>supporter community, BANDS team</span></div>
      <ul class="roster">
        <li v-for="artist in artists" :key="artist.name">
          <span class="name">{{ artist.name }}</span>
          <span class="genre">{{ artist.genre }}</span>
          <span class="cc">{{ artist.country }}</span>
          <span class="role"><span :class="['pill', artist.roleClass]">{{ artist.role }}</span></span>
          <span class="links">
            <a
              v-for="link in artist.links"
              :key="link.kind"
              class="icon-link"
              :href="link.href"
              target="_blank"
              rel="noopener"
              :title="`${artist.name} on ${linkLabels[link.kind]}`"
              :aria-label="`${artist.name} on ${linkLabels[link.kind]}`"
            >
              <svg v-if="link.kind === 'web'" viewBox="0 0 24 24" aria-hidden="true"><circle cx="12" cy="12" r="9" /><path d="M3 12h18M12 3c2.5 2.7 3.8 5.7 3.8 9s-1.3 6.3-3.8 9c-2.5-2.7-3.8-5.7-3.8-9S9.5 5.7 12 3z" /></svg>
              <svg v-else-if="link.kind === 'listen'" viewBox="0 0 24 24" aria-hidden="true"><circle cx="12" cy="12" r="9" /><path d="M10 8.5v7l6-3.5z" class="fill" /></svg>
              <svg v-else viewBox="0 0 24 24" aria-hidden="true"><path d="M12 20s-7-4.4-7-10a4 4 0 0 1 7-2.6A4 4 0 0 1 19 10c0 5.6-7 10-7 10z" /></svg>
            </a>
          </span>
        </li>
      </ul>
      <div class="roster-photos-m">
          <div class="photo-row">
            <figure><img src="/img/me/voyager-euroblast.jpg" alt="Amalia backstage with Voyager at Euroblast" loading="lazy" width="900" height="600"><figcaption>Voyager, Euroblast</figcaption></figure>
            <figure><img src="/img/me/earthside-2.jpg" alt="Amalia backstage with Earthside" loading="lazy" width="900" height="600"><figcaption>Earthside</figcaption></figure>
            <figure><img src="/img/me/unprocessed-festival.jpg" alt="Amalia with Unprocessed and the team at a festival" loading="lazy" width="900" height="600"><figcaption>Unprocessed</figcaption></figure>
          </div>
        <figure class="rail-photo"><img src="/img/me/benthos-unprocessed-wall.jpg" alt="Amalia in front of Benthos and Unprocessed posters on a festival wall" loading="lazy" width="640" height="1138"><figcaption>Benthos and Unprocessed, side by side</figcaption></figure>
      </div>
    </div>
  </section>

  <section class="block" id="cv" aria-labelledby="cv-h">
    <div class="wrap">
      <div class="sec-head">
        <p class="label">Experience</p>
        <div>
          <h2 id="cv-h">Over ten years around bands</h2>
          <p class="intro">From volunteering at shows and festivals to a music business degree and full-time artist management.</p>
        </div>
      </div>
      <ol class="snapshot">
        <li><span class="when-sm">2015</span><h3>First gigs</h3><p>Volunteering on merch and street teams</p></li>
        <li><span class="when-sm">2018 – 2021</span><h3>BA (Hons) Commercial Music</h3><p>University of the West of Scotland · First Class Honours</p></li>
        <li><span class="when-sm">2022</span><h3>Artist Manager</h3><p>Independent · Milan, managing Benthos</p></li>
        <li><span class="when-sm">2024</span><h3>Event Production Programme</h3><p>Legend Club, Milan · 1 of 15 selected</p></li>
        <li><span class="when-sm">2025 – now</span><h3>Artist Manager</h3><p>BANDS Management</p></li>
      </ol>
      <div class="btns services-cta">
        <RouterLink class="btn solid" to="/experience">See full experience</RouterLink>
      </div>
    </div>
  </section>

  <section class="block" id="work" aria-labelledby="work-h">
    <div class="wrap">
      <div class="sec-head">
        <p class="label">Work</p>
        <div>
          <h2 id="work-h">Examples of my work</h2>
          <p class="intro">Two projects chosen to show the range of the job: running a band end to end, and releasing an album without a label. Below them, a few of my most recent freelance clients.</p>
        </div>
      </div>

      <div class="cases">
        <article class="case">
          <div class="case-side">
            <span class="who">Benthos</span>
            <span class="yr">2022 – now</span>
            <span class="role-line">Sole manager</span>
            <div class="tags"><span class="pill">Management</span><span class="pill">Booking</span><span class="pill">Tour management</span><span class="pill">Digital marketing</span><span class="pill">Socials &amp; visuals</span></div>
            <div class="case-more case-more-photos" :class="{ open: openCases[0] }"><div class="case-more-inner"><div class="case-photos">
              <figure class="rail-photo"><img src="/img/me/benthos-sony.jpg" alt="Amalia with Benthos outside Sony Music" loading="lazy" width="640" height="800"><figcaption>With Benthos at Sony Music</figcaption></figure>
              <figure class="rail-photo"><img src="/img/me/benthos-insideout.jpg" alt="Amalia with Benthos and the InsideOut Music team at the label office" loading="lazy" width="900" height="600"><figcaption>With Benthos and the InsideOut Music team</figcaption></figure>
            </div></div></div>
          </div>
          <div>
            <h3 class="case-title" @click="toggleCase(0)"><i>From Nothing</i>, and a first year on European stages</h3>
            <p class="summary">I'm the sole manager of Italian prog metal band <strong>Benthos</strong>, covering every side of the job: management, marketing, booking and the road. Since their InsideOut Music debut that has meant festival bills, major support tours and a first UK headline run.</p>
            <button type="button" class="case-toggle" :aria-expanded="openCases[0]" aria-controls="case-0" @click="toggleCase(0)"><span>{{ openCases[0] ? 'Show less' : 'See what I did' }}</span><span class="case-toggle-icon" aria-hidden="true"></span></button>
            <div id="case-0" class="case-more" :class="{ open: openCases[0] }" :inert="!openCases[0]"><div class="case-more-inner">
            <p class="swipe-hint" aria-hidden="true">Swipe for more →</p>
            <div class="case-cols">
              <div><h4>What I do</h4><ul>
                <li>Find opportunities and shape the plan for the band's growth</li>
                <li>Manage releases with InsideOut Music and liaise with PR</li>
                <li>Plan the marketing and socials, and create their visuals</li>
                <li>Book their festivals, headline shows and support tours</li>
                <li>Tour manage on the road: advancing, budgets, logistics and customs</li>
                <li>Build and run Meta campaigns for streams and awareness as well as ticket sales, with copy in English, Italian and German</li>
                <li>Plan merch stock from past sell-through by show type</li>
              </ul></div>
              <div><h4>Results</h4><ul>
                <li><i>From Nothing</i> listed in Loudwire's 11 Best Prog Metal Albums of 2025</li>
                <li>Metal Hammer UK print feature, with my band photo; “As A Cordyceps” shortlisted for its Best Metal Songs of 2025</li>
                <li>Four Prog Report Awards 2025 nominations, including Breakthrough of the Year, plus Progspace Awards nominations</li>
                <li>Kerrang! Radio play and a Guitar World Editors' Pick</li>
                <li>Festivals including Euroblast, Midsummer Prog, RADAR and ArcTanGent</li>
                <li>Support slots with Between The Buried And Me, Protest The Hero, Stick To Your Guns and Haken</li>
              </ul></div>
            </div>
            <blockquote class="quote"><p>“The Italian prog metal merchants questioning the universe.”</p><cite>Metal Hammer UK</cite></blockquote>
            </div></div>
          </div>
        </article>

        <article class="case">
          <div class="case-side">
            <span class="who">Unprocessed</span>
            <span class="yr">2025</span>
            <span class="role-line">Co-manager</span>
            <div class="tags"><span class="pill">Independent release</span><span class="pill">Physical &amp; retail</span><span class="pill">Fan events</span><span class="pill">Partnerships</span></div>
            <div class="case-more case-more-photos" :class="{ open: openCases[1] }"><div class="case-more-inner"><div class="case-photos">
              <figure class="rail-photo"><img src="/img/me/unprocessed-release.jpg" alt="Amalia with Unprocessed and the team at the Angel release party in London" loading="lazy" width="900" height="600"><figcaption><i>Angel</i> release party, London</figcaption></figure>
            </div></div></div>
          </div>
          <div>
            <h3 class="case-title" @click="toggleCase(1)">Releasing <i>Angel</i> without a label</h3>
            <p class="summary">With German progressive metalcore band <strong>Unprocessed</strong>, our biggest project together was <i>Angel</i>, an independent album, where the management team took on everything a label would normally do, then turned release week into a run of Halloween events.</p>
            <button type="button" class="case-toggle" :aria-expanded="openCases[1]" aria-controls="case-1" @click="toggleCase(1)"><span>{{ openCases[1] ? 'Show less' : 'See what I did' }}</span><span class="case-toggle-icon" aria-hidden="true"></span></button>
            <div id="case-1" class="case-more" :class="{ open: openCases[1] }" :inert="!openCases[1]"><div class="case-more-inner">
            <p class="swipe-hint" aria-hidden="true">Swipe for more →</p>
            <div class="case-cols">
              <div><h4>What we did</h4><ul>
                <li>Managed vinyl and CD manufacturing: three double-vinyl variants, CD and a deluxe box</li>
                <li>Set up retail with record shops and EMP</li>
                <li>Planned a week of release events across the UK and Germany</li>
                <li>Partnered with Schott on two custom Unprocessed wines, with wine tastings at the in-store signings</li>
                <li>Created a co-branded lager with Blondies Brewery, named after the track “Head in the Clouds”</li>
              </ul></div>
              <div><h4>Release week</h4><ul class="dates">
                <li><span>30 Oct</span>Halloween release party, Blondies Brewery, London</li>
                <li><span>31 Oct</span>In-store signing, Rough Trade West, London</li>
                <li><span>3 Nov</span>In-store signing, EMP, Leipzig</li>
                <li><span>4 Nov</span>In-store signing, Rough Trade, Berlin</li>
                <li><span>5 Nov</span>In-store signing, Cruise Records, Hamburg</li>
                <li><span>6 Nov</span>Halloween release party, Kreativfabrik, Wiesbaden</li>
              </ul></div>
            </div>
            <blockquote class="quote"><p>“…attention-grabbing contrasts that persuade you that <i>Angel</i> might be the quartet's best work.”</p><cite>Kerrang!</cite></blockquote>
            </div></div>
          </div>
        </article>
      </div>

      <div class="freelance" aria-labelledby="freelance-h">
        <div class="freelance-head">
          <h3 class="sub-sm" id="freelance-h">Recent freelance clients</h3>
          <p>The latest of many: digital marketing campaigns for independent bands from the Milan scene.</p>
        </div>
        <ul class="fl-list">
          <li><span class="fl-name">Margin Code</span><span class="fl-genre">Progressive metal · Milan</span></li>
          <li><span class="fl-name">Omens Before Hysteria</span><span class="fl-genre">Deathcore · Milan</span></li>
          <li><span class="fl-name">Furor Gallico</span><span class="fl-genre">Folk metal · Milan</span></li>
        </ul>
      </div>
    </div>
  </section>

  <section class="block" id="services" aria-labelledby="services-h">
    <div class="wrap">
      <div class="sec-head">
        <p class="label">Services</p>
        <div>
          <h2 id="services-h">Work with me</h2>
          <p class="intro">Consulting, ad campaigns and press materials for bands and artists, especially in metal and heavy music. In English and Italian, from Milan to anywhere.</p>
        </div>
      </div>
      <nav class="svc-jump svc-preview" aria-label="Services">
        <RouterLink v-for="sv in services" :key="sv.hash" :to="{ path: '/services', hash: sv.hash }">
          <span class="jump-icon" aria-hidden="true"><svg viewBox="0 0 24 24" v-html="sv.icon"></svg></span>
          <span class="jump-t"><b>{{ sv.title }}</b><small>{{ sv.short }}</small></span>
          <span class="jump-arrow" aria-hidden="true">→</span>
        </RouterLink>
      </nav>
      <div class="btns services-cta">
        <RouterLink class="btn solid" to="/services">See all services</RouterLink>
      </div>
      <div class="photo-band svc-band">
        <div>
          <h3 id="photo-h">Also behind the camera</h3>
          <p>Concert and music photographer based in Milan, shooting shows, festivals and press photos in Italy and on tour across Europe.</p>
        </div>
        <RouterLink class="btn" to="/photos">View photography →</RouterLink>
      </div>
    </div>
  </section>

  <section class="contact" id="contact" aria-labelledby="contact-h">
    <div class="wrap">
      <div class="contact-grid">
        <div>
          <p class="label">Contact</p>
          <h2 id="contact-h" class="contact-h">Working on a release or a tour? <em>Let's talk.</em></h2>
          <p class="based">Based in Milan, Italy · Available worldwide</p>
          <p class="contact-svc">I offer 1:1 consultations, Meta and YouTube ad campaigns, press releases, EPKs and websites. <RouterLink to="/services">See all services →</RouterLink></p>
          <div class="mail">
            <a ref="addr" class="addr" href="mailto:info@amaliacicala.com">info@amaliacicala.com</a>
            <button class="copy" id="copyMail" type="button" @click="copyMail">{{ copyLabel }}</button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
