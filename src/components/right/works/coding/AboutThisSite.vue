<template>
  <section ref="this-site" id="this-site" class="grid-about">
    <div data-aos="fade-left">
      <button @click="doToPage('WorksCoding')" class="my-btn portfolio-btn btn-back"><i class="fa-solid fa-arrow-left"></i></button>
    </div>

    <div class="content text-shadow">
      <div data-aos="fade-left" data-aos-delay="100">
        <h2 class="title">作品集網站</h2>
      </div>
      <div data-aos="fade-left" data-aos-delay="200" class="icons">
          <img src="/src/assets/icon/vue_logo.svg" alt="vue logo" class="icon">
          <img src="/src/assets/icon/figma_logo.svg" alt="figma logo" class="icon">
      </div>
      <div data-aos="fade-left" data-aos-delay="300">
        <h3>使用套件：</h3>
        <p>AOS：DOM 過渡動畫</p>
        <p>Three：3D 物件</p>
        <p>TypeIt：打字動畫</p>
      </div>
    </div>
  </section>
</template>

<script setup>
  import { useTemplateRef } from "vue";

  const section = useTemplateRef('this-site')
  const emit = defineEmits(['doShowPage', 'toggleFadeOut'])

  const doToPage = (page) => {
    section.value.classList.add("slid-right");

    emit('toggleFadeOut')

    setTimeout(() => {
      emit('doShowPage', page)
    }, 750);
  }
</script>

<style scoped>
  .content {
    text-align: center;
    justify-items: center;
  }

  .title {
    color: var(--text);
    margin: 0.4em 0;
  }

  .icons {
    display: grid;
    grid-template-columns: 1fr 1fr;
    justify-items: center;
    width: 100px;
    margin: 1.5em 0;
  }
  
  .icon {
    width: 40px;
  }

  .btn-back {
    padding: 0;
    height: 50px;
    width: 50px;
    border-radius: 50%;
  }

  h3 {
    color: var(--text);
    margin-bottom: 0.5em;
    padding: 0;
  }

  p {
    margin: 0;
    margin-bottom: 0.1em;
    padding: 0;
  }
</style>