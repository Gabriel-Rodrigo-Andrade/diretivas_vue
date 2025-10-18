<template>
   <div class="container-item-list">
      <ul v-if="items.length">
         <li v-for="(item, index) in items" :key="index"> <span class="item-text" @click="handleClick(item)">{{  item }}</span></li>
      </ul>
      <p v-else>Nenhum item na lista</p>
   </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
   items: {
      type: Array,
      default: () => []
   }
})

const emit = defineEmits(['select'])
function handleClick(item) {
   emit('select', item)
}
</script>

<style scoped>
.container-item-list {
   ul {
      list-style: disc inside;
      padding: 0.5em 0;
      max-width: 100%;
   }
   li {
      padding: 0.25em 0;
   }
   p {
      font-family: 'Poppins', sans-serif;
   }
}
</style>
