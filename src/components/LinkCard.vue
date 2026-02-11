<template>
  <a 
  href="#" target="_blank" 
  rel="noopener noreferrer"
  class="flex w-full items-center gap-4 rounded-xl border border-gray-700 bg-gr-800 p-4 shadow-md shadow-gray-900/50 hover:scale-[1.02] hover:shadow-xl transition-all duration-300 hover:border-green-600 hover:shadow-green-500/20"
  >
  <!-- Icon Container -->
    <div class="flex h-12 w-12 shrink-0 items-center justify-center rounded-lg bg-gray-700 text-green-400">
      <svg viewBox="0 0 24 24" 
      fill="none" 
      stroke=" currentColor" 
      class="h-6 w-6">

      <path 
      stroke-linecap="round"
      stroke-linejoin="round"
      stroke-width="2"
      d="M6 12v9a1 1 0 0 1-2 0V4c0-1.1.9-2 2-2h6c1.1 0 1.999.9 1.999 2H18a2 2 0 0 1 2 2v6a2 2 0 0 1-2 2h-5a2 2 0 0 1-1.997-2zm0-8v6h7v2h5.002V6H12V4z"/></svg>

    </div>

    <!-- Text Content -->
     <div class="min-w-0 flex-1">
      <h3 class="font-display truncate font-semibold text-white">Link Title</h3>
      <p class="truncate text-sm text-gray-400">
        This is a text area.
      </p>
     </div>
  </a>
  </template>