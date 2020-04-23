<template>
	<div>
		<li>
			<input type="checkbox" v-on:change="todo.completed = !todo.completed">
			<span v-bind:class="{done: todo.completed}">
				
				<strong>{{index+1}}</strong>
				{{ todo.title }}
			</span>
			<button class="rm"
				v-on:click="$emit('remove-todo', todo.id)"
			>&times;</button>
		</li>
	</div>
</template>
<script>
	export default{
		props:{
			todo:{
				type: Object,
				required: true
			},
			index: Number
		}
	}
</script>

<style scoped>
	li{
		border: 2px solid #2C2C40;
		border-radius: 10vw;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 5px;
		margin-bottom: 1rem;
	}
	.rm{
		background: #D30609;
		color: #fff;
		border: none;
		font-size: 1rem;
		border-radius: 50%;
	}
	input{
		margin-right: 2rem;
	}
	.done{
		text-decoration: line-through;
	}
</style>