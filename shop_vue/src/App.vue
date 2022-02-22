<template>
<div id="wrapper">
  <nav class="navbar is-light">
  <div class="navbar-brand">
    <router-link to="/" class="navbar-item"><strong>Shop</strong></router-link>
  <a class="navbar-burger" aria-label="menu" aria-expanded="false" data-target="navbar-menu" @click="showMobileMenu = !showMobileMenu">
  <span aria-hidden="true"></span>
  <span aria-hidden="true"></span>
  <span aria-hidden="true"></span>
  </a>
  </div>
<div class="navbar-menu" id="navbar-menu" v-bind:class="{'is-active': showMobileMenu }">
  <div class="navbar-end">
    <router-link to="/tops" class="navbar-item">Tops</router-link>
    <router-link to="/bottoms" class="navbar-item">Bottoms</router-link>
<div class="navbar-item">
  <div class="buttons">
    <router-link to="/log-in" class="button is-light">Log in</router-link>
    <router-link to="/cart" class="button is-dark">
    <span class="icon"><i class="fas fa-shopping-cart"></i></span>
  <span>Cart ({{ cartTotalLength }})</span>
</router-link>
  </div>
  </div> 
  </div>
</div>
  </nav>
  <section class="section">
    <router-view/>
  </section>
  <footer class="footer">
    <p class="has-text-centered">Copyright (c) 2022</p>
  </footer>
</div>
</template>
<script>
export default {
  data(){
    return{
      showMobileMenu: false,
      cart: {
        items: []
      }
    }
  },
  beforeCreate(){
    this.$store.commit('initializeStore')
  },
  mounted(){
    this.cart = this.$store.state.cart
  },
  computed: {
    cartTotalLength(){
      let totalLength = 0
      for (let i = 0; i < this.cart.items.length; i++){
        totalLength += this.cart.items[i].quantity
      }
      return totalLength
    }
  }
}
</script>
<style lang="scss">
@charset "utf-8";
@import "../node_modules/bulma/bulma.sass";
</style>
