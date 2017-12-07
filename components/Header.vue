<template>
  <header>
    <el-popover
      ref="basket-popper"
      placement="bottom"
      width="298"
      trigger="click"
      popper-class="basket-popper">
      <SwBasket></SwBasket>
    </el-popover>

    <nav class="container--row nav nav--top-bar">
      <section class="nav__inner-container">
        <ul class="nav__section--left title-nav">
          <li class="hidden-md-up clickable" v-on:click="openSidenav"><i class="fa fa-bars fa-2x" aria-hidden="true"></i></li>
          <li class="name"><nuxt-link to="/"><img src="~/assets/images/logo.png"></nuxt-link></li>
        </ul>
        <ul class="nav__section--left main-nav hidden-sm-down">
          <li class="sw-bold"><nuxt-link to="/about/">About</nuxt-link></li>
          <li class="sw-bold"><nuxt-link to="/artists/">Artists</nuxt-link></li>
          <li class="sw-bold"><nuxt-link to="/shop/all-shoes/">Artworks</nuxt-link></li>
        </ul>
        <ul class="nav__section--right main-nav">
          <li class="hidden-sm-down" v-popover:basket-popper>
            <i class="fa fa-shopping-basket" aria-hidden="true"></i>
          </li>
          <li class="hidden-md-up" v-on:click="openBasketDialog"><i class="fa fa-shopping-basket fa-2x" aria-hidden="true"></i></li>
          <li class="sw-bold no-padding-left hidden-sm-down">Sign in</li>
          <li class="padding-sm padding-h hidden-sm-down">or</li>
          <li class="sw-bold no-padding-right hidden-sm-down" v-on:click="openUserDialog">Join</li>
          <li class="hidden-sm-down">
            <el-input
              placeholder="Search"
              icon="search">
            </el-input>
          </li>
        </ul>
      </section>
    </nav>
  </header>
</template>

<script>
  import SwBasket from '~/components/Basket.vue'

  export default {
    components: {
      SwBasket
    },
    methods: {
      openSidenav () {
        this.$emit('sidenav')
      },
      openBasketDialog () {
        this.$emit('basketDialog')
      },
      openUserDialog () {
        this.$emit('userDialog')
      }
    }
  }
</script>

<style>
  header {
    background-color: white;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 100;
    position: relative;
    border-bottom: 3px #B52C24 solid;
  }
</style>
