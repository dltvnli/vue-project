<script setup>
import axios from 'axios'
import { ref } from 'vue'
  const user = ref({
    email: '',
    password: ''
  })

  const loging = async () => {
    const responce = await axios.post('http://localhost:8000/api/login/', {
      email: user.value.email,
      password: user.value.password
    })
    localStorage.setItem('access_token', responce.data.access)
    localStorage.setItem('refresh_token', responce.data.refresh)
    // this.$router.push('/')
  }

</script>

<template>
  <main class="form-signin w-100 m-auto text-center container">
    <main class="row py-lg-3" > </main>
        <main class="col-lg-6 col-md-8 mx-auto"> </main>
  <form>
    <h1 class="h3 mb-5 fw-normal">Please login</h1>
    <main class="row py-lg-1"> </main>

    <div class="form-floating position top-50 start-50 translate-middle" style="width: 18rem;" >
      <input type="email" class="form-control" id="floatingInput" placeholder="name@example.com">
      <label for="floatingInput">Email</label>
    </div>
    <div class="form-floating position top-50 start-50 translate-middle " style="width: 18rem;">
      <input type="password" class="form-control" id="floatingPassword" placeholder="Password">
      <label for="floatingPassword">Password</label>
    </div>

    <div class="checkbox mb-">
      <label>
        <input type="checkbox" value="remember-me"> Remember me
      </label>
    </div>
    <button class="w-25 btn btn-lg btn-primary" style="width: 18rem;" type="submit">Login</button>
    <p class="mt-5 mb-3 text-body-secondary">© 2023</p>
  </form>
</main>
</template>