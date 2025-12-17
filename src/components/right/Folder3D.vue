<template>
  <section id="folder-3d" class="grid-section">
    <iframe data-aos="fade" id="bg" src="src/components/right/Blender.html">
    </iframe>

    <div data-aos="fade-up" style="text-align: center;">
      <button @click="doToPortfolio" class="my-btn portfolio-btn">所有作品</button>
    </div>

    <div class="content">
      <Works3D />
    </div>

    <div></div>
  </section>
</template>

<script setup>
  import Works3D from './Works3D.vue';

  const emit = defineEmits(['doShowPortfolio'])

  const doToPortfolio = () => {
    console.log("click")


    document.querySelector("#bg").classList.add("fade-out");

    document.querySelector("#folder-3d").classList.add("slid-down");

    setTimeout(() => {
      console.log("emit")
      emit('doShowPortfolio')
    }, 750);
  }

</script>

<style scoped>
  .content {
    position: relative;
    z-index: 1;
  }

  #bg {
    position: fixed;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
    z-index: -1;
    border: none;
    pointer-events: none;
  }
</style>