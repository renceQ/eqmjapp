<template>
<div style="background-color:rgb(245, 245, 245);">
    <div style="  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
    animation: fade-up 0.8s ease-out forwards; position: absolute; margin-top:160px; margin-left:90px; ">
      <img style="width:70px; height:70px; "  v-if="info.length > 0" :src="info[0].profile_picture" alt="Profile" class="profile-picture-navbar">
      <span v-if="info.length > 0" style="font-weight: 400;">
        <a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{{ info[0].showed_username }}</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color: darkorange;" href="/editprofiles"><i class="fas fa-pencil-alt"></i>&nbsp;&nbsp;&nbsp; Edit Profile</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color:black;" href="/orderhistory"><i class="fas fa-history custom-icon"></i>&nbsp;&nbsp;&nbsp; Order History</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color: black;" href="/toship_main"> <i class="fas fa-shopping-bag"></i>&nbsp;&nbsp;&nbsp; My Purchase</a>
        <br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color: rgb(0, 0, 0);" href="/addtocart"> <i class="fas fa-shopping-cart custom-icon"></i>  &nbsp;&nbsp;&nbsp;Shopping Cart</a>
      </span>
    </div>
    <div>

        <!-- <div class="neumorphic-search" style="margin-top: 170px; margin-left:315px;">
            <input type="text" placeholder="Search Product by name..." class="search-input" style="border: 0px;"/>
            <button style="position:absolute; margin-left:602px; width:49px; height: 49px; " class="search-button">
                <i class="fas fa-search"></i>
              </button>
          </div> -->
             
               
      
    
  
    </div>

<br><br><br><br><br>


                <!--products container-->
         
                <div>
                  <div class="container" style="   opacity: 0; /* Set initial opacity to 0 for fade-in effect */
                  animation: fade-up .8s ease-out forwards;
                  animation-delay: 0.2s;margin-top: 20px;">
                    <nav class="neumorphic-navbars" style="background-color:rgb(245, 245, 245);width: 945px; margin-left: 200px; z-index: 10;">
                      <ul>
                        <li>
                          <br>
                          <div>
                            
                          </div>
                          <div class="card mb-4 mb-xl-0" style="margin-top:8px; width: 880px;">
                            <div class="card-header">Profile Picture</div>

                            <form @submit.prevent="updateProfilePicture" style="margin-left: 1px;">
                              <div class="card-body text-center">
                                <img class="img-account-profile rounded-circle mb-2" v-if="selectedImage" :src="selectedImage" alt="" style="box-shadow: 10px 10px 30px #eeecec, -5px -5px 20px #ffffff;">
                                <img class="img-account-profile rounded-circle mb-2" v-else-if="info.length > 0" :src="info[0].profile_picture" alt="" style="box-shadow: 10px 10px 30px #eeecec, -5px -5px 20px #ffffff;">
                                <img class="img-account-profile rounded-circle mb-2" v-else :src="'path_to_default_image.jpg'" alt="" style="box-shadow: 10px 10px 30px #eeecec, -5px -5px 20px #ffffff;">
                                <div class="small font-italic text-muted mb-4">JPG or PNG no larger than 5 MB</div>
                                <input v-if="info.length > 0" class="form-control" id="inputLastName" type="hidden" placeholder="Enter your Address" v-model="info[0].id">
                                <input type="file" style="border: 0; width: 29%; border-radius: 5px; background-color: rgb(220, 220, 223)" class="neumorphic-button" accept="image/*" @change="updateEditImage" required><br>
                                <button type="submit" class="neumorphic-button" style="width: 200px; margin-top: 15px; margin-bottom: 10px;">Update Profile Picture</button>
                              </div>
                            </form>

                          </div>

                     
                <form @submit.prevent="updateProfile" style="  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
                animation: fade-up .8s ease-out forwards;
                animation-delay: 0.4s; margin-left: 1px;" >
            <div class="card mb-4" style="height:700px; width:880px;">
                <div class="card-header">Account Details</div>
                <div class="card-body">
                    <div style="margin-left: 10px;">
                      <div class="mb-3">
                        <label class="small mb-1" for="inputUsername">Username</label>
                        <input v-if="info.length > 0" class="form-control" id="inputUsername" type="text" placeholder="Enter your username" v-model="info[0].showed_username" required>
                      </div>
                
                      <div class="row gx-3 mb-3">
                        <div class="col-md-6">
                          <label class="small mb-1" for="inputFirstName">Contact</label>
                          <input v-if="info.length > 0" class="form-control" id="inputFirstName" type="text" placeholder="Enter your contact" v-model="info[0].contact" required>
                        </div>
                        <div class="col-md-6">
                          <label class="small mb-1" for="inputLastName">Address</label>
                          <input v-if="info.length > 0" class="form-control" id="inputLastName" type="text" placeholder="Enter your Address" v-model="info[0].address" required>
                        </div>
                      </div>
                
                      <div class="mb-3">
                        <label class="small mb-1" for="inputEmailAddress">Other Information</label>
                        <input class="form-control" id="inputEmailAddress" type="text" placeholder="Enter your other information" v-model="info[0].other_info" required>
                      </div>
                
                      <div class="row gx-3 mb-3">
                        <div class="col-md-6">
                          <label class="small mb-1" for="input_name">Name</label>
                          <input class="form-control" id="input_name" type="text" placeholder="Enter your name" v-model="info[0].legit_name" required>
                        </div>
                        <div class="col-md-6">
                          <label>Gender:</label>
                          <br>
                          <label style="margin-top: 8px; margin-left:10px;">
                            <input type="radio" v-model="info[0].gender" value="male" > Male
                          </label>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                          <label>
                            <input type="radio" v-model="info[0].gender" value="female" > Female
                          </label>
                        </div>
                      </div>
                      <button type="submit" class="neumorphic-button" style="width:220px; margin-top:10px; margin-left:300px; margin-bottom:10px;">Update Account Details</button>
                    
                    </div>
                  </div>
                </div>
              </form>
                       

                        </li>
                      </ul>  
                    </nav>
                    
                  </div>
                </div>

           


                <!--cancel modal-->
                <v-dialog v-model="dialogs" max-width="400px">
                  <v-card>
                    <v-card-title class="headline" style="margin-left: 99px;"></v-card-title>
                    <v-card-text>
                      <div class="text-center">
                        <p> Account details successfully updated </p>
                        <img :src="require('../../../public/img/check.gif')"  style="width: 120px; height: 120px;">
                      </div>
                    </v-card-text>
                    <v-card-actions>
                      <v-btn style="margin-left: 43%;" @click="closeDialog" color="primary">ok</v-btn>
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
      formData: null,
    imageInput: null,
      selectedGender: '',
      selectedImage: null,
        isNavbarHidden: false,
      lastScrollTop: 0,
      inputValue: '',
      isActive: false,
      isProcessing: false,
      infos: [],
	    info: [ {
          profile_picture: 'path_to_default_image.jpg',
          // other properties...
        }],
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
      image: null,
      
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
      return this.infos.filter(product => product.status !== 'deleted');
    },
  },

  methods: {
    updateEditImage(event) {
  const fileInput = event.target;
  const selectedFile = fileInput.files[0];

  if (selectedFile) {
    this.formData = new FormData();
    // Append the file to the form data
    this.formData.append('file', selectedFile);

    // Update selectedImage to reflect the selected file immediately
    const reader = new FileReader();
    reader.onload = (e) => {
      this.selectedImage = e.target.result;
    };
    reader.readAsDataURL(selectedFile);
  }
},
updateProfilePicture() {
  // Check if there is a file selected for uploading
  if (this.formData) {
    // Get the user ID
    const userId = this.info.length > 0 ? this.info[0].id : null;

    // Ask for confirmation before proceeding
    const confirmed = window.confirm('Are you sure you want to update your profile picture?');

    if (confirmed) {
      // User confirmed, proceed with the update
      // Example: Use axios to make an HTTP request to send the data
      axios.post(`updateProfilePicture/${userId}`, this.formData)
        .then(response => {
          // Handle the response, e.g., update UI or show a success message
          console.log('Profile picture updated successfully', response.data);
          
          // Optionally, you can update the info array with the new profile picture path
          if (this.info.length > 0) {
            this.info[0].profile_picture = response.data.newProfilePicturePath;
           
          }
          window.location.reload();
         
        })
        .catch(error => {
          // Handle the error, e.g., show an error message
          console.error('Error updating profile picture', error);
        });
    } else {
      // User canceled the update
      console.log('Profile picture update canceled.');
    }
  } else {
    // No file selected, show a message or handle accordingly
    console.warn('No file selected for profile picture update.');
  }
},


async updateProfile() {
  try {
    // Ask for confirmation before proceeding
    const confirmed = window.confirm('Are you sure you want to update your account details?');

    if (!confirmed) {
      console.log('Profile update canceled.');
      return;
    }

    const userId = this.info[0].id; // Assuming you have access to the user's ID
    const formData = new FormData();

    // Add other properties
    formData.append('showed_username', this.info[0].showed_username);
    formData.append('contact', this.info[0].contact);
    formData.append('address', this.info[0].address);
    formData.append('other_info', this.info[0].other_info);
    formData.append('legit_name', this.info[0].legit_name);
    formData.append('gender', this.info[0].gender);

    const response = await axios.post(`/updateProfile/${userId}`, formData, {
      headers: {
        'Content-Type': 'multipart/form-data',
      },
    });

    if (response.status === 200) {
      this.dialogs = true;
      console.log('Profile updated successfully');
    } else {
      console.error('Error updating profile');
    }
  } catch (error) {
    console.error('Error updating profile:', error);
  }
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

<style scoped>
.button-container {
  display: flex;
}
.active {
  background-color: lightblue;
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

/* Navbar link hover style=scope's */
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
  body{margin-top:20px;
background-color:#f2f6fc;
color:#69707a;
}
.img-account-profile {
    height: 10rem;
}
.rounded-circle {
    border-radius: 50% !important;
}
.card {
    box-shadow: 0 0.15rem 1.75rem 0 rgb(33 40 50 / 15%);
}
.card .card-header {
    font-weight: 500;
}
.card-header:first-child {
    border-radius: 0.35rem 0.35rem 0 0;
}
.card-header {
    padding: 1rem 1.35rem;
    margin-bottom: 0;
    background-color: rgba(33, 40, 50, 0.03);
    border-bottom: 1px solid rgba(33, 40, 50, 0.125);
}
.form-control, .dataTable-input {
    display: block;
    width: 100%;
    padding: 0.875rem 1.125rem;
    font-size: 0.875rem;
    font-weight: 400;
    line-height: 1;
    color: #69707a;
    background-color: #fff;
    background-clip: padding-box;
    border: 1px solid #c5ccd6;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    border-radius: 0.35rem;
    transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}

.nav-borders .nav-link.active {
    color: #0061f2;
    border-bottom-color: #0061f2;
}
.nav-borders .nav-link {
    color: #69707a;
    border-bottom-width: 0.125rem;
    border-bottom-style: solid;
    border-bottom-color: transparent;
    padding-top: 0.5rem;
    padding-bottom: 0.5rem;
    padding-left: 0;
    padding-right: 0;
    margin-left: 1rem;
    margin-right: 1rem;
}
</style>