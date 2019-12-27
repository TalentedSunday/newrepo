<template>
  <div id="app">
    <header id="header-section">
      <div class="container-fluid">
        <!-- navbar -->
          <navbar @search="searchProduct"></navbar>
      </div>
    </header>

    <main class="main">
        <div class="container-fluid">
          <div class="site-content">
                <div class="row">
                  <div class="col-md-9">
                    <!-- product -->
                    <products :items="items" @addedItem="getCartAddedItem"></products>
                  </div>
                  <div class="col-md-3">
                    <div class="sidebar-section">
                      <!-- shopping cart-->
                        <cart :cartItemAdded="cartItem" :total="cartCounter" @removeitem="removeItemCart"></cart>
                    </div>
                  </div>
                </div>
            </div>
        </div>
    </main>
    
  </div>
</template>

<script>
window.$ = window.jQuery = require('jquery');
import 'bootstrap'
import bootstrap from '../node_modules/bootstrap/dist/css/bootstrap.min.css'
import fontAwesome from '../node_modules/font-awesome/css/font-awesome.min.css'
import navbar from './components/navbar'
import products from './components/products'
import cart from './components/cart'
import data from './assets/js/product-data.js'

export default {
  name: 'App',
  components: {
    navbar,
    products,
    cart
  },
  data(){
    return {
      items: [],
      cartItem: [],
      cartCounter: 0
    }
  },
  mounted(){
    this.items = data;
  },
  methods: {
    getCartAddedItem(item, counter){
      this.cartItem.push(item);
      this.cartCounter = counter;
    },
    removeItemCart(index){
      this.cartItem.splice(index, 1);
    },
    searchProduct(keyword){
      this.items = data.filter(item=> {
      return item.title.toLowerCase().indexOf(keyword.toLowerCase()) !== -1;
      });
    }
  },
}
</script>


