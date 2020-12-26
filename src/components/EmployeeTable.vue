<template>
	<div>
		<p v-if="employees.length < 1" class="empty-table">No Employees</p>
		<table v-else>
			<thead>
				<tr>
					<th>Employee Name</th>
					<th>Employee Email</th>
					<th>Actions</th>
				</tr>
			</thead>
			<tbody>
				<tr v-for="employee in employees" v-bind:key="employee.id">
					<td v-if="editing === employee.id">
						<input  type="text" name="name" v-model="employee.name"/>
					</td>
					<td v-else>{{employee.name}}</td>
					<td v-if="editing === employee.id">
						<input type="text" name="email" v-model="employee.email">
					</td>
					<td v-else>{{employee.email}}</td>
					<td v-if="editing === employee.id">
						<button @click="editEmployee(employee)">Save</button>
						<button @click="editing = null" class="mute-button">Cancel</button>
					</td>
					<td v-else>
						<button @click="editMode(employee.id)">Edit</button>
						<button @click="$emit('delete:employee', employee.id)">Delete</button>
					</td>
				</tr>
			</tbody>
		</table>
	</div>
</template>

<script>
	export default {
		name: 'employee-table',
		props: {
			employees: Array
		},
		data() {
			return {
				editing: null
			}
		},
		methods: {
			editMode(id) {
				this.editing = id
			},

			editEmployee(employee) {
				if(employee.name === '' || employee.email === '' ) return
				this.$emit('edit:employee', employee, employee.id)
				this.editing = null
			}
		}
	}
</script>
<style scoped="">
	button {
		margin: 0 0.5rem 0 0;
	}

	.empty-table {
		text-align: center;
	}
</style>