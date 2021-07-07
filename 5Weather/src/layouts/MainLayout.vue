<template>
  <q-layout view="hHh Lpr fFf"> <!-- Be sure to play with the Layout demo on docs -->

    <!-- (Optional) The Header -->
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          round
          dense
          icon="menu"
          @click="toggleLeftDrawer"
        />
      </q-toolbar>
       <div class="q-px-lg q-pt-xl q-mb-md">
         <div class="text-h3">Todo</div>
         <div class="class text-subtitle1">{{ todaysDate }}</div>
       </div>
       <q-img
         src="https://cdn.pixabay.com/photo/2017/05/20/20/22/clouds-2329680_960_720.jpg"
         class="header-image absolute-top" />
    </q-header>

    <!-- (Optional) Footer section below -->
    <q-footer>
      <q-tabs>
        <q-route-tab class=""
          icon="home"
          label="Home" />
      </q-tabs>
    </q-footer>

    <!-- (Optional) A Drawer; you can add one more with side="right" or change this one's side -->
    <q-drawer
      v-model="leftDrawerOpen"
      side="left"
      bordered
      class="bg-grey-2"
    >
      <!-- QScrollArea is optional -->
      <q-scroll-area class="fit q-pa-sm">
        <!-- Content here -->
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <!-- This is where pages get injected -->
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<style lang="scss">
.header-image {
  height: 100%;
  z-index: -1;
  opacity: 0.2;
  filter: grayscale(100%);
}
</style>

<script>
import { ref } from 'vue'
import { date } from 'quasar'

export default {
  // name: 'LayoutName',

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }    
  },
  computed: {
    todaysDate() {
          const timeStamp = Date.now()
          return date.formatDate(timeStamp, 'dddd d YYYY')

    }
  },
}
</script>
