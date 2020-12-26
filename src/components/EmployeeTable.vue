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
					<td>{{employee.name}}</td>
					<td>{{employee.email}}</td>
					<td>
						<button>Edit</button>
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