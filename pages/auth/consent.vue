<template>
  <div class="w-full">
    <Logo></Logo>
    <LoginScreenWelcome class="mb-6" sub-title="Eurofurence Registration would like to access the following Data:"
                        title="Grant Permission"></LoginScreenWelcome>
    <div class="ml-4 mb-2 flex items-center">
      <div class="bg-gray-200 rounded p-2 inline-block">
        <svg aria-hidden="true" class="svg-inline--fa fa-paw fa-w-16 w-6 h-6 text-primary-700" data-icon="paw"
             data-prefix="fas"
             focusable="false" role="img"
             viewBox="0 0 512 512" xmlns="http://www.w3.org/2000/svg">
          <path
            d="M256 224c-79.41 0-192 122.76-192 200.25 0 34.9 26.81 55.75 71.74 55.75 48.84 0 81.09-25.08 120.26-25.08 39.51 0 71.85 25.08 120.26 25.08 44.93 0 71.74-20.85 71.74-55.75C448 346.76 335.41 224 256 224zm-147.28-12.61c-10.4-34.65-42.44-57.09-71.56-50.13-29.12 6.96-44.29 40.69-33.89 75.34 10.4 34.65 42.44 57.09 71.56 50.13 29.12-6.96 44.29-40.69 33.89-75.34zm84.72-20.78c30.94-8.14 46.42-49.94 34.58-93.36s-46.52-72.01-77.46-63.87-46.42 49.94-34.58 93.36c11.84 43.42 46.53 72.02 77.46 63.87zm281.39-29.34c-29.12-6.96-61.15 15.48-71.56 50.13-10.4 34.65 4.77 68.38 33.89 75.34 29.12 6.96 61.15-15.48 71.56-50.13 10.4-34.65-4.77-68.38-33.89-75.34zm-156.27 29.34c30.94 8.14 65.62-20.45 77.46-63.87 11.84-43.42-3.64-85.21-34.58-93.36s-65.62 20.45-77.46 63.87c-11.84 43.42 3.64 85.22 34.58 93.36z"
            fill="currentColor"></path>
        </svg>
      </div>
      <span class="ml-2 text-gray-800 font-semibold">Your User Profile</span>
    </div>
    <div class="ml-4 mb-10 flex items-center">
      <div class="bg-gray-200 rounded p-2 inline-block">
        <svg aria-hidden="true" focusable="false" data-prefix="fas" data-icon="envelope" class="svg-inline--fa fa-envelope fa-w-16 w-6 h-6 text-primary-700" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path fill="currentColor" d="M502.3 190.8c3.9-3.1 9.7-.2 9.7 4.7V400c0 26.5-21.5 48-48 48H48c-26.5 0-48-21.5-48-48V195.6c0-5 5.7-7.8 9.7-4.7 22.4 17.4 52.1 39.5 154.1 113.6 21.1 15.4 56.7 47.8 92.2 47.6 35.7.3 72-32.8 92.3-47.6 102-74.1 131.6-96.3 154-113.7zM256 320c23.2.4 56.6-29.2 73.4-41.4 132.7-96.3 142.8-104.7 173.4-128.7 5.8-4.5 9.2-11.5 9.2-18.9v-19c0-26.5-21.5-48-48-48H48C21.5 64 0 85.5 0 112v19c0 7.4 3.4 14.3 9.2 18.9 30.6 23.9 40.7 32.4 173.4 128.7 16.8 12.2 50.2 41.8 73.4 41.4z"></path></svg>
      </div>
      <span class="ml-2 text-gray-800 font-semibold">Your E-Mail Address</span>
    </div>
    <div class="grid gap-3 grid-cols-2">
      <a href="#" class="w-full text-center rounded bg-gray-300 py-4 text-xl font-semibold text-gray-800">Decline</a>
      <a href="#" class="w-full text-center rounded bg-primary-700 py-4 text-xl font-semibold text-primary-100">Accept</a>
    </div>
  </div>
</template>

<script>
import Logo from "@/components/Logo";
import LoginScreenWelcome from "@/components/LoginScreenWelcome";

export default {
  name: 'consent',
  layout: 'auth',
  components: {LoginScreenWelcome, Logo},
  data() {
    return {
      email: '',
      password: '',
      submitStatus: null,
    }
  },
  methods: {}
}
</script>
