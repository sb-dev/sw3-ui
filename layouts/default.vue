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

    <el-dialog :visible.sync="showProductDialog" :before-close="clearHash">
      <el-popover
        ref="popover5"
        placement="top"
        width="280"
        v-model="showSizePopover">
        <el-row :gutter="5">
          <el-col :span="12"><el-button class="size">UK 7.5</el-button></el-col>
          <el-col :span="12"><el-button class="size">UK 8.5</el-button></el-col>
          <el-col :span="12"><el-button class="size">UK 10.5</el-button></el-col>
        </el-row>
      </el-popover>
      <el-row type="flex">
        <el-col :span="14">
          <el-carousel arrow="always" :autoplay="false" indicator-position="none">
            <el-carousel-item v-for="(item, index) in items" :key="item.index">
              <img v-bind:src="item.image" class="image clickable">
            </el-carousel-item>
          </el-carousel>
        </el-col>
        <el-col :span="10">
          <div class="content">
            <div class="content__inner-container">
              <div class="padding-sm no-padding-top">
                <h2>Yummy hamburger</h2>
                <span>Athletic Kicks</span>
                <h3>by Mr.T</h3>
                <span class="sw-bold">
                  <el-rate v-model="value5" disabled show-text text-color="#ff9900" text-template="({value})"></el-rate>
                </span>
                <h3 class="margin-sm margin-top">£200</h3>
                <div class="size"><el-button type="text" v-popover:popover5>Choose Size <i class="fa fa-caret-down" aria-hidden="true"></i></el-button></div>
                <el-row :gutter="20">
                  <el-col :span="24" class="margin-sm margin-v">
                    <el-button type="primary" size="large">Add to basket</el-button>
                  </el-col>
                  <el-col :span="12" class="margin-sm margin-v">
                    <el-button>View full details</el-button>
                  </el-col>
                  <el-col :span="12" class="margin-sm margin-v">
                    <el-button><i aria-hidden="true" class="fa fa-heart"></i></el-button>
                  </el-col>
                </el-row>
              </div>
            </div>
          </div>
        </el-col>
      </el-row>
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

  export default {
    components: {
      SwHeader,
      SwBasket,
      SwJoin
    },
    data () {
      return {
        value5: 127,
        showSidenav: false,
        showBasketDialog: false,
        showUserDialog: false,
        showProductDialog: false,
        showSizePopover: false,
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
        window.addEventListener('hashchange', this.processHash.bind(this))
      }
    },
    methods: {
      processHash () {
        if (location.hash.includes('quick-view')) {
          this.showProductDialog = true
        }
      },
      clearHash (done) {
        location.hash = ''
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
</style>
