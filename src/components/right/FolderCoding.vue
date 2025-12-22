<template>
  <CodeTyping v-if="currPage === 'WorksCoding'" :fade-out="fadeOut" />
  <section ref="folder-coding" id="folder-coding" class="grid-section">
    <div></div>

    <div class="content">

      <WorksCoding v-if="currPage === 'WorksCoding'" @doShowPage="doShowPage" @toggleFadeOut="toggleFadeOut" />

      <AboutDoggoNest v-if="currPage === 'AboutDoggoNest'" @doShowPage="doShowPage" @toggleFadeOut="toggleFadeOut" />

      <AboutThisSite v-if="currPage === 'AboutThisSite'" @doShowPage="doShowPage" @toggleFadeOut="toggleFadeOut" />

    </div>

    <div data-aos="fade-down" data-aos-offset="-200" style="text-align: center;">
      <button @click="doToPortfolio" class="my-btn portfolio-btn">所有作品</button>
    </div>
  </section>
</template>

<script setup>
  import { ref, useTemplateRef } from 'vue';
  import CodeTyping from './CodeTyping.vue';
  import WorksCoding from './WorksCoding.vue';
  import AboutDoggoNest from './works/coding/AboutDoggoNest.vue';
  import AboutThisSite from './works/coding/AboutThisSite.vue';

  const currPage = ref('WorksCoding')

  const doShowPage = (page) => {
    currPage.value = page
  }

  const section = useTemplateRef('folder-coding')
  const emit = defineEmits(['doShowPortfolio'])
  const fadeOut = ref(false)

  const toggleFadeOut = () => {
    fadeOut.value = !fadeOut.value
  }

  const doToPortfolio = () => {
    section.value.classList.add("slid-up");

    toggleFadeOut()

    setTimeout(() => {
      emit('doShowPortfolio')
    }, 750);
  }

</script>

<style scoped></style>