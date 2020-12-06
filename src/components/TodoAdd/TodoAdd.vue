



<template>
	<div>
		<h4>Todo Add</h4>
		<form>
			<input v-model="todoName" placeholder="enter todo name"/>
			<button v-on:click.prevent="handleSubmit">add</button>
		</form>
	</div>
</template>


<script>

	export default {
		name: 'TodoAdd',
		data: function(){
			return {
				todoName: ''
			}
		},
		methods: {
			handleSubmit: function(){

				if(!this.todoName)
					return

				console.log(this.todoName)
				this.$emit('todo-added', this.todoName)
				this.todoName = ''
			}
		},
	}
</script>





