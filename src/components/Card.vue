<script setup>
   defineProps({
      title: String,
      imageUrl: String,
      price: Number,
      isFavorite: Boolean,
      isAdded: Boolean,
      onClickAdd: Function,
      onClickFavorite: Function,
   })

</script>

<template>
   <div class="relative m-10 border border-slate-100 rounded-3xl p-8 cursor-pointer hover:-translate-y-2 hover:shadow-xl transition bg-white">

      <img 
         @click="onClickFavorite" 
         :src="isFavorite ? 'like-2.svg' : 'like-1.svg'" alt="like 1" 
         class="absolute top-8 left-8"
      />

      <img :src="imageUrl" alt="Card Image">

      <p class="mt-2">{{ title }}</p>

      <div class="flex justify-between mt-5">
         <div class="flex flex-col">
            <span class="text-slate-400">Цена:</span>
            <b>{{ price }} руб.</b>
         </div>

         <img 
            @click="onClickAdd" 
            :src="!isAdded ? '/plus.svg' : '/checked.svg'" alt="plus" 
         />
      </div>
   </div>
</template>