<template>
  <div class="product">
    <el-popover
      ref="size-popover"
      placement="bottom"
      width="280"
      v-model="showSizePopover">
      <el-row :gutter="5">
        <el-col :span="24">
          <el-switch
            v-model="size"
            on-color="#6BC89E"
            off-color="#6BC89E"
            on-value="UK"
            on-text="UK"
            off-value="EU"
            off-text="EU"
            class="size-switch">
          </el-switch>
        </el-col>
        <el-col :span="12"><el-button class="size">UK 6</el-button></el-col>
        <el-col :span="12"><el-button class="size" :disabled="true">UK 6.5</el-button></el-col>
        <el-col :span="12"><el-button class="size">UK 7</el-button></el-col>
        <el-col :span="12"><el-button class="size">UK 7.5</el-button></el-col>
        <el-col :span="12"><el-button class="size">UK 8</el-button></el-col>
        <el-col :span="12"><el-button class="size">UK 8.5</el-button></el-col>
        <el-col :span="12"><el-button class="size">UK 9</el-button></el-col>
        <el-col :span="12"><el-button class="size">UK 9.5</el-button></el-col>
        <el-col :span="12"><el-button class="size">UK 10</el-button></el-col>
        <el-col :span="12"><el-button class="size">UK 10.5</el-button></el-col>
        <el-col :span="12"><el-button class="size" :disabled="true">UK 11</el-button></el-col>
        <el-col :span="12"><el-button class="size">UK 11.5</el-button></el-col>
        <el-col :span="12"><el-button class="size">UK 12</el-button></el-col>
        <el-col :span="12"><el-button class="size" :disabled="true">UK 13</el-button></el-col>
        <el-col :span="12"><el-button class="size" :disabled="true">UK 14</el-button></el-col>
        <el-col :span="12"><el-button class="size" :disabled="true">UK 15</el-button></el-col>
      </el-row>
    </el-popover>
    <el-row :gutter="20">
      <el-col :span="gallerySize">
        <el-carousel arrow="always" :autoplay="false" indicator-position="none" v-if="!fullView">
          <el-carousel-item v-for="(item, index) in items" :key="item.index">
            <img v-bind:src="item.image" class="product-image clickable">
          </el-carousel-item>
        </el-carousel>

        <el-row :gutter="20" v-if="fullView">
          <el-col :span="12" v-for="(item, index) in items" :key="item.index">
            <img v-bind:src="item.image" class="product-image clickable margin-sm margin-v">
          </el-col>
        </el-row>
      </el-col>
      <el-col :span="productDetailsSize" v-bind:class="{ 'margin-sm margin-v': fullView }">
        <div class="content">
          <div class="content__inner-container">
            <div class="padding-sm no-padding-top">
              <h2>Yummy hamburger</h2>
              <span>Athletic Kicks</span>&nbsp;&middot;&nbsp;<span class="price">£200</span>
              <h3>by Mr.T</h3>
              <span class="sw-bold">
                  <el-rate v-model="value5" disabled show-text text-color="#ff9900" text-template="({value})"></el-rate>
                </span>
              <div class="size">
                <el-button type="text" v-if="!fullView" v-popover:size-popover>Choose Size <i class="fa fa-caret-down" aria-hidden="true"></i></el-button>
                <el-switch
                  v-model="size"
                  on-color="#6BC89E"
                  off-color="#6BC89E"
                  on-value="UK"
                  on-text="UK"
                  off-value="EU"
                  off-text="EU"
                  class="margin-sm margin-v" v-if="fullView">
                </el-switch>
                <el-button type="text" class="right">Size guide</el-button>
              </div>
              <el-row :gutter="20" v-if="!fullView">
                <el-col :span="24" class="margin-sm margin-v">
                  <el-button type="primary" size="large">Add to basket</el-button>
                </el-col>
                <el-col :span="12" class="margin-sm margin-v">
                  <el-button v-on:click="viewFullDetails">View full details</el-button>
                </el-col>
                <el-col :span="12" class="margin-sm margin-v">
                  <el-button><i aria-hidden="true" class="fa fa-heart"></i></el-button>
                </el-col>
              </el-row>
              <el-row :gutter="10" v-if="fullView">
                <el-col :span="24">
                  <el-row :gutter="5">
                    <el-col :span="12"><el-button class="size">UK 6</el-button></el-col>
                    <el-col :span="12"><el-button class="size" :disabled="true">UK 6.5</el-button></el-col>
                    <el-col :span="12"><el-button class="size">UK 7</el-button></el-col>
                    <el-col :span="12"><el-button class="size">UK 7.5</el-button></el-col>
                    <el-col :span="12"><el-button class="size">UK 8</el-button></el-col>
                    <el-col :span="12"><el-button class="size">UK 8.5</el-button></el-col>
                    <el-col :span="12"><el-button class="size">UK 9</el-button></el-col>
                    <el-col :span="12"><el-button class="size">UK 9.5</el-button></el-col>
                    <el-col :span="12"><el-button class="size">UK 10</el-button></el-col>
                    <el-col :span="12"><el-button class="size">UK 10.5</el-button></el-col>
                    <el-col :span="12"><el-button class="size" :disabled="true">UK 11</el-button></el-col>
                    <el-col :span="12"><el-button class="size">UK 11.5</el-button></el-col>
                    <el-col :span="12"><el-button class="size">UK 12</el-button></el-col>
                    <el-col :span="12"><el-button class="size" :disabled="true">UK 13</el-button></el-col>
                    <el-col :span="12"><el-button class="size" :disabled="true">UK 14</el-button></el-col>
                    <el-col :span="12"><el-button class="size" :disabled="true">UK 15</el-button></el-col>
                  </el-row>
                </el-col>
                <el-col :span="18" class="margin-sm margin-v">
                  <el-button type="primary" size="large">Add to basket</el-button>
                </el-col>
                <el-col :span="6" class="margin-sm margin-v">
                  <el-button size="large"><i aria-hidden="true" class="fa fa-heart"></i></el-button>
                </el-col>
              </el-row>
            </div>
          </div>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  export default {
    fetch ({ store, params }) {
      console.log('params', params)
    },
    data () {
      return {
        showSizePopover: false,
        size: 'EU',
        value5: 127,
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
    props: ['fullView'],
    computed: {
      gallerySize () {
        if (!this.fullView) {
          return 14
        } else {
          return 16
        }
      },
      productDetailsSize () {
        if (!this.fullView) {
          return 10
        } else {
          return 8
        }
      }
    },
    methods: {
      viewFullDetails () {
        this.$router.push('/product/Yummy-Hamburger')
        window.trigger('hashchange')
      }
    }
  }
</script>

<style>
  .product-image{
    width: 100%;
  }

  .content {
    display: table;
    height: 100%;
    width: 100%;
  }

  .content__inner-container {
    display: table-cell;
    vertical-align: top;
  }

  .content .el-button:not(.el-button--text) {
    width: 100%;
  }

  .size {
    width: 100%;
    margin-bottom: 0.312rem;
  }
</style>
