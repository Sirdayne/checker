<template>
  <v-app id="inspire">
    <v-navigation-drawer
            v-model="drawer"
            fixed
            app
    >
      <v-list dense>
        <v-list-tile @click="">
          <v-list-tile-action>
            <v-icon>home</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>Home</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile @click="">
          <v-list-tile-action>
            <v-icon>contact_mail</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>Contact</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar color="indigo" dark fixed app>
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title>Checker</v-toolbar-title>
    </v-toolbar>
    <v-content>
      <v-container fluid>
        <v-layout
                justify-center
                align-center
        >
            <v-flex>
                <v-list>
                    <template v-for="(item, index) in items">
                        <v-list-tile :key="index" avatar ripple @click="">
                            <v-list-tile-content>
                                <v-list-tile-title>{{ item.title }}</v-list-tile-title>
                            </v-list-tile-content>
                        </v-list-tile>
                        <v-divider v-if="index + 1 < items.length" :key="`divider-${index}`"></v-divider>
                    </template>
                </v-list>
            </v-flex>
        </v-layout>
      </v-container>
    </v-content>
    <v-footer color="indigo" app>
      <span class="white--text">&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data () {
    return {
      drawer: false,
      items: [
        { title: 'Чек-лист для подготовки 1', link: 'first.json' },
        { title: 'Чек-лист для подготовки 2', link: 'second.json' }
      ]
    }
  }
}
</script>
