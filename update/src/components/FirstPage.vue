<template>
<div class="bg-body w-screen h-screen">
  <div class="text-3xl font-mono space-x-8">
      <div class="space-x-20">
    <button @click="SignIn" class="mt-60 bg-white px-6 py-4 rounded-full transform hover:scale-110 motion-reduce:transform-none">
     <i class="fas fa-sign-in-alt"></i> Sign In
    </button>
    <button @click="SignUp" class="bg-white px-6 py-4 rounded-full transform hover:scale-110 motion-reduce:transform-none">
     <i class="fas fa-user-plus"></i> Sign Up
    </button>
      </div>
  </div>
</div>
</template>

<script>
export default {
    methods:{
        SignIn(){
            this.$router.push('/SignIn');
        },
        SignUp(){
            this.$router.push('/Signup');
        },
    }
};
</script>

<style scoped>
.bg-body{
    background-color: #f0e8e7;
    background-image: linear-gradient(315deg, #c2270b 0%, #cfb388 74%);
}
.img {
    background-image: url("https://crew.bet/wp-content/uploads/2017/02/bet-blocks-bg-purple.png?id=2014");
    background-repeat: no-repeat;
}
</style>
<!--
<style>
.carousel-open:checked + .carousel-item {
  position: static;
  opacity: 100;
}
.carousel-item {
  -webkit-transition: opacity 0.6s ease-out;
  transition: opacity 0.6s ease-out;
}
#carousel-1:checked ~ .control-1,
#carousel-2:checked ~ .control-2,
#carousel-3:checked ~ .control-3 {
  display: block;
}
.carousel-indicators {
  list-style: none;
  margin: 0;
  padding: 0;
  position: absolute;
  bottom: 2%;
  left: 0;
  right: 0;
  text-align: center;
  z-index: 10;
}
#carousel-1:checked
  ~ .control-1
  ~ .carousel-indicators
  li:nth-child(1)
  .carousel-bullet,
#carousel-2:checked
  ~ .control-2
  ~ .carousel-indicators
  li:nth-child(2)
  .carousel-bullet,
#carousel-3:checked
  ~ .control-3
  ~ .carousel-indicators
  li:nth-child(3)
  .carousel-bullet {
  color: #2b6cb0; /*Set to match the Tailwind colour you want the active one to be */
}
</style>
-->
