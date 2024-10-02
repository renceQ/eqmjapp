<template>
  <div style="position:absolute;background-color:rgb(245, 245, 245); width:100%; height:2000px;">
    <div style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
    animation: fade-up 0.8s ease-out forwards; position: absolute; margin-top:160px; margin-left:90px; ">
      <img style="width:70px; height:70px; "  v-if="info.length > 0" :src="info[0].profile_picture" alt="Profile" class="profile-picture-navbar">
      <span v-if="info.length > 0" style="font-weight: 400;">
        <a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{{ info[0].showed_username }}</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color: black;" href="/editprofiles"><i class="fas fa-pencil-alt"></i>&nbsp;&nbsp;&nbsp; Edit Profile</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color:rgb(0, 0, 0);" href="/orderhistory"><i class="fas fa-history custom-icon"></i>&nbsp;&nbsp;&nbsp; Order History</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color: black;" href="/toship_main"> <i class="fas fa-shopping-bag"></i>&nbsp;&nbsp;&nbsp; My Purchase</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color: darkorange;" href="/addtocart"> <i class="fas fa-shopping-cart custom-icon"></i>  &nbsp;&nbsp;&nbsp;Shopping Cart</a>
      </span>
    </div>
    <div>

        <div class="neumorphic-search" style="  height:50px; margin-top: 150px; opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up .8s ease-out forwards;
        animation-delay: 0.2s; margin-left:315px; ">
          <input v-model="searchText" @input="updateSearch" type="text" placeholder="Search Product by name..." class="search-input" style="margin-top:8px;border: 0px;"/>
          <button style="position:absolute;margin-top:8px; margin-left:602px; width:49px; height: 49px; " class="search-button">
            <i class="fas fa-search"></i>
          </button>
              <a href="/addtocart" style="position:absolute;margin-top:8px; margin-left:660px; width:49px; height: 49px; color: black;"  class="search-button">
                <i style="margin-left:7px; margin-top:8px;" class="fas fa-shopping-cart custom-icon"></i>
                </a>
             
              <!-- <img :src="require('../../../public/img/higa.gif')"  style="width: 180px; height: 150px;">     -->
          </div>
             
               
      
    
        <nav class="neumorphic-navbars" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up .8s ease-out forwards;
        animation-delay: 0.4s; margin-top: 20px; width: 71%; height: 60px; margin-left: 315px; z-index: 10;">
          <!-- Replace these router-links or hrefs with methods that filter based on status -->
         

          <span class="nav-item">
            <a href="/addtocart" class="nav-link" style="font-weight:700; color:darkorange;" >Shopping Cart</a>
          </span>
          <span v-if="selectedCheckboxesComputed.length > 0" class="nav-item">
            <a @click="selectAllItems" class="nav-link" style="font-weight:400; color:rgb(0, 0, 0); margin-right:350px;">Select All</a>
          </span>

          <a style="margin-left: 190px; margin-right: 20px;" class="navbar-brand">Product | <span>Status.</span></a>
        </nav>


        <!-- empty cart container -->
        <div v-if="filteredInfos.length === 0" class="text-center" style="  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up .8s ease-out forwards;
        animation-delay: 0.4s; margin-top: 70px; margin-left:230px;">
        <span class="loader" ref="spinGif" style="display: none;"></span>
          <!-- <img :src="require('../../../public/img/spin.gif')" style="width: 60px; height: 60px; display: none;" ref="spinGif"> -->
          <img :src="require('../../../public/img/3cart.gif')" style="width: 55px; height: 55px;" ref="cartGif">
         
          <p style="font-weight: 600; margin-top:10px; margin-bottom:30px;">your shopping cart is empty.</p>
          <a @click="goShoppingNow" class="neumorphic-button" style="text-decoration: none; border-radius: 3px;  width: 200px; background-color: rgb(248, 53, 53); color: white; transition: background-color 0.3s;" onmouseover="this.style.backgroundColor='darkred'" onmouseout="this.style.backgroundColor='rgb(248, 53, 53)'">
            Go Shopping Now
          </a>
        </div>
        
        <!-- end of empty cart container -->






        <!-- check out box -->
        <nav class="neumorphic-navbars checkout-box" style="  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up .8s ease-out forwards;
        animation-delay: 0.5s; position: fixed; bottom: 20px; left: 40px; width: 19%; height: 150px; z-index: 10;">
          <!-- ... (existing content) ... -->
          <div class="container">
            <div class="row">
              <div class="col-12">
                <button
                @click="openDialogs"
                  
                  class="neumorphic-button checkout-button"
                  :disabled="!hasSelectedItems"
                  style="background-color: green; color: white; margin-left: 35px; margin-top: 30px; width: 158px;"
                  onmouseover="this.style.backgroundColor='darkgreen'; this.style.color='white';"
                  onmouseout="this.style.backgroundColor='green'; this.style.color='white';"
                >
                  Check out
                </button>  
              </div>
            </div>
            
                           
          
            <div class="row">
              <div class="col-12">
                <span class="nav-item">
                  <h1 class="nav-link" style="font-weight:400; margin-left:35px; margin-top:20px; color:rgb(0, 0, 0);">
                    Total ({{ selectedCheckboxesComputed.length }} item): ₱{{ calculateTotalPrice() }}
                  </h1>
                </span>                        
              </div>
            </div>
          </div>
          
        
          <!-- <a style="margin-left: 190px; margin-right: 20px;" class="navbar-brand">Product | <span>Status.</span></a> -->
        </nav>
      
    </div>




                <!--products container-->
                <div>
                  <div v-for="filteredInfo in filteredInfos" :key="filteredInfo.id" class="container" style="  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
                  animation: fade-up .8s ease-out forwards;
                  animation-delay: 0.4s; margin-top: 20px; width:820%">
                    <input
                    type="checkbox"
                    :id="'checkbox-' + filteredInfo.id"
                    class="product-checkbox"
                    style="position: absolute; margin-top: 18px; margin-left: 220px;"
                    v-model="selectedCheckboxes"
                    :value="filteredInfo.id"
                    @change="updateSelectAllButton"
                  >
                    <nav class="neumorphic-navbars" style="width: 950px; margin-left: 200px; z-index: 10;">
                      <ul>
                        <li>
                          <br>
                          <div>
                            <asd><span style="color:rgb(13, 109, 19); margin-left:740px;"><i class="fas fa-box custom-icon"></i>
                              &nbsp;&nbsp;&nbsp;in-cart product.</span></asd>
                          </div>
            
                          <div style="margin-bottom: 20px;"> 
                            <an  v-if="filteredInfo.image">
                              <img :src="filteredInfo.image" class="img-fluids" style="max-width: 140px; max-height: 140px;" readonly>
                              <span style="margin-right: 140px; margin-left: 80px;">Product:{{ filteredInfo.prod_name }}</span> 
                              <span style="margin-right: 140px;">Quantity: 
                                <a class="neumorphic-button" @click="decrementQuantity(filteredInfo)" style="margin-right: 5px; width:17px;">-</a>
                                {{ filteredInfo.quantity }}
                                <a class="neumorphic-button" @click="incrementQuantity(filteredInfo)" style="margin-left: 5px; width:17px;">+</a>
                              </span>
                              <span>Total: ₱{{ parseFloat(filteredInfo.total).toFixed(0) }}</span>
                              <span v-if="!hideStatus" class="product-info">{{ status }}</span> 
                              <span v-if="!hideToken" class="product-info">{{ token }}</span>
                              <span v-if="!hideCategory" class="product-info">{{ category_id }}</span>
                         
                            </an>
                            <div>
                              
                                <button @click="openDialog(filteredInfo.category_id)" class="neumorphic-button" style="margin-left:450px; width: 200px;">
                                  <i class="fas fa-search custom-icon"></i>&nbsp;&nbsp;Find Similar
                                </button> &nbsp;&nbsp;
                                
                              <!-- <button @click="buyagain(filteredInfo.id)" class="neumorphic-button" style="margin-left:450px; width: 200px;"><i class="fas fa-phone custom-icon"></i> &nbsp;&nbsp;Buy Again</button> &nbsp;&nbsp; -->
                              <button @click="deletehistory(filteredInfo.id)"   class="neumorphic-button" style="width: 200px; background-color:rgb(248, 53, 53); color:white;">
                                Delete</button>
                            </div>
                          </div>
                        </li>
                      </ul>
                    </nav>
                  </div>
                </div>
                


                <!--kelangan walo lang makikita-->
                <v-dialog v-model="dialogs" max-width="75%">
                  <v-card>
                    <v-card-title class="headline" style="margin-left: 99px;"></v-card-title>
                    <v-card-text>
                      <div class="row justify-content-center">
                        <div v-for="(product, index) in getprods.slice(0, 8)" :key="product.id" class="col-lg-3 col-md-6 mb-4">
                          <!-- Product Card -->
                          <div class="room-item text-center">
                            <img :src="product.image" alt="" style="width: 100px; height: 100px;">
                            <div class="ri-text" >
                              <h6>{{ product.prod_name }}</h6>
                              <h6 style="display: none;">{{ product.stock }}</h6>
                              <h6 style="display: none;">{{ product.category_id }}</h6>
                              <p style="font-size: 13px;">Unit Price: ₱{{ product.unit_price }}</p>
                              <p style="font-size: 13px;"><span style="font-size: 13px;">Available Size:</span> {{ getSizeName(product.size_id) }}</p> 
                              <button class="neumorphic-button" style="font-weight:400;opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s; width: 99px; background-color:rgb(43, 42, 42); color:white; border-radius:4px; height:33px; " @click="preOrder(product)"><span style="font-size: 13px; position:absolute; top:25%; left:25%;">Pre order</span></button>
                              <!-- @click="preOrder(product)" function ng preorder button -->
                            </div>
                          </div>
                        </div>
                      </div>
                    </v-card-text>
                    <v-card-actions>
                      <v-btn @click="closeDialog" color="primary">Cancel</v-btn>
                      <v-btn @click="submitReason" color="primary" small>
                        Submit
                      </v-btn>
                    </v-card-actions>
                  </v-card>
                </v-dialog>


                <v-dialog v-model="dialogss" max-width="76%">
                  <v-card>
                    <v-card-title class="headline" style="margin-left: 99px;"></v-card-title>
                    <v-card-text>

                      <nav class="neumorphic-navbars" style="margin-top: 1px; width: 950px; height: 60px; margin-left: 10px; z-index: 10;">
                        <!-- Replace these router-links or hrefs with methods that filter based on status -->
                       
              
                        <span class="nav-item" style="width: 200px;">
                          <a1 href="#" class="nav-link" style="font-weight:700; color:darkorange;margin-left:10px;" ><i class="fas fa-map-marker-alt custom-icon"></i>&nbsp;&nbsp;&nbsp;Delivery Address</a1>
                        </span>

                        <span class="nav-item" style="width: 700px; position:absolute;">
                          <a2 style="margin-left:170px;">{{ info[0].address }}</a2><br>
                        </span>
                        <!-- <span v-if="selectedCheckboxesComputed.length > 0" class="nav-item">
                          <a @click="selectAllItems" class="nav-link" style="font-weight:400; color:rgb(0, 0, 0); margin-right:350px;">Select All</a>
                        </span> -->
                        <a1 style="position: absolute; margin-left: 610px; margin-right: 10px; color:red" class="navbar-brand">Default</a1>
                        <a style="position: absolute; margin-left: 670px; margin-right: 10px;" class="navbar-brand">Change</a>
                        <a style="margin-left: 190px; margin-right: 20px;" class="navbar-brand">Order | <span>Summary.</span></a>
                      </nav>
              
              


                <div>
                  <div v-for="filteredInfo in filteredInfos" :key="filteredInfo.id" class="container" style="margin-top: 20px;">
                    <input
                      v-if="selectedCheckboxes.includes(filteredInfo.id)"
                      type="checkbox"
                      :id="'checkbox-' + filteredInfo.id"
                      class="product-checkbox"
                      style="position: absolute; margin-top: 18px; margin-left: 15px;"
                      v-model="selectedCheckboxes"
                      :value="filteredInfo.id"
                      @change="updateSelectAllButton"
                    >
                    
                    <!-- Only display the product card if the checkbox is checked -->
                    <div v-if="selectedCheckboxes.includes(filteredInfo.id)">
                      <nav class="neumorphic-navbars" style="width: 950px; z-index: 10;">
                        <ul>
                          <li>
                            <br>
                            <div>
                              <asd><span style="color:rgb(13, 109, 19); margin-left:580px;"><i class="fas fa-box custom-icon"></i>
                                &nbsp;&nbsp;&nbsp;We will be packing your parcel soon...</span></asd>
                            </div>
              
                            <div style="margin-bottom: 20px;"> 
                              <an  v-if="filteredInfo.image">
                                <img :src="filteredInfo.image" class="img-fluids" style="max-width: 140px; max-height: 140px;" readonly>
                                <span style="margin-right: 140px; margin-left: 20px; position:absolute; margin-top:60px;">Product:{{ filteredInfo.prod_name }}</span> 
                                <span style="margin-right: 140px; margin-left:350px; ">Quantity: 
                                  <a class="neumorphic-button" @click="decrementQuantity(filteredInfo)" style="margin-left:10px; margin-right: 5px; width:17px;">-</a>
                                <span > {{ filteredInfo.quantity }} </span>  
                                  <a class="neumorphic-button" @click="incrementQuantity(filteredInfo)" style="margin-left: 5px; width:17px;">+</a>
                                </span>
                                <span>Total: ₱{{ parseFloat(filteredInfo.total).toFixed(0) }}</span>
                                <span v-if="!hideStatus" class="product-info">{{ status }}</span> 
                                <span v-if="!hideToken" class="product-info">{{ token }}</span>
                                <span v-if="!hideCategory" class="product-info">{{ category_id }}</span>
                                <span v-if="!hideproduct_id" class="product-info">{{ category_id }}</span>
                               
                           
                              </an>
                              <div>
                                
                                  <button @click="openDialog(filteredInfo.category_id)" class="neumorphic-button" style="margin-left:450px; width: 200px;">
                                    <i class="fas fa-search custom-icon"></i>&nbsp;&nbsp;Find Similar
                                  </button> &nbsp;&nbsp;
                                  
                                <!-- <button @click="buyagain(filteredInfo.id)" class="neumorphic-button" style="margin-left:450px; width: 200px;"><i class="fas fa-phone custom-icon"></i> &nbsp;&nbsp;Buy Again</button> &nbsp;&nbsp; -->
                                <button @click="deletehistory(filteredInfo.id)"   class="neumorphic-button" style="width: 200px; background-color:rgb(248, 53, 53); color:white;">
                                  Change Item</button>
                              </div>
                            </div>
                          </li>
                        </ul>
                      </nav>
                    </div>
                  </div>
                </div>
                

                    </v-card-text>
                    <v-card-actions>
                      <button @click="closeDialogs"    class="neumorphic-button" style=" position:absolute; margin-left:30px; margin-bottom:30px; width: 130px; background-color:#f0f0f0; color:rgb(0, 0, 0);">
                        Cancel</button>
                      <button @click="updateStatusToPending"   class="neumorphic-button" style=" position:absolute; margin-left:510px; margin-bottom:30px; width: 200px; background-color:rgb(4, 134, 32); color:white;">
                        Pre order</button>
                      <h1 class="nav-link" style="font-weight:400; margin-left:750px; margin-top:5px; margin-bottom:35px; color:rgb(0, 0, 0);">
                        Total ({{ selectedCheckboxesComputed.length }} item): ₱{{ calculateTotalPrice() }}
                      </h1>
                    </v-card-actions>
                  </v-card>
                </v-dialog>


                <v-dialog v-model="dialogsss" persistent max-width="400">
                  <v-card>
                    <v-card-text>
                      <div class="text-center">
                        <p>  Your order has been successfully placed. </p>
                        <img :src="require('../../../public/img/check.gif')"  style="width: 120px; height: 120px;">
                      </div>
                    </v-card-text>
                    <v-card-actions>
                      <v-btn  style="margin-left:162px;"   color="primary" @click="closeDialogss" >OK</v-btn>
                    </v-card-actions>
                  </v-card>
                </v-dialog>

                
              </div>
              
</template>
<script>
import axios from 'axios';

export default {
  data() {
    return {  

      productData: { // Initialize productData object
      transaction_code: '', // Initialize transaction_code property
    },

      searchText: '',
      selectedCheckboxes: [], // Array to store IDs of selected checkboxes
      showSelectAllButton: false, // Control visibility of a button
      originalProds: [],
      getprods: [],
      sizes: [],
      size_id: '',
      isNavbarHidden: false,
      lastScrollTop: 0,
      inputValue: '',
      isActive: false,
      isProcessing: false,
      infos: [],
	    info: [],
      token: '',
      status: '',
      dialogs: false,
      dialogss: false,
      dialogsss: false,
      selectedReason: null,
      cancellationReasons: [
        'Need to change delivery address',
        'Seller is not responsive to my inquiries',
        'Others/Change of mind'
      ],
      hideStatus: false,
      selectedReason: null,
      selectedInfo: null,
      
    };
  },
  mounted() {
	this.getInfo(); 
  this.getOrder();
  this.getprod();

  },
  created() {
	this.token = sessionStorage.getItem('jwt');
  if (this.token) {
    this.getInfo();
  } else {
    // Handle the case where token is not available in local storage
    console.error('JWT token not found in local storage');
  }
  this.getInfo();
},
computed: {
  hasSelectedItems() {
      return this.selectedCheckboxes.length > 0;
    },
  selectedCheckboxesComputed() {
    return this.selectedCheckboxes;
  },
  filteredInfos() {
  // Filter the 'infos' array based on the token in session storage and status equals 'Approved'
  return this.infos.filter(info => {
    const isTokenMatch = info.token === this.token;
    const isStatusMatch = info.status === 'cart';
    const isNameMatch = info.prod_name.toLowerCase().includes(this.searchText.toLowerCase());

    return isTokenMatch && isStatusMatch && isNameMatch;
  });
},

    selectedCheckboxesComputed() {
      return this.selectedCheckboxes;
    },
  },
  
  methods: {
    
    generateTransactionCode() {
    // Generate a random transaction code (for example purposes)
    const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
    const length = 8;
    let transactionCode = '';
    for (let i = 0; i < length; i++) {
      const randomIndex = Math.floor(Math.random() * chars.length);
      transactionCode += chars.charAt(randomIndex);
    }
    return transactionCode;
  },
   
      preOrder(product) {
  const { image, prod_name, unit_price, size_id, stock, id, category_id, product_description, ships, } = product; //category_id di pa tapos iretrieve
  const transactionCode = this.generateTransactionCode();
  this.$router.push({
    name: 'productrequest',
    params: {
      image,
      prod_name,
      unit_price,
      category_id,
      size_id,
      stock, // Include stock parameter
      id,
      transaction_code: transactionCode,
      product_description,
      ships,
      
    }
  });
},


    updateSearch() {
      // Triggered on every input change in the search input
      // Update searchText and trigger the computed property update
      this.searchText = event.target.value;
    },
    incrementQuantity(filteredInfo) {
    // Convert the current quantity to a number and add 1  dipa ayos dapat max quantity ay nakabase sa stock value ng product
    filteredInfo.quantity = +filteredInfo.quantity + 1;

    // Update the total value based on the new quantity
    this.updateTotalValue(filteredInfo);

    // Force a re-render to update the UI immediately
    this.$forceUpdate();
  },

  decrementQuantity(filteredInfo) {
    // Ensure the quantity does not go below 1
    if (filteredInfo.quantity > 1) {
      // Retrieve the current quantity value
      let currentQuantity = filteredInfo.quantity;

      // Decrement the quantity of the selected product
      currentQuantity -= 1;

      // Update the quantity value
      filteredInfo.quantity = currentQuantity;

      // Update the total value based on the new quantity
      this.updateTotalValue(filteredInfo);

      // Force a re-render to update the UI immediately
      this.$forceUpdate();
    }
  },
  updateTotalValue(filteredInfo) {
    // Calculate the new total value based on quantity and unit price
    filteredInfo.total = (filteredInfo.quantity * filteredInfo.unit_price);
  },
    goShoppingNow() {
    // Show spin.gif and hide 3cart.gif
    this.$refs.spinGif.style.display = 'block' ;
    this.$refs.spinGif.style.marginLeft = '530px';
    this.$refs.cartGif.style.display = 'none';

    // Redirect after 3 seconds
    setTimeout(() => {
      this.$router.push('/userproducts'); // Redirect to /userproducts route
    }, 3000);
  },

async updateStatusToPending() {
  try {
    const confirmed = window.confirm('Are you sure you want to proceed with the checkout?');

    if (confirmed) {
      // Loop through the selectedCheckboxes array and update the status, quantity, and total of selected items to 'pending'
      for (const id of this.selectedCheckboxes) {
        const selectedItem = this.filteredInfos.find(item => item.id === id);

        // Ensure the selectedItem exists and has quantity and total properties
        if (selectedItem && selectedItem.hasOwnProperty('quantity') && selectedItem.hasOwnProperty('total')) {
          const response = await axios.post(`/updateOrderStatus/${id}`, {
            status: 'pending',
            quantity: selectedItem.quantity,  // Include the quantity in the request payload
            total: selectedItem.total,        // Include the total price in the request payload
          });

          if (response.status === 200) {
            // You might want to update the UI or perform other actions upon successful update
            console.log(`Item with ID ${id} status, quantity, and total updated to pending`);
          } else {
            console.error(`Error updating status for item with ID ${id}`);
          }
        }
      }

      // Clear the selectedCheckboxes array after updating the status
      this.selectedCheckboxes = [];
      this.getOrder(); 
      this.dialogss = false;
      this.dialogsss = true;
    } else {
      console.log('Checkout canceled');
    }
  } catch (error) {
    console.error('Error during checkout:', error);
  }
},


  calculateTotalPrice() {
  let totalPrice = 0;
  this.filteredInfos.forEach(info => {
    if (this.selectedCheckboxes.includes(info.id)) {
      totalPrice += parseFloat(info.total); // Assuming 'info.total' holds the item's price
    }
  });
  return totalPrice.toFixed(2); // To display the total price with 2 decimal places
},

    updateSelectAllButton() {
      // Check if at least one checkbox is selected
      this.showSelectAllButton = this.selectedCheckboxes.length > 0;
    },
    selectAllItems() {
      if (this.filteredInfos.length === this.selectedCheckboxes.length) {
        // If all checkboxes are already checked, uncheck all
        this.selectedCheckboxes = [];
      } else {
        // Otherwise, check all checkboxes
        this.selectedCheckboxes = this.filteredInfos.map(info => info.id);
      }

      // Call the method to update the 'Select All' button visibility
      this.updateSelectAllButton();
    },
   async deletehistory(id) {
  try {
    const confirmed = window.confirm('Are you sure you want to delete this record?');

    if (confirmed) {
      const userInput = prompt('Type "okay" to confirm:');
      if (userInput && userInput.trim().toLowerCase() === 'okay') {
        const response = await axios.post(`/deleteprod/${id}`, {
  status: 'deleted',
});


        if (response.status === 200) {
          this.getOrder(); // Refresh orders after status update
        } else {
          console.error('Error updating order status');
        }
      } else {
        console.log('No changes were made.');
      }
    } else {
      console.log('No changes were made.');
    }
  } catch (error) {
    console.error('Error updating order status:', error);
  }
},

openDialogss() {
      this.dialogsss = true; // Open the dialog
    },  
    closeDialogss() {
      this.dialogsss = false; // Close the dialog
    },
openDialogs() {
      this.dialogss = true; // Open the dialog
    },  
    closeDialogs() {
      this.dialogss = false; // Close the dialog
    },

openDialog(categoryId) {
      this.dialogs = true; // Open the dialog

      // Filter products based on category_id from originalProds
      this.getprods = this.originalProds.filter(
        (product) => product.category_id === categoryId
      );
    },  

    closeDialog() {
      this.dialogs = false; // Close the dialog
    },
    async getOrder() {
  try {
    const response = await axios.get('getOrder');
    this.infos = response.data;
    // Set hideToken to true after fetching notifications
    this.hideToken = true;
  } catch (error) {
    console.error(error);
  }
},
async getprod() {
      try {
        const response = await axios.get('getprod');
        this.getprods = response.data;
        this.originalProds = [...response.data]; // Store original products
        // Set hideToken to true after fetching notifications
        this.hideToken = true;
      } catch (error) {
        console.error(error);
      }
    },
getSizeName(sizeId) {
      const size = this.sizes.find(size => size.size_id === sizeId);
      return size ? size.item_size : 'Unknown';
    },
    async getItemSizes() {
      try {
        const response = await axios.get('getsize');
        this.sizes = response.data;
      } catch (error) {
        console.log(error);
      }
    },
    toggleDropdown() {
    const menu = document.querySelector('.menu-item');
    menu.classList.toggle('active');
  },
  async getInfo() {
    try {
      const response = await axios.get(`getUserData/${this.token}`);
      this.info = response.data; // Assuming response.data is an object/array of user data
    } catch (error) {
      console.error(error);
      // Handle the error case, such as showing a message to the user
    }
  },
  handleScroll() {
      const currentScroll = window.pageYOffset || document.documentElement.scrollTop;

      if (currentScroll <= 0) {
        // At the top of the page
        this.isNavbarHidden = false;
      } else {
        // Scrolled down
        this.isNavbarHidden = true;
      }

      this.lastScrollTop = currentScroll <= 0 ? 0 : currentScroll;
    },
    activateFinder() {
      this.isActive = true;
    },
    deactivateFinder() {
      if (this.inputValue.length === 0) {
        this.isActive = false;
      }
    },
    submitForm() {
      this.isProcessing = true;
      this.isActive = false;
      this.$refs.icon.classList.remove('active');
      this.$refs.icon.classList.add('processing');
      this.inputValue = ''; // Clear input value

      setTimeout(() => {
        this.isProcessing = false;
        this.$refs.icon.classList.remove('processing');
        this.inputValue = ''; // Clear input value again

        if (this.inputValue.length > 0) {
          this.isActive = true;
          this.$refs.icon.classList.add('active');
        }
      }, 1000);
    },
  }
};
</script>

<style scoped>
.loader {
  width: 48px;
  height: 48px;
  display: inline-block;
  position: relative;
  transform: rotate(45deg);
}
.loader::before {
  content: '';  
  box-sizing: border-box;
  width: 24px;
  height: 24px;
  position: absolute;
  left: 0;
  top: -24px;
  animation: animloader 4s ease infinite;
}
.loader::after {
  content: '';  
  box-sizing: border-box;
  position: absolute;
  left: 0;
  top: 0;
  width: 24px;
  height: 24px;
  background: rgba(255, 94, 0, 0.85);
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.15);
  animation: animloader2 2s ease infinite;
}

@keyframes animloader {
  0% {
    box-shadow: 0 24px rgba(255, 255, 255, 0), 24px 24px rgba(255, 255, 255, 0), 24px 48px rgba(255, 255, 255, 0), 0px 48px rgba(255, 255, 255, 0);
  }
  12% {
    box-shadow: 0 24px white, 24px 24px rgba(255, 255, 255, 0), 24px 48px rgba(255, 255, 255, 0), 0px 48px rgba(255, 255, 255, 0);
  }
  25% {
    box-shadow: 0 24px white, 24px 24px white, 24px 48px rgba(255, 255, 255, 0), 0px 48px rgba(255, 255, 255, 0);
  }
  37% {
    box-shadow: 0 24px white, 24px 24px white, 24px 48px white, 0px 48px rgba(255, 255, 255, 0);
  }
  50% {
    box-shadow: 0 24px white, 24px 24px white, 24px 48px white, 0px 48px white;
  }
  62% {
    box-shadow: 0 24px rgba(255, 255, 255, 0), 24px 24px white, 24px 48px white, 0px 48px white;
  }
  75% {
    box-shadow: 0 24px rgba(255, 255, 255, 0), 24px 24px rgba(255, 255, 255, 0), 24px 48px white, 0px 48px white;
  }
  87% {
    box-shadow: 0 24px rgba(255, 255, 255, 0), 24px 24px rgba(255, 255, 255, 0), 24px 48px rgba(255, 255, 255, 0), 0px 48px white;
  }
  100% {
    box-shadow: 0 24px rgba(255, 255, 255, 0), 24px 24px rgba(255, 255, 255, 0), 24px 48px rgba(255, 255, 255, 0), 0px 48px rgba(255, 255, 255, 0);
  }
}

@keyframes animloader2 {
  0% {
    transform: translate(0, 0) rotateX(0) rotateY(0);
  }
  25% {
    transform: translate(100%, 0) rotateX(0) rotateY(180deg);
  }
  50% {
    transform: translate(100%, 100%) rotateX(-180deg) rotateY(180deg);
  }
  75% {
    transform: translate(0, 100%) rotateX(-180deg) rotateY(360deg);
  }
  100% {
    transform: translate(0, 0) rotateX(0) rotateY(360deg);
  }
}
    
.dialog-transition-enter-active,
.dialog-transition-leave-active {
  transition: opacity 0.5s;
}

.dialog-transition-enter, 
.dialog-transition-leave-to /* .dialog-transition-leave-active in <2.1.8 */ {
  opacity: 0;
}
.neumorphic-navbars {

  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 10px 10px 30px #eeecec, -10px -10px 30px #ffffff;
  transition: top 0.3s;
}
.neumorphic-navbars a {
  color: rgb(14, 13, 13)262;
  text-decoration: none;
  padding: 8px 15px;
  border-radius: 3px;
  transition: all 0.3s ease;
}

/* Navbar link hover styles */
.neumorphic-navbars a:hover {
  background-color: #e9e1e1;
  box-shadow: 5px 5px 10px #bcbcbc, -5px -5px 10px #ffffff;
  color: #1b1b1b;
}

a[href="#"] {
  text-decoration: none;
  color: black;
}

.neumorphic-search {
    display: flex;
    align-items: center;
    border-radius: 5px;
    background-color: #fff;
    box-shadow: 10px 10px 30px #eeecec, -10px -10px 30px #ffffff;
    padding: 8px;
    height: 40px;
    margin-top: 35px; /* Adjust this margin as needed */
    margin-left: 70px; /* Adjust this margin as needed */
    width: 600px;
  }

  .search-input {
    height: 36px;
    margin-top: 2px;
    border: none;
    outline: none;
    flex: 1;
    padding: 8px;
    border-radius: 5px;
    box-shadow: inset 2px 2px 5px #c9c9c9, inset -2px -2px 5px #ffffff;
  }

  .search-button {
    background-color: #fff;
    border: none;
    outline: none;
    cursor: pointer;
    padding: 8px;
    border-radius: 5px;
    margin-left: 8px;
    margin-bottom: 12px;
    width: 40px;
    box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.1);
  }
</style>
