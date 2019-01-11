<template>
  <v-card-text class="pt-4">
    <div>
        <v-form v-model="valid" ref="form">
          <v-text-field
            label="Enter your e-mail address"
            v-model="email"
            :rules="emailRules"
            required
          ></v-text-field>
          <v-text-field
            label="Enter your password"
            v-model="password"
            min="8"
            :append-icon="e1 ? 'visibility_off' : 'visibility'"
            :append-icon-cb="() => (e1 = !e1)"
            :type="e1 ? 'password' : 'text'"
            :rules="passwordRules"
            counter
            required
          ></v-text-field>
          <v-layout justify-space-between>
              <v-btn @click="submit" :class=" { 'blue darken-4 white--text' : valid, disabled: !valid }">Login</v-btn>
              <v-btn to="/auth/forgot" @click.native="close" flat>Forgot Password</v-btn>
          </v-layout>
        </v-form>
    </div>
  </v-card-text>
</template>

<script>
export default {
  data() {
    return {
      valid: false,
      e1: true,
      password: '',
      passwordRules: [
        (v) => !!v || 'Password is required',
      ],
      email: '',
      emailRules: [
        (v) => !!v || 'E-mail is required',
        (v) => /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
      ],
    }
  },
  mounted() {
    let self = this
    window.addEventListener('keyup', function (event) {
      if (event.keyCode === 13) {
        self.submit()
      }
    })
  },
  methods: {
    submit () {
      if (this.$refs.form.validate()) {
        this.$refs.form.$el.submit()
      }
    },
    clear () {
      this.$refs.form.reset()
    },
    close() {
      this.clear()
      this.$emit('update:dialog_login', false)
    }
  }
}
</script>
