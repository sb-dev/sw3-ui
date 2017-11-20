<template>
  <div class="artworks padding-lg padding-v">
    <div class="container--row clearfix">
      <el-form :inline="true" :model="formInline" class="form-inline right">
        <el-form-item>
          <el-select v-model="formInline.region" placeholder="SORT BY:">
            <el-option label="Highest rated" value="Best match"></el-option>
            <el-option label="Price (high-low)" value="beijing"></el-option>
            <el-option label="Price (Low-high)" value="beijing"></el-option>
            <el-option label="Newest" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item>
          <el-select v-model="formInline.region" placeholder="DISPLAY:">
            <el-option label="50 per page" value="shanghai"></el-option>
            <el-option label="200 per page" value="beijing"></el-option>
          </el-select>
        </el-form-item>
      </el-form>
    </div>
    <div class="container--row">
      <el-row :gutter="10">
        <el-col :span="6" v-for="(item, index) in items" :key="item.index">
          <el-card :body-style="{ padding: '0px' }" class="item margin-xs">
            <img v-bind:src="item.image" class="image">
            <div class="padding-sm no-padding-top">
              <span class="sw-bold">Yummy hamburger</span> &middot; <span class="sm-text">by Mr.T</span>
              <br />
              <span class="sm-text">Athletic Kicks</span>
              <div class="bottom clearfix">
                <span class="sw-bold">£200</span>
                <span class="right">
                  <el-button type="text" class="button padding-sm padding-h no-padding-right"><i aria-hidden="true" class="fa fa-heart"></i></el-button>
                  <el-button type="text" class="button"><i aria-hidden="true" class="fa fa-shopping-basket"></i></el-button>
                </span>
              </div>
            </div>
          </el-card>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        align: 'center',
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
        ],
        isBusy: false,
        formInline: {
          user: '',
          region: ''
        }
      }
    },
    methods: {
      onSubmit () {
        console.log('submit!')
      }
    }
  }
</script>

<style>
  .item img{
    height: 141px;
  }

  .bottom {
    margin-top: 13px;
    line-height: 12px;
  }

  .button {
    padding: 0;
  }

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }

  .clearfix:after {
    clear: both
  }
</style>
