<script setup>
import {ref} from "vue";

const isShowLogin = ref(true)
const isShowAllForm = ref(true)

const userName= ref('')
const userPassWord= ref('')
const userPassWordConfirm= ref('')
const validUsername = ref("admin")
const validPassword = ref("1234")
const submitLogin =()=>{
  if(validUsername.value==userName.value && validPassword.value==userPassWord.value){
      isShowAllForm.value = false
  }else{
    alert('Password or User do not Match.')
  }
}

const submitSigup=()=>{
  if(userPassWordConfirm.value!==userPassWord.value){
    alert('Confirm Password do not Match.')
  }else if(userName.value!='' && userPassWord.value!=''){
    validUsername.value=userName.value
    validPassword.value=userPassWord.value
    isShowAllForm.value = false
  }else{
    alert('User Name or Password is empty.')
  }

}
const logout = ()=>{
  if(confirm('Are You Sure?')){
    isShowAllForm.value = true
    userName.value = ''
    userPassWord.value = ''
    userPassWordConfirm.value = ''
  }
}
</script>

<template>
  <div class="flex min-h-full flex-1 flex-col justify-center px-6 py-12 lg:px-8">
    <div class="sm:mx-auto sm:w-full sm:max-w-sm">
      <img class="mx-auto h-10 w-auto" src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600" alt="Your Company" />
      <h2 v-show="isShowAllForm" class="mt-2 text-center text-2xl font-bold leading-9 tracking-tight text-gray-900">{{ isShowLogin?'Sign in to':'Sign Up for'}} your account</h2>

    </div>
    <div v-show="!isShowAllForm">
        <h1  class="mt-10 text-center text-4xl font-bold leading-9 tracking-tight text-gray-900">Hi {{ userName }}<br>Welcome To Admin Panel.</h1>
        <button type="submit" @click="logout()" class="mx-auto mt-5 flex w-20 rounded-md bg-red-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Logout</button>
    </div>
    <div v-show="isShowAllForm">
        <div class="mt-10 sm:mx-auto sm:w-full sm:max-w-sm" v-show="isShowLogin">
            <form class="space-y-6" action="#" method="POST">
              <div>
                <label for="username" class="block text-sm font-medium leading-6 text-gray-900">Email address</label>
                <div class="mt-2">
                  <input id="username" v-model="userName"  type="text" autocomplete="username" placeholder="Write your username here"  class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
                </div>
              </div>

              <div>
                <div class="flex items-center justify-between">
                  <label for="password" class="block text-sm font-medium leading-6 text-gray-900">Password</label>
                </div>
                <div class="mt-2">
                  <input id="password" v-model="userPassWord" name="password" type="password" placeholder="Write your password here" autocomplete="current-password"  class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
                </div>
              </div>

              <div>
                <button type="submit" @click.prevent="submitLogin()" class="flex w-full justify-center rounded-md bg-indigo-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Sign in</button>
              </div>
            </form>

            <p class="mt-10 text-center text-sm text-gray-500">
              Not a member?
              {{ ' ' }}
              <a href="#" @click="isShowLogin=false" class="font-semibold leading-6 text-indigo-600 hover:text-indigo-500">Register Now</a>
            </p>
        </div>

    <div class=" sm:mx-auto sm:w-full sm:max-w-sm" v-show="!isShowLogin">
      <form class="space-y-6" action="#" method="POST">
        <div>
          <label for="username" class="block text-sm font-medium leading-6 text-gray-900">User Name</label>
          <div class="mt-2">
            <input id="username" v-model="userName"  type="text" autocomplete="username" placeholder="Write your username here"  class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
          </div>
        </div>
        <div>
          <div class="flex items-center justify-between">
            <label for="password" class="block text-sm font-medium leading-6 text-gray-900">Password</label>
          </div>
          <div class="mt-2">
            <input id="password" v-model="userPassWord" name="password" type="password" autocomplete="current-password" placeholder="Write your password here"  class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
          </div>
        </div>
        <div>
          <div class="flex items-center justify-between">
            <label for="confirm_password" class="block text-sm font-medium leading-6 text-gray-900">Confirm Password</label>
          </div>
          <div class="mt-2">
            <input id="confirm_password"  v-model="userPassWordConfirm" name="confirm_password" type="password" autocomplete="current-password" placeholder="Write your password here"  class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" />
          </div>
        </div>
        <div>
          <button type="submit" @click.prevent="submitSigup()" class="flex w-full justify-center rounded-md bg-indigo-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Sign Up</button>
        </div>
      </form>

      <p class="mt-10 text-center text-sm text-gray-500">
        If a member?
        {{ ' ' }}
        <a href="#" @click="isShowLogin=true" class="font-semibold leading-6 text-indigo-600 hover:text-indigo-500">Login Now</a>
      </p>
    </div>

  </div>
  </div>
</template>

