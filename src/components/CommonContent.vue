<template>
	<div id="product" class="wrapper">
        <ul id="product-tags">
            <li>Best seller</li>
            <li>Popular</li>
            <li>New Arrivals</li>
        </ul>
        <div id="loading">
            <img src="../assets/img/loading.gif" alt="">
        </div>
        <ul id="product-list">
        	<product-list v-for="product in productList" :id='product.prod_id' :img='product.prod_img' :name='product.prod_name' :price='product.prod_price'></product-list>
        </ul>
        <div id="load-more" @click='loadDate'>
            加载更多...
        </div>
    </div>
</template>
<script>
	import ProductList from './ProductList'
	import Axios from 'axios'
	export default{
		data(){
			return{
				productList:[],
				page:1,
				isEnd:false
			}
		},
		components:{
			ProductList
		},
		created:function(){
			var _this=this;
			Axios.get('http://127.0.0.1/eshop/product/get_products',{
				params:{
					page:this.page
				}
			}).then((res)=>{
				this.productList = res.data.products;
			});		
		},
		methods:{
			loadDate:function(){
				if(this.isEnd){
						alert('没有数据啦♪(^∇^*)♪~\(≧▽≦)/~啦啦啦');
					}else{
						Axios.get('http://127.0.0.1/eshop/product/get_products',{
							params:{
								page:++this.page
							}
						}).then((res)=>{
							this.productList = this.productList.concat(res.data.products);
							this.isEnd = res.data.isEnd;
						});	
					}	
			}
		}
	}
</script>
<style>
	@import '../assets/css/bootstrap.css';
    @import '../assets/css/index.css';
    @import '../assets/css/style.css';
</style>