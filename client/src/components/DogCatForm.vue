<template lang="html">

<div class="dog-cat-form">
<form>
<fieldset>
<legend> Add an animal!</legend>
<label for="name">Name:</label>
<input type="text" name="name" v-model="name" />

<label for="breed">Breed:</label>
<input type="text" name="breed" v-model="breed" />

<label for="type">Type</label>
<select name="type" v-model="type">
	<option value="" disabled>Choose...</option>
	<option value="dogs">Dog</option>
	<option value="cats">Cat</option>
</select>
</fieldset>
<input type="button" @click="handleSubmit" value="Apply" />
</form>
</div>
</template>

<script>
import { eventBus } from '../main';
export default {
	name: "dog-cat-form",
	data(){
		return {
			name: "",
			breed: "",
			type: ""
		}
	},
	methods: {
		handleSubmit(){

			const url = `http://localhost:3000/api/${this.type}`;
			const payload = {
				name: this.name,
				breed: this.breed
			};

			fetch(url, {
				method: 'POST',
				body: JSON.stringify(payload),
				headers: { 'Content-Type': 'application/json' }
			}).then(response => {
				eventBus.$emit("refresh-data", this.type);
				this.name = this.breed = this.type = "";
			});
		}
	}
}
</script>

<style lang="css" scoped>
.dog-cat-form{
	max-width: 200px;
	padding: 10px 20px;
	background: #f4f7f8;
	padding: 20px;
	background: #f4f7f8;
	border-radius: 8px;
	font-family: Georgia, "Times New Roman", Times, serif;
}
.dog-cat-form fieldset{
	border: none;
}
.dog-cat-form legend {
	font-size: 1.4em;
	margin-bottom: 10px;
}
.dog-cat-form label {
	display: block;
	margin-bottom: 8px;
}
.dog-cat-form input[type="text"],
.dog-cat-form select {
	font-family: Georgia, "Times New Roman", Times, serif;
	background: rgba(255,255,255,.1);
	border: none;
	border-radius: 4px;
	font-size: 15px;
	margin: 0;
	outline: 0;
	padding: 10px;
	width: 100%;
	box-sizing: border-box;
	-webkit-box-sizing: border-box;
	-moz-box-sizing: border-box;
	background-color: #e8eeef;
	color:#8a97a0;
	-webkit-box-shadow: 0 1px 0 rgba(0,0,0,0.03) inset;
	box-shadow: 0 1px 0 rgba(0,0,0,0.03) inset;
}
.dog-cat-form input[type="text"]:focus,
.dog-cat-form select:focus{
	background: #d2d9dd;
}
.dog-cat-form select{
	-webkit-appearance: menulist-button;
	height:35px;
}

.dog-cat-form input[type="button"]
{
	display: block;
	padding: 19px 39px 18px 39px;
	color: #FFF;
	margin: 0 auto;
	background: #1abc9c;
	font-size: 18px;
	text-align: center;
	font-style: normal;
	width: 75%;
	border: 1px solid #16a085;
	border-width: 1px 1px 3px;
	margin-bottom: 10px;
}
.dog-cat-form input[type="submit"]:hover,
.dog-cat-form input[type="button"]:hover
{
	background: #109177;
}
</style>
