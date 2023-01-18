<template>
  <div>
    
    <div class="container">

  
 <form @submit.prevent="reg">
  <div class="mb-3">

    <label for="exampleInputEmail1" class="form-label">Email</label>
    <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" v-model="email">
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label" >Password</label>
    <input type="password" class="form-control" id="exampleInputPassword1"  v-model="password">
  </div>

  <button type="submit" class="btn btn-primary">Submit</button>
</form>
  </div>
  </div>  
</template>

<script setup>
const supa = useSupabaseAuthClient()
const email = ref()
const password = ref()

async function reg() {
  const { error } = await supa
    .auth
    .signInWithPassword({
      email: email.value,
      password: password.value
    })

  navigateTo('/admin')
}
</script>
