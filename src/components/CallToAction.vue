<template>
    <div>
      <section class="hero is-primary is-fullheight">
        <div class="hero-body">
          <div class="container">
            <div class="container level is-mobile">
              <h1 class="title is-1 level-item">{{text.title}}</h1>
            </div>
            <div class="container level is-mobile">
              <form class="level-item">
                <div class="field is-horizontal has-addons">
                    <label for="need" class="field-label is-large">{{text.inputlabel}}</label>
                  <div class="control">
                    <input type="text"
                           id="need"
                           class="field-body input is-large"
                           :placeholder="text.placeholder[inputPlaceholderIndex]"
                           v-model="inputValue"
                    >
                  </div>
                  <div class="control">
                    <a class="button is-info is-large" :href="mailLink">{{text.cta}}</a>
                  </div>
                </div>
              </form>
            </div>
          </div>
        </div>
      </section>
    </div>
</template>

<script>
    export default {
        name: "call-to-action",
      data() {
          return {
            text: {
              title: 'What is your story?',
              inputlabel: 'I need',
              cta: 'Go!',
              placeholder: [
                'a Website',
                'an API',
                'an Email-Template',
                'an Alexa-Skill',
                'an Idea'
              ]
            },
            inputPlaceholderIndex: 0,
            inputValue: ''
          }
      },
      computed: {
          mailLink: function () {
            let linkhead = 'mailto:janisaltherr@gmail.com';
            let subject = 'I need ' + this.inputValue + '!';
            let mailBody = 'Hey Janis!\nI could need some help with ' + this.inputValue + '!\n Can you do this?'
            return linkhead + '?subject=' + encodeURI(subject) + '&body=' + encodeURI(mailBody)
          }
      },
      methods: {
        updateInputPlaceholder: function () {
          if(this.text.placeholder.length-1 > this.inputPlaceholderIndex){
            this.inputPlaceholderIndex += 1;
          }
          else {
            this.inputPlaceholderIndex = 0;
          }
          setTimeout(()=>{this.updateInputPlaceholder()}, 1500) // Never stop.
        }
      },
      created: function() {
          this.updateInputPlaceholder()
      }
    }
</script>

<style scoped>

</style>
