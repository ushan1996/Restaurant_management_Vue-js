<template>
    <Header></Header>
    <h3 class="header-home">Hello {{ name }} </h3>
    <h2 class="header-home2">Restaurant List</h2>
    <table border="1" class="rest">
        <tr>
            <th>Id</th>
            <th>Name</th>
            <th>Contact</th>
            <th width="35%">Address</th>
            <th>Update</th>
            <th>Delete</th>
        </tr>
        <tr v-for="item in restaurant" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.contact }}</td>
            <td>{{ item.address }}</td>
            <td>
                <button class="btn1"><router-link :to="'/update/' + item.id" class="rout1">Update</router-link></button>
                
            </td>
            <td>
                <button class="btn2" v-on:click="deleteResttaurant(item.id)">Delete</button>
            </td>
        </tr>
    </table>
</template>
<script>
import Header from './Header.vue';
import Axios from 'axios';
export default {
    name: 'Home-component',
    data() {
        return {
            name: '',
            restaurant: []
        }
    },
    components: {
        Header
    },
    methods: {
        async deleteResttaurant(id) {
            let result = await Axios.delete("http://localhost:3000/restsurant/" + id);
            console.warn(result.status)
            if (result.status == 200) {
                    this.loadData() 
            }
        },
        async loadData() {
            let user = localStorage.getItem('user-info');
            this.name = JSON.parse(user).name;
            if (!user) {
                this.$router.push({ name: 'SignUp' })
            }
            let result = await Axios.get("http://localhost:3000/restsurant");
            console.warn(result)
            this.restaurant = result.data;
        }
    },
    async mounted() {
        this.loadData();

    }
}
</script>
<style>
body {
 background-image: url("https://wallpaperaccess.com/full/952192.jpg");
}
.rest {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
width: 90%;
  margin-left: 80px;
}

.rest td, #customers th {
  border: 1px solid #ddd;
  padding: 8px;
}

.rest tr:nth-child(even){background-color: #f2f2f2;}

.rest tr:hover {background-color: #ddd;}

.rest th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: #000000;
  color: white;
  text-align:center;
}
.btn2{
    border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  background-color: red;
  border-radius: 25px;
}
.btn1{
    border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  background-color: green;
  border-radius: 25px;
}
.rout1{
    color: #ddd;
    text-decoration: none;
}
.header-home{
    text-align: left;
    padding-left: 20px;
    color: #000000;
}
.header-home2{
    color: #000000;
}
</style>