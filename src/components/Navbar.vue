<template>
  <header class="p-3 text-bg-dark">
    <div class="container">
      <div
        class="d-flex flex-wrap align-items-center justify-content-center justify-content-lg-start"
      >
      <svg xmlns="http://www.w3.org/2000/svg" width="23" height="23" fill="currentColor" class="bi bi-apple" viewBox="0 0 16 16">
  <path d="M11.182.008C11.148-.03 9.923.023 8.857 1.18c-1.066 1.156-.902 2.482-.878 2.516.024.034 1.52.087 2.475-1.258.955-1.345.762-2.391.728-2.43Zm3.314 11.733c-.048-.096-2.325-1.234-2.113-3.422.212-2.189 1.675-2.789 1.698-2.854.023-.065-.597-.79-1.254-1.157a3.692 3.692 0 0 0-1.563-.434c-.108-.003-.483-.095-1.254.116-.508.139-1.653.589-1.968.607-.316.018-1.256-.522-2.267-.665-.647-.125-1.333.131-1.824.328-.49.196-1.422.754-2.074 2.237-.652 1.482-.311 3.83-.067 4.56.244.729.625 1.924 1.273 2.796.576.984 1.34 1.667 1.659 1.899.319.232 1.219.386 1.843.067.502-.308 1.408-.485 1.766-.472.357.013 1.061.154 1.782.539.571.197 1.111.115 1.652-.105.541-.221 1.324-1.059 2.238-2.758.347-.79.505-1.217.473-1.282Z"/>
  <path d="M11.182.008C11.148-.03 9.923.023 8.857 1.18c-1.066 1.156-.902 2.482-.878 2.516.024.034 1.52.087 2.475-1.258.955-1.345.762-2.391.728-2.43Zm3.314 11.733c-.048-.096-2.325-1.234-2.113-3.422.212-2.189 1.675-2.789 1.698-2.854.023-.065-.597-.79-1.254-1.157a3.692 3.692 0 0 0-1.563-.434c-.108-.003-.483-.095-1.254.116-.508.139-1.653.589-1.968.607-.316.018-1.256-.522-2.267-.665-.647-.125-1.333.131-1.824.328-.49.196-1.422.754-2.074 2.237-.652 1.482-.311 3.83-.067 4.56.244.729.625 1.924 1.273 2.796.576.984 1.34 1.667 1.659 1.899.319.232 1.219.386 1.843.067.502-.308 1.408-.485 1.766-.472.357.013 1.061.154 1.782.539.571.197 1.111.115 1.652-.105.541-.221 1.324-1.059 2.238-2.758.347-.79.505-1.217.473-1.282Z"/>
</svg>
        
        <ul class="nav col-12 col-lg-auto me-lg-auto mb-2 justify-content-center mb-md-0">
          <li><RouterLink to="/" class="nav-link px-2 text-white">Home</RouterLink></li>
          <li>
            <div class="dropdown">
              <a
                class="dropdown-toggle nav-link px-2 text-white"
                href="#"
                role="button"
                data-bs-toggle="dropdown"
                aria-expanded="false"
                >Products</a
              >
              <ul class="dropdown-menu">
                <li>
                  <RouterLink
                    :to="{ name: 'products', query: { category: 1 } }"
                    class="dropdown-item"
                    >Phones</RouterLink
                  >
                </li>
                <li>
                  <RouterLink
                    :to="{ name: 'products', query: { category: 2 } }"
                    class="dropdown-item"
                    >Laptops</RouterLink
                  >
                </li>
                <li>
                  <RouterLink
                    :to="{ name: 'products', query: { category: 3 } }"
                    class="dropdown-item"
                    >Headphones</RouterLink
                  >
                </li>
                <li>
                  <RouterLink
                    :to="{ name: 'products', query: { category: 4 } }"
                    class="dropdown-item"
                    >Watch</RouterLink
                  >
                </li>
                <li>
                  <RouterLink
                    :to="{ name: 'products', query: { category: 5 } }"
                    class="dropdown-item"
                    >Ipad</RouterLink
                  >
                </li>
              </ul>
            </div>
          </li>
          <li><RouterLink to="/cart" class="nav-link px-2 text-white">Cart</RouterLink></li>
          <li><RouterLink to="/about" class="nav-link px-2 text-white">About</RouterLink></li>
          <li><RouterLink to="/wishlist" class="nav-link px-2 text-white">Wishlist</RouterLink></li>
          <li><RouterLink to="/login" class="nav-link px-2 text-white">Login</RouterLink></li>
          <li><button class="btn btn-primary" @click="logout">logout</button></li>
        </ul>
        <div class="col-md-3 text-end">
        <button type="button" class="btn btn-outline-primary me-2">Login</button>
        <button type="button" class="btn btn-primary">Sign-up</button>
      </div>
      </div>
    </div>
  </header>
</template>
<script setup></script>