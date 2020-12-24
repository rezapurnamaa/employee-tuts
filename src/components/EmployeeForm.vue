<template>
	<div>
		<form>
			<label>Employee Name</label>
			<input type="text" name="name">
			<label>Employee Email</label>
			<input type="text" name="email">
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
		}
	}
</script>

<style scoped>
	
</style>