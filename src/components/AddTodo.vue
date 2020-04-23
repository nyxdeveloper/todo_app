<template>
	<form @submit.prevent="onSubmit">
		<input type="text" class="added" v-model="title">
		<button type="submit" class="add">Add</button>
	</form>
</template>
<script>
	export default{
		data(){
			return{
				title: ''
			}
		},
		methods:{
			onSubmit(){
				console.log('submit', this.title)
				if (this.title.trim()) {
					const newTodo={
						id:Date.now(),
						title: this.title,
						completed: false
					}
				this.$emit('add-todo', newTodo)
				}
				this.title=''
			}
		}
	}
</script>
<style>
	form{
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.added{
		margin: 1rem;
		width: 40vw;
		border-radius: 10vw;
		border: 1px solid #2C2C40;
		height: 40px;
		padding-left: 1rem;
		font-size: 1rem;
	}
	.add{
		background: #4AE72E;
		border: none;
		border-radius: 6vw;
		color: #fff;
		height: 40px;
		width: 5vw;
		min-width: 70px;
	}
	.add:hover{
		background: #3DBE26;
		transition: 0.5s;
		transform: scale(1.05);
	}
	button, input, textarea, a, button:active, input:active, textarea:active, a:active, button:focus, input:focus, textarea:focus, a:focus{
		outline: none;
	}

</style>