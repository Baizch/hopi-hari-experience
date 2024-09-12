<script setup lang="ts">
import Title from '../../components/title/Title.vue';
import Children from './children/Children.vue';
import Family from './family/Family.vue';
import Radical from './radical/Radical.vue';
import Warning from '../../components/warning/Warning.vue';
</script>

<template>
  <section>
    <div class="mt-12 max-w-full mx-auto px-6 text-center mb-64">
      <Title />
      <Children />
      <Family />
      <Radical />
      <Warning />
    </div>
  </section>
</template>
