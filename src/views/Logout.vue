<template>
  <div class="Login">
    <h1>Logout</h1>
    <button class="btn btn-danger" @click="doLogout">Logout</button>
  </div>
</template>

<script>


export default {
  name: 'Lougout',
 methods: {
     doLogout() {
         this.$store.commit("logout")
         this.$router.push("/login")
     }
 }
}
</script>
