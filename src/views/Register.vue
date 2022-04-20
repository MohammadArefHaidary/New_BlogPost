<template>
  <div class="Register">
    <div class="row">
      <div class=" col-lg-3 mx-auto border shadow rounded p-4 mt-3 bg-light bg-gradient size ">
            <h1 class="text-center mt-3 mb-4">Register</h1>
            <form @submit.prevent="doRegister">
                <div class="form-group">
                 <label for="usernameInput">Username</label>
                 <input type="text" class="form-control" id="usernameInput" v-model="username"
                 :class="{'is-invalid':usernameE===true,
                 'is-valid':usernameE===false}">
                  <div class="invalid-feedback" v-if="usernameE">
                      {{usernameEM}}
                </div>
                 <div class="valid-feedback" v-if="usernameE===false">
                Looks good!
                </div>
                </div>
                <div class="form-group">
                    <label for="passwordInput">Password</label>
                    <input type="password" class="form-control" id="passwordInput" v-model="password"
                     :class="{'is-invalid':passwordE===true,
                     'is-valid':passwordE===false}">  
                      <div class="invalid-feedback" v-if="passwordE">
                      {{passwordEM}}
                </div>
                 <div class="valid-feedback" v-if="passwordE===false">
                Looks good!
                </div>
                </div>
                 <div class="form-group">
                    <label for="passwordInput2">Repeat Password</label>
                    <input type="password" class="form-control" id="passwordInput2" v-model="password2"
                     :class="{'is-invalid':password2E===true,
                     'is-valid':password2E===false}">  
                      <div class="invalid-feedback" v-if="password2E">
                      {{password2EM}}
                </div>
                 <div class="valid-feedback" v-if="password2E===false">
                Looks good!
                </div>
                </div>
                <button type="submit" class="btn btn-primary mt-2">Register</button>
            </form>
        </div>
     </div>
  </div>
</template>

<script>


export default {
  name: 'Login',
  data(){
      return {
          username: '',
          password: '',
          password2: '',
          usernameE:null,
          username2E:null,
          passwordE:null,
          usernameEM:null,
          username2EM:null,
          passwordEM:null,
      }
  },
 methods: {
     doRegister() {
      let access = true
        if(this.username.length < 5){
            access = false
            this.usernameE = true
            if(this.username.length == 0){
                this.usernameEM = "Username required"
            } else {

                this.usernameEM = "Username must be at least 5 charecters long."

            }
        }
        else {
            this.usernameE = false
            this.usernameEM = ''
        }
         if(this.password.length < 6){
             access = false
            this.passwordE = true
            if(this.password.length == 0){
                this.passwordEM = "Password required"
            } else {

                this.passwordEM = "Password must be at least 6 charecters long."

            }
        }
        else {
            this.passwordE = false
            this.passwordEM = ''
        }
          if(this.password2.length < 6){
             access = false
            this.password2E = true
            if(this.password2.length == 0){
                this.password2EM = "Repeat Password required"
            } else {

                this.password2EM = "Repeat Password must be at least 6 charecters long."

            }
        }
        else {
            this.password2E = false
            this.password2EM = ''
        }
         if(this.password != this.password2){
             access = false
            this.passwordE = true
            this.password2E = true
            this.passwordEM = " Password aren`t same"
          
        }
        else {
          if (!this.passwordEM && !this.password2EM) {
            this.passwordEM = ""
          }
        }
         if (access) {
             this.$store.commit("login",`${this.username}:${this.password}`)
             this.$router.push("/profile")
         }
     }
  }
}
</script>

<style scoped>
@media only screen and (max-width: 987px)  {
    .size {
    max-width: 45%;
}  

    }

</style>Register