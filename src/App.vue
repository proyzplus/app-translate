<template>
  <div id="app">
  	<h1>在线翻译</h1>
  	<h5>简单   / 快捷   / 简约</h5>
   <translateForm v-on:formSubmit="translateTest"></translateForm>
   <translateOut v-text="tranlated"></translateOut>
  </div>
</template>

<script>
	import translateForm from './components/translateForm'
	import translateOut from './components/translateOut'
export default {
  name: 'App',
  data(){
  	return{
  		tranlated:""
  	}
  },
  components:{
  	translateForm,translateOut
  },
  methods:{
  	translateTest:function(text,language){
//		alert(text);
			this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190618T020436Z.01436cdad94fcca4.4348cab4e82b3bfc8280aa70d5f9713da1041792&lang='+language+'&text='+text)
			.then((res)=>{
//				console.log(res.body.text[0]);
				this.tranlated = res.body.text[0];
			})
  	}
  }
}
</script>

<style>
#app{
	text-align: center;
}
</style>
