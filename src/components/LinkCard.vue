<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
  url: {
    type: String,
    required: false, 
    default: '',
  },
  description: {
    type: String,
    default: '',
  },
  icon: {
    type: String,
    default: 'flag',
  },
  isFuture: { 
    type: Boolean, 
    default: false
  },
  futureLinks: { 
    type: Array, 
    default: () => [] 
  },
})

const icons = {
  flag: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 12v9a1 1 0 0 1-2 0V4c0-1.1.9-2 2-2h6c1.1 0 1.999.9 1.999 2H18a2 2 0 0 1 2 2v6a2 2 0 0 1-2 2h-5a2 2 0 0 1-1.997-2zm0-8v6h7v2h5.002V6H12V4z"/>`,
  code: '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.25 6.75 22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3-4.5 16.5"></path>',
  briefcase: '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.25 14.15v4.25c0 1.094-.787 2.036-1.872 2.18-2.087.277-4.216.42-6.378.42s-4.291-.143-6.378-.42c-1.085-.144-1.872-1.086-1.872-2.18v-4.25m16.5 0a2.18 2.18 0 0 0 .75-1.661V8.706c0-1.081-.768-2.015-1.837-2.175a48.114 48.114 0 0 0-3.413-.387m4.5 8.006c-.194.165-.42.295-.673.38A23.978 23.978 0 0 1 12 15.75c-2.648 0-5.195-.429-7.577-1.22a2.016 2.016 0 0 1-.673-.38m0 0A2.18 2.18 0 0 1 3 12.489V8.706c0-1.081.768-2.015 1.837-2.175a48.111 48.111 0 0 1 3.413-.387m7.5 0V5.25A2.25 2.25 0 0 0 13.5 3h-3a2.25 2.25 0 0 0-2.25 2.25v.894m7.5 0a48.667 48.667 0 0 0-7.5 0M12 12.75h.008v.008H12v-.008Z"></path>',
  folder: '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.25 12.75V12A2.25 2.25 0 0 1 4.5 9.75h15A2.25 2.25 0 0 1 21.75 12v.75m-8.69-6.44-2.12-2.12a1.5 1.5 0 0 0-1.061-.44H4.5A2.25 2.25 0 0 0 2.25 6v12a2.25 2.25 0 0 0 2.25 2.25h15A2.25 2.25 0 0 0 21.75 18V9a2.25 2.25 0 0 0-2.25-2.25h-5.379a1.5 1.5 0 0 1-1.06-.44Z"></path>'
}
</script>


<template>
  <component
    :is="isFuture ? 'div' : 'a'"
    :href="!isFuture ? url : undefined"
    target="_blank"
    rel="noopener noreferrer"
    class="relative group flex w-full flex-col items-start gap-4 rounded-xl border border-gray-700 bg-gray-800 p-4 shadow-md shadow-gray-900/50 hover:scale-[1.02] hover:shadow-xl transition-all duration-300 hover:border-green-600 hover:shadow-green-500/20"
  >
    <div class="flex h-12 w-12 shrink-0 items-center justify-center rounded-lg bg-gray-700 text-green-400 transition-all duration-300 group-hover:scale-110 group-hover:bg-green-500 group-hover:text-white group-hover:shadow-xl group-hover:shadow-green-500/20">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" class="h-6 w-6" v-html="icons[icon] || icons.flag"></svg>
    </div>

    <div class="min-w-0 flex-1">
      <h3 class="truncate font-display font-semibold text-white">{{ title }}</h3>
      
      <!-- Logic to show nested links if isFuture is true -->
      <div v-if="isFuture && futureLinks?.length" class="text-sm text-gray-400 mt-2 space-y-2">
        <a 
          v-for="link in futureLinks" 
          :key="link.url" 
          :href="link.url" 
          target="_blank" 
          class="block underline decoration-green-500/30 hover:text-green-400 hover:decoration-green-400 transition-colors"
        >
          {{ link.name }}
        </a>
      </div>
      <p v-else class="text-sm text-gray-400 truncate">{{ description }}</p>
    </div>
  </component>
</template>
