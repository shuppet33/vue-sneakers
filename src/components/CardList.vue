<script setup>
   import Card from './Card.vue'

   defineProps({
    items: Array,
  })

   const onClickAdd = () => {
   }
</script>

<template>
      <div class="grid grid-cols-4 gap-5">
         <Card
            v-for="item in items"
            :key="item.id"
            :imageUrl="item.imageUrl" 
            :title="item.title" 
            :price="item.price"
            :isAdded="true"
            :isFavorite="false"
            :onClickAdd="onClickAdd"
         />
      </div>
</template>