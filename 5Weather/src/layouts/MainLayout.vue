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

    <!-- (Optional) Footer section below -->

    <!-- (Optional) A Drawer; you can add one more with side="right" or change this one's side -->
    
    
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
