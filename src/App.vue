<template>
  <div id="app">
    <router-view/>
    <FooterC/>
  </div>
</template>

<script>
import FooterC from '@/components/FooterC.vue'
export default {
  components:{
    FooterC
  }
}
</script>