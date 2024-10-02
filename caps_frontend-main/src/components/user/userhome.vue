<template>

  <div class="all" style="position: absolute;background-color:rgb(245, 245, 245); width:100%; height:100%;">
	<!-- <div :class="{ 'welcome-message': true, 'hidden': !showWelcomeMessage }" style="position:absolute; width:200px; height:100px; margin-top: 180px; margin-left:155px; ">
		<div class="box speech-bottom success">
		  <em>Hello! welcome</em><br/>
		  <strong v-if="info.length > 0" style="font-size: 15px;"> {{ info[0].showed_username }} </strong>
		</div>
	  </div> -->
	<form @data-saved="getUserDetails" />
	<div>
		<tr v-for="info in info">
			<td>{{ info.category_name}}</td>
			<td>
			 
			</td>
		  </tr>
	</div>
	<br>
	<br>
	<br>
	<br>
	<br>
    <div style="display: flex; align-items: center;">
      <img 
      class="neumorphic-navbar" 
      @click="toggleWelcomeMessage" 
      :src="require('../../../src/assets/img/band.png')" 
      alt="Description of the image" 
      style="position:absolute; width: 250px; margin-left: 680px; margin-right: 0px; margin-top:280px; transition: transform 0.3s ease; border-radius:3px; box-shadow: 5px 5px 10px #bcbcbc, -5px -5px 10px #ffffff; transform: rotate(-5deg); z-index: 1;" 
      onmouseover="this.style.transform='scale(1.1)'"
      onmouseout="this.style.transform='rotate(-5deg)'"
    />
    
    <img 
      class="neumorphic-navbar" 
      @click="toggleWelcomeMessage" 
      :src="require('../../../src/assets/img/shoot.png')" 
      alt="Description of the image" 
      style="position:absolute;width: 270px; margin-left: 900px; margin-right: 0px; margin-top:160px; transition: transform 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94); border-radius:3px; box-shadow: 5px 5px 10px #bcbcbc; z-index: 1;" 
    />
    
    <img 
      class="neumorphic-navbar" 
      @click="toggleWelcomeMessage" 
      :src="require('../../../src/assets/img/damit.png')" 
      alt="Description of the image" 
      style="position:absolute; width: 190px; margin-left: 1060px; margin-right: 0px; margin-top:320px; transition: transform 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94);  transform: rotate(5deg); border-radius:3px; box-shadow: 5px 5px 10px #bcbcbc; z-index: 1;" 
      onmouseover="this.style.transform='scale(1.1)'"
      onmouseout="this.style.transform='rotate(5deg)'"
    />
    

    

		<div style="margin-left:180px;">
			
	
        <h1 class="text-center" style="   opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up .8s ease-out forwards;
        animation-delay: 0.2s;font-size: 20px;font-family: 'Poppins', sans-serif; font-size:30px; font-weight:700;  margin-right:255px; margin-top:-30px;color:orange;">Introducing<a style="color:black;font-size:50px;"> QMJ</a> <span style="font-size: 52px;  font-weight:100;color:black;">|</span>&nbsp;&nbsp; <span style="position:absolute;top:-10px;font-size:68px; font-weight:400; font-family: 'WindSong', cursive;color:black;">Images...</span></h1>
		
			<h2 class="navbar-brand" href="index.html" style="  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
			animation: fade-up .8s ease-out forwards; font-family: 'Poppins', sans-serif;
			animation-delay: 0.4s;margin-top:30px;font-size: 16px; ">
			<a></a>	Youre one stop destination for memorable experiences!
        <br>
				<br><a style="font-size: 13px; text-align: justify;">
          Explore our curated book event services, discover unique<br>
          products, and personalized items to make  each moment<br>
          uniquely yours, Immerse yourself in a world of creativity<br>
           and possibilities. Let's create unforgettable <br>
           memories together!.
        </a>
        
			</h2>
			<div>
	
				<br>
				<router-link
  to="/about"
  class="neumorphic-link"
  style="
  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
animation: fade-up .8s ease-out forwards;
animation-delay: 0.5s;
font-family: 'Poppins', sans-serif;
font-size: 14px;
    font-weight:500;
    padding: 10px 30px;
    
    background: rgb(22, 22, 22);
   
	color:rgb(255, 255, 255);
    border-radius: 2px;
    box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff;
    transition: all 0.3s ease;
    text-decoration: none; /* Remove underline */
    display: inline-block; /* To remove underline */
    position: relative; /* For pseudo-element */
  "
>
  Explore
</router-link>

<span>	
	
	
	<router-link
	to="/userServices"
	class="neumorphic-link"
	style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
	animation: fade-up .8s ease-out forwards;
	animation-delay: 0.5s;
	  margin-left:10px;
	  padding: 10px 20px;
	  font-size: 16px;
	  background: white;
    font-family: 'Poppins', sans-serif;
font-size: 14px;
    font-weight:500;
	  height:40px;
	  color:rgb(0, 0, 0);
	  border-radius: 2px;
	  box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff;
	  transition: all 0.3s ease;
	  text-decoration: 1pxx; /* Remove underline */
	  display: inline-block; /* To remove underline */
	  position: absolute; /* For pseudo-element */

	"
  >
	Our Services
  </router-link></span>

			</div>
			<br>
		
		</div>
	</div>
</div>

</template>

<style scoped>
img:hover {
    transform: scale(1.1);
   
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
.neumorphic-link {
	/* Your existing styles */
	/* ... */
  
	/* Remove underline by default */
	text-decoration: none;
  }
  
  .neumorphic-link:hover {
	/* Style on hover */
	background-color: #ddd;
	box-shadow: 5px 5px 10px #bcbcbc, -5px -5px 10px #ffffff;
	color: #000000; /* Change text color on hover */
  }
  
  /* Hide the underline only on hover */
  .neumorphic-link::after {
	content: '';
	position: absolute;
	left: 0;
	right: 0;
	bottom: -5px; /* Adjust this value to fine-tune the positioning */
	height: 1px;
	background-color: transparent; /* Make the underline transparent */
	transition: all 0.3s ease;
  }
  
  .neumorphic-link:hover::after {
	bottom: -10px; /* Move the underline away on hover */
	background-color: transparent; /* Hide the underline on hover */
  }




.box.success
{
  border-color:  rgb(25, 26, 25);
  background: rgb(25, 26, 25);
  color: white;
}

.box
{
  min-width: 50px;
  min-height: 40px;
  border-color: #CCC;
  background-color: #CCC;
  color: #555;
  display: inline-block;
  position: relative;
  padding: 10px;
  font-size: 13px;
  margin: 20px;
  border-radius: 10px;  
  box-shadow: inset 1px 1px 0px rgba(172, 171, 171, 0.2),
              inset -1px -1px 0px rgba(0, 0, 0, 0.6),
              0 14px 6px -10px rgba(0, 0, 0, 0.3);
}

.speech-top:after
{
  content: "";
  position: absolute;
  width: 0;
  height: 0;
  top: -19px;
  left: 10px;
  border: 10px solid;
  border-color: transparent;
  border-bottom-color: inherit;  
}

.speech-bottom:after
{
  content: "";
  position: absolute;
  width: 0px;
  height: 0px;
  top: 89%;
  left: 82px;
  margin-top: -2px;
  border: 10px solid;  
  border-color: transparent;
  border-top-color: inherit;
}

.speech-push-right:after
{
  left: 100%;
  margin-left: -30px;
}
.welcome-message {
	opacity: 1;
	transition: opacity 0.4s ease-in-out; /* Adjust the duration and timing function as needed */
  }
  
  .welcome-message.hidden {
	opacity: 0;
	transition: opacity 0.5s ease-in-out; /* Adjust the duration and timing function as needed */
  }
  
</style>
<style scoped>
  /* Your existing styles */

 

  img:hover {
    transform: scale(1.1);
  }
/*.all {
  background-image: url('../../../src/assets/img/try.png');
  background-size:400px; 
 

}*/
  /* ... your other styles ... */
</style>


<script>

import axios from 'axios';

export default {
  data() {
    return {
	    info: [],
		showWelcomeMessage: false,
    };
  },
  mounted() {
	this.getInfo(); 
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
  methods: {
	toggleWelcomeMessage() {
  // Toggle the welcome message visibility
  this.showWelcomeMessage = !this.showWelcomeMessage;

  // If showing the welcome message, set a timeout to hide it after 3 seconds
  if (this.showWelcomeMessage) {
    setTimeout(() => {
      this.showWelcomeMessage = false;
    }, 3000); // 3000 milliseconds (3 seconds)
  }
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
}
};
</script>