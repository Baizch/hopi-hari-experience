<script setup lang="ts">
const props = defineProps({
  subtitle: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <h2 class="font-semibold mt-4 float-left text-lg">{{ props.subtitle }}</h2>
</template>
