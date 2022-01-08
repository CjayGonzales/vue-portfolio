<template class="">
  <div class="">

    <div class="row margin_lg">
      <div class="col-5">
        <img class="profile_image" src="@/assets/Profile.jpg" alt="">
      </div>
      
      <div class="col-6">
        <h3>About</h3>
        <h1 class="header">Clemente Gonzales</h1>
        <p class="margin_sm">
          Hi! My name is Clemente Gonzales. Im a student studying Creative Computing in IADT with a love for 
          Front End Development and Design. I specialize in web design, and I am familiar with HTML5, CSS, Javascript, PHP aswell
          as different frameworks and libraries such as Vue, Bootstrap, Material Design and GSAP for animating web pages


        </p>

        <b-button type="dark" squared class="projects_button margin_sm" :to="{name: 'projects'}">View my Projects</b-button>
      </div>
      
    </div>
  
  </div>
</template>

<script>


export default {
  name: 'Home'
}
</script>

<style>

.projects_button{
  width: 200px;
  border-radius: 0;
}

.background_dark{
  background-color: black;
}

.profile_image{
  width: 500px;
  height: 500px;
  object-fit: cover;
  box-shadow: 0px 12px 28px -10px rgba(0, 0, 0, 0.5);
-webkit-box-shadow: 0px 12px 28px -10px rgba(0, 0, 0, 0.5);
}

.header{
  font-size: 60px;
  border-bottom: 2px solid black;
}

.margin_sm{
  margin-top: 10px;
}

.margin_lg{
  margin-top: 100px;
}

</style>