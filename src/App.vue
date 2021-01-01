<template>
    <header-title/>
    <clock/>
    <music-box/>
</template>

<script>

import MusicBox from './components/music_box.vue'
import HeaderTitle from './components/header_title.vue'
import Clock from './components/clock.vue'

export default {
  name:'App',
  components:{
    MusicBox,
    HeaderTitle,
    Clock
  }
}
</script>

<style>

</style>