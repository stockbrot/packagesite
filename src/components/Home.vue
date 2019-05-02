<template>
  <div>
    <section>
      <v-parallax v-bind:src="require('../assets/packageman.png')" height="550">
        <v-container fluid>
          <v-layout row fill-height>
            <v-flex d-flex xs12>
              <v-flex d-flex xs6>
                <v-layout
                  column
                  align-center
                  justify-center
                  class="white--text"
                >
                  <!-- Box -->
                  <v-icon id="waitAnimate4" size="200px" class="orange--text">fa-box-open</v-icon>
                  <!-- Text -->
                  <h1 id="waitAnimate2" class="orange--text mb-2 display-1 text-xs-center text-uppercase card-padding">{{ paralax.headline }}</h1>
                  <div id="waitAnimate3" class="subheading mb-3 text-xs-center card-padding">{{ paralax.subheading }}</div>
                  <!-- Arrows -->
                  <v-btn @click="$vuetify.goTo('#first', options)" icon>
                    <v-icon id="waitAnimate5" size="50px" class="animated infinite rubberBand orange--text delay-1s">fa-angle-double-down</v-icon>
                  </v-btn>
                </v-layout>
              </v-flex>
              <!-- YouTube / Banner -->
              <v-flex d-flex xs6>
                <v-layout
                  column
                  align-center
                  justify-center
                >
                  <iframe id="youtube" width="560" height="315" src="https://www.youtube.com/embed/7FQa_noUneo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </v-layout>
              </v-flex>
            </v-flex>
          </v-layout>
        </v-container>
      </v-parallax>
    </section>

    <!-- Three important parts -->
    <section>
      <v-layout
        column
        wrap
        class="my-5"
        align-center
      >
        <v-flex xs12 sm4 class="my-3">
          <div class="text-xs-center">
            <h2 id="first" class="headline">{{ main3.headline }}</h2>
            <span class="subheading">
              {{ main3.subheading }}
            </span>
          </div>
        </v-flex>
        <v-flex xs12>
          <v-container grid-list-xl>
            <v-layout align-space-around justify-space-around row wrap>
              <template v-for="main in main3.items">
                <v-flex d-flex xs12 s12 md4 :key="main.id">
                  <v-card class="transparent elevation-5">
                    <v-card-text class="text-xs-center">
                      <v-icon x-large class="orange--text">{{ main.icon }}</v-icon>
                    </v-card-text>
                    <v-card-title primary-title class="layout justify-center">
                      <div class="headline text-xs-center">{{ main.title }}</div>
                    </v-card-title>
                    <v-card-text>{{ main.text }}</v-card-text>
                  </v-card>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </v-flex>
      </v-layout>
    </section>

    <!-- Call to Action -->
    <section>
      <v-parallax :src="require('../assets/packageman2.png')" height="380">
        <v-layout column align-center justify-center>
          <div class="headline orange--text mb-3 text-xs-center card-padding">{{ cta.headline }}</div>
          <span class="white--text card-padding">{{ cta.subheading }}</span>
          <v-btn
            class="orange mt-5"
            dark
            large
            v-on:click="switchContent(nav.community)"
          >
            {{ cta.button }}
          </v-btn>
        </v-layout>
      </v-parallax>
    </section>

    <!-- Info & Contact -->
    <section>
      <v-container grid-list-xl>
        <v-layout row wrap justify-center class="my-5">
          <v-flex d-flex xs12 sm4>
            <v-card class="elevation-5 transparent">
              <v-card-title primary-title class="layout justify-center">
                <div class="headline">{{ company.headline }}</div>
              </v-card-title>
              <v-card-text>
                {{ company.text }}
              </v-card-text>
            </v-card>
          </v-flex>
          <v-flex d-flex xs12 sm4 offset-sm1>
            <v-card class="elevation-5 transparent">
              <v-card-title primary-title class="layout justify-center">
                <div class="headline">{{ company.contact.headline }}</div>
              </v-card-title>
              <v-card-text>
                {{ company.contact.text }}
              </v-card-text>
              <v-list class="transparent">
                <v-list-tile>
                  <v-list-tile-action>
                    <v-icon class="orange--text">phone</v-icon>
                  </v-list-tile-action>
                  <v-list-tile-content>
                    <v-list-tile-title>{{ company.contact.phone }}</v-list-tile-title>
                  </v-list-tile-content>
                </v-list-tile>
                <v-list-tile>
                  <v-list-tile-action>
                    <v-icon class="orange--text">place</v-icon>
                  </v-list-tile-action>
                  <v-list-tile-content>
                    <v-list-tile-title>{{ company.contact.location }}</v-list-tile-title>
                  </v-list-tile-content>
                </v-list-tile>
                <v-list-tile>
                  <v-list-tile-action>
                    <v-icon class="orange--text">email</v-icon>
                  </v-list-tile-action>
                  <v-list-tile-content>
                    <v-list-tile-title>{{ company.contact.mail }}</v-list-tile-title>
                  </v-list-tile-content>
                </v-list-tile>
              </v-list>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      msg: 'Awesome',
      paralax: {
        headline: 'Out soon!',
        subheading: 'Available on all major platforms!'
      },
      // Three Important Main Site
      main3: {
        headline: 'Three ways to play',
        subheading: 'You should play now!',
        items: {
          one: {
            id: 1,
            icon: 'fa-truck',
            title: 'Singleplayer Story',
            text: 'Play as Carl the Package deliverer in a crazy and colorfull world.'
          },
          two: {
            id: 2,
            icon: 'fa-truck',
            title: 'Singleplayer Arcade',
            text: 'In this mode, your only objective is to acquire as many points as possible! Climb the leaderboards and get daily rewards based on your rank.'
          },
          three: {
            id: 3,
            icon: 'fa-truck',
            title: 'Multiplayer',
            text: 'Play with or against your Friends, either to gain points or just for fun!.'
          }
        }
      },
      cta: {
        headline: 'Join our Community',
        subheading: 'or start a discussion in our Forums',
        button: 'To Community hub'
      },
      company: {
        headline: 'Company Info',
        text: 'Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Nullam in aliquet odio. Aliquam eu est vitae tellus bibendum tincidunt. Suspendisse potenti.',
        contact: {
          headline: 'Contact Us',
          text: 'Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare.',
          phone: '777-867-5309',
          location: 'Chicago, US',
          mail: 'john@vuetifyjs.com'
        }
      }
    }
  },
  computed: {
    options () {
      return {
        offset: 100
      }
    }
  }
}
</script>

<style>
</style>
