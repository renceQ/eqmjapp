<template>
	
	<form @data-saved="getUserDetails" />
	<div>
		<tr v-for="info in info">
			<td>{{ info.category_name}}</td>
			<td>
			  <button @click="editprofile" class="btn btn-success btn-sm edit">Edit profile</button>
			</td>
		  </tr>
	</div>
	<br>
	<br>
	<br>
	<br>
	<br>
    <div style="display: flex; align-items: center;">
		<img :src="require('../../assets/images/logo.jpg')" alt="Description of the image" style="width: 300px; margin-left: 200px;margin-right: 90px; margin-top: 90px;">
		<div style="margin-left:100px;">
			<br>
			<br>
			<br>
	
			<h1 class="navbar-brand" href="index.html" style="font-size: 60px; "> Wel<span>Come...</span></h1>
			<br>
			<h2 class="navbar-brand" href="index.html" style="font-size: 20px;">
				"Welcome to our page! where your convenience 
				<br>meets our expertise.Schedule your tailored<br>
				 service appointment today for a seamless <br>
			and personalized experience."
			</h2>
			<div>
				<router-link
  to="/about"
  class="neumorphic-link"
  style="
    padding: 10px 20px;
    font-size: 16px;
    background-color: #ffffff;
    border: none;
    border-radius: 4px;
    box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff;
    transition: all 0.3s ease;
    text-decoration: none; /* Remove underline */
    display: inline-block; /* To remove underline */
    position: relative; /* For pseudo-element */
  "
>
  Explore
</router-link>

			</div>
			<br>
		
		</div>
	</div>





  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <div>
<div style="margin-left:450px;">
			<h1 class="navbar-brand" href="index.html" style="font-size: 50px;margin-left:90px; "> Our|<span>Services...</span></h1>
			<br>
      <br>
			<h2 class="navbar-brand" href="index.html" style="font-size: 20px;">
				"Welcome to QMJ Enterprises! We offer a diverse range of <br>services including sounds and lighting appointments, <br>professional photo and video shoots, album production, <br>invitations, souvenirs, personalized clothing, and bespoke <br>design suggestions."
			</h2>
            <br>
            <br>
            <br>
          </div>
			<div style="margin-left:320px;">
				<a style="padding: 10px 20px; font-size: 16px; background-color: #f0f0f0; border: none;  box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff; transition: all 0.3s ease;">Sounds and Lights</a>
                <a  style="padding: 10px 20px; font-size: 16px; background-color: #f0f0f0; border: none;  box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff; transition: all 0.3s ease;">photo/video production</a>
                <a  style="padding: 10px 20px; font-size: 16px; background-color: #f0f0f0; border: none;  box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff; transition: all 0.3s ease;">Items Customization</a>
                <a  style="padding: 10px 20px; font-size: 16px; background-color: #f0f0f0; border: none;  box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff; transition: all 0.3s ease;">Tarpaulin Printing </a>
			</div>
    </div>
      <br>

            <br><br><br><br>
        
          <div class="row justify-content-end" style="margin-left:450px;">
            <strong class="mb-4" style="margin-right: 300px; font-size: 50px;">What We Do....</strong>
            <div class="col-md-7">
               
            </div>
          </div>

    
        <section class="sec1" id="sec1" >
        <div class="container">
          <div class="row d-flex">
            <div class="col-md-6 d-flex">
              <img :src="require('../../assets/images/soundsandlights.jpg')" alt="Description of the image" style="border-radius: 10px; width: 500px; margin-right: 100px; margin-top: 10px;margin-bottom: 100px;">
            </div>
            <div class="col-md-6 pl-md-5 py-5">    
                <div class="col-md-12 ">
                  <h2 class="mb-4">Sounds and Lights</h2>
              </div>
              <div class="row" style="width: 1100px;">
                <div class="col-md-6 ">
                  <div class="block-18 text-center py-4 bg-light mb-4">
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
        </section>

            
        <section class="sec2" id="sec2" >
            <div class="container">
              <div class="row d-flex">
                <div class="col-md-6 d-flex">
                  <img :src="require('../../assets/images/pis2.jpg')" alt="Description of the image" style="border-radius: 10px; width: 500px; margin-right: 100px; margin-top: 10px;margin-bottom: 100px;">
                </div>
                <div class="col-md-6 pl-md-5 py-5">    
                    <div class="col-md-12 ">
                      <h2 class="mb-4">Photo and Video Production</h2>
                  </div>
                  <div class="row" style="width: 1100px;">
                    <div class="col-md-6 ">
                      <div class="block-18 text-center py-4 bg-light mb-4">
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
            </section>
    
    
            <section class="sec3" id="sec3" >
                <div class="container">
                  <div class="row d-flex">
                    <div class="col-md-6 d-flex">
                      <img :src="require('../../assets/images/hood.jpg')" alt="Description of the image" style="border-radius: 10px; width: 500px; margin-right: 100px; margin-top: 10px;margin-bottom: 100px;">
                    </div>
                    <div class="col-md-6 pl-md-5 py-5">    
                        <div class="col-md-12 ">
                          <h2 class="mb-4">Items Customization</h2>
                      </div>
                      <div class="row" style="width: 1100px;">
                        <div class="col-md-6 ">
                          <div class="block-18 text-center py-4 bg-light mb-4">
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
                </section>

                
    
            <section class="sec4" id="sec4" >
                <div class="container">
                  <div class="row d-flex">
                    <div class="col-md-6 d-flex">
                      <img :src="require('../../assets/images/tarp.jpg')" alt="Description of the image" style="border-radius: 10px; width: 500px; margin-right: 100px; margin-top: 10px;margin-bottom: 100px;">
                    </div>
                    <div class="col-md-6 pl-md-5 py-5">    
                        <div class="col-md-12 ">
                          <h2 class="mb-4">Tarpaulin Printing </h2>
                      </div>
                      <div class="row" style="width: 1100px;">
                        <div class="col-md-6 ">
                          <div class="block-18 text-center py-4 bg-light mb-4">
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
                </section>


                <br>
                <br>
                <br>
                <section class="hero-wrap-0 js-fullheight" style="background-image: url('images/bg_2.jpg'); margin-bottom:100px;" data-stellar-background-ratio="0.5">
                  <div style="display: flex; align-items: left; text-align: justify;">
                    <div style="margin-right: 50px; margin-left: 100px;">
                      <h1 class="navbar-brand" style="font-size: 50px;"> About|<span>US...</span></h1>
                      <h2 class="navbar-brand" href="index.html" style="font-size: 15px;">
                        QMJ Enterprises is dedicated to crafting unforgettable experiences <br>
                        through a diverse array of services. From expertly arranging sound <br>
                        and lighting setups to capturing captivating moments through professional<br>
                         photo and video shoots, their expertise extends to designing albums, <br>
                         creating bespoke souvenirs, and customizing clothing. Additionally, <br>
                         they excel in printing tarpaulins, ensuring every event is marked with <br>
                         personalized and exceptional touches that leave a lasting impression.
                      </h2>
                    </div>
                    <div style="display: flex; align-items: center; justify-content: flex-end;">
                      <img :src="require('../../assets/images/logo2.jpg')" alt="Description of the image" style="border-radius: 10px; width: 450px; margin-right: 100px; ">
                    </div>
                  </div>
                  <br>
                  <div class="container">
                    <div class="row d-flex">
                      <div class="col-md-7">
                        <h3 class="navbar-brand" style="font-size: 15px;">
                          At the heart of QMJ Enterprise lies a dedication to crafting unforgettable experiences. Established with a vision to redefine industry <br>
                          standards, QMJ Enterprise has consistently delivered excellence across its diverse array of services. From expertly arranging sound and <br> 
                          lighting setups to capturing captivating moments through professional photo and video shoots, QMJ Enterprise ensures that every project <br>
                          is marked by personalized and exceptional touches. This commitment not only ensures that its offerings are cutting-edge but also reflects <br>  
                          a proactive approach to meeting and exceeding client expectations. Whether it's designing albums, creating bespoke souvenirs, customizing <br>
                          clothing, or excelling in printing tarpaulins, QMJ Enterprise embraces innovation as a driving force for success.
                        </h3>
                      </div>
                    </div>
                    <br>
                    <br>
                    <div class="row">
                      <div class="col-md-7">
                        <h1 class="navbar-brand" style="font-size: 30px;"> OurStory|<span>2013...</span></h1>
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
                      <div class="col-md-5" style="margin-top: 10px;">
                        <h1 class="navbar-brand" style="font-size: 30px;"> Challenges<span>...</span></h1>
                        <h4 class="navbar-brand" style="font-size: 15px; text-align: justify;">
                          It's important to note that businesses also use challenges as <br>
                          opportunities for growth and improvement. Qmj may develop strategies,<br>
                          innovate, and adapt to overcome obstacles and enhance their overall <br> 
                          resilience. To get specific information about challenges faced by QMJ <br>
                          Enterprises, I recommend checking their official communications, reports,<br>
                          or contacting the company directly for the latest and most accurate details.
                        </h4>
                      </div>
                    </div>
                    <div class="row d-flex align-items-center">
                      <div class="col-md-7">
                        <img :src="require('../../assets/images/logo2.jpg')" alt="Description of the image" style="border-radius: 10px; width: 600px; margin-right: 20px; margin-top: 80px;">
                      </div>
                      <div class="col-md-5">
                        <div class="col-md-5">
                        <h3 class="navbar-brand" style="font-size: 15px; text-align: justify;">
                          At the heart of QMJ Enterprise lies a dedication to crafting unforgettable <br> 
                          experience. Established with a vision to redefine industry standards, QMJ <br>
                          Enterprise has consistently delivered excellence across its diverse array <br>
                          of services. From expertly arranging sound and lighting setups to capturing <br>
                          captivating moments through professional photo and video shoots, QMJ <br> 
                          Enterprise ensures that every project is marked by personalized and <br> 
                          exceptional touches. This commitment not only ensures that its offerings <br> 
                          are cutting-edge but also reflects a proactive approach to meeting and <br>
                          exceeding client expectations. Whether it's designing albums, creating <br> 
                          bespoke souvenirs, customizing clothing, or excelling in printing tarpaulins,<br>
                          QMJ Enterprise embraces innovation as a driving force for success.
                        </h3>
                      </div>
                    </div>
                  </div>
                  </div>
                </section>
            

                <section id="blog" class="blog" >
                            <div class="container">
                                <div class="section-header">
                        <br>
                        <br>
                
                        <div class="center-text">
                        <h1 class="navbar-brand" href="index.html" style="font-size: 50px; "> Monthly|<span>BLOG</span></h1>
                                    <h2>Blogs and Articles</h2>
                                    <p>Always upto date with our latest News and Events </p>
                                </div><!--/.section-header-->
                        </div>
                        <br>
                                <div class="blog-content">
                                    <div class="row">
                                        <div class="col-md-4 col-sm-6">
                                            <div class="single-blog-item ">
                                <div class="single-blog-item-img">
                        <img :src="require('../../assets/images/blog/b1.jpg')" alt="blog image">
                                </div>
                
                                                <div class="single-blog-item-txt">
                                                    <h2><a href="#">Want to know the best lighting for your place?</a></h2>
                                                    <h4>posted <span>by</span> <a href="#">admin</a> November 2023 </h4>
                                                    <p>
                                    Explore the illuminating world of home lighting with our comprehensive blog! Discover the perfect lighting solutions tailored to your space, whether it's cozy corners, vibrant living rooms, or soothing bedrooms. 
                                    Uncover tips, trends, and expert advice to create the ambiance you've always dreamed of. Illuminate your home...
                                                    </p>
                                  <div>
                  <!-- External Link -->
                  <a href="https://www.bhg.com/home-improvement/lighting/planning/best-lighting-rooms/" target="_blank" rel="noopener noreferrer" style="padding: 10px 20px; font-size: 16px; background-color: #f0f0f0; border: none; border-radius: 8px; box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff; transition: all 0.3s ease;">Read More</a>
                </div>
                        <br>
                                                </div>
                                            </div>
                                        </div>
                                        <div class="col-md-4 col-sm-6">
                                            <div class="single-blog-item2">
                                <div class="single-blog-item-img">
                        <img :src="require('../../assets/images/blog/b3.jpg')" alt="blog image">
                                </div>
                                                <div class="single-blog-item-txt">
                                                    <h2><a href="#">Event Tips and Ideas for better Celebration moments</a></h2>
                                                    <h4>posted <span>by</span> <a href="#">admin</a> November 2023</h4>
                                                    <p>
                                                        Elevate your celebrations to unforgettable heights with our Event Tips and Ideas blog! Whether you're planning a birthday bash, wedding extravaganza, or a corporate gathering, we've got you covered. 
                                    Discover creative themes, expert tips, and innovative ideas to transform your events into extraordinary moments. 
                                    From decor inspiration  ... 
                                                    </p>
                                  <div>
                  <!-- External Link -->
                  <a href="https://eventistrybyalecia.com/11-ways-to-make-your-event-unforgettable/" target="_blank" rel="noopener noreferrer" style="padding: 10px 20px; font-size: 16px; background-color: #f0f0f0; border: none; border-radius: 8px; box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff; transition: all 0.3s ease;">Read More</a>
                </div>
                        <br>
                                                </div>
                                            </div>
                                        </div>
                                        <div class="col-md-4 col-sm-6">
                                            <div class="single-blog-item3">
                                <div class="single-blog-item-img">
                        <img :src="require('../../assets/images/blog/b2.jpg')" alt="blog image">
                                </div>
                                                <div class="single-blog-item-txt">
                                                    <h2><a href="#">How sound systems creates a better experience for your One time Experience </a></h2>
                                                    <h4>posted <span>by</span> <a href="#">admin</a> November 2023</h4>
                                                    <p>
                                    Unlock the Power of Sound: How Exceptional Sound Systems Transform Your One-Time Experiences.
                                     Dive into the immersive world of audio excellence as we explore the impact of top-notch sound systems on your special moments.
                                     From concerts and live events to once-in-a-lifetime...								
                                    </p>
                                    <div>
                  <!-- External Link -->
                  <a href="https://illuminated-integration.com/blog/sound-design-for-theatre/" target="_blank" rel="noopener noreferrer" style="padding: 10px 20px; font-size: 16px; background-color: #f0f0f0; border: none; border-radius: 8px; box-shadow: 4px 4px 8px #c7c7c7, -4px -4px 8px #ffffff; transition: all 0.3s ease;">Read More</a>
                </div>
                <br>
                
                        <br>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div><!--/.container-->
                      
                            
                        </section><!--/.blog-->
                        <!--blog end -->
                   
                        <div class="center-text">
                        <h1 class="navbar-brand" href="index.html" style="font-size: 50px; "> Explore more QMJ|<span>NEWS/UPDATES </span></h1>
                                    <h2>News and Updates</h2>
                                    <p>Get Instant Updates: Check Out Our Real-time Feed.</p>
                                </div>
                           <br><br><br><br>
                      
              
                
                           <section id="home" class="update1">
                    <div class="container">
                        <div class="col-md-100 d-flex">
                        </div>
                        <div class="col-md-100 pl-md-5 py-5">    
                            <div class="welcome-hero-txt">
                              <h2 class="navbar-brand" href="index.html" style="font-size: 50px; "><span>November 05, 2023</span></h2>
                          </div>
                                  </div>
                                  <h5 style="color: #ffffff;">"Deep gratitude to @IyamHuertoCatering in Bancuro, Naujan for turning our event into an unforgettable feast! 🍽️ Your culinary artistry added an exquisite touch to our celebration. THIS IS QMJ Images TV, Sounds and Stage Lights Pro, 
                                    and the reliable Genset team for creating an atmosphere filled with visual and auditory splendor! 
                                     #IyamHuertoCatering #QMJImagesTV #SoundsAndStageLightsPro #GensetExcellence</h5>
                                    <br> <br> <br>
                                    <a href="https://www.facebook.com/permalink.php?story_fbid=pfbid0tuxrPVuCUqy3UwGkaFQfe8nNMFx1fU49uqdX91nMFcKj7PA4oGgnURhKcuNvdw91l&id=100064010826799" 
                                    target="_blank" rel="noopener noreferrer" style="padding: 15px 25px;font-size: 18px;background-color: #2a2b36;color: #fff;border: 2px solid #2a2b36;border-radius: 10px;box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);transition: all 0.3s ease;
                  text-decoration: none;display: inline-block;letter-spacing: 1px;cursor: pointer;animation: glowing 2s infinite; /* Add glowing effect */">Read More</a>
                                </div>
                    </section>
              
                        
                    <section id="home" class="update2">
                    <div class="container">
                        <div class="col-md-100 d-flex">
                        </div>
                        <div class="col-md-100 pl-md-5 py-5">    
                            <div class="welcome-hero-txt">
                              <h2 class="navbar-brand" href="index.html" style="font-size: 50px; "><span>March 08, 2023</span></h2>
                          </div>
                                  </div>
                                  <h5 style="color: #ffffff;">"March 8 marked an extraordinary day as we celebrated amidst the scenic backdrop of Anahaw Island View Resort with a basic setup that spoke volumes. 
                                    A huge shoutout to QMJ Images TV for capturing the magic and Sounds and Stage Lights Pro for orchestrating an ambiance that echoed perfection. 
                                    Every moment, a symphony; every detail, a masterpiece. 🌟"</h5>
                                    <br> <br> <br>
                                    <a href="https://www.facebook.com/kram.quinio/posts/pfbid0vMHqU8mEq4ZwHWD44KXhNH6cmVQxU9xxYmNLP9SZb2y4HiLcJBNcunUecNdJMdcNl" 
                                    target="_blank" rel="noopener noreferrer" style="padding: 15px 25px;font-size: 18px;background-color: #2a2b36;color: #fff;border: 2px solid #2a2b36;border-radius: 10px;box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);transition: all 0.3s ease;
                  text-decoration: none;display: inline-block;letter-spacing: 1px;cursor: pointer;animation: glowing 2s infinite; /* Add glowing effect */"> Read More</a>
                                </div>
                    </section>
              
                
                
                    <section id="home" class="update5">
                    <div class="container">
                        <div class="col-md-100 d-flex">
                        </div>
                        <div class="col-md-100 pl-md-5 py-5">    
                            <div class="welcome-hero-txt">
                              <h2 class="navbar-brand" href="index.html" style="font-size: 50px; "><span>February 26, 2023</span></h2>
                          </div>
                                  </div>
                                  <h5 style="color: #ffffff;">"Embark on a journey to celebrate the grandeur of an 18th birthday at the enchanting Anahaw Island View Resort.
                                     Immerse yourself in the scenic beauty as we transform moments into memories. A heartfelt 'Maraming Salamat po'
                                      for being part of this joyous occasion! 🌟✨ #MJDM #QMJImagesTV #SoundsAndStageLightsPro #AnahawCelebrations"</h5>
                                    <br> <br> <br>
                                    <a href="https://www.facebook.com/permalink.php?story_fbid=pfbid0FKFpYdMSoLa6N6LEZPTTig7nt6A2KnPpcw43xpZWvFRBQzKxMtorXVsXTdWSd3aDl&id=100064010826799" 
               target="_blank" rel="noopener noreferrer" style="padding: 15px 25px;font-size: 18px;background-color: #2a2b36;color: #fff;border: 2px solid #2a2b36;border-radius: 10px;box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);transition: all 0.3s ease;
                  text-decoration: none;display: inline-block;letter-spacing: 1px;cursor: pointer;animation: glowing 2s infinite; /* Add glowing effect */">Read More</a>
                                </div>
                    </section>
                            
                
                    <section id="home" class="update4">
                    <div class="container">
                        <div class="col-md-100 d-flex">
                        </div>
                        <div class="col-md-100 pl-md-5 py-5">    
                            <div class="welcome-hero-txt">
                              <h2 class="navbar-brand" href="index.html" style="font-size: 50px; "><span>March 04, 2023</span></h2>
                          </div>
                                  </div>
                                  <h5 style="color: #ffffff;">"On March 4, the vibrant spirit of Canubing 2 came alive with a spectacular event—the presentation of candidates. Heartfelt thanks to Consi Aldwin Macatangay and the entire Sanggunian ng Canubing 2 for orchestrating a memorable gathering.
                                     Special gratitude to QMJ Images TV for immortalizing the moments and Sounds and Stage Lights Pro for setting the perfect stage. Together, we painted an unforgettable canvas of unity and celebration. 🎉✨ "</h5>
                                    <br> <br> <br>
                                    <a href="https://www.facebook.com/kram.quinio/posts/pfbid02Kef5jBVaK1qr2Lfs2F7ELeRGtS9ZoUPxTaNFt7Z6NK4sxtCne6tr1eM2LprCkKbXl" 
                                    target="_blank" rel="noopener noreferrer" style="padding: 15px 25px;font-size: 18px;background-color: #2a2b36;color: #fff;border: 2px solid #2a2b36;border-radius: 10px;box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);transition: all 0.3s ease;
                  text-decoration: none;display: inline-block;letter-spacing: 1px;cursor: pointer;animation: glowing 2s infinite; /* Add glowing effect */">Read More</a>
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


</template>

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
</style>

<script>


</script>