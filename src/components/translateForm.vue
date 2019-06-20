<template>
  <div id="translateForm">
   <form v-on:submit="formSubmit">
   	<input type="text" v-model="textTranslate" placeholder="请输入要翻译的内容" />
   	<select v-model="language">
   		<option value="en">英语</option>
   		<option value="eo">世界语</option>
   		<option value="ru">俄语</option>
   		<option value="de">德语</option>
   		<option value="ko">韩语</option>
   	</select>
   	<input type="submit" value="翻译" />
   </form>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data(){
  	return{
  		textTranslate:"",
  		language:""
  	}
  },
  methods:{
  	formSubmit:function(event){
//		alert(this.textTranslate);
		this.$emit("formSubmit",this.textTranslate,this.language);
  		event.preventDefault();
  	}
  },
  created:function(){
  	this.language = "en";
  }
}
</script>

<style>

</style>
