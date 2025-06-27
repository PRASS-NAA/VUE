<script setup>
defineProps(['users'])
</script>

<template>
    <table>
        <thead>
            <tr>
                <th>Name</th>
                <th>DOB</th>
                <th>City</th>
                <th>Designation</th>
                <th>Phone Number</th>
                <th>Age</th>
            </tr>
        </thead>

        <tbody>
            <tr v-for="user in users">
                <td>{{ user.name }}</td>
                <td>{{ user.DOB }}</td>
                <td>{{ user.city }}</td>
                <td>{{ user.designation }}</td>
                <td>{{ user.number }}</td>
                <td>{{ user.age }}</td>
            </tr>
        </tbody>
    </table>
</template>

<style scoped>
table {
  border-collapse: collapse;
  min-width: 500px;
  border: 1px solid #ddd;
}

thead {
  background-color: #4caf50;
  color: white;
}

th,
td {
  padding: 12px 15px;
  border: 1px solid #ddd;
  text-align: left;
}
</style>