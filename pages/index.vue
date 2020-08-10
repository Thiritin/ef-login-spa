<template>
  <div
    class="container px-4 sm:px-12 pt-16 pb-12 mx-auto flex items-center md:min-h-screen"
    style="max-width:600px"
  >
    <div class="w-full">
      <Logo></Logo>
      <LoginScreenWelcome/>
      <FormInput
        v-model.trim.lazy="$v.email.$model"
        :placeholder="$t('email')"
        autocomplete="email"
        type="email"
        class="mb-4"
        :class="{'border-red-500 focus:border-red-500': (!$v.email.email ||! $v.email.required && submitStatus != null)}"/>
      <FormInput
        :class="{'border-red-500 focus:border-red-500': !$v.password.required && submitStatus != null}"
        :placeholder="$t('password')"
        autocomplete="password"
        class="mb-16"
        type="password"
        v-model.lazy="$v.password.$model"
      />
      <div class="flex flex-col">
        <button
          :class="submitStatus === 'PENDING' ? 'bg-primary-400' : 'bg-primary-500'"
          :disabled="submitStatus === 'PENDING'"
          @click="submit"
          class="py-3 rounded-lg px-12 ml-auto text-white text-2xl mb-4 font-semibold focus:outline-none"
        >
          {{ $t('sign_in') }}
        </button>
        <nuxt-link class="ml-auto text-gray-700" to="/auth/forgot-password">
          {{ $t('forgot_password_btn') }}
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
import {email, required} from 'vuelidate/lib/validators'
import Logo from "@/components/Logo";
import FormInput from "@/components/Form/FormInput";
import LoginScreenWelcome from "@/components/LoginScreenWelcome";

export default {
  layout: 'auth',
  components: {LoginScreenWelcome, FormInput, Logo},
  data() {
    return {
      email: '',
      password: '',
      submitStatus: null,
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
      console.log("suuubmit");
      this.$v.$touch();
      if (this.$v.$invalid) {
        console.log(this.$v);
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
