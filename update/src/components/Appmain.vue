<template>
  <form
    class="rounded mx-auto max-w-3xl w-full my-6 inputs space-y-4 bg-center"
  >
  
    <div class="flex flex-nowrap space-x-4">
      <div class="card mr-4 mb-10 mt-10">
        <h1 class="text-gray-200 font-bold uppercase flex justify-center mt-6">Welcome With US !</h1>
        <div class="mt-4 mr-4 px-20 space-x-0">
            <button class="justify-center"><i class="fab fa-google px-2 text-gray-50 text-3xl"></i></button>
            <button class="rounded-full"><i class="fab fa-facebook px-2 text-gray-50 text-3xl"></i></button>
            <button class="rounded-full"><i class="fab fa-twitter px-2 text-gray-50 text-3xl"></i></button>
        </div>
        <div class="mt-4">
          <label for="username" class="font-black">Username</label>
          <input
            class="placeholder-gray-500 placeholder-opacity-100 border border-gray-400 px-4 py-2 rounded w-full focus:outline-none focus:ring focus:border-blue-300"
            type="input"
            name="address"
            id="address"
            placeholder="Username"
            maxlength="20"
            minlength="4"
            v-model="username"
            required
          />
        </div>
        <div class="mt-4">
          <label for="address" class="font-black">Email</label>
          <input
            class="placeholder-gray-500 placeholder-opacity-100 border border-gray-400 px-4 py-2 rounded w-full focus:outline-none focus:ring focus:border-blue-300"
            type="email"
            name="address"
            id="address"
            placeholder="Example@gmail.com"
            maxlength="200"
            minlength="20"
            v-model="address"
            required
          />
        </div>

        <div class="mt-4">
          <label for="password" class="font-black">Password</label>
          <input
            class="placeholder-gray-500 placeholder-opacity-100 border border-gray-400 px-4 py-2 rounded w-full focus:outline-none focus:ring focus:border-blue-300"
            type="password"
            name="password"
            id="password"
            placeholder="**************"
            maxlength="200"
            minlength="20"
            v-model="password"
            onkeypress="return ((event.charCode > 64 && event.charCode < 91) || (event.charCode > 96 && event.charCode < 123) || event.charCode == 8 || event.charCode == 32 || (event.charCode >= 48 && event.charCode <= 57));"
            required
          />
        </div>

        <div>
          <input type="checkbox" class="rounded text-pink-500 mt-4" required />
          <label class="font-mono tracking-tighter"
            >&nbsp; I Agree to the terms of users</label
          >
        </div>
        <div>
          <div class="px-4 py-6 flex justify-center">
            <div class="flex space-x-4">
              <button
                type="submit"
                class="bg-white px-4 py-2 rounded-full font-semibold text-purple-700 transform hover:scale-110 motion-reduce:transform-none">
                SIGN UP
              </button>
            </div>
          </div>
        </div>
      </div>

      <div class="cardtwo mr-4 mb-10 mt-10">
        <h1 class="text-gray-200 font-bold uppercase flex justify-center mt-8">Hello, Friends !</h1>
        <div class="mt-4 mr-4 space-x-2 px-20">
            <button class="rounded-full px-2"><i class="fab fa-google text-gray-50 text-3xl"></i></button>
            <button class="rounded-full px-2"><i class="fab fa-facebook text-gray-50 text-3xl"></i></button>
            <button class="rounded-full px-2"><i class="fab fa-twitter text-gray-50 text-3xl"></i></button>
        </div>
        <div class="mt-16">
          <label for="address" class="font-black">Email</label>
          <input
            class="placeholder-gray-500 placeholder-opacity-100 border border-gray-400 px-4 py-2 rounded w-full focus:outline-none focus:ring focus:border-blue-300"
            type="email"
            name="address"
            id="address"
            placeholder="Example@gmail.com"
            maxlength="200"
            minlength="20"
            v-model="address"
            required
          />
        </div>
          <div class="mt-4">
          <label for="password" class="font-black">Password</label>
          <input
            class="placeholder-gray-500 placeholder-opacity-100 border border-gray-400 px-4 py-2 rounded w-full focus:outline-none focus:ring focus:border-blue-300"
            type="password"
            name="password"
            id="password"
            placeholder="**************"
            maxlength="200"
            minlength="20"
            v-model="password"
            onkeypress="return ((event.charCode > 64 && event.charCode < 91) || (event.charCode > 96 && event.charCode < 123) || event.charCode == 8 || event.charCode == 32 || (event.charCode >= 48 && event.charCode <= 57));"
            required
          />
          <h3 class="text-gray-200 font-mono tracking-tighter flex justify-center mt-8">Forget Your Password?</h3>
        </div>
                    
        <div class="px-8 py-4 mt-4 flex justify-center">
            <div class="flex">
              <button
                type="submit"
                class="bg-white px-4 py-2 mt-2 rounded-full font-semibold text-purple-700 transform hover:scale-110 motion-reduce:transform-none">
                SIGN IN
              </button>
            </div>             
          </div>
      </div>
    </div>
  </form>
</template>

<script>
export default { };
</script>

<style lang="scss" scoped>
.body-bg {
  background-color: #ac4533;
  background-image: linear-gradient(315deg, #8d422f 0%, #624ddb 74%);
}
.card {
  background-color: #ac4533;
  background-image: linear-gradient(315deg, #8d422f 0%, #624ddb 74%);
  display: flex;
  flex-direction: column;
  width: 500px;
  padding: 20px 25px;
  border-radius: 20px;
  box-shadow: 0 19px 38px rgba(0, 0, 0, 0.13);
}

.cardtwo {
  background-color: #ac4533;
  background-image: linear-gradient(315deg, #8d422f 0%, #624ddb 74%);
  display: flex;
  flex-direction: column;
  width: 500px;
  padding: 10px 15px;
  border-radius: 20px;
  box-shadow: 0 19px 38px rgba(0, 0, 0, 0.13);
}
label {
  color: #c9bbc9;
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
