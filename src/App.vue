<script setup lang="ts">
import { useThingsStore } from "@/stores/things";
import ThingCards from "@/components/ThingCards.vue";
import type {IThing} from "@/types/Thing";

const leftThings: IThing[] = useThingsStore().leftThings
const rightThings: IThing[] = useThingsStore().rightThings
</script>

<template>
<div class="wrapper">
  <thing-cards :things="leftThings" :max="6" />

  <thing-cards :things="rightThings" :max="1" />
</div>
</template>

<style scoped>
.wrapper {
  display: flex;
  justify-content: space-between;
  gap: 20px;
}
</style>
