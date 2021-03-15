<template>
  <form
    class="rounded mx-auto max-w-3xl w-screen my-6 inputs space-y-4 bg-center"
    @submit.prevent="FormSignUp"
  >       
      <div class="card mr-10 mb-8 mt-8">
        <h1 class="text-white font-bold uppercase flex justify-center mt-6 text-2xl">
          Welcome With US !
        </h1>
        <div class="mt-4 mr-4 space-x-4 px-20">
        <button class="rounded px-2 bg-white py-2 transform hover:scale-110 motion-reduce:transform-none" 
        style="border-radius:50%;">
          <i class="fab fa-google text-red-600 text-3xl"></i>
        </button>
        <button class="rounded px-2 py-2 bg-white transform hover:scale-110 motion-reduce:transform-none" 
        style="border-radius:50%;">
          <i class="fab fa-facebook text-blue-500 text-3xl"></i>
        </button>
        <button class="rounded px-2 py-2 bg-white transform hover:scale-110 motion-reduce:transform-none" 
        style="border-radius:50%;">
          <i class="fab fa-twitter text-blue-400 text-3xl"></i>
        </button>
      </div>
        <!-- Alert Status -->
      <div v-if="error">
        <div
          class="border-t-4 border-teal-500 rounded-b text-teal-900 px-4 py-3 shadow-md mt-6"
          role="alert"
        >
          <div class="flex">
    <div class="py-1 text-gray-500"><svg class="fill-current h-6 w-6 text-teal-500 mr-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M2.93 17.07A10 10 0 1 1 17.07 2.93 10 10 0 0 1 2.93 17.07zm12.73-1.41A8 8 0 1 0 4.34 4.34a8 8 0 0 0 11.32 11.32zM9 11V9h2v6H9v-4zm0-6h2v2H9V5z"/></svg></div>
              <p class="font-bold text-gray-500">{{ error }}</p>
            </div>
          </div>
        
      </div>
      <!-- End Alert -->
        <div class="mt-4">
          <label for="username" class="font-black">Username</label>
          <input
            class="placeholder-gray-500 placeholder-opacity-100 appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
            type="input"
            name="Username"
            id="Username"
            placeholder="Username"
            maxlength="20"
            minlength="3"
            v-model="Username"
            required
          />
        </div>
        <div class="mt-4">
          <label for="address" class="font-black">Email</label>
          <input
            class="placeholder-gray-500 placeholder-opacity-100 appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
            type="email"
            name="Email"
            id="Email"
            placeholder="Example@gmail.com"
            maxlength="200"
            minlength="15"
            v-model="Email"
            required
          />
        </div>

        <div class="mt-4">
          <label for="password" class="font-black">Password</label>
          <input
            class="placeholder-gray-500 placeholder-opacity-100 appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
            type="password"
            name="Password"
            id="Password"
            placeholder="**************"
            maxlength="200"
            minlength="8"
            v-model="Password"
            required
          />
        </div>

        <div>
          <input type="checkbox" class="rounded text-pink-500 mt-4" required/>
          <label class="font-mono tracking-tighter"
            >&nbsp; I Agree to the terms of users</label
          >
        </div>
        <div>
          <div class="px-4 py-6 flex justify-center">
            <div class="flex space-x-4">
              <button
                type="submit"
                class="bg-white px-4 py-2 rounded-full font-semibold text-red-600 transform hover:scale-110 motion-reduce:transform-none"
                @click="persist"
              ><i class="fas fa-user-plus"></i>
                SIGN UP
              </button>
            </div>
        </div>
        <button class="-mt-4 text-white text-xl transform hover:scale-150 motion-reduce:transform-none" style="margin-left:-500px;" @click="SignIn"><i class="fas fa-sign-in-alt"></i></button>
        </div>
      </div>
    
  </form>
</template>

<script>
import axios from "axios";
export default {
  el: "#app",
  data() {
    return {
      Username: "",
      Email: "",
      Password: "",
      response: "",
      success: "",
      error: "",
    };
  },
  mounted() {
     if (localStorage.Username) {
      this.Username = localStorage.Username;
    }
    if (localStorage.Email) {
      this.Email = localStorage.Email;
    }
  },
  methods: {
    FormSignUp() {      
      axios
        .post("http://localhost:3000/users/SignUp", {
          Username: this.Username,
          Email: this.Email,
          Password: this.Password,
        })
        .then((response) => {
          console.log(response);
          //localStorage.Password = this.response.Password;
          this.response = response.data
          if(this.response.success==true) {
            this.$router.push('/SignIn');}
          // this.success = "Data saved successfully";
          // this.response = JSON.stringify(response, null, 2);
          else {
              this.$router.push('/SignUp');
              this.error = this.response.error;
              this.Username = "";
              this.Email = "";
              this.Password = "";
          }
        })
        .catch((error) => {
          this.response = "Error: " + error.response.status;
        });
    },
    persist() {
      localStorage.Email = this.Email;
      console.log("Success");
    },
    SignIn(){
        this.$router.push('/SignIn');
    },
  },
};
</script>

<style>
.card {
  background-color: #f0e8e7;
  background-image: linear-gradient(315deg, #c2270b 0%, #cfb388 74%);
  display: flex;
  flex-direction: column;
  width: 600px;
  padding: 20px 25px;
  border-radius: 20px;
  box-shadow: 0 19px 38px rgba(0, 0, 0, 0.13);
  margin-left: 80px;
  margin-top: 3rem;
}
label {
  color: #fffdff;
}
.labled {
  margin-left: 35px;
  color: white;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
button {
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
input[type="text"] {
  text-transform: capitalize;
}
</style>
