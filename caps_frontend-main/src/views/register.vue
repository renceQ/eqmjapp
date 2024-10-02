<template>
  <div class="neumorphic-navbar" style="box-shadow: 5px 5px 10px #bcbcbc, -5px -5px 10px #ffffff;position:absolute; width:500px; height:500px; margin-left:450px; ">

    <div style="position:absolute;" >
      <div style="margin-bottom: 20px;">
        <img :src="require('../assets/images/logo.jpg')" alt="Description of the image" style="  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up 0.8s ease-out forwards;max-width: 100%; height: 100%; width:50px; height:50px; margin-top:-390px; margin-left:370px;">
      </div>
      
      <h3 style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
      animation: fade-up 0.8s ease-out forwards;margin-left: 70px; margin-top:-250px; font-size: 14px; font-weight:900;" >WELCOME TO<span style="font-size: 22px;  font-weight:100;">&nbsp;&nbsp;|&nbsp;</span><span style="font-weight:400; font-family: 'WindSong', cursive; font-size:33px;">Qmj Ent</span></h3>
      <p style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
      animation: fade-up 0.8s ease-out forwards;margin-left:70px; margin-top:-15px; font-weight:800;">REGISTER FORM</p>
    </div>
    <div >
      <div>

       
        
        <br>
        <h4 style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up .8s ease-out forwards;
        animation-delay: 0.2s;margin-left:100px; font-size: 14px; margin-top:-100px; margin-left:170px;">Register New Account</h4>
       
        
        <div class="v-sheet"> 
          <form @submit.prevent="register">
            <div v-if="message" class="error-message-box" style="position:absolute; width:355px; margin-left:-87%; top:20%;">
              <div class="error-message">{{ message }}</div>
            </div>
           
        
            <label for="username" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s;position:absolute; right:70%;margin-top:30px;">Username:</label>
            <input style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s;position:absolute;  right:13%; top:40.5%; border:0px;" class="search-input" v-model="username" id="username" type="text" required>
        
            <label for="password" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s;position:absolute; right:70.5%;top:54%;">Password:</label>
            <input style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s;position:absolute;  right:13%; top:51.5%; width:250px;" class="search-input" v-model="password" id="password" type="password" required>
        
            <label for="passwordConfirm" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s;position:absolute; right:66.5%;top:64.5%;">Confirm Pass:</label>
            <input  style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s;position:absolute;  right:13%; top:62.5%; width:250px;" v-model="passwordConfirm" id="passwordConfirm"  class="search-input" type="password" required>
        
            <button type="submit" class="mt-2" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s;background-color: #222121; color: #FFFFFF;position:absolute;  right:13%; top:76.5%; width:360px;">Submit</button>
            <p onclick="window.location.href='/'" class="new" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s;color: black; margin-left: 10%; right: 45.5%; top: 90%; display: block; position: absolute; text-align: center; cursor: pointer; top:88%;">Login</p>
          </form>
        </div>
        


      </div>
    </div>
    </div>
    
  </template>
  
  <script>
  import router from '@/router';
  import axios from 'axios';
  
  export default {
    data() {
      return {
        username: '',
        password: '',
        passwordConfirm: '',
        message: '', // Initially, no message
      };
    },
    methods: {
      async register() {
  this.message = ''; // Resetting message before each form submission

  if (!this.username || !this.password || !this.passwordConfirm) {
    this.message = 'Please fill in all fields';
    return;
  }

  // Validate password complexity
  const letterNumberRegex = /^(?=.*[a-zA-Z])(?=.*[0-9])/;
  if (this.password.length < 10 || !letterNumberRegex.test(this.password)) {
    this.message = 'Password must be at least 10 characters long and contain both letters and numbers.';
    return;
  }

  if (this.password !== this.passwordConfirm) {
    this.message = 'Passwords do not match';
    return;
  }

  try {
    // Check if username already exists
    const usernameExists = await this.checkUsernameExists(this.username);
    
    if (usernameExists) {
      this.message = 'Username already exists';
      return;
    }

    // If username does not exist, proceed with registration
    const data = await axios.post('api/register', {
      username: this.username,
      password: this.password,
    });

    if (data.data.msg === 'okay') {
      alert('Registered successfully');
      router.push('/');
    } else {
      this.message = data.data.msg || 'Invalid response';
    }
  } catch (error) {
    console.error('Error:', error);
    this.message = 'Error occurred while registering';
  }
},

async checkUsernameExists(username) {
  try {
    const response = await axios.post('api/checkUsername', {
      username: username,
    });
    
    return response.data.exists; // Return true or false based on server response
  } catch (error) {
    console.error('Error checking username:', error);
    return false; // Return false in case of an error
  }
},
    },
  };
  </script>

  <style>
  .error-message-box {
    background-color: rgba(255, 0, 0, 0.05);
    padding: 8px;
    border-radius: 8px;
  }
  
  .error-message {
    color: rgb(60, 60, 60);
    font-size: 14px;
  }

  </style>
  