<template>
	<div id="product">
		<common-header></common-header>
		<ul>
			<li v-for='product in productList'>
				<div>product-name:{{product.prod_name}}</div>
				<div>product-price:{{product.prod_price}}</div>
			</li>
		</ul>
	</div>
</template>
<script>
import CommonHeader from './CommonHeader'	import Axios from 'axios'
	export default{
		data(){
			return{
				productList:''
			}
		},
		mounted:function(){
			Axios.get('http://127.0.0.1/eshop/product/get_cart_list/')
			.then((res)=>{
					this.productList = res.data;
				});		
		},
		components:{
			CommonHeader
		}
	}
</script>
<style>

</style>