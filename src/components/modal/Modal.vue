<script setup lang="ts">
import { PropType } from 'vue';
import { IAttractions } from '../../types';

const props = defineProps({
  open: {
    type: Boolean,
    required: true,
  },
  closeModal: {
    type: Function,
    required: true,
  },
  selectedItem: {
    type: Object as PropType<IAttractions>,
    required: true,
  },
});
</script>

<template>
  <a-modal
    v-if="props.selectedItem"
    v-model:open="props.open"
    :title="props.selectedItem.name"
    :closable="false"
    :destroyOnClose="true"
  >
    <div class="space-y-4">
      <a-typography-paragraph>
        {{ props.selectedItem.description }}
      </a-typography-paragraph>
      <iframe
        width="470"
        height="315"
        :src="`https://www.youtube.com/embed/${props.selectedItem.video}`"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope;"
        referrerpolicy="strict-origin-when-cross-origin"
      ></iframe>
    </div>
    <template #footer>
      <button
        @click="props.closeModal"
        class="mt-4 font-extrabold bg-white hover:bg-gray-100 text-gray-800 py-2 px-4 border border-gray-400 rounded shadow"
      >
        Fechar
      </button>
    </template>
  </a-modal>
</template>
