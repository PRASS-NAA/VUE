<script setup>
import { ref, computed, reactive } from 'vue'
import List from './List.vue'

const name = ref('')
const DOB = ref('')
const city = ref('')
const designation = ref('')
const phoneNum = ref('')
let btnText = ref('Show Users')
let toggle = ref(true)

const users = reactive([])

const age = computed(() => {
  if (!DOB.value) return ''
  return new Date().getFullYear() - new Date(DOB.value).getFullYear()
})

function createUser() {
  const newUser = {
    name: name.value,
    DOB: DOB.value,
    city: city.value,
    designation: designation.value,
    number: phoneNum.value,
    age: age.value,
  }

  users.push(newUser)

  name.value = ''
  DOB.value = ''
  city.value = ''
  designation.value = ''
  phoneNum.value = ''

  console.log(users)
}

function changeBtnText() {
  console.log('value of btnText : ', btnText.value, 'value of toggle is  ', toggle.value)
  if (toggle.value) {
    toggle.value = false
    btnText.value = 'Hide Users'
    return
  } else {
    toggle.value = true
    btnText.value = 'Show Users'
    return
  }
}
</script>

<template>
  <div id="main-div">
    <div id="form-div">
      <h1>User Form</h1>
      <form @submit.prevent="createUser">
        <label>Name:</label>
        <input v-model="name" type="text" />

        <label>DOB:</label>
        <input v-model="DOB" type="date" />

        <label>City:</label>
        <input v-model="city" type="text" />

        <label>Designation:</label>
        <input v-model="designation" type="text" />

        <label>Phone Number:</label>
        <input v-model="phoneNum" type="number" />

        <button type="submit">Create User</button>
      </form>
    </div>
    <div>
        <button @click="changeBtnText" id="toggleBtn">{{ btnText }}</button>
      <List v-show="!toggle" :users="users"/>
    </div>
  </div>    
</template>

<style scoped>
#main-div {
  display: flex;
  gap: 30px; 
  align-items: flex-start;
  margin: 20px;
  flex-wrap: wrap; 
}

#form-div {
  width: 373px;
  height: 532px;
  margin-bottom: 100px;
}

form {
  display: flex;
  flex-direction: column;
  border: #ccc 3px solid;
      width: 600px;
    height: 563px;
    padding: 62px;
}

form:hover {
  background-color: brown;
}
form label {
  margin-top: 10px;
  font-weight: bold;
}

form input {
  margin-top: 4px;
  padding: 6px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

form button, #toggleBtn {
  margin-top: 20px;
  padding: 10px 15px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}


</style>
