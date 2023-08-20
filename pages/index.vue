<template>
  <div class="relative isolate overflow-hidden bg-zinc-900">
    <svg class="absolute inset-0 -z-10 h-full w-full stroke-white/10 [mask-image:radial-gradient(100%_100%_at_top_right,white,transparent)]" aria-hidden="true">
      <defs>
        <pattern id="983e3e4c-de6d-4c3f-8d64-b9761d1534cc" width="200" height="200" x="50%" y="-1" patternUnits="userSpaceOnUse">
          <path d="M.5 200V.5H200" fill="none" />
        </pattern>
      </defs>
      <svg x="50%" y="-1" class="overflow-visible fill-zinc-800/20">
        <path d="M-200 0h201v201h-201Z M600 0h201v201h-201Z M-400 600h201v201h-201Z M200 800h201v201h-201Z" stroke-width="0" />
      </svg>
      <rect width="100%" height="100%" stroke-width="0" fill="url(#983e3e4c-de6d-4c3f-8d64-b9761d1534cc)" />
    </svg>
    <div class="absolute left-[calc(50%-4rem)] top-10 -z-10 transform-gpu blur-3xl sm:left-[calc(50%-18rem)] lg:left-48 lg:top-[calc(50%-30rem)] xl:left-[calc(50%-24rem)]" aria-hidden="true">
      <div class="aspect-[1108/632] w-[69.25rem] bg-gradient-to-r from-[#80caff] to-[#4f46e5] opacity-20" style="clip-path: polygon(73.6% 51.7%, 91.7% 11.8%, 100% 46.4%, 97.4% 82.2%, 92.5% 84.9%, 75.7% 64%, 55.3% 47.5%, 46.5% 49.4%, 45% 62.9%, 50.3% 87.2%, 21.3% 64.1%, 0.1% 100%, 5.4% 51.1%, 21.4% 63.9%, 58.9% 0.2%, 73.6% 51.7%)"></div>
    </div>
    <div class="mx-auto max-w-7xl px-6 pb-24 pt-10 sm:pb-32 lg:flex lg:px-8 lg:py-40">
      <div class="mx-auto max-w-2xl flex-shrink-0 lg:mx-0 lg:max-w-xl lg:pt-8">
        <img class="h-11" src="../assets/img/aisu.png" alt="aisu">
        <h1 class="mt-14 text-4xl font-bold tracking-tight text-zinc-100 sm:text-6xl">Freeing engineers from the overhead of Agile</h1>
        <p class="mt-6 text-lg leading-8 text-zinc-400">Our goal is to eliminate the overhead of agile. We are automating scrum, status updates, and sprint planning. Your engineers should spend time coding, not being micromanaged.</p>
        <div class="mt-10 flex items-center gap-x-6">
          <NuxtLink to="/signup" class="rounded-md bg-sky-600 px-7 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-sky-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-sky-400 transition-hover">Get started</NuxtLink>
        </div>
      </div>
      <div class="mx-auto mt-16 flex max-w-2xl sm:mt-24 lg:ml-10 lg:mr-0 lg:mt-0 lg:max-w-none lg:flex-none xl:ml-32">
        <div class="max-w-3xl flex-none sm:max-w-5xl lg:max-w-none">
          <img src="../assets/img/app_screenshot.png" alt="App screenshot" width="2432" height="1442" class="w-[76rem] rounded-md bg-white/5 shadow-2xl ring-1 ring-white/10">
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
useHead({
  title: 'AiSu - Freeing engineers from Agile',
  meta: [
    // PRIMARY TAGS
    { hid: 'description', name: 'description', content: "Our goal is to eliminate the overhead of agile. We are automating scrum, status updates, and sprint planning. Your engineers should spend time coding, not being micromanaged." },
    { hid: 'title', name: 'title', content: 'AiSu - Freeing engineers from Agile' },

    // OPEN GRAPH/FACEBOOK
    { hid: 'og:type', property: 'og:type', content: 'website' },
    // { hid: 'og:url', property: 'og:url', content: config.public.appBase },
    { hid: 'og:title', property: 'og:title', content: 'AiSu - Freeing engineers from Agile' },
    { hid: 'og:image', property: 'og:image', content: '/meta_card.png' },

    // TWITTER
    { name: 'twitter:card', content: 'summary_large_image' },
    { name: 'twitter:title', content: 'AiSu - Freeing engineers from Agile' },
    { name: 'twitter:description', content: "Our goal is to eliminate the overhead of agile. We are automating scrum, status updates, and sprint planning. Your engineers should spend time coding, not being micromanaged." },
    { name: 'twitter:image', content: '/meta_card.png' }
  ]
}) 

</script>
