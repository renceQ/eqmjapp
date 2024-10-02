<template>
  <div style="background-color:rgb(245, 245, 245);">
  <div class="container">
    <br><br><br><br><br><br>
    <!-- <h1 class="text-center" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
    animation: fade-up 0.8s ease-out forwards;font-size: 35px; font-weight:900; margin-left:50px;">AVAILABLE <span style="font-size: 30px; font-weight:100;">|</span>&nbsp;&nbsp; <span style="font-size:70px; font-weight:400; font-family: 'WindSong', cursive;">Products...</span></h1>
     --><br>
    <div class="row justify-content-center">
      <div class="col-md-6" style="position: absolute;left:-14%; margin-top:20px;">
        <label for="category_id" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up 0.8s ease-out forwards; font-weight:600;margin-left:-50px;font-family: 'Poppins', sans-serif;color:#000000;" class="label text-center">SEARCH FILTER</label><br>
        <div class="select-wrapper" style="margin-left:36%;" >
          <select v-model="category_id" @change="filterProducts" class="neumorphic-button" style="font-size:14px;font-weight:400;opacity: 0; animation: fade-up .8s ease-out forwards; animation-delay: 0.2s; width: 140px; background-color: rgb(255, 255, 255); color: rgb(0, 0, 0); border: none; border-radius: 3px; outline: none;">
            <option class="option" value="">All Categories</option>
            <option v-for="category in categories" :key="category.id" :value="category.id">
              {{ category.category_name }}
            </option>
          </select>
          
          <i class="fas fa-caret-down arrow-icon" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
          animation: fade-up .8s ease-out forwards;
          animation-delay: 0.2s; top:13px; position: absolute; margin-right:64px;"></i>
        </div>
      </div>
    </div>

   
    <div class="neumorphic-search" style=" height:50px;opacity: 0; /* Set initial opacity to 0 for fade-in effect */
    animation: fade-up .8s ease-out forwards;
    animation-delay: 0.2s; margin-top: -5px; margin-left:100px; position:absolute;box-shadow: 10px 10px 30px #eeecec, -1px -1px 10px #ffffff;">
      <input v-model="searchText" @input="updateSearch" type="text" placeholder="Search Product by name..." class="search-input" style="font-weight:400;margin-top:10px;border: 0px;"/>
      <button style="position:absolute; margin-left:602px; width:49px; height: 49px;margin-top:10px; " class="search-button">
        <i class="fas fa-search"></i>
      </button>
      <a href="/addtocart" style="margin-top:10px;position:absolute; margin-left:660px; width:49px; height: 49px; color: black;"  class="search-button">
        <i style="margin-left:7px; margin-top:8px;" class="fas fa-shopping-cart custom-icon"></i>
        </a>
      <div  style="position:absolute;right:-78%; margin-top:13px;">
        <button @click="previousPage" :disabled="currentPage === 1" class="search-button" style="height:46px; width:46px;margin-right:20px;">
          <i class="fa fa-chevron-left"></i>
        </button>
        <span style="font-family: 'Poppins', sans-serif; font-size:15px;">1{{ currentPage }}</span>
        <button @click="nextPage" :disabled="currentPage * pageSize >= info.length" class="search-button" style="height:46px; width:46px;margin-left:20px;">
          <i class="fa fa-chevron-right"></i>
        </button>
      </div>
          
      </div>
    <br>

    <div v-if="isLoading" style="left:700px;margin-top:190px; position:absolute;">
      <span class="loader"></span>
     <!-- <a style="margin-left:84px;"> Loading...</a> -->
    </div>

    <div v-else>
      <div class="row justify-content-start" style="position:absolute; margin-left:90px; margin-top:44px;">
          <div v-for="(product, index) in filteredProducts" :key="product.id" class="col-lg-3 col-md-6" style="width: 225px; margin-right:-6px;">
   
          <div class="room-item text-center" style="margin-bottom: 17px; height: 370px; background-color: #ffffff; border-radius: 10px; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2); text-align: left;">
      
          <img class="imgs" :src="product.image" alt="" style="  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
          animation: fade-up .8s ease-out forwards;
          animation-delay: 0.4s;width: 190px; height: 190px;margin-top:20px;">
          <div class="ri-text">
            <p style="opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s;  color:rgb(53, 53, 53); font-weight:100;  margin-top:15px; font-size:16px; margin-right:11%;" align-items>₱&nbsp;{{ product.unit_price }}<span style="font-size: 12px;font-family: 'Poppins', sans-serif; color:#7a7a7a; font-weight:300">&nbsp;/ new release</span></p>
            <h4 style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s;text-align: left;margin-left:26px;font-size:14.5px; margin-top:-2%; font-weight:500; color:#1b1b1b; font-family: 'Roboto', sans-serif;">{{ product.prod_name }}</h4>

            <h4 style="display: none;">{{ product.category_id }}</h4>

             <button class="neumorphic" style="font-weight:400;opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.4s; background-color:none;  height:43px; position:absolute; margin-top:-50px;margin-left:50px;" @click="preOrder(product)"><span style="font-size: 18px; position:absolute; "><i style="height:100px;" class="fas fa-shopping-bag"></i></span></button>
            <p style="font-weight:400;opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s; text-align:left; margin-left:26px; font-family: 'Poppins';font-size:13px;color:#575757;">Size: {{ getSizeName(product.size_id) }}</p>
  
            <p style="font-weight: 400; opacity: 0; animation: fade-up .8s ease-out forwards;font-weight:500; animation-delay: 0.2s; text-align: left; margin-left: 26px; font-family: 'Poppins'; font-size: 13px; margin-top: -19px;color: #3686ff;">
              Sold: {{ getTotalQuantitySold(product.id) }}
            </p>
            <p style="font-weight: 400; opacity: 0; animation: fade-up .8s ease-out forwards; animation-delay: 0.2s; text-align: left; margin-left: 24px; font-family: 'Poppins'; font-size: 15px; margin-top: -19px; color: #ffee00;">
              {{ getStarRating(getTotalQuantitySold(product.id)) }}
            </p>
            
              
           
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
   <!-- generated transact code -->
  <input type="hidden" v-model="productData.transaction_code">

    <!-- Footer Section -->
    <footer class="ftco-footer ftco-bg-dark ftco-section" style="margin-top: 2000px;">
      <div class="container">
        <div class="row mb-5">
          <div class="col-md">
            <div class="ftco-footer-widget mb-4">
              <h2 class="ftco-heading-2">QMJ IMAGES ENTERPRISES</h2>
              <p>Your best source of Photography and Videography
Sound and stage lights production.</p>
              <ul class="ftco-footer-social list-unstyled float-md-left float-lft mt-5">
                <li class="ftco-animate"><a href="#"><span class="icon-twitter"></span></a></li>
                <li class="ftco-animate"><a href="#"><span class="icon-facebook"></span></a></li>
                <li class="ftco-animate"><a href="#"><span class="icon-instagram"></span></a></li>
              </ul>
            </div>
          </div>
          <div class="col-md">
            <div class="ftco-footer-widget mb-4 ml-md-5">
              <h2 class="ftco-heading-2">Useful Links</h2>
              <ul class="list-unstyled">
                <li><a href="#" class="py-2 d-block">Speakers</a></li>
                <li><a href="#" class="py-2 d-block">Shcedule</a></li>
                <li><a href="#" class="py-2 d-block">Events</a></li>
                <li><a href="/userblog" class="py-2 d-block">Blog</a></li>
              </ul>
            </div>
          </div>
          <div class="col-md">
             <div class="ftco-footer-widget mb-4">
              <h2 class="ftco-heading-2">Privacy</h2>
              <ul class="list-unstyled">
                <li><a href="/bookevents" class="py-2 d-block">Book Event</a></li>
                <li><a href="/about" class="py-2 d-block">About Us</a></li>
                <li><a href="/contacts" class="py-2 d-block">Contact Us</a></li>
                <li><a href="/userServices" class="py-2 d-block">Services</a></li>
                <li><a href="/userproducts" class="py-2 d-block">Products</a></li>
              </ul>
            </div>
          </div>
          <div class="col-md">
            <div class="ftco-footer-widget mb-4">
              <h2 class="ftco-heading-2">Want more Answers to your Questions?</h2>
              <div class="block-23 mb-3">
                <ul>
                  <li><span class="icon icon-map-marker"></span><span class="text">km. 13 BIGA, Calapan, Philippines</span></li>
                  <li><a href="Tel:0947 406 2928"><span class="icon icon-phone"></span><span class="text">0947 406 2928</span></a></li>
                  <li><a href="mailto:qmjimages2018@gmail.com"><span class="icon icon-envelope"></span><span class="text">qmjimages2018@gmail.com</span></a></li>
                  
                </ul>
              </div>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-md-12 text-center">
  
          </div>
        </div>
      </div>
    </footer>
  </div>
  </template>
  

<!-- Your existing script and style sections remain unchanged -->



 <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {  
        isLoading: false,
        searchText: "",
        salesRecords: [],
        categories: [], 
        info: [],
      sizes: [],
      category_id: '',
      size_id: '',
      productData: { // Initialize productData object
      transaction_code: '', // Initialize transaction_code property
    }
      };
    },
    created() {
    this.getData();
  },

  computed: {
    filteredProducts() {
            if (!this.searchText) {
                return this.info;  // Return all products if search text is empty
            }

            // Filter products based on the search text
            const searchTextLower = this.searchText.toLowerCase();
            return this.info.filter(product => {
                // Adjust the condition based on your actual product name property
                return product.prod_name.toLowerCase().includes(searchTextLower);
            });
        },
  getTotalQuantitySold() {
    return function(productId) {
      const salesRecords = this.getFilteredSalesRecords(productId);
      return salesRecords.reduce((total, record) => total + parseInt(record.quantity), 0);
    };
  },
  getStarRating() {
      return function(quantitySold) {
        if (quantitySold === 0) {
          return ''; // 0 star
        } else if (quantitySold <= 20) {
          return '★'; // 1 stars
        } else if (quantitySold <= 40) {
          return '★★'; // 2 stars
        } else if (quantitySold <= 60) {
          return '★★★'; // 3 stars
        } else if (quantitySold <= 80) {
          return '★★★★'; // 4 stars
        } else {
          return '★★★★★'; // 5 stars
        }
      };
    },
},
    methods: {
      updateSearch() {
            // Set loading state to true
            this.isLoading = true;

            // Simulate loading for 3 seconds
            setTimeout(() => {
                // Reset loading state after 3 seconds
                this.isLoading = false;
            }, 1500);

            // Add any additional functionality you need for updating the search
        },
      getFilteredSalesRecords(productId) {
      return this.salesRecords.filter(record => record.product_id === productId);
    },
   async getSalesRecord() {
    try {
        const response = await axios.get(`getitemsales`);
        this.salesRecords = response.data; // Update salesRecords with fetched data
    } catch (error) {
        console.error(error);
    }
},

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


      
      async filterProducts() {
      try {
        if (this.category_id) {
          const response = await axios.get(`getProductsByCategory/${this.category_id}`);
          this.info = response.data;
        } else {
          this.getInfo(); // Fetch all products if no category selected
        }
      } catch (error) {
        console.error(error);
      }
    },
      async fetchCategories() {
        try {
          const response = await axios.get("getcat");
          this.categories = response.data; // Assuming response.data contains the categories array
        } catch (error) {
          console.error(error);
        }
      },
      async getData() {
      try {
        await Promise.all([this.getCategories(), this.getInfo(), this.getItemSizes()]);
      } catch (error) {
        console.error(error);
      }
    },
    async getInfo() {
      try {
        const response = await axios.get('getDatas');
        this.info = response.data;
      } catch (error) {
        console.log(error);
      }
    },
    async getCategories() {
      try {
        const response = await axios.get('getcat');
        this.categories = response.data;
      } catch (error) {
        console.log(error);
      }
    },
    async getItemSizes() {
      try {
        const response = await axios.get('getsize');
        this.sizes = response.data;
      } catch (error) {
        console.log(error);
      }
    },
    getSizeName(sizeId) {
      const size = this.sizes.find(size => size.size_id === sizeId);
      return size ? size.item_size : 'Unknown';
    },
    getCategoryName(categoryId) {
      const category = this.categories.find(category => category.id === categoryId);
      return category ? category.category_name : 'Unknown';
    },
      
    },
    mounted() {
      this.fetchCategories();
      this.getSalesRecord(); 
    },
  };
  </script>






<style>


.neumorphic-button:focus {
  border: 0px solid; /* Set the border to 2px when focused */
  border-radius: px;
}

.room-item {
  background-color: #ffffff;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s ease-in-out;
}

.room-item:hover {
  transform: scale(1.05);
}
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css');
@import url('https://fonts.googleapis.com/css2?family=WindSong&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');
/* Style for the label */
.label {
  font-weight: bold;
  margin-bottom: 5px;
  display: block;
}

/* Style for the select dropdown */
.select-wrapper {
  position: relative;
  width: 200px;
  border: 0px;
}

.select {
  padding: 8px 30px 8px 8px;
  border: 0px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  width: 100%;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="%23333333"><path d="M7 10l5 5 5-5z" /></svg>') no-repeat right 8px center/12px;

}

.arrow-icon {
  position: absolute;
  top: 50%;
  right: 10px;
  transform: translateY(-50%);
  color: #333333;
  pointer-events: none;
}

.loader {
  width: 60px;
  height: 60px;
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
  background: rgba(255, 136, 0, 0.85);
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
    
</style>