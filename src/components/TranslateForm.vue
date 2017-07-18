<template>
  <div class="row" id="translateForm">
  	<div class="col-md-6 col-md-offset-3">
	<form id="transForm" class="form-inline well" v-on:submit.prevent="formSubmit">
		<input type="text" class="form-control" v-model="textToTranslate" placeholder="Введите текст ...">
		<select v-model="language" class="form-control">
			<option value="ru">Русский</option>
			<option value="es">Spanish</option>
			<option value="fr">French</option>
			<option value="zh">Chinese</option>
		</select>
		<input type="submit" class="btn btn-primary" value="Перевести">
	</form>
	</div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data () {
  	return {
  		textToTranslate: '',
  		language: ''
  	}
  },
  created() {
  	this.language = 'ru';
  },
  methods: {
  	formSubmit() {
  		this.$emit('formSubmit', this.textToTranslate, this.language);
  	}
  }
}
</script>

<style>
#transForm {
	border-radius: 10px;
	border:1px #ccc solid;
}
</style>
