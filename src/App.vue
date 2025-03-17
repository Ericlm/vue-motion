<script setup lang="ts">
import { ref } from 'vue'
import { ReorderGroup, ReorderItem } from 'motion-v'

interface Item {
  value: string
}

const initialItems: Item[] = [{value: '🍅 Tomato'}, {value: '🥒 Cucumber'}, {value: '🧀 Cheese'}, {value: '🥬 Lettuce'}]
const items = ref(initialItems)

function setItems(newItems: Item[]) {
  items.value = newItems
}
</script>

<template>
  <ReorderGroup
    :values="items"
    axis="y"
    class="relative w-[300px]"
    @update:values="setItems"
  >
    <ReorderItem
      v-for="item in items"
      :key="item.value"
      :value="item"
      drag
      class="rounded-lg select-none list-none mb-2 cursor-grab w-full py-4 px-6 bg-purple-500 justify-between flex flex-shrink-0"
    >
      {{ item }}
    </ReorderItem>
  </ReorderGroup>
</template>

<style scoped>
</style>

