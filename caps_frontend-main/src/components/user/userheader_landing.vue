
<template>
	<div>
	<nav class="neumorphic-navbar" :class="{ 'navbar-hidden': isNavbarHidden }">
				<a class="navbar-brand">Qmj<span>Ent.</span></a>
				<!--profile picture-->
				<!-- <img style="width:50px; height:50px;"  v-if="info.length > 0" :src="info[0].profile_picture" alt="Profile" class="profile-picture-navbar"> -->
				<span style="margin-left:300px;" class="nav-item">
				  <router-link to="/qmjimages"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           zxaclass="nav-link">Home</router-link>
				</span>
				<span class="nav-item">
				  <router-link to="#" class="nav-link">About</router-link>
				</span>
				<span class="nav-item">
				  <a href="#" class="nav-link">Services</a>
				</span>
				<span class="nav-item">
				  <a class="nav-link" @click="openDialog">Book Event</a>
				</span>
				<span class="nav-item">
				  <a href="#" class="nav-link">Blog</a>
				</span>
				<span class="nav-item">
				  <a @click="openDialog" class="nav-link">Products</a>
				</span>
                <span class="nav-item">
                    <a href="/" class="nav-link">Login Account</a>
                  </span>
				<span class="nav-item cta">
				  <router-link to="/contacts" class="nav-link">Contact Us</router-link>
				</span>	
		
				

				
			  </nav>

			  <router-view></router-view>
			</div>
			
              <!--Dialog for request account-->

              <v-dialog v-model="dialog" max-width="500px">
                <v-card>
                  <v-card-title class="headline" style="margin-left:99px;">Rigister Account As new User</v-card-title>
                  <v-card-text>
                    <p style="margin-left:120px;">Doesn't have an account yet?</p>
                    <img :src="require('../../../public/img/galit.gif')"  style="margin-left:160px; width: 120px; height: 120px;">
                  </v-card-text>
                  <v-card-actions>
                    <v-btn color="primary" href="/register" style="margin-right:100px; margin-left:40px;">Register</v-btn>
                    <v-btn style="margin-left:90px;" @click="closeDialog" >Register Later</v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>


                 <!--Dialog for request account-->

                 <!-- <v-dialog v-model="dialoglogin" max-width="500px">
                    <v-card>
                      <v-card-title class="headline">Account Information</v-card-title>
                      <v-card-text>
                        <p>Do you have an account yet?</p>
                      </v-card-text>
                      <v-card-actions>
                        <v-btn color="primary" href="/register">Register</v-btn>
                        <v-btn @click="closeDialoglogin">Register Later</v-btn>
                      </v-card-actions>
                    </v-card>
                  </v-dialog> -->

</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      isNavbarHidden: false,
      lastScrollTop: 0,
	  info: [],
      dialog: false,
      dialoglogin: false
    };
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
	this.getInfo(); 
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  created() {
	this.token = sessionStorage.getItem('jwt');
  if (this.token) {
    this.getInfo();
  } else {
    // Handle the case where token is not available in local storage
    console.error('JWT token not found in session storage');
  }
},
  
  methods: {
    openDialog() {
      this.dialog = true;
    },
    closeDialog() {
      this.dialog = false;
    },
    openlogin() {
      this.dialoglogin = true;
    },
    closeDialoglogin() {
      this.dialoglogin = false;
    },
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
  },
};
</script>

<style >

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
  top: 0;
  left: 0;
  width: 1200px;
  z-index: 1000;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #fffdfd;
  padding: 15px;
  border-radius: 5px;

  transition: top 0.3s;
  margin-top: 35px;
  margin-left: 70px;
}

.profile-picture-navbar {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin-left: 10px;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.3);
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
  font-weight:400 ;
}

/* Navbar link hover styles */
.neumorphic-navbar a:hover {
  background-color: #e9e1e1;
  box-shadow: 5px 5px 10px #bcbcbc, -5px -5px 10px #ffffff;
  color: #1b1b1b;
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

  
</style>