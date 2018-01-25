<template>
  <div class="hero is-primary is-fullheight is-bold">
    <div class="hero-body">
      <div class="container">
        <h1 class="title is-1">{{text.hello}}</h1>
        <h2 class="subtitle is-3">{{text.welcomemessage}}</h2>
      </div>
    </div>
    <div @click="blink()" class="janis">
      <img v-show="(janisEyeState==='left')" src="../assets/Janis.svg" />
      <img v-show="(janisEyeState==='right')" src="../assets/Janis_looks_right.svg" />
      <img v-show="(janisEyeState==='blink')" src="../assets/Janis_blinks.svg" />
    </div>
  </div>
</template>

<script>
  export default {
    name: 'stage-component',
    data() {
      return {
        text: {
          hello: 'Nice to meet you.',
          welcomemessage: 'I am Janis, a full stack web developer.',
        },
        janisEyeState: 'left',
        janisEyeAnimationInProgress: false
      }
    },
    methods: {
      blink() {
        if(!this.janisEyeAnimationInProgress) { // don't start the animation while it's running.
          this.janisEyeAnimationInProgress = true;

          // There is no proper sleep() function in js, so we fake one with nested setTimeout() functions.
          // I should make it a recursive for loop one day, but this works for now.
          this.janisEyeState = 'right';
          setTimeout(() => {
              this.janisEyeState = 'left';
              setTimeout(() => {
                  this.janisEyeState = 'blink';
                  setTimeout(() => {
                      this.janisEyeState = 'left';
                      this.janisEyeAnimationInProgress = false; // Finished. Reset.
                  }, 100)
              }, 300);
          }, 300);
        }
      }
    }
  }
</script>

<style scoped>
  .janis {
    position: absolute;
    top: 70vh; /* We need to set this to (100vh-img height), instead of bottom: 0, because Webkit subtracts the search bar from the position  */
    right: 5vh;
  }
  .janis img {
    height: 30vh;
    width: 30vh;
    display: block;
  }
</style>
