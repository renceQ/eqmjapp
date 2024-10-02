<template>
  <div v-show="showDescription" style="position: absolute; z-index: 9999;">
    <nav
      class="neumorphic-navbar"
      style="opacity: 0; /* Set initial opacity to 0 for fade-in effect */
        animation: fade-up .8s ease-out forwards;
        animation-delay: 0.4s; border-radius: 5px; height: 490px; width: 450px; overflow-y: auto;
        display: flex; flex-direction: column; justify-content: flex-start;
        align-items: flex-start; margin-top: 60px; margin-left: 13%;"
    >
    <div style="width:400px;">
    <p style="margin-left: 20px; margin-top: 20px; font-size: 14px; font-weight:700;">PRODUCT SPECIFICATION: <br><br><span style=" font-weight:200;font-size:14px; color:rgb(240, 141, 29);"> <span style="color: gray;">Stock: </span><span style="color: black;">&nbsp;&nbsp;{{ productData.stock }}</span></span></p>
    <p style="margin-left: 20px; font-size: 14px; font-weight:700;"><span style=" font-weight:200;font-size:14px; color:rgb(240, 141, 29);"> <span style="color: gray;">Category: </span><span style="color: black;">&nbsp;&nbsp;{{ getCategoryName(productData.category_id) }}</span></span></p>
    <p style="margin-left: 20px; font-size: 14px; font-weight:700;"><span style=" font-weight:200;font-size:14px; color:rgb(240, 141, 29);"> <span style="color: gray;">Ships From: </span><span style="color: black;">&nbsp;&nbsp;{{ productData.ships }}</span></span></p><br>
    <p style="margin-left: 20px; margin-top: 20px; font-size: 14px; font-weight:700;">PRODUCT DESCRIPTION: <br><br><span style=" font-weight:200;font-size:14px; color:rgb(240, 141, 29);"> {{ productData.product_description }}</span></p>
  </div>
     
      
      <router-link
      to="#"
      @click="toggleDescription"
      style="position: fixed; bottom: 34px; width: 150px; right: 35px; font-size: 14px; font-weight: 400; font-size: 11px; background-color:green; color: rgb(255, 255, 255)"
      class="neumorphic-button"
    >
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PRODUCT INFO
    </router-link>
    </nav>
  </div>





  <div  v-if="showReviews" style="">
  <button
  to="#"
  @click="toggleReviews"
  style="opacity: 0; /* Set initial opacity to 0 for fade-in effect */
  animation: fade-up .8s ease-out forwards;
  animation-delay: 0.4s; position: fixed; bottom: 80px; left: 440px; width: 150px; font-size: 14px;border-radius:3px; font-weight:200; font-size: 11px; background-color: green; color: rgb(255, 255, 255); z-index: 1000;"
  class="neumorphic-button">
   PRODUCT INFO
</button>
</div>
<div  v-if="showReviews" style="">

</div>



  <div v-if="showReviews" style="position: relative; z-index: 100;">
  <nav
  class="neumorphic-navbar"
  style="opacity: 0; /* Set initial opacity to 0 for fade-in effect */
    animation: fade-up .8s ease-out forwards;
    animation-delay: 0.4s; border-radius: 5px; height: 490px; width: 450px; overflow-y: auto;
    display: flex; flex-direction: column; justify-content: flex-start;
    align-items: flex-start; margin-top: 60px; margin-left: 13%;"
>
<p
to="#"

style="font-weight:600; opacity: 0; /* Set initial opacity to 0 for fade-in effect */
animation: fade-up .8s ease-out forwards;
animation-delay: 0.4s; position: fixed; top: 20px; left: 30px; width: 150px; font-size: 12px; border-radius:3px;  background-color:none; color:rgb(240, 141, 29);"
>
 PRODUCT RATINGS 
</p>
<p
to="#"

style="font-weight:600; opacity: 0; /* Set initial opacity to 0 for fade-in effect */
animation: fade-up .8s ease-out forwards;
animation-delay: 0.4s; position: fixed; top: 20px; left: 160px; width: 150px; font-size: 12px; border-radius:3px;  background-color:none; color:rgb(0, 0, 0); "
>
({{ calculateAverageRating() }}) out of 5<span style="color: yellow; font-size: 14px;">
{{ calculateStarRating() }}
</span>
</p>


<div style="display: flex; justify-content: space-between;">
<button @click="selectRating('all')" type="button" class="neumorphic-button" style="opacity: 0; animation: fade-up .8s ease-out forwards; animation-delay: 0.2s; background-color: rgb(255, 255, 255);  height: 40px; margin-left: 30px; width: 110px; border-radius: 2px; margin-top: 33px;">
  <span style="margin-top: 10px; font-size: 11px; font-weight: 700;"> All  ({{ filteredProducts.length }}) </span>
</button>
<button @click="selectRating('Excellent')" class="neumorphic-button" style="opacity: 0; animation: fade-up .8s ease-out forwards; animation-delay: 0.2s; background-color: rgb(255, 255, 255);  height: 40px; margin-left: 15px; width: 110px; border-radius: 2px; margin-top: 33px;">
  <span style="margin-top: 10px; font-size: 11px; font-weight: 700;"> 5 Star ({{ getCountByRating('Excellent') }}) </span>
</button>
<button @click="selectRating('Great')" type="button" class="neumorphic-button" style="opacity: 0; animation: fade-up .8s ease-out forwards; animation-delay: 0.2s; background-color: rgb(255, 255, 255);  height: 40px; margin-left: 15px; width: 110px; border-radius: 2px; margin-top: 33px;">
  <span style="margin-top: 10px; font-size: 11px; font-weight: 700;"> 4 Star ({{ getCountByRating('Great') }}) </span>
</button>
</div>

<div style="display: flex; justify-content: space-between;">
<button @click="selectRating('Average')" type="button" class="neumorphic-button" style="opacity: 0; animation: fade-up .8s ease-out forwards; animation-delay: 0.2s; background-color: rgb(255, 255, 255);  height: 40px; margin-left: 30px; width: 110px; border-radius: 2px; margin-top: 10px;">
  <span style="margin-top: 10px; font-size: 11px; font-weight: 700;"> 3 Star ({{ getCountByRating('Average') }}) </span>
</button>
<button @click="selectRating('Poor')" type="button" class="neumorphic-button" style="opacity: 0; animation: fade-up .8s ease-out forwards; animation-delay: 0.2s; background-color: rgb(255, 255, 255);  height: 40px; margin-left: 15px; width: 110px; border-radius: 2px; margin-top: 10px;">
  <span style="margin-top: 10px; font-size: 11px; font-weight: 700;"> 2 Star ({{ getCountByRating('Poor') }}) </span>
</button>
<button @click="selectRating('Bad')" type="button" class="neumorphic-button" style="opacity: 0; animation: fade-up .8s ease-out forwards; animation-delay: 0.2s; background-color: rgb(255, 255, 255);  height: 40px; margin-left: 15px; width: 110px; border-radius: 2px; margin-top: 10px;">
  <span style="margin-top: 10px; font-size: 11px; font-weight: 700;"> 1 Star ({{ getCountByRating('Bad') }}) </span>
</button>

</div>





<div  v-for="product in filteredProducts" :key="product.product_id" style="width: 350px; margin-left:20px; margin-top:15px;">

  <img style="width:50px; height:50px; margin-bottom:15px; margin-top:3px;" v-if="info.length > 0" :src="product.profile_picture" alt="Profile" class="profile-picture-navbar">
  
  <span style="font-weight:900;" v-if="info.length > 0 && product.isAnonymous === 'anonymous'">&nbsp;&nbsp; &nbsp;&nbsp;******</span>
  <span style="position:absolute; margin-top:15px;font-family: 'Sacramento', cursive; font-weight:600; font-size:22px;" v-else>&nbsp;&nbsp; &nbsp;&nbsp;{{ product.username }}</span>

  <p>ordered item: {{ product.prod_name }}</p>
  <p>Comment:</p>
  <p>{{ product.comment }}</p>
  <!-- Add other fields as needed -->
  <img v-if="product.first_image" style="height:100px; width:100px;margin-right:10px;" :src="product.first_image" />
  <img v-if="product.second_image" style="height:100px; width:100px;margin-right:10px;" :src="product.second_image" />
  <img v-if="product.third_image" style="height:100px; width:100px;" :src="product.third_image" />      
  <div>
    <br>
    <p style="display: none;">Product ID: {{ product.product_id }}</p>
    <p style="display: none;">Rate: {{ product.rate }}</p>
    <div v-if="product.rate === 'Bad'">
      
      <p>Rate:&nbsp;&nbsp;<span style="color: yellow; font-size:20px;">★ &nbsp;&nbsp;<span style="color: black; font-size:14px;">Bad</span></span></p>
    </div>
    <div v-else-if="product.rate === 'Poor'">
      
      <p> Rate:&nbsp;&nbsp;<span style="color: yellow; font-size:20px;">★★ &nbsp;&nbsp;<span style="color: black; font-size:14px;">Poor</span></span></p>
    </div>
    <div v-else-if="product.rate === 'Average'">
 
      <p> Rate:&nbsp;&nbsp;<span style="color: yellow; font-size:20px;">★★★ &nbsp;&nbsp;<span style="color: black; font-size:14px;">Average</span></span></p>
    </div>
    <div v-else-if="product.rate === 'Great'">
     
      <p> Rate:&nbsp;&nbsp;<span style="color: yellow; font-size:20px;">★★★★ &nbsp;&nbsp;<span style="color: black; font-size:14px;">Great</span></span></p>
    </div>
    <div v-else-if="product.rate === 'Excellent'">
     
      <p> Rate:&nbsp;&nbsp;<span style="color: yellow; font-size:20px;">★★★★★ &nbsp;&nbsp;<span style="color: black; font-size:14px;">Excellent</span></span></p>
    </div>
    <p style="display: none;">Anonymous: {{ product.isAnonymous }}</p>
  </div>
  <hr />
</div>
</nav>
</div>





<br>
  <div class="container mt-4" style=" opacity: 0; /* Set initial opacity to 0 for fade-in effect */
  animation: fade-up .8s ease-out forwards;
  animation-delay: 0.3s;margin-left:270px; height:200px;">
    <h2 style="margin-left:450px; font-size:30px; margin-top:70px; font-family: 'Bebas Neue', cursive; ">ORDER FORM</h2>
    <form @submit.prevent="placeOrder">
    <div class="row">
      <div class="col">
        <div style="display: none;">
          <p>Image:</p>
          <img :src="productData.image" alt="Product Image" class="img-fluid" style="max-width: 200px; max-height: 200px;">
          <p>Product Name: <a style="font-size: 10px;">{{ productData.prod_name }}</a></p>
          <p>Unit Price: ₱{{ productData.unit_price }}</p>
          <p>size : {{ getSizeName(productData.size_id) }}</p> 
      </div>
        <div class="mb-3" style="position:absolute; left:-5.5%;">
          <p>Quantity:</p>
          <div class="btn-group" role="group" aria-label="Quantity">
            <button @click="decreaseQuantity" type="button" class="neumorphic-button" style="height:38px;width:40px;">-</button>
            <p class="btn">{{ quantity }}</p>
            <button @click="increaseQuantity" type="button" class="neumorphic-button" style="height:38px;width:40px;">+</button>
          </div>
        </div>
          <!--hidden fields-->
          <input type="hidden" v-model="productData.id">
          <input type="hidden" v-model="productData.category_id">
          <input type="hidden" v-model="productData.transaction_code">

          <div style=" position:absolute; top:-39.3%; left:30%;">
            <h5 style="margin-top:30%; font-weight:900; font-size:15px;">CONTACT<span style="font-size: 22px;  font-weight:100;">&nbsp;&nbsp;|&nbsp;</span><span style="font-weight:400; font-family: 'WindSong', cursive; font-size:33px;">Details</span></h5>
            <div style="margin-top: 20px;">
              <div v-for="userData in info" :key="userData.id" class="user-profile">
                <div class="profile-details">
                  <div class="row">
                    <div class="col-sm-6">
                        
                     <input type="text" v-model="userData.address" placeholder="Enter Address" class="search-input" style="border: 0px; height:43px;" required>
                    </div>
                  </div>
                  <div class="row">
                    <div class="col-sm-6">
                      <input type="text" v-model="userData.contact" placeholder="Enter Contact" class="search-input" style="border: 0px; height:43px;" required>
                     </div>
                  </div>
                  <div class="row">
                    <div class="col-sm-6">
                      <input type="text" v-model="userData.other_info" placeholder="Enter Other Information"  class="search-input" style="border: 0px; height:43px;" required>
                      <input type="hidden" v-model="userData.token" placeholder="Enter Other Information"  class="search-input" style="border: 0px; height:43px;" required>
                  </div>

                <div class="row">
                  <div class="col-sm-6">
                    <input  type="text" id="customerName" v-model="userData.username" placeholder="customer name"  class="search-input" style="border: 0px; height:43px;" required>
                  </div>
                </div>











            </div>
            <div style="margin-top: 30px;">
              <a style="position: absolute; font-size:15px; margin-left:-40px; margin-top:-20px;">Shipping Fee:&nbsp;&nbsp; ₱ &nbsp;{{ shippingFee }}</a>
                                                                                                                                                <!-- isama shipping lang sa pag submit   --> 
            </div>
            <div>
              <a style="position: absolute; font-size:15px; color:red; margin-left:-40px; margin-top:8px;">Total Price:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ₱</a>
              <input type="text" style="border:0px; font-size:15px; color:red; position: absolute;margin-left:75px;" v-model="productData.total" placeholder="total price" disabled> 
            </div>
                  <div>
                    <a style="position: absolute; font-size:15px; color:red; margin-left:-40px; margin-top:26px;">Total Price:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ₱</a>
                    <input type="text" style="border:0px; font-size:15px; color:red; margin-top:18px;position: absolute;margin-left:75px;" v-model="productData.totalplusshipping" placeholder="total price" disabled> 
                  </div>
                </div>
              </div>
              
            
            </div>
          </div>

        <div >
          <br>
          <br>
          <div class="row" style="margin-top:200px;">
            <button1 @click="opendialog"  style=" position: absolute; border-radius:5px; width:32%; width:152px; right:83%; top:85%; background-color:rgb(32, 32, 32); color:white;" class="neumorphic-button">&nbsp;&nbsp;&nbsp;Payment Method</button1>
            <div class="row" style="margin-top:90px; margin-left:17%;">

          <!-- <button1 @click="placeOrder('cart')" type="submit" style=" border-radius:5px; width:24%;  margin-right:2%; margin-bottom:3%; " class="neumorphic-button">&nbsp;&nbsp;<i class="fas fa-shopping-cart custom-icon"></i>&nbsp;&nbsp;Add to Cart</button1> -->
          <!-- <button1 @click="placeOrder('pending')" type="submit" style="  border-radius:5px;width:24%;  margin-bottom:3%;" class="neumorphic-button">&nbsp;&nbsp;<i class="fas fa-shopping-bag custom-icon"></i>&nbsp;&nbsp;Place Order</button1> -->
          <button1 @click="placeOrder('cart')" type="submit" style=" border-radius:5px; width:24%;  margin-right:2%; margin-bottom:3%; " class="neumorphic-button">&nbsp;&nbsp;<i class="fas fa-shopping-cart custom-icon"></i>&nbsp;&nbsp;Add to Cart</button1>
          <button1 @click="open" type="submit" style="  border-radius:5px;width:24%;  margin-bottom:3%;" class="neumorphic-button">&nbsp;&nbsp;<i class="fas fa-shopping-bag custom-icon"></i>&nbsp;&nbsp;Place Order</button1>
        </div>

          
          </div>
        </div>
        </div>
      </div>
    </form>
    </div>





    <v-dialog v-model="dialogsss" persistent max-width="600"  >
      <v-card>
        <v-card-text style="height: 495px;">
          <form @submit.prevent="placeOrder">
            <div>
              <div
              class="neumorphic-navbars" style="width:200px; height:200px; margin-left:-500px; margin-top:-30%;" >
             
               <img :src="productData.image" alt="Product Image" class="img-fluid" style="position:absolute; max-width: 170px; max-height: 170px; left:6.5%
               ;top:6.5%;">

            </div>
            </div>
        
            <div>
             <p style="position:absolute; left:43%; top:12%; font-size: 11px; font-weight:600; font-family: 'Audiowide', cursive;">PRODUCT NAME: <a style="font-size: 22px; color:darkorange;font-family: 'Poppins', sans-serif;">&nbsp;&nbsp;{{ productData.prod_name }}</a></p>
             <p style="position:absolute; left:43%; top:19.5%; font-size: 11px; font-weight:600; font-family: 'Audiowide', cursive;">SIZE:  <a style="font-size: 14px;font-family:'Courier New', Courier, monospace; color:darkorange;">&nbsp; {{ getSizeName(productData.size_id) }}</a></p>
             <p style="position:absolute; left:10%; bottom:12%; font-size: 11px; font-weight:600; font-family: 'Audiowide', cursive;">UNIT PRICE:  <a style="font-size: 14px;font-family:'Courier New', Courier, monospace; color:darkorange;">&nbsp;&nbsp;₱&nbsp;{{ productData.unit_price }}</a></p>
             <p style="position:absolute; left:10%; bottom:7%; font-size: 11px; font-weight:600; font-family: 'Audiowide', cursive;">SHIPPING FEE:  <a style="font-size: 14px;font-family:'Courier New', Courier, monospace; color:darkorange;">&nbsp;  ₱ {{ shippingFee }}</a></p>
             <p style="position:absolute; left:10%; bottom:2%; font-size: 11px; font-weight:600; font-family: 'Audiowide', cursive;">TOTAL PRICE:  <a style="font-size: 14px;font-family:'Courier New', Courier, monospace; color:darkorange;">&nbsp;  ₱ {{ totalPrice }}</a></p>

            
            </div>
            
            <div class="mb-3" style="position:absolute; left:43%; top:26%;">
              <p style=" font-size: 11px; font-weight:600; font-family: 'Audiowide', cursive;">QUANTITY:</p>
              <div class="btn-group" role="group" aria-label="Quantity">
                <button @click="decreaseQuantity" type="button" class="neumorphic-button" style="height:38px;width:40px; border-radius:4px;">-</button>
                <p class="btn">{{ quantity }}</p>
                <button @click="increaseQuantity" type="button" class="neumorphic-button" style="height:38px;width:40px; border-radius:4px;">+</button>
              </div>
               <!--hidden fields-->
          <input type="hidden" v-model="productData.id">
          <input type="hidden" v-model="productData.category_id">
          <input type="hidden" v-model="productData.transaction_code">
            </div>


            <div v-for="userData in info" :key="userData.id" class="user-profile" style="position:absolute;margin-top:-20px;">
              <br><br>
              <a style="position:absolute;margin-top:70px; left:-233%;width:200px;font-weight:600; font-family: 'Audiowide', cursive; font-size:11px;">DELIVERY ADDRESS:</a>
              <input type="text" v-model="userData.address" placeholder="Enter Address" class="search-input" style="border: 0px; height:43px; position:absolute;left:-220%; margin-top:170px;" readonly>
              <a style="position:absolute;margin-top:70px; left:-128%;width:200px;font-weight:600; font-family: 'Audiowide', cursive; font-size:11px;">CONTACT:</a>
              <input type="text" v-model="userData.contact" placeholder="Enter Contact" class="search-input" style="border: 0px; height:43px;  position:absolute;left:-99%; margin-top:170px;" readonly>
              <a style="position:absolute;margin-top:250px; left:-233%;width:200px;font-weight:600; font-family: 'Audiowide', cursive; font-size:11px;">OTHER INFORMATION:</a>
              <input type="text" v-model="userData.other_info" placeholder="Enter Other Information"  class="search-input" style="border: 0px; height:43px;position:absolute;left:-220%; margin-top:350px;" readonly>
              <input type="hidden" v-model="userData.token" placeholder="Enter Other Information"  class="search-input" style="border: 0px; height:43px;" required>
              <a style="position:absolute;margin-top:250px; left:-123%;width:200px;font-weight:600; font-family: 'Audiowide', cursive; font-size:11px;">USER NAME:</a>
              <input  type="text" id="customerName" v-model="userData.username" placeholder="customer name"  class="search-input" style="border: 0px; height:43px;position:absolute;left:-99%; margin-top:350px;" readonly>

            </div>
            <div>
              <h3 style="font-size: 14px; left:47%;font-weight:900;position:absolute; margin-top:-200px;" >PRODUCT<span style="font-size: 22px;  font-weight:100;">&nbsp;&nbsp;|&nbsp;</span><span style="font-weight:400; font-family: 'WindSong', cursive; font-size:33px;">Summary</span></h3>
            </div>
   
        
        </form>
        </v-card-text>
        <v-card-actions>
          <button1 @click="close()" type="submit" style="margin-left:62%;  border-radius:5px;width:29%;  margin-bottom:3%; margin-top:11.5%;position:absolute;" class="neumorphic-button">&nbsp;&nbsp;<i class="fas fa-undo custom-icon"></i>&nbsp;&nbsp;Change Details</button1>
          <button1 @click="placeOrder('pending')" type="submit" style="margin-left:64%;  border-radius:5px;width:30%;  margin-bottom:2.5%; margin-top:30%; background-color:rgb(37, 37, 37); color:white;" class="neumorphic-button">&nbsp;&nbsp;&nbsp;&nbsp;<i class="fas fa-shopping-bag custom-icon"></i>&nbsp;&nbsp;&nbsp;&nbsp;Check Out</button1>
        </v-card-actions>
      </v-card>
    </v-dialog>




    <v-dialog v-model="dialog" persistent max-width="400">
      <v-card>
        <v-card-text>
          <div class="text-center">
            <p>  Your order has been successfully placed. </p>
            <img :src="require('../../../public/img/check.gif')"  style="width: 120px; height: 120px;">
          </div>
        </v-card-text>
        <v-card-actions>
          <v-btn  style="margin-left:162px;"  href="/userproducts" color="primary" @click="dialog = false">OK</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>      

    <v-dialog v-model="dialogs" persistent max-width="400">
      <v-card>
        <v-card-text>
          <div class="text-center">
            <p>  Your order has been successfully added to cart. </p>
            <img :src="require('../../../public/img/dash.gif')"  style="width: 180px; height: 150px;">
          </div>
        </v-card-text>
        <v-card-actions>
          <v-btn  style="margin-left:162px;"  href="/userproducts" color="primary" @click="dialog = false">OK</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    

    <v-dialog v-model="dialogss" persistent max-width="400">
      <v-card>
        <v-card-text>
          <div class="text-center">
            <p>  Choose payment method </p>
            <!-- <img :src="require('../../../public/img/dash.gif')"  style="width: 180px; height: 150px;"> -->
          <!-- add payment button here -->
          <a class="neumorphic-navbars" style="width: 150px; border-radius:17px; margin-left:96px;" href="https://connect-sb-issuing.paymaya.com/login" target="_blank">
            <img src="https://payments-web-sbx-assets.maya.ph/payments-web/assets/static/media/pay-with-maya.a7968dfe.svg" alt="Paymaya" style="width: 150px; height: 50px;">
          </a>  
          </div>
        </v-card-text>
        <v-card-actions>
          <v-btn  style="margin-left:162px;"   color="primary" @click="closemodal">OK</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog> 


    <div v-if="!showReviews" style="" >
      <nav
      class="neumorphic-navbar"
      style="  opacity: 0; /* Set initial opacity to 0 for fade-in effect */
      animation: fade-up 0.8s ease-out forwards;border-radius:5px;height:483px; width: 450px; display: flex; flex-direction: column; justify-content: flex-start; align-items: flex-start; margin-top:60px; margin-left:13%;"
    >
        <p style=" margin-left: 20px; margin-bottom: 10px; font-size: 11px; font-weight:600; font-family: 'Audiowide', cursive;">PRODUCT NAME:  <span style="font-size: 30px; font-weight:200; margin-left:15px; color:rgb(223, 146, 5);font-family: 'Bebas Neue', cursive; ">{{ productData.prod_name }}</span></p> 
    
        <div style="display: flex; flex-direction: column; align-items: center; margin-bottom: 20px;">
            <!-- <p>Image:</p> -->
            <img :src="productData.image" alt="Product Image" class="img-fluid" style="max-width: 250px; max-height: 250px; margin-top:20px; margin-left: 90px;">
        </div>
    
        <p style="margin-left: 20px; margin-bottom: 10px; font-size: 11px; font-weight:700;font-family: 'Audiowide', cursive;">UNIT PRICE: <span style="font-weight: 200; margin-left: 10px; color:rgb(240, 141, 29); font-size:20px; font-family: 'Poppins', sans-serif;">₱  <span style="font-family: 'Wallpoet', cursive; font-weight:200;font-size:25px; color:rgb(240, 141, 29);">{{ productData.unit_price }}</span></span></p>
        <p style="margin-left: 20px; margin-bottom: 10px; font-size: 11px; font-weight:600;font-family: 'Audiowide', cursive;" >SIZE: <span style="margin-left: 10px; color:rgb(240, 141, 29);font-weight:100; font-size:16px;">{{ getSizeName(productData.size_id) }}</span></p>
        <p style="margin-left: 20px; margin-bottom: 15px; font-size: 11px; font-weight:600;font-family: 'Audiowide', cursive;" >SHARE: <span style="margin-left: 10px; font-size:20px; "><i class="fab fa-facebook custom-icon"></i>&nbsp;&nbsp;<i class="fab fa-instagram custom-icon"></i>&nbsp;&nbsp;<i class="fab fa-twitter custom-icon"></i>&nbsp;&nbsp;<i class="fab fa-facebook-messenger custom-icon"></i></span></p>
        <router-link
      to="#"
      @click="toggleReviews"
      style="position: absolute; bottom: 114px; width: 150px; right: 35px; font-size: 14px; font-weight: 400; font-size: 11px; background-color:green; color: rgb(255, 255, 255)"
      class="neumorphic-button"
    >
      &nbsp;&nbsp;PRODUCT REVIEWS
    </router-link>
    <router-link
    to="#"
    @click="toggleDescription"
    style="position: absolute; bottom: 74px; width: 150px; right: 35px; height:31px; font-size: 9.5px; font-weight: 400;  background-color:#868686; color: rgb(255, 255, 255)"
    class="neumorphic-button"
  >
    &nbsp;&nbsp;PRODUCT DESCRIPTION
  </router-link>
        <router-link to="/userproducts" style=" border-radius:5px;width:150px; margin-left:250px; position:absolute; margin-top:402px; font-size:10px; font-weight:400; background-color:rgb(19, 18, 18);color:rgb(255, 255, 255)" class="neumorphic-button">  CHOOSE ANOTHER PRODUCT</router-link>
        
    </nav>
  </div>
  

    
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      showRating: true,
      selectedRating: 'all',
      products: [],
      showReviews: false,
      showDescription: false,

      status: '',
      dialog: false,
      dialogs: false,
      dialogss: false,
      dialogsss: false,
      productData: {
        image: '',
        prod_name: '',
        unit_price: '',
        sizes: [],
        transaction_code: '',
        total: 0,
        totalplusshipping:"",
        category_id: '',
        product_description: '',
        ships: '',

      },
      shippingFee: this.getRandomShippingFee(),
      info: [],
      categories: [],
      quantity: 1, // Initial quantity
      size_id: '',
      image:'', 
        prod_name:'', 
        unit_price:'',  
        address:'', 
        contact:'', 
        other_info:'', 
        customerName: '',
        id: '',
        token: '',
        status: '',
        username: '',
        category_id: '',
        
    };
  },
  
  created() {
    this.getProductDetails();
    this.token = sessionStorage.getItem('jwt');
    if (this.token) {
      this.getInfo();
    } else {
      console.error('JWT token not found in session storage');
    }
  },
  computed: {
    totalPrice() {
    // Convert values to numbers before performing calculations
    const unitPrice = Number(this.productData.unit_price);
    const shippingFee = Number(this.shippingFee);
    const quantity = Number(this.quantity);
    
    // Calculate the total price
    const total = (unitPrice * quantity) + shippingFee;
    
    // Return the total price formatted to 2 decimal places
    return total.toFixed(2);
  },
    // Calculate total price based on quantity and unit price
    totalAmount() {
      return this.quantity * this.productData.unit_price;
    },
    totalplusshipping() {
      return this.quantity * this.productData.unit_price + this.shippingFee;
    },
    filteredProducts() {
    if (this.selectedRating === 'all') {
      return this.products.filter(product => product.prod_name.includes(this.productData.prod_name));
    } else {
      return this.products.filter(product => product.rate === this.selectedRating && product.prod_name.includes(this.productData.prod_name));
    }
  },
  },
  watch: {
    // Watch for changes in quantity or unit price to update total
    totalAmount() {
      this.productData.total = this.totalAmount;
    },
    totalplusshipping() {
      this.productData.totalplusshipping = this.totalplusshipping;
    },
    'productData.unit_price'() {
      this.productData.total = this.totalAmount;
    }
  },
  methods: {
    
    getRandomShippingFee() {
    return Math.floor(Math.random() * (35 - 25 + 1)) + 25;
  },
    calculateAverageRating() {
// Replace this with your actual logic to calculate average rating
const averageRating = 0.0; // Replace with your actual calculation

// Map average rating to star rating based on specified conditions
if (averageRating < 0.1) {
  return 0.0;
} else if (averageRating >= 0.1 && averageRating > 2.0) {
  return 1.0;
} else if (averageRating >= 2.0 && averageRating > 3.0) {
  return 2.0;
} else if (averageRating >= 3.0 && averageRating < 4.0) {
  return 3.0;
} else if (averageRating >= 4.0 && averageRating < 5.0) {
  return 4.0;
} else {
  return 5.0;
}
},

      calculateStarRating() {
        const averageRating = this.calculateAverageRating();
        const starRating = Math.round(averageRating);
        return '★'.repeat(starRating); // Display stars based on rounded rating
      },
    selectRating(rating) {
    this.selectedRating = rating;
  },
    getCountByRating(rating) {
    return this.filteredProducts.filter(product => product.rate === rating).length;
  },

    calculateAverageRating() {
    const totalRatings = this.filteredProducts.length;
    let totalStars = 0;

    // Calculate total stars based on the ratings
    this.filteredProducts.forEach((product) => {
      switch (product.rate) {
        case 'Bad':
          totalStars += 1;
          break;
        case 'Poor':
          totalStars += 2;
          break;
        case 'Average':
          totalStars += 3;
          break;
        case 'Great':
          totalStars += 4;
          break;
        case 'Excellent':
          totalStars += 5;
          break;
      }
    });

    // Calculate the average rating
    const averageRating = totalRatings > 0 ? totalStars / (totalRatings * 5) : 0;

    // Format the average rating to 1 decimal place
    return averageRating.toFixed(1);
  },

    async fetchData() {
    try {
      const response = await axios.get('getReview');
      this.products = response.data;
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  },
  toggleDescription() {
    this.showDescription = !this.showDescription;
  },
    toggleReviews() {
    this.showReviews = !this.showReviews;
  },
    opendialog(){
      this.dialogss = true;
    },
    closemodal(){
      this.dialogss = false;
    },

    open(){
      this.dialogsss = true;
    },
    close(){
      this.dialogsss = false;
    },

    async placeOrder(status) {
      try {
        const ins = await axios.post("placeOrder", {
          image: this.productData.image,
          prod_name: this.productData.prod_name,
          unit_price: this.productData.unit_price,
          size_id: this.productData.size_id,
          category_id: this.productData.category_id,
          quantity: this.quantity,
          address: this.info[0].address, // Assuming you want the first user's address
          contact: this.info[0].contact, // Assuming you want the first user's contact
          other_info: this.info[0].other_info, // Assuming you want the first user's other info
          token: this.info[0].token, // Assuming you want the first user's other info
          customerName: this.info[0].username,
          id: this.productData.id,
          transaction_code: this.productData.transaction_code,
          total: this.productData.total,
          totalplusshipping: this.productData.totalplusshipping,
          shippingFee: this.shippingFee,
          // shipping lang dagdag
          status: status,
          
        });

        // Resetting data after order placement
        this.quantity = 1;
        this.customerName = "";

        // Triggering data retrieval after order placement
        await this.getInfo();

        if (status === 'cart') {
      // Open dialog for 'cart' status
      this.dialogs = true;
    } else if (status === 'pending') {
    this.dialog = true;
    }
      } catch (error) {
        console.error(error);
      }
    },
    async getInfo() {
      try {
        const response = await axios.get(`getUserData/${this.token}`);
        this.info = response.data;
      } catch (error) {
        console.error(error);
      }
    },
    getProductDetails() {
      this.productData.image = this.$route.params.image || '';
      this.productData.prod_name = this.$route.params.prod_name || '';
      this.productData.unit_price = this.$route.params.unit_price || 0;
      this.productData.size_id = this.$route.params.size_id || '';
      this.productData.stock = this.$route.params.stock || 0;
      this.productData.id = this.$route.params.id || '';
      this.productData.transaction_code = this.$route.params.transaction_code || '';
      this.productData.category_id = this.$route.params.category_id || '';
      this.productData.product_description = this.$route.params.product_description || '';
      this.productData.ships = this.$route.params.ships || '';
      
    },
    increaseQuantity() {
  if (this.quantity < this.productData.stock) {
    this.quantity += 1;
  } else {
    console.log('Maximum stock reached');
    window.alert('Maximum stock reached. Cannot increase quantity further.');
  }
},
    decreaseQuantity() {
      if (this.quantity > 1) {
        this.quantity -= 1;
      }
    },
    async fetchSizes() {
      try {
        const response = await axios.get("getsize");
        this.productData.sizes = response.data;
      } catch (error) {
        console.error(error);
      }
    },
    getSizeName(sizeId) {
  const size = this.productData.sizes.find(size => size.size_id === sizeId);
  return size ? size.item_size : 'Unknown';
}, 
async fetchCategories() {
    try {
      const response = await axios.get("getcat");
      this.categories = response.data; // Assuming response.data contains the categories array
    } catch (error) {
      console.error(error);
    }
  },
  getCategoryName(categoryId) {
    const category = this.categories.find(category => category.id === categoryId);
    return category ? category.category_name : 'Unknown';
  },
  },
  mounted() {
    this.fetchSizes();
    this.getInfo();
    this.fetchData();
    this.fetchCategories();
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Wallpoet&display=swap');

@import url('https://fonts.googleapis.com/css2?family=Sacramento&display=swap');

@import url('https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css');
@import url('https://fonts.googleapis.com/css2?family=Podkova&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Rochester&display=swap');
/* Add additional styles if needed */
.user-profile {
  width: 220px;
  margin-right: 100px;
}

.neumorphic-navbar {
  background-color: #fffefe;
  box-shadow: 5px 5px 10px #bcbcbc, -5px -5px 10px #ffffff;
  color: #1b1b1b;
}
.neumorphic-navbar::-webkit-scrollbar {
  width: 11px; /* Set the width of the scrollbar */
  height: 5px;
}

.neumorphic-navbar::-webkit-scrollbar-thumb {
  background-color: rgba(54, 54, 54, 0.26); /* Set the color of the scrollbar thumb */
  border-radius: 10px; /* Set the border radius of the scrollbar thumb */
}

.neumorphic-navbar::-webkit-scrollbar-track {
  background-color: #eee8e871; /* Set the color of the scrollbar track */
}

</style>
