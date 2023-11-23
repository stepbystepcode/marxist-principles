<template>
  <q-page>
    <div class="row q-ma-lg q-pt-xl">
      <q-carousel style="flex:1;height:auto;aspect-ratio: 16/9;" animated v-model="slide" navigation infinite
        :autoplay="autoplay" arrows transition-prev="slide-right" transition-next="slide-left"
        @mouseenter="autoplay = false" @mouseleave="autoplay = true">
        <q-carousel-slide :name="1" img-src="/banner/1.jpg" />
        <q-carousel-slide :name="2" img-src="/banner/2.jpg" />
        <q-carousel-slide :name="3" img-src="/banner/3.jpg" />
        <q-carousel-slide :name="4" img-src="/banner/4.jpg" />
      </q-carousel>
      <div style="flex:1" class="q-px-lg"> <q-list bordered separator>
          <q-item>
            <q-item-section>
              精选文章
            </q-item-section>
          </q-item>

          <q-item clickable v-ripple>
            <q-item-section>

            </q-item-section>
          </q-item>

          <q-item clickable v-ripple>
            <q-item-section>

            </q-item-section>
          </q-item>

          <q-item clickable v-ripple>
            <q-item-section>

            </q-item-section>
          </q-item>
        </q-list></div>
    </div>
    <div class="column q-pt-md bg flex-center">
      <h5 style="font-family: 'Noto Serif SC', serif;">学术著作</h5>
      <div class="flex-center row q-mx-xl q-gutter-lg">
      <div v-for="i in 10" :key="i" class="book">
        <img :src="`/books/${i}.jpg`" alt="">
      </div>
    </div>
    </div>
    <q-img src="/files/map.png"></q-img>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
const slide = ref(1);
const autoplay = ref(true);
</script>
<style scoped lang="scss">
.bg {
  background-color: #d6d6d6b0;
}

.book {
  img {
    width: 7rem;
    aspect-ratio: 9/14;
    border:1px solid black;
    box-shadow: 6px 9px 4px rgba(0, 0, 0, 0.24);
    transition: All 0.4s ease-in-out;
    margin-top: 0;
    &:hover{
      transform: translate(0,-10px);

    }
  }
}
</style>
