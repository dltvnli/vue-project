<script setup>
import { ref } from 'vue'
import axios from 'axios'
// name, email, password
const user = ref({
  name:'',
  email:'',
  password:''
})

const register = async () => {
  await axios.post('http://localhost:8000/api/register/', {
    name: user.value.name,
    email: user.value.email,
    password: user.value.password
  })

  // const response = await axios.post('http://localhost:8000/api/login/', {
  //   email: user.value.email,
  //   password: user.value.password
  // })
  // localStorage.setItem('access_token', response.data.access)
  // localStorage.setItem('refresh_token', response.data.refresh)
  // router.push('/')
}
</script>

<template>
	<section class="h-100">
		<div class="container h-100">
			<div class="row justify-content-sm-center py-5 h-100">
				<div class="col-xxl-4 col-xl-5 col-lg-5 col-md-7 col-sm-9">
					<div class="card shadow-lg">
						<div class="card-body p-5">
							<h1 class="fs-4 card-title fw-bold mb-4">Sign up</h1>
							<form method="POST" class="needs-validation" novalidate="" >
								<div class="mb-3">
									<label class="mb-2 text-muted" for="name">Name</label>
									<input id="name" type="text" class="form-control" name="name" value="" required >
									<div class="invalid-feedback">
										Name is required	
									</div>
								</div>

								<div class="mb-3">
									<label class="mb-2 text-muted" for="email">E-Mail Address</label>
									<input id="email" type="email" class="form-control" name="email" value="" required>
									<div class="invalid-feedback">
										Email is invalid
									</div>
								</div>

								<div class="mb-3">
									<label class="mb-2 text-muted" for="password">Password</label>
									<input id="password" type="password" class="form-control" name="password" required>
								    <div class="invalid-feedback">
								    	Password is required
							    	</div>
								</div>

								<div class="align-items-center d-flex" >
                  
									<button class="btn btn-primary ms-auto">
                    <RouterLink to="/" class="nav-link px-2 text-white ">Register</RouterLink>
									</button>
								</div>
							</form>
						</div>
						<div class="card-footer py-3 border-0">
							<div class="text-center">
								Already have an account? <a href="login" class="text-dark">Login</a>
							</div>
						</div>
					</div>
					<div class="text-center mt-5 text-muted">
						Copyright &copy; 2017-2023 &mdash; Your Company 
					</div>
				</div>
			</div>
		</div>
	</section>
</template>
<style scoped>
.card-hover:hover {
  box-shadow: 0 0 11px rgba(33, 33, 33, 0.2);
}

</style>