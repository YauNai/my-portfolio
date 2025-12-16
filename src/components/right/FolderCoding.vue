<template>
  <CodeTyping v-if="showCodeTyping" :fade-out="fadeOut" />
  <section id="folder-coding" class="grid-section">
    <div></div>

    <div class="content">

      <WorksCoding 
        v-if="showWorksCoding"
        @toggleFadeOut="toggleFadeOut" 
        @doShowAboutDoggoNest="doShowAboutDoggoNest"
      />

      <AboutDoggoNest 
        v-if="showAboutDoggoNest"
        @toggleFadeOut="toggleFadeOut"
        @doShowWorksCoding="doShowWorksCoding" 
      />

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

  const showCodeTyping = ref(true)
  const showWorksCoding = ref(true)
  const showAboutDoggoNest = ref(false)

  const emit = defineEmits(['doShowPortfolio'])
  const fadeOut = ref(false)

  const toggleFadeOut = () => {
    fadeOut.value = !fadeOut.value
  }

  const doToPortfolio = () => {
    document.querySelector("#folder-coding").classList.add("slid-up");

    toggleFadeOut()

    setTimeout(() => {
      emit('doShowPortfolio')
    }, 750);
  }

  const doShowAboutDoggoNest = () => {
    showCodeTyping.value = false
    showWorksCoding.value = false
    showAboutDoggoNest.value = true
  }

  const doShowWorksCoding = () => {
    showCodeTyping.value = true
    showWorksCoding.value = true
    showAboutDoggoNest.value = false
  }
</script>

<style scoped></style>