<template>
  <v-app id="inspire">
    <!-- Logo and title start -->
    <v-navigation-drawer v-model="drawer" app color="#921616">
      <v-sheet>
        <v-list
          style="
            margin-top: -10px;
            margin-bottom: -10px;
            background-color: #030303;
          "
        >
          <v-list-item>
            <v-list-item-icon>
              <img
                src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSXY-_lnGo3tAwURreIu9GWHNphPO9Dl_JqqA&usqp=CAU"
                height="40px"
                width="40px"
                style="margin-right: -10px"
              />
            </v-list-item-icon>

            <v-list-item-content class="font-weight-thin">
              <strong
                style="color:#ffffff;
                  font-size: 35px;
                  font-weight: bolder;
                  
                  
                "
              >
                FILMOVI</strong
              >
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-sheet>
      <!-- Logo and title end -->

      <v-divider></v-divider>

      <!-- Navigation start -->
      <v-list rounded flat>
        <v-list-item
          v-for="[icon, text, route] in links"
          :key="icon"
          :to="route"
          link
        >
          <v-list-item-icon >
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title id="li">{{ text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <!-- Navigation end -->

    <!--App bar-->
    <v-row class="d-lg-none">
      <v-col style="background-color:#050505">
        
          <v-app-bar dense elevation="15" fixed>
            <v-btn @click="drawer = !drawer" icon>
              <v-app-bar-nav-icon style="color: rgb(2, 2, 2)"></v-app-bar-nav-icon>
            </v-btn>
            <v-list-item>
              <v-list-item-icon>
                <img
                  src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRmk0EqWA8EpYGjKEBtv_W14PNifzQz4-jSKQ&usqp=CAU"
                  height="40px"
                  width="40px"
                  style="margin-right: -10px"
                />
              </v-list-item-icon>

              <v-list-item-content class="font-weight-thin">
                <strong
                  style="color:#f1eaea; 
                  font-size: 35px;
                  font-weight: bolder;
                  
                  "
                >
                  FILMOVI</strong
                >
              </v-list-item-content>
            </v-list-item>
            <v-spacer></v-spacer>

            <v-btn icon href="/" style="color: #500000">
              <v-icon>mdi-home</v-icon>
            </v-btn>
          </v-app-bar>
       
      </v-col>
    </v-row>
    <!--App bar end-->

    <!-- Main section start -->
    <v-main style="background-color: #181818">
      <v-container>
        <router-view></router-view>
      </v-container>

      <!--FOOOTER-->
    
      
 
   
  <v-footer
    class="black lighten-1 white--text text-center"

    padless
    style="
          position: absolute;
          bottom: 0;
          min-width: 100%;
          height: 60px; /* Height of the footer */
          background: #0e0e0e;
        "
  >
    <v-row
      justify="center"
      no-gutters
    >
      
      
    </v-row>
  </v-footer>
    
 
    </v-main>
  </v-app>
</template>
<style>
.foot {
  width: 300px;
  margin: auto;
}
</style>

<script>
export default {
  data: () => ({
    drawer: true,

    group: null,
    links: [
      ["mdi-home", "Home", "/"],
      ["mdi-movie-open", "Filmovi", "/filmovi"],
      ["mdi-information-outline", "About", "/about"],
    ],
  }),
};
</script>