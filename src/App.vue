<template>
   <div id="app" :style="{ backgroundColor: bgColor }">
      <header class="container-header">
         <img alt="Gra logo" class="logo" src="./assets/img/logo-gra-branca.png" />
      </header>

      <main class="main-container">
         <div class="wrapper">
            <div class="content-select-color">
               <ColorPicker v-model="bgColor" />
            </div>

            <button class="btn-show-list" @click="toggleList">{{  showList ? 'Esconder lista' : 'Mostrar lista' }}</button>
            
            <div class="content-list">
               <ItemList v-if="showList" :items="items" @select="handleSelect" />
            </div>         
         </div>
         <button class="btn-iten-select" v-if="selected"> Item selecionado: <span class="select-option">{{ selected }}</span></button>
      </main>
   </div>
</template>

<script setup>
import { ref } from 'vue'
import ItemList from './components/ItemList.vue';
import ColorPicker from './components/ColorPicker.vue';

const items = ref(['Comprar bomba', 'Aplicar tudo a bomba', 'Repetir o ciclo'])
const showList = ref(true)
const bgColor = ref('#ffffff')
const selected = ref(null)

function toggleList() {
   showList.value = !showList.value
}

function handleSelect(item) {
   selected.value = item
   console.log('Item selecionado:', item)
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');

.main-container {
   display: block;
   
}

.container-header {
   display: flex;
   justify-content: center;
   .logo {
      width: 35%;
   }
}

.main-container {
   .btn-iten-select {
      font-family: 'Poppins', sans-serif;
      font-size: 16px;
      font-weight: 600;
      color: #ffffff;
      background-color: #442397;
      border: none;
      border-radius: 15px;
      padding: 6px 24px;
      cursor: pointer;
      transition: all 0.3s ease;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
      background: linear-gradient(135deg, #47073f, #3e3aa8, #1e1b4b);
   }

      button:hover {
         background-color: #ba83c2;
         transform: translateY(-2px);
         box-shadow: 0 6px 14px rgba(106, 25, 118, 0.25);
      }

   .content-list {
      font-size: 18px;
      font-family: 'Poppins', sans-serif;
   }
   .select-option {
      font-style: italic;
   }
   .wrapper {
      button {
         font-family: 'Poppins', sans-serif;
         font-size: 16px;
         font-weight: 600;
         color: #ffffff;
         background-color: #442397;
         border: none;
         border-radius: 15px;
         padding: 6px 24px;
         cursor: pointer;
         transition: all 0.3s ease;
         box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
         background: linear-gradient(135deg, #47073f, #3e3aa8, #1e1b4b);
      }

      button:hover {
         background-color: #ba83c2;
         transform: translateY(-2px);
         box-shadow: 0 6px 14px rgba(106, 25, 118, 0.25);
      }

      .btn-show-list {
         margin-top: 2rem;
         margin-bottom: 0.5rem;
      }
   }
}
</style>