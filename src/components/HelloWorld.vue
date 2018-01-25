<template>
  <div>
    <stage-component/>
    <intro/>
    <puzzle viewIndex="2"/>
    <showcase/>
    <call-to-action />
    <footer-component />
  </div>
</template>

<script>
  import StageComponent from './StageComponent';
  import Intro from './Intro';
  import Puzzle from './Puzzle';
  import Showcase from './Showcase';
  import CallToAction from './CallToAction';
  import FooterComponent from './FooterComponent';

  export default {
  components: {StageComponent, Intro, Puzzle, Showcase, CallToAction, FooterComponent}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
