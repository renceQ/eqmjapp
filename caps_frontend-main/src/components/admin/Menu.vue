<template>
  <div>

<nav style=" margin-left:-30px; position:absolute; margin-top:-1px; " >    
    <!-- <input type="checkbox" id="check">
    <label for="check">
  <i class="fa fa-bars" id="btn" ></i>
  <i class="fa fa-times" id="cancle" style=" margin-left:20px;" ></i>
  </label> -->
    <div class="sidebar">
  <header>
    <img v-if="info.length > 0" :src="info[0].profile_picture" alt="Profile" style="margin-top: 30px; margin-left:30px;" >
  <p style="margin-top:5px; font-family: 'Poppins', sans-serif; font-weight:600; font-size:18px; margin-left:30px; color: rgba(250, 123, 4, 0.993); ">Qmj Images&nbsp;&nbsp;<i class="fas fa-user-edit"></i>
  </p>
  <p style=" position:absolute; font-family: 'Poppins', sans-serif; font-weight:500; font-size:16px; margin-left:92px; top:18.5%; ">Administrator</p>
  <br>
</header>


  <ul> 
    <div style="">
      <li><a style="font-size:15px;font-weight:500;font-family: 'Poppins', sans-serif; text-decoration: none;" href="/dashBoard"> &nbsp;&nbsp;&nbsp;&nbsp;<i class="fas fa-qrcode"></i> Dashboard</a></li>
      <li><a style="font-size:15px;font-weight:500;font-family: 'Poppins', sans-serif; text-decoration: none;" href="/productstable"> &nbsp;&nbsp;&nbsp;&nbsp;<i class="fas fa-list"></i>Products List</a></li>
      <li><a style="font-size:15px;font-weight:500;font-family: 'Poppins', sans-serif; text-decoration: none;" href="/orderRequest"> &nbsp;&nbsp;&nbsp;&nbsp<i class="fas fa-shopping-cart"></i>Product Request</a></li>
      <li><a style="font-size:15px;font-weight:500;font-family: 'Poppins', sans-serif; text-decoration: none;" href="/productcategory"> &nbsp;&nbsp;&nbsp;&nbsp;<i class="fas fa-tags"></i>Product Category</a></li>
      <li><a style="font-size:15px;font-weight:500;font-family: 'Poppins', sans-serif; text-decoration: none;" href="/orderproducts"> &nbsp;&nbsp;&nbsp;&nbsp;<i class="fas fa-clipboard-list"></i> Order List</a></li>
      <li><a style="font-size:15px;font-weight:500;font-family: 'Poppins', sans-serif; text-decoration: none;" href="/service"> &nbsp;&nbsp;&nbsp;&nbsp;<i class="fas fa-cogs"></i>Service List</a></li>
      <li><a style="font-size:15px;font-weight:500;font-family: 'Poppins', sans-serif; text-decoration: none;" href="/bookingtable"> &nbsp;&nbsp;&nbsp;&nbsp;<i class="fas fa-book"></i>Service Request</a></li>
      <li><a style="font-size:15px;font-weight:500;font-family: 'Poppins', sans-serif; text-decoration: none;" href="/approved_events"> &nbsp;&nbsp;&nbsp;&nbsp;<i class="far fa-calendar-alt"></i>Event Schedules</a></li>
      <li><a style="font-size:15px;font-weight:500;font-family: 'Poppins', sans-serif; text-decoration: none;" href="/customer"> &nbsp;&nbsp;&nbsp;&nbsp;<i class="fas fa-link"></i> Customer List</a></li>
      <li><a style="font-size:15px;font-weight:500;font-family: 'Poppins', sans-serif; text-decoration: none;" href="#"> &nbsp;&nbsp;&nbsp;&nbsp;<i class="fas fa-question-circle"></i> About</a></li>
      <li><a style="font-size:15px;font-weight:500;font-family: 'Poppins', sans-serif; text-decoration: none;" href="#"> &nbsp;&nbsp;&nbsp;&nbsp;<i class="fas fa-cog"></i> Services</a></li>
      <li><a style="font-size:15px;font-weight:500;font-family: 'Poppins', sans-serif; text-decoration: none;" href="#"> &nbsp;&nbsp;&nbsp;&nbsp;<i class="fas fa-phone"></i> Contact</a></li>
    </div>
    </ul>

     <li style="margin-left:43px;">
        <div class="social-links">
          <a href="#"><i class="fab fa-facebook"></i></a>
          <a href="#"><i class="fab fa-youtube"></i></a>
          <a href="#"><i class="fab fa-twitter"></i></a>
          <a href="#"><i class="fab fa-linkedin"></i></a>
        </div>
      </li>
  </div>
</nav>
</div>
  </template>
  
  <script>
import axios from 'axios';

export default {
  data() {
    return {
	  info: [],
    };
  },
  created() {
	this.token = sessionStorage.getItem('jwt');
  if (this.token) {
    this.getInfo();
  } else {
    // Handle the case where token is not available in local storage
    console.error('JWT token not found in local storage');
  }
},
  
  methods: {
    
	async logout() {
		        sessionStorage.clear();
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
  },
};
</script>
  <style>
  @import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css');
      @import '../../assets/css/style.css';
  * {
    margin: 0;
    padding: 0;
    list-style: none;
    text-decoration: none;
  }
  body{
    height: 100vh;
    background: #ffffff;
    font-family: Arial;
    font-weight: 600;
  }
  #check {
    display: none;
  }
  label #btn,
  label #cancle {
    position: absolute;
    cursor: pointer;
    background: #dde1e7;
    box-shadow: -3px -3px 7px #ffffff73,
                2px 2px 5px rgba(128, 135, 148, 0.562);
    color: rgb(4, 145, 216);
    border-radius: 3px;
  }
   
  label #btn {
    left: 40px;
    top: 25px;
    font-size: 35px;
    color: rgb(14, 186, 243);
    padding: 6px 12px;
    transition: all 0.5s;
  }
  #cancle {
    z-index: 1111;
    left: -195px;
    top: 17px;
    font-size: 30px;
    color: #0a5275;
    padding: 4px 9px;
    transition: all 0.5s;
  }
  /* active side bar */
  /* CSS for sidebar */
.sidebar {
  position: absolute;
  left: 1; /* Change this from -250px to 0 */
  width: 300px;
  background-color: #dde1e7;
  box-shadow: -3px -3px 7px #ffffff73, 2px 2px 5px rgba(128, 135, 148, 0.562);
  transition: all 0.5s ease;
}

/* Hide the toggle button when sidebar is visible */
#check:checked ~ label #btn {
  left: 250px;
  opacity: 0;
  pointer-events: none;
}

/* Adjust cancel button position */
#check:checked ~ label #cancle {
  left: 245px;
}

/* Move content to the right when sidebar is visible */
#check:checked ~ section {
  margin-left: 250px;
}

  .sidebar header img {
    border-radius: 50%;
    width: 120px;
    height: 120px;
    margin-top: 10px;
    box-shadow: 
     
  0px 0px 2px #5f5f5f,
  0px 0px 0px 7px #ecf0f3,
  8px 8px 15px #a7aaaf,
  -8px -8px 15px #ffffff
  ;
  }
  .sidebar header {
    font-size: 24px;
    color: rgb(57, 57, 57);
    text-align: center;
    line-height: 30px;
    background: #dde1e7;
     
    user-select: none;
  }
  .sidebar header p {
    padding: 15px;
  }
   
  .sidebar ul a {
    display: block;
    height: 100%;
    width: 100%;
    line-height: 56px;
    font-size: 18px;
    color: rgb(68, 68, 68);
    padding-left: 40px;
    box-sizing: border-box;
   
    box-shadow: -3px -3px 7px #ffffff,
                2px 2px 5px rgba(128, 135, 148, 0.562);
     
    transition: 0.4s;
  }
  .sidebar ul a i {
    margin-right: 16px;
  }
  /* hover effect */
  ul li:hover a {
    padding-left: 50px;
    color: rgb(0, 158, 216);
    box-shadow: inset -1px -1px 2px #dde1e7;
  }
         
  /* Social Links */
  .social-links i {
    padding: 10px;
    margin-left: 16px;
    
    color: rgb(4, 61, 118);
    background: #dde1e7;
    font-size: 20px;
    box-shadow: -3px -3px 7px #ffffff,
                2px 2px 5px rgba(128, 135, 148, 0.562);
  }
  /* icons hover effect */
  .social-links i:hover {
    color: rgb(0, 170, 255);
  }
  </style>
  
  <script>

</script>
  
  
  
  sidebar back up