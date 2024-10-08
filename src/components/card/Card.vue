<script setup lang="ts">
import { InfoCircleOutlined } from '@ant-design/icons-vue';

const props = defineProps({
  list: {
    type: Array,
    required: true,
  },
  showModal: {
    type: Function,
    required: true,
  },
});
</script>

<template>
  <div class="grid lg:grid-cols-4 md:grid-cols-3 gap-4 mt-14">
    <div
      class="rounded overflow-hidden shadow-lg mb-4"
      v-for="(item, index) in props.list"
      :key="index"
    >
      <img class="w-full" :src="item.image" :alt="item.altImage" />
      <div class="px-6 py-4">
        <a-space>
          <div class="font-bold text-xl mb-2">{{ item.name }}</div>
          <a-tooltip v-if="item.observation !== ''">
            <template #title>{{ item.observation }}</template>
            <InfoCircleOutlined class="mb-2" />
          </a-tooltip>
        </a-space>
        <p class="text-gray-700 text-base mt-2 space-x-2">
          <strong>Status:</strong>
          <span
            v-if="item.status === 'Aberto'"
            class="inline-flex items-center rounded-md bg-green-50 px-2 py-1 text-xs font-medium text-green-700 ring-1 ring-inset ring-green-600/20"
            >{{ item.status }}</span
          >
          <span
            v-else-if="item.status === 'Manutenção'"
            class="inline-flex items-center rounded-md bg-yellow-50 px-2 py-1 text-xs font-medium text-yellow-800 ring-1 ring-inset ring-yellow-600/20"
            >{{ item.status }}</span
          >
          <span
            v-else="item.status === 'Fechado'"
            class="inline-flex items-center rounded-md bg-red-50 px-2 py-1 text-xs font-medium text-red-700 ring-1 ring-inset ring-red-600/10"
            >{{ item.status }}</span
          >
        </p>
        <div v-if="item.openingHours !== ''" class="block space-x-2">
          <p class="text-gray-700 text-base mt-2">
            <strong>Horário de funcionamento:</strong>
          </p>
          <p class="mt-2">{{ item.openingHours }}</p>
        </div>
        <div
          v-if="item.minHeight && item.maxHeight !== ''"
          class="flex xs:space-x-36 sm:space-x-64 md:space-x-12 lg:space-x-12"
        >
          <p class="text-gray-700 text-base mt-2">
            <strong>Altura mínima: </strong> {{ item.minHeight }}
          </p>
          <p class="text-gray-700 text-base mt-2">
            <strong>Altura máxima: </strong> {{ item.maxHeight }}
          </p>
        </div>
        <button
          :disabled="item.video === ''"
          class="w-full mt-4 font-extrabold bg-white hover:bg-gray-100 text-gray-800 py-2 px-4 border border-gray-400 rounded shadow disabled:bg-gray-200"
          @click="props.showModal(item)"
        >
          Ver vídeo
        </button>
      </div>
    </div>
  </div>
</template>
