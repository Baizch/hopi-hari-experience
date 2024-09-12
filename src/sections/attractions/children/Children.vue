<script setup lang="ts">
import { ref } from 'vue';
import { ChildrenAttractions } from '../../../types';

import Subtitle from '../../../components/subtitle/Subtitle.vue';
import Modal from '../../../components/modal/Modal.vue';
import Card from '../../../components/card/Card.vue';

import attractions from '../attractions.json';

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
  <Card :list="list" :showModal="showModal" />
</template>
