<script setup lang="ts">
import { onBeforeUnmount, onMounted, ref, watch } from 'vue';
import { RouterLink, useRoute } from 'vue-router';

const links = [
  { label: 'Artists', to: { path: '/', hash: '#roster' } },
  { label: 'Work', to: { path: '/', hash: '#work' } },
  { label: 'Experience', to: '/experience', match: '/experience' },
  { label: 'Services', to: '/services', match: '/services' },
  { label: 'Photography', to: '/photos', match: '/photos' },
  { label: 'Contact', to: { path: '/', hash: '#contact' } }
];

const open = ref(false);
const route = useRoute();
const close = () => (open.value = false);

watch(() => route.fullPath, close);
watch(open, (v) => document.documentElement.classList.toggle('menu-open', v));

const onKey = (e: KeyboardEvent) => {
  if (e.key === 'Escape') close();
};
onMounted(() => window.addEventListener('keydown', onKey));
onBeforeUnmount(() => {
  window.removeEventListener('keydown', onKey);
  document.documentElement.classList.remove('menu-open');
});
</script>

<template>
  <nav class="top" :class="{ open }" aria-label="Main">
    <div class="wrap">
      <RouterLink class="mark" to="/" @click="close">Amalia Cicala<span>.</span></RouterLink>
      <button
        type="button"
        class="menu-btn"
        :aria-expanded="open"
        aria-controls="site-menu"
        :aria-label="open ? 'Close menu' : 'Open menu'"
        @click="open = !open"
      >
        <span class="bars" aria-hidden="true"><span></span><span></span></span>
      </button>
      <ul id="site-menu">
        <li v-for="(l, i) in links" :key="l.label" :style="{ '--n': i }">
          <RouterLink :to="l.to" :class="{ current: l.match && route.path.startsWith(l.match) }" @click="close">{{ l.label }}</RouterLink>
        </li>
      </ul>
    </div>
  </nav>
</template>
