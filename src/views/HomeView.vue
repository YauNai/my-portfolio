<script setup>
import Contact from '@/components/left/Contact.vue';
import LeftMain from '@/components/left/Main.vue';
import Resume from '@/components/left/Resume.vue';
import Folder3D from '@/components/right/Folder3D.vue';
import FolderCoding from '@/components/right/FolderCoding.vue';
import Protfolio from '@/components/right/Protfolio.vue';
import { onMounted, ref } from 'vue';

const sizeW = ref()
const tooBig = ref(true)
const resizeW = () => {
  sizeW.value = window.innerWidth
  sizeW.value > 950 ? tooBig.value = true : tooBig.value = false
}

onMounted(() => {
  sizeW.value = window.innerWidth
  sizeW.value > 950 ? tooBig.value = true : tooBig.value = false
  window.addEventListener('resize', () => {
    resizeW()
  })
})

const showLeft = ref(true)
const showRight = ref(false)
const toggleShowRight = () => {
  showLeft.value = !showLeft.value
  showRight.value = !showRight.value
}

// Left
const showLeftMain = ref(true)
const showResume = ref(false)
const showContact = ref(false)
const fromWhereToResume = ref("fromLeftMain")

const doShowLeftMain = () => {
  showLeftMain.value = true
  showResume.value = false
  showContact.value = false
}

const doShowResume = () => {
  showLeftMain.value = false
  showResume.value = true
  showContact.value = false
}

const doShowContact = () => {
  showLeftMain.value = false
  showResume.value = false
  showContact.value = true
}

const fromLeftMain = () => {
  fromWhereToResume.value = "fromLeftMain"
}
const fromContact = () => {
  fromWhereToResume.value = "fromContact"
}

// Right
const showFolderCoding = ref(false)
const showPortfolio = ref(true)
const showFolder3D = ref(false)

const doShowWorksCoding = () => {
  showFolderCoding.value = true
  showPortfolio.value = false
  showFolder3D.value = false
}

const doShowPortfolio = () => {
  showFolderCoding.value = false
  showPortfolio.value = true
  showFolder3D.value = false
}

const doShowWorks3D = () => {
  showFolderCoding.value = false
  showPortfolio.value = false
  showFolder3D.value = true
}
</script>

<template>
  <div class="grid">
    <div v-if="showLeft || tooBig" class="left">

      <button @click="toggleShowRight" class="my-btn btn-left">切換到作品集</button>

      <LeftMain v-if="showLeftMain" @doShowResume="doShowResume" @fromLeftMain="fromLeftMain" />

      <Resume v-if="showResume" :fromWhereToResume="fromWhereToResume" @doShowLeftMain="doShowLeftMain"
        @doShowContact="doShowContact" />

      <Contact v-if="showContact" @doShowResume="doShowResume" @fromContact="fromContact" />

    </div>
    <div v-if="showRight || tooBig" class="right">

      <button @click="toggleShowRight" class="my-btn portfolio-btn btn-right">切換到履歷</button>

      <FolderCoding v-if="showFolderCoding" @doShowPortfolio="doShowPortfolio" />

      <Protfolio v-if="showPortfolio" @doShowWorksCoding="doShowWorksCoding" @doShowWorks3D="doShowWorks3D" />

      <Folder3D v-if="showFolder3D" @doShowPortfolio="doShowPortfolio" />

    </div>
  </div>
</template>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.left {
  height: 100vh;
  width: 100%;
  background: var(--bg-secondary);
  position: relative;
}

.right {
  height: 100vh;
  width: 100%;
  background: var(--bg);
  position: relative;
}

.my-btn {
  position: absolute;
  z-index: 1;
  top: 25px;
}

.btn-left {
  display: none;
  right: 30px;
}

.btn-right {
  display: none;
  left: 30px;
}

@media screen and (max-width: 950px) {
  .grid {
    grid-template-columns: 1fr;
  }

  .btn-left, .btn-right {
    display: block;
  }
}
</style>