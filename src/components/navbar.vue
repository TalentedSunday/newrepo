<template>
    <div class="header">
        <div class="row">
            <div class="col-md-8">
                <nav class="navbar nabar-success">
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">Gallery</a></li>
                    <li><a href="#">Services</a></li>
                    <li><a href="#">About us</a></li>
                </ul>
                </nav>
            </div>
            <div class="col-md-4">
                <div id="search" class="mt-2">
                    <form @submit.prevent="search" class="form-inline float-right">
                        <input class="form-control" type="search" name="" id="" v-model="keyword" placeholder="Search products...">
                        <button class="btn search-button" type="submit"><span class="fa fa-search"></span></button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data: function(){
            return {
                keyword: ''
            }
        },
        methods: {
            search(){
                this.$emit('search', this.keyword);
            }
        },
    }
</script>