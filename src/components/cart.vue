<template>
<div class="shopping-cart">
    <div class="shopping-cart-header">
        <i class="fa fa-shopping-cart cart-icon"></i><span class="badge">Item {{total}}</span>
        <div class="shopping-cart-total">
            <span class="lighter-text">Total:</span>
            <span class="main-color-text">${{totalCartVal}}</span>
        </div>
        </div> <!--end shopping-cart-header -->

        <ul class="shopping-cart-items">
        <li class="clearfix" v-for="(item, index) in cartItemAdded" :key="index">
            <img :src="item.image" v-bind:alt="item.title" />
            <span class="item-name">{{item.title}}</span>
            <span class="item-price">${{item.price}}</span>
            <span class="item-quantity">Quantity: 01</span>
            <span class="item-quantity fa fa-close remove-item" v-on:click="removeItemCart(index)"></span>
        </li>
        </ul>

        <a href="#" class="button">Checkout</a>
    </div> <!--end shopping-cart -->
</template>

<script>
    export default {
        props: ['cartItemAdded', 'total'],
        computed: {
            totalCartVal(){
                var totalBal=0;
                this.cartItemAdded.forEach(item=> {
                    totalBal += parseFloat(item.price);
                });
                return totalBal;
            }
        },
        methods: {
            removeItemCart(index){
                this.$emit('removeitem', index);
            }
        },
        
    }
</script>