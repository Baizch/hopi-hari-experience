<script setup lang="ts">
import { ref } from 'vue';

import Subtitle from '../../../components/subtitle/Subtitle.vue';
import Modal from '../../../components/modal/Modal.vue';

import attractions from '../attractions.json';

interface ChildrenAttractions {
  name: string;
  description: string;
  status: string;
  openingHours: string;
  minHeight: string;
  maxHeight: string;
  image: string;
  altImage: string;
  video: string;
}

const list: ChildrenAttractions[] = attractions.attractions.children;

const open = ref<boolean>(false);
const selectedItem = ref<ChildrenAttractions | null>(null);

const showModal = (item: ChildrenAttractions) => {
  open.value = true;
  selectedItem.value = item;
};

const closeModal = () => {
  open.value = false;
  selectedItem.value = null;
};

const subtitle: string = 'Infantis';
</script>

<template>
  <Modal :open="open" :closeModal="closeModal" :selectedItem="selectedItem" />
  <Subtitle :subtitle="subtitle" />

  <!-- TO DO: componetizar -->
  <div class="grid lg:grid-cols-4 md:grid-cols-3 gap-4 mt-14 mb-64">
    <div
      class="rounded overflow-hidden shadow-lg mb-2"
      v-for="(item, index) in list"
      :key="index"
    >
      <img class="w-full" :src="item.image" :alt="item.altImage" />
      <div class="px-6 py-4">
        <div class="font-bold text-xl mb-2">{{ item.name }}</div>
        <p class="text-gray-700 text-base">
          {{ item.description }}
        </p>
        <p class="text-gray-700 text-base mt-2 space-x-1">
          <strong>Status:</strong>
          <span
            class="inline-flex items-center rounded-md bg-green-50 px-2 py-1 text-xs font-medium text-green-700 ring-1 ring-inset ring-green-600/20"
            >{{ item.status }}</span
          >
        </p>
        <p class="text-gray-700 text-base mt-2">
          <strong>Horário de funcionamento:</strong> {{ item.openingHours }}
        </p>
        <div class="flex space-x-20">
          <p class="text-gray-700 text-base mt-2">
            <strong>Altura mínima: </strong> {{ item.minHeight }}
          </p>
          <p class="text-gray-700 text-base mt-2">
            <strong>Altura máxima: </strong> {{ item.maxHeight }}
          </p>
        </div>
        <button
          class="mt-4 font-extrabold bg-white hover:bg-gray-100 text-gray-800 py-2 px-4 border border-gray-400 rounded shadow"
          @click="showModal(item)"
        >
          Ver vídeo
        </button>
      </div>
    </div>
  </div>
</template>
