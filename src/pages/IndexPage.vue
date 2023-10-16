<template>
  <q-page class="q-ma-lg">
    <div class="row q-pt-xl">
      <q-carousel  style="flex:1" animated v-model="slide" navigation infinite :autoplay="autoplay" arrows
        transition-prev="slide-right" transition-next="slide-left" @mouseenter="autoplay = false"
        @mouseleave="autoplay = true">
        <q-carousel-slide :name="1" img-src="https://cdn.quasar.dev/img/mountains.jpg" />
        <q-carousel-slide :name="2" img-src="https://cdn.quasar.dev/img/parallax1.jpg" />
        <q-carousel-slide :name="3" img-src="https://cdn.quasar.dev/img/parallax2.jpg" />
        <q-carousel-slide :name="4" img-src="https://cdn.quasar.dev/img/quasar.jpg" />
      </q-carousel>
      <div style="flex:1" class="q-pa-lg"> <q-list bordered separator>
        <q-item clickable v-ripple>
          <q-item-section>Single line item</q-item-section>
        </q-item>
  
        <q-item clickable v-ripple>
          <q-item-section>
            <q-item-label>Item with caption</q-item-label>
            <q-item-label caption>Caption</q-item-label>
          </q-item-section>
        </q-item>
  
        <q-item clickable v-ripple>
          <q-item-section>
            <q-item-label overline>OVERLINE</q-item-label>
            <q-item-label>Item with caption</q-item-label>
          </q-item-section>
        </q-item>
      </q-list></div>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
const slide = ref(1);
const autoplay = ref(true);
</script>
<style scoped lang="scss">

</style>
