
<template>
  <div style="background-color:rgb(245, 245, 245); width:100%; height:100%;">
    <br>
    
    <div class="hero-wrap hero-wrap-2 js-fullheight" style="height:1400px;" data-stellar-background-ratio="0.5">
      <div style="width: 1200px; position: absolute; margin-left: 100px; ">
        <div >
          
         
          <div style="margin-top:190px;">

            <label for="category_id" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up 0.8s ease-out forwards;animation-delay: 0.2s; font-size:19px; font-weight:600;margin-left:36px;font-family: 'Poppins', sans-serif; position:absolute; margin-top:-70px; color:rgb(255, 145, 0);" class="label text-center">AVAIL SERVICE NOW!</label><br>
            <label for="category_id" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up 0.8s ease-out forwards;animation-delay: 0.2s; font-size:14px; font-weight:600;margin-left:36px;font-family: 'Poppins', sans-serif; position:absolute; margin-top:-60px; color:rgba(2, 54, 97, 0.884);" class="label text-center">Turn your precious moments into unforgettable memories</label><br>
            <label for="category_id" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
            animation: fade-up 0.8s ease-out forwards;animation-delay: 0.2s; font-size:13px; font-weight:400;margin-left:37px;font-family: 'Poppins', sans-serif; position:absolute; margin-top:-60px; color:rgb(138, 138, 138);" class="label text-center"> Explore our range services tailored to meet your unique needs.</label><br>
           
            
            <div class="neumorphic-search" style=" width:420px;height:50px;opacity: 0; /* Set initial opacity to 0 for fade-in effect */
    animation: fade-up .8s ease-out forwards;
    animation-delay: 0.2s; margin-top: -110px; margin-left:680px; position:absolute;box-shadow: 10px 10px 30px #eeecec, -1px -1px 10px #ffffff;">
      <input v-model="searchText" @input="updateSearch" type="text" placeholder="Search for event..." class="search-input" style="margin-top:10px;border: 0px;font-weight:500;font-family: 'Poppins', sans-serif;"/>
      <button style="position:absolute; margin-left:422px; width:49px; height: 49px;margin-top:10px; " class="search-button">
        <i class="fas fa-search"></i>
      </button>
      <a  @click="availability_dialog()" style="text-decoration: none; font-family: 'Poppins', sans-serif; font-size:13px;font-weight:400; margin-top: 10px; position: absolute; margin-left: -200px; width: 170px; height: 49px; color: black;" class="search-button">
        &nbsp;&nbsp;&nbsp;Check Availability <i style="margin-left: 7px; margin-top: 8px;" class="fas fa-calendar custom-icon"></i>
      </a>
      
      <div  style="position:absolute;right:-78%; margin-top:-10px;">
       
      </div>
          
      </div>

          <div style="margin-top:-20px;">
            <button
              v-for="(item, index) in filteredServinfo"
              :key="index"
              @click="openDialogs(item)"
              type="button"
              class="room-item text-center"
              style=" opacity: 0;
              animation: fade-up 0.8s ease-out forwards;
              animation-delay: 0.2s;
              background-color: rgb(255, 255, 255);
              width: 260px;
              height: 330px;
              margin-left: 30px;
              margin-top: -10px;
              border-radius:9px;
              margin-bottom:40px;"
            >
            <div>
              <img
              :src="item.image"
              alt="Service Image"
              v-if="item.image"
              style="
                position: absolute;
                box-shadow: 3px 2px 2px rgba(0, 0, 0, 0.2);
                border-radius: 6px;
                width: 260px;
                height: 260px; /* Set the actual height of the image */
                overflow: hidden;
                clip: rect(0, 260px, 180px, 0); /* Clip the image to show only the upper 220 pixels */
                margin-left: -130px;
                top:-1px;
              "
            />
            
            <span
            style="
            width:200px;
              position: absolute;
              margin-left: -104px;
              margin-top: 50px;
              font-size: 17.3px;
              font-weight:400;
              text-align: left;
              color:#1b1b1b; font-family: 'Roboto', sans-serif;
            "
          >₱&nbsp;{{ item.low_pricing }}<span style="color:rgb(168, 168, 168); font-size:13px;"> / price</span></span>
              <span
                style="
                width:200px;
                  position: absolute;
                  margin-left: -104px;
                  margin-top: 80px;
                  font-size: 17.3px;
                  font-weight:500;
                  text-align: left;
                  color:#1b1b1b;font-family: 'Poppins', sans-serif;
                "
              >{{ item.service }}</span>
              <span style="display:none;">{{ item.id }}</span><br>
              <p style="position:absolute; font-weight: 400; opacity: 0; animation: fade-up .8s ease-out forwards; animation-delay: 0.2s; text-align: left; margin-left: 26px; font-family: 'Poppins'; font-size: 17px; margin-top: 108px; color: #ffee00;">
                ★★★★ 
              </p>
              <span
                style="
                  position: absolute;
                  margin-left: -104px;
                  font-size: 13px;
                  font-weight:900px;
                  margin-top: 130px;
                  color: rgb(22, 103, 255);
                  font-family: 'Roboto', sans-serif;font-family: 'Poppins', sans-serif;
                "
              >Avail Service <span style="font-size:20px;margin-left:6px; font-weight:300; position:absolute; top:-4px;"> ></span></span>
            </div><br>
            
          </button>
        </div>

  
            
          </div>
          <br>
        </div>

    
    </div>
    </div>
    
  
   
    <div class="ftco-footer ftco-bg-dark ftco-section">
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
    </div>
  </div>
  


 <v-dialog v-model="dialogs" max-width="900px" >
  <form @submit.prevent="saveBooking" class="container">
    <v-card style="height:700px;">
      <br>
      <img style="width:60px; height:60px; position:absolute;margin-left:20px;margin-top:20px;"  v-if="info.length > 0" :src="require('../../../src/assets/img/qmj.png')" class="logo-picture-navbar">
      <v-card-title class="headline " style="margin-top:5px;font-size: 19px; font-weight:600;margin-left:76px;font-family: 'Poppins', sans-serif;  color:rgb(0, 153, 255); ">REQUEST FORM<span style="font-size: 22px;  font-weight:100;">&nbsp;&nbsp;&nbsp;</span><span style="font-weight:400; font-family: 'WindSong', cursive; font-size:33px;"></span></v-card-title>
      <v-card-title class="headline " style="position:absolute; margin-top:45px;font-size: 13px; font-weight:600;margin-left:76px;font-family: 'Poppins', sans-serif;  color:rgb(0, 61, 102); ">Fill in the following details for your event<span style="font-size: 22px;  font-weight:100;">&nbsp;&nbsp;&nbsp;</span><span style="font-weight:400; font-family: 'WindSong', cursive; font-size:33px;"></span></v-card-title>

      <v-card-text>

      <div style="font-family: 'Poppins', sans-serif; font-size:13px; margin-top:20px;">
        <div class="form-group">
          <label for="service" style="margin-top:10px; margin-left:40px;">Selected Service:</label>
          <input type="text"  style=" margin-top:-10px;margin-left:30px;font-size:22px;color:rgb(2, 70, 102);width:100%; height:45px; border: none;" placeholder="" v-model="selectedService.service" readonly>
        </div>

        <div class="form-group" style="position:absolute; top:23%;right:120px;">
          <label for="computedTotal">Total Cost:</label>
          <br>
          <input type="text" style="  margin-top:-10px;height:45px; border: none;font-size:22px;color:rgb(2, 70, 102);" placeholder="" v-model="computedTotal" readonly>
        </div>

        <div class="form-row" style="margin-top:-27px;margin-left:360px;  position: absolute;">
          <div class="form-group col-md-6">
            <label for="start_date">Event Start Date:</label>
            <input type="date" class="neumorphic-button" style="font-size:13px; width:150px;background-color:white; border-radius:3px;" v-model="start_date" required>
          </div>

          <div class="form-group col-md-6" style="margin-left:-10px;">
            <label for="end_date" style="position:absolute; margin-left:40px; width:200px;">Event End Date:</label>
            <input type="date" class="neumorphic-button" style="position:absolute;margin-top:27px; margin-left:40px;font-size:13px;width:150px; background-color:white; border-radius:3px;" v-model="end_date" required>
          </div>
        </div>

        <div class="form-row" style="margin-top:127px;margin-left:366px;  position: absolute;">
          <label for="event">Meeting Schedule:</label>
          <div>
            <input for="meeting_date" type="date" class="neumorphic-button" style="font-size:13px; width:150px;background-color:white; border-radius:3px;" v-model="meeting_date" required>
            <input for="meeting_time" type="time" class="neumorphic-button" style="font-size:13px; width:150px;background-color:white; border-radius:3px;margin-left:14px;" id="meeting-time" v-model="meeting_time" name="meeting-time" required>
        </div>
        </div>

        <div class="form-row" style="margin-top:50px;margin-left:360px;  position: absolute;">
          <div class="form-group col-md-6">
            <label for="start_date">Event Start Time:</label>
            <input type="time" for="start_time" class="neumorphic-button" style="font-size:13px; width:150px;background-color:white; border-radius:3px;" id="start_time" v-model="start_time" name="start_time" required>
            <label for="end_time" style="width:200px;position:absolute; margin-left:165px; top:-1px;">Event End Time:</label>
            <input type="time" for="end_time" class="neumorphic-button" style="position:absolute; margin-left:165px; top:26px;font-size:13px; width:150px;background-color:white; border-radius:3px;" id="end_time" v-model="end_time" name="end_time" required>
          </div>
        </div>

        <div class="form-row" style="position: absolute; margin-top:-27px; margin-left:35px;">
          <div class="form-group col-md-6">
            <label for="location">Location:</label><br>
            <input type="text" class="search-input" style="height:40px;width:290px; border:0px;" placeholder="Street-City-Province" v-model="location" required>
          </div>
        </div>

        <div class="form-row" style="position: absolute;margin-top:50px; margin-left:35px;">
          <div class="form-group col-md-6">
            <label for="event_title">Event:</label><br>
            <input type="text" class="search-input" style="height:40px;width:290px; border:0px;" placeholder="example (Wedding, 7th Birthday)" v-model="event_title" required>
          </div>
        </div>

        <div class="form-row" style="position: absolute;margin-left:35px;margin-top:125px;">
          <div class="form-group col-md-6">
            <label for="event_description">Description:</label>
            <textarea class="search-input" v-model="event_description" style="height:50%;width:290px; border:0px;" placeholder="Other Description" required></textarea>
          </div>
        </div>
        

        <div class="form-group" v-if="shouldShowTable" style="position:absolute; margin-left:330px; margin-top:340px;">
          <label for="total_cost" style="margin-left:40px;">Added Items:</label><br>
          <table id="datatable-responsive"  cellspacing="0"  style=" font-family: 'Poppins', sans-serif; height:50px; margin-top:-1px;width:320px;margin-left:30px;  font-size:12px; ">
           
            <thead style="border:0px;">
              <tr>
                <th style=" text-align:center;">ITEM'S</th>
                <th style=" text-align:center;">PRICE</th>
                <th style="width:100px;text-align:center;">QUANTITY</th>
              </tr>
            </thead>
            <tbody>
              <tr v-if="selectedService.first_req && selectedService.first_req.trim() !== '' && inputValue > 0" style="height:10px; ">
                <td>{{ selectedService.first_req }} </td>
                <td>₱{{ selectedService.first_price }}</td>
                <td>{{ inputValue || '0' }}</td>
              </tr>
              <tr v-if="selectedService.second_req && selectedService.second_req.trim() !== '' && secondInputValue > 0" style="height:10px; ">
                <td>{{ selectedService.second_req }} </td>
                <td>₱{{ selectedService.second_price }}</td>
                <td>{{ secondInputValue || '0' }}</td>
              </tr>
              <tr v-if="selectedService.third_req && selectedService.third_req.trim() !== '' && thirdInputValue > 0" style="height:10px; ">
                <td>{{ selectedService.third_req }} </td>
                <td>₱{{ selectedService.third_price }}</td>
                <td>{{ thirdInputValue || '0' }}</td>
              </tr>
              <tr v-if="selectedService.fourth_req && selectedService.fourth_req.trim() !== '' && fourthInputValue > 0" style="height:10px; ">
                <td>{{ selectedService.fourth_req }} </td>
                <td>₱{{ selectedService.fourth_price }}</td>
                <td>{{ fourthInputValue || '0' }}</td>
              </tr>
              <tr v-if="selectedService.fifth_req && selectedService.fifth_req.trim() !== '' && fifthInputValue > 0" style="height:10px; ">
                <td>{{ selectedService.fifth_req }} </td>
                <td>₱{{ selectedService.fifth_price }}</td>
                <td>{{ fifthInputValue || '0' }}</td>
              </tr>
              <tr v-if="selectedService.sixth_req && selectedService.sixth_req.trim() !== '' && sixthInputValue > 0" style="height:10px; ">
                <td>{{ selectedService.sixth_req }} </td>
                <td>₱{{ selectedService.sixth_price }}</td>
                <td>{{ sixthInputValue || '0' }}</td>
              </tr>
             
  
            </tbody>
          </table>
          <br><br>
        </div>

        <div class="form-row" style="">
          <div class="form-group col-md-6" style="margin-left:365px;margin-top:260px;">
            <label for="email">Email:</label>
            <br>
            <input type="email" class="search-input" style="height:40px; width:310px;" placeholder="Email Address" v-model="email" required>
          </div>
        </div>

        <div style="position:absolute;">
        <h3 style="margin-top:-120px; font-size: 14px; font-weight:500;margin-left:41px;font-size:20px;color:rgb(2, 70, 102);" >Contact Details<span style="font-size: 22px;  font-weight:100;">&nbsp;&nbsp;&nbsp;</span><span style="font-weight:400; font-family: 'WindSong', cursive; font-size:33px;"></span></h3>
        <br>
        <div class="form-row">
          <div class="form-group col-md-6" style="margin-left:37px;margin-top:-31px;">
            <label for="name">Name:</label>
            <br>
            <input type="text" class="search-input" style="width:295px;border:0px;height:40px;" placeholder="Name" v-model="name" required>
          </div>
        </div>

       

        <div class="form-group" style="margin-left:37px; margin-top:-10px;">
          <label for="phone">Phone:</label>
          <div>
          <input type="tel" class="search-input" style="width:295px; height:40px;;" placeholder="format 09218510473" v-model="phone" required>
          </div>
        </div>
      </div>
      </div>
      </v-card-text>
      <v-card-actions>

        <div style="margin-bottom: 10px;">
          <button type="submit" class="neumorphic-button" style="margin-left: 52px;margin-top:80px; width: 295px;; background-color: rgb(49, 48, 48); color: white;">Book Event</button>
        </div>

      </v-card-actions>

    </v-card>
  </form>
</v-dialog> 




<v-dialog v-model="dialogss" max-width="810px"> 
  <form @submit.prevent="saveBooking" class="container">
    <v-card style="height:570px;">
      <br>
      <v-card-title class="headline " style="font-size: 19px; font-weight:600;margin-left:36px;font-family: 'Poppins', sans-serif;  color:rgb(0, 153, 255); ">SERVICE INFORMATION<span style="font-size: 22px;  font-weight:100;">&nbsp;&nbsp;&nbsp;</span><span style="font-weight:400; font-family: 'WindSong', cursive; font-size:33px;"></span></v-card-title>
      <v-card-text>
       
        <v-card-text class="headline text-center" style="font-family: 'Poppins', sans-serif;font-size: 17px; font-weight:500; margin-top:-42px; margin-left:15px; position:absolute;color:#022a80;">
          {{ selectedService.service }} 
        </v-card-text>

        <div style=" margin-left:10px; margin-top:-1px; width:150px;" >
        <v-card-text class="headline text-left" style="">
          <img :src="selectedService.image" style="height:220px; height:220px;" alt="Service Image">
        </v-card-text>
        </div>

        <v-card-text class="headline text-left" style="font-family: 'Poppins', sans-serif;position:absolute; top:70%; left:6%; width:270px; font-size: 13px; font-weight:400; text-align: justify;">

          &nbsp;&nbsp;{{ selectedService.information }}
        
        </v-card-text>
        
        
        
        

        <br>
<!-- filter pa ang table sa startdate na match sa button select date  -->
  <span>
    <v-card-text class="headline text-left" style="position:absolute; top:60%; left:3%; width:350px; font-size: 24px; font-weight:500;color:#3a3a3a;">
      &nbsp;&nbsp;₱&nbsp;{{ displayMinimumPrice }} <span style="font-size: 15px;color:#aaaaaa;"> / minimum price</span>
    </v-card-text>
  </span> 
        
        <span><v-card-text class="headline text-left" style="  font-family: 'Poppins', sans-serif; color: rgb(2, 97, 185);position:absolute; top:3%; left:46%; width:360px; font-size: 16px; font-weight:500;">
          &nbsp;&nbsp;Incremental Cost for Additional Units
         </v-card-text>  </span>
         <v-card-text class="headline text-left" style="font-family: 'Poppins', sans-serif; color: rgb(2, 37, 70); position: absolute; top: 9%; left: 47.5%; width: 322px; font-size: 11.7px; font-weight: 500;">
         Customize your request by adding item based<br>
                     on your preferences. The total price will reflect <br>
                     any additional items accordingly.
        </v-card-text>
        
        <table id="datatable-responsive" class="table table-bordered table-striped dt-responsive nowrap" cellspacing="0" width="80%" style="margin: 0 auto; display:none;">
          <thead>
            <tr>
              
              <th>start_date</th>
              <th>end_date</th>

              <th>service</th>
              <th>status</th>
             
              <th>first_req</th>
              <th>second_req</th>
              <th>third_req</th>
              <th>fourth_req</th>
              <th>fifth_req</th>
              <th>sixth_req</th>
              <th>inputValue</th>
              <th>secondInputValue</th>
              <th>thirdInputValue</th>
              <th>fourthInputValue</th>
              <th>fifthInputValue</th>
              <th>sixthInputValue</th>
            </tr>
          </thead>
          <tbody>
            <!-- <tr v-for="info in info"> -->
              <tr v-for="bookinginfo in bookinginfo" :key="bookinginfo.id">
               
                <td>{{ formatDate(bookinginfo.start_date) }}</td>

                <td>{{ bookinginfo.end_date }}</td>

                <td>{{ bookinginfo.service }}</td>
                <td>{{ bookinginfo.status }}</td>
               
                <td>{{ bookinginfo.first_req }}</td>
                <td>{{ bookinginfo.second_req }}</td>
                <td>{{ bookinginfo.third_req }}</td>
                <td>{{ bookinginfo.fourth_req }}</td>
                <td>{{ bookinginfo.fifth_req }}</td>
                <td>{{ bookinginfo.sixth_req }}</td>
                <td>{{ bookinginfo.inputValue }}</td>
                <td>{{ bookinginfo.secondInputValue }}</td>
                <td>{{ bookinginfo.thirdInputValue }}</td>
                <td>{{ bookinginfo.fourthInputValue }}</td>
                <td>{{ bookinginfo.fifthInputValue }}</td>
                <td>{{ bookinginfo.sixthInputValue }}</td>
                <td>
                    <button @click="editRecord(bookinginfo)" class="btn btn-success btn-sm edit">EDIT</button>
                </td>
            </tr>
          </tbody>
        </table>



        <table id="datatable-responsive" class="table table-bordered table-striped dt-responsive nowrap" cellspacing="0" width="80%" style="margin: 0 auto;display:none;">
          <thead>
            <tr>
              
              <th>start_date</th>
              <th>end_date</th>

              <th>service</th>
              <th>status</th>
             
              <th>first_req</th>
              <th>second_req</th>
              <th>third_req</th>
              <th>fourth_req</th>
              <th>fifth_req</th>
              <th>sixth_req</th>
              <th>inputValue</th>
              <th>secondInputValue</th>
              <th>thirdInputValue</th>
              <th>fourthInputValue</th>
              <th>fifthInputValue</th>
              <th>sixthInputValue</th>
            </tr>
          </thead>
          <tbody>
            <!-- <tr v-for="info in info"> -->
              <tr v-for="bookinginfoallservices in bookinginfoallservices" :key="bookinginfoallservices.id">
               
                <td>{{ formatDate(bookinginfoallservices.start_date) }}</td>

                <td>{{ bookinginfoallservices.end_date }}</td>

                <td>{{ bookinginfoallservices.service }}</td>
                <td>{{ bookinginfoallservices.status }}</td>
               
                <td>{{ bookinginfoallservices.first_req }}</td>
                <td>{{ bookinginfoallservices.second_req }}</td>
                <td>{{ bookinginfoallservices.third_req }}</td>
                <td>{{ bookinginfoallservices.fourth_req }}</td>
                <td>{{ bookinginfoallservices.fifth_req }}</td>
                <td>{{ bookinginfoallservices.sixth_req }}</td>
                <td>{{ bookinginfoallservices.inputValue }}</td>
                <td>{{ bookinginfoallservices.secondInputValue }}</td>
                <td>{{ bookinginfoallservices.thirdInputValue }}</td>
                <td>{{ bookinginfoallservices.fourthInputValue }}</td>
                <td>{{ bookinginfoallservices.fifthInputValue }}</td>
                <td>{{ bookinginfoallservices.sixthInputValue }}</td>
                <td>
                    <button @click="editRecord(bookinginfoallservice)" class="btn btn-success btn-sm edit">EDIT</button>
                </td>
            </tr>
          </tbody>
        </table>


        <table id="datatable-responsive"  cellspacing="0"  style=" font-family: 'Poppins', sans-serif; height:50px; width:340px;top:130px;right:60px; position:absolute; font-size:12px; color:black;">
          <thead>
            <tr>
              <th style=" text-align:center;">ITEM'S</th>
              <th style=" text-align:center;">PRICE</th>
              <th style="width:100px;text-align:center;">QUANTITY</th>
              <th style="width:100px;text-align:center;">STOCK</th>
            </tr>
          </thead>
          <tbody>
            <tr v-if="selectedService.first_req && selectedService.first_req.trim() !== ''" style="height:10px;">
              <td >{{ selectedService.first_req }} </td>
              <td>{{ selectedService.first_price }}</td>
              
              <td> <input type="number" class="search-input"  inputmode="numeric"  style="
                background-color: rgb(255, 255, 255);
                width: 80px;
                height: 30px;
                border-radius:2px;
              " placeholder="0"  v-model="inputValue" @input="updateMinimumPrice" ></td>
              <td style="display:none;">{{ selectedService.first_stock }}</td>
              <td>{{ stockDifferences.first }}</td>
              
            </tr>
            <tr v-if="selectedService.second_req && selectedService.second_req.trim() !== ''" style="height:10px;">
              <td>{{ selectedService.second_req }} </td>
              <td>{{ selectedService.second_price }}</td>
              <td> <input type="number" class="search-input"  inputmode="numeric"  style="
                background-color: rgb(255, 255, 255);
                width: 80px;
                height: 30px;
                border-radius:2px;
              " placeholder="0"   v-model="secondInputValue" @input="updateMinimumPrice" ></td>
              <td style="display:none;">{{ selectedService.second_stock }}</td>
              <td>{{ stockDifferences.second }}</td>
              
            </tr>
            <tr v-if="selectedService.third_req && selectedService.third_req.trim() !== ''" style="height:10px;">
              <td>{{ selectedService.third_req }} </td>
              <td>{{ selectedService.third_price }}</td>
              <td> <input type="number" class="search-input"  inputmode="numeric"  style="
                background-color: rgb(255, 255, 255);
                width: 80px;
                height: 30px;
                border-radius:2px;
              " placeholder="0"   v-model="thirdInputValue" @input="updateMinimumPrice" ></td>
              <td style="display:none;">{{ selectedService.third_stock }}</td>
              <td>{{ stockDifferences.third }}</td>
              
            </tr>
            <tr v-if="selectedService.fourth_req && selectedService.fourth_req.trim() !== ''" style="height:10px;">
              <td>{{ selectedService.fourth_req }} </td>
              <td>{{ selectedService.fourth_price }}</td>
              <td> <input type="number" class="search-input"  inputmode="numeric"  style="
                background-color: rgb(255, 255, 255);
                width: 80px;
                height: 30px;
                border-radius:2px;
              " placeholder="0"   v-model="fourthInputValue" @input="updateMinimumPrice" ></td>
              <td style="display:none;">{{ selectedService.fourth_stock }}</td>
              <td>{{ stockDifferences.fourth }}</td>
              
            </tr>
            <tr v-if="selectedService.fifth_req && selectedService.fifth_req.trim() !== ''" style="height:10px;">
              <td>{{ selectedService.fifth_req }} </td>
              <td>{{ selectedService.fifth_price }}</td>
              <td> <input type="number" class="search-input"  inputmode="numeric"  style="
                background-color: rgb(255, 255, 255);
                width: 80px;
                height: 30px;
                border-radius:2px;
              " placeholder="0"   v-model="fifthInputValue" @input="updateMinimumPrice" ></td>
              <td style="display:none;">{{ selectedService.fifth_stock }}</td>
              <td>{{ stockDifferences.fifth }}</td>
              
            </tr>
            <tr v-if="selectedService.sixth_req && selectedService.sixth_req.trim() !== ''" style="height:10px;">
              <td>{{ selectedService.sixth_req }} </td>
              <td>{{ selectedService.sixth_price }}</td>
              <td> <input type="number" class="search-input"  inputmode="numeric"  style="
                background-color: rgb(255, 255, 255);
                width: 80px;
                height: 30px;
                border-radius:2px;
              " placeholder="0"   v-model="sixthInputValue" @input="updateMinimumPrice" ></td>
              <td style="display:none;">{{ selectedService.sixth_stock }}</td>
              <td>{{ stockDifferences.sixth }}</td>
            </tr>

          </tbody>
        </table>
   
      
      <button
      type="button"
      @click="openDialog(item)"
      class="neumorphic-button"
      :class="{ 'disabled-button': disableButton }"
      :style="buttonStyles"
      :disabled="disableButton"
      style="
        position:absolute;
        background-color: rgb(50, 50, 51);
        width: 150px;
        height: 40px;
        margin-left:490px;
        margin-top: 310px;
        border-radius:3px;
        color:white;
        
      "
    >File Request <span v-if="disableButton" class="question-icon" title="Button is disabled due to reaching the limit of 3 records.">?</span>
    </button>
    <button
      type="button"
      @click="closeDialogs()"
    
      style="
        position:absolute;
        background-color:none;
        width: 45px;
        height: 40px;
        margin-left:676px;
        margin-top: -382px;
        border-radius:3px;
        color:rgb(49, 47, 47);
        font-size:17px;
        
      "
    >&nbsp;&nbsp;🗙 &nbsp;&nbsp;
    </button>

    <li class="menu-item" >
    <a
      type="button"
      @click="openDialogsss()"
      class="neumorphic-button"
      style="
        position:absolute;
        background-color: rgb(255, 255, 255);
        width: 170px;
        height: 40px;
        margin-left: 310px;
        margin-top: 300px;
        border-radius:3px;
      "
    > Show Added Items
    </a>
    <div style="position:absolute; margin-top:231px; margin-left:150px;">
    <!-- <label for="start_date" style="position:absolute;">Select Day for Service Request:</label> -->
    <!-- <input type="date" class="neumorphic-button" style="font-size:13px; width:150px;background-color:white; border-radius:3px;" v-model="start_date" required> -->
    <input type="date" class="neumorphic-button" style="font-size:13px; width:150px;background-color:white; border-radius:3px;" v-model="startDate" required>
    </div>
    </li> 

      </v-card-text>
      <v-card-actions>
      
      </v-card-actions>
    </v-card>
  </form>
</v-dialog>




<v-dialog v-model="dialogssss" max-width="400px">
  <form @submit.prevent="saveBooking" class="container">
    <v-card style="height:430px;">
      <br>
      <v-card-title class="headline text-center" style="height:40px;font-size: 17px; font-weight:700;font-family: 'Poppins', sans-serif;">  ADDED ITEMS</v-card-title>
      <v-card-title class="headline text-center" style="height:40px;font-size: 13px; font-weight:400; margin-top:-15px;color:#0569ff; ">  Price calculation for the addded item</v-card-title>
      <v-card-text>

        <table id="datatable-responsive"  cellspacing="0"  style=" font-family: 'Poppins', sans-serif; height:50px; width:340px;top:70px;right:17px; position:absolute; font-size:12px;">
          <thead>
            <tr>
              <th style=" text-align:center;">ITEM'S</th>
              <th style=" text-align:center;">PRICE</th>
              <th style="width:100px;text-align:center;">QUANTITY</th>
            </tr>
          </thead>
          <tbody>
            <tr v-if="selectedService.first_req && selectedService.first_req.trim() !== ''" style="height:10px; ">
              <td >{{ selectedService.first_req }} </td>
              <td>{{ selectedService.first_price }}</td>
              <td>{{ inputValue || '0' }}</td>
            </tr>
            <tr v-if="selectedService.second_req && selectedService.second_req.trim() !== ''" style="height:10px; ">
              <td>{{ selectedService.second_req }} </td>
              <td>{{ selectedService.second_price }}</td>
              <td>{{ secondInputValue || '0' }}</td>
            </tr>
            <tr v-if="selectedService.third_req && selectedService.third_req.trim() !== ''" style="height:10px; ">
              <td>{{ selectedService.third_req }} </td>
              <td>{{ selectedService.third_price }}</td>
              <td>{{ thirdInputValue || '0' }}</td>
            </tr>
            <tr v-if="selectedService.fourth_req && selectedService.fourth_req.trim() !== ''" style="height:10px; ">
              <td>{{ selectedService.fourth_req }} </td>
              <td>{{ selectedService.fourth_price }}</td>
              <td>{{ fourthInputValue || '0' }}</td>
            </tr>
            <tr v-if="selectedService.fifth_req && selectedService.fifth_req.trim() !== ''" style="height:10px; ">
              <td>{{ selectedService.fifth_req }} </td>
              <td>{{ selectedService.fifth_price }}</td>
              <td>{{ fifthInputValue || '0' }}</td>
            </tr>
            <tr v-if="selectedService.sixth_req && selectedService.sixth_req.trim() !== ''" style="height:10px; ">
              <td>{{ selectedService.sixth_req }} </td>
              <td>{{ selectedService.sixth_price }}</td>
              <td>{{ sixthInputValue || '0' }}</td>
            </tr>
           

          </tbody>
        </table>

       
        <br>
        <div style="position:absolute;">
          <div style="margin-top:225px;">Added items total price: {{ totalSum }}</div>
          <div>Minimum price: {{ selectedService.low_pricing.toLocaleString() }}</div>
          <div>Total cost: {{
              (parseFloat(totalSum) + parseFloat(selectedService.low_pricing))
                  .toFixed(2)
                  .replace(/\.0+$/, '')
                  .toLocaleString()
          }}</div>
      </div>
      
      

        
        <button
        type="button"
        @click="closeDialogsss()"
        class="neumorphic-button"
        style="
          position:absolute;
          background-color: rgb(50, 50, 51);
          width: 115px;
          height: 40px;
          margin-left:214px;
          margin-top: 245px;
          border-radius:3px;
          color:white;
          
        "
      >Done
      </button>
      </v-card-text>
      <v-card-actions>
      
      </v-card-actions>
    </v-card>
  </form>
</v-dialog>

<v-dialog v-model="avail" max-width="900px" style="border-radius:0px;position:absolute;">
  <form @submit.prevent="save_request" class="container">
    <v-card style="height:650px; overflow: hidden;font-family: 'Poppins', sans-serif; font-weight: 600;font-size:11.5px;">

      <div class="calendar-container" style=" position: absolute; left:-375px;top: 25px;">

 <!-- <a style="display: none;">{{ event.event_title }} </a> {{ event.start_date }} <a style="display: none;">to {{ event.end_date }} </a> -->
      <div>
        <v-row>
          <v-col cols="12">
           
            <ul>
              <li v-for="event in approvedRequests" :key="event.id">
              
              <a style="display: none;"> {{ event.start_date }}</a>
              </li>
            </ul>
          </v-col>
        </v-row>

        <div style="position: absolute; top:3px;">
          <tr>
            <th  colspan="7"><a style="font-size:30px; margin-left:8px; font-weight:400;">{{ currentMonth }}</a> <a style="font-size:30px; color:#ffcc5c; font-weight:300; margin-left:10px;">{{ selectedYear }}</a></th>
          </tr>
        </div>
    
        <div style="margin-left:20px; margin-top:30px;">
          <div>
          <label for="month">Select Month:</label><br>
          <select style="width: 100px; background-color: #fff;
          box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);color: rgb(0, 0, 0); border: none; border-radius: 3px; outline: none;" id="month" v-model="selectedMonth" @change="updateCalendar">
            <option v-for="(month, index) in months" :key="index" :value="index">{{ month }}</option>
          </select>
          <i class="fas fa-caret-down arrow-icon" style=" z-index: 2;top:109px; position: absolute; margin-right:309px;"></i>
         
        </div>
        <div style="position: absolute; top:65px; margin-left:300px;">
          <label style="" for="year">Select Year:</label><br>
          <select style="z-index: 1;width: 80px; background-color: #fff;
          box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);color: rgb(0, 0, 0); border: none; border-radius: 3px; outline: none;" id="year" v-model="selectedYear" @change="updateCalendar">
            <option v-for="year in years" :key="year" :value="year">{{ year }}</option>
          </select>
          <i class="fas fa-caret-down arrow-icon" style=" z-index: 2;top:41px; position: absolute; margin-right:14px;"></i>
        </div>
        </div>
    
      
        <div>
          <table style=" margin-left:23px; height:350px; width:380px; ">
            <thead>
              <tr>
                <th v-for="day in days" style="margin-left:2px; width:50px; height:50px; background-color:none;" :key="day">{{ day }}</th>
              </tr>
            </thead>
            <tbody >
              <tr v-for="week in calendar" :key="week">
                <td 
                v-for="day in week" 
                :key="day.number"
                :class="{ 'marked-day': day.marked }" style=" cursor: pointer;"
              >
              <button
              style="width: 30px; height: 30px;"
              @click="openday(day.number)"
            >{{ day.number }}</button>
            
              </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
      </div>

      <div class="calendar-container" style="  box-shadow: 5px 5px 10px #bcbcbc, -5px -5px 10px #ffffff;height:662px; width:400px;position: absolute; left:-780px;top: -10px; background-color:#111213;">
       <div>
       </div>
        <div style="position: absolute;margin-top:-80px; margin-left:100px;">
          <button for="service" style="position:absolute; margin-top:-80px; font-family: 'Stok Web', sans-serif; font-size:160px; font-weight:400;margin-left:-12px; color:#FEAA01;" @click="availability_dialogs()"><i style="color:#FEAA01; font-size:20px;" class="fas fa-calendar custom-icon"></i></button>
          <label for="service" style="margin-top:140px; font-size:35px; font-weight:600; margin-left:40px;color:#ffffff;"> {{ currentDay }}</label><br>
          <label for="service" style="position:absolute; margin-top:-30px; font-family: 'Stok Web', sans-serif; font-size:140px; font-weight:400;margin-left:50px; color:#ffffff;"> {{ currentDayNumber }}</label>
        
        
          <a style="color:#E3E3E3; font-size:14px; position:absolute; margin-left:15px; margin-top:30px; top:65px; font-weight:300;"><a style="color:#FEAA01;font-size:17px;"></a> Today's Event</a>
         
         
          <img v-if="approvedRequests.length === 0" :src="require('../../../public/img/event.png')" style="margin-top:140px; margin-left:42px; width: 150px; height: 150px;" ref="cartGif"> <br>
        <a v-if="approvedRequests.length === 0" style="margin-left:65px;margin-top:-12px;  position:absolute; width: 300px; height: 150px; color: white;" > No Event for Today</a>
         
          <br><br><br><br><br><br><br><br> <li v-for="event in approvedRequests" :key="event.id">

            <div style="margin-top:5px; height:50px; width:220px;opacity:0.2; border-radius:3px; margin-left:10px;  background-color:#eeecec; color:#ffffff;"></div>
        <label for="service" style="position:absolute; margin-top:-38px; width:200px; font-size:15px; font-weight:300; margin-left:35px;  color:#Ffffff;"> {{ event.event_title }}<a style="display: none;">{{ event.start_date }}</a></label>

        </li>
        <div style="margin-top:20px; ">
        <li v-for="event in approvedRequests" :key="event.id">

        
        <a style="color:#E3E3E3; font-size:14px;  margin-left:15px; margin-top:30px;  font-weight:300;"><a style="color:#FEAA01;font-size:17px;">&nbsp;•&nbsp;</a> {{ event.service }}</a>
   
      </li>
      </div>
    </div>



      </div>
              
    </v-card>
  </form>
</v-dialog>

<v-dialog v-model="day_event" max-width="730px" class="modern-dialog">
  <form @submit.prevent="save_event" class="container">
    <v-card class="event-card">
      <h2 class="dialog-title" style="font-family: 'Poppins', sans-serif; margin-left:34px;margin-top:30px; ">{{ formatDate(clickedDate) }}<a style="font-size:15px; font-weight:400; color:#FEAA01;">&nbsp;&nbsp;&nbsp;Event Schedules</a> </h2>
      <h2 class="dialog-title" style="position:absolute; font-size:19px; font-family: 'Poppins', sans-serif; margin-left:414px; margin-top:30px;">
        Available Slot : 
        <a style="display:none; color:#FEAA01;font-size:19px; font-weight:400;">
          {{ matchingEvents.length }}
        </a>
        <a style="color:#FEAA01;font-size:19px; font-weight:400;">
          {{ availableSlotsCount }}
        </a>
        <!-- <a style="font-size:14px; font-weight:400; color:#FEAA01;">&nbsp;&nbsp;&nbsp;</a>  -->
      </h2>
      <div class="event-table-wrapper">
        <table class="event-table" style="width:580px; margin-left:24px; height:280px;  margin-bottom:24px;">
          <thead>
            <tr style="height:60px;">
              <th>Event</th>
              <th>Service</th>
              <th>Start Time</th>
              <th>End Time</th>
              <th>End Date</th>
            </tr>
          </thead>
          <tbody>
            <tr style="height:40px;" v-for="event in matchingEvents" :key="event.id">
              <td style="height:40px;" >{{ event.event_title }}</td>
              <td style="height:40px;" >{{ event.service }}</td>
              <td style="height:40px;" >{{ event.start_time }}</td>
              <td style="height:40px;" >{{ event.end_time }}</td>
              <td style="height:40px;" >{{ event.end_date }}</td>
            </tr>
          </tbody>
        </table>
      </div>

    <div>
      <button @click="openchooseService()" class="neumorphic-button" style="border-radius:3px; margin-left:400px; width: 200px; margin-bottom:30px;" :disabled="disableButton" :style="{ opacity: disableButton ? '0.5' : '1' }">
        <i :class="disableButton ? 'fas fa-question-circle' : 'fas fa-calendar-plus custom-icon'" v-bind:title="disableButton ? 'This day has reached the limit for booking service' : ''"></i>&nbsp;&nbsp;{{ disableButton ? 'Book Service' : 'Book Service' }}
      </button>  

    </div>

    <div>
      <v-btn text @click="toggleDropdown"  style="position:absolute;bottom:30px; margin-left:40px;">{{ selectedService ? selectedService : 'Select Service' }}</v-btn>
      <v-menu v-model="dropdown" offset-y style=" width:200px; margin-left:400px; margin-top:200px;">
        <v-list>
          <v-list-item v-for="(service, index) in servinfo" :key="index" @click="selectService(service)">
            <v-list-item-title>{{ service.service }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>

      <input type="text" v-model="lowPricing" placeholder="Low Pricing" style="display:none; position:absolute; bottom:30px; margin-left:260px; width: 150px; padding: 8px; border: 1px solid #ccc; border-radius: 4px;">
    </div>

    
    </v-card>
  </form>
</v-dialog>



<v-dialog v-model="dialogservice" max-width="850px">

  <form @submit.prevent="saveBooking" class="container">
    <v-card style="height:590px;">
      <br>
      <v-card-title class="headline " style="font-size: 19px; font-weight:600;margin-left:36px;font-family: 'Poppins', sans-serif;  color:rgb(0, 153, 255); ">SERVICE INFROMATION<span style="font-size: 22px;  font-weight:100;">&nbsp;&nbsp;&nbsp;</span><span style="font-weight:400; font-family: 'WindSong', cursive; font-size:33px;"></span></v-card-title>
      <v-card-text>
       
        <v-card-text class="headline text-center" style="font-family: 'Poppins', sans-serif;font-size: 17px; font-weight:500; margin-top:-42px; margin-left:15px; position:absolute;color:#022a80;">
          {{ selectedService.service }} 
        </v-card-text>

        <div style=" margin-left:10px; margin-top:-1px; width:150px;" >
        <v-card-text class="headline text-left" style="">
          <img :src="selectedService.image" style="height:220px; height:220px;" alt="Service Image">
        </v-card-text>
        </div>

        <v-card-text class="headline text-left" style="font-family: 'Poppins', sans-serif;position:absolute; top:70%; left:6%; width:270px; font-size: 13px; font-weight:400; text-align: justify;">

          &nbsp;&nbsp;{{ selectedService.information }}
        
        </v-card-text>
        

        <br>

  <span>
    <v-card-text class="headline text-left" style="position:absolute; top:60%; left:3%; width:350px; font-size: 24px; font-weight:500;color:#3a3a3a;">
      &nbsp;&nbsp;₱&nbsp;{{ displayMinimumPrice }} <span style="font-size: 15px;color:#aaaaaa;"> / minimum price</span>
    </v-card-text>
  </span>
        
        <span><v-card-text class="headline text-left" style="  font-family: 'Poppins', sans-serif; color: rgb(2, 97, 185);position:absolute; top:3%; left:46%; width:360px; font-size: 16px; font-weight:500;">
          &nbsp;&nbsp;Incremental Cost for Additional Units
          <!-- geteventfullrecord bagong retrieved data para sa 3 slot per day na pag babasehan para ma disable file request button -->
         </v-card-text>  </span>
         <v-card-text class="headline text-left" style="font-family: 'Poppins', sans-serif; color: rgb(2, 37, 70); position: absolute; top: 9%; left: 47.5%; width: 322px; font-size: 11.7px; font-weight: 500;">
         Customize your request by adding item based<br>
                     on your preferences. The total price will reflect <br>
                     any additional items accordingly.
        </v-card-text>
        
       
        <table id="datatable-responsive"  cellspacing="0"  style=" font-family: 'Poppins', sans-serif; height:50px; width:340px;top:130px;right:60px; position:absolute; font-size:12px; color:black;">
          <thead>
            <tr>
              <th style=" text-align:center;">ITEM'S</th>
              <th style=" text-align:center;">PRICE</th>
              <th style="width:100px;text-align:center;">QUANTITY</th>
            </tr>
          </thead>
          <tbody>
            <tr v-if="selectedService.first_req && selectedService.first_req.trim() !== ''" style="height:10px;">
              <td >{{ selectedService.first_req }} </td>
              <td>₱{{ selectedService.first_price }}</td>
              <td> <input type="number" class="search-input"  inputmode="numeric"  style="
                background-color: rgb(255, 255, 255);
                width: 80px;
                height: 30px;
                border-radius:2px;
              " placeholder="0"  v-model="inputValue" @input="updateMinimumPrice" ></td>
            </tr>
            <tr v-if="selectedService.second_req && selectedService.second_req.trim() !== ''" style="height:10px;">
              <td>{{ selectedService.second_req }} </td>
              <td>₱{{ selectedService.second_price }}</td>
              <td> <input type="number" class="search-input"  inputmode="numeric"  style="
                background-color: rgb(255, 255, 255);
                width: 80px;
                height: 30px;
                border-radius:2px;
              " placeholder="0"   v-model="secondInputValue" @input="updateMinimumPrice" ></td>
            </tr>
            <tr v-if="selectedService.third_req && selectedService.third_req.trim() !== ''" style="height:10px;">
              <td>{{ selectedService.third_req }} </td>
              <td>₱{{ selectedService.third_price }}</td>
              <td> <input type="number" class="search-input"  inputmode="numeric"  style="
                background-color: rgb(255, 255, 255);
                width: 80px;
                height: 30px;
                border-radius:2px;
              " placeholder="0"   v-model="thirdInputValue" @input="updateMinimumPrice" ></td>
            </tr>
            <tr v-if="selectedService.fourth_req && selectedService.fourth_req.trim() !== ''" style="height:10px;">
              <td>{{ selectedService.fourth_req }} </td>
              <td>₱{{ selectedService.fourth_price }}</td>
              <td> <input type="number" class="search-input"  inputmode="numeric"  style="
                background-color: rgb(255, 255, 255);
                width: 80px;
                height: 30px;
                border-radius:2px;
              " placeholder="0"   v-model="fourthInputValue" @input="updateMinimumPrice" ></td>
            </tr>
            <tr v-if="selectedService.fifth_req && selectedService.fifth_req.trim() !== ''" style="height:10px;">
              <td>{{ selectedService.fifth_req }} </td>
              <td>₱{{ selectedService.fifth_price }}</td>
              <td> <input type="number" class="search-input"  inputmode="numeric"  style="
                background-color: rgb(255, 255, 255);
                width: 80px;
                height: 30px;
                border-radius:2px;
              " placeholder="0"   v-model="fifthInputValue" @input="updateMinimumPrice" ></td>
            </tr>
            <tr v-if="selectedService.sixth_req && selectedService.sixth_req.trim() !== ''" style="height:10px;">
              <td>{{ selectedService.sixth_req }} </td>
              <td>₱{{ selectedService.sixth_price }}</td>
              <td> <input type="number" class="search-input"  inputmode="numeric"  style="
                background-color: rgb(255, 255, 255);
                width: 80px;
                height: 30px;
                border-radius:2px;
              " placeholder="0"   v-model="sixthInputValue" @input="updateMinimumPrice" ></td>
            </tr>

          </tbody>
        </table>
       

      <button
      type="button"
      @click="openDialog(item)"
      class="neumorphic-button"
      style="
        position:absolute;
        background-color: rgb(50, 50, 51);
        width: 155px;
        height: 40px;
        margin-left:520px;
        margin-top: 135px;
        border-radius:3px;
        color:white;
        
      "
    >File Request
    </button>
    <button
      type="button"
      @click="closeDialogs()"
    
      style="
        position:absolute;
        background-color:none;
        width: 48px;
        height: 40px;
        margin-left:686px;
        margin-top: -352px;
        border-radius:3px;
        color:rgb(49, 47, 47);
        font-size:17px;
        
      "
    >&nbsp;&nbsp;🗙 &nbsp;&nbsp;
    </button>

    <li class="menu-item" >
    <a
      type="button"
      @click="openDialogsss()"
      class="neumorphic-button"
      style="
        position:absolute;
        background-color: rgb(255, 255, 255);
        width: 169px;
        height: 40px;
        margin-left: 340px;
        margin-top: 120px;
        border-radius:3px;
      "
    > Show Added Items
    </a>
    </li> 

      </v-card-text>
      <v-card-actions>
      
      </v-card-actions>
    </v-card>
  </form>
</v-dialog>

  </template>
  
  
  <script>
  import axios from 'axios'

  export default {
  data() {
    return {
      bookinginfoallservices: [],
      disableButton: false,
      bookinginfo: [],
      servinfo: [],
      dropdown: false,
      selectedService: null,
      lowPricing: null,
      matchingEvents: [],
      clickedDate: null,
      markedDates: [],
      searchText: '',
      inputValue: "",
      secondInputValue: "",
      thirdInputValue: "",
    fourthInputValue: "",
    fifthInputValue: "",
    sixthInputValue: "",
      selectedServiceInDialog: null,
      selectedService: {},
      selectedService: null,
      retrievedService: "",
      servinfo: [],
      day_event:false,
      avail: false,
      dialogs: false,
      dialogss: false,
      dialogsss: false,
      dialogssss: false,
      dialogservice: false,
      selectedMonth: new Date().getMonth(),
      selectedYear: new Date().getFullYear(),
      days: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'],
      months: [
        'January', 'February', 'March', 'April', 'May', 'June',
        'July', 'August', 'September', 'October', 'November', 'December'
      ],
      approvedRequests: [ /* Your approved events data */ ],
      calendar: [],
      startDate: this.getFormattedDate(new Date()),
        event_title:"", 
        start_date:"", 
        end_date:"", 
        location:"", 
        event_description:"", 
        name:"", 
        email:"", 
        phone:"",
        service:"",
        computedTotalValue: "", 
        meeting_date:"",
        meeting_time:"",
        start_time:"",
        end_time:"",
        info: [],
        first_req:"",
        second_req:"",
        third_req:"",
        fourth_req:"",
        fifth_req:"",
        sixth_req:"",
    }
  },
  computed: {
    
    buttonStyles() {
      return this.disableButton ? { opacity: 0.9 } : {};
    },
    stockDifferences() {
    // Initialize an object to store the differences for each stock item
    const differences = {
      first: this.selectedService.first_stock,
      second: this.selectedService.second_stock,
      third: this.selectedService.third_stock,
      fourth: this.selectedService.fourth_stock,
      fifth: this.selectedService.fifth_stock,
      sixth: this.selectedService.sixth_stock,
    };
    
    // Iterate over the filtered booking info
    this.bookinginfo.forEach(booking => {
      // Subtract input values from the corresponding stock values
      differences.first -= booking.inputValue || 0;
      differences.second -= booking.secondInputValue || 0;
      differences.third -= booking.thirdInputValue || 0;
      differences.fourth -= booking.fourthInputValue || 0;
      differences.fifth -= booking.fifthInputValue || 0;
      differences.sixth -= booking.sixthInputValue || 0;
    });

    // Return the calculated differences
    return differences;
  },
    
    availableSlotsCount() {
    let availableSlots = 3 - this.matchingEvents.length;
    return availableSlots < 0 ? 0 : availableSlots;
  },
    disableButton() {
    return this.matchingEvents.length >= 3;
  },
    currentFormattedDate() {
    const currentDate = new Date();
    const formattedDate = `${currentDate.getFullYear()}-${String(currentDate.getMonth() + 1).padStart(2, '0')}-${String(currentDate.getDate()).padStart(2, '0')}`;
    return formattedDate;
  },

    currentDayNumber() {
      const currentDate = new Date();
      const currentDayNumber = currentDate.getDate();
      return `${currentDayNumber}`;
    },
    shouldShowTable() {
      // Check if at least one input value is greater than 0
      return (
        this.inputValue > 0 || this.secondInputValue > 0 || this.thirdInputValue > 0 ||
        this.fourthInputValue > 0 || this.fifthInputValue > 0 || this.sixthInputValue > 0
      );
    },
    filteredServinfo() {
    const searchText = this.searchText.toLowerCase();
    return this.servinfo.filter(item => {
      return (
        item.service.toLowerCase().includes(searchText) ||
        item.low_pricing.toString().includes(searchText)
        // Add more fields to search if needed
      );
    });
  },
    computedTotal() {
      const sum = parseFloat(this.totalSum) + parseFloat(this.selectedService.low_pricing);
      return sum.toFixed(2).replace(/\.0+$/, '');
    },
  
    first_totalPrice: function() {
      const inputNumber = parseFloat(this.inputValue) || 0;
      const result = inputNumber * this.selectedService.first_price;
      const formattedResult = result % 1 === 0 ? result.toFixed(0) : result.toFixed(2);
      return formattedResult;
    },
    second_totalPrice: function() {
      const inputNumber = parseFloat(this.secondInputValue) || 0;
      const result = inputNumber * this.selectedService.second_price;
      const formattedResult = result % 1 === 0 ? result.toFixed(0) : result.toFixed(2);
      return formattedResult;
    },
    third_totalPrice: function() {
      const inputNumber = parseFloat(this.thirdInputValue) || 0;
      const result = inputNumber * this.selectedService.third_price;
      const formattedResult = result % 1 === 0 ? result.toFixed(0) : result.toFixed(2);
      return formattedResult;
    },
    fourth_totalPrice: function() {
      const inputNumber = parseFloat(this.fourthInputValue) || 0;
      const result = inputNumber * this.selectedService.fourth_price;
      const formattedResult = result % 1 === 0 ? result.toFixed(0) : result.toFixed(2);
      return formattedResult;
    },
    fifth_totalPrice: function() {
      const inputNumber = parseFloat(this.fifthInputValue) || 0;
      const result = inputNumber * this.selectedService.fifth_price;
      const formattedResult = result % 1 === 0 ? result.toFixed(0) : result.toFixed(2);
      return formattedResult;
    },
    sixth_totalPrice: function() {
      const inputNumber = parseFloat(this.sixthInputValue) || 0;
      const result = inputNumber * this.selectedService.sixth_price;
      const formattedResult = result % 1 === 0 ? result.toFixed(0) : result.toFixed(2);
      return formattedResult;
    },
    totalSum: function() {
  const sum =
    parseFloat(this.first_totalPrice) +
    parseFloat(this.second_totalPrice) +
    parseFloat(this.third_totalPrice) +
    parseFloat(this.fourth_totalPrice) +
    parseFloat(this.fifth_totalPrice) +
    parseFloat(this.sixth_totalPrice);

  const formattedSum = sum.toFixed(2).toString();

  // Remove the trailing .00
  const totalWithoutDecimal = formattedSum.endsWith('.00') ? formattedSum.slice(0, -3) : formattedSum;

  return totalWithoutDecimal;
},
    displayMinimumPrice() {
    const firstInputMultiplier = this.inputValue === "" ? 0 : parseInt(this.inputValue);
    const secondInputMultiplier = this.secondInputValue === "" ? 0 : parseInt(this.secondInputValue);
    const thirdInputMultiplier = this.thirdInputValue === "" ? 0 : parseInt(this.thirdInputValue);
    const fourthInputMultiplier = this.fourthInputValue === "" ? 0 : parseInt(this.fourthInputValue);
    const fifthInputMultiplier = this.fifthInputValue === "" ? 0 : parseInt(this.fifthInputValue);
    const sixthInputMultiplier = this.sixthInputValue === "" ? 0 : parseInt(this.sixthInputValue);

    const calculatedPrice =
      firstInputMultiplier * this.selectedService.first_price +
      secondInputMultiplier * this.selectedService.second_price +
      thirdInputMultiplier * this.selectedService.third_price +
      fourthInputMultiplier * this.selectedService.fourth_price +
      fifthInputMultiplier * this.selectedService.fifth_price +
      sixthInputMultiplier * this.selectedService.sixth_price +
      parseInt(this.selectedService.low_pricing);

    return calculatedPrice.toString();
  },
    displaySecondPrice() {
    if (this.secondInputValue === "") {
      return 0; // Default value if no input
    } else {
      return parseInt(this.secondInputValue) * this.selectedService.second_price;
    }
  },
  displayThirdPrice() {
    if (this.thirdInputValue === "") {
      return 0; // Default value if no input
    } else {
      return parseInt(this.thirdInputValue) * this.selectedService.third_price;
    }
  },
  displayFourthPrice() {
    if (this.fourthInputValue === "") {
      return 0; // Default value if no input
    } else {
      return parseInt(this.fourthInputValue) * this.selectedService.fourth_price;
    }
  },
  displayFifthPrice() {
    if (this.fifthInputValue === "") {
      return 0; // Default value if no input
    } else {
      return parseInt(this.fifthInputValue) * this.selectedService.fifth_price;
    }
  },
  displaySixthPrice() {
    if (this.sixthInputValue === "") {
      return 0; // Default value if no input
    } else {
      return parseInt(this.sixthInputValue) * this.selectedService.sixth_price;
    }
  },
    currentMonth() {
      return this.months[this.selectedMonth];
    },
      approvedRequests() {
    const currentDate = new Date();
    const formattedCurrentDate = `${currentDate.getFullYear()}-${String(currentDate.getMonth() + 1).padStart(2, '0')}-${String(currentDate.getDate()).padStart(2, '0')}`;

    return this.info.filter(item => {
      const startDate = new Date(item.start_date);
      const endDate = new Date(item.end_date);

    
      return item.status === 'approved' && currentDate >= startDate && currentDate <= new Date(endDate.getTime() + 86400000);

    });
  },

approvedRequests_perday() {
  const currentDate = new Date();
  const formattedCurrentDate = `${currentDate.getFullYear()}-${String(currentDate.getMonth() + 1).padStart(2, '0')}-${String(currentDate.getDate()).padStart(2, '0')}`;

  return this.info.filter(item => item.status === 'approved'  );
},
    years() {
  const currentYear = new Date().getFullYear();
  const yearsBefore = 10;
  const yearsAfter = 10;
  const years = [];

  for (let i = currentYear - yearsBefore; i <= currentYear + yearsAfter; i++) {
    years.push(i);
  }

  return years;
},
currentDay() {
      const days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];
      const currentDate = new Date();
      const currentDayIndex = currentDate.getDay(); // 0 for Sunday, 1 for Monday, etc.
      return ` ${days[currentDayIndex]}`;
    },
    filteredApprovedRequests() {
    return this.approvedRequests.filter(event => event.start_date === this.currentFormattedDate);
  },
  },
  created() {
    this.getEventInfo();
    this.getbookingInfo();
    this.bookinginfoallservice();
  },
  mounted() {
    this.updateCalendar();
    this.getInfo(); 
  },
  
  watch: {
    bookinginfoallservices: {
      handler(newVal) {
        // Check the length of the bookinginfoallservices array
        this.disableButton = newVal.length >= 3;
      },
      immediate: true, // Run the handler function immediately on initial load
    },
    startDate(newDate) {
    if (newDate) {
      this.getbookingInfo();
    this.bookinginfoallservice();

    }
  },
  selectedService(newService) {
    if (newService) {
      this.getbookingInfo();
    }
  },
    inputValue: function (newValue) {
    // Check if the new input value is negative
    if (newValue < 0) {
      // Display an alert to notify the user
      alert('Input cannot be negative. Please enter a value of 0 or higher.');
      
      // Reset the input value to 0
      this.inputValue = 0;
    } else if (newValue > this.stockDifferences.first) {
      // Check if the new input value exceeds the first_stock value of the selected service
      alert('Input exceeds the limit for first stock.');
      
      // Reset the input value to the maximum allowed value
      this.inputValue = this.stockDifferences.first;
    }
  },
  secondInputValue: function (newValue) {
    if (newValue < 0) {
      alert('Input cannot be negative. Please enter a value of 0 or higher.');
      this.secondInputValue = 0;
    } else if (newValue > this.stockDifferences.second) {
      alert('Input exceeds the limit for second stock.');
      this.secondInputValue = this.stockDifferences.second;
    }
  },
  thirdInputValue: function (newValue) {
    if (newValue < 0) {
      alert('Input cannot be negative. Please enter a value of 0 or higher.');
      this.thirdInputValue = 0;
    } else if (newValue > this.stockDifferences.third) {
      alert('Input exceeds the limit for third stock.');
      this.thirdInputValue = this.stockDifferences.third;
    }
  },
  fourthInputValue: function (newValue) {
    if (newValue < 0) {
      alert('Input cannot be negative. Please enter a value of 0 or higher.');
      this.fourthInputValue = 0;
    } else if (newValue > this.stockDifferences.fourth) {
      alert('Input exceeds the limit for fourth stock.');
      this.fourthInputValue = this.stockDifferences.fourth;
    }
  },
  fifthInputValue: function (newValue) {
    if (newValue < 0) {
      alert('Input cannot be negative. Please enter a value of 0 or higher.');
      this.fifthInputValue = 0;
    } else if (newValue > this.stockDifferences.fifth) {
      alert('Input exceeds the limit for fifth stock.');
      this.fifthInputValue = this.stockDifferences.fifth;
    }
  },
  sixthInputValue: function (newValue) {
    if (newValue < 0) {
      alert('Input cannot be negative. Please enter a value of 0 or higher.');
      this.sixthInputValue = 0;
    } else if (newValue > this.stockDifferences.sixth) {
      alert('Input exceeds the limit for sixth stock.');
      this.sixthInputValue = this.stockDifferences.sixth;
    }
  },
},
  methods: {
    openDialog(item) {
      if (!this.disableButton) {
        this.dialogs = true;
      }
    },
    formatDate(dateString) {
    const date = new Date(dateString);
    const options = { year: 'numeric', month: '2-digit', day: '2-digit' };
    return date.toLocaleDateString(undefined, options);
  },
  async getbookingInfo() {
  try {
    const response = await axios.get('geteventforslot');
  
    const filteredBookingInfo = response.data.filter(
      booking =>
        booking.status === 'approved' &&
        booking.service === this.selectedService.service &&
       
        new Date(this.startDate) >= new Date(booking.start_date) &&
        new Date(this.startDate) <= new Date(booking.end_date)
    );
    this.bookinginfo = filteredBookingInfo;
  } catch (error) {
    console.error(error);
  }
},
async bookinginfoallservice() {
  try {
    const response = await axios.get('geteventfullrecord');
  
    const filteredBookingInfo = response.data.filter(
      booking =>
        booking.status === 'approved' &&
       
        new Date(this.startDate) >= new Date(booking.start_date) &&
        new Date(this.startDate) <= new Date(booking.end_date)
    );
    this.bookinginfoallservices = filteredBookingInfo;
  } catch (error) {
    console.error(error);
  }
},
    getFormattedDate(date) {
      const year = date.getFullYear();
      let month = (1 + date.getMonth()).toString().padStart(2, '0');
      let day = date.getDate().toString().padStart(2, '0');

      return `${year}-${month}-${day}`;
    },
    async getInfo() {
      try {
        const response = await axios.get('getservice');
        this.servinfo = response.data;
      } catch (error) {
        console.error(error);
      }
    },
    toggleDropdown() {
      this.dropdown = !this.dropdown;
    },
    selectService(service) {
      this.selectedService = service.service;
      this.lowPricing = service.low_pricing;
    },
    formatDate(dateString) {
  const options = { year: 'numeric', month: 'long', day: 'numeric' };
  const date = new Date(dateString);
  return date.toLocaleDateString(undefined, options);
},
    availability_dialog()
    {
      this.avail = true;
    },

    availability_dialogs()
    {
      this.avail = false;
    },
    openday(day) {
      this.clickedDate = `${this.selectedYear}-${String(this.selectedMonth + 1).padStart(2, '0')}-${String(day).padStart(2, '0')}`;
      
      // Filter events that match the date range
      this.matchingEvents = this.approvedRequests_perday.filter(event => {
        const startDate = new Date(event.start_date);
        const endDate = new Date(event.end_date);
        const clickedDate = new Date(this.clickedDate);
        return clickedDate >= startDate && clickedDate <= endDate;
      });

      this.day_event = true; // Open the dialog
    },
    updateSearch() {
    // You can add additional functionality here if needed
  },
    updateMinimumPrice() {
  
},
   

    async getInfo() {
      try {
        const response = await axios.get('getservice');
        this.servinfo = response.data;
      } catch (error) {
        console.error(error);
      }
    }, 


  openchooseService() {
    this.dialogservice = true;
  },
    closeDialog() {
      this.dialogs = false;
    },
    openDialogs(item) {
      this.selectedService = item; // Set the selected service information
      this.dialogss = true; // Open the dialog
    },

    closeDialogs() {
      this.dialogss = false;
    },
    openDialogss(req) {
      this.dialogsss = true;
      this.retrievedService = req;
    },

    closeDialogss() {
      this.dialogsss = false;
    },
    
    openDialogsss() {
      this.dialogssss = true;
    },

    closeDialogsss() {
      this.dialogssss = false;
    },
    updateCalendar() {
  const firstDay = new Date(this.selectedYear, this.selectedMonth, 1).getDay();
  const lastDate = new Date(this.selectedYear, this.selectedMonth + 1, 0).getDate();
  const calendar = [];
  let date = 1;

  for (let i = 0; i < 6; i++) {
    const week = [];

    for (let j = 0; j < 7; j++) {
      if (i === 0 && j < firstDay) {
        week.push({ number: '', marked: false });
      } else if (date > lastDate) {
        break;
      } else {
        const currentDate = new Date(this.selectedYear, this.selectedMonth, date);
        const isMarked = this.isDateMarked(currentDate);

        week.push({
          number: date,
          marked: isMarked,
        });

        date++;
      }
    }

    calendar.push(week);
    if (date > lastDate) break;
  }

  this.calendar = calendar;
},

isDateMarked(date) {
  const formattedDate = `${date.getFullYear()}-${String(date.getMonth() + 1).padStart(2, '0')}-${String(date.getDate()).padStart(2, '0')}`;
  return this.markedDates.includes(formattedDate) && date >= new Date(this.selectedYear, this.selectedMonth, 1) && date <= new Date(this.selectedYear, this.selectedMonth + 1, 0);
},


 
 
    async approveEvent() {
    try {
      const response = await axios.post('/updateEventStatus', {
        id: this.selectedEvent.id,
        status: 'approved'
      });

      if (response.status === 200) {
        // Update the status in the selectedEvent object
        this.showModal = false; // Close the modal after approval
        this.selectedEvent.status = 'approved';
        this.getEventInfo();

        // Find the index of the updated event in the info array and update it
        const index = this.info.findIndex(event => event.id === this.selectedEvent.id);
        if (index !== -1) {
          this.$set(this.info, index, { ...this.selectedEvent });
        }

        this.showModal = false; // Close the modal
      } else {
        console.error('Error updating event status');
      }
    } catch (error) {
      console.error('Error updating event status:', error);
    }
  },


  async getEventInfo() {
      try {
        const response = await axios.get('getevent');
        this.info = response.data;

        // Filter events with status "approved" and update markedDates array
       this.markedDates = this.info
  .filter(event => event.status === 'approved')
  .flatMap(event => {
    const startDate = new Date(event.start_date);
    const endDate = new Date(event.end_date);
    const dateRange = [];

    // Loop through the date range and add each date to the array
    for (let date = startDate; date <= endDate; date.setDate(date.getDate() + 1)) {
      dateRange.push(date.toISOString().split('T')[0]); // Format as "YYYY-MM-DD"
    }

    return dateRange;
  });

// Remove duplicates from markedDates array
this.markedDates = [...new Set(this.markedDates)];

// Call updateCalendar to refresh the calendar with the new marked dates
this.updateCalendar();
      } catch (error) {
        console.error(error);
      }
    },

async saveBooking() {
  try {
    // Display a confirmation dialog
    const userConfirmed = window.confirm('Are you sure you want to save?');

    // Check if the user clicked OK
    if (userConfirmed) {
      const ins = await axios.post("saveBooking", {
        event_title: this.event_title,
        start_date: this.start_date,
        end_date: this.end_date,
        location: this.location,
        event_description: this.event_description,
        name: this.name,
        email: this.email,
        phone: this.phone,
        service: this.selectedService.service,
        computedTotal: this.computedTotal,
        meeting_date: this.meeting_date,
        meeting_time: this.meeting_time, // Ensure both date and time are included
        start_time: this.start_time, // Include AM/PM information
        end_time: this.end_time, // Include AM/PM information
        additionalData: {
          // Include additional data here
          first_req: this.selectedService.first_req,
          second_req: this.selectedService.second_req,
          third_req: this.selectedService.third_req,
          fourth_req: this.selectedService.fourth_req,
          fifth_req: this.selectedService.fifth_req,
          sixth_req: this.selectedService.sixth_req,
          inputValue: this.inputValue,
          secondInputValue: this.secondInputValue,
          thirdInputValue: this.thirdInputValue,
          fourthInputValue: this.fourthInputValue,
          fifthInputValue: this.fifthInputValue,
          sixthInputValue: this.sixthInputValue,
        },
      });

      // Clear form fields after successful save
      this.event_title = "";
      this.start_date = "";
      this.end_date = "";
      this.location = "";
      this.event_description = "";
      this.name = "";
      this.email = "";
      this.phone = "";
      this.service = "";
      this.computedTotal = "";
      this.meeting_date = "";
      this.meeting_time = "";
      this.start_time = "";
      this.end_time = "";
       this.selectedService.first_req = "";
       this.selectedService.second_req = "";
       this.selectedService.third_req = "";
       this.selectedService.fourth_req = "";
       this.selectedService.fifth_req = "";
       this.selectedService.sixth_req = "";
       this.inputValue = "";
       this.secondInputValue = "";
       this.thirdInputValue = "";
       this.fourthInputValue = "";
       this.fifthInputValue = "";
       this.sixthInputValue = "";

      // Emit event and perform other actions
      this.$emit('data-saved');

      this.dialogs = false;
      this.dialogss = false;
    }
    // If the user clicked Cancel, do nothing
  } catch (error) {
    console.error(error);
  }
},

  }
};
  </script>
  
  <style scoped> 
  .room-item {
    background-color: #ffffff;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
    transition: transform 0.3s ease-in-out;
  }
  
  .room-item:hover {
    background-color: rgba(250, 164, 4, 0.993);
    transform: scale(1.05);
  }
  .calendar-container {
    position: absolute;
    margin-left: 700px;
    top: 160px;
   
    border-radius: 4px; /* Rounded corners */
    padding: 20px;
  }

  .calendar-container {
    position: absolute;
    margin-left: 700px;
    top: 160px;
    background-color: rgba(255, 255, 255, 0.5); /* Transparent background */
    backdrop-filter: blur(10px); /* Adding blur effect */
    border-radius: 4px; /* Rounded corners */
    padding: 20px;
  }

  /* Select boxes */
  select {
    padding: 8px;
    border-radius: 4px;
    border: 1px solid rgba(255, 255, 255, 0.5); /* Transparent border */
    margin-right: 10px;
    background-color: rgba(255, 255, 255, 0.3); /* Transparent background for select */
  }

  /* Table styles */
  table {
    width: 400px;
    height: 400px;
    border-collapse: collapse;
    margin-top: 15px;
    backdrop-filter: blur(5px); /* Adding blur effect */
    border-radius: 4px; /* Rounded corners */
    border: 1px solid rgba(255, 255, 255, 0.3); /* Transparent border */
  }

  th {
    padding: 10px;
    text-align: center;
    background-color: rgba(255, 255, 255, 0.3); /* Transparent background for table header */
  }

  td {
    padding: 10px;
    text-align: center;
    border: 1px solid rgba(255, 255, 255, 0.3); /* Transparent border */
    background-color: rgba(255, 255, 255, 0.2); /* Transparent background for table cell */
  }

 
  .glass-effect {
    padding: 8px;
    border-radius: 4px;
    border: 1px solid rgba(255, 255, 255, 0.5); /* Transparent border */
    margin-right: 10px;
    background-color: rgba(255, 255, 255, 0.3); /* Transparent background */
    backdrop-filter: blur(5px); /* Adding blur effect */
  }
  
  /* Styling for the calendar background image */
  .calendar-container table {
    width: 380px;
    height: 380px;
    border-collapse: collapse;
    margin-top: 15px;
    backdrop-filter: blur(5px); /* Adding blur effect */
    border-radius: 4px; /* Rounded corners */
    border: 1px solid rgba(255, 255, 255, 0.3); /* Transparent border */
    background-size: cover;
    background-repeat: no-repeat;
    position: relative;
  }
  
  @import 'https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css';
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
  .modern-dialog {
    position: absolute;
  }
  
  .event-card {
    background-color: #f9f9f9;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  .dialog-title {
    font-size: 22px;
    font-weight: 600;
    margin-top: 20px;
    margin-bottom: 15px;
    color: #333;
  }
  
  .event-table-wrapper {
    overflow-x: auto;
  }
  
  .event-table {
   
    border-collapse: collapse;
  }
  
  .event-table th,
  .event-table td {
    padding: 12px;
    text-align: center;
  }
  
  .event-table th {
    background-color: #e0e0e0;
    color: #333;
    font-weight: 500;
  }
  
  .event-table td {
    background-color: #fff;
    color: #555;
  }
  
  .event-table tbody tr:nth-child(even) {
    background-color: #f5f5f5;
  }
  
  .event-table tbody tr:hover {
    background-color: #fafafa;
  }
  
  .marked-day {
    background-color: #ffa600fa; /* or any other style you prefer */
    border:0px;
    width: 10px; /* Set the width of the element */
    height: 10px; /* Set the height of the element */
    border-radius: 50%;
    color: #ffffff;
  
    
  
   box-shadow: 5px 5px 10px #bcbcbc; 
   
  
}

  
  </style>