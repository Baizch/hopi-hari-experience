<script setup lang="ts">
import headerData from './header.json';

const text: string = headerData.text;
</script>

<template>
  <div>
    <nav
      class="sticky top-0 py-6 bg-neutral-600 text-white font-bold flex items-center justify-center text-3xl"
    >
      <p>{{ text }}</p>
    </nav>
  </div>
</template>
