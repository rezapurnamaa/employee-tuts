<template>
	<div>
		<form @submit.prevent="handleSubmit">
			<label>Employee Name</label>
			<input v-model="employee.name" type="text" name="name">
			<label>Employee Email</label>
			<input v-model="employee.email" type="text" name="email">
			<button>Add Employee</button>
		</form>
	</div>
</template>

<script>
	export default {
		name: 'employee-form',
		data() {
			return {
				employee: {
					name: '',
					email: ''
				}
			}
		},
		methods: {
			handleSubmit() {
				console.log('handleSubmit')
			}
		}
	}
</script>

<style scoped>
	
</style>