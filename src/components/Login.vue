<template>
    
<div class="box-form">
    <link href="https://fonts.googleapis.com/css?family=Open+Sans" rel="stylesheet">
		<div class="left">
			<div class="overlay">
				<h1>Welcome to</h1>
				<p>Resturant Management System</p>
			</div>
		</div>
		<div class="right">
			<h5>Login</h5>
			<div class="inputs">
				<input type="text" v-model="email" placeholder="Enter Email">
				<br>
				<input type="password" v-model="password" placeholder="Enter Password">
			</div>
						
			<br><br>
			<button v-on:click="login" >Login</button><br><br>
            <p class="last_in_login">Don't have an account?..<router-link to="/sign-up">Create Your Account</router-link> </p>

	</div>
	
</div>
</template>
<script>
    import axios from 'axios'
    export default{
        name: 'Login-component',
        data(){
            return{
                email:'',
                password:''
            }
        },
        methods:{
            async login(){
                let result = await axios.get(
                    `http://localhost:3000/user?email=${this.email}&password=${this.password}`
                )
                if(result.status==200 && result.data.length>0){
                    alert("Sign Up Done");
                    localStorage.setItem("user-info",JSON.stringify(result.data[0]))
                    this.$router.push({name:'Home'}) 
                }
                console.warn(result)
            }
        },
         mounted(){
        let user = localStorage.getItem('user-info');
        if(user){
            this.$router.push({name:'Home'}) 
        }
       }
    }
</script>
<style>
 

.box-form {
	
  margin-top: 90px;
  margin-left: 300px;
  width: 60%;
height: 550px;
  background: #FFFFFF;
  border-radius: 20px;
  overflow: hidden;
  display: flex;
  flex: 1 1 100%;
  align-items: stretch;
  justify-content: space-between;
  box-shadow: 0 0 20px 6px #090b6f85;
}

.box-form .left {
  color: #FFFFFF;
  background-size: cover;
  background-repeat: no-repeat;
  background-image: url("https://www.localsamosa.com/wp-content/uploads/2021/04/istockphoto-1018141890-612x612-1.jpg");
  overflow: hidden;
  width: 60%
}
.box-form .left .overlay {
  width: 100%;
  height: 100%;
  background: #00000090;
  overflow: hidden;
  box-sizing: border-box;
}
.box-form .left .overlay h1 {
    font-family: 'Brush Script MT', cursive;
  font-size: 80px;
  line-height: 1;
  font-weight: 900;
  margin-top: 40px;
  margin-bottom: 20px;
  text-align: left;
  padding-left: 50px;
  
}
.box-form .left .overlay p {
    

  font-size: 30px;
  line-height: 1;
  font-weight: 600;
  margin-top: 40px;
  margin-bottom: 20px;
}
.box-form .right {
  padding-right: 60px;
  padding-top: 20px;
}
.box-form .right h5 {
  font-size: 40px;
  line-height: 0;
  text-align: left;
}
.box-form .right p {
  font-size: 14px;
  color: #B0B3B9;
}
.box-form .right input {
  width: 100%;
  padding: 10px;
  margin-top: 22px;
  font-size: 16px;
  border: none;
  outline: none;
  border-bottom: 2px solid #B0B3B9;
}


.box-form .right button {

  color: #fff;
  font-size: 16px;
  padding: 12px 35px;
  border-radius: 50px;
  display: inline-block;
  border: 0;
  outline: 0;
   box-shadow: 0px 4px 20px 0px #808B96;
  background-image: linear-gradient(135deg, #000000 10%, #5D6D7E 100%);
  width:100%;
}
.last_in_login{
    padding-top: 100px;
}
</style>