<template>
  <div>
    <div class="tile-container" @click="flipCard">
      <transition name="flip">
      <!-- State if Box is not activated -->
      <div class="box is-mobile is-radiusless level" :class="color" v-show="isFrontShown">
        <div class="level-item is-block is-marginless">
          <div class="level is-mobile">
            <div class="level-item is-marginless">
               <span class="icon is-large">
                <i class="fas fa-3x" :class="icon"></i>
              </span>
            </div>
          </div>
          <div class="level is-mobile">
            <div class="level-item has-text-centered is-marginless">
              <h1 class="title is-4">{{title}}</h1>
            </div>
          </div>
        </div>
      </div>
    </transition>
    <transition name="flip">
      <!-- State if Box is activated -->
      <div class="box level is-mobile is-radiusless" :class="color" v-show="isBackShown">
        <div class="level-item">
          <div>
            <div class="is-text has-text-centered">{{text}}</div>
            <div v-if="skills" class="level">
              <table class="level-item skills" >
                <tbody>
                <tr v-for="skill in skills">
                  <td>
                    {{skill.name}}
                  </td>
                  <td>
                      <span v-for="i in [1,2,3,4,5]">
                        <span v-if="i<=(skill.percentage/100*5)">&#9679;</span>
                        <span v-else>&#9675;</span>
                      </span>
                  </td>
                </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </transition>
  </div>
  </div>
</template>

<script>
    export default {
      name: "showcase-tile",
      props: {
        tilePosition: String,
        icon: String,
        title: String,
        text: String,
        skills: Array,
        color: String
      },
      data() {
          return {
            isFrontShown: true,
            isBackShown: false,
            isEffectActive: false
          }
      },
      methods: {
        flipCard: function() {
          if (!this.isEffectActive) { // Prevent this effect from being executed again while its still in transition
            this.isEffectActive = true;
            let delay = 350;
            if(this.isFrontShown){
              this.isFrontShown = !this.isFrontShown;
              setTimeout(() => {
                this.isBackShown = !this.isBackShown;
                this.isEffectActive = false;
              }, delay)
            }
            else{
              this.isBackShown = !this.isBackShown;
              setTimeout(() => {
                this.isFrontShown = !this.isFrontShown;
                this.isEffectActive = false;
              }, delay)
            }
          }
        }
      }
    }
</script>

<style scoped>

  /* scoped layout adjustments */
  .tile-container {
    height: 40vw;
    width: 40vw;
    max-height: 450px;
    max-width: 450px;
    perspective: 1000px;
  }
  .box {
    position: absolute;
    top: 30px;
    left: 30px;
    right: 30px;
    bottom: 30px;
    margin: 0;
  }
  .skills {
    margin-top: 20px;
  }
  .skills td {
    padding: 2px;
  }

  /* Screen size dependent special treatments */
  @media screen and (min-width: 768px) {
    /* For two-column layout */
    .left {
      float:right;
    }
    .right {
      float:left;
    }
  }
  @media screen and (max-width: 768px) {
    .tile-container {
      height: 50vw;
      width: 50vw;
      margin: 0 auto;
    }
    .box {
      top: 20px;
      left: 20px;
      right: 20px;
      bottom: 20px;
    }
  }
  @media screen and (max-width: 620px) {
    .tile-container {
      height: 70vw;
      width: 70vw;
    }
    .box {
      top: 10px;
      left: 10px;
      right: 10px;
      bottom: 10px;
    }
  }

  /* Font Adjustments */
  .box, .box .title {
    color: #ffffff;
  }
  .icon {
    height: 3rem; width:3rem;
  }
  .icon i {
    font-size: 3em;
  }

  /* Box background colors */
  .box.green {
    background-color: #00d1b2;
  }
  .box.green:hover {
    background-color: #10e1c2;
  }
  .box.yellow {
    background-color: #e0ac2e;
  }
  .box.yellow:hover {
    background-color: #f0bc3e;
  }

  /* Transition effects */
  .flip-enter-active {
    transition: ease-out 350ms;
    transform-style: preserve-3d;
    -webkit-transform-style: preserve-3d;
  }
  .flip-leave-active {
    transition: ease-in 350ms;
    transform-style: preserve-3d;
    -webkit-transform-style: preserve-3d;
  }
  .flip-enter {
    transform: rotateY(90deg);
  }
  .flip-leave-to {
    transform: rotateY(-90deg);
  }
</style>
