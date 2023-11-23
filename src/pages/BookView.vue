<template>
  <div>
    <vue-pdf-embed
      ref="pdfRef"
      :source="`/files/${route.params.id}.pdf`"
      :page="page"
    />
  </div>
</template>

<script setup>
import { ref,watch } from 'vue';
import VuePdfEmbed from 'vue-pdf-embed'
import {useRoute} from 'vue-router'
const route=useRoute();
const isLoading=ref(true);
const page= ref(null);
const pageCount= ref(1);
const showAllPages= ref(true);
watch(showAllPages, () => {
  page.value = showAllPages.value ? null : 1;
});
</script>


<style lang="scss" scoped>

</style>
