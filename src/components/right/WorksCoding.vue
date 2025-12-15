<template>
  <section id="worksCoding" class="grid-section">

    <div></div>

    <div class="content">

      <div data-aos="fade-down" data-aos-delay="200">
        <button class="my-btn portfolio-btn"><a href="./doggo-nest">Doggo Nest</a></button>
      </div>
      <div data-aos="fade-down" data-aos-delay="100">
        <button class="my-btn portfolio-btn">關於此網頁</button>
      </div>
    </div>


    <div data-aos="fade-down" data-aos-offset="-200">
      <button @click="doToPortfolio" class="my-btn portfolio-btn">所有作品</button>
    </div>
  </section>
</template>

<script setup>

  const emit = defineEmits(['doShowPortfolio'])

  const doToPortfolio = () => {
    document.querySelector("#worksCoding").classList.add("slid-up");

    setTimeout(() => {
      emit('doShowPortfolio')
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