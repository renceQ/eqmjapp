<template>
  <div style="background-color:rgb(245, 245, 245); width:100%; height:100%;">
  <div class="hero-wrap-0 js-fullheight" style=" margin-bottom:100px;  margin-left:80px;" data-stellar-background-ratio="0.5">
    
    <div style="display: flex; align-items: left; text-align: justify;">

      <div style="margin-right: 0px;margin-top:180px; margin-left: 120px;  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
      animation: fade-up 0.8s ease-out forwards;">
        <h1 class="text-center" style="font-size: 35px; font-weight:900; margin-left:30px;font-family: 'Poppins', sans-serif;">ABOUT <span style="font-size: 30px; font-weight:100;margin-left:10px;">|</span>&nbsp;&nbsp; <span style="font-size:77px; font-weight:400; font-family: 'WindSong', cursive;">Us...</span></h1>
        <h2 class="navbar-brand" href="index.html" style="opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up .8s ease-out forwards;
        animation-delay: 0.2s;font-size: 14px;  font-family: 'Poppins', sans-serif;">
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;QMJ Enterprises is dedicated to crafting unforgettable experiences <br>
          through a diverse array of services. From expertly arranging sound and<br>
         lighting setups to capturing captivating moments through professional<br>
           photo and video shoots, their expertise extends to designing albums, cr <br>
           eating bespoke souvenirs, and customizing clothing. Additionally, they<br>excel in printing tarpaulins, ensuring every event is marked with person<br>
           alized and exceptional touches that leave a lasting impression.
        </h2>
      </div>

      <router-link
  to="#"
  @click="scrollDown"
  class="neumorphic-link"
  style="
  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
animation: fade-up .8s ease-out forwards;
animation-delay: 0.5s;
font-family: 'Poppins', sans-serif;
font-size: 14px;
    font-weight:500;
    padding: 8px 30px;
    margin-top:38%;
    height:40px;
    left:14.5%;
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

      <div style="display: flex; margin-top:140px; align-items: center; justify-content: flex-end; { backgroundImage: 'url(' + require('../../../src/assets/img/line/png') + ')' }">
        <img 
          :src="require('../../assets/img/first.png')" 
          alt="Description of the image" 
          style="  
        
          animation-delay: 0.3s;
        position:absolute; border-radius: 10px; width: 570px; right:7%;margin-top:45px; transition: transform 0.3s ease-in-out ;"
          onmouseover="this.style.transform='scale(1.1)'" 
          onmouseout="this.style.transform='scale(1)'"
        />
      </div>

    </div>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <div class="container">
      <div class="row d-flex"> 
        <div class="col-md-7">
          <h3 class="navbar-brand" style="font-size: 15px;">
            <span style="margin-left:45px;font-size: 20px;">BE SPOKE |</span>&nbsp;&nbsp;<span style="font-size: 21px; font-weight:400;font-family: 'Poppins', sans-serif;">CREATIONS</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br><br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <a style="font-family: 'Poppins', sans-serif; font-size:13px;">At the heart of Qmj Enterprise lies a dedication to crafting unforgettable experiences. Established with a vision to redefine industry standards, QMJ  <br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Enterprise has consistently delivered excellence across its diverse array of services. From expertly arranging sound and lighting setups to capturing cap-<br> 
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tivating moments through professional photo and video shoots, QMJ Enterprise ensures that every project is marked by personalized and exceptional to-<br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;uches. This commitment not only ensures that its offerings are cutting-edge but also reflects a proactive approach to meeting and exceeding client expec-<br>  
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tations. Whether it's designing albums, creating bespoke souvenirs, customizing clothing, or excelling in printing tarpaulins, QMJ Enterprise embraces in- <br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;novation as a driving force for success.</a>
          </h3>
        </div>
      </div>
      <br>
      <br>
      <br>
      <br>
      <div class="row">
        <div class="col-md-7" style="margin-left:550px;">
          <h1 class="navbar-brand" style="font-size: 25px;  margin-top:-20px;"> Our Story&nbsp;|<span>&nbsp;2013...</span></h1>
          <h4 class="navbar-brand" style="font-size: 15px; text-align: justify;">
            The early days weren't without challenges. From navigating <br>
            market fluctuations to establishing a foothold in a competitive <br> 
            industry, QMJ Enterprise faced its share of obstacles. However, <br> 
            resilience and a dedication to excellence guided the team through <br> 
            these challenges, strengthening their resolve to succeed. <br>
            Understanding that each client is unique, the enterprise adopted <br>
            a client-centric approach, actively engaging with clients to tailor <br>
            solutions that not only met but exceeded expectations.
          </h4>
        </div>
        <div style="display: flex; align-items: center; justify-content: flex-end;">
          <img 
            :src="require('../../assets/img/KRAM (1).png')" 
            alt="Description of the image" 
            style="position:absolute; top:37%; border-radius: 10px; width: 650px; right:44%; transition: transform 0.3s ease-in-out;"
            onmouseover="this.style.transform='scale(1.1)'" 
            onmouseout="this.style.transform='scale(1)'"
          />
        </div>
      
        <div class="col-md-5" style="position:abosolute; margin-top:90px; margin-left:50px;">
          <h1 class="navbar-brand" style="font-size: 30px;"> Challenges<span>...</span></h1>
          <h4 class="navbar-brand" style="font-size: 15px; text-align: justify;">
            It's important to note that businesses also use challenges as opportunities for growth and improvement. Qmj may develop strategies, innovate,  and adapt<br>
            to overcome obstacles and enhance their overall resilience. To get specific information about challenges faced by QMJ Enterprises, I recommend checking  <br> 
            their official communications, reports,  or contacting the company directly for the latest and most accurate details.<br>
           
          </h4>
        </div>
      </div>

  
    </div>
  </div>
  <br>
  <br><br>
  <br><br>
  <br><br>
  
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
  
<script>
export default {
  methods: {
    scrollDown() {
      // Calculate the position to scroll to (adjust the value as needed)
      const scrollPosition = window.scrollY + 570; // You can adjust the value as needed

      // Use smooth scroll for a better user experience
      window.scrollTo({
        top: scrollPosition,
        behavior: 'smooth'
      });
    }
  }
};

</script>

<style>

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

</style>