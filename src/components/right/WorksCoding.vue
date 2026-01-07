<template>
  <section ref="works-coding" id="works-coding" class="grid-section">
    <div></div>

    <div class="content">

      <div data-aos="fade-down" data-aos-delay="200">
        <button @click="doToPage('AboutDoggoNest')" class="my-btn portfolio-btn">Doggo Nest</button>
      </div>

      <div data-aos="fade-down" data-aos-delay="200">
        <button @click="doToPage('AboutUserDashboard')" class="my-btn portfolio-btn">「悅讀」會員頁面</button>
      </div>

      <div data-aos="fade-down" data-aos-delay="100">
        <button @click="doToPage('AboutThisSite')" class="my-btn portfolio-btn">關於此網頁</button>
      </div>

    </div>
  </section>
</template>

<script setup>
  import { useTemplateRef } from 'vue';

  const section = useTemplateRef('works-coding')
  const emit = defineEmits(['toggleFadeOut', 'doShowPage'])

  const doToPage = (page) => {
    section.value.classList.add('slid-left')
    emit('toggleFadeOut')

    setTimeout(() => {
      emit('doShowPage', page)
    }, 750);

  }
</script>

<style scoped>
  .grid-section {
    text-align: center;
  }

  button {
    margin: 0.3em 0;
  }
</style>