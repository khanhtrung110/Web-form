<template>
  <form>
    <label>Email:</label>
    <input type="email" required v-model="email">

    <label>Password:</label>
    <input type="password" required v-model="password">
    <label>Role: </label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>
    <div class="skills">
      <label>Skill:</label>
      <input type="text" @keyup="addSkill" v-model="tempSkill">
      <p v-for="item in skills" :key="item" class="pill" @click="deleteSkill(item)">{{item}}</p>
    </div>
    <div class="terms">
      <input type="checkbox" v-model="terms" required>
      <label >Accept term and condition</label>
    </div>
  </form>
</template>

<script>
export default {
  data(){
    return{
      email: '',
      password: '',
      role: 'developer',
      terms: false,
      tempSkill:'',
      skills : []
    }
  },
  methods:{
    addSkill(e){
      if (e.key == ' ' && this.tempSkill) {
          if (!this.skills.includes(this.tempSkill)) {
           this.skills.push(this.tempSkill); 
          }
          this.tempSkill = ''
      }
    },
    deleteSkill(item){
        this.skills = this.skills.filter(function(skill,index) {
            return item !== skill;
        })
    }
  }
}
</script>

<style>
form{
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}
label{
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input,select{
    width: 100%;
    display: block;
    padding: 10px 10px;
    widows: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
input[type="checkbox"]{
  display: inline-block;
  width: 16px;
  margin-right: 10px;
  position: relative;
  top: 2px;
}
.pill{
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
</style>