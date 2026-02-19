<script setup>
import { ref } from 'vue'
import LinkCard from '@/components/LinkCard.vue'

const profile = ref({
  name: 'Braulio Carreno',
  slogan: 'Intro to Full Stack Developer and Student',
  avatar: 
  'https://api.dicebear.com/9.x/adventurer-neutral/svg?seed=Braulio',
  links: [
    {
      id:1,
      title: 'GitHub',
      url: 'https://github.com/bcarreno2026',
      icon: 'code',
      description: 'Check out my projects',
    },

    {
      id:2,
      title: 'Linkedin',
      url: 'https://www.linkedin.com/in/braulio-carreno-176128220/',
      icon: 'briefcase',
      description: 'Connect with me professionally',
    },
    {
      id: 3,
      title: 'Expense Divider (Future Projects)',
      url: '',
      icon: 'folder', 
      isFuture: true,
      futureLinks: [
        { name: 'expense-splitter-vue', url: 'https://expense-splitter-vue.expense-splitter-vue-123.workers.dev' },
        { name: 'expenses-html', url: 'https://expenses-html-51k.pages.dev' },
      ],
    }
  ]

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

        <LinkCard 
        v-for="link in profile.links" 
        :key="link.id"
        :title="link.title"
        :url="link.url"
        :description="link.description"
        :icon="link.icon"
        :isFuture="link.isFuture"
        :futureLinks="link.futureLinks"
        />
      </div>

      <!-- Navigate to Info -->
       <RouterLink to="/Info" 
       class="mt-8 text-sm text-gray-400 underline-offset-4 transition-colors duration-200 hover:text-green-400 hover:underline"
       > 
       About me ➡️
      </RouterLink>
  </main>
</template>
