<template>
  <v-container grid-list-xs>
    <v-layout row justify-center align-center wrap>
      <v-flex xs12 sm12 md1>
        <v-slide-y-transition>
          <v-layout
            v-show="loaded"
            column
            justify-center
            align-center
            wrap
            class="ma-2"
          >
            <v-btn
              small
              depressed
              fab
              color="primary"
              nuxt
              to="/"
            >
              <v-icon>mdi-chevron-left</v-icon>
            </v-btn>
          </v-layout>
        </v-slide-y-transition>
      </v-flex>
      <v-flex xs12 sm12 md11>
        <v-layout row wrap>
          <v-flex
            v-for="(product, index) in menu"
            :key="index"
            xs12
            sm12
            md6
            class="pa-2"
          >
            <v-slide-y-reverse-transition>
              <v-card v-show="loaded" :to="`/${product.link}`" class="pa-2 pa-md-4 overflow--hidden card--hover" outlined>
                <v-card-title class="title-container justify-center justify-md-start" primary-title>
                  <div>
                    <h2 class="text-h5 text-lg-h4 text-truncate">
                      「 {{ product.text }} <span>{{ product.category }} 」</span>
                    </h2>
                  </div>
                </v-card-title>
                <v-card-text class="text-center text-md-left">
                  <div class="text-container px-2 px-md-6">
                    <p>
                      {{ product.desc }}
                    </p>
                  </div>
                </v-card-text>
                <v-img class="particle-hover" width="150" :src="logo" />
              </v-card>
            </v-slide-y-reverse-transition>
          </v-flex>
        </v-layout>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<style lang="scss">
.card--hover:hover {
  .particle-hover {
    bottom: 0;
    right: 0;
    transform: rotate(0deg) scale(2);
  }
}

.particle-hover {
  position: absolute;
  transition: 0.7s ease !important;
  bottom: -100%;
  right: 0;
  opacity: 0.1;
  transform: rotate(180deg) scale(1);
}
</style>

<script>
import Logo from '@/static/logo/logo_flat_sak.png'

export default {
  data: () => ({
    logo: Logo,
    menu: [
      {
        text: 'Sakura',
        category: 'Members',
        link: 'member',
        desc: 'People who have contributed to the Team'
      },
      {
        text: 'Sakura',
        category: 'MEPS',
        link: 'project/mep',
        desc: 'Sakura Multi Editor Projects'
      },
      {
        text: 'Sakura',
        category: 'Projects',
        link: 'project/dedication',
        desc: 'Sakura dedications'
      },
      {
        text: 'Sakura',
        category: 'Collabs',
        link: 'project/collab',
        desc: 'Sakura Collaboration Projects'
      }
    ],
    loaded: false
  }),
  mounted () {
    setTimeout(() => {
      this.loaded = true
    }, 250)
  }
}
</script>
