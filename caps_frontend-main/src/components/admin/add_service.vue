<template>
  <div style="height:1000px;">
    <Menu />
    <button @click="opendialog" class="neumorphic-button" style="border-radius:3px;position:absolute; width:170px; right:105px; margin-top:65px;">ADD EVENT</button>
    <br><br><br><br>
    <div class="row" style="margin-left: 300px; margin-right: 20px;">
        <div class="col-md-12 col-sm-12">
          <button @click="" style="border-radius:3px; width:18%; margin-left:80px; margin-top:-1.5%; position:absolute; font-size:18px;font-family: 'Poppins', sans-serif;color:#1679AB;" class="neumorphic-button">List of Product</button>
          <input type="date" class="neumorphic-button" style=" margin-left:590px; top:-12px; height:40px;font-size:13px; width:150px;background-color:white; border-radius:3px; position:absolute;" v-model="startDate" required>

            </div>
              <div class="row" style="margin-left:70px; margin-top:60px; width:900px; font-family: 'Poppins', sans-serif;">
                <div class="col-sm-12">
                
                      <insert @data-saved="getInfo" />
                  <!-- Container with fixed width and height, and scrollbars enabled -->
<div style="width: 900px; height: 400px; overflow: auto;">
  <!-- Fixed width of 760px for the table and font size of 12px -->
  <table id="datatable-responsive" cellspacing="0" style="margin: 0 auto; width: 100%; font-size: 12px;">
    <thead>
      <tr>
        <!-- Setting the width and height of each column to 100px -->
        <th style="width: 100px; height: 100px;">ID</th>
        <th style="width: 100px; height: 100px;">IMAGE</th>
        <th style="width: 100px; height: 100px;">SERVICE</th>
        <th style="width: 100px; height: 100px;">INFORMATION</th>
        <th style="width: 100px; height: 100px;">LOWEST PRICE</th>
        <th style="width: 100px; height: 100px;">FIRST REQUEST</th>
        <th style="width: 100px; height: 100px;">SECOND REQUEST</th>
        <th style="width: 100px; height: 100px;">THIRD REQUEST</th>
        <th style="width: 100px; height: 100px;">FOURTH REQUEST</th>
        <th style="width: 100px; height: 100px;">FIFTH REQUEST</th>
        <th style="width: 100px; height: 100px;">SIXTH REQUEST</th>
        <th style="width: 100px; height: 100px;">FIRST PRICE</th>
        <th style="width: 100px; height: 100px;">SECOND PRICE</th>
        <th style="width: 100px; height: 100px;">THIRD PRICE</th>
        <th style="width: 100px; height: 100px;">FOURTH PRICE</th>
        <th style="width: 100px; height: 100px;">FIFTH PRICE</th>
        <th style="width: 100px; height: 100px;">SIXTH PRICE</th>
        <th style="width: 100px; height: 100px;">FIRST STOCK</th>
        <th style="width: 100px; height: 100px;">SECOND STOCK</th>
        <th style="width: 100px; height: 100px;">THIRD STOCK</th>
        <th style="width: 100px; height: 100px;">FOURTH STOCK</th>
        <th style="width: 100px; height: 100px;">FIFTH STOCK</th>
        <th style="width: 100px; height: 100px;">SIXTH STOCK</th>
        <th style="width: 100px; height: 100px;">ACTION</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="info in info">
        <td style="width: 100px; height: 100px;">{{ info.id }}</td>
        <td style="width: 100px; height: 100px;">
          <img v-if="info.image" :src="info.image" alt="Image" style="width:100px;height:100px;">
          <span v-else>No Image</span>
        </td>
        <td style="width: 100px; height: 100px;">{{ info.service }}</td>
        <td style="width: 100px; height: 100px;">{{ info.information }}</td>
        <td style="width: 100px; height: 100px;">{{ info.low_pricing }}</td>
        <td style="width: 100px; height: 100px;">{{ info.first_req }}</td>
        <td style="width: 100px; height: 100px;">{{ info.second_req }}</td>
        <td style="width: 100px; height: 100px;">{{ info.third_req }}</td>
        <td style="width: 100px; height: 100px;">{{ info.fourth_req }}</td>
        <td style="width: 100px; height: 100px;">{{ info.fifth_req }}</td>
        <td style="width: 100px; height: 100px;">{{ info.sixth_req }}</td>
        <td style="width: 100px; height: 100px;">{{ info.first_price }}</td>
        <td style="width: 100px; height: 100px;">{{ info.second_price }}</td>
        <td style="width: 100px; height: 100px;">{{ info.third_price }}</td>
        <td style="width: 100px; height: 100px;">{{ info.fourth_price }}</td>
        <td style="width: 100px; height: 100px;">{{ info.fifth_price }}</td>
        <td style="width: 100px; height: 100px;">{{ info.sixth_price }}</td>
        <td style="width: 100px; height: 100px;">{{ info.first_stock }}</td>
        <td style="width: 100px; height: 100px;">{{ info.second_stock }}</td>
        <td style="width: 100px; height: 100px;">{{ info.third_stock }}</td>
        <td style="width: 100px; height: 100px;">{{ info.fourth_stock }}</td>
        <td style="width: 100px; height: 100px;">{{ info.fifth_stock }}</td>
        <td style="width: 100px; height: 100px;">{{ info.sixth_stock }}</td>
        <td style="width: 100px; height: 100px;">
          <button @click="editRecord" class="btn btn-success btn-sm edit">EDIT</button>
        </td>
      </tr>
    </tbody>
  </table>
</div>

                  </div>
                </div>
              </div>
            


            <v-dialog v-model="dialogss" max-width="800px">
                <form @submit.prevent="saveService" class="container">
                  <v-card>
                    <br>
                    <v-card-title class="headline" style="margin-left: 155px; font-size: 14px; font-weight:900;  ">ADD<span style="font-size: 22px;  font-weight:100;">&nbsp;&nbsp;|&nbsp;</span><span style="font-weight:400; font-family: 'WindSong', cursive; font-size:33px;">Services</span></v-card-title>
                    <v-card-text>
              
                      <div class="form-group">
                        <label for="service">Service Title:</label>
                        <input type="text" class="search-input" style="width:100%; height:45px; border:none;" placeholder="Service Title" v-model="service" required>
                      </div>
                      <br>
                      <div class="form-row">
                        <div class="form-group col-md-6">
                          <label for="image">Upload File:</label>
                          <input type="file" id="image" class="neumorphic-button" style="width: 110%; background-color: white; border-radius: 3px;" @change="handleFileChange" accept="image/*" required>
                        </div>
                        <div>
                          <img v-if="imageUrl" :src="imageUrl" alt="Uploaded Image" style="position:absolute;width: 120px; height: 120px; right:11%;">
                        </div>
                      </div>
                      
                      
                      <br><br>
                      <div>
                        <div class="form-row">
                          <div class="form-group col-md-6">
                            <label for="low_pricing">Minimum Price:</label>
                            <input
                              type="number"
                              inputmode="numeric"
                              class="search-input"
                              style="width: 206%; height: 60%"
                              placeholder="Minimum price"
                              v-model="low_pricing"
                              required
                            />
                          </div>
                        </div>
                    
                        <!-- <div class="form-row">
                          <div class="form-group col-md-6">
                            <label for="high_pricing">Highest Price:</label>
                            <input
                              type="number"
                              inputmode="numeric"
                              class="search-input"
                              style="width: 206%; height: 60%"
                              placeholder="High price"
                              v-model="high_pricing"
                              required
                            />
                          </div>
                        </div> -->
                      </div>
              
                      <div class="form-row">
                        <div class="form-group col-md-6">
                          <label for="information">Service Information:</label>
                          <textarea class="search-input" v-model="information" style="width:206%; height:100%;" placeholder="service offers" required></textarea>
                        </div>
                      </div>
              
                      <br><br>
                      <h3 style="margin-left: 95px; font-size: 14px; font-weight:900;" >REQUEST<span style="font-size: 22px;  font-weight:100;">&nbsp;&nbsp;|&nbsp;</span><span style="font-weight:400; font-family: 'WindSong', cursive; font-size:33px;">Options</span></h3>
                      <br>

                      <div class="form-row">
                         <div class="form-group col-md-4">
                          <label for="first_req">Request 1:</label>
                          <input type="text" class="search-input" style="width:200px; height:70%; border:none;" placeholder="first request" v-model="first_req" >
                        </div>
                         <div class="form-group col-md-4">
                          <label for="first_price" style="margin-left:32%;">request price:</label>
                          <input type="number" class="search-input"  inputmode="numeric" style="width:66%;height:70%; border:none;margin-left:32%;" placeholder="0000" v-model="first_price" >
                        </div>
                         <div class="form-group col-md-4">
                          <label for="first_stock" style="margin-left:32%;">stock:</label>
                          <input type="number" class="search-input"  inputmode="numeric" style="width:66%;height:70%; border:none;margin-left:32%;" placeholder="0000" v-model="first_stock" >
                        </div>
                      </div>
              
                      <div class="form-row">
                         <div class="form-group col-md-4">
                          <label for="second_req">Request 2:</label>
                          <input type="text" class="search-input" style="width:126%;height:70%;border:none;" placeholder="second request" v-model="second_req" >
                        </div>
                         <div class="form-group col-md-4">
                          <label for="second_price" style="margin-left:32%;">request price:</label>
                          <input type="number" class="search-input"  inputmode="numeric" style="width:66%;height:70%; border:none;margin-left:32%;" placeholder="0000" v-model="second_price" >
                        </div>
                         <div class="form-group col-md-4">
                          <label for="second_stock" style="margin-left:32%;">stock:</label>
                          <input type="number" class="search-input"  inputmode="numeric" style="width:66%;height:70%; border:none;margin-left:32%;" placeholder="0000" v-model="second_stock" >
                        </div>
                      </div>

                      <div class="form-row">
                        <div class="form-group col-md-4">
                          <label for="third_req">Request 3:</label>
                          <input type="text" class="search-input" style="width:126%;height:70%;border:none;" placeholder="third request" v-model="third_req" >
                        </div>
                        <div class="form-group col-md-4">
                          <label for="third_price" style="margin-left:32%;">request price:</label>
                          <input type="number" class="search-input"  inputmode="numeric" style="width:66%;height:70%; border:none;margin-left:32%;" placeholder="0000" v-model="third_price" >
                        </div>
                        <div class="form-group col-md-4">
                          <label for="third_stock" style="margin-left:32%;">stock:</label>
                          <input type="number" class="search-input"  inputmode="numeric" style="width:66%;height:70%; border:none;margin-left:32%;" placeholder="0000" v-model="third_stock" >
                        </div>
                      </div>

                      <div class="form-row">
                        <div class="form-group col-md-4">
                          <label for="fourth_req">Request 4:</label>
                          <input type="text" class="search-input" style="width:126%;height:70%;border:none;" placeholder="fourth request" v-model="fourth_req" >
                        </div>
                        <div class="form-group col-md-4">
                          <label for="fourth_price" style="margin-left:32%;">request price:</label>
                          <input type="number" class="search-input"  inputmode="numeric" style="width:66%;height:70%; border:none;margin-left:32%;" placeholder="0000" v-model="fourth_price" >
                        </div>
                        <div class="form-group col-md-4">
                          <label for="fourth_stock" style="margin-left:32%;">stock:</label>
                          <input type="number" class="search-input"  inputmode="numeric" style="width:66%;height:70%; border:none;margin-left:32%;" placeholder="0000" v-model="fourth_stock" >
                        </div>
                      </div>

                      <div class="form-row">
                        <div class="form-group col-md-4">
                          <label for="fifth_req">Request 5:</label>
                          <input type="text" class="search-input" style="width:126%;height:70%;border:none;" placeholder="fifth request" v-model="fifth_req" >
                        </div>
                        <div class="form-group col-md-4">
                          <label for="fifth_price" style="margin-left:32%;">request price:</label>
                          <input type="number" class="search-input"  inputmode="numeric" style="width:66%;height:70%; border:none;margin-left:32%;" placeholder="0000" v-model="fifth_price" >
                        </div>
                        <div class="form-group col-md-4">
                          <label for="fifth_stock" style="margin-left:32%;">stock:</label>
                          <input type="number" class="search-input"  inputmode="numeric" style="width:66%;height:70%; border:none;margin-left:32%;" placeholder="0000" v-model="fifth_stock" >
                        </div>
                      </div>

                      <div class="form-row">
                        <div class="form-group col-md-4">
                          <label for="sixth_req">Request 6:</label>
                          <input type="text" class="search-input" style="width:126%;height:70%;border:none;" placeholder="sixth request" v-model="sixth_req" >
                        </div>
                        <div class="form-group col-md-4">
                          <label for="sixth_price" style="margin-left:32%;">request price:</label>
                          <input type="number" class="search-input"  inputmode="numeric" style="width:66%;height:70%; border:none;margin-left:32%;" placeholder="0000" v-model="sixth_price" >
                        </div>
                        <div class="form-group col-md-4">
                          <label for="sixth_stock" style="margin-left:32%;">stock:</label>
                          <input type="number" class="search-input"  inputmode="numeric" style="width:66%;height:70%; border:none;margin-left:32%;" placeholder="0000" v-model="sixth_stock" >
                        </div>
                      </div>

                    </v-card-text>
                    <v-card-actions>
              
                      <div style="margin-bottom: 10px;">
                        <button type="submit" class="neumorphic-button" style="margin-left: 15px; width: 275%; background-color: rgb(49, 48, 48); color: white;">Save Service</button>
                      </div>
              
                    </v-card-actions>
              
                  </v-card>
                </form>
              </v-dialog>
            </div>
  </template>
    
  <script>
  import { defineComponent } from 'vue';
  import axios from 'axios'
  import Menu from '@/components/admin/Menu.vue'
  
  export default
  defineComponent({
    data() {
    return { 
      info: [], 
      dialogss: false,
      imageUrl: null,
      service:"", 
      service:"", 
      information:"", 
      low_pricing:"", 
      image:"", 
      first_req:"", 
      second_req:"", 
      third_req:"", 
      fourth_req:"", 
      fifth_req:"", 
      sixth_req:"", 
      first_price:"", 
      second_price:"", 
      third_price:"", 
      fourth_price:"", 
      fifth_price:"", 
      sixth_price:"",
      first_stock:"", 
      second_stock:"", 
      third_stock:"", 
      fourth_stock:"", 
      fifth_stock:"", 
      sixth_stock:"", 
    }
  },
      components:{
          Menu,
          info:[],

      },
      created(){
          console.log(Menu);
          this.getInfo();
      },
      methods: {

async saveService() {
  try {
    // Display a confirmation dialog
    const userConfirmed = window.confirm('Are you sure you want to save?');

    // Check if the user clicked OK
    if (userConfirmed) {
      const formData = new FormData();
      formData.append('service', this.service);
      formData.append('information', this.information);
      formData.append('low_pricing', this.low_pricing);
      formData.append('first_req', this.first_req);
      formData.append('second_req', this.second_req);
      formData.append('third_req', this.third_req);
      formData.append('fourth_req', this.fourth_req);
      formData.append('fifth_req', this.fifth_req);
      formData.append('sixth_req', this.sixth_req);
      formData.append('first_price', this.first_price);
      formData.append('second_price', this.second_price);
      formData.append('third_price', this.third_price);
      formData.append('fourth_price', this.fourth_price);
      formData.append('fifth_price', this.fifth_price);
      formData.append('sixth_price', this.sixth_price);
      formData.append('first_stock', this.first_stock);
      formData.append('second_stock', this.second_stock);
      formData.append('third_stock', this.third_stock);
      formData.append('fourth_stock', this.fourth_stock);
      formData.append('fifth_stock', this.fifth_stock);
      formData.append('sixth_stock', this.sixth_stock);

      if (this.image instanceof File) {
        formData.append('image', this.image);
      }

      const ins = await axios.post("saveService", formData);

      // Clear form fields after successful save
      this.event_title = "";
      this.service = "";
      this.information = "";
      this.low_pricing = "";
      this.first_req = "";
      this.second_req = "";
      this.third_req = "";
      this.fourth_req = "";
      this.fifth_req = "";
      this.sixth_req = "";
      this.first_price = "";
      this.second_price = "";
      this.third_price = "";
      this.fourth_price = "";
      this.fifth_price = "";
      this.sixth_price = "";
      this.first_stock = "";
      this.second_stock = "";
      this.third_stock = "";
      this.fourth_stock = "";
      this.fifth_stock = "";
      this.sixth_stock = "";

      // Emit event and perform other actions
      this.$emit('data-saved');
      this.dialogss = false;
      this.getInfo();
    }
    // If the user clicked Cancel, do nothing
  } catch (error) {
    console.error(error);
  }
},

handleFileChange(event) {
  const file = event.target.files[0];
  if (file) {
    this.imageUrl = URL.createObjectURL(file);
    this.image = file; // Store the file object
  }
},
        async getInfo() {
      try {
        const response = await axios.get('getservice');
        this.info = response.data;
      } catch (error) {
        console.error(error);
      }
    }, 
  
    opendialog(){
        this.dialogss = true;
      },
      closemodal(){
        this.dialogss = false;
      },
      }
  });
  </script>
  
  <style scoped>
  
  </style>
  
  
  