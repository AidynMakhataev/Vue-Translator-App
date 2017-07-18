<template>
  <div class="text-center" id="app">
    <h1>Переводчик на базе Yandex API</h1>
    <h5>Made by AidynMakhataev</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
export default {
  name: 'app',
  data: function() {
    return {
      translatedText: ''
    }
  },
  components: {
    TranslateForm,
    TranslateOutput
  },
  methods: {
    translateText:function(text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170718T171149Z.e7730f4ba3509bfd.f7989a1c0f066f567375ceb55e4093ede3fce49d&lang='+language+'&text='+text)
       .then( response => {
        this.translatedText = response.body.text[0];
       })
    }
  }
}
</script>

<style>
body {
  background: #fefefe;
}
</style>
