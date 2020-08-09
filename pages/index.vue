<template>
  <div
    class="container px-4 sm:px-12 pt-16 pb-12 mx-auto flex items-center md:min-h-screen"
    style="max-width:600px"
  >
    <div class="w-full">
      <img alt="Eurofurence Logo" src="~/assets/ef.svg"/>
      <div class="mt-12 mb-12">
        <h1 class="text-primary-500 font-semibold text-5xl">{{ $t('loginscreen_welcome') }}</h1>
        <h2 class="text-gray-600 text-3xl">{{ $t('loginscreen_sign_in_to_continue') }}</h2>
      </div>
      <div class="mb-4">
        <input
          :class="{'border-red-500 focus:border-red-500': (!$v.email.email ||! $v.email.required && $v.$anyError)}"
          :placeholder="$t('email')"
          autocomplete="email"
          class="w-full bg-gray-200 p-6 py-5 rounded-lg transition-all duration-75 ease-in-out tran border-transparent border-2 focus:border-2 focus:border-primary-500 focus:outline-none"
          style="-webkit-box-sizing: border-box;"
          type="email"
          v-model.trim.lazy="$v.email.$model"
        />
      </div>
      <div class="mb-16">
        <input
          :class="{'border-red-500 focus:border-red-500': !$v.password.required && $v.$anyError}"
          :placeholder="$t('password')"
          autocomplete="password"
          class="w-full bg-gray-200 p-6 py-5 rounded-lg transition-all duration-75 ease-in-out tran border-transparent border-2 focus:border-2 focus:border-primary-500 focus:outline-none"
          style="    -moz-box-sizing: border-box;"
          type="password"
          v-model.lazy="$v.password.$model"
        />
      </div>
      <div class="flex flex-col">
        <button
          :class="submitStatus === 'PENDING' ? 'bg-primary-400' : 'bg-primary-500'"
          :disabled="submitStatus === 'PENDING'"
          @click="submit"
          class="py-3 rounded-lg px-12 ml-auto text-white text-2xl mb-4 font-semibold focus:outline-none"
        >
          {{ $t('sign_in') }}
        </button>
        <nuxt-link class="ml-auto text-gray-700" to="/auth/forgot-password"
        >{{ $t('forgot_password_btn') }}
        </nuxt-link
        >
      </div>
    </div>
  </div>
</template>

<script>
import {email, required} from 'vuelidate/lib/validators'

export default {
  layout: 'auth',
  components: {},
  data() {
    return {
      email: '',
      password: '',
      submitStatus: '',
    }
  },
  validations: {
    email: {
      required,
      email
    },
    password: {
      required
    }
  },
  methods: {
    submit() {
      console.log('Submit');
      this.$v.$touch()
      if (this.$v.$invalid) {
        this.submitStatus = 'ERROR'
      } else {
        this.submitStatus = 'PENDING'
        setTimeout(() => {
          this.submitStatus = 'OK'
        }, 500)
      }
    }
  }
}
</script>
