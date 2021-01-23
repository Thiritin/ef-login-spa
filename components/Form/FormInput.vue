<template>
  <input
    v-bind:value="value"
    v-on:input="updateValue($event.target.value)"
    class="w-full bg-gray-200 p-6 py-5 rounded-lg transition-all duration-75 ease-in-out tran border-transparent border-2 focus:border-primary-500 focus:outline-none"
    style="-webkit-box-sizing: border-box;"
  />
</template>

<script>
export default {
  name: "FormInput",
  props: {
    value: String
  },
  methods: {
    updateValue: function (value) {
      this.$emit('input', value)
    }
  }
}
</script>
