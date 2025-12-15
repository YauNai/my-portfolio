<template>
  <section id="doggo-nest" class="grid-about">
    <div>
      <button class="my-btn portfolio-btn btn-back"><i class="fa-solid fa-arrow-left"></i></button>
    </div>

    <div class="content">
      <div>
        <h3 class="sub-title">單頁式應用程式<br>Single-Page Application</h3>
      </div>
      <div>
        <h2 class="title">Doggo Nest｜狗狗窩研究所</h2>
      </div>
      <div class="icons">
          <img src="/src/assets/icon/vue_logo.svg" alt="vue logo" class="icon">
          <img src="/src/assets/icon/figma_logo.svg" alt="vue logo" class="icon">
          <img src="/src/assets/icon/ChatGPT_Logo.svg" alt="vue logo" class="icon">
          <img src="/src/assets/icon/Gemini_logo.svg" alt="vue logo" class="icon">
          <img src="/src/assets/icon/Claude_logo.svg" alt="vue logo" class="icon">
      </div>
      <div>
        <button class="my-btn portfolio-btn"><a href="./doggo-nest">進入網頁</a></button>
      </div>
    </div>
  </section>
</template>

<script setup>

</script>

<style scoped>
  .content {
    text-align: center;
    justify-items: center;
  }

  .sub-title {
    color: var(--secondary);
    font-size: 1.5em;
  }

  .title {
    color: var(--text);
  }

  .icons {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    justify-items: center;
    width: 80%;
    padding: 1em 0;
  }
  
  .icon {
    width: 50px;
  }

  .btn-back {
    padding: 0;
    height: 50px;
    width: 50px;
    border-radius: 50%;
  }
</style>