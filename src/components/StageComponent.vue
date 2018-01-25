<template>
  <div class="hero is-primary is-fullheight is-bold">
    <div class="hero-body">
      <div class="container">
        <h1 class="title is-1">{{text.hello}}</h1>
        <h2 class="subtitle is-3">{{text.welcomemessage}}</h2>
      </div>
      <div @click="blink()" class="janis">
        <img v-show="(janisEyeState==='left')" src="../assets/Janis.svg" />
        <img v-show="(janisEyeState==='right')" src="../assets/Janis_looks_right.svg" />
        <img v-show="(janisEyeState==='blink')" src="../assets/Janis_blinks.svg" />
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'StageComponent',
    data() {
      return {
        text: {
          hello: 'Nice to meet you.',
          welcomemessage: 'I am Janis, a full stack web developer.',
        },
        janisEyeState: 'left'
      }
    },
    methods: {
      blink() {
        this.janisEyeState = 'right';
        setTimeout(()=>{
          this.janisEyeState = 'left';
          setTimeout(()=>{
            this.janisEyeState = 'blink';
            setTimeout(()=>{this.janisEyeState = 'left'},100)
          },300);
        },300);
      }
    }
  }
</script>

<style scoped>
  .hero {
    padding: 0;
  }
  .janis {
    position: absolute;
    bottom: 0px;
    right: 5vh;
  }
  .janis img {
    height: 30vh;
    width: 30vh;
    display: block;
  }
  .hidden {
    display:none;
  }
</style>
