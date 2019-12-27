<template>
<div class="content-section">
    <div class="row">
        <div class="col-md-4 col-sm-6" v-for="(item, index) in items" :key="index">
            <div class="product-grid4">
                <div class="product-image4">
                    <a href="#">
                        <img class="pic-1" :src="item.image">
                        <img class="pic-2" :src="item.image">
                    </a>
                    <ul class="social">
                        <li><a href="#" data-tip="Quick View"><i class="fa fa-eye"></i></a></li>
                        <li><a href="#" data-tip="Add to Wishlist"><i class="fa fa-shopping-bag"></i></a></li>
                        <li><a href="#" data-tip="Add to Cart"><i class="fa fa-shopping-cart"></i></a></li>
                    </ul>
                    <span class="product-new-label">New</span>
                    <span class="product-discount-label">-10%</span>
                </div>
                <div class="product-content">
                    <h3 class="title"><a href="#">{{item.title}}</a></h3>
                    <div class="price">${{item.price}}
                        <span>$16.00</span>
                    </div>
                    <a class="add-to-cart" href="" @click.prevent="addItemToCart(item, counter +=1)">ADD TO CART</a>
                </div>
            </div>
        </div>
    </div>
</div>
</template>
<script>
    export default {
        props: ['items'],
        data: function(){
            return {
                counter: 0
            }
        },
        methods: {
            addItemToCart(item, counter){
                this.$emit('addedItem', item, counter);
            }
        },
    }
</script>