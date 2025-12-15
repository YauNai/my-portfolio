<template>

  <section id="main" class="grid-section">

    <div class="content text-shadow">
      <div data-aos="fade" data-aos-duration="1000">
        <h1 class="glow">
          張揚
        </h1>
      </div>

      <h2 id="title1" class="hide-cursor glow"></h2>

      <div id="title2" data-aos="fade" data-aos-duration="1000">
        <h2 class="glow">3D 動畫師</h2>
      </div>

      <div class="icons">
        <div id="icon1" data-aos="fade" data-aos-duration="1000">
          <img class="icon glow" src="/src/assets/icon/blender_logo.svg" alt="blender logo">
        </div>
        <div id="icon2" data-aos="fade" data-aos-duration="1000">
          <img class="icon glow" src="/src/assets/icon/vue_logo.svg" alt="vue logo">
        </div>
      </div>

    </div>

    <div 
      id="btnResume"  
      data-aos="fade" 
      data-aos-duration="1000" 
      data-aos-offset="-200"
      class="text-center"
    >
      <button @click="doToResume" class="my-btn btn-bottom">履歷</button>
    </div>

  </section>

</template>

<script setup>
  import TypeIt from 'typeit';
  import { nextTick, onMounted } from 'vue';

  const emit = defineEmits(['doShowResume', 'fromLeftMain'])

  const doToResume = () => {
    document.querySelector("#main").classList.add("slid-up");

    setTimeout(() => {
      emit('doShowResume')
      emit('fromLeftMain')
    }, 750);
  }

  onMounted(async () => {

    await nextTick()

    document.querySelector("#title2").classList.remove("aos-animate")
    document.querySelector("#icon1").classList.remove("aos-animate")
    document.querySelector("#icon2").classList.remove("aos-animate")

    const title1Element = document.querySelector("#title1");

    new TypeIt("#title1", {
      cursor: true,
      speed: 100,
      startDelay: 1000,
      afterComplete: function (instance) {
        instance.destroy()
      }
    })
      .exec(() => {
        title1Element.classList.remove("hide-cursor");
      })
      .type("前端網頁設計師")
      .pause(500)
      .exec(() => {
        document.querySelector("#title2").classList.add("aos-animate")
      })
      .pause(500)
      .exec(() => {
        document.querySelector("#icon1").classList.add("aos-animate")
      })
      .pause(500)
      .exec(() => {
        document.querySelector("#icon2").classList.add("aos-animate")
      })
      .pause(2000)
      .go()
  }) 
</script>

<style scoped>
  .grid-section {
    text-align: center;
  }

  .content {
    grid-row: 2;
    line-height: 0.5;
  }

  #btnResume {
    grid-row: 3;
  }

  .hide-cursor :deep(.ti-cursor) {
    display: none;
  }

  .icons {
    display: flex;
    justify-content: center;
    gap: 20px;
  }

  .icon {
    height: 30px;
  }
</style>