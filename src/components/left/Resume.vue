<template>
  <section id="resume" v-if="fromWhereToResume === 'fromLeftMain'" class="grid-section">
    <div data-aos="fade-up" style="text-align: center;">
      <button @click="doToLeftMain" class="my-btn">首頁</button>
    </div>

    <div class="content text-shadow">

        <div data-aos="fade-up" data-aos-delay="100">
          <h2 class="title">姓名：</h2>
          <h2 class="text">張揚</h2>
        </div>

        <div data-aos="fade-up" data-aos-delay="200">
          <h2 class="title">生日：</h2>
          <h2 class="text">1999 / 02 / 08</h2>
        </div>

        <div data-aos="fade-up" data-aos-delay="300">
          <h2 class="title">學歷：</h2>
          <h3 class="text-muted">2018 - 2021<br>東吳大學 哲學系</h3>
          <h2 class="text">文學士學位</h2>
        </div>

        <div data-aos="fade-up" data-aos-delay="400">
          <h2 class="title">經歷：</h2>
          <h3 class="text-muted">2021 - 2025<br>簡單生活電子商務有限公司</h3>
          <h2 class="text">動畫技術組副組長</h2>
        </div>

        <div data-aos="fade-up" data-aos-delay="500" class="skills">
          <h2 class="title">擅長工具：</h2>
          <div class="skill">

            <div>
              <div class="icon-word">
                <img src="/src/assets/icon/vue_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">VUE</span>
              </div>
              <div class="icon-word">
                <img src="/src/assets/icon/html_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">HTML</span>
              </div>
              <div class="icon-word">
                <img src="/src/assets/icon/css_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">CSS</span>
              </div>
              <div class="icon-word">
                <img src="/src/assets/icon/figma_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">Figma</span>
              </div>
            </div>

            <div>
              <div class="icon-word">
                <img src="/src/assets/icon/Blender_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">Blender</span>
              </div>
              <div class="icon-word">
                <img src="/src/assets/icon/ChatGPT_Logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">ChatGPT</span>
              </div>
              <div class="icon-word">
                <img src="/src/assets/icon/Gemini_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">Gemini</span>
              </div>
              <div class="icon-word">
                <img src="/src/assets/icon/Claude_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">Claude</span>
              </div>
            </div>

          </div>
        </div>

      </div>

    <div data-aos="fade-up" data-aos-delay="600" data-aos-offset="-200" style="text-align: center;">
      <button @click="doToContact" class="my-btn">與我聯繫</button>
    </div>
  </section>

  <section id="resume" v-if="fromWhereToResume === 'fromContact'" class="grid-section">
    <div data-aos="fade-down" data-aos-delay="500" style="text-align: center;">
      <button @click="doToLeftMain" class="my-btn">首頁</button>
    </div>

    <div class="content text-shadow">

        <div data-aos="fade-down" data-aos-delay="500">
          <h2 class="title">姓名：</h2>
          <h2 class="text">張揚</h2>
        </div>

        <div data-aos="fade-down" data-aos-delay="400">
          <h2 class="title">生日：</h2>
          <h2 class="text">1999 / 02 / 08</h2>
        </div>

        <div data-aos="fade-down" data-aos-delay="300">
          <h2 class="title">學歷：</h2>
          <h3 class="text-muted">2018 - 2021<br>東吳大學 哲學系</h3>
          <h2 class="text">文學士學位</h2>
        </div>

        <div data-aos="fade-down" data-aos-delay="200">
          <h2 class="title">經歷：</h2>
          <h3 class="text-muted">2021 - 2025<br>簡單生活電子商務有限公司</h3>
          <h2 class="text">動畫技術組副組長</h2>
        </div>

        <div data-aos="fade-down" data-aos-delay="100" class="skills">
          <h2 class="title">擅長工具：</h2>
          <div class="skill">

            <div>
              <div class="icon-word">
                <img src="/src/assets/icon/vue_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">VUE</span>
              </div>
              <div class="icon-word">
                <img src="/src/assets/icon/html_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">HTML</span>
              </div>
              <div class="icon-word">
                <img src="/src/assets/icon/css_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">CSS</span>
              </div>
              <div class="icon-word">
                <img src="/src/assets/icon/figma_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">Figma</span>
              </div>
            </div>

            <div>
              <div class="icon-word">
                <img src="/src/assets/icon/Blender_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">Blender</span>
              </div>
              <div class="icon-word">
                <img src="/src/assets/icon/ChatGPT_Logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">ChatGPT</span>
              </div>
              <div class="icon-word">
                <img src="/src/assets/icon/Gemini_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">Gemini</span>
              </div>
              <div class="icon-word">
                <img src="/src/assets/icon/Claude_logo.svg" alt="vue logo" class="icon">
                <span class="skill-name">Claude</span>
              </div>
            </div>

          </div>
        </div>

      </div>

    <div data-aos="fade-down" data-aos-offset="-200" style="text-align: center;">
      <button @click="doToContact" class="my-btn">與我聯繫</button>
    </div>
  </section>

</template>

<script setup>
  const props = defineProps({
    fromWhereToResume: {
      type: String,
      required: true
    }
  })

  const emit = defineEmits(['doShowLeftMain', 'doShowContact'])

  const doToLeftMain = () => {
    document.querySelector("#resume").classList.add("slid-down");

    setTimeout(() => {
      emit('doShowLeftMain')
    }, 750);
  }

  const doToContact = () => {
    document.querySelector("#resume").classList.add("slid-up");

    setTimeout(() => {
      emit('doShowContact')
    }, 750);
  }
</script>

<style scoped>
  .content {
    line-height: 0.5;
    display: grid;
    grid-template-rows: 15% 15% 20% 20% 30%;
    align-items: center;
    max-width: 400px;
    margin: 0 auto;
  }

  .title {
    color: var(--secondary);
    font-size: 1.8em;
    margin-bottom: 1em;
  }

  .text {
    color: var(--text);
    font-size: 2em;
    margin-top: -0.3em;
  }

  .text-muted {
    color: var(--text-muted);
    font-size: 1.5em;
    line-height: 1;
    margin-top: -0.6em;
  }

  .skills {
    display: grid;
    grid-template-rows: 20% 80%;
  }

  .skill {
    display: grid;
    grid-template-columns: 1fr 1fr;
    margin-top: 1em;
  }
</style>