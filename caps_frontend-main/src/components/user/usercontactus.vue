<template>

<div style="background-color:rgb(245, 245, 245);">
<br>
<br>
<br>
<section class="ftco-section contact-section">
  <div class="container" style="  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
  animation: fade-up .8s ease-out forwards;">
    <div class="row align-items-center">
      <div class="mb-5">
        <h2 class="h3">Contact Info</h2>
        <p>Refer to the details below for additional contact information within QMJ Enterprise and Creative Services.</p>
      </div>
      <div class="w-100">Philippines</div>
      <ul class="list-unstyled mb-5">
        <li class="">
          <span class="mr-3"><span class="icon-map"></span></span> km. 13 BIGA, Calapan City, Oriental Mindoro, Luzon, Philippines
        </li>
        <li class=""><span class="mr-3"><span class="icon-phone"></span></span> +639474062928</li>
        <li class=""><span class="mr-3"><span class="icon-envelope-o"></span></span> qmjimages2018@gmail.com </li>
      </ul>
      <div class="row align-items-center">
        <p>Basic Info:<br><span>Photography and Videography
Sound and stage lights production</span><br></p>
      </div>
      <div class="row align-items-center">
        <p>Open Hour:<br><span> 8:00 AM - 9:00 PM</span><br></p>
      </div>
      
      <div class="col-md-3">
        <div class="icon"></div>
        <p></p>
      </div>
    </div>
  </div>
</section>

    <section class="ftco-section-parallax">
      <div class="parallax-img d-flex align-items-center">
        <div class="container">
          <div class="row d-flex justify-content-center">
            <div class="col-md-7 text-center heading-section heading-section-white ">
              <h2>Subscribe to our Services to gain Monthly Discount!</h2>
              <p>Photography and Videography Sound and stage lights production</p>
              <div class="row d-flex justify-content-center mt-4 mb-4">
                <div class="col-md-8">
                  <form action="#" class="subscribe-form">
                    <div class="form-group d-flex">
                      <input type="text" class="form-control" placeholder="Enter email address">
                      <input type="submit" value="Subscribe" class="submit px-3">
                    </div>
                  </form>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
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
  

<script>
import axios from 'axios';
export default{
    data(){
        return{
            trackcode:"",
            firstname:"",
            middlename:"",
            lastname:"",
            email:"",
            date:"",
        }
    },
    methods:{
        async save(){
            try {
                const ins = await axios.post("save",{
                    trackcode: this.trackcode,
                    firstname: this.firstname,
                    middlename: this.middlename,
                    lastname: this.lastname,
                    email: this.email,
                });
                    this.trackcode = "";
                    this.firstname = "";
                    this.middlename = "";
                    this.lastname = "";
                    this.email = "";

                this.$emit('data-saved');
                this.getInfo();
                console.log(trackcode, firstname, middlename, lastname, email);
            } catch (error) {
                console.error("Error saving data:", error);
            }
        }
    }
}
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
<style>
@media (max-width: 767px) {
  .contact-info .col-md-3 {
    margin-bottom: 20px;
  }

  .contact-form {
    margin-top: 20px;
  }

  #map {
    width: 100%;
  }
}
</style>
