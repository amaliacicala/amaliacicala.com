<script setup lang="ts">
import { RouterLink } from 'vue-router';
</script>

<template>
  <section class="block cv-page" id="cv" aria-labelledby="cv-h">
    <div class="wrap">
      <div class="sec-head">
        <p class="label">Experience</p>
        <div>
          <h1 id="cv-h" class="page-h">Experience</h1>
          <p class="intro">Artist manager and music marketer based in Milan. Ten years working with bands and artists, from volunteering at shows to managing international acts.</p>
        </div>
      </div>
      <div class="cv">
        <ol class="timeline" reversed>
          <li><span class="when">2025 – now</span><div>
            <h3>Artist Manager</h3>
            <p class="org">BANDS Management · Worthing, UK · Full-time, hybrid</p>
            <p class="d">Sole manager of Benthos, now as part of the agency, covering management, marketing, booking and tour management. Part of the management team for Earthside, Einar Solberg, Caligula's Horse, Textures, Voyager and Unprocessed, working on releases, campaigns, touring and merch. Runs the Leprous Patreon with the team: content plan and schedule, Q&amp;As, reworking the membership tiers, optimising the page and supporting the community.</p>
          </div></li>
          <li><span class="when">2023 – 2025</span><div>
            <h3>Artist Manager</h3>
            <p class="org">Independent · Milan</p>
            <p class="d">Started managing Benthos on my own in 2023, covering management, marketing, booking and tour management, before joining BANDS Management.</p>
          </div></li>
          <li><span class="when">2020 – now</span><div>
            <h3>Music Marketing &amp; Digital Management</h3>
            <p class="org">Freelance · Remote</p>
            <p class="d">Services for independent artists alongside agency work:</p>
            <ul class="d-list">
              <li>Social media campaigns for visibility, streams and tour promotion</li>
              <li>Digital management, including content distribution and PRO support</li>
              <li>Design for promo materials, and photo and video content</li>
              <li>Coaching on fan growth, branding and messaging</li>
            </ul>
          </div></li>
          <li><span class="when">2023 – now</span><div>
            <h3>Concert Photographer</h3>
            <p class="org">Freelance · Milan &amp; worldwide</p>
            <p class="d">Live photography for bands and venues.</p>
          </div></li>
        </ol>
        <aside class="kit" aria-label="Toolkit">
          <div class="kit-group"><h3>Marketing</h3><div class="chips"><span>Meta Ads Manager</span><span>Meta Pixel</span><span>Google Ads</span><span>Google Analytics</span><span>SEO</span><span>Feature.fm</span><span>Bandsintown</span><span>Songkick</span></div></div>
          <div class="kit-group"><h3>Content</h3><div class="chips"><span>Photoshop</span><span>Illustrator</span><span>Lightroom</span><span>Premiere Pro</span><span>CapCut</span><span>Meta Business Suite</span><span>Mailchimp</span><span>YouTube Studio</span><span>Photography</span></div></div>
          <div class="kit-group"><h3>Operations</h3><div class="chips"><span>Google Workspace</span><span>Notion</span><span>Excel</span><span>Daysheets</span><span>Shopify</span><span>SumUp POS</span><span>Discord</span><span>ATA Carnet</span></div></div>
          <div class="kit-group"><h3>Languages</h3><div class="chips"><span>Italian · native</span><span>English · C2</span><span>German · B1</span></div></div>
        </aside>
      </div>

      <div class="volunteer" aria-labelledby="vol-h">
        <h3 class="sub-sm" id="vol-h">Volunteering</h3>
        <ul class="vol-list">
          <li>
            <span class="when-sm">2019 – 2024</span>
            <h4>Volunteer Steward</h4>
            <p class="org">ArcTanGent Festival, Bristol</p>
            <p class="d">Three editions as a volunteer steward, years before bringing Benthos to its stage in 2026.</p>
          </li>
          <li>
            <span class="when-sm">2019</span>
            <h4>Volunteer Steward</h4>
            <p class="org">Wallride Festival</p>
            <p class="d">Social media, ticket sales, info point, contest registrations and merch sales.</p>
          </li>
          <li>
            <span class="when-sm">2015 – 2016</span>
            <h4>Volunteer, Street Team</h4>
            <p class="org">Steven Wilson</p>
            <p class="d">Sold official merchandise, welcomed fans and processed payments at four shows across Italy and Germany.</p>
          </li>
        </ul>
      </div>

      <div class="edu" aria-labelledby="edu-h">
        <h3 class="sub" id="edu-h">Education</h3>
        <div class="edu-grid">
          <div class="edu-cards">
            <div class="degree">
            <p class="when-sm">2018 – 2021</p>
            <h4>BA (Hons) Commercial Music</h4>
            <p class="org">University of the West of Scotland</p>
            <p class="honours">First Class Honours</p>
            <ul>
              <li>Specialism: Music Business</li>
              <li>Scholarship for academic excellence</li>
            </ul>
          </div>
            <div class="degree alt">
              <p class="when-sm">2024</p>
              <h4>Event Production Programme</h4>
              <p class="org">Legend Club, Milan</p>
              <p class="honours">1 of 15 selected</p>
              <ul>
                <li>Artistic direction, event planning, pre-production, production and hospitality</li>
                <li>Organised two events at the venue</li>
                <li>Worked hospitality and production across the spring/summer 2024 programme</li>
              </ul>
            </div>
          </div>
          <div class="certs">
            <h4 class="sub-sm">Courses &amp; certifications</h4>
            <ul class="cert-list">
              <li><span>Concert Photography Masterclass</span><span class="by">Skillshare</span><span class="y">2024</span></li>
              <li><span>Google Analytics Individual Qualification</span><span class="by">Google</span><span class="y">2021</span></li>
              <li><a class="cert-link" href="https://www.coursera.org/account/accomplishments/verify/NLUSXB6VUZ8G" target="_blank" rel="noopener">Music Business Foundations ↗</a><span class="by">Berklee Online</span><span class="y">2021</span></li>
              <li><span>Marketing</span><span class="by">Woom Italia</span><span class="y">2021</span></li>
              <li><span>Google Ads Display Certification</span><span class="by">Google</span><span class="y">2021</span></li>
              <li><span>Social Media Marketing Specialist</span><span class="by">Sudformazione</span><span class="y">2021</span></li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section class="contact" aria-labelledby="exp-contact-h">
    <div class="wrap">
      <p class="label">Contact</p>
      <h2 id="exp-contact-h" class="contact-h">Want to work together? <em>Get in touch.</em></h2>
      <p class="contact-svc">See what I offer bands and artists. <RouterLink to="/services">See all services →</RouterLink></p>
      <div class="mail">
        <a class="addr" href="mailto:amalia@bands.management">amalia@bands.management</a>
      </div>
    </div>
  </section>
</template>
