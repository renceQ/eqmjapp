<template>
  <div style="position:absolute;background-color:rgb(245, 245, 245); width:100%; height:2000px;">
    <div style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
    animation: fade-up 0.8s ease-out forwards; position: absolute; margin-top:160px; margin-left:90px; ">
      <img style="width:70px; height:70px; "  v-if="info.length > 0" :src="info[0].profile_picture" alt="Profile" class="profile-picture-navbar">
      <span v-if="info.length > 0" style="font-weight: 400;">
        <a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{{ info[0].showed_username }}</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color: black;" href="/editprofiles"><i class="fas fa-pencil-alt"></i>&nbsp;&nbsp;&nbsp; Edit Profile</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color:darkorange;" href="/orderhistory"><i class="fas fa-history custom-icon"></i>&nbsp;&nbsp;&nbsp; Order History</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color: black;" href="/toship_main"> <i class="fas fa-shopping-bag"></i>&nbsp;&nbsp;&nbsp; My Purchase</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color: rgb(0, 0, 0);" href="/addtocart"><i class="fas fa-shopping-cart custom-icon"></i>&nbsp;&nbsp;&nbsp;Shopping Cart</a>
      </span>
    </div>
    <div>

        <div class="neumorphic-search" style="  height:50px; margin-top: 150px;  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up .8s ease-out forwards;
        animation-delay: 0.2s; margin-left:315px;">
          <input v-model="searchText" @input="updateSearch" type="text" placeholder="Search Product by name..." class="search-input" style="margin-top:8px;border: 0px;"/>
          <button style="position:absolute; margin-left:602px; width:49px; height: 49px; margin-top:8px;" class="search-button">
            <i class="fas fa-search"></i>
          </button>
              <a href="/addtocart" style="margin-top:8px;position:absolute; margin-left:660px; width:49px; height: 49px; color: black;"  class="search-button">
                <i style="margin-left:7px; margin-top:8px;" class="fas fa-shopping-cart custom-icon"></i>
                </a>
          </div>
             
               
      
    
        <nav class="neumorphic-navbars" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up .8s ease-out forwards;
        animation-delay: 0.4s; margin-top: 20px; width: 950px; height: 60px; margin-left: 315px; z-index: 10;">
          <!-- Replace these router-links or hrefs with methods that filter based on status -->
         

          <span class="nav-item">
            <a href="/pending_main" class="nav-link" style="font-weight:400; color:rgb(14, 11, 9)" >Pending</a>
          </span>
          <span class="nav-item">
            <a href="/orderhistory" class="nav-link" style="font-weight:700; color:darkorange; margin-right:350px;" >Order History</a>
          </span>

          <a style="margin-left: 190px; margin-right: 20px;" class="navbar-brand">Product | <span>Status.</span></a>
        </nav>
      
    </div>




                <!--products container-->
                <div>
                  <div v-for="infos in filteredProducts" :key="infos.id" class="container" style="  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
                  animation: fade-up .8s ease-out forwards;
                  animation-delay: 0.5s; margin-top: 20px;">
                    <nav class="neumorphic-navbars" style="width: 950px; margin-left: 200px; z-index: 10;">
                      <ul>
                        <li>
                          <br>
                          <div>
                            <asd><span style="color:rgb(13, 109, 19); margin-left:730px;"><i class="fas fa-history custom-icon"></i>
                              &nbsp;&nbsp;&nbsp;Order History...</span></asd>
                          </div>
            
                          <div style="margin-bottom: 20px;"> 
                            <an  v-if="infos.image">
                              <img :src="infos.image" class="img-fluids" style="max-width: 140px; max-height: 140px;" readonly>
                              <span style="margin-right: 140px; margin-left: 80px;">Product:{{ infos.prod_name }}</span> 
                              <span style="margin-right: 140px;">Quantity:{{ infos.quantity }}</span> 
                              <span >Total: ₱{{ infos.total }}</span>
                              <span v-if="!hideStatus" class="product-info">{{ status }}</span> 
                              <span v-if="!hideToken" class="product-info">{{ token }}</span>
                            </an>
                            <div>

                                <button @click="deletehistory(infos.id)" class="neumorphic-button" style=" margin-left:650px; width: 200px; background-color:rgb(248, 53, 53); color:white;"><i class="fas fa-trash-alt custom-icon"></i>
                                    Delete</button>
                            </div>
                          </div>
                        </li>
                      </ul>
                    </nav>
                  </div>
                </div>
                


                <!--cancel modal-->
                <v-dialog v-model="dialogs" max-width="500px">
                  <v-card>
                    <v-card-title class="headline" style="margin-left: 99px;">Reasons for Order Cancellation</v-card-title>
                    <v-card-text>
                      <v-radio-group v-model="selectedReason">
                        <v-radio v-for="(reason, index) in cancellationReasons" :key="index" :label="reason" :value="reason"></v-radio>
                      </v-radio-group>
                    </v-card-text>
                    <v-card-actions>
                      <v-btn @click="closeDialog" color="primary">Cancel</v-btn>
                      <v-btn @click="submitReason" color="primary">Submit</v-btn>
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
      searchText: '',
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
      selectedReason: null,
      cancellationReasons: [
        'Need to change delivery address',
        'Seller is not responsive to my inquiries',
        'Others/Change of mind'
        // Add more reasons if needed
      ],
      hideStatus: false,
      selectedInfo: null,
      
    };
  },
  mounted() {
	this.getInfo(); 
  this.getOrder();
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
    filteredProducts() {
  // Filter products based on the status
  return this.infos.filter(product => {
    const isStatusMatch = product.status !== 'deleted';
    const isNameMatch = product.prod_name.toLowerCase().includes(this.searchText.toLowerCase());

    return isStatusMatch && isNameMatch;
  });
}

  },

  methods: {

    updateSearch() {
      // Triggered on every input change in the search input
      // Update searchText and trigger the computed property update
      this.searchText = event.target.value;
    },
    
   async deletehistory(id) {
  try {
    const confirmed = window.confirm('Are you sure you want to delete this record?');

    if (confirmed) {
      const userInput = prompt('Type "okay" to confirm:');
      if (userInput && userInput.trim().toLowerCase() === 'okay') {
        const response = await axios.post(`/updateNotifStatus/${id}`, {
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
    openDialog() {
      this.dialogs = true;
    },
    closeDialog() {
      this.dialogs = false;
      this.selectedReason = null; // Reset selected reason
    },
    submitReason() {
      // Handle submission of selected reason, e.g., emit an event or perform an action
      if (this.selectedReason) {
        // Perform action with selected reason
        console.log('Selected Reason:', this.selectedReason);
        // Reset selected reason and close dialog
        this.selectedReason = null;
        this.dialog = false;
      } else {
        // Inform user to select a reason
        console.log('Please select a reason.');
        // Optionally, you can provide a message to the user indicating they need to select a reason before submitting.
      }
    },
    async getOrder() {
  try {
    const response = await axios.get('getNotif');
    this.infos = response.data;
    // Set hideToken to true after fetching notifications
    this.hideToken = true;
  } catch (error) {
    console.error(error);
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

<style>

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
