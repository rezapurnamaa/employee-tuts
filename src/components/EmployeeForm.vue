<template>
	<div id="employee-form">
		<form @submit.prevent="handleSubmit">
			<label>Employee Name</label>
			<input 
				ref="first"
				v-model="employee.name" 
				type="text" 
				name="name"
				:class="{'has-error': submitting && invalidName}"
				@focus="clearStatus"
				@keyPress="clearStatus"
			/>
			<label>Employee Email</label>
			<input v-model="employee.email" 
			type="text" 
			name="email"
			:class="{'has-error': submitting && invalidEmail}"
			@focus="clearStatus"
			@keyPress="clearStatus"		
			/>
			<p v-if="error && submitting" class="error-message">
				❗️Please fill out required fields
			</p>
			<p v-if="success" class="success-message">
				✅ Employee successfully added
			</p>
			<button>Add Employee</button>
		</form>
	</div>
</template>

<script>
	export default {
		name: 'employee-form',
		data() {
			return {
				submitting: false,
				error: false,
				success: false,
				employee: {
					name: '',
					email: ''
				}
			}
		},
		computed: {
			invalidName() {
				return this.employee.name === ''
			},

			invalidEmail() {
				return this.employee.email === ''
			}
		},

		methods: {
			handleSubmit() {
				this.submitting = true
				this.clearStatus()

				if(this.invalidName || this.invalidEmail) {
					this.error = true
					return
				}

				this.$emit('add:employee', this.employee)
				this.employee = {
					name: '',
					email: ''
				}

				this.error = false
				this.success = true
				this.submitting = false
				this.$refs.first.focus()
			},

			clearStatus() {
				this.error = false,
				this.success = false
			}
		}
	}
</script>

<style scoped>
	form {
		margin-bottom: 2rem;
	}

	[class*='-message'] {
		font-weight: 500;
	}

	.error-message {
		color: #d33c40;
	}

	.success-message {
		color: #32a95d;
	}
	
</style>