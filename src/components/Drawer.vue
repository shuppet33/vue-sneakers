<script setup>
   import DrawerHead from './DrawerHead.vue';
   import CartItemList from './CartItemList.vue';
   import CartItem from './CartItem.vue';
</script>

<template>
   <div>
      <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70 "></div>
      <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8 ">

         <DrawerHead  />

         <div class="flex flex-col justify-between">
            <CartItemList >
               <CartItem  />
               <CartItem  />
               <CartItem  />
            </CartItemList>


            <div class="flex flex-col gap-4 mt-7">
               <div class="flex gap-2 " >
                  <span> Итого: </span>
                  <div class="flex-1 border-b border-dashed border-slate-400 "></div>
                  <b>12999 руб.</b>
               </div>

               <div class="flex gap-2 " >
                  <span> Налог: 5%</span>
                  <div class="flex-1 border-b border-dashed border-slate-400 "></div>
                  <b>900 руб.</b>
               </div>

               <button disabled class="mt-4 bg-lime-500 w-full rounded-xl py-3 text-white hover:bg-lime-600 transition active:bg-lime-700 disabled:bg-slate-300 cursor-pointer">
               Оформить заказ
            </button>
            </div>

         </div>
      </div>
   </div>
</template>