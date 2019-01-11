<template>
  <v-card-text class="pt-4">
    <v-form v-model="valid" ref="form">
      <v-text-field
        label="Enter your e-mail address"
        v-model="email"
        :rules="emailRules"
        required
      ></v-text-field>
      <v-layout justify-space-between>
          <v-btn @click="submit" :class=" { 'blue darken-4 white--text' : valid, disabled: !valid }">Send Reset Email</v-btn>
      </v-layout>
    </v-form>
  </v-card-text>
</template>


<script>
export default {
  data() {
    return {
      valid: false,
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
