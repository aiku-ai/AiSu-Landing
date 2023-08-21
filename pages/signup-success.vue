<template>
  <div class="isolate bg-zinc-900 h-screen py-20 px-4">
    <svg class="absolute inset-0 -z-10 h-full w-full stroke-white/10 [mask-image:radial-gradient(100%_100%_at_top_right,white,transparent)]" aria-hidden="true">
      <defs>
        <pattern id="983e3e4c-de6d-4c3f-8d64-b9761d1534cc" width="200" height="200" x="50%" y="-1" patternUnits="userSpaceOnUse">
          <path d="M.5 200V.5H200" fill="none" />
        </pattern>
      </defs>
      <svg x="50%" y="-1" class="overflow-visible fill-gray-800/20">
        <path d="M-200 0h201v201h-201Z M600 0h201v201h-201Z M-400 600h201v201h-201Z M200 800h201v201h-201Z" stroke-width="0" />
      </svg>
      <rect width="100%" height="100%" stroke-width="0" fill="url(#983e3e4c-de6d-4c3f-8d64-b9761d1534cc)" />
    </svg>
    <div class="max-w-2xl mx-auto">
      <div class="max-w-lg">
        <img class="h-11" src="../assets/img/aisu.png" alt="aisu">
        <h2 class="mt-5 text-2xl tracking-tight text-zinc-400">Freeing developers one at a time from the overhead of status updates, scrum, and agile.</h2>
      </div>
      <div class="mt-32">
        <p class="mb-10 text-4xl font-bold tracking-tight text-zinc-100">Thanks for sending us a message! We'll respond soon.</p>
        <NuxtLink to="/" class="text-sm font-semibold leading-6 text-zinc-400 hover:text-zinc-100 transition-hover">Go home <span aria-hidden="true">→</span></NuxtLink>
      </div>
    </div>
  </div>
</template>
