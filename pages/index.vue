<template>
  <v-container class="mt-10">
    <v-row align="center">
      <v-col>
        <v-window>
          <v-window-item>
            <v-card color="transparent">
              <v-card-text class="font-monts">
                <v-row class="mb-4 f-20" align="center">
                  <v-avatar size="50" class="mr-4">
                    <v-img
                      width="50"
                      height="50"
                      src="/oyusec-client/logo.png"
                    />
                  </v-avatar>
                  <strong class="f-25" v-text="competition.name" />
                </v-row>

                <span
                  class="f-19"
                  style="line-height: 200%"
                  v-text="competition.description"
                />
                <div class="text-center mt-10">
                  <p class="f-19">Бидэнтэй 4 нэгдээрэй</p>
                  <v-btn
                    v-for="link in links"
                    :key="link.icon"
                    icon
                    class="ml-5"
                    :href="link.url"
                    target="_blank"
                  >
                    <v-icon size="50" color="white" v-text="link.icon"></v-icon>
                  </v-btn>
                </div>
              </v-card-text>
            </v-card>
          </v-window-item>
        </v-window>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { mapState } from 'vuex'

export default {
  data: () => ({
    links: [
      {
        icon: 'mdi-facebook',
        url: 'https://facebook.com/oyusec/',
      },
      {
        icon: 'mdi-github',
        url: 'https://github.com/oyusec/',
      },
      {
        icon: 'mdi-discord',
        url: 'https://discord.gg/9fqVFEBAhv',
      },
    ],
  }),
  head() {
    return {
      title: 'Нүүр хуудас',
    }
  },
  computed: {
    ...mapState({
      competition: (state) => state.competition,
    }),
  },
}
</script>
