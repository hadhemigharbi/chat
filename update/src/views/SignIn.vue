<template>
  <form
    class="rounded mx-auto max-w-3xl w-full my-6 inputs space-y-4 bg-center"
    @submit.prevent="submitForm"
  >
    <div class="card mr-4 mb-10 mt-10">
      <h1 class="text-white font-bold uppercase flex justify-center mt-8 text-2xl">
        Hello, Friends !
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
      <div v-if="status">
        <div
          class="border-t-4 border-teal-500 rounded-b text-teal-900 px-4 py-3 shadow-md mt-6 -mb-6"
          role="alert"
        >
          <div class="flex">
            <div class="py-1 text-gray-500"><svg class="fill-current h-6 w-6 text-teal-500 mr-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M2.93 17.07A10 10 0 1 1 17.07 2.93 10 10 0 0 1 2.93 17.07zm12.73-1.41A8 8 0 1 0 4.34 4.34a8 8 0 0 0 11.32 11.32zM9 11V9h2v6H9v-4zm0-6h2v2H9V5z"/></svg></div>
              <p class="font-bold text-gray-500">{{ status }}</p>
          </div>
        </div>
      </div>
      <!-- End Alert -->

      <div class="mt-10">
        <label for="address" class="font-black">Email</label>
        <input
          class="placeholder-gray-500 placeholder-opacity-100 appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
          type="email"
          name="Email"
          id="Email"
          placeholder="Example@gmail.com"
          maxlength="200"
          minlength="10"
          v-model="Email"
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
          onkeypress="return ((event.charCode > 64 && event.charCode < 91) || (event.charCode > 96 && event.charCode < 123) || event.charCode == 8 || event.charCode == 32 || (event.charCode >= 48 && event.charCode <= 57));"
        />
        <h3
          class="text-gray-200 font-mono tracking-tighter flex justify-center mt-8"
        >
          Forget Your Password?
        </h3>
      </div>

      <div class="px-8 py-4 mt-4 flex justify-center">
        <div class="flex">
          <button
            type="submit"
            class="bg-white px-4 py-2 -mt-2 rounded-full font-semibold text-red-700 transform hover:scale-110 motion-reduce:transform-none"
          ><i class="fas fa-sign-in-alt"></i>
            SIGN IN
          </button>
        </div>
      </div>
      <button @click="SignUp" class="w-10 text-white text-xl transform hover:scale-150 motion-reduce:transform-none"><i class="fas fa-user-plus"></i></button>
    </div>
  </form>
</template>

<style scoped></style>

<script>
//import router from '../router';
import axios from "axios";
export default {
  el: "#app",
  data() {
    return {
      Username: "",
      Email: null,
      Password: null,
      response: "",
      success: "",
      status: "",
    };
  },
  mounted() {
     
    if (localStorage.Email) {
      this.Email = localStorage.Email;
    }
    if (localStorage.Password) {
      this.Password = localStorage.Password;
    }
  },
  methods: {
    submitForm() {
      axios
        .post("http://localhost:3000/users/SignIn", {
          Email: this.Email,
          Password: this.Password,
        })
        .then((response) => {
          console.log(response);
          this.response = response.data;
          if (this.response.success == true) {
            this.$router.push("/UI");
            localStorage.Username = this.response.username;
            localStorage.Email = this.Email;
            localStorage.Password = this.response.password;
            localStorage.Token = this.response.token;
          } else{
            this.$router.push("/SignIn");
            this.status = this.response.status;
            localStorage.clear();
            //this.response = JSON.stringify(response, null, 2);
          }         
        })
        .catch((error) => {
          this.response = "Error: " + error.response.status;
        });
    },
    Verif(){
      if (localStorage.Token == ''){
            this.$router.push("/SignIn");
          }
    },
     SignUp(){
        this.$router.push('/SignUp');
    },
  },
};
</script>