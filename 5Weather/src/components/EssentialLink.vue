<template>
  <q-item
    clickable
    tag="a"
    target="_blank"
    :href="link"
  >
    <q-item-section
      v-if="icon"
      avatar
    >
      <q-icon :name="icon" />
    </q-item-section>

    <q-item-section>
      <q-item-label>{{ title }}</q-item-label>
      <q-item-label caption>
        {{ description }}
      </q-item-label>
    </q-item-section>
  </q-item>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'EssentialLink',
  props: {
    title: {
      type: String,
      required: true
    },

    caption: {
      type: String,
      default: ''
    },

    description: {
      type: String,
      default: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean varius turpis sed sem luctus, a blandit tortor aliquam. Praesent euismod leo risus, sed eleifend dolor faucibus quis. Maecenas feugiat dictum leo, sit amet feugiat orci pulvinar eu. Nullam tincidunt arcu id fringilla vulputate. Quisque porta elit id pretium efficitur. Integer odio magna, luctus ac sodales in, dictum ut augue. Pellentesque mattis enim dui, non aliquet turpis fermentum quis.'
    },

    link: {
      type: String,
      default: '#'
    },

    icon: {
      type: String,
      default: ''
    }
  }
})
</script>
