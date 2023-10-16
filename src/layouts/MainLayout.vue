<template>
  <q-layout view="lHh Lpr lFf" style="max-width: 1280px;margin:0 auto;">
    <q-header elevated>
      <q-toolbar class="row justify-center"  style="max-width: 1280px;margin:0 auto;">
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title class="column q-py-sm text-black">
          <div style="font-family: 'Noto Serif SC', serif; font-size:1.3em;">马克思主义原理</div>
          <div style="font-family: copperplate;">Basic Principles of Marxism</div>
        </q-toolbar-title>

        <div><q-input filled v-model="text" label="搜索..." /></div>
      </q-toolbar>
      <div class="flag-warp">
        <div class="flag">首页</div>
      </div>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header>
          Essential Links
        </q-item-label>

        <EssentialLink v-for="link in essentialLinks" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

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

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup() {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
<style scoped lang="scss">
@font-face {
  font-family: copperplate;
  src: url(/GreatVibes-Regular.ttf);
}
.flag-warp {
  box-shadow: 0 0 4px rgba(0, 0, 0, 0.24);
  background-color: red;

  .flag {
    position: relative;
    width: 80px;
    height: 50px;
    font-size: 1.2em;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #ff4b4b;
    left: 270px;
    box-shadow: 0 0 4px rgba(0, 0, 0, 0.24);
    &::before {
      content: '';
      width: 0;
      height: 0;
      border: 40px solid #ff4b4b;
      border-color: #ff4b4b transparent transparent transparent;
      bottom: -80px;
      z-index: 100;
      position: absolute;
    }
  }
}
</style>
