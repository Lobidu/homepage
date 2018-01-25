<template>
    <div class="container tile-container" @click="flipCard">
      <transition name="flip">
      <!-- State if Box is not activated -->
      <div class="box level is-mobile is-radiusless" :class="[color, tilePosition]" v-if="isFrontShown">
        <div class="level-item tile is-child is-parent is-vertical">
          <div class="tile is-child level">
            <div class="level-item">
               <span class="icon is-large">
                <i class="fas fa-3x" :class="icon"></i>
              </span>
            </div>
          </div>
          <div class="tile is-child level">
            <h1 class="title is-4 level-item">{{title}}</h1>
          </div>
        </div>
      </div>
    </transition>
    <transition name="flip">
      <!-- State if Box is activated -->
      <div class="box level is-radiusless" :class="[color, tilePosition]" v-if="isBackShown">
        <div class="level level-item">
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
            isBackShown: false
          }
      },
      methods: {
        flipCard: function() {
          let delay = 400; // A slight bit more than the transition effect itself to avoid both elements existing at the same time
          if(this.isFrontShown){
            this.isFrontShown = !this.isFrontShown;
            setTimeout(() => {this.isBackShown = !this.isBackShown}, delay)
          }
          else{
            this.isBackShown = !this.isBackShown;
            setTimeout(() => {this.isFrontShown = !this.isFrontShown}, delay)
          }
        }
      }
    }
</script>

<style scoped>
  .tile-container {
    padding: 50px;
    perspective: 1000px;
  }
  .box {
    height: 35vw;
    max-height: 400px;
    width: 35vw;
    max-width: 400px;
    margin: 0 auto;
  }
  @media screen and (min-width: 768px) {
    .box.left {
      float:right;
    }
    .box.right {
      float:left;
    }
  }
  @media screen and (max-width: 768px) {
    .box {
      height: 50vw;
      width: 50vw;
    }
  }
  @media screen and (max-width: 620px) {
    .box {
      height: 70vw;
      width: 70vw;
    }
  }
  .box, .box .title {
    color: #ffffff;
  }
  .icon {
    height: 3rem; width:3rem;
  }
  .icon i {
    font-size: 3em;
  }
  .skills {
    margin-top: 20px;
  }
  .skills td {
    padding: 2px;
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
  .flip-enter{
    transform: rotateY(90deg);
  }
  .flip-leave-to {
    transform: rotateY(-90deg);
  }
</style>
