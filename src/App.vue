<script setup>
  import { onMounted } from 'vue';
  import Header from './components/Header.vue'
  import CardList from './components/CardList.vue'
  import Drawer from './components/Drawer.vue'

  onMounted(() => {
    console.log(123)
  })
</script>

<template>
  <div class="bg-white w-4/5  m-auto rounded-xl shadow-xl mt-14 ">

    <!-- <Drawer  /> -->
    <Header />
    
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>

        <div class="flex items-center gap-4">
          <select class="py-2 px-3 border rounded-md  outline-none focus:border-gray-400 border-gray-200">
            <option>По названию</option>
            <option>По цене (дешевле)</option>
            <option>По цене (дороже)</option>
          </select>

          <div class="relative">
            <img class="absolute left-4 top-2.5" src="/search.svg" alt="search">
            <input class="border border border-gray-200 rounded-md py-1.5 pl-11 pr-4 outline-none focus:border-gray-400"
            type=""
            placeholder="Поиск">
          </div>
        </div>
      </div>
    
      <CardList  :items="items"/>

    </div>
  </div>
</template>