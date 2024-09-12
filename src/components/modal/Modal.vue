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
    <video class="h-full w-full rounded-lg mt-4" controls>
      <source :src="props.selectedItem.video" type="video/mp4" />
    </video>
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
