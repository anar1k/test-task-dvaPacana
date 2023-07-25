<script setup lang="ts">
export interface Props {
  radius?: boolean
}

withDefaults(defineProps<Props>(), {
  radius: false,
})
</script>

<template>
<div class="card" :class="{'radius' : radius}">
  <slot/>
</div>
</template>

<style scoped>
.card {
  display: inline-block;
  padding: 16px;
  border: 2px solid #000;
}

.radius {
  border-radius: 20px;
}
</style>
