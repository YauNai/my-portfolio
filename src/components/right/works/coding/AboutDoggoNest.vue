<template>
  <section ref="doggo-nest" id="doggo-nest" class="grid-about">

    <div data-aos="fade" class="bg">
      <img :src="bgDoggoNest" alt="bgDoggoNest">
    </div>

    <div data-aos="fade-left">
      <button @click="doToPage('WorksCoding')" class="my-btn portfolio-btn btn-back"><i class="fa-solid fa-arrow-left"></i></button>
    </div>

    <div class="content text-shadow">
      <div data-aos="fade-left" data-aos-delay="100">
        <h3 class="sub-title">單頁式應用程式<br>Single-Page Application</h3>
      </div>
      <div data-aos="fade-left" data-aos-delay="200">
        <h2 class="title">狗狗窩研究所</h2>
      </div>
      <div data-aos="fade-left" data-aos-delay="300" class="icons">
          <img src="/src/assets/icon/vue_logo.svg" alt="vue logo" class="icon">
          <img src="/src/assets/icon/figma_logo.svg" alt="vue logo" class="icon">
          <img src="/src/assets/icon/ChatGPT_Logo.svg" alt="vue logo" class="icon">
          <img src="/src/assets/icon/Gemini_logo.svg" alt="vue logo" class="icon">
          <img src="/src/assets/icon/Claude_logo.svg" alt="vue logo" class="icon">
      </div>
      <div data-aos="fade-left" data-aos-delay="400">
        <button class="my-btn portfolio-btn"><a href="./doggo-nest-offline" target="_blank">進入網頁</a></button>
      </div>
    </div>
  </section>
</template>

<script setup>
  import bgDoggoNest from "@/assets/image/bg_doggonest.jpeg"
  import { useTemplateRef } from 'vue';

  const section = useTemplateRef('doggo-nest')
  const emit = defineEmits(['toggleFadeOut', 'doShowPage'])

  const doToPage = (page) => {
    section.value.classList.add('slid-right')
    emit('toggleFadeOut')

    setTimeout(() => {
      emit('doShowPage', page)
    }, 750);

  }
</script>

<style scoped>
  .bg {
    z-index: -1;
    position: absolute;
    height: 100%;
    width: 100%;
    transition: opacity 0.3s ease;
    overflow: hidden;
  }

  .bg img {
    z-index: 1;
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center top;

    animation-name: bg-slid-up;
    animation-duration: 60s;
    animation-iteration-count: infinite;
    animation-timing-function: ease;
  }

  .bg::before {
    z-index: 2;
    content: "";
    top: 0;
    left: 0;
    background-color: var(--bg);
    position: absolute;
    height: 100%;
    width: 100%;
    opacity: 0.9;
  }

  @keyframes bg-slid-up {
    0% {
      object-position: center top;
      opacity: 0;
    }
    5% {
      opacity: 1;
    }
    95% {
      opacity: 1;
    }
    100% {
      object-position: center bottom;
      opacity: 0;
    }
  }

  .content {
    text-align: center;
    justify-items: center;
  }

  .sub-title {
    color: var(--secondary);
    font-size: 1.5em;
    margin: 0.1em 0;
  }

  .title {
    color: var(--text);
    margin: 0.4em 0;
  }

  .icons {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    justify-items: center;
    width: 250px;
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
</style>