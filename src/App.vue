<template>
  <div class="flexible-content">
    <!--Navbar-->
    <mdb-navbar class="flexible-navbar white" light position="top" scrolling>
      <mdb-navbar-brand href="#" target="_blank">Loan App</mdb-navbar-brand>
      <mdb-navbar-toggler>
        <mdb-navbar-nav left> </mdb-navbar-nav>
        <mdb-navbar-nav right>
          <mdb-nav-item href="#!" waves-fixed>
            <mdb-icon fab class="text-black" icon="facebook-square" />
          </mdb-nav-item>
          <mdb-nav-item href="#!" waves-fixed>
            <mdb-icon fab icon="twitter" />
          </mdb-nav-item>
          <mdb-nav-item
            href="#"
            waves-fixed
            class="border border-light rounded"
            target="_blank"
          >
            <i class="fas fa-sign-out-alt"></i>Log Out
          </mdb-nav-item>
        </mdb-navbar-nav>
      </mdb-navbar-toggler>
    </mdb-navbar>
    <!--/.Navbar-->
    <!-- Sidebar -->
    <div class="sidebar-fixed position-fixed">
      <a class="logo-wrapper">
        <img alt class="img-fluid" src="./assets/logo-mdb-vue-small.png" />
      </a>
      <mdb-list-group class="list-group-flush">
        <router-link to="/dashboard" @click.native="activeItem = 1">
          <mdb-list-group-item
            :action="true"
            :class="activeItem === 1 && 'active'"
          >
            <mdb-icon icon="table" class="mr-3" />Loan List
          </mdb-list-group-item>
        </router-link>
        <router-link to="/loan-application" @click.native="activeItem = 2">
          <mdb-list-group-item
            :action="true"
            :class="activeItem === 2 && 'active'"
          >
            <mdb-icon icon="edit" class="mr-3" />Loan Application
          </mdb-list-group-item>
        </router-link>
        <router-link to="/tables" @click.native="activeItem = 3">
          <mdb-list-group-item
            :action="true"
            :class="activeItem === 3 && 'active'"
          >
            <mdb-icon icon="diagnoses" class="mr-3" />Server Diagnostics
          </mdb-list-group-item>
        </router-link>
      </mdb-list-group>
    </div>
    <!-- /Sidebar  -->
    <main>
      <div class="mt-5 p-5">
        <router-view></router-view>
      </div>
      <!-- Footer -->
      <ftr color="primary-color-dark" class="text-center font-small darken-2">
        <hr class="my4" />
        <div class="pb-4">
          <a href="#">
            <mdb-icon fab icon="facebook-square" class="mr-3" />
          </a>
          <a href="#">
            <mdb-icon fab icon="twitter" class="mr-3" />
          </a>
          <a href="#">
            <mdb-icon fab icon="youtube" class="mr-3" />
          </a>
          <a href="#">
            <mdb-icon fab icon="google-plus" class="mr-3" />
          </a>
          <a href="#">
            <mdb-icon fab icon="dribbble" class="mr-3" />
          </a>
          <a href="#">
            <mdb-icon fab icon="pinterest" class="mr-3" />
          </a>
          <a href="#">
            <mdb-icon fab icon="github" class="mr-3" />
          </a>
          <a href="#">
            <mdb-icon fab icon="codepen" class="mr-3" />
          </a>
        </div>
        <p class="footer-copyright mb-0 py-3 text-center">
          &copy; {{ new Date().getFullYear() }} Copyright Keith Ong
        </p>
      </ftr>
    </main>
  </div>
</template>

<script>
import {
  mdbContainer,
  mdbNavbar,
  mdbNavbarBrand,
  mdbNavItem,
  mdbNavbarNav,
  mdbNavbarToggler,
  mdbBtn,
  mdbIcon,
  mdbListGroup,
  mdbListGroupItem,
  mdbCardBody,
  mdbFooter,
  waves
} from 'mdbvue'
import Dashboard from './components/Dashboard'
import LoanApplication from './components/LoanApplication'

export default {
  name: 'AdminTemplate',
  components: {
    mdbContainer,
    mdbNavbar,
    mdbNavbarBrand,
    mdbNavItem,
    mdbNavbarNav,
    mdbNavbarToggler,
    mdbBtn,
    mdbListGroup,
    mdbListGroupItem,
    mdbIcon,
    mdbCardBody,
    ftr: mdbFooter,
    Dashboard,
    LoanApplication
  },
  data() {
    return {
      activeItem: 1
    }
  },
  beforeMount() {
    this.activeItem = this.$route.matched[0].props.default.page
  },
  mixins: [waves]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
main {
  background-color: #ededee;
}

.flexible-content {
  transition: padding-left 0.3s;
  padding-left: 270px;
}

.flexible-navbar {
  transition: padding-left 0.5s;
  padding-left: 270px;
}

.sidebar-fixed {
  left: 0;
  top: 0;
  height: 100vh;
  width: 270px;
  box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  z-index: 1050;
  background-color: #fff;
  padding: 1.5rem;
  padding-top: 0;
}

.sidebar-fixed .logo-wrapper img {
  width: 100%;
  padding: 2.5rem;
}

.sidebar-fixed .list-group-item {
  display: block !important;
  transition: background-color 0.3s;
}

.sidebar-fixed .list-group .active {
  box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  border-radius: 5px;
}

@media (max-width: 1199.98px) {
  .sidebar-fixed {
    display: none;
  }
  .flexible-content {
    padding-left: 0;
  }
  .flexible-navbar {
    padding-left: 10px;
  }
}
</style>
<style>
.navbar-light .navbar-brand {
  margin-left: 15px;
  color: #2196f3 !important;
  font-weight: bolder;
}
</style>
