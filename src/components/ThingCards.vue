<script setup lang="ts">
import VCard from "@/components/UI/VCard.vue";
import {ref} from "vue";
import type {IThing} from "@/types/Thing";

export interface Props {
  things?: IThing[]
  max?: number
}

const props = withDefaults(defineProps<Props>(), {
  things: () => [],
  max: 1
})

const selectedItems = ref<IThing[]>([]);

const addItem = (el: IThing) => {
  if(selectedItems.value?.length === props.max) return

  selectedItems.value.push(el)
}
</script>

<template>
<div class="thing-cards">
  <v-card
      v-if="selectedItems.length"
      class="thing-cards__selected-items"
  >
    <template v-if="max === 1">
      {{ selectedItems[0]?.name }}
    </template>

    <template v-else>
      <v-card
          v-for="(item, index) in selectedItems"
          class="thing-cards__item"
          :key="index"
      >
        {{ item.name }}
      </v-card>
    </template>
  </v-card>

  <v-card class="thing-cards__items">
    <v-card
        class="thing-cards__item"
        v-for="(item, index) in things"
        @click="addItem(item)"
        :key="index"
    >
      {{ item.name }}
    </v-card>
  </v-card>
</div>
</template>

<style scoped>
.thing-cards__selected-items {
  margin-bottom: 40px;
}

.thing-cards__item {
  cursor: pointer;
}

.thing-cards__item:hover {
  color: red;
}
</style>
