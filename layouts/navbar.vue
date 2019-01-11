<template>

  <v-toolbar>
    <v-toolbar-title>StatusCake &nbsp;&nbsp;</v-toolbar-title>
    <v-toolbar-items>
      <v-btn 
        flat 
        to="/">
        <v-icon>home</v-icon>
      </v-btn>
      <v-btn 
        flat 
        to="/dashboard">
        <v-icon>bar_chart</v-icon>
      </v-btn>
    </v-toolbar-items>
    <v-spacer />

    <!-- Full Screen Options -->
    <v-toolbar-items class="hidden-sm-and-down">

      <v-btn
          slot="activator"
          @click="dialog_login = true"
          flat>
          Login
      </v-btn>

      <v-dialog
        right
        flat
        v-model="dialog_login"
        width="500">
        <v-card>
          <v-card-title
            class="headline"
            primary-title
          >
            Login
          </v-card-title>
          <!-- Login page loaded in Dialog -->
          <Login :dialog_login.sync="dialog_login" />
        </v-card>
        
      </v-dialog>
  
      <v-btn 
        flat 
        to="/auth/register">
        Register
      </v-btn>

      <v-btn 
        flat 
        to="/auth/logout">
        Logout
      </v-btn>
    </v-toolbar-items>
    <!-- Mobile View Options -->
    <v-menu class="hidden-md-and-up">
        <v-toolbar-side-icon slot="activator"></v-toolbar-side-icon>
        <v-list>

          <v-list-tile to="/">
            <v-list-tile-content>
              <v-list-tile-title>
                <v-icon>home</v-icon>
              </v-list-tile-title>
             </v-list-tile-content>
          </v-list-tile>  

          <v-list-tile>
            <v-list-tile-content>
              <v-list-tile-title
                slot="activator"
                @click="dialog_login = true"
                flat>
                Login
              </v-list-tile-title>
             </v-list-tile-content>
          </v-list-tile>  
          <v-dialog
            right
            flat
            v-model="dialog_login"
            width="500">
            <v-card>
              <v-card-title
                class="headline"
                primary-title
              >
                Login
              </v-card-title>
              <!-- Login page loaded in Dialog -->
              <Login :dialog_login.sync="dialog_login" />
            </v-card>
          </v-dialog>

          <v-list-tile to="/auth/register">
            <v-list-tile-content>
              <v-list-tile-title>
                Register
              </v-list-tile-title>
             </v-list-tile-content>
          </v-list-tile>  

          <v-list-tile to="/auth/logout">
            <v-list-tile-content>
              <v-list-tile-title>
                Logout
              </v-list-tile-title>
             </v-list-tile-content>
          </v-list-tile>  

        </v-list>
      </v-menu>
  </v-toolbar>
</template> 


<script>

  import Login from '@/pages/auth/login'

  export default {
    components: {
      Login
    },
    data() {
      return {
        dialog_login : false
      }
    }
  }
</script>
