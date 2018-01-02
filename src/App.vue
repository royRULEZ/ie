<template>
  <v-app>
  <!-- <div id="app"> -->

    <!-- sidemenu -->
    <v-navigation-drawer absolute temporary v-model="sideNav" app>
      <div id="nav_drawer-title">Insanely Expensive</div>
    </v-navigation-drawer>
    <!-- /sidemenu -->

    <header>
      <div id="header-upper" class="clearfix">
        <div id="header_upper-menu">
            <button id="menu-button" class="rp-button header-icon" v-on:click="sideNav = !sideNav">
              <span class="material-icons">menu</span> 
            </button>
            <router-link to="/">
              <button class="rp-button header">Home</button>
            </router-link>
            <button class="rp-button header">Store</button>
        </div>
        <div id="header_upper-actions">
            <button class="rp-button header">Subscribe</button>  
            <button id="search-button" class="rp-button header-icon">
              <span class="material-icons">search</span>
            </button>                      
        </div>        
      </div>
      <div id="header-lower" class="clearfix">
        <div id="header-l-logo">
            Insanely <img src="./assets/images/diamond.png" /> Expensive
        </div>        
      </div>
    </header>

    <!-- nav -->
    <nav>
      <span class="color-test">Fashion</span>
      <span>People</span>
      <span>Cars</span>
      <span>Homes</span>
      <span>Locations</span>
      <span>Food</span>
      <span>Tech</span>

    </nav>
    <!-- /nav -->

    <!-- home-ad -->
      <div id="list_ad-billboard">
          <div id="list_ad-b-ad"></div>
      </div>
    <!-- /home-ad -->

    <v-content>
    <v-container fluid>
    <!-- router -->
    <router-view/>
    </v-container>
    </v-content>

    <!-- footer -->
    <!-- <v-footer app> -->
    <footer>
      <div id="footer-title">
        Insanely <img src="./assets/images/diamond.png" /> Expensive
      </div>
      <div id="footer-social">

      </div>
      <div id="footer-links">
        <span>link</span>   
      </div>      
      <div id="footer-info">
        © insanelyexpensive.com | ALL RIGHTS RESERVED.
      </div> 
    </footer>
    <!-- /footer -->
    <!-- </v-footer> -->

  </v-app>
  <!-- </div> -->
</template>

<script>
export default {
  name: "app",
  data: () => ({
    sideNav: false
  })
};
</script>

<style lang="scss">
  @import "./assets/scss/main.scss";

  .application.theme--light {
    background: #FFF;
    //color: rgba(0,0,0,.87);
  }
</style>
