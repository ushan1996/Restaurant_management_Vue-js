<template>
    <div class="nav">
        <div>
            <router-link to="/" >Restaurant Management System</router-link> 
        <router-link to="/add">Add Restaurant</router-link>
        </div>
         

            <a v-on:click="logout" clsss="logout"  >Logout >>></a>  

        
    </div>
</template>
<script>
    export default{
        name:'Header-component',
        methods:{
            logout(){ 
                localStorage.clear();
                this.$router.push({name:'Login'})
            }
        }
    }

</script>
<style>
    .nav{
        background-color:black;
        overflow: hidden;
        display: flex;
		justify-content:space-between;
        font-weight: 700;
    }
   .logout{
    display: block; text-align: center;
   }
</style>