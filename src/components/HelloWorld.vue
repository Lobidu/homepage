<template>
  <div>
    <stage-component/>
    <intro-component/>
    <puzzle-component viewIndex="2"/>
    <showcase-component/>
    <call-to-action-component />
    <footer-component />
  </div>
</template>

<script>
  import StageComponent from './StageComponent';
  import IntroComponent from './IntroComponent';
  import PuzzleComponent from './PuzzleComponent';
  import ShowcaseComponent from './ShowcaseComponent';
  import CallToActionComponent from './CallToActionComponent';
  import FooterComponent from './FooterComponent';

  export default {
  components: {StageComponent, IntroComponent, PuzzleComponent, ShowcaseComponent, CallToActionComponent, FooterComponent}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
