<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-md">
        <div class="text-h3"> My ToDoList </div>
        <div class="text-subtitle"> {{todayDate}} </div>
      </div>
      <q-img class="header-img absolute-top" src="..\assets\pngwing.com.png" />
    </q-header>

    <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
      >
        <q-scroll-area style="height: calc(100% - 185px); margin-top: 185px; border-right: 1px solid #ddd">
          <!-- ToDoList -->
          <q-list padding>
            <q-item  
            to="/" exact
            clickable 
            v-ripple>
              <q-item-section avatar>
                <q-icon name="list" />
              </q-item-section>

              <q-item-section>
                ToDo List
              </q-item-section>
            </q-item>
          </q-list>
          <!-- help -->
          <q-list padding>
            <q-item  
            to="/help" exact
            clickable 
            v-ripple>
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>

              <q-item-section>
                Help
              </q-item-section>
            </q-item>
          </q-list>
          <!-- about -->
          <q-list padding>
            <q-item  
            to="/about" exact
            clickable 
            v-ripple>
              <q-item-section avatar>
                <q-icon name="info" />
              </q-item-section>

              <q-item-section>
                About
              </q-item-section>
            </q-item>
          </q-list>
          <!-- contacts -->
          <q-list padding>
            <q-item  
            to="/contacts" exact
            clickable 
            v-ripple>
              <q-item-section avatar>
                <q-icon name="contacts" />
              </q-item-section>

              <q-item-section>
                Contacts
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="..\assets\background.gif" style="height: 185px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="..\assets\myself.jpg">
            </q-avatar>
            <div class="text-weight-bold text-color-name">Kamenik Ilya</div>
            <div class="text-color-name">kamenikii@yandex.ru</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'
import { date } from 'quasar'

defineOptions({
  name: 'MainLayout'
})

/**
 *    ██████╗░░█████╗░████████╗███████╗
 *    ██╔══██╗██╔══██╗╚══██╔══╝██╔════╝
 *    ██║░░██║███████║░░░██║░░░█████╗░░
 *    ██║░░██║██╔══██║░░░██║░░░██╔══╝░░
 *    ██████╔╝██║░░██║░░░██║░░░███████╗
 *    ╚═════╝░╚═╝░░╚═╝░░░╚═╝░░░╚══════╝
 */
const todayDate = date.formatDate(Date.now(), 'YYYY, D MMMM, dddd')

const linksList = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer () {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>

<style lang="scss">
.header-img {
  height: 100%;
  z-index: -1;
  opacity: 0.1;
}

.text-color-name {
  color: $primary;
  font-size: 20px;
}

</style>