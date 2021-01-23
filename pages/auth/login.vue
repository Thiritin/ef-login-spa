<template>
  <div class="w-full">
    <Logo></Logo>
    <LoginScreenWelcome :sub-title="$t('loginscreen_sign_in_to_continue')" :title="$t('loginscreen_welcome')"
                        class="mb-10"/>
    <FormInput
      :class="{'border-red-500 focus:border-red-500': (!$v.email.email ||! $v.email.required && submitStatus != null)}"
      :placeholder="$t('email')"
      autocomplete="email"
      class="mb-4"
      type="email"
      v-model.trim.lazy="$v.email.$model"/>
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
      this.$v.$touch();
      if (this.$v.$invalid) {
        this.submitStatus = 'ERROR'
      } else {
        this.submitStatus = 'PENDING'
        this.$axios.post('/auth/login', {
          "email": this.email,
          "password": this.password,
          "login_challenge": this.$route.query.login_challenge
        }).then((res) => {
          this.$toast.clear()
          window.location = res['data']['data']['redirect_to'];
          this.$toast.success('Successfully authenticated')
          this.submitStatus = 'OK'
        }).catch((err) => {
            console.log(err.response);
            this.$toast.clear()
            this.$toast.error(err.response.data.message)
            this.submitStatus = ''
          }
        );
      }
    }
  }
}
</script>
