<template>
  <div class="text-center" id="app">
    <h1>Word Translator</h1>
    <h5>Powered by Vue Js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput :text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function() {
    return {
      translatedText: ''
    }
  },
  methods : {
    translateText: function(text, lang){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181028T062325Z.57d020a3e1d74c21.b46a5d245e161a446e566fe7e04d35f2d64b0580&lang='+lang+'&text='+text)
      .then((response)=>{
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
  body{
    background-color: #fefefe;
  }
  #app{
    margin-top: 100px;
  }
</style>
