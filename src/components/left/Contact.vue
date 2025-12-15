<template>
  <section id="contact" class="grid-section">
    <div data-aos="fade-up" class="text-center" style="text-align: center;">
      <button @click="doToResume" class="my-btn btn-top">履歷</button>
    </div>
    <div class="content text-shadow">
      <div data-aos="fade-up" data-aos-delay="100" style="padding: 0.1em 0;">
        <h2 class="title">姓名：</h2>
        <h2 class="text">張揚</h2>
      </div>

      <div data-aos="fade-up" data-aos-delay="200" style="padding: 0.1em 0;">
        <h2 class="title">電話：</h2>
        <h2 class="text">0975-429-747</h2>
      </div>

      <div data-aos="fade-up" data-aos-delay="300" style="padding: 0.1em 0;">
        <h2 class="title">電子信箱：</h2>
        <h2 class="text">w62796854w@gmail.com</h2>
      </div>
    </div>
  </section>
</template>

<script setup>
  const emit = defineEmits(['doShowResume', 'fromContact'])

  const doToResume = () => {
    document.querySelector("#contact").classList.add("slid-down");

    setTimeout(() => {
      emit('doShowResume')
      emit('fromContact')
    }, 750);
  }
</script>

<style scoped>
  .content {
    line-height: 0.5;
    max-width: 400px;
    margin: 0 auto;
  }

  .title {
    color: var(--secondary);
    font-size: 1.8em;
  }

  .text {
    color: var(--text);
    font-size: 2em;
  }
</style>