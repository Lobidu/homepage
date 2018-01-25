<template>
  <div class="hero">
    <div class="effect-bar">
      <div class="bar top left green" :style="leftBarStyle">
      </div>
      <div class="bar top right red" :style="rightBarStyle">
      </div>
      <div class="bar middle left green level is-mobile" :style="leftBarStyle">
        <div class="text-container level-right level-item">
          <h1 class="title is-1 is-size-2-mobile">{{text.software}}</h1>
        </div>
      </div>
      <div class="bar middle right red level is-mobile" :style="rightBarStyle">
        <div class="text-container level-left level-item">
          <h1 class="title is-1 is-size-2-mobile">{{text.story}}</h1>
        </div>
      </div>
      <div class="bar bottom left green" :style="leftBarStyle">
      </div>
      <div class="bar bottom right red" :style="rightBarStyle">
      </div>
    </div>
    <div class="hero description">
      <div class="hero-body">
        <div class="container">
          <h1 class="title is-2">{{text.title}}</h1>
          <p>{{text.subtitle}}</p>
        </div>
      </div>
    </div>
    <div class="clearfix"></div>
  </div>
</template>

<script>
    export default {
        name: "puzzle",
      props: {
          viewIndex: String
      },
      data() {
          return {
            text: {
              story: 'Story',
              software: 'Software &',
              title: 'I make the software for your story',
              subtitle: 'I make sure the software plays nicely with your story.'
            },
            scrollY: 0,
            initialOffset: 90,
            lastScrollPosition: 0
          }
      },
      computed: {
        leftBarStyle: function() {
          let difference = (this.initialOffset*-1) + this.distance;
          return 'margin-left: ' + difference + 'vw;'
        },
        rightBarStyle: function() {
          let difference = this.initialOffset - this.distance - 20;
          return 'margin-left: ' + difference + 'vw;'
        },
        distance: function () {
          let effectStartYValue = this.viewIndex * window.innerHeight - window.innerHeight/2;
          let effectPosition = -(effectStartYValue - this.scrollY)/250*30; // The difference to the starting Position as a 250th of 30

          // Prevent all this from happening as long as the element is not in sight
          if (effectStartYValue > this.scrollY) {
            return 0
          }
          else if (effectPosition<=30) {
            return effectPosition;
          }
          else {
            return 30
          }
        }
      },
      methods: {
        handleScroll: function () {
          // Register the scroll value as a component data as to make this.distance reactive
          this.scrollY = window.scrollY;
        }
      },
      created: function() {
        // There is no v-on:scroll event in vue.js so we have to create an event listener.
        window.addEventListener('scroll', this.handleScroll)
      },
      destroyed: function () {
        window.removeEventListener('scroll', this.handleScroll)
      }
    }
</script>

<style scoped>
  .bar {
    height: 10vh;
    width: 100vw;
    position: absolute;
    box-sizing: border-box;
  }
  .middle {
    top: 9.9vh;
    left: 10vh;
    overflow: hidden;
  }
  .bottom {
    top: 19.8vh;
    left: 5vh;
  }
  .text-container {
    padding-left: .5em;
  }
  .middle .text-container h1 {
    color: #ffffff;
  }
  .effect-bar {
    position: relative;
    height: 30vh;
   transform: rotate(-15deg);
  }
  .description {z-index: 9;
   transform: rotate(-15deg);
  }
  .green {
    background-color: #00d1b2;
  }
  .red {
    background-color: #e0ac2e;
  }
  .clearfix {
    height: 40vh;
  }
</style>
