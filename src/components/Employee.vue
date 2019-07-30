<template>
  <q-page class="flex flex-center">
    <div>{{employeeData}}</div>

    <div class="row" style="background: #008080; color: white">

      <div class ="col">
        <p>ini firstname</p>  
        <button class = "primary" @click="getFirstNameOnly">Firstname</button>
        <p>{{firstNameDataOnly}}</p>
      </div>
      

      <div class ="col">
        <p>ini lastname</p>
        <button class = "primary" @click="getLastNameOnly">Lastname</button>
        <p>{{lastNameDataOnly}}</p>
      </div>

      <div class="col">
        <p>Submit</p>
        <button class="primary" @click="createEmployee()">Submit</button>
      </div>
      
    </div>
  </q-page>
</template>

<style>
</style>

<script>
import Vue from 'vue'
import employee from "../api/employee/index";

export default {
  name: 'Employee',

  data() {
      return {
          employeeData: {},
          firstNameDataOnly: [],
          lastNameDataOnly: [],
          param: {
            "firstname": "asdasd",
            "lastname": "haasdasdhah",
            "email": "aku@asdjk.com",
            "phone": "0811782920"
          }
      }
  },

  methods: {
    getFirstNameOnly() {
      const self = this;
      employee.getEmployee(window).then(function(datas){
        console.log('Ini data nama depan', datas)
        for (let i=0; i < datas.length; i++) {
          self.firstNameDataOnly.push(datas[i].firstname)
        }
        return datas;
      }).catch(function(err) {
        console.log(err)
      });
    },

    getLastNameOnly() {
      const self = this;
      employee.getEmployee(window).then(function(datas){
        console.log('Ini data nama depan', datas)
        for (let i=0; i < datas.length; i++) {
          self.lastNameDataOnly.push(datas[i].lastname)
        }
        return datas;
      }).catch(function(err) {
        console.log(err)
      });
    },

    createEmployee(){
      const self = this;
      employee.submitEmployee(window, self.param).then(function(res){
        return res
      }).catch(function(err){
        console.log(err)
      })
    }

  },

  beforeCreate(){

      let self = this
      employee.getEmployee(window).then(function(datas) {
          return datas
      }).then(function(res){
          console.log(res)
          self.employeeData = res
      }).catch(function(err){
          console.log(err)
      })
  }
}
</script>
