<script setup>
import Contact from '@/components/left/Contact.vue';
import LeftMain from '@/components/left/Main.vue';
import Resume from '@/components/left/Resume.vue';
import Folder3D from '@/components/right/Folder3D.vue';
import FolderCoding from '@/components/right/FolderCoding.vue';
import Protfolio from '@/components/right/Protfolio.vue';
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
const showFolderCoding = ref(false)
const showPortfolio = ref(false)
const showFolder3D = ref(true)

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
      <FolderCoding 
        v-if="showFolderCoding"
        @doShowPortfolio="doShowPortfolio" 
      />

      <Protfolio
        v-if="showPortfolio"
        @doShowWorksCoding="doShowWorksCoding" 
        @doShowWorks3D="doShowWorks3D" 
      />

      <Folder3D 
        v-if="showFolder3D"
        @doShowPortfolio="doShowPortfolio"
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