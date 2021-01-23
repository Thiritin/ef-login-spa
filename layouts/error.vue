<template>
  <div>
    <div class="absolute left-0 bottom-0 pointer-events-none hidden lg:block">
      <img alt="Background Logo" src="~/assets/bg-logo.svg"/>
    </div>
    <div
      class="container px-4 sm:px-12 pt-16 pb-12 mx-auto flex items-center md:min-h-screen md:-mt-12"
      style="max-width:600px"
    >
      <nuxt />
    </div>
  </div>
</template>

<script>
export default {
  name: "error.vue"
}
</script>

<style scoped>

</style>
