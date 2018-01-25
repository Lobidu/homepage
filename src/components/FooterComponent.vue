<template>
  <footer class="footer">
    <div class="container">
      <div class="content has-text-centered">
        <p>
          This website was proudly handcrafted using vue.js, bulma and AWS S3. <a href="">View it on github</a>.
        </p>
        <p>&copy; {{new Date().getFullYear()}}</p>
      </div>
    </div>
  </footer>

</template>

<script>
    export default {
        name: "footer-component"
    }
</script>

<style scoped>

</style>
