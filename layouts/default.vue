<template>
  <div v-bind:class="{ 'page--sidenav-opened': showSidenav }" class="page-wrapper">
    <el-dialog
      title="Your Basket"
      custom-class="dialog"
      :visible.sync="showBasketDialog"
      size="small">
      <SwBasket></SwBasket>
    </el-dialog>

    <el-dialog
      title="Join"
      custom-class="dialog"
      :visible.sync="showUserDialog"
      size="small">
      <SwJoin></SwJoin>
    </el-dialog>

    <el-dialog :visible.sync="showProductDialog" :before-close="clearHash" custom-class="product quick-view">
      <SwProduct v-on:productDialog="closeProductDialog"></SwProduct>
    </el-dialog>

    <div class="sidenav"></div>
    <div class="overlay" v-on:click="showSidenav = false" v-bind:class="{ 'overlay--sidenav-opened': showSidenav }"></div>
    <div class="page">
      <SwHeader v-on:sidenav="openSidenav" v-on:basketDialog="openBasketDialog"></SwHeader>
      <nuxt/>
    </div>
  </div>
</template>

<script>
  import SwHeader from '~/components/Header.vue'
  import SwBasket from '~/components/Basket.vue'
  import SwJoin from '~/components/Join.vue'
  import SwProduct from '~/components/Product.vue'

  export default {
    components: {
      SwHeader,
      SwBasket,
      SwJoin,
      SwProduct
    },
    head: {
      bodyAttrs: {
        class: 'sw'
      }
    },
    data () {
      return {
        showSidenav: false,
        showBasketDialog: false,
        showUserDialog: false,
        showProductDialog: false,
        items: [
          {
            index: 1,
            image: '/056A7345.jpg',
            height: 141,
            width: 257
          },
          {
            index: 2,
            image: '/056A7345.jpg',
            height: 141,
            width: 257
          },
          {
            index: 3,
            image: '/056A7345.jpg',
            height: 141,
            width: 257
          },
          {
            index: 4,
            image: '/056A7345.jpg',
            height: 141,
            width: 257
          },
          {
            index: 5,
            image: '/056A7345.jpg',
            height: 141,
            width: 257
          },
          {
            index: 6,
            image: '/056A7345.jpg',
            height: 141,
            width: 257
          }
        ]
      }
    },
    mounted: function () {
      if (typeof window !== 'undefined') {
        this.processHash()
        window.addEventListener('hashchange', this.processHash.bind(this), false)
      }
    },
    methods: {
      processHash () {
        if (location.hash.includes('quick-view')) {
          this.showProductDialog = true
        } else {
          this.showProductDialog = false
        }
      },
      clearHash (done) {
        location.hash = '#'
        done()
      },
      openSidenav () {
        this.showSidenav = true
      },
      openBasketDialog () {
        this.showBasketDialog = true
      },
      openUserDialog () {
        this.showUserDialog = true
      },
      closeProductDialog () {
        this.showProductDialog = false
      }
    }
  }
</script>

<style src="element-ui/lib/theme-default/index.css"></style>
<style>
  @media (min-width: 64em) {
    .container--row {
      margin: 0 auto;
      max-width: 73.125rem;
      width: 100%;
      padding: 0 0.9375rem
    }
  }

  .page-wrapper {
    position: relative;
    overflow: hidden;
    width: 100%;
  }

  .page--sidenav-opened .sidenav {
    width: 250px;
  }

  .page--sidenav-opened .page {
    margin-left: 250px;
  }

  .page--sidenav-opened .overlay {
    background-color: rgba(0,0,0,0.4);
    transition: background-color 1s;
  }

  .overlay {
    position:fixed;
    left: 0;
    right: 0;
    top:0;
    bottom: 0;
    background-color: transparent;
    z-index: 1000;
    display: none;
    transition: background-color 1s ease;
  }

  .overlay--sidenav-opened {
    display: block;
  }

  .sidenav {
    height: 100%;
    width: 0;
    position: fixed;
    z-index: 1001;
    top: 0;
    left: 0;
    background-color: #324157;
    overflow-x: hidden; /* Disable horizontal scroll */
    transition: 0.5s;
  }

  .page {
    position: relative;
    transition: margin-left .5s;
    width: 100%;
  }

  .right {
    float: right;
  }

  .size-switch {
    width: 58px;
    margin: 4px auto;
    display: block;
  }
</style>
