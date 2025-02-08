<script setup>
  import { onMounted, ref, toRaw, watch, reactive } from 'vue';
  import axios from 'axios';
  import Header from './components/Header.vue'
  import CardList from './components/CardList.vue'
  import Drawer from './components/Drawer.vue'

  const items = ref([]); // {value: []}

  const filters = reactive({
    sortBy: '',
    searchQuery: '',
  })

  const fetchItems = () => {
    fetch(`https://7e71aaffa8818ec6.mokky.dev/items?title=*${filters.searchQuery}*&sortBy=${filters.sortBy}`)
      .then(resp => resp.json())
      .then(data => {
        items.value = data;
      })
      .catch(error => console.error('Ошибка при получении данных:', error));
  }

  const onChangeSelect = (event) => {
    filters.sortBy = event.target.value
  }

  const onChangeSearchInput = (event) => {
    filters.searchQuery = event.target.value
  }

  onMounted(fetchItems);
  watch(filters, fetchItems)

</script>

<template>
  <div class="bg-white w-4/5  m-auto rounded-xl shadow-xl mt-14 ">

    <!-- <Drawer  /> -->
    <Header />
    
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>

        <div class="flex items-center gap-4">
          <select @change="onChangeSelect" class="py-2 px-3 border rounded-md  outline-none focus:border-gray-400 border-gray-200">
            <option value="name">По названию</option>
            <option value="price">По цене (дешевле)</option>
            <option value="-price">По цене (дороже)</option>
          </select>

          <div class="relative">
            <img class="absolute left-4 top-2.5" src="/search.svg" alt="search">
            <input @change="onChangeSearchInput" class="border border border-gray-200 rounded-md py-1.5 pl-11 pr-4 outline-none focus:border-gray-400"
            type=""
            placeholder="Поиск">
          </div>
        </div>
      </div>
    
      <CardList  :items="items"/>

    </div>
  </div>
</template>