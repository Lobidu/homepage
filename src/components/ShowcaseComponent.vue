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
      name: "showcase-component",
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
              title: 'Front end development',
              text: 'I love trying new technologies and languages. If yours ' +
              'is not included, chances are, I\'d love to learn it anyway.',
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
              icon: 'fa-server',
              title: 'Back end development',
              text: 'I always try to write fast, secure and maintainable code. I use open source solutions ' +
              'to ensure easy maintenance.',
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
                      'name': 'NoSQL / SQL',
                      'percentage': 60
                  }
                ]
            },
            {
              color: 'green',
              icon: 'fa-envelope',
              title: 'Email development',
              text: 'Email frontend development is completely different from web frontend. I create awesome mobile-first' +
              ' email templates that work in almost all mail clients. Even Outlook!',
              skills: [
                {
                  'name': 'Email Frontend Design',
                  'percentage': 100
                }
              ]
            },
            {
              color: 'yellow',
              icon: 'fa-chart-bar',
              title: 'Data Analysis & Testing',
              text: 'Everything you think you know about your users - do you really know it or do you assume? ' +
              'Data Analysis and A/B-Tests help you keep track of what your users are doing. I can help you ' +
              'with quick ad-hoc testing and automated KPI-Analysis',

            },
            {
              color: 'yellow',
              icon: 'fa-users',
              title: 'User Experience Design',
              text: 'I develop my software constantly with the user in mind. I have a degree in Communications and ' +
              'years of experience in storytelling. It\'s something that comes with it.'
            },
            {
              color: 'green',
              icon: 'fa-mobile-alt',
              title: 'Content Management Systems',
              text: 'CMS are probably the easiest quick-start into the web. I have set up countless Drupal ' +
              'and Wordpress instances (and a few other CMS, too) so I know exactly how to tune them to your needs.',
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
          ]
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
