<template>
  <v-container>
    <v-row justify="center" class="font-cabin">
      <v-col xs="12" cols="12" sm="12" md="5" lg="5" xl="6">
        <v-form ref="form" v-model="form.valid" @submit.prevent="submit">
          <v-card class="user-bg mt-10" elevation="5" shaped>
            <v-card-title class="justify-center font-press f-17" primary-title
              >Шинэ хаяг нээх</v-card-title
            >
            <v-card-text>
              <v-text-field
                v-model="form.username"
                :rules="[rules.required, rules.counter, rules.letterOnly]"
                :counter="25"
                :loading="form.loading"
                class="mt-5"
                label="Хэрэглэгчийн нэр"
                hint="Сайт дээрх таны хэрэглэгчийн нэр"
                maxlength="25"
                outlined
                dense
              ></v-text-field>
              <v-text-field
                v-model="form.email"
                :rules="[rules.required, rules.email]"
                :loading="form.loading"
                label="Имэйл"
                type="email"
                hint="Хэзээ ч нийтэд харагдахгүй"
                outlined
                dense
                class="mt-2"
              ></v-text-field>
              <v-text-field
                v-model="form.password"
                :type="passwordShow ? 'text' : 'password'"
                :append-icon="passwordShow ? 'mdi-eye' : 'mdi-eye-off'"
                :rules="[rules.limitPass]"
                :loading="form.loading"
                label="Нууц үг"
                hint="Таны хаяганд нэвтрэхэд ашиглагдах нууц үг"
                outlined
                dense
                class="mt-2"
                @click:append="passwordShow = !passwordShow"
              ></v-text-field>
              <v-card-actions class="mt-2">
                <v-btn
                  :loading="form.loading"
                  :disabled="!form.valid"
                  rounded
                  elevation="2"
                  depressed
                  block
                  color="primary"
                  type="submit"
                >
                  Болсон
                </v-btn>
              </v-card-actions>
            </v-card-text>
          </v-card>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    form: {
      username: '',
      password: '',
      email: '',
      valid: true,
      loading: false,
    },
    passwordShow: false,
    rules: {
      required: (value) => !!value || 'Заавал бөглөх ёстой',
      counter: (value) => value.length <= 25 || 'Max 25 characters',
      email: (value) => {
        const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
        return pattern.test(value) || 'Дахин шалгана уу'
      },
      letterOnly: (value) => {
        const pattern = /^[A-Za-z0-9]+$/
        return pattern.test(value) || 'Зөвхөн тэмдэгт оруулна уу'
      },
      limitPass: (value) => value.length >= 8 || '8 тэмдэгтээс их байх ёстой',
    },
  }),
  head: () => ({
    title: 'Бүртгүүлэх',
  }),
  methods: {
    reset() {
      this.form = {
        username: '',
        email: '',
        password: '',
        loading: false,
        valid: true,
      }
      this.$refs.form.resetValidation()
    },
    submit() {
      this.form.loading = true
      this.$store.dispatch('user/registerUser', {
        nuxt: this.$nuxt,
        form: this.form,
      })
      this.reset()
    },
  },
}
</script>
