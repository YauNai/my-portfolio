<template>
  <section id="works-coding" class="grid-section">
    <div></div>

    <div class="content">

      <div data-aos="fade-down" data-aos-delay="200">
        <button @click="doToAboutDoggoNest" class="my-btn portfolio-btn">Doggo Nest</button>
      </div>

      <div data-aos="fade-down" data-aos-delay="100">
        <button class="my-btn portfolio-btn">關於此網頁</button>
      </div>

    </div>
  </section>
</template>

<script setup>
  const emit = defineEmits(['doShowAboutDoggoNest', 'toggleFadeOut'])

  const doToAboutDoggoNest = () => {
    document.querySelector("#works-coding").classList.add("slid-left");

    emit('toggleFadeOut')

    setTimeout(() => {
      emit('doShowAboutDoggoNest')
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