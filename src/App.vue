<template>
  <div>
    <nav class="navbar navbar-expand-lg custom-navbar" data-bs-theme="dark">
      <div class="container">
        <router-link :to="{ name: 'home' }" class="navbar-brand">
          HOME
        </router-link>

        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <router-link
                to="/products"
                class="nav-link active"
                aria-current="page"
              >
                PRODUCTS
              </router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <!--- render router view -->
    <router-view />
  </div>
</template>

<style scoped>
.custom-navbar {
  background-color: #132133;
  padding: 14px 0;
  box-shadow: 0 4px 15px rgba(19, 33, 51, 0.15);
}

.navbar-brand {
  color: #ffffff !important;
  font-size: 21px;
  font-weight: 700;
  letter-spacing: 0.5px;
  transition: 0.2s ease;
}

.navbar-brand:hover {
  color: #ffc107 !important;
}

.nav-link {
  color: #ffffff !important;
  font-size: 21px;
  font-weight: 700;
  margin-left: 20px;
  padding: 8px 14px !important;
  transition: 0.2s ease;
}

.nav-link:hover {
  color: #ffc107 !important;
  background-color: transparent !important;
}
</style>