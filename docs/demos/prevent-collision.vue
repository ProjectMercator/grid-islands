<script setup lang="ts">
import { reactive } from 'vue'

const layout = reactive([
  { x: 0, y: 0, w: 2, h: 2, i: '0', static: false },
  { x: 2, y: 0, w: 2, h: 4, i: '1', static: false },
  { x: 4, y: 0, w: 2, h: 5, i: '2', static: false },
  { x: 6, y: 0, w: 2, h: 3, i: '3', static: false }
])
</script>

<template>
  <GridLayout
    v-model:layout="layout"
    :row-height="30"
    :responsive="false"
    :vertical-compact="false"
    :prevent-collision="true"
    :resize-from-edges="true"
    :use-style-cursor="true"
  >
    <GridItem
      v-for="item in layout"
      :key="item.i"
      :x="item.x"
      :y="item.y"
      :w="item.w"
      :h="item.h"
      :i="item.i"
      :resize-from-edges="true"
      :resize-option="{
        edges: {
          top: true,
          right: true,
          bottom: true,
          left: true
        }
      }"
    >
      <span class="text">{{ item.i }}</span>
    </GridItem>
  </GridLayout>
</template>

<style scoped>
.vgl-layout {
  background-color: #eee;
}

:deep(.vgl-item:not(.vgl-item--placeholder)) {
  background-color: #ccc;
  border: 1px solid black;
}

:deep(.vgl-item--resizing) {
  opacity: 90%;
}

:deep(.vgl-item--static) {
  background-color: #cce;
}

.text {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  margin: auto;
  font-size: 24px;
  text-align: center;
}
</style>
