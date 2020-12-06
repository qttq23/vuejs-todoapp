



<template>
	<li v-bind:class="{done: item.isDone}">
		{{item.title}}
		<div class="btnGroup">
			<button class="btnDone" v-on:click="$emit('todo-done', item)">done</button>
			<button class="btnDelete" v-on:click="$emit('todo-deleted', item)">delete</button>
		</div>
	</li>
</template>


<script>

	export default {
		name: 'TodoItem',

		props: ['item']
	}
</script>


<style>


.done .btnDelete, .done .btnDone {
	display: none;
}

.btnDelete{
	border: 2px solid #DC3545;
	color: white;
	background-color: #DC3545;
}

.btnDone{
	border: 2px solid #28A745;
	color: white;
	background-color: #28A745;
}

</style>




