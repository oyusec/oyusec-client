<template>
  <v-form ref="form" v-model="form.valid" @submit.prevent="submit">
    <v-card class="user-bg">
      <v-card-text>
        <v-text-field
          v-model="form.name"
          label="Бодлогын нэр"
          outlined
          dense
        ></v-text-field>
        <v-text-field
          v-model="form.category"
          label="Бодлогын төрөл"
          outlined
          dense
        ></v-text-field>
        <v-textarea
          v-model="form.description"
          placeholder="
            Та текстийн **bold** бас _italic_ болгох боломжтой.
            > Мөн санамж, бичиг зэрэг
          "
          class="mt-n2"
          outlined
          label="Бодлогын тайлбар"
          auto-grow
        ></v-textarea>
        <v-text-field
          v-model="form.value"
          label="Бодлогын оноо"
          placeholder="1000"
          type="number"
          outlined
          hint="Бодлогын эхлэх оноо буюу хэн ч бодоогүй үеийн оноо"
          dense
        ></v-text-field>
        <v-text-field
          v-model="form.decay"
          label="Бодлогын буурах хувь"
          type="number"
          placeholder="30"
          hint="Хүн бодлого бодох үед оноог хэр хэмжээтэй буурахыг тодорхойлно"
          outlined
          dense
        ></v-text-field>
        <v-text-field
          v-model="form.minimum"
          label="Бодлогын хамгийн бага оноо"
          placeholder="100"
          type="number"
          hint="Оноо буурсаар эцсийн дүндээ хэд болохыг тодорхойлно"
          outlined
          dense
        ></v-text-field>
        <v-select
          v-model="form.state"
          :item-text="form.state"
          :items="form.stateItems"
          dense
          label="Бодлогын төлөв"
          outlined
        >
        </v-select>
        <v-text-field
          v-model="form.flag"
          placeholder="flag{.*}"
          label="Бодлогын хариу"
          outlined
          dense
        ></v-text-field>
        <v-row justify="end">
          <v-card-actions>
            <v-btn small elevation="2" color="primary" type="submit">
              Болсон
            </v-btn>
          </v-card-actions>
        </v-row>
      </v-card-text>
    </v-card>
  </v-form>
</template>

<script>
export default {
  data: () => ({
    form: {
      state: 'Ил харагдана',
      stateItems: ['Ил харагдана', 'Нууцлагдмал'],
    },
  }),
  methods: {
    reset() {
      this.form.name = ''
      this.form.description = ''
      this.form.value = ''
      this.form.state = 'Ил харагдана'
      this.form.category = ''
      this.form.flag = ''
      this.form.decay = ''
      this.form.minimum = ''
      this.$refs.form.resetValidation()
    },

    submit() {
      this.$store.dispatch('admin/addChallenge', {
        $form: this.form,
        $type: 'dynamic',
      })
      this.reset()
    },
  },
}
</script>
