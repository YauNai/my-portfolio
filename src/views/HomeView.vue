<script setup>
import Contact from '@/components/left/Contact.vue';
import LeftMain from '@/components/left/Main.vue';
import Resume from '@/components/left/Resume.vue';
import WorksCoding from '@/components/right/WorksCoding.vue';
import Protfolio from '@/components/right/Protfolio.vue';
import Works3D from '@/components/right/Works3D.vue';
import { ref } from 'vue';

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
const showWorksCoding = ref(false)
const showPortfolio = ref(true)
const showWorks3D = ref(false)

const doShowWorksCoding = () => {
  showWorksCoding.value = true
  showPortfolio.value = false
  showWorks3D.value = false
}

const doShowPortfolio = () => {
  showWorksCoding.value = false
  showPortfolio.value = true
  showWorks3D.value = false
}
</script>

<template>
  <div class="grid">
    <div class="left">
      <LeftMain
        v-if="showLeftMain" 
        @doShowResume="doShowResume" 
        @fromLeftMain="fromLeftMain"
      />

      <Resume
        v-if="showResume"
        :fromWhereToResume="fromWhereToResume"
        @doShowLeftMain="doShowLeftMain" 
        @doShowContact="doShowContact" 
      />

      <Contact
        v-if="showContact" 
        @doShowResume="doShowResume"
        @fromContact="fromContact"
      />

    </div>
    <div class="right">
      <WorksCoding
        v-if="showWorksCoding"
        @doShowPortfolio="doShowPortfolio" 
      />

      <Protfolio
        v-if="showPortfolio"
        @doShowWorksCoding="doShowWorksCoding" 
      />

      <Works3D 
        v-if="showWorks3D"
      />
      
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
</style>