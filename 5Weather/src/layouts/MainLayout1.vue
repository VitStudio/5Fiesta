<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
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
        <div class="text-h3">Todo</div>
        <div class="text-subtitle1">{{ todaysDate }}</div>
      </div>
      <q-img
      src="https://cdn.pixabay.com/photo/2017/05/20/20/22/clouds-2329680_960_720.jpg" 
      class="header-image absolute-top"/>
    </q-header>

    <q-footer>
      <q-tabs>
        <q-route-tab
          v-for="nav in navs"
          :to="nav.to"
          :icon="nav.icon" 
          :key="nav.label"/>
      </q-tabs>
    </q-footer>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      class="bg-grey-1"
    >
      <q-list>
        <div class="col q-pt-md q-px-md">
          <div class="text-h2 text-weight-light">
              Menu
          </div>
        </div>
        <hr>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
          exact
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Home',
    icon: 'dns',
    link: '#'
  },
  {
    title: 'Settings',
    icon: 'settings',
    link: '#/settings'
  },
  {
    title: 'Account',
    icon: 'account_circle',
    link: ''
  },
];

import { date } from 'quasar';
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',
  
  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      tab: ref('images'),
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },
      computed: {
        todaysDate() {
          const timeStamp = Date.now()
          return date.formatDate(timeStamp, 'YYYY-MM-DDTHH:mm:ss.SSSZ')
        }
      }
    }
  }
});


</script>

<style language="scss">
.header-image {
  height: 100%;
  z-index: -1;
  opacity: 0.2;
  filter: grayscale(100%)
}
</style>