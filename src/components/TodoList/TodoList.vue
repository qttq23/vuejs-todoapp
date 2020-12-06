



<template>
	<div>
		<h4>Todo List</h4>
		<ul>
			<TodoItem
			v-for="item in items" 
			:key="item.id" 
			:item="item"
			v-on:todo-deleted="$emit('todo-deleted', $event)"
			v-on:todo-done="$emit('todo-done', $event)"
			/>
		</ul>
	</div>
</template>


<script>

	import TodoItem from './TodoItem/TodoItem.vue'
	export default {
		name: 'TodoList',

		props: ['items'],

		components: {TodoItem}
	}
</script>





