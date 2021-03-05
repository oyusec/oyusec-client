<template>
  <div class="user-bg">
    <v-row class="mx-3">
      <v-col v-for="item in challenges" :key="item.title" cols="6">
        <v-tooltip bottom>
          <template #activator="{ on, attrs }">
            <span v-text="item.title" />
            <v-progress-linear
              height="8px"
              :value="item.value"
              :color="item.color"
              v-bind="attrs"
              rounded
              v-on="on"
            ></v-progress-linear>
          </template>
          <span v-text="item.value + '%'"></span>
        </v-tooltip>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  // Update this later
  data: () => ({
    challenges: [
      {
        title: 'Cryptography',
        color: 'red darken-2',
        value: 0,
      },
      {
        title: 'Programming',
        color: 'pink darken-2',
        value: 0,
      },
      {
        title: 'Miscellaneous',
        color: 'purple darken-1',
        value: 0,
      },
      {
        title: 'Reverse Engineering',
        color: 'deep-purple darken-2',
        value: 0,
      },
      {
        title: 'Web exploitation',
        color: 'amber accent-4',
        value: 0,
      },
      {
        title: 'Binary exploitation',
        color: 'blue darken-2',
        value: 0,
      },
      {
        title: 'Forensics',
        color: 'orange darken-3',
        value: 0,
      },
    ],
  }),
}
</script>
