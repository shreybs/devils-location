<template>
<html>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.5.2/animate.min.css">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">

    <div class="container">
      <div class="intro">
      <h1> Welcome to Devil's Locations</h1><br>
      <p> "Be safe. Be sure" - Our motto. Be sure about any street or place you are to attend
        by searching for it below. View the safety ratings and number of incidents
        and comments submitted by other women for each place or submit them yourself. <br><br>
        Help other women by reviewing places with the comment button below.
        You can also call local police using the menu button on the side or book a local cab.
        Thank you and we hope you are safe and happy.
        </p>
        
      </div>
      <img src='https://mylg.io/wp-content/uploads/2016/07/Freebsd-logo.png'>
    </div>
    <div class="content">
      <div class="profile">
        <h3>Mahima S</h3><br>
        @mahi256 <br>
        <img src="http://www.homeselfe.com/wp-content/uploads/2016/10/profile-placeholder-generic.png">
        <br><br><br>
        <a href="http://opencity.in/data/bengaluru-city-police-police-stations-and-helpline-contact-numbers" target="_blank"><button class="btn btn-danger servicer">Request Security</button></a><br><br>
        <a href="https://www.olacabs.com/" target="_blank"><button class="btn btn-danger servicer">Request Cab Service</button></a>  
        <br><br>
        <a href="file:///home/neotius/Desktop/Devil's%20Locations/devils-location/src/components/logout.htm"><button class="btn btn-primary"><i class="fa sing-out-alt"> Log Out </i></button></a> 
      </div>
      <i class="fa fa-search icoo"></i>
      <div class="searchBar">
        <input type="text" placeholder="Enter Location Name" v-model='search'>
      </div>
      <div class="reviews">
        <div class="Introduce">Reviews</div> 
       <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
         <li v-for="(data,index) in filteredLocations" :key='index'>
           <form @submit.prevent="addComment">
           <input type="text" v-model='commentText' class="commentBox" placeholder="Enter your review here">
           <button class="submitComment" id="comment" type="submit"> Post Comment</button>
           </form>
           <h2>{{index+1}}.) {{data.areaName}}</h2> <br>
           <h4>Rating: {{data.rating}} / 5</h4><br>
           <h4>Number of Incidents Reported: {{data.incidents}}.</h4>
           <h2> Comments:</h2>
           

           <p v-for="(comments,ind) in data.comments" :key="ind">
             > {{comments}}
           </p>
           
         </li>
         </transition-group>
       </ul>

      </div>





    </div>

    

</html>
</template>

<script>

class Areas{
  constructor(areaName,rating,incidents,comments=[]){
    this.areaName = areaName;
    this.rating = rating;
    this.incidents = incidents;
    this.comments = comments;
  }
}


export default {
  name: 'Dlocation',
  
  data(){
    return{
      'search':'',
      'commentText':'',
      placeList:[
        new Areas("SP Road","2.8","12",["You'll be fine in most places with people","Avoid the small roads with many male populated shops","Don't walk alone into any shops or alleys no matter what"]),
        new Areas("Malleshwaram","4.7","3",["Probably one of the safest places in Bangalore","Friendly people and most places are very safe"]),
        new Areas("KR Market","1.2","23",["Don't trust anyone here !! Especially the shop keepers","Trust your gut...many people here will try to scam you","I wouldn't visit it alone on any day. Get a friend with you."]),
       ]
    }
  },
  computed: {
    filteredLocations(){
      return this.placeList.filter((post)=>{
        return post.areaName.includes(this.search);
      });
    }
  },
  methods: {
    addComment(){
      this.placeList[0].comments.push(this.commentText);
      this.commentText='';
    }
  }
}
</script>







<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import url('https://fonts.googleapis.com/css?family=Roboto+Condensed|Permanent+Marker|Bree+Serif|Kaushan+Script|Roboto+Slab');
  @import url('https://fonts.googleapis.com/css?family=Nova+Mono|Merienda+One');

  .Introduce{
    font-family: 'Merienda One';
    font-size: 52px;
    background-color: rgb(248, 37, 37);
    color: white;
    margin: 0;
    padding: 2px;
    border-radius: 15px ;

  }
  .container{
    margin: 0;
    top:1px;
    width: 100%;
    color:white;
    background: rgb(248, 37, 37);
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
    
  }
  .container h1{
    font-family: 'Kaushan Script';
    font-size: 72px;
    color:white;
  }

  .container img{
    float: left;
    height: 256px;
    width: 256px;
    margin-top: 110px;
  }
  .intro{
    width: 60%;
    padding: 15px;
    color:white;
    font-size: 18px;
    
  }
  .intro p{
    font-family: 'Roboto Slab';
    font-size: 21px;
  }

  .profile{
    margin-top: 30px;
    transform: translateX(1200px);
    height: 545px;
    padding: 5px;
    font-family: 'Bree Serif';
    font-size: 22px;
    width: 256px;
    border: 0px;
    border-radius: 15px;
    box-shadow: inset 0 0 10px #000000;
    
  }


  .profile img{
    width: 128px;
    height: 128px;
  }

  .profile h3{
    font-size: 31px;
  }
  .profile ul{
    list-style: none;
    color: black;
    text-decoration: none;
    left: 5px;
  }
  .profile li{
    margin-top: 10px;
    text-decoration: none;
    color: white;
    background-color: yellow;
    border: 1px solid yellow;
    border-radius: 10px;
  }
  
  .servicer{
    
    width: 135px;
    height: 55px;
    padding: 5px;
  }

  .reviews{
    color: rgb(255, 255, 255);
    border: 15px solid rgb(248, 37, 37);
    border-radius: 25px;
    padding: 10px;
    border-radius: 20px;
    font-family: 'Roboto Slab';
    width: 70%;
    transform: translateY(-420px);
    margin-left: 45px;
  }

  .reviews li{
    box-shadow: inset 0 0 10px #000000;
    padding: 5px;
    border-radius: 15px;
    margin-top: 20px;
    background-color: rgb(248, 37, 37);

  }

  .reviews ul{
    text-align: center;
  }

  .reviews h1{
    font-family: 'Roboto Condensed';
    font-size: 54px;
    text-align: left;
    padding: 5px;
  }

  .reviews h2{
    font-size: 39px;
    text-align: left;
    padding: 5px;

  }
  .reviews h4{
    font-size: 29px;
    text-align: left;
    padding: 5px;
  }
  .reviews p{
    font-size: 21px;
    font-style: italic;
    text-align: left;
    color: black;
    background-color: white;
  }

  .searchBar{
    margin-left: 120px;
    transform: translateY(-500px);
    width: 70%;
    font-family: 'Nova Mono';
    font-size: 18px;
    padding: 0px;
    border: 10px solid rgb(248, 37, 37);;
    border-radius: 0px 60px 60px 0px;

  }
  .searchBar input{
    width:100%;
    height: 100%;
    padding: 10px;
    border-radius: 0px 60px 60px 0px;
    font-size: 25px;

  }
  textarea:focus, input:focus{
    outline: none;
  }

  .icoo{
    width: 100px;
    font-size: 50px;
    color: white;
    height: 75px;
    background-color: rgb(248, 37, 37);
    border: 10px solid rgb(248, 37, 37);;
    border-radius: 60px 0px 0px 60px;
    transform: translateY(-425px) translateX(-660px);
  }

  .submitComment{
    width: 140px;
    height: 90px;
    font-family: 'Roboto Slab';
    font-size: 21px;
    font-weight: 800;
    padding: 10px;
    background-color: white;
    color: rgb(248, 37, 37);
    border-radius: 15px;
    margin-top: 25px;
    margin-right: 20px;
    float: right;
  }

  .commentBox{
    color : black;
    width:280px;
    height: 60px;
    margin-top: 25px;
    border-radius: 15px;
    font-family: Times;
    font-size: 18px;
    transform: translateX(235px);
  }


</style>
