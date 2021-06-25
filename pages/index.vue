<template>
  <v-container grid-list-xs class="my-4">
    <v-layout row justify-center align-center wrap>
      <v-flex xs5 sm4 md4>
        <kinesis-container>
          <kinesis-element
            :strength="strengthKinesis"
            type="depth"
            transform-origin="50% 50%"
          >
            <v-slide-y-transition>
              <v-img
                v-show="loaded"
                class="logo"
                width="100%"
                contain
                :src="logo"
                :lazy-src="logo"
                aspect-ratio="1"
                @click="toggleTheme"
              >
                <template v-slot:placeholder>
                  <v-row
                    class="fill-height ma-0"
                    align="center"
                    justify="center"
                  >
                    <v-progress-circular indeterminate color="primarylight" />
                  </v-row>
                </template>
              </v-img>
            </v-slide-y-transition>
          </kinesis-element>
        </kinesis-container>
      </v-flex>
      <v-flex xs12 sm12 md7>
        <v-slide-y-reverse-transition>
          <v-card v-show="loaded" class="pa-2 pa-md-6" outlined>
            <v-card-title class="title-container justify-center justify-md-start" primary-title>
              <div>
                <h2 class="text-h5 text-lg-h4 text-truncate">
                  「 Sakura <span>Editors 」</span>
                </h2>
              </div>
            </v-card-title>
            <v-card-text class="text-center text-md-left">
              <div class="text-container px-2 px-md-6">
                <p>
                  桜/Sakura/ is an Editing team dedicated for creating inspiring Art.
                  <br>
                  Team Lead: Sakuratree ツ
                </p>
                <p>AMVS | MMVS | Edits | Design | Art | Effects</p>
                <p>Youtube: https://www.youtube.com/channel/UCXpJ7nHpU89__ybywv34rXg/featured </p>
                <p>Instagram: https://www.instagram.com/sakura.editors/ </p>
                <p>RECRUITMENT FROM: </p>
              </div>
              <div class="mt-8 mx-4">
                <template v-for="(social, index) in links">
                               
                </template>
              </div>
            </v-card-text>
          </v-card>
        </v-slide-y-reverse-transition>
      </v-flex>
      <v-flex xs12 sm12 md1 class="mt-2">
        <v-slide-y-transition>
          <v-layout
            v-show="loaded"
            class="flex-row flex-md-column"
            justify-center
            align-center
            wrap
          >
            </template>
          </v-layout>
        </v-slide-y-transition>
      </v-flex>
    </v-layout>
  </v-container>
</template>
<script>
import {
  KinesisContainer,
  KinesisElement
} from 'vue-kinesis'
import LogoText from '@/static/logo/logo_sak.png'
import LogoTextWhite from '@/static/logo/logo_white_sak.png'

export default {
  components: {
    KinesisContainer,
    KinesisElement
  },
  data: () => ({
    loaded: false,
    descriptions: [
      '桜/Sakura/ is an Editing team dedicated for creating inspiring Art.',
      'Team Lead: Sakuratree ツ'
    ],
    descriptions2: [
      'AMVS | MMVS | Edits | Design | Art | Effects'
    ],
    socials: [
      {
        text: 'Youtube',
        icon: 'mdi-youtube',
        link: 'https://www.youtube.com/channel/UCs2piDFpWHC4lMhgLx33Jzg'
      },
      {
        text: 'Instagram',
        icon: 'mdi-instagram',
        link: 'https://www.instagram.com/sakuratreeloll.pvt/'
      },
      {
        text: 'Discord',
        icon: 'mdi-discord',
        link: 'https://discord.gg/eheKrTw3JB'
      }
    ]
  }),
  computed: {
    links () {
      return this.$store.getters.links || []
    },
    logo () {
      switch (this.$vuetify.theme.dark) {
        case false: return LogoText
        default: return LogoTextWhite
      }
    },
    widthLogo () {
      switch (this.$vuetify.breakpoint.smAndDown) {
        case true: return '100%'
        case false: return '100%'
        default: return '100%'
      }
    },
    strengthKinesis () {
      switch (this.$vuetify.breakpoint.smAndDown) {
        case true: return 0
        default: return 20
      }
    }
  },
  mounted () {
    setTimeout(() => {
      this.loaded = true
    }, 250)
  },
  methods: {
    toggleTheme () {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark
      localStorage.setItem('kireihana_dark', this.$vuetify.theme.dark)
      // this.$vuetify.theme.themes.light.primary = '#F98298'
      // this.$vuetify.theme.themes.dark.primary = '#F98298'
    }
  }
}
</script>
