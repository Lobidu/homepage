<template>
  <div class="hero is-light">
    <div class="hero-body">
      <div class="container level">
        <h1 class="title is-1 level-item">{{text.title}}</h1>
      </div>
      <div class="container">
          <!-- This statement makes rows of two tiles, independent of how many tiles exist.-->
          <div class="columns level" v-for="i in (tiles.length/2)" :key="i">
            <!-- The formula [(i-1)*2,(i-1)*2+1] returns an array of the indexes of the two tiles in the current row-->
            <ShowcaseTile
              v-for="j in [(i-1)*2,(i-1)*2+1]"
              v-bind="tiles[j]"
              :key="j"
              class="column"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
  import ShowcaseTile from './ShowcaseTile';
    export default {
      name: "showcase",
      components: {ShowcaseTile},
      data() {
        return {
          text: {
            title: 'This is what I do',
          },
          tiles: [
            {
              color: 'yellow',
              icon: 'fa-code',
              title: 'Front end Development',
              text: 'I try to create fast, maintainable code. I love trying new technologies and languages. So if yours ' +
              'is not included, chances are, I\'d love to try it anyway.',
              skills: [
                {
                  'name': 'HTML/CSS',
                  'percentage': 100
                },
                {
                  'name': 'Javascript',
                  'percentage': 100
                },
                {
                  'name': 'vue.js',
                  'percentage': 90
                },
                {
                  'name': 'React',
                  'percentage': 60
                },
                {
                  'name': 'Angular',
                  'percentage': 50
                }
              ]
            },
            {
              color: 'green',
              icon: 'fa-envelope',
              title: 'Email Development',
              text: 'Email frontend development is completely different from Web frontend. I create awesome mobile-first' +
              ' email templates that work in almost all mail clients. Even Outlook!',
              skills: [
                {
                  'name': 'Email Frontend Design',
                  'percentage': 100
                }
              ]
            },
            {
              color: 'green',
              icon: 'fa-users',
              title: 'User Experience Design',
              text: ''
            },
            {
              color: 'yellow',
              icon: 'fa-mobile-alt',
              title: 'Content Management Systems',
              text: '',
              skills: [
                {
                  'name': 'Drupal',
                  'percentage': 100
                },
                {
                  'name': 'Wordpress',
                  'percentage': 90
                }
              ]
            },
            {
              color: 'yellow',
              icon: 'fa-server',
              title: 'Back end development',
              text: '',
              skills: [
                {
                  'name': 'node.js',
                  'percentage': 100
                },
                {
                  'name': 'Python',
                  'percentage': 100
                },
                {
                  'name': 'php',
                  'percentage': 80
                },
                {
                  'name': 'REST API',
                  'percentage': 80
                },
                {
                  'name': 'NoSQL',
                  'percentage': 75
                },
                {
                  'name': 'SQL',
                  'percentage': 60
                }
              ]
            },
            {
              color: 'green',
              icon: 'fa-chart-bar',
              title: 'Data Analysis & Testing',
              text: 'Everything you think you know about your users - do you really know it or do you assume? ' +
              'Data Analysis and A/B-Tests help you keep track of what your users are doing. I can help you ' +
              'with quick ad-hoc testing and complex automated KPI-Analysis',

            }
          ]
        }
      },
      methods: {
        getTilePosition: function(j) {
          // In two-column layouts the tile should either be left or right aligned. We can get a tiles' position
          // by calculating the remainder of a division by two and using it as the index of the array ['left','right'].
          let positions=['left','right'];
          //return positions[j%2]
        }
      }
    }
</script>

<style scoped>
  .columns {
    max-width: 960px;
    margin: 0 auto;
  }
</style>
