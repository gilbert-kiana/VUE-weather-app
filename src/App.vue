<template>
  <div id="app">
    <main>
     <div class="search-box">
       <input type="text" class="search-bar" placeholder="Search weather....."/>
     </div>
     <div class="weather-contain">
        <div class="location-box">
          <div class="location">Nairobi,Kenya</div>
          <div class="date">Wednesday 8 July 2020</div>
        </div>
     </div>
    </main>
  </div>
</template>

<script>


export default {
  name: 'App', 
  
}
</script>

<style>
 *{
   margin:0;
   box-sizing: border-box;
   padding: 0;
   
 }

 body{
   font-family:'montserrat',sans-serif;
 }
 

 #app{
   background-image:url('./assets/railway.jpg');
   background-size:cover ;
   background-position:bottom ;
   transition: 0.4s;
 }

 main{
   min-height:100vh;
   padding: 25px;

   background-image:linear-gradient(to bottom,rgba(0,0,0,0.25),rgba(0,0,0,0.75));
 }
 
 .search-box{
   width:100%;
   margin-top: 30px; 
   border:none;

 }

 .search-box .search-bar{
   display:block;
   width: 100%;
   padding:15px ;
   color: #313131;
   font-size: 20px;
   appearance: none;
   border: none; 
   background-color:rgba(255,255,255,0.5);
   border-radius:20px 20px 20px 20px;
   transition: 0.4s;
   outline: none;
   box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
 }

 .search-box .search-bar:focus {
   box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
   background-color: rgba(255, 255,255,0.75);
   border-radius: 20px 0px 20px 0px; 
   border:none;
 }
</style>
