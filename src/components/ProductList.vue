<template>
	<li class="product-item">
        <router-link :to="'/detail/'+id"><img :src="'http://127.0.0.1/eshop/'+img" alt=""></router-link>
        <div class="product-info">
            <h3 class="product-name">{{name}}</h3>
            <strong class="product-price">${{price}}</strong>
            <input type="text" class="quantity" v-model="quantity">
            <button class="btn-add-cart" @click='add'>Add</button>
        </div>
    </li>
</template>
<script>
	import Axios from 'axios'
	export default{
		props:['id','img','name','price','logined'],
		data(){
			return{
				quantity:1
			}
		},
		methods:{
			add:function(){
				this.check_login();
			},
			add_cart:function(){
				Axios.get('http://127.0.0.1/eshop/product/add_cart',{
					params:{
						quantity:this.quantity,
						id:this.id
					}
				}).then((res)=>{

				});
			},
			check_login:function(){
				if(this.logined){
					this.add_cart();
				}else{
					this.$emit('showDialog',"true"); 
				}
				// Axios.get('http://127.0.0.1/eshop/welcome/check_login').
				// then((res)=>{
				// 		if(res.data=='login'){
				// 			this.add_cart();
				// 		}else{
				// 			//弹出登录框
				// 			this.$emit('showDialog',"true");
				// 		}
				// 	});
			}
		}
	}
</script>
<style>

</style>