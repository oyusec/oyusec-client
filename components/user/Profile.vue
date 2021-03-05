<template>
  <div class="user-bg">
    <v-row class="mx-1">
      <v-col xs="12" cols="4" sm="3" md="4" lg="4" xl="3">
        <v-avatar size="100">
          <v-img src="logo.png" />
        </v-avatar>
      </v-col>
      <v-col xs="12" cols="8" sm="9" md="8" lg="8" xl="9">
        <h2>Byambadalai Sumiya</h2>
        <h3 class="mt-1 text-gray-400">ByamB4</h3>
        <h4 class="mt-1">500 pts</h4>
      </v-col>
      <v-col cols="12">
        <v-divider></v-divider>
      </v-col>
      <v-col cols="12">
        <v-icon
          v-for="index in data.fblood"
          :key="index"
          size="40"
          color="amber"
          >mdi-trophy</v-icon
        >
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data: () => ({
    data: {
      fblood: 5,
    },
  }),
}
</script>
