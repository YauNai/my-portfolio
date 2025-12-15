<template>
  <section id="portfolio" class="grid-section">

    <div></div>

    <div class="content">
      <div data-aos="fade" data-aos-duration="1000" data-aos-delay="500">
        <button @click="doToWorksCoding" class="my-btn portfolio-btn">網頁設計作品</button>
      </div>
      <div data-aos="fade" data-aos-duration="1000" data-aos-delay="1000">
        <button class="my-btn portfolio-btn">3D 動畫作品</button>
      </div>
    </div>
  </section>
</template>

<script setup>
  import { ref } from 'vue';

  const showCodeTyping = ref(false)

  const emit = defineEmits(['doShowWorksCoding', 'doShowWorks3D'])

  const doToWorksCoding = () => {
    document.querySelector("#portfolio").classList.add("slid-down");

    setTimeout(() => {
      emit('doShowWorksCoding')
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