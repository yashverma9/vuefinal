<template>
  <div>
    <!-- <h1>inside hospitaladmind</h1> -->
    <h1>{{x}}</h1>
    <h1 id="hero2">HOSPITAL ADMIN</h1>
    <div class="flex-container">
      <div>
          <h1>Doctor Details</h1>
        <table style="width:100%">
          <tr>
            <th>Firstname</th>
            <th>Lastname</th>
            <th>Age</th>
          </tr>
          <tr>
            <td>Jill</td>
            <td>Smith</td>
            <td>50</td>
          </tr>
        </table>
      </div>

      <div>
          <h1>Patient Details</h1>
        <table style="width:100%">
          <tr>
            <th>Firstname</th>
            <th>Lastname</th>
            <th>Age</th>
          </tr>
          <tr>
            <td>Jill</td>
            <td>Smith</td>
            <td>50</td>
          </tr>
          <tr>
            <td>Jill</td>
            <td>Smith</td>
            <td>50</td>
          </tr>
        </table>
      </div>
    </div>

     <div class="ro ">

                <h3 id="up">UPLOAD PRESCRIPTION</h3>
                <form @submit="fs" enctype=multipart/form-data >
                    <ul>
                        <li>
                            
                                <label for="fname" >Patient ID:</label>
                                <input type="text" v-model="patid" id="fname" name="patid" >
                            
                        </li>
                        <li>
                            <label for="fname" >Upload prescription:</label>
                            <input type="file"  ref="file" id="myFile" name="patreport" >
                        </li>
                        
                            
                            <li>
                                <input type="submit" value="Submit" name="patsubmit" class="cfs" id="reg">
                            </li>
                        
                    </ul>
               </form>
            </div>
    



  </div>
</template>

<script>
// import blob from 'blob';
// import docxtemplater from "docxtemplater";
// import PizZip from "docxtemplater"
import axios from "axios";
export default {
  name: "hospitaladmind",
  mounted() {
    console.log("created");
    this.x = 99;
  },

  data() {
    return {
      x: 1,
      patid:"",
      file:{}
    };
  },
    methods: {
        fs(e)
        { 
             
            e.preventDefault();
            console.log("submit pressed")
            console.log(this.patid)
            this.file= this.$refs.file.files[0];
             var doc=this.file;
             console.log("this is file")
              console.log(doc)
              const formData = new FormData();
              formData.append('file' , this.file)
              console.log("this is after object")
              console.log(formData)
              axios.post('/upload' , formData)
             .then(res => console.log(res.data))
        
            .catch(e => {
            this.errors.push(e)
            })
            //   var text=doc.getFullText();
            // console.log("this is doc");
            // // var x = JSON.stringify(doc)
            // //var stream = blob.stream(doc);
            //  console.log(text);
            //  console.log(doc);
            // // console.log(this.file)
        },
        // generate()
        // {
        //   if (docs.files.length === 0) {
        // alert("No files selected")
        // }
        // reader.readAsBinaryString(docs.files.item(0));

        //  reader.onerror = function (evt) {
        // console.log("error reading file", evt);
        // alert("error reading file" + evt)
        // }
        //  reader.onload = function (evt) {
        // const content = evt.target.result;
        // var zip = new PizZip(content);
        // // Same code as in the main HTML example.
        // }
        // }
     

    //  created(){

    //      axios.get('https://jsonplaceholder.typicode.com/todos')
    //      .then(res => console.log(res))
    //      .catch(err => console.log(err))

    //  }
    }
};
console.log("outside");
</script>

<style scoped>
table,
th,
td {
  /* border: 1px solid black; */
  border-collapse: collapse;
}

.flex-container {
  display: flex;
  /* background-color: rgb(255, 255, 255); */
   background-color: white;
  /* color: white; */
  justify-content: space-around;
   /* border-radius: 25px; */
     -webkit-box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
          box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}

#hero2{
    text-align: center;
    font-size: 2em;
}

.ro {
  height: 230px;
  width: 250px;
  background-color: white;
  /* color: white; */
  border-radius: 25px;
  padding: 0.5em;
    margin: 2em auto;
  
  -webkit-box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
          box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}

#up{
    text-align: center;
}
</style>