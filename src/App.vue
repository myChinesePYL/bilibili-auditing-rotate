<template>
  <video ref="audio" loop>
    <source src="./mp3.mp3" type="audio/mp3">
  </video>
  <h1 id="text" @mouseup="start">审核</h1>
</template>

<script>
  import screenfull from 'screenfull';
  
  export default {
    data(){return{
      text: ''
    }},
    methods: {
      start(e) {
        let music = this.$refs.audio;
        music.volume = 1;
        music.muted = false;
        music.play();
        e.currentTarget.style.animation = '1.9s r linear infinite';
        document.body.style.animation = '2.1s bt ease-in-out infinite';
        screenfull.request();
      }
    }
  }
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
html {
  font-size: 15px;
  font-family: Arial, Helvetica, Sans-Serif;
}
body {
  display: flex;
  min-height: 100vh;
  align-items: center;
  justify-content: center;
  perspective: 100vmin;
}
#text {
  font-size: 256px;
  transform-style: preserve-3d;
  -webkit-user-select: none;
  user-select: none;
}
@keyframes r {
  0% {
    transform: rotateY(0deg);
    text-shadow: 0px 0px 0px gray;
  }
  25% {
    transform: rotateY(90deg);
    text-shadow: -30px 0px 0px gray;
  }
  50% {
    transform: rotateY(180deg);
    text-shadow: 0px 0px 0px gray;
  }
  75% {
    transform: rotateY(270deg);
    text-shadow: 30px 0px 0px gray;
  }
  100% {
    transform: rotateY(360deg);
    text-shadow: 0px 0px 0px gray
  }
}
@keyframes bt {
  0%,100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(70px);
  }
}
</style>