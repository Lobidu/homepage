<template>
    <div>
      <section class="hero is-primary is-fullheight">
        <div class="hero-body">
          <div class="container">
            <div class="container level">
              <h1 class="title is-1 level-item has-text-centered">{{text.title}}</h1>
            </div>
            <div class="level">
              <form class="level-item is-horizontal">
                  <div class="field-body">
                    <div class="field-label is-large">
                      <label for="need" class="label">{{text.inputlabel}}</label>
                    </div>
                    <div class="field">
                      <div class="control">
                          <input type="text"
                               id="need"
                               class="input is-fullwidth is-large"
                               :placeholder="text.placeholder[inputPlaceholderIndex]"
                               v-model="inputValue"
                          >
                      </div>
                    </div>
                    <div class="field-label">
                      <a class="button is-info is-large is-pulled-left" :href="mailLink">{{text.cta}}</a>
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
        name: "call-to-action-component",
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
              if(this.inputValue) {
                  let linkhead = 'mailto:janisaltherr@gmail.com';
                  let subject = 'I need ' + this.inputValue + '!';
                  let mailBody = 'Hey Janis!\nI could need some help with ' + this.inputValue + '!\n Can you do this?'
                  return linkhead + '?subject=' + encodeURI(subject) + '&body=' + encodeURI(mailBody)
              }
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
  .label {
    color: #ffffff
  }
</style>
