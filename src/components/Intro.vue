<template>
    <div class="hero is-fullheight is-bold">
      <div class="hero-body">
        <div class="container">
          <h1 class="title is-2">{{text.title}}</h1>
          <p>{{text.message}}</p>
        </div>
      </div>
    </div>
</template>

<script>
    export default {
      name: "intro",
      data () {
          return {
            text: {
              title: 'The story of great software',
              message: 'Every website tells a story. It is like a tale of a different place, of the' +
              ' people there and, again, of their stories. And it keeps telling it over, and over ' +
              'again. So that story should be the best one you can tell. '
            }
          }
      }
    }
</script>

<style scoped>

</style>
