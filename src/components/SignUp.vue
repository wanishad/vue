<template>
<h1>Sign Up</h1>
<div class="register">
<input type="name" v-model="name" placeholder="Enter Name">
<input type="email" v-model="email" placeholder="Enter Email">
<input type="password" v-model="password" placeholder="Enter password">
<button v-on:click="Submit" class="btn">SignUp</button>
</div>
</template>
<script>
import axios from 'axios'
export default {
    name: "SignUp",
    data()
    {
      return {
        name: "",
        email: "",
        password: ""
      }
    },
    methods:{
      async Submit(){
        let response = await axios.post('http://localhost:3000/user', {
          
          name:this.name,
          email:this.email,
          password:this.password
        });
        console.log(response);
        if(response.status==201){
          alert("signup user")
        }
        localStorage.setItem("info", JSON.stringify(response.data))
      }
    }
}
</script>

<style scoped>
.register input{
    width: 345px;
  display: block;
  margin: 20px auto;
  border: 1px solid gray;
  padding: 6px 11px;
    transition: all ease-out 0.3s;
  &:hover{
    border: 1px solid orange;
  }
}
h1{
    transition: all ease-in-out 0.3s;
    color: grey;
    cursor: pointer;
    &:hover{
        color: orange;
    }  
}
.btn{
    padding: 6px 0px;
    width: 367px;
    background-color: orange;
    color: black;
    border: 1px solid transparent;
    transition: all ease-out 0.3s ;
    &:hover{
        background-color: transparent;
        color: orange;
        border: 1px solid orange;
        
    }

}


</style>