<template>
<!-- <div>
   <h1>YESSSSSSSSSSSSSS</h1>
</div>
-->
  <div class="flex">
    <!-- Premiére partie -->
    <div class="w-1/5 mt-0 h-screen body-bg2 font-mono text-gray-700">
      <hr />
      <input type="text" placeholder="search" class="search mt-14 mb-14" />
      <hr />
      <ul class="space-y-4 cl">
        <h2 class="text-xl font-semibold block">Rooms</h2>
        <li class="">
          <ul class="space-y-4 py-4">
            <li class="">#Room_1</li>
            <li class="">#Room_2</li>
          </ul>
        </li>
        <hr />
        <h2 class="text-xl font-semibold block">Users</h2>
        <li v-for="user in users" :key="user._id" class="">
          <ul class="aside -mb-8">
            <li class="aside">
              <img
                src="https://www.delta-corp.net/images/profil3.jpg"
                alt=""
                class="aside mt-8"
              />
              <div class="aside -mt-12">
                <h2 class="aside">{{ user.Username }}</h2>
                <h3 class="aside">
                  <span class="status green"></span>
                  online
                </h3>
              </div>
            </li>
          </ul>
        </li>
       
      </ul>
    </div>

    <!-- Deuxiéme partie -->
    <div class="w-4/5">
      <!--*******************-->

      <div class="flex">
        <div class="w-4/5">
          <div class="mt-0 py-0 bg-gradient-to-r from-white-500">
            <!-- Connect With -->
            <div class="flex body-bg4">
              <div class="">
                <img
                  src="https://www.delta-corp.net/images/profil3.jpg"
                  class="px-2 py-4 img-user-chat"
                />
              </div>
              <div class="mt-8 mr-96">
                <h3
                  class="text-xl"
                  style="margin-left: -120px; margin-right: 20px"
                >
                  Ali
                </h3>
                <h3 class="mr-36" style="margin-left: 1px;">
                  <span class="status green"></span>
                  Online
                </h3>
              </div>
            </div>
            <!-- End Connect With -->

            <!--Partie chat-->
            <ul id="chat" class="">
              <li class="you">
                <div class="entete mr-96 -px-28">
                  <span class="status green"></span>
                  <h2>User 1</h2>
                  <h3>10:12AM, Today</h3>
                </div>
                <div class="message">
                  Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
                  Aenean commodo ligula eget dolor.                  
                </div>
              </li>
              <li class="me">
                <div class="entete">
                  <h3>10:12AM, Today</h3>
                  <h2>{{ Username }}</h2>
                  <span class="status blue"></span>
                </div>
                <div class="message">
                  Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
                  Aenean commodo ligula eget dolor.
                </div>
              </li>
              <li class="me">
                <div class="entete">
                  <h3>10:12AM, Today</h3>
                  <h2>{{ Username }}</h2>
                  <span class="status blue"></span>
                </div>
                <div class="triangle"></div>
                <div class="message">
                  OK
                </div>
              </li>
              <li class="you">
                <div class="entete mr-96 -px-28">
                  <span class="status green"></span>
                  <h2>User 1</h2>
                  <h3>10:12AM, Today</h3>
                </div>
                <div class="message">
                  Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
                  Aenean commodo ligula eget dolor.
                </div>
              </li>
            </ul>
            <!-- End chat partie -->

            <form class="mt-68 py-4">
              <textarea
                rows="4"
                cols="80"
                name="msg"
                class="w-full h-30"
                placeholder="  Enter Your message..."
              >
              </textarea>
              <button
                class="bg-yellow-400 ring ring-yellow-400 ring-offset-2 text-white font-mono rounded-full py-2 px-6 mt-4"
              >
                SEND
              </button>
              <div class="attachment-panel">
                <a href="#" class="fa fa-thumbs-up"></a>
                <a href="#" class="fa fa-camera"></a>
                <a href="#" class="fa fa-video-camera"></a>
                <a href="#" class="fa fa-image"></a>
                <a href="#" class="fa fa-paperclip"></a>
                <a href="#" class="fa fa-link"></a>
                <a href="#" class="fa fa-trash-o"></a>
                <a href="#" class="fa fa-search"></a>
              </div>
            </form>
          </div>
        </div>
        <!-- Partie Profile -->
        <div class="1/5 h-screen body-bg3">
          <img
            src="https://i2.wp.com/nofiredrills.com/wp-content/uploads/2016/10/myavatar.png?fit=400%2C400&ssl=1"
            class="img-profile mt-32"
          />
          <h1 class="mt-4 text-xl font-mono">{{ Username }}</h1>
          <h3 class="aside">
            <span class="status green"></span>
            Online
          </h3>
          <h2 class="font-mono mt-2">{{ Email }}</h2>
          <button
            class="rounded-full bg-gray-300 px-2 py-2 mt-4 -mr-2 ring ring-gray-300 ring-offset-2"
          @click="OUT"
          >
            SIGN OUT
          </button>
        </div>
        <!-- End Partie Profile -->
      </div>
      <!--************-->
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
    data() {
    return {
      Username: "",
      Email: null,
      Password: null,
      response: "",
      success: "",
      status: "",
      users:[],
    };
  },
  mounted(){
     axios
    .get("http://localhost:3000/users/All")
    .then((reponse) => {
      this.users = reponse.data;
      console.log(this.users);
    });
      this.Username = localStorage.Username;
      this.Email = localStorage.Email;
      if(localStorage==""){
          this.$router.push('/SignIn');
      }
  },
    methods:{
        OUT(){            
            this.$router.push('/SignIn');            
            localStorage.clear();
        },
        SignIn(){
            this.$router.push('/SignIn');
        }
    }         
}
</script>

<style>
.body-bg2 {
  background-color: #f0e8e7;
  background-image: linear-gradient(315deg, #b99e99 0%, #eea942 74%);
}
.body-bg3 {
  background-color: #f0e8e7;
  background-image: linear-gradient(315deg, #e99887 0%, #e7e2db 74%);
}
.body-bg4 {
  background-color: #f0e8e7;
  background-image: linear-gradient(315deg, #e7e2db 0%, #eebe77 74%);
}
textarea {
  background-color: #a0adda27;
}
.search {
  width: 100%;
  height: 50px;
  line-height: 50px;
  padding: 0 50px 0 20px;
  background-color: #edf1f827;
  border: none;
  border-radius: 3px;
  color: #fff;
  background-image: url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/1940306/ico_search.png);
  background-repeat: no-repeat;
  background-position: 220px;
  background-size: 40px;
}
.search::placeholder {
  color: #fff;
}
.img-profile {
  border-radius: 50%;
  height: 30%;
  width: 45%;
  margin-left: 117px;
  margin-right: 0px;
}
.img-user-chat {
  border-radius: 50%;
  height: 100px;
}
.aside ul {
  list-style-type: none;
  overflow-y: scroll;
}
.aside li:hover {
  background-color: #181c2b27;
}
.aside li img {
  border-radius: 50%;
  margin-left: 15px;
  margin-right: 8px;
  height: 50px;
}
.aside li div {
  display: inline-block;
  vertical-align: top;
}
.aside li h2 {
  font-size: 14px;
  color: #fff;
  font-weight: normal;
  margin-bottom: 3px;
}
.aside li h3 {
  font-size: 12px;
  color: white;
  font-weight: normal;
}
.status {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  display: inline-block;
  margin-right: 3px;
}
.green {
  background-color: #58b666;
}
.orange {
  background-color: #ff725d;
}
.cl {
  list-style-type: none;
  overflow-y: scroll;
  height: 490px;
}
.cl li:hover {
  background-color: #181c2b27;
}
#chat {
  list-style-type: none;
  overflow-y: scroll;
  height: 330px;
  border-top: 0px solid #fff;
  border-bottom: 2px solid #fff;
}
#chat li {
  padding: 10px 30px;
}
#chat h2,
#chat h3 {
  display: inline-block;
  font-size: 13px;
  font-weight: normal;
}
#chat h3 {
  color: #bbb;
}
#chat .entete {
  margin-bottom: 5px;
}
#chat .message {
  padding: 20px;
  color: #fff;
  line-height: 25px;
  max-width: 100%;
  display: inline-block;
  text-align: left;
  border-radius: 5px;
}
#chat .me {
  text-align: right;
}
#chat .you .message {
  background-color: #ebc458;
}
#chat .me .message {
  background-color: #aeb9c0;
}
.attachment-panel {
  padding: 3px 10px;
  text-align: right;
}

.attachment-panel a,
.attachment-panel a:link,
.attachment-panel a:visited {
  margin: 0 0 0 7px;
  text-decoration: none;
  color: rgba(0, 0, 0, 0.5);
}
</style>
