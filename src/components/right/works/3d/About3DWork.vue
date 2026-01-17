<template>
  <section ref="section" class="grid-about">

    <div data-aos="fade-left">
      <button @click="doToPage('Works3D')" class="my-btn portfolio-btn btn-back"><i
          class="fa-solid fa-arrow-left"></i></button>
    </div>

    <div class="content text-shadow">
      <div data-aos="fade-left" data-aos-delay="100">
        <h3 class="sub-title">{{ subtitle }}</h3>
      </div>
      <div data-aos="fade-left" data-aos-delay="200">
        <h2 class="title">{{ title }}</h2>
      </div>
      <div data-aos="fade-left" data-aos-delay="300" class="icons">
        <img :src="iconBlender" alt="blender logo" class="icon">
      </div>
      <div data-aos="fade-left" data-aos-delay="400" class="links">
        <button class="my-btn portfolio-btn"><a href="https://user-dashboard-1p36.onrender.com/" target="_blank">觀看</a>
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
  import iconBlender from '@/assets/icon/Blender_logo.svg'
  import { useTemplateRef } from 'vue';

  const props = defineProps(['subtitle', 'title'])
  const section = useTemplateRef('section')
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
  .content {
    position: absolute;
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
    grid-template-columns: 1fr;
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

  .links {
    display: flex;
    flex-direction: column;
    gap: 1em;
  }
</style>