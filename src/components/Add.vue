<template>
    <Header></Header>
    <div class="box-form3">
    <link href="https://fonts.googleapis.com/css?family=Open+Sans" rel="stylesheet">
		<div class="left">
			<div class="overlay">
				<h1>Add New........ ........Resturant</h1>
			</div>
		</div>
		<div class="right">
			<h5>Add New</h5>
			<div class="inputs">
                <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name"/>
                <br>
				<input type="text" name="address" placeholder="Enter Address" v-model="restaurant.address" />
				<br>
				<input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact"/>
			</div>
						
			<br><br>
			<button type="button" v-on:click="addRestaurant">Add New Resturant</button><br><br>
            <p class="last_in_add">.................................................................... </p>

	</div>
	
    </div>
</template>
<script>
    import Header from './Header.vue' ;
    import Axios from 'axios';
    export default{
        name: 'Add-component',
        components:{
            Header
        },
        data(){
            return{
                restaurant :{
                    name:'',
                    address:'',
                    contact:''
                }
            }
        },
        methods:{
              async addRestaurant(){
                console.warn(this.restaurant)
                const result = await Axios.post("http://localhost:3000/restsurant",{
                    name: this.restaurant.name,
                    address : this.restaurant.address,
                    contact : this.restaurant.contact
                });
                if(result.status == 201){
                     this.$router.push({name:'Home'}) 
                }
                console.warn("result", result)
              }  
        },  
         mounted(){
        let user = localStorage.getItem('user-info');
        if(!user){
            this.$router.push({name:'SignUp'}) 
        }
       }
    }
</script>
<style>

  .box-form3 {
	
  margin-top: 60px;
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

.box-form3 .left {
  color: #FFFFFF;
  background-size: cover;
  background-repeat: no-repeat;
  background-image: url("https://wallpapercave.com/wp/HARng0a.jpg");
  overflow: hidden;
  width: 60%
}
.box-form3 .left .overlay {
  width: 100%;
  height: 100%;
  background: #00000099;
  overflow: hidden;
  box-sizing: border-box;
}
.box-form3 .left .overlay h1 {
    font-family: 'Brush Script MT', cursive;
  font-size: 80px;
  line-height: 1;
  font-weight: 900;
  margin-top: 40px;
  margin-bottom: 20px;
  text-align: left;
  padding-left: 50px;
  
}
.box-form3 .left .overlay p {
    

  font-size: 30px;
  line-height: 1;
  font-weight: 600;
  margin-top: 40px;
  margin-bottom: 20px;
}
.box-form3 .right {
  padding-right: 60px;
  padding-top: 20px;
}
.box-form3 .right h5 {
  font-size: 40px;
  line-height: 0;
  text-align: left;
}
.box-form3 .right p {
  font-size: 14px;
  color: #B0B3B9;
}
.box-form3 .right input {
  width: 100%;
  padding: 10px;
  margin-top: 22px;
  font-size: 16px;
  border: none;
  outline: none;
  border-bottom: 2px solid #B0B3B9;
}


.box-form3 .right button {

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
.last_in_add{
    padding-top: 100px;
}
</style>