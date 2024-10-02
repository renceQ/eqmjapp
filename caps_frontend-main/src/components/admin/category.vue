<template>
  <div style="height:950px;">
  <button @click="" style="border-radius:3px; width:18%; margin-left:27.5%; margin-top:4%; position:absolute; font-size:18px;font-family: 'Poppins', sans-serif; color:#1679AB;" class="neumorphic-button ">Product Category</button>
    <div class="row" style="margin-left: 300px; margin-right: 20px;">
      <div class="col-md-12 col-sm-12">
            
          </div>
            <div class="row" style="margin-top:140px;width:940px; margin-left:50px;">
              <div class="col-sm-12">
                <div class="card-box table-responsive">
                    <insert @data-saved="getInfo" />
                  <table id="datatable-responsive" class="table table-bordered table-striped dt-responsive nowrap" cellspacing="0" width="80%" style="margin: 0 auto;">
                    <thead>
                      <tr>
                        <th>ID</th>
                        <th>CATEGORY</th>
                        <th>ACTION</th>
                      </tr>
                    </thead>
                    <tbody>
                      <tr v-for="info in info">
                        <td>{{ info.id}}</td>
                        <td>{{ info.category_name}}</td>
                        <td>
                          <button @click="editRecord" class="btn btn-success btn-sm edit"> EDIT</button>
                        </td>
                      </tr>
                    </tbody>
                  </table>
                </div>
              </div>
            </div>
          </div>


    <div>
      <form @submit.prevent="savecateg">
        <label for="category_name">Category</label>
        <input type="text" placeholder="category_name" v-model="category_name" required>
        <br>
        <button type="submit" class="btn btn-primary">Submit</button>
      </form>
    </div>

  
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      category_name:"", 
      info: [], 
 
    }
  },
  created() {
    this.getInfo();
    
  },
  methods: {

    async savecateg() {
      try {
        const ins = await axios.post("savecateg", {
          category_name: this.category_name,
        });

        this.category_name ="";
        this.$emit('data-saved');
        this.getInfo();

        $('successModal').modal('show');
      } catch (error) {
        console.error(error);
      }
    },

    async getInfo() {
      try {
        const response = await axios.get('getcat');
        this.info = response.data;
      } catch (error) {
        console.error(error);
      }
    }, 
    deleteRecord(categoryId) {
      console.log(`Deleting category with ID: ${categoryId}`);
      // Implement delete logic here
    }
  }
};
</script>

<style >
/* Global styles */
body {
  font-family: Arial, sans-serif;
  background-color: #f3f3f3;
  margin: 0;
}

.container {
  width: 90%;
  margin: 0 auto;
}

.x_panel {
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 5px;
  margin-bottom: 20px;
}

.x_title {
  border-bottom: 1px solid #ddd;
  padding: 10px 15px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.x_title h2 {
  font-size: 24px;
  margin: 0;
}

.x_content {
  padding: 15px;
}

.card-box {
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
  background-color: #fff;
}

.table {
  width: 100%;
  border-collapse: collapse;
}

.table th,
.table td {
  border: 1px solid #ddd;
  padding: 8px;
}

.table th {
  background-color: #f2f2f2;
  color: #333;
  font-weight: bold;
}

.table tbody tr:nth-child(even) {
  background-color: #f9f9f9;
}

.table tbody tr:hover {
  background-color: #e0e0e0;
}

.btn {
  padding: 6px 12px;
  font-size: 14px;
  border-radius: 4px;
  cursor: pointer;
}

.btn-success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}

.btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}

/* Form styles */
form {
  margin-top: 20px;
  margin-left: 500px;
}

/* Input field styles */
input[type="text"] {
  width: 250px;
  padding: 8px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

input[type="text"]:focus {
  outline: none;
  border-color: #5cb85c; /* Change color on focus */
}

/* Button styles */
button[type="submit"] {
  padding: 8px 20px;
  font-size: 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  background-color: #337ab7;
  color: #fff;
}

button[type="submit"]:hover {
  background-color: #286090; /* Darker color on hover */
}


</style>