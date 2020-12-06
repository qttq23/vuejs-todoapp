



<template>
	<div>
		<h4>Search</h4>
		<input v-model="keySearch" placeholder="enter todo name">
		<button v-on:click="handleClearBtnClicked">clear</button>
	</div>
</template>


<script>

	export default {
		name: 'SearchBar',
		data: function(){
			return {
				keySearch: ''
			}
		},
		watch: {
			keySearch: function(value, oldValue){
				console.log(value)
				console.log(oldValue)

				this.$emit('keysearch-changed', value)
			}
		},
		methods: {
			handleClearBtnClicked: function(){
				this.keySearch = ''
			}
		},
	}
</script>





