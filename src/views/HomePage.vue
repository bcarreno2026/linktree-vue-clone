<script setup>
import { ref } from 'vue'
import LinkCard from '@/components/LinkCard.vue'

const profile = ref({
  name: 'Braulio Carreno',
  slogan: 'Intro to Full Stack Developer and Student',
  // Make sure this is ONLY the text inside quotes!
  avatar: 'https://api.dicebear.com/9.x/adventurer-neutral/svg?seed=Braulio'

})

</script>

<template>
  <main class="flex min-h-screen flex-col items-center px-4 py-8">
    <!-- Profile Header -->
     <div class="mb-8 flex flex-col items-center text-center">
      <div 
      class="h-24 w-24 overflow-hidden rounded-full border-4 border-green-400 shadow-lg shadow-green-500/20">
      <img
        :src="profile.avatar"
        :alt="profile.name"
        class="h-full w-full object-cover"
      />
      </div>
      <h1 class="font-display mb-2 text-2x1 font-bold text-white sm:text-3xl">{{ profile.name }}</h1>
      <p class="max-w-xs text-gray-400 mt-2 sm:text-lg">{{ profile.slogan }}</p>
     </div>

     <!-- Link List-->
      <div class="flex w-full max-w-md flex-col gap-4">

        <LinkCard v-for="x of [1,2,3]" :key="x"/>
      </div>

      <!-- Navigate to Info -->
       <RouterLink to="/Info" 
       class="mt-8 text-sm text-gray-400 underline-offset-4 transition-colors duration-200 hover:text-green-400 hover:underline"
       > 
       About me ➡️
      </RouterLink>
  </main>
</template>
