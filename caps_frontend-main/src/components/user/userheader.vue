
<template>
	<div>

	<nav class="neumorphic-navbar" style="width:90%; background-color:rgb(245, 245, 245)" :class="{ 'navbar-hidden': isNavbarHidden }">
    <span class="nav-item">
      <img style="width:70px; height:70px;"  v-if="info.length > 0" :src="require('../../../src/assets/img/qmj.png')" class="logo-picture-navbar">
      <img style="width:70px; height:70px;"  v-if="info.length > 0" :src="require('../../../src/assets/img/qmj2.png')" class="logo-picture-navbar">
    </span>
    <!-- <router-link to="/home" style=" font-weight: 400; font-family: 'Poppins', sans-serif; color:black;" >Qmj<span>Ent.</span></router-link> -->
				<!--profile picture-->

				<span style="margin-left:20px;" class="nav-item">
				  <router-link to="/home" style="font-weight:500; font-size:13px;" class="nav-link">Home</router-link>
				</span>
				<span class="nav-item">
				  <router-link to="/about" style="font-weight:500; font-size:13px;" class="nav-link">About</router-link>
				</span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
				<span class="nav-item">
				  <a href="/userServices" style="font-weight:500; font-size:13px;" class="nav-link">Services</a>
				</span>
				<span class="nav-item">
				  <a href="/bookevents" style="font-weight:500; font-size:13px;" class="nav-link">Book event</a>
				</span>
				<span class="nav-item">
				  <a href="userblog" style="font-weight:500; font-size:13px;" class="nav-link">Blog</a>
				</span>
				<span class="nav-item">
				  <a href="/userproducts" style="font-weight:500; font-size:13px;" class="nav-link">Products</a>
				</span>
        

        <nav class="navbar">
          <li class="menu-item" >
          <a href="#">
            <i class="fas fa-shopping-bag"></i>
          </a>
          <ul class="dropdown" style="position:absolute; height:270px;">
            <h2></h2>
            <li style="width: 138px; margin-top:15px;"><a href="/toship_main">To Ship</a></li>
            <li style="width: 138px;"><a href="/torecieve_main">To Recieve</a></li>
            <li style="width: 138px;"><a href="/completed_main">Recieved</a></li>
            <li style="width: 138px;"><a href="/cancel_main">Returns and Cancelation</a></li>
            <li style="width: 138px;"><a href="/orderhistory">Order History</a></li>
          </ul>
          </li>
        </nav>





        <!--NOTIFFFFFFFFFFFFFFFFF-->
        <div class="NOTIF">
          <nav class="navbar">
            <li class="menu-item">
              <a href="#">
                <i class="fas fa-bell"></i>
                <div v-if="filteredInfos.length > 0" class="notification-indicator">
                  {{ filteredInfos.length }}
                </div>
              </a>
              <ul class="dropdown" :class="{ active: showAll }" style="position: absolute; margin-right: 5px; width:300px;">
                <br>
                <li><h4>Notifications</h4><aa  style="font-weight:500; font-size:13px;">mark all as read</aa></li>
                <br>
                <!-- Filtered notifications -->
                <li v-for="(filteredInfo, index) in displayedNotifications" :key="filteredInfo.id">
                  <!-- Display notifications based on 'showAll' flag -->
                  <a href="/toship_main" style="width:230px;">
                    <i class="fas fa-comment custom-icon" style="color: green;"></i>&nbsp;&nbsp;&nbsp; 
                    <span style="font-size: 14px; align-items: center; font-weight:700;">
                      {{ filteredInfo.prod_name }} -
                    </span>
                    <!-- Show the appropriate message based on status -->
                    <br>
                    <span v-if="filteredInfo.status === 'approved'" style="font-size: 13px;">
                      Hi! {{ filteredInfo.customerName }}, your order has been approved. We will be packing your parcel soon!
                    </span>
                    <span v-else-if="filteredInfo.status === 'denied'" >
                      Your request has been denied due to some reasons.
                    </span>
                    <!-- Display other relevant information -->
                    <span v-if="!hideToken">{{ token }}</span>
                    <span v-if="!hideStatus">{{ status }}</span>
                  </a>
                </li>
                <br>
                
                <!-- Change the button text to 'Hide All' when 'showAll' is true -->
                <a @click.stop.prevent="toggleShowAll" v-if="filteredInfos.length > 3" style="align-items: center; width:88px; margin-left:80px; cursor: pointer;">
                  {{ showAll ? 'Hide All' : 'View All' }}
                </a>
                <br>
              </ul>
            </li>  
          </nav>
        </div>
        
        
        

				<span class="nav-item cta">
				  <router-link  style="font-weight:500; font-size:13px;" to="/contacts" class="nav-link">Contact Us</router-link>
				</span>	



        
				<nav class="navbar">
					  <li class="menu-item" >
						<a  style="font-weight:500; font-size:13px;" href="#">Menu</a>
						<ul class="dropdown" style="margin-right: 200px; position:absolute;">
              <h2></h2>
						  <!-- <li><a href="#">View Your Profile</a></li> -->
						  <li style="width: 140px; margin-top:20px;"><a href="#">Settings and Privacy</a></li>
						  <li style="width: 140px;"><a href="editprofiles">Edit Profile</a></li>
						  <li style="width: 140px;"><a href="#" class="nav-link" @click="logout">Log out</a></li>
              <br>
						</ul>
					  </li>
				  </nav>
          <!-- <router-link to="/editprofiles"> -->
            <img href="/editprofiles"
              v-if="info.length > 0"
              :src="info[0].profile_picture"
              alt="Profile"
              class="profile-picture-navbar"
              style="width: 40px; height: 40px; cursor: pointer; transition: left 0.2s;"
              :style="{ left: isHovered ? '5px' : '0' }"
              @mouseover="redirect = true"
            />
          <!-- </router-link> -->
        

			  </nav>
        

			  <router-view></router-view>
			</div>
			  <!-- <div style="margin-top: 150px;">
				Your form or insert component
				  <tbody>
					<tr v-for="userData in info" :key="userData.id">
					  <td>
						<div class="user-profile">
						  <img :src="userData.profile_picture" alt="" class="profile-picture">
						  <div class="profile-details">
							<div>{{ userData.username }}</div>
							<div>{{ userData.address }}</div>
							<div>{{ userData.contact }}</div>
							<div>{{ userData.other_info }}</div>
						  </div>
						</div>
					  </td>
					</tr>
				  </tbody>
	
			  </div> -->
        
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      
      isNavbarHidden: false,
      lastScrollTop: 0,
	    info: [],
      infos: [],
      token: '',
    hideToken: true,
    showAll: false,
    };
  },
  computed: {
    filteredInfos() {
    // Filter the 'infos' array based on the token in session storage and status "approved" or "denied"
    const filtered = this.infos.filter(info => info.token === this.token && (info.status === "approved" || info.status === "denied"));

    // Sort the filtered notifications based on the 'updated_at' field in descending order
    return filtered.sort((a, b) => {
      // Convert the 'updated_at' strings to Date objects for comparison
      const dateA = new Date(a.updated_at);
      const dateB = new Date(b.updated_at);

      // Sort by the latest 'updated_at' first (descending order)
      return dateB - dateA;
    });
  },
  displayedNotifications() {
      // If 'showAll' is true, display all notifications, otherwise show the first 3
      return this.showAll ? this.filteredInfos : this.filteredInfos.slice(0, 3);
    },
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  this.getOrder();
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  created() {
	this.token = sessionStorage.getItem('jwt');
  if (this.token) {
    this.getInfo();
  } else {
    // Handle the case where token is not available in local storage     session token
    console.error('JWT token not found in session storage');
  }
},
  
  methods: {
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
	async logout() {
		        sessionStorage.clear();
            // this.$router.push('/landing');
    },
	
	toggleDropdown() {
    const menu = document.querySelector('.menu-item');
    menu.classList.toggle('active');
  },
    async getInfo() {
    try {
      const response = await axios.get(`getUserData/${this.token}`);
      this.info = response.data; // Assuming response.data is an object/array of user data   get session token
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
    toggleShowAll() {
      this.showAll = !this.showAll; // Toggle the 'showAll' flag when 'View All'/'Hide All' is clicked
    },
    preventClose(event) {
      if (this.showAll) {
        event.stopPropagation(); // Prevent the dropdown from closing when 'View All' is clicked
      }
    }
  },
};
</script>

<style scoped>
.dropdown {
  overflow-y: hidden; /* Hide the scrollbar by default */
}

.dropdown.active {
  overflow-y: auto; /* Show scrollbar when 'View All'/'Hide All' is clicked */
  max-height: 300px; /* Limit the height to 300px */
}
@import url('https://fonts.googleapis.com/css?family=Work+Sans:100,200,300,400,500,600,700,800,900');
@import '../../assets/css/open-iconic-bootstrap.min.css';
@import '../../assets/css/animate.css';

@import '../../assets/css/owl.theme.default.min.css';
@import '../../assets/css/magnific-popup.css';
@import '../../assets/css/aos.css';
@import '../../assets/css/ionicons.min.css';

@import '../../assets/css/flaticon.css';
@import '../../assets/css/icomoon.css';
@import '../../assets/css/style.css';

/* Common styles for the navbar */
.neumorphic-navbar {
  position: fixed;

  left: 0;
  width: 1200px;
  z-index: 1000;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #ffffff;
  
  border-radius: 5px;
 
  transition: top 0.3s;
  margin-top: 10px;
  margin-left: 70px;
}

.profile-picture-navbar {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin-left: 10px;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.3);
}




.logo-picture-navbar {
  width: 30px;
  height: 30px;
  border-radius: 0%;
  margin-left: 10px;
}

/* Hide the navbar when scrolled down */
.navbar-hidden {
  top: -100px;
}

/* Navbar links */
.neumorphic-navbar a {
  color: rgb(14, 13, 13)262;
  text-decoration: none;
  padding: 8px 15px;
  border-radius: 3px;
  transition: all 0.3s ease;
  font-family: 'Poppins', sans-serif;
}


/* Navbar link hover styles */
.neumorphic-navbar a:hover {
  margin-left: 3px;
  background-color: #f3f3f3;
  box-shadow: 5px 5px 10px #bcbcbc, -5px -5px 10px #ffffff;
  color: #00a2ff;
}

/* Additional styles for user profile display */
.user-profile {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.profile-picture {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}

.profile-details {
  display: flex;
  flex-direction: column;
  justify-content: center;
  color: #333;
  font-size: 14px;
}

/* Dropdown styles */
.menu-item {
  position: relative;
  display: inline-block;
  z-index: 1;
}

.menu-item .dropdown {
  position: absolute;
  top: 100%;
  left: 0;
  display: none;
  z-index: 1000;
  background-color: #fff;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.menu-item:hover .dropdown,
.menu-item:focus-within .dropdown {
  display: block;
}

.menu-item a {
  display: block;
  text-decoration: none;
  color: #333;
}

.dropdown {
  width: 205px;
  margin-right: 300px;
  margin-top: 10px;
  display: none;
  z-index: 1;
  background-color: #fff;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}


.dropdown li {
  display: block;
}

.dropdown li a {
  padding: 8px 15px;
  color: #333;
  text-decoration: none;
}
.menu-item > a {
	text-decoration: none;
  }
  
  /* Add this CSS to remove underline on hover for dropdown items */
  .dropdown li a:hover {
	text-decoration: none;
  }
  
  /* Add this CSS to hide dropdown when the menu is clicked again */
  .menu-item.active .dropdown {
	display: none;
  }
/* Responsive styles */
@media screen and (max-width: 768px) {
  .neumorphic-navbar {
    width: 100%;
    margin: 0;
    border-radius: 0;
    padding: 10px;
  }

  .profile-picture-navbar {
    width: 40px;
    height: 40px;
  }

  .neumorphic-navbar a {
    padding: 5px 10px;
  }
  /* Add more styles for smaller screens if needed */
}

.notification-container {
  position: relative;
}

.notification-indicator {
  position: absolute;
  top: -8px;
  right: -8px;
  background-color: red;
  color: white;
  border-radius: 50%;
  width: 20px;
  height: 20px;
  font-size: 12px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: bold;
}


</style>