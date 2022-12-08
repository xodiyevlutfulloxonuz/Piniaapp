<script setup>
import { useCounterStore } from './store/counter';
const counterApp=useCounterStore()
</script>

<template>
  <div class="container">

    <div class="row">
      <h1 class="text-center"> Todo App</h1>
      <button class="btn btn-danger cleardata" @click="counterApp.clearUsers"> clear users</button>
      <h3 class="text center" v-if="(counterApp.users.length!==0)"> Userlar soni {{counterApp.users.length}}</h3>
     <h3 class="text center" v-else> Hozircha Userlar mavjud emas</h3>
    <form class="col-md-6 offset-3" @submit="counterApp.addUser">
      <input type="text" class="form-control" placeholder="Enter name..." v-model="counterApp.name">
      <input type="text" class="form-control my-2" placeholder="Enter email..." v-model="counterApp.email">
      <input type="text" class="form-control" placeholder="Enter job..." v-model="counterApp.job">
      <button class="btn btn-primary mt-2" type="submit"> add user</button>
    </form>
    <div class="col-md-6 mt-2">
      <table class="table table-striped">
        <thead>
          <tr>
            <th scope="col">#ID</th>
            <th scope="col">Name</th>
            <th scope="col">Email</th>
            <th scope="col">Job</th>
            <th scope="col">Update</th>
            <th scope="col">Delete</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="user in counterApp.users" :key="user.id">
            <th scope="row">{{user.id}}</th>
            <td>{{user.name}}</td>
            <td>{{user.email}}</td>
            <td>{{user.job}}</td>
            <td><button class="btn btn-primary"> update</button></td>
            <td><button class="btn btn-danger" @click="counterApp.deleteUser(user.id)">delete</button></td>
          </tr>
         
        </tbody>
      </table>
    </div>
    </div>

  </div>
 
</template>

<style>
.cleardata{
  width: 200px!important;
  padding: 10px 15px;

}
</style>>


