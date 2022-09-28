<template>
  <div class="main-container">
    <h2 class="search-header">Search Records</h2>
    <input 
      type="text" 
      placeholder="Enter Employee Name" 
      class="employee-searchbar"
      v-model="searchCriteria"
    />
    <button @click="searchEmployees" class="search-employee-btn">Search</button>

    <h2 v-if="noRecordFoundMsg!==''" class="noRecordsMessage">{{noRecordFoundMsg}}</h2>

    <template v-for="employeeInfo in allEmployeesInfo" :key="employeeInfo.empid">
      <div class="employee-info-card">
        <h3>Name  : {{employeeInfo.name}}</h3>
        <h3>EmpId : {{employeeInfo.empid}}</h3>
        <h3 v-if="employeeInfo.age!=null">Age : {{employeeInfo.age}}</h3>
        <h3 v-if="employeeInfo.designation!=''">Designation : {{employeeInfo.designation}}</h3>
        <h3 v-if="employeeInfo.yearsOfExperience!=''">YOE : {{employeeInfo.yearsOfExperience}} years</h3>
        <div class="skills-main-container" v-if="employeeInfo.skills.length!==0">
          <h3 class="skill-header">Skills : </h3>
          <h3 class="skill-name" v-for="skill in employeeInfo.skills">
              {{skill}}
          </h3>
        </div>
      </div>
    </template>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    data() {
      return {
        searchCriteria: '',
        allEmployeesInfo : null,
        noRecordFoundMsg : ''
      }
    },
    methods : {
      searchEmployees()
      {
        let vm = this;
        if(this.searchCriteria!=="")
        {
          axios.get(`/api/records/${this.searchCriteria}`)
          .then(res=>{
            vm.allEmployeesInfo = res.data.allEmployees
            if(res.data.allEmployees.length==0)
            {
              vm.noRecordFoundMsg = "No Records Found"
            }
            else
            {
              vm.noRecordFoundMsg = ""
            }
          })
          .catch(err=>console.log(err))
        }
      }
    }
  }
</script>

<style scoped>
.main-container {
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

.search-header {
  color: var(--color-white);
}

.employee-searchbar {
  width: 70rem;
  min-width: 29rem;
  margin-top: 2rem;
  padding: 1.5rem 1.5rem;
  font-size: 1.5rem;
  box-sizing: border-box;
  outline: none;
  border: none;
  border-radius: 8px;
  font-family: 'Comfortaa';
}

.search-employee-btn {
  font-size: large;
  width: 300px;
  padding: 1rem 0;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 2.5rem;
}

.search-employee-btn:active {
  color: var(--color-white);
  background-color: var(--color-pink1);
}

.noRecordsMessage {
  color: var(--color-white);
  margin-top: 4rem;
}

.employee-info-card {
  width: 70rem;
  min-width: 29rem;
  margin-top: 4rem;
  padding: 1rem 2rem;
  background-color: var(--color-white);
  box-sizing: border-box;
  border-radius: 8px;
}

.skills-main-container {
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
}

.skill-header {
  margin-right: 1rem;
}

.skill-name {
  padding: 0 1rem;
  margin: 0 1rem 1rem 1rem;
  display: inline;
  vertical-align: middle;
  color: var(--color-white);
  background-color: var(--color-cadetblue);
  border-radius: 1rem;
}

@media only screen and (max-width:720px){
  .employee-searchbar, .employee-info-card {
    width: 50rem;
  }
}

@media only screen and (max-width:520px){
  .employee-searchbar, .employee-info-card {
    width: 30rem;
  }
}
</style>
