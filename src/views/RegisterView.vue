<template>
  <main>
    <form @submit.prevent="handleRegisterFormSubmit">
      <h2>Register New Employee</h2>

      <div class="form-input-container">
        <label for="name"><h3>Full Name</h3></label>
        <input class="form-inputs" type="text" id="name" v-model.trim="registerFormValues.name" required/>
      </div>

      <div class="form-input-container">
        <label for="empid"><h3>Employee Id</h3></label>
        <input class="form-inputs" type="text" id="empid" maxlength="6" v-model.trim="registerFormValues.empid" required/>
      </div>
      
      <div class="form-input-container">
        <label for="age"><h3>Age</h3></label>
        <input class="form-inputs" type="number" id="age" min="0" v-model.number="registerFormValues.age"/>
      </div>
      
      <div class="form-input-container">
        <label for="designation"><h3>Designation</h3></label>
        <input class="form-inputs" type="text" id="designation" v-model="registerFormValues.designation"/>
      </div>
      
      <div class="form-input-container">
        <label><h3>Years Of Experience</h3></label>

        <div class="yoe-radio-container">
          <input class="form-inputs" type="radio" value="0-2" id="0-2yoe" v-model="registerFormValues.yearsOfExperience"/>
          <label for="0-2yoe">0-2</label>
        </div>

        <div class="yoe-radio-container">
          <input class="form-inputs" type="radio" value="3-5" id="3-5yoe" v-model="registerFormValues.yearsOfExperience"/>
          <label for="3-5yoe">3-5</label>
        </div>
        
        <div class="yoe-radio-container">
          <input class="form-inputs" type="radio" value="5-10" id="5-10yoe" v-model="registerFormValues.yearsOfExperience"/>
          <label for="5-10yoe">5-10</label>
        </div>
       
        <div class="yoe-radio-container"> 
          <input class="form-inputs" type="radio" value="10+" id="10+yoe" v-model="registerFormValues.yearsOfExperience"/>
          <label for="10+yoe">10+</label>
        </div>
      </div>
      
      <div class="form-input-container">
        <label for="skills"><h3>Skills</h3></label>
        
        <div class="yoe-checkbox-container">
          <input class="form-inputs" type="checkbox" value="HTML" id="html" v-model="registerFormValues.skills"/>
          <label for="html">HTML</label>
        </div>
       
        <div class="yoe-checkbox-container"> 
          <input class="form-inputs" type="checkbox" value="CSS" id="css" v-model="registerFormValues.skills"/>
          <label for="css">CSS</label>
        </div>
       
        <div class="yoe-checkbox-container"> 
          <input class="form-inputs" type="checkbox" value="Javascript" id="javascript" v-model="registerFormValues.skills"/>
          <label for="javascript">JavaScript</label>
        </div>
       
        <div class="yoe-checkbox-container"> 
          <input class="form-inputs" type="checkbox" value="React.js" id="react" v-model="registerFormValues.skills"/>
          <label for="react">React.js</label>
        </div>
       
        <div class="yoe-checkbox-container"> 
          <input class="form-inputs" type="checkbox" value="Redux" id="redux" v-model="registerFormValues.skills"/>
          <label for="redux">Redux</label>
        </div>
       
        <div class="yoe-checkbox-container"> 
          <input class="form-inputs" type="checkbox" value="Next.js" id="next" v-model="registerFormValues.skills"/>
          <label for="next">Next.js</label>
        </div>
      </div>
      
      <button class="registeration-submit-btn">Submit</button>
    </form>
  </main>
</template>

<script>
  import axios from 'axios';
  
  const initialFormValue = {
          name: '',
          empid: '',
          age: '',
          designation: '',
          yearsOfExperience: '',
          skills: []
        }
  export default {
    data()
    {
      return {
        registerFormValues : JSON.parse(JSON.stringify(initialFormValue))
      }
    },
    methods : {
      handleRegisterFormSubmit(event) {
        let vm = this
  
        axios.post("/api/register",this.registerFormValues)
        .then((res)=>{
          vm.registerFormValues = JSON.parse(JSON.stringify(initialFormValue))
        })
        .catch((err)=>{
          console.log("Error:",err)
        })
      }
    }
  }
</script>

<style scoped>
main {
  min-height: calc(100vh - 74px);
  height: fit-content;
  padding: 3rem 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  background: url('../assets/hexagonBg.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
  background-attachment: fixed;
}

form {
  width: 70rem;
  min-width: 29rem;
  padding: 2rem 4rem 3rem 4rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: var(--color-white);
  border-radius: 1rem;
  box-sizing: border-box;
}

.form-input-container {
  width: 100%;
  margin: 2rem 0;
}

form h2{
  margin-bottom: 2rem;
}

form label{
  cursor: pointer;
  margin: 2rem 0 1rem 0;
}

.form-inputs{
  outline: none;
  padding: 1rem;
  width: 100%;
}

.yoe-radio-container, .yoe-checkbox-container {
  display: flex;
}
.yoe-radio-container input, .yoe-checkbox-container input {
  width: 2rem;
  vertical-align: middle;
}

.yoe-radio-container label, .yoe-checkbox-container label {
  margin: 1rem;
}

.registeration-submit-btn {
  font-size: large;
  width: 100%;
  padding: 1rem 0;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.registeration-submit-btn:active {
  color: var(--color-white);
  background-color: var(--color-cadetblue);
}

@media only screen and (max-width:720px){
  form {
    width: 50rem;
  }
}

@media only screen and (max-width:520px){
  form {
    width: 30rem;
  }
}

</style>