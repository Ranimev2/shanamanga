<script setup>
const { data: anime } = await useFetch("https://ranimev2-api.vercel.app/wibudesu/latest?page=1");
</script>
<template>
   <div>
      <h2 class="font-semibold mt-6">anime latest</h2>
      <div class="flex flex-col gap-4 mt-4">
         <NuxtLink :to="anime.endpoint" class="flex gap-4 p-4 shadow-card hover:shadow-xl hover:shadow-black/10 transition duration-300 rounded-xl bg-white items-center" v-for="anime in anime.data" :key="anime.id">
            <img class="w-20 h-20 object-cover rounded-md" :src="anime.image" :alt="'thumbnail' + anime.title" />

            <div>
               <h5 class="font-semibold line-clamp-1">{{ anime.title }}</h5>
               <h6 class="text-sm text-gray-500">{{ anime.type }}</h6>
               <p class="text-[10px] bg-blue-100 text-blue-500 px-2 py-1 inline-flex rounded-full mt-2">{{ anime.desc.slice(0, 18) }}</p>
            </div>
         </NuxtLink>
      </div>
   </div>
</template>
