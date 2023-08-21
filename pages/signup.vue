<template>
  <div id="join-team" class="isolate bg-zinc-900 px-4 py-16 sm:py-24 sm:h-screen">
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
    <div class="mx-auto max-w-xl">
      <img class="h-11" src="../assets/img/aisu.png" alt="aisu">
      <h2 class="mt-10 text-3xl font-bold tracking-tight text-zinc-200">Signup for our private beta</h2>
      <p class="mt-2 text-lg leading-8 text-zinc-400">We're now accepting requests to signup for our private beta. Please fill out the below form and we'll reach out to you to get things started.</p>
    </div>
    <form 
      netlify
      name="contact-form"
      action="/signup-success"
      method="POST"
      data-netlify="true"
      class="mx-auto mt-16 max-w-xl sm:mt-12"
    >
      <input type="hidden" name="form-name" value="contact-form" />
      <div class="grid grid-cols-1 gap-x-8 gap-y-6 sm:grid-cols-2">
        <div>
          <label for="first-name" class="block text-sm font-semibold leading-6 text-zinc-200">First name <span class="text-red-500">*</span></label>
          <div class="mt-2.5">
            <input v-model="form.firstName.value" type="text" name="first-name" id="first-name" autocomplete="given-name" class="bg-zinc-900 block w-full rounded-md border-0 px-3.5 py-2 text-zinc-100 ring-1 ring-inset ring-zinc-400 placeholder:text-zinc-500 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6 transition-hover focus:outline-none" placeholder="Jane">
          </div>
        </div>
        <div>
          <label for="last-name" class="block text-sm font-semibold leading-6 text-zinc-200">Last name <span class="text-red-500">*</span></label>
          <div class="mt-2.5">
            <input v-model="form.lastName.value" type="text" name="last-name" id="last-name" autocomplete="family-name" class="bg-zinc-900 block w-full rounded-md border-0 px-3.5 py-2 text-zinc-100 shadow-sm ring-1 ring-inset ring-zinc-400 placeholder:text-zinc-500 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6 transition-hover focus:outline-none" placeholder="Doe">
          </div>
        </div>
        <div class="sm:col-span-1">
          <label for="email" class="block text-sm font-semibold leading-6 text-zinc-200">Email <span class="text-red-500">*</span></label>
          <div class="mt-2.5">
            <input v-model="form.email.value" type="email" name="email" id="email" autocomplete="email" class="bg-zinc-900 block w-full rounded-md border-0 px-3.5 py-2 text-zinc-100 shadow-sm ring-1 ring-inset ring-zinc-400 placeholder:text-zinc-500 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6 transition-hover focus:outline-none" placeholder="janedoe@email.com">
          </div>
        </div>
        <div class="sm:col-span-1">
          <label for="org" class="block text-sm font-semibold leading-6 text-zinc-200">Organization</label>
          <div class="mt-2.5">
            <input v-model="form.org.value" type="text" name="org" id="org" autocomplete="organization" class="bg-zinc-900 block w-full rounded-md border-0 px-3.5 py-2 text-zinc-100 shadow-sm ring-1 ring-inset ring-zinc-400 placeholder:text-zinc-500 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6 transition-hover focus:outline-none" placeholder="Company Inc">
          </div>
        </div>
        <div class="sm:col-span-2">
          <label for="message" class="block text-sm font-semibold leading-6 text-zinc-200">Message</label>
          <div class="mt-2.5">
            <textarea v-model="form.message.value" name="message" id="message" rows="4" class="bg-zinc-900 block w-full rounded-md border-0 px-3.5 py-2 text-zinc-100 shadow-sm ring-1 ring-inset ring-zinc-400 placeholder:text-zinc-500 focus:ring-2 focus:ring-inset focus:ring-sky-600 sm:text-sm sm:leading-6 transition-hover focus:outline-none" placeholder="A message about how excited you are to eliminate Agile"></textarea>
          </div>
        </div>
      </div>
      <div class="mt-10">
        <button v-if="formIsValid && sendsMsgStatus === 'unsent' && !sendMsgLoading" type="submit" class="block w-full rounded-md bg-sky-600 px-3.5 py-2.5 text-center text-sm font-semibold text-white shadow-sm hover:bg-sky-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-sky-600 transition-hover">Submit</button>

        <div v-if="!formIsValid && sendsMsgStatus === 'unsent' && !sendMsgLoading" class="w-full">
          <div class="group">
            <button disabled class="block w-full rounded-md bg-sky-500 px-3.5 py-2.5 text-center text-sm font-semibold text-zinc-200 shadow-sm cursor-not-allowed">Submit</button>              
            <span
              class="block mt-1 text-xs text-red-500 pointer-events-none max-w-2xl opacity-0 transition-opacity group-hover:opacity-100"
            >
              {{ formIsMissingMessage }}
            </span>
          </div>
        </div>

        <button v-if="sendMsgLoading" disabled class="inline-flex items-center justify-center w-full rounded-md bg-sky-500 px-3.5 py-2.5 text-center text-sm font-semibold text-zinc-100 shadow-sm cursor-wait">
          <svg class="mr-2 h-3 w-3 animate-spin -ml-1 text-white" xmlns="http://www.w3.org/2000/svg" fill="none"
            viewBox="0 0 24 24">
            <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
            <path class="opacity-75" fill="currentColor"
              d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z">
            </path>
          </svg>
          Submit
        </button>
        <button v-if="sendsMsgStatus === 'sent' || sendsMsgStatus === 'error'" disabled class="block w-full rounded-md bg-sky-500 px-3.5 py-2.5 text-center text-sm font-semibold text-zinc-100 shadow-sm cursor-not-allowed">Submit</button>

        <!-- form alert -->
        <div class="mt-2">
          <!-- error -->
          <div v-if="sendsMsgStatus === 'error'" class="rounded-md bg-sky-50 p-4">
            <div class="flex">
              <div class="flex-shrink-0">
                <svg class="h-5 w-5 text-sky-400" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM8.28 7.22a.75.75 0 00-1.06 1.06L8.94 10l-1.72 1.72a.75.75 0 101.06 1.06L10 11.06l1.72 1.72a.75.75 0 101.06-1.06L11.06 10l1.72-1.72a.75.75 0 00-1.06-1.06L10 8.94 8.28 7.22z" clip-rule="evenodd" />
                </svg>
              </div>
              <div class="ml-3">
                <h3 class="text-sm font-medium text-sky-800">Error</h3>
                <p class="mt-2 text-sm text-sky-700">{{ sendsMsgErrorStatus }}</p>
              </div>
            </div>
          </div>

          <!-- success -->
          <div v-if="sendsMsgStatus === 'sent'" class="rounded-md bg-green-50 p-4">
            <div class="flex">
              <div class="flex-shrink-0">
                <svg class="h-5 w-5 text-green-400" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.857-9.809a.75.75 0 00-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 10-1.06 1.061l2.5 2.5a.75.75 0 001.137-.089l4-5.5z" clip-rule="evenodd" />
                </svg>
              </div>
              <div class="ml-3">
                <h3 class="text-sm font-medium text-green-800">Success</h3>
                <div class="mt-2 text-sm text-green-700">
                  <p>We will reach out to you shortly.</p>
                </div>
              </div>
            </div>
          </div>

        </div>
      </div>
    </form>
  </div>
</template>

<script setup lang="ts">

const form = ref<{
  firstName: { value: null | string, requisky: boolean, friendlyName: string },
  lastName: { value: null | string, requisky: boolean, friendlyName: string  },
  org: { value: null | string, requisky: boolean, friendlyName: string  },
  email: { value: null | string, requisky: boolean, friendlyName: string  },
  message: { value: string, requisky: boolean, friendlyName: string  },
}>({
  firstName: {value: null, requisky: true, friendlyName: "First Name" },
  lastName: {value: null, requisky: true, friendlyName: "Last Name" },
  org: {value: null, requisky: false, friendlyName: "Organization" },
  email: {value: null, requisky: true, friendlyName: "Email" },
  message: {value: "", requisky: false, friendlyName: "Message" },
})

const emailIsValid = computed(() => {
  if (!form.value.email.value) {
    return false
  }
  const regex = /(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))/
  const re = new RegExp(regex)
  return re.test(form.value.email.value.toLowerCase())
})

const formIsValid = computed(() => {
  if (form.value.firstName.value && form.value.lastName.value && emailIsValid.value) {
    return true
  }
  return false
})

const formIsMissingMessage = computed(() => {
  let isMissingMessage = ""
  for (const key in form.value) {
    // @ts-ignore
    const val = form.value[key].value
    // @ts-ignore
    const friendlyName = form.value[key].friendlyName
    // @ts-ignore
    const isRequisky = form.value[key].requisky

    // this should not be hardcoded
    if (key === 'email' && !emailIsValid.value) {
      isMissingMessage += `${friendlyName} is not valid, `
      continue
    }

    if (isRequisky && !val) {
      isMissingMessage += `${friendlyName} is required, `
    }
  }

  // remove trailing comma and any whitespace
  isMissingMessage = isMissingMessage.slice(0, isMissingMessage.length - 2).trim()
  return isMissingMessage
})


const sendMsgLoading = ref(false)
const sendsMsgStatus = ref<"unsent" | "sent" | "error">("unsent")
const sendsMsgErrorStatus = ref<string | null>(null)

async function sendMessage() {
  sendMsgLoading.value = true
  const { error } = await useFetch("/api/messages", {
    method: "POST",
    body: {
      firstName: form.value.firstName.value,
      lastName: form.value.lastName.value,
      email: form.value.email.value,
      org: form.value.org.value,
      message: form.value.message.value,
    }
  })

  sendMsgLoading.value = false
  if (error.value) {
    sendsMsgStatus.value = "error"
    sendsMsgErrorStatus.value = "Something went wrong went sending your message, please try again later."
    return
  }

  sendsMsgStatus.value = "sent"
}

useHead({
  title: 'AiSu - Private Beta Signup',
  meta: [
    // PRIMARY TAGS
    { hid: 'description', name: 'description', content: "We're now accepting requests to signup for our private beta. Please fill out the below form and we'll reach out to you to get things started." },
    { hid: 'title', name: 'title', content: 'AiSu - Private Beta Signup' },

    // OPEN GRAPH/FACEBOOK
    { hid: 'og:type', property: 'og:type', content: 'website' },
    // { hid: 'og:url', property: 'og:url', content: config.public.appBase },
    { hid: 'og:title', property: 'og:title', content: 'AiSu - Private Beta Signup' },
    { hid: 'og:image', property: 'og:image', content: '/meta_card.png' },

    // TWITTER
    { name: 'twitter:card', content: 'summary_large_image' },
    { name: 'twitter:title', content: 'AiSu - Private Beta Signup' },
    { name: 'twitter:description', content: "We're now accepting requests to signup for our private beta. Please fill out the below form and we'll reach out to you to get things started." },
    { name: 'twitter:image', content: '/meta_card.png' }
  ]
}) 
</script>
