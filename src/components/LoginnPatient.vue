<template>
      <div>
       
       <h1>{{objj}}</h1>
            
          <div class="regpatient" style="height: 680px;">
                <h1 >PATIENT LOGIN</h1>
                <form @submit="fs" enctype=multipart/form-data>
                    <ul>
                        <li>
                            <label for="fname" class="label" >Username:</label>
                            <input type="text"   v-model="username"   id="fname" name="username" class="inputfield" required><br><br>
                        </li>
                        <li>
                            <label for="fname" class="label">Password:</label>
                            <input type="text"    v-model="password"   id="fname" name="password" class="inputfield"><br><br>
                        </li>
                      
                      
                       
                        <li>
                            <input type="submit" value="Submit" name="patient" class="signup">
                        </li>
                    </ul>
                </form>
        
            </div>

            <h1>{{objj}}</h1>
            <h1>hello</h1>
            <vue-instant-loading-spinner ref="Spinner"></vue-instant-loading-spinner>
   </div>
    
    
</template>

<script>
// import uuid from 'uuid';
import VueInstantLoadingSpinner from "vue-instant-loading-spinner/src/components/VueInstantLoadingSpinner.vue";
// import axios from "axios";
export default {
    name: "LoginnPatient",
    data (){
        return{
            objj: {
                username:"",
                password:""
               
               

            },
            
            username: '',
            password: '',
          
        
    
        }
    },

    components: {
    VueInstantLoadingSpinner
  },
  methods:{
         fs(e)
        { 
             
            e.preventDefault();
            console.log("submit pressed")
            this.objj.username=this.username
            this.objj.password=this.password
          
            const newTodo = {
                username: this.username,
                password : this.password ,
             
               
            
            }
            console.log(newTodo)

        //   axios.post('https://jsonplaceholder.typicode.com/todos', {
        //         patientId: this.username,
        //         pswd : this.password ,
            
        //          })
        //     .then(res => this.objj = res.data)
        //     .catch(e => {
        //     this.errors.push(e)
        //     })
        if (newTodo.username=='1')
        {
            this.$router.push('Home') 
        }
      
        }
  }
   
}
</script>

<style  scoped>


</style>