<template>
  <div id="app">
    <main>
     <div class="search-box">
       <input type="text" class="search-bar" placeholder="Search weather....." v-model="query" 
       @keypress="fetchweather"/>
     </div>
     <div class="weather-contain" v-if="typeof weather.main !='undefined'">
        <div class="location-box">
          <div class="location">{{weather.name}},{{weather.sys.country}}</div>
          <!--div class="date">{{dateBuilder()}}</div>-->
        </div>
        <div class="weather-box">
          <div class="temp">{{Math.round(weather.main.temp)}}</div>
            <div class="weather-status">{{weather.weather[0].main}}</div>
          </div>
     </div> 
    </main>
  </div>
</template>

<script>


export default {   
  name: 'App', 
  data(){
    return{
      api_key:'ca17567b826e566c3acd2e78e0d69d51',
      url_base:'https://home.openweathermap.org/data/2.5/',
      query:'',
      weather:{}
    }
  },
  methods:{
    fetchweather(e){
       if(e.key=="Enter"){
          fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setResults);
       }
    },
    setResults(results){
      this.weather = results;
    },
  
  }
  
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
 .weather-contain{
   color:white;
 }

 .location-box .location{
   color:#fff;
   font-size:32px;
   font-weight:500;
   text-align: center;
   text-shadow:3px 3px rgba(0,0,0,0.25);
 }
 
 .location-box .date{
   color:#fff;
   font-size:20px;
   font-weight:500;
   text-align: center;
   font-style:italic;
 }
   .weather-box{
     text-align:center;
   }

   .weather-box .temp{
    display: inline-block;
    padding:10px 25px;
    color:#fff;    
    font-size:102px;
    font-weight:900;
    text-shadow:3px 6px rgba(0,0,0,0.25);
    background-color: rgba(255, 255, 255, 0.25);
    border-radius:16px;
    margin:30px 0px;
    box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
 }
 
 .weather-box .weather-status{
   color:#fff;
   font-size:40px;
   font-weight: 700;
   font-style:italic;
   text-shadow:3px 6px rgba(0, 0, 0, 0.25);

 }
</style>
