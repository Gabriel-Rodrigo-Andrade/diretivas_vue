<template>
   <div class="container-color-picker">
      <label>
         Escolha a cor de fundo:   
         <input class="inp-select-color" type="color" :value="modelValue" @input="onInput" />
      </label>
      <span class="hex-select">{{ modelValue }}</span>
   </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
   modelValue: {
      type: String,
      default: '#ffffff'
   }
})

const emit = defineEmits(['update:modelValue']) //pq essa merda é dentro de uma array???

function onInput(e) {
   emit('update:modelValue', e.target.value)
}
</script>

<style scoped>
.container-color-picker {
   display: flex;
   align-items: center;
   gap: 1rem;
   font-family: 'Poppins', sans-serif;

      label {
         display: flex;
         align-items: center;
         gap: 0.5rem;
         font-weight: 500;

         .inp-select-color {
            margin-left: 12px;
            appearance: none;
            -webkit-appearance: none;
            border: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
            overflow: hidden;
            box-shadow: 0 0 0 2px #ccc, 0 2px 6px rgba(0,0,0,0.1);
            transition: all 0.2s ease-in-out;
         }

         .inp-select-color:hover {
            transform: scale(1.05);
            box-shadow: 0 0 0 2px #888, 0 3px 8px rgba(0,0,0,0.15);
         }

         /* esse krl remove o quadrado padrão do seletor no Chrome, peguei do GPT msm */
         .inp-select-color::-webkit-color-swatch-wrapper {
            padding: 0;
         }
         .inp-select-color::-webkit-color-swatch {
            border-radius: 50%;
         }
      }

      .hex-select {
         font-size: 12px;
         background: #f8f8f8;
         padding: 0.2rem 0.4rem;
         border-radius: 8px;
         min-width: 60px;
         text-align: center;
      }
}
</style>
