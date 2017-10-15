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
        <ul class="nav__section--left main-nav hidden-md-down">
          <li class="sw-bold"><nuxt-link to="/discover">Discover</nuxt-link></li>
          <li class="sw-bold"><nuxt-link to="/">Artists</nuxt-link></li>
          <li class="sw-bold"><nuxt-link to="/">Artworks</nuxt-link></li>
        </ul>
        <ul class="nav__section--right main-nav">
          <li class="hidden-sm-down" v-popover:basket-popper>
            <i class="fa fa-shopping-basket" aria-hidden="true"></i>
          </li>
          <li class="hidden-md-up" v-on:click="openDialog"><i class="fa fa-shopping-basket fa-2x" aria-hidden="true"></i></li>
          <li class="sw-bold no-padding hidden-sm-down">Sign in</li>
          <li class="padding-sm padding-h hidden-sm-down">or</li>
          <li class="sw-bold no-padding hidden-sm-down">Join</li>
          <li class="hidden-sm-down"><nuxt-link to="/discover">About</nuxt-link></li>
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
      openDialog () {
        this.$emit('dialog')
      }
    }
  }
</script>

<style>
  header {
    background-color: #f5f4f2;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 100;
    position: relative;
  }
</style>
