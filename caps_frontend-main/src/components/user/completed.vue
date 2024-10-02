<template>
  <div style="position:absolute;background-color:rgb(245, 245, 245); width:100%;height:2000px;">
    <div style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
    animation: fade-up 0.8s ease-out forwards; position: absolute; margin-top:160px; margin-left:90px; ">
      <img style="width:70px; height:70px; "  v-if="info.length > 0" :src="info[0].profile_picture" alt="Profile" class="profile-picture-navbar">
      <span v-if="info.length > 0" style="font-weight: 400;">
        <a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{{ info[0].showed_username }}</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color: black;" href="/editprofiles"><i class="fas fa-pencil-alt"></i>&nbsp;&nbsp;&nbsp; Edit Profile</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color: black;" href="/orderhistory"><i class="fas fa-history custom-icon"></i>&nbsp;&nbsp;&nbsp; Order History</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color:darkorange;" href="/toship_main"> <i class="fas fa-shopping-bag"></i>&nbsp;&nbsp;&nbsp; My Purchase</a><br>
        <a style="position:absolute; margin-top:30px; text-decoration: none; color: rgb(0, 0, 0);" href="/addtocart"> <i class="fas fa-shopping-cart custom-icon"></i>  &nbsp;&nbsp;&nbsp;Shopping Cart</a>
      </span>
    </div>
    <div>

        <div class="neumorphic-search" style=" height:50px; margin-top: 150px;  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up .8s ease-out forwards;
        animation-delay: 0.2s;  margin-left:315px;">
          <input
          v-model="searchInput"
          @input="performSearch"
          type="text"
          placeholder="Search Product by name..."
          class="search-input"
          style="margin-top:8px;border: 0px;"
        />
            <button style="position:absolute;margin-top:8px; margin-left:602px; width:49px; height: 49px; " class="search-button">
                <i class="fas fa-search"></i>
              </button>
              <a href="/addtocart" style="position:absolute; margin-top:8px;margin-left:660px; width:49px; height: 49px; color: black;"  class="search-button">
                <i style="margin-left:7px; margin-top:8px;" class="fas fa-shopping-cart custom-icon"></i>
                </a>
          </div>
             
               
      
    
        <nav class="neumorphic-navbars" style="  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up .8s ease-out forwards;
        animation-delay: 0.4s; margin-top: 20px; width: 950px; height: 60px; margin-left: 315px; z-index: 10;">
          <!-- Replace these router-links or hrefs with methods that filter based on status -->
         
          <span class="nav-item">
            <a href="toship_main" class="nav-link" >To Ship</a>
          </span>
          <span class="nav-item">
            <a href="torecieve_main" class="nav-link">To Receive</a>
          </span>
          <span class="nav-item">
            <a  href="completed_main" class="nav-link" style="font-weight:700; color:darkorange">Recieved</a>
          </span>
          <span class="nav-item">
            <a href="cancel_main" class="nav-link">Returns and Cancellation</a>
          </span>
          <a style="margin-left: 190px; margin-right: 20px;" class="navbar-brand">Product | <span>Status.</span></a>
        </nav>
      
                </div>




                <!--products container--> <!--filtered container-->
                <div>
                  <div v-for="filteredInfo in filteredInfos" :key="filteredInfo.id" class="container" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
                  animation: fade-up .8s ease-out forwards;
                  animation-delay: 0.5s; margin-top: 20px;">
                    <nav class="neumorphic-navbars" style="width: 950px; margin-left: 200px; z-index: 10;">
                      <ul>
                        <li>
                          <br>
                          <div>
                           <asd><span style="color:rgb(13, 109, 19); margin-left:650px;"><i class="fas fa-truck custom-icon"></i>&nbsp;&nbsp;&nbsp;Parcel has been delivered...</span></asd>
                          </div>
            
                          <div style="margin-bottom: 20px;"> 
                            <an  v-if="filteredInfo.image">
                              <img :src="filteredInfo.image" class="img-fluids" style="max-width: 140px; max-height: 140px;" readonly>
                              <span style="margin-right: 140px; margin-left: 80px;">Product:{{ filteredInfo.prod_name }}</span> 
                              <span style="margin-right: 140px;">Quantity:{{ filteredInfo.quantity }}</span> 
                              <span >Total: ₱{{ filteredInfo.total }}</span>
                              <span v-if="!hideStatus" class="product-info">{{ status }}</span> 
                              <span v-if="!hideToken" class="product-info">{{ token }}</span>
                            </an>
                            <div>
                              <button @click="openModal" class="neumorphic-button" style="margin-left:30px;width: 200px;"><i class="fas fa-shopping-cart custom-icon"></i>&nbsp;&nbsp;Buy Again</button> &nbsp;&nbsp;
                              <button @click="openDialog(filteredInfo)" class="neumorphic-button" style="margin-left:5px; width: 200px; background-color:rgb(240, 206, 14); color:white;">
                                <i class="fas fa-star custom-icon"></i> Rate
                              </button>
                              &nbsp;&nbsp;&nbsp;

                              <button @click="openModal" class="neumorphic-button" style="width: 200px;"><i class="fas fa-phone custom-icon"></i> &nbsp;&nbsp;Contact Seller</button> &nbsp;&nbsp;
                              <button @click="deletehistory(filteredInfo.id)" class="neumorphic-button" style="width: 200px; background-color:rgb(248, 53, 53); color:white;"><i class="fas fa-trash-alt custom-icon"></i>
                                Delete</button>
                            </div>
                          </div>
                        </li>
                      </ul>
                    </nav>
                  </div>
                </div>
                


              
                <!-- review dialog-->
<v-dialog v-model="dialogs" max-width="500px">
  <v-card>
    <v-card-title class="headline" style="margin-left: 160px;">Write a Review</v-card-title>
    <v-card-text>
      <div v-if="selectedRecord">
    
        <img :src="selectedRecord.image" alt="Product Image" class="img-fluids" style="max-width: 100px; max-height: 100px;">
        <span style="margin-right: 140px; margin-top:30px;position:absolute;margin-left: 40px; width:70px;">Product:<br> {{ selectedRecord.prod_name }}</span>
        <span style="display: none;">Product:<br> {{ selectedRecord.product_id }}</span>
        <span style="margin-right: 140px; margin-top:30px; margin-left:140px;position:absolute; width:100px;">Quantity: <br> &nbsp;&nbsp;&nbsp; &nbsp;{{ selectedRecord.quantity }}</span>
        <span  style="margin-right: 140px;margin-left: 250px; margin-top:30px; position:absolute;">Total: ₱{{ selectedRecord.total }}</span>
        <textarea ref="reviewTextarea" class="search-input" placeholder="  What would you recommend this product to others" v-model="reviewText" rows="1" style="height:100px; margin-top: 30px; width: 100%; padding: 8px;" required></textarea>
        <a v-if="shouldShowUsername">{{ info[0].showed_username }}</a><br>
        <a v-if="shouldShowUsername">{{ info[0].profile_picture }}</a>

        <div style="display: flex; align-items: center;">
          <v-rating v-model="rating" label="Rate the product" :max="5" style="color: rgb(255, 255, 0); "></v-rating>
          <div style="margin-left: 50px; color: rgb(0, 0, 0)5, 255, 255);">{{ getRatingMessage() }}</div>
        </div>

        <v-btn  style="margin-left:400px; position:absolute; margin-top:15px; " icon @click="openFilePicker">
          <i class="fas fa-camera"></i>
        </v-btn>
        <input type="file" ref="fileInput" style="display: none " multiple @change="handleFileChange" />
        
        <div style="display: flex; flex-wrap: wrap; margin-left:10px; height:90px;">
          <div v-for="(image, index) in selectedImages" :key="index" style="margin-right: 10px; position: relative;">
            <img :src="image" alt="Selected Image" style="max-width: 70px; max-height: 70px; margin-top:10px;" />
            <button class="close-button" style="background-color: none; margin-top:10px; margin-right:4px;" @click="removeImage(index)">x</button>
          </div>
        </div>

        <div>
          <input style="margin-left:5px; margin-top:3px;" type="checkbox" id="isAnonymous" ref="isAnonymous">
          <label style="margin-left:20px;" for="isAnonymous">Make review anonymous</label>
        </div>
      
      </div>
    </v-card-text>
    <v-card-actions>

      <div style="margin-bottom: 10px;">
        <button
        class="neumorphic-button"
        style="margin-left: 10px; width: 460px; background-color: rgb(49, 48, 48); color: white;"
        @click="validateAndSubmitReview"
    >
        &nbsp;&nbsp;submit
    </button>
      </div>
 
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
      reviewText: '', 
      shouldShowUsername: false, 
      rating: 0,
      isAnonymous: false,
      selectedImages: [],
      selectedRecord: null,
      searchInput: '',
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


  filteredInfos() {
      // Filter the 'infos' array based on the token in session storage and status equals 'Approved'
      let filteredArray = this.infos.filter(info => info.token === this.token && info.status === 'recieved');

      // Apply search filter if searchInput is not empty
      if (this.searchInput.trim() !== '') {
        const searchQuery = this.searchInput.toLowerCase();

        filteredArray = filteredArray.filter(info =>
          info.prod_name.toLowerCase().includes(searchQuery)
        );
      }

      return filteredArray;
    },
},
  methods: {
    async validateAndSubmitReview() {
    // Check if the textarea is empty
    if (!this.reviewText.trim()) {
        window.alert('Please provide a comment before submitting.');
        // Focus on the textarea to bring user attention
        this.$refs.reviewTextarea.focus();
        return;
    }

    // If the textarea is not empty, proceed to submit the review
    await this.submitReview();
},
//     async submitReview() {
//     try {
//         const filteredComment = this.filterBadWords(this.reviewText);

//         if (filteredComment === null) {
//             // If filteredComment is null, it means inappropriate words were found
//             window.alert('Please remove unnecessary words. Comment not saved.');
//             return;
//         }

//         const requestData = {
//             prod_name: this.selectedRecord.prod_name,
//             product_id: this.selectedRecord.product_id,
//             comment: filteredComment,
//             rate: this.getRatingMessage(),
//             first_image: this.selectedImages[0] || null,
//             second_image: this.selectedImages[1] || null,
//             third_image: this.selectedImages[2] || null,
//             isAnonymous: document.getElementById('isAnonymous').checked ? 'anonymous' : 'public',
//             username: this.info[0].showed_username,
//             profile_picture: this.info[0].profile_picture,
//         };

//         const response = await axios.post('/submitReview', requestData);

//         // Check if 'data' property exists before accessing it
//         const responseData = response?.data;

//         // Handle the response as needed
//         if (responseData) {
//             console.log('Review submitted successfully:', responseData);

//             // Close the dialog
//             this.dialogs = false;

//             // You can emit an event or perform other actions after successful submission
//             this.$emit('data-saved');
//             this.getInfo();

//             // Show success modal
//             $('#successModal').modal('show');
//         } else {
//             console.error('Unexpected response format:', response);
//         }
//     } catch (error) {
//         // Handle errors
//         console.error('Error submitting review:', error.response?.data || error.message);
//     }
// },
async submitReview() {
    try {
        const filteredComment = this.filterBadWords(this.reviewText);

        if (filteredComment === null) {
            window.alert('Please remove unnecessary words. Comment not saved.');
            return;
        }

        const imageBase64Data = await Promise.all(this.selectedImageFiles.map(file => {
            return file ? this.convertFileToBase64(file) : null;
        }));

        const requestData = {
            prod_name: this.selectedRecord.prod_name,
            product_id: this.selectedRecord.product_id,
            comment: filteredComment,
            rate: this.getRatingMessage(),
            first_image: imageBase64Data[0] || null,
            second_image: imageBase64Data[1] || null,
            third_image: imageBase64Data[2] || null,
            isAnonymous: document.getElementById('isAnonymous').checked ? 'anonymous' : 'public',
            username: this.info[0].showed_username,
            profile_picture: this.info[0].profile_picture,
        };

        const response = await axios.post('/submitReview', requestData);
        const responseData = response?.data;

        if (responseData) {
            console.log('Review submitted successfully:', responseData);
            this.dialogs = false;
            this.$emit('data-saved');
            this.getInfo();
            $('#successModal').modal('show');
        } else {
            console.error('Unexpected response format:', response);
        }
    } catch (error) {
        console.error('Error submitting review:', error.response?.data || error.message);
    }
},

convertFileToBase64(file) {
    return new Promise((resolve, reject) => {
        const reader = new FileReader();
        reader.onloadend = () => resolve(reader.result.split(',')[1]);
        reader.onerror = reject;
        reader.readAsDataURL(file);
    });
},
filterBadWords(comment) {
    const badWords = [
        'tangina mo', 'gago', 'bastos', 'puta', 'putang ina mo',
        'putanginamo', 'tanga', 'bobo', 'inaka', 'baluga',
        'gago', 'kinginamo', 'in@ka', 'tang ina mo', 'tanginamo', 'inamo', 'inamoka', 'bitch', 'fuck', 'fuckyou', 'fuck you', 'asshole', 'puke', 'tite', 'kipay', 'ulaga', 'puki', 'titi', 'uten', 
    ];

    const lowerCaseComment = comment.toLowerCase();

    for (const word of badWords) {
        // Use indexOf for case-insensitive matching
        if (lowerCaseComment.includes(word.toLowerCase())) {
            // Comment contains a forbidden word, show alert and do not save
            return null;
        }
    }

    // No forbidden words found, return the comment
    return comment;
},


    getRatingMessage() {
      switch (this.rating) {
        case 1:
          return 'Bad';
        case 2:
          return 'Poor';
        case 3:
          return 'Average';
        case 4:
          return 'Great';
        case 5:
          return 'Excellent';
        default:
          return '';
      }
    },
    openFilePicker() {
      this.$refs.fileInput.click();
    },
    handleFileChange(event) {
    const selectedFiles = event.target.files;
    this.selectedImages = [];
    this.selectedImageFiles = []; // Store File objects

    for (let i = 0; i < Math.min(selectedFiles.length, 3); i++) {
        const selectedFile = selectedFiles[i];
        const imageUrl = URL.createObjectURL(selectedFile);

        this.selectedImages.push(imageUrl);
        this.selectedImageFiles.push(selectedFile);
    }
},

    removeImage(index) {
      // Remove the selected image at the given index
      this.selectedImages.splice(index, 1);
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

    performSearch() {
    // This method is triggered on input change in the search box
    // It updates the filteredInfos array based on the search input
    // You can add additional logic here if needed

    // Trim leading and trailing whitespaces from the search input
    const searchQuery = this.searchInput.trim().toLowerCase();

    // Filter the 'infos' array based on the token in session storage and status equals 'recieved'
    let filteredArray = this.infos.filter(info => info.token === this.token && info.status === 'recieved');

    // Apply search filter if searchInput is not empty
    if (searchQuery !== '') {
      // Filter based on the product name
      filteredArray = filteredArray.filter(info =>
        info.prod_name.toLowerCase().includes(searchQuery)
      );

      // Additional logic: You can add more conditions to filter based on other properties
      // Example: Filter based on quantity, total, or any other property in 'info' object
      // filteredArray = filteredArray.filter(info =>
      //   info.quantity.toString().includes(searchQuery) ||
      //   info.total.toString().includes(searchQuery)
      // );
    }

    // Set the filtered array to update the UI
    this.filteredInfos = filteredArray;
  },

  openDialog(selectedRecord) {
    this.selectedRecord = selectedRecord;
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
    const response = await axios.get('getOrder');
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
.close-button {
  position: absolute;
  top: 0;
  right: 0;
 
  border: none;
  cursor: pointer;
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
