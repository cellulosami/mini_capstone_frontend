<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Mini Capstone <span style="font-size: 15px; color: gray; margin-left: 10px;" v-if="userEmail">Welcome, {{ userEmail }}!</span></a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <router-link class="nav-link" to="/">Home</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/products">Products</router-link>
            </li>
            <li class="nav-item" v-if="userEmail">
              <router-link class="nav-link" to="/Logout">Logout</router-link>
            </li>
            <div v-else>
              <li class="nav-item">
                <router-link class="nav-link" to="/Login">Login</router-link>
              </li>
              <li class="nav-item">
                <router-link class="nav-link" to="/Signup">Signup</router-link>
              </li>
            </div>
            <!-- <li class="nav-item dropdown">
              <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                Dropdown
              </a>
              <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
                <li><a class="dropdown-item" href="#">Action</a></li>
                <li><a class="dropdown-item" href="#">Another action</a></li>
                <li><hr class="dropdown-divider"></li>
                <li><a class="dropdown-item" href="#">Something else here</a></li>
              </ul>
            </li> -->
            <!-- <li class="nav-item">
              <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
            </li> -->
          </ul>
          <form class="d-flex">
            <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
            <button class="btn btn-outline-success" type="submit">Search</button>
          </form>
        </div>
      </div>
    </nav>
    <br />
    <div class="container" id="main-body">
      <router-view/>
    </div>
  </div>
</template>

<style>
#main-body {
  background-color: #9fb8ad;
  border-radius: 10px;
}

#app {
  font-family: "Century Gothic", CenturyGothic, AppleGothic, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #383e56;
  background-color: #383e56;
}

#nav {
  padding: 30px;
  text-align: center;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav-item a.router-link-exact-active {
  color: #fff;
}
</style>

<script>
export default {
  data: function () {
    return {
      userEmail: null
    };
  },
  mounted: function () {
      localStorage.removeItem("jwt");
      localStorage.removeItem("userEmail");
  },
  updated: function() {
    if (localStorage.userEmail) {
      this.userEmail = localStorage.userEmail;
    } else {
      this.userEmail = null;
    }
  }
};
</script>