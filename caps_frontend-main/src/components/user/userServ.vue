<template>
<div style="background-color:rgb(245, 245, 245); width:100%; height:100%;">
  <div>
<div style="margin-left:600px; ">
  <div class="row d-flex align-items-center">
     
   <img 
    :src="require('../../../public/img/cart.png')" 
    alt="Description of the image" 
    style="  
        
    animation-delay: 0.3s;
  position:absolute; border-radius: 10px;top:4.5%; width: 790px; left:-1%; transition: transform 0.3s ease-in-out ;"
    onmouseover="this.style.transform='scale(1.1)'" 
    onmouseout="this.style.transform='scale(1)'"
/>


</div>
<h1 class="text-center" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
animation: fade-up 0.8s ease-out forwards;font-size: 35px; font-weight:900; left:49%; position:absolute; top:5.5%;font-family: 'Poppins', sans-serif;">OUR <span style="font-size: 35px; font-weight:100; margin-left:10px;">|</span>&nbsp;&nbsp; <span style="font-size:84px; font-weight:400; font-family: 'WindSong', cursive;">Services...</span></h1>

			<br>
      <br>
			<h2 class="navbar-brand" href="index.html" style="opacity: 0; /* Set initial opacity to 0 for fade-in effect */
      animation: fade-up .8s ease-out forwards;font-family: 'Poppins', sans-serif;
      animation-delay: 0.2s;font-size: 15px; margin-left:65px;  margin-top:250px;">
				"Welcome to QMJ Enterprises! We offer a diverse range <br>of services including sounds and lighting appointments, <br>professional photo and video shoots, album production, <br>invitations, souvenirs, pre order products,  personalized<br>clothing, and bespoke design suggestions."
			</h2>  
      
      
      <router-link
      to="#"
      @click="scrollDown"
      class="neumorphic-link"
      style="
      opacity: 0; /* Set initial opacity to 0 for fade-in effect */
    animation: fade-up .8s ease-out forwards;
    animation-delay: 0.5s;
    font-family: 'Poppins', sans-serif;
        padding: 8px 30px;
        margin-top:30%;
        height:40px;
        right:40.5%;
        font-size: 14px;
        background-color:white ;
        border: none;
      color:rgb(0, 0, 0);
        border-radius: 4px;
        box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff;
        transition: all 0.3s ease;
        text-decoration: none; /* Remove underline */
        display: inline-block; /* To remove underline */
        position: absolute
        ; /* For pseudo-element */
      "
    >
      Read More
    </router-link>


            <br>
            <br>
            
            <br>
          </div>
    </div>
      <br>

           
        
          <div class="row justify-content-end" style="margin-left:450px; margin-top:140px;">
            <h1 class="text-center" style="   opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up .8s ease-out forwards;
            animation-delay: 0.2s;font-size: 30px; font-weight:900;  margin-right:70%; margin-top:20px;">What we <span style="font-size: 32px;  font-weight:100;">|</span>&nbsp;&nbsp; <span style="position:absolute;top:-30px;font-size:73px; font-weight:400; font-family: 'WindSong', cursive;">Do...</span></h1>
            <div class="col-md-7">
               
            </div>
          </div>

    
        <section class="sec1" id="sec1" >
        <div class="container">
          <div class="row d-flex">
            <div class="col-md-6 d-flex">
              <img :src="require('../../assets/images/soundsandlights.jpg')" alt="Description of the image" style="border-radius: 10px; width: 400px; height:350px; margin-left: 15%; margin-top: 8%;margin-bottom: 100px;">
            </div>
            <div class="col-md-6 pl-md-5 py-5">    
                <div class="col-md-12 ">
                  <h2 class="mb-4" style="margin-top:20px;">Sounds and Lights</h2>
              </div>
              <div class="row" style="width: 1100px; ">
                <div class="col-md-6 ">
                  <div class="block-18 py-4 ">
                    <div class="text">
                      <div class="icon ">
                      </div>
                      <h5 style="font-size:17px; ">Our services cover a complete spectrum of event solutions,<br> 
                        specializing in cutting-edge sound and lighting arrangements.<br>
                        We provide a comprehensive range of top-quality sound systems <br>
                        and state-of-the-art lighting setups tailored to elevate any <br>
                        occasion. With our expertise, we guarantee an immersive <br>audio-visual
                        experience, ensuring your event stands out with  <br>unparalleled ambiance
                        and professional-grade equipment.</h5>
         
                        <br> <br> <br>
                    </div>
                  
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <router-link
        to="/bookevents"
        @click="scrollUp"
        class="neumorphic-link"
        style="
       
        position:absolute;
        opacity: 0; /* Set initial opacity to 0 for fade-in effect */
      animation: fade-up .8s ease-out forwards;
      animation-delay: 0.5s;
          padding: 8px 30px;
        
          top:31.5%;
          height:40px;
          left:53.5%;
          font-size: 16px;
          background: linear-gradient(45deg, #180101, #740a0a, #fae6e6);
          border: none;
        color:white;
          border-radius: 4px;
          box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff;
          transition: all 0.3s ease;
          text-decoration: none; /* Remove underline */
          display: inline-block; /* To remove underline */
          
          ; /* For pseudo-element */
        "
      >
        Make Request
      </router-link>
        </section>

            
        <section class="sec2" id="sec2" >
            <div class="container">
              <div class="row d-flex">
                <div class="col-md-6 d-flex">
                  <img :src="require('../../assets/images/pis2.jpg')" alt="Description of the image" style="border-radius: 10px;  width: 400px; height:380px; margin-left: 80px; margin-top: 25px;margin-bottom: 100px;">
                </div>
                <div class="col-md-6 pl-md-5 py-5">    
                    <div class="col-md-12 ">
                      <h2 class="mb-4" style="margin-top:50px;">Photo and Video Production</h2>
                  </div>
                  <div class="row" style="width: 1100px;">
                    <div class="col-md-6 ">
                      <div class="block-18  py-4 ">
                        <div class="text">
                          <div class="icon ">
                          </div>
                          <h5 style="font-size:17px;">Our services cover a complete spectrum of event solutions,<br> 
                            specializing in cutting-edge sound and whiteing arrangements.<br>
                            We provide a comprehensive range of top-quality sound systems <br>
                            and state-of-the-art lighting setups tailored to elevate any <br>
                            occasion. With our expertise, we guarantee an immersive <br>audio-visual
                            experience, ensuring your event stands out with  <br>unparalleled ambiance
                            and professional-grade equipment.</h5>
                            <br> <br> <br>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <router-link
            to="/bookevents"
            @click="scrollUps"
            class="neumorphic-link"
            style="
           
            position:absolute;
            opacity: 0; /* Set initial opacity to 0 for fade-in effect */
          animation: fade-up .8s ease-out forwards;
          animation-delay: 0.5s;
              padding: 8px 30px;
            
              top:46.8%;
              height:40px;
              left:51.5%;
              font-size: 16px;
              background: linear-gradient(45deg, #000000, #394255, #f6f3fd);
              border: none;
            color:white;
              border-radius: 4px;
              box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff;
              transition: all 0.3s ease;
              text-decoration: none; /* Remove underline */
              display: inline-block; /* To remove underline */
              
              ; /* For pseudo-element */
            "
          >
            Make Request
          </router-link>
            </section>
    
    
            <section class="sec3" id="sec3" >
                <div class="container">
                  <div class="row d-flex">
                    <div class="col-md-6 d-flex">
                      <img :src="require('../../assets/images/hood.jpg')" alt="Description of the image" style="border-radius: 10px; width: 400px; margin-left: 80px; margin-top: 40px;margin-bottom: 100px;">
                    </div>
                    <div class="col-md-6 pl-md-5 py-5">    
                        <div class="col-md-12 ">
                          <h2 class="mb-4" style="margin-top:60px;">Items Customization</h2>
                      </div>
                      <div class="row" style="width: 1100px; ">
                        <div class="col-md-6 ">
                          <div class="block-18 py-4  " >
                            <div class="text">
                              <div class="icon ">
                              </div>
                              <h5 style="font-size:17px;">Our services cover a complete spectrum of event solutions,<br> 
                                specializing in cutting-edge sound and lighting arrangements.<br>
                                We provide a comprehensive range of top-quality sound systems <br>
                                and state-of-the-art lighting setups tailored to elevate any <br>
                                occasion. With our expertise, we guarantee an immersive <br>audio-visual
                                experience, ensuring your event stands out with  <br>unparalleled ambiance
                                and professional-grade equipment.</h5>
                                <br> <br> <br>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <router-link
                to="/bookevents"
                @click="scrollUps"
                class="neumorphic-link"
                style="
               
                position:absolute;
                opacity: 0; /* Set initial opacity to 0 for fade-in effect */
              animation: fade-up .8s ease-out forwards;
              animation-delay: 0.5s;
                  padding: 8px 30px;
                
                  top:62.8%;
                  height:40px;
                  left:51.5%;
                  font-size: 16px;
                  background: linear-gradient(45deg, #000000, #553b26, #f6f3fd);
                  border: none;
                color:white;
                  border-radius: 4px;
                  box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff;
                  transition: all 0.3s ease;
                  text-decoration: none; /* Remove underline */
                  display: inline-block; /* To remove underline */
                  
                  ; /* For pseudo-element */
                "
              >
                Make Request
              </router-link>
                </section>

                
    
            <section class="sec4" id="sec4" >
                <div class="container">
                  <div class="row d-flex">
                    <div class="col-md-6 d-flex">
                      <img :src="require('../../assets/images/eccom.jpg')" alt="Description of the image" style="border-radius: 10px; width: 400px; height:370px; margin-left: 80px; margin-top: 40px;margin-bottom: 100px;">
                    </div>
                    <div class="col-md-6 pl-md-5 py-5">    
                        <div class="col-md-12 ">
                          <h2 class="mb-4" style="margin-top:60px;">Efficient Order Handling of Products  </h2>
                      </div>
                      <div class="row" style="width: 1100px;">
                        <div class="col-md-6 ">
                          <div class="block-18  py-4 ">
                            <div class="text">
                              <div class="icon ">
                              </div>
                              <h5 style="font-size:17px;">Our services cover a complete spectrum of event solutions,<br> 
                                specializing in cutting-edge sound and lighting arrangements.<br>
                                We provide a comprehensive range of top-quality sound systems <br>
                                and state-of-the-art lighting setups tailored to elevate any <br>
                                occasion. With our expertise, we guarantee an immersive <br>audio-visual
                                experience, ensuring your event stands out with  <br>unparalleled ambiance
                                and professional-grade equipment.</h5>
                                <br> <br> <br>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>  <router-link
                to="/bookevents"
                @click="scrollUps"
                class="neumorphic-link"
                style="
               
                position:absolute;
                opacity: 0; /* Set initial opacity to 0 for fade-in effect */
              animation: fade-up .8s ease-out forwards;
              animation-delay: 0.5s;
                  padding: 8px 30px;
                
                  top:79.1%;
                  height:40px;
                  left:51.5%;
                  font-size: 16px;
                  background: linear-gradient(45deg, #000000, #022457, #f6f3fd);
                  border: none;
                color:white;
                  border-radius: 4px;
                  box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff;
                  transition: all 0.3s ease;
                  text-decoration: none; /* Remove underline */
                  display: inline-block; /* To remove underline */
                  
                  ; /* For pseudo-element */
                "
              >
                Make Request
              </router-link>
                </section>

                

                <footer class="ftco-footer ftco-bg-dark ftco-section">
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

<style>
.zoomable {
  cursor: pointer;
}

.zoomable:hover {
  transform: scale(1.1);
  opacity: 1;

}


</style>

<script>
export default {
  data() {
    return {
      currentSection: '' 
    };
  },
  methods: {
    scrollDown() {
      // Calculate the position to scroll to (adjust the value as needed)
      const scrollPosition = window.scrollY + 550; // You can adjust the value as needed

      // Use smooth scroll for a better user experience
      window.scrollTo({
        top: scrollPosition,
        behavior: 'smooth'
      });
    },
    scrollUp() {
      // Calculate the position to scroll to (adjust the value as needed)
      const scrollPosition = window.scrollY - 1050; // You can adjust the value as needed

      // Use smooth scroll for a better user experience
      window.scrollTo({
        top: scrollPosition,
        behavior: 'smooth'
      });
    },
    scrollUps() {
      // Calculate the position to scroll to (adjust the value as needed)
      const scrollPosition = window.scrollY - 1200; // You can adjust the value as needed

      // Use smooth scroll for a better user experience
      window.scrollTo({
        top: scrollPosition,
        behavior: 'smooth'
      });
    }
}
};
</script>