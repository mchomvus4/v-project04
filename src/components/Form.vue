<template>
  <form @submit.prevent="handleSubmit">
   <label>Email:</label>
   <input type="email" required v-model="email">
   <label>Password:</label>
   <input type="password" required v-model="password">
   <div v-if="passwordError" class="error">{{passwordError}}</div>

   <label>Role:</label>
   <select v-model="role">
    <option value="">Select From a List</option>
    <option value="developer">Web Developer</option>
    <option value="designer">Web Designer</option>
   </select>

   <label>Skills:</label>
   <input type="text" v-model="tempSkill" @keyup="addSkill">
   <div v-for="skill in skills" v-bind:key="skill" class="addSkills">
    <span @click="deleteSkill(skill)">{{skill}}</span>
   </div>

   <div class="terms">
    <input type="checkbox" v-model="terms" required>
    <label>Accept terms and conditions</label>
   </div>
   <div class="submit">
    <button>Create an Account</button>
   </div>
  </form>

  <!-- <p>Email:  {{email}} </p>
  <p>Password:  {{password}}</p>
  <p>Role: {{role}}</p>
  <p>Terms: {{terms}}</p> -->
 
</template>

<script>
export default {
data(){
 return{
  email:'',
  password:'',
  role:'',
  terms: false,
  tempSkill:'',
  skills:[],
  passwordError:''
 }
},
methods: {
 addSkill(e){
  if(e.key === ',' && this.tempSkill){
   if(!this.skills.includes(this.tempSkill)){
      this.skills.push(this.tempSkill)
   }
   this.tempSkill = ''
  }
 },
 deleteSkill(skill){
  this.skills = this.skills.filter((item)=>{
   return skill !== item
  })
 },
 handleSubmit(){
 //validate password
   this.passwordError = this.password.length > 8 ? 
     '' : 'Password must be at least 8 character long'
     if(!this.passwordError){
      console.log('email', this.email)
      console.log('password', this.password)
      console.log('role', this.role)
      console.log('skills', this.skills)
      console.log('terms', this.terms)
     }
 }
}
}
</script>

<style scoped>
form{
 max-width: 420px;
 margin: 30px auto;
 background: #fff;
 text-align: left;
 padding: 40px;
 border-radius: 10px;
}
label{
 color: #aaa;
 display: inline-block;
 margin: 25px 0px 15px;
 font-size: 0.6rem;
 text-transform: uppercase;
 letter-spacing: 1px;
 font-weight: bold;
}
input, select{
 display: block;
 padding: 10px 6px;
 width: 100%;
 box-sizing: border-box;
 border: none;
 border-bottom: 1px solid #487eb0;
 color: #555;
 outline: none;
}
input[type="checkbox"]{
display: inline-block;
width: 16px;
margin: 0 10px 0 0;
position: relative;
top: 2px; 
}
.addSkills{
 display: inline-block;
 margin: 20px 10px 0 0;
 padding: 6px 12px;
 background: #eee;
 border-radius: 20px;
 font-size: 12px;
 letter-spacing: 1px;
 font-weight: bold;
 color: #777;
 cursor: pointer;
}
button{
 background: #487eb0;
 border: none;
 padding: 10px 20px;
 margin-top: 20px;
 color: #fff;
 border-radius: 20px;
}
.submit{
 text-align: center;
}
.error{
 color: #ff0062;
 margin-top: 10px;
 font-size: 0.8em;
 font-weight: bold;
}
</style>