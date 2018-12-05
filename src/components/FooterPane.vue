<template lang="html">
<div>
  <div class="w-full relative bg-indigo cta">
    <div class="container mx-auto py-32 px-4">
      <div class="flex items-center flex-col md:flex-row">
        <div>
          <img class="mb-2" src="../assets/speedo-icon.svg">
          <p class="title text-yellow">Build robust FaaS implemntations</p>
          <h3 class="header text-white">datahook.io</h3>
        </div>
        <div class="md:ml-32">
        </div>
      </div>
    </div>
  </div>
  <div class="w-full relative bg-grey-lighter">
    <div class="container mx-auto pt-8 px-4">
      <div class="flex items-center justify-around flex-col md:flex-row">
      <img src="../assets/datahook.io---Social-Media---5.png" alt="datahook.io logo" class="h-80">
      </div> 
    </div>
    <div class="px-4">
      <div class="container mx-auto pt-4 pb-6 items-center flex">
<!--        <img src="../assets/datahook.io---Social-Media---5.png" alt="datahook.io logo" class="h-10"> -->
        <span class="uppercase text-grey-dark pt-2 pl-4">All rights reserved 2018</span>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import Rellax from 'rellax'

export default {
  mounted () {
    if (this.$el.clientWidth > 768) {
      Rellax('.rellax', {
        vertical: true,
        center: true
      })
    }
  }
}
</script>

<style lang="sass">
.cta
  background-image: linear-gradient(155deg, #6883f5 0%, #495fb9 80%)
</style>
