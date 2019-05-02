<template>
  <v-layout row fixed class="dick">
    <!-- Orange underlying toolbar -->
    <v-toolbar
      flat
      fixed
      height="75px"
      color="orange"
      width="100%"
    >
    </v-toolbar>
    <!-- Main Toolbar -->
    <v-toolbar fixed>
      <v-toolbar-side-icon class="hidden-md-and-up" @click="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title id="waitAnimate1" class="text-uppercase display-1"><v-btn flat transparent class="display-1" v-on:click="switchContent(nav.home)">Package Man</v-btn></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <template v-for="(page, i) in nav">
          <v-btn flat :key="i" :class="{active: page.show, orange: page.show}" class="title" :disabled="page.show" @click="sendData(page)">{{ page.title }}</v-btn>
        </template>
      </v-toolbar-items>

      <!-- Mobile Navigation Drawer -->
      <v-navigation-drawer
        v-model="drawer"
        absolute
        temporary
        class="overflow-vis"
      >
        <v-list class="pa-1">
          <v-list-tile avatar>
            <!-- <v-list-tile-avatar>
              <img src="https://randomuser.me/api/portraits/men/85.jpg">
            </v-list-tile-avatar> -->

            <v-list-tile-content>
              <v-list-tile-title class="title">PACKAGE MAN</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>

        <v-list class="pt-0" dense>
          <v-divider></v-divider>

          <v-list-tile
            v-for="item in nav"
            :key="item.title"
            @click="switchContent(item)"
            class="nav-bg text-uppercase"
            :class="{orange: item.show}"
          >
            <!-- <v-list-tile-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-tile-action> -->

            <v-list-tile-content>
                <v-list-tile-title>{{ item.title }}</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-navigation-drawer>
    </v-toolbar>
  </v-layout>
</template>

<script>
import EventBus from '../eventbus.js'

export default {
  name: 'Navigation',
  data () {
    return {
      nav: {
        home: {
          title: 'Home',
          show: true
        },
        about: {
          title: 'About',
          show: false
        },
        blog: {
          title: 'Blog',
          show: false
        },
        buy: {
          title: 'Buy',
          show: false
        },
        community: {
          title: 'Community',
          show: false
        }
      },
      drawer: false
    }
  },
  methods: {
    sleep: async function (ms) {
      return new Promise(resolve => setTimeout(resolve, ms))
    },
    sendData: async function (data) {
      this.nav.home.show = false
      this.nav.about.show = false
      this.nav.community.show = false
      this.nav.buy.show = false
      this.nav.blog.show = false

      data.show = true

      await this.sleep(50)
      this.drawer = false
      this.$vuetify.goTo(0, this.options)
      const payload = {
        page: data.title
      }
      EventBus.$emit('TOOLBAR_CLICKED', payload)
      console.log('Sending Data')
    }
  }
}
</script>

<style>
</style>
