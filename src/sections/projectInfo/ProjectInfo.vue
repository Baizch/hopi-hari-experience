<script setup lang="ts">
import projectInfo from './projectInfo.json';

import Divider from '../../components/divider/Divider.vue';
</script>

<template>
  <section>
    <div class="mt-12 max-w-full mx-auto px-6 text-center">
      <h2 class="font-bold text-3xl uppercase">{{ projectInfo.title }}</h2>

      <p class="text-center mt-4 text-lg leading-relaxed mb-6">
        <strong>{{ projectInfo.welcomeText }}</strong>
      </p>

      <p class="text-lg leading-relaxed mb-6">
        {{ projectInfo.firstParagraph }}
      </p>

      <p class="text-lg leading-relaxed mb-6">
        {{ projectInfo.secondParagraph }}
      </p>

      <p class="text-lg leading-relaxed mb-6">
        <strong>{{ projectInfo.observationText }}</strong>
        {{ projectInfo.thirdParagraph }}
      </p>

      <Divider />
    </div>
  </section>
</template>
