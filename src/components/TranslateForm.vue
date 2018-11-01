<template>
  <div id="translateForm" class="container">
      <div class="row">
        <div class="col-md-6 offset-md-3 text-center">
            <form id="submitForm" class="form-inline" v-on:submit="formSubmit">
                <input type="text" class="form-control" v-model="textToTranslate" placeholder="Enter a word....">
                <select v-model="language" class="form-control">
                    <option value="ru">Russian</option>
                    <option value="es">Spanish</option>
                    <option value="fr">French</option>
                    <option value="bn">Bengali</option>
                </select>
                <input type="submit" class="btn btn-primary" value="Translate">
            </form>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data() {
      return{
          textToTranslate: '',
          language: ''
      }
  },
  created(){
      this.language = 'bn'
  },
  methods : {
      formSubmit(e){
          e.preventDefault();
          this.$emit('formSubmit', this.textToTranslate, this.language);
      }
  }
}
</script>

<style>
    #submitForm{
        justify-content: center;
        padding: 30px 0;
        margin: 20px 0;
        box-shadow: rgba(0, 0, 0, 0.05) 0px 10px 20px, rgba(0, 0, 0, 0.2) 0px 0px 1px;
        border-radius: 4px;
        background: rgb(255, 255, 255);
    }
</style>
