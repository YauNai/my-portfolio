<template>
  <!-- <CodeTyping :fade-out="fadeOut" /> -->
  <section id="folder-coding" class="grid-section">
    <div></div>

    <div class="content">
      <!-- <WorksCoding /> -->
      <AboutDoggoNest />
    </div>

    <div data-aos="fade-down" data-aos-offset="-200" style="text-align: center;">
      <button @click="doToPortfolio" class="my-btn portfolio-btn">所有作品</button>
    </div>
  </section>
</template>

<script setup>
  import { ref } from 'vue';
  import CodeTyping from './CodeTyping.vue';
  import WorksCoding from './WorksCoding.vue';
import AboutDoggoNest from './works/coding/AboutDoggoNest.vue';

  const emit = defineEmits(['doShowPortfolio'])
  const fadeOut = ref(false)

  const doToPortfolio = () => {
    document.querySelector("#folder-coding").classList.add("slid-up");

    fadeOut.value = true

    setTimeout(() => {
      emit('doShowPortfolio')
    }, 750);
  }
</script>

<style scoped></style>