<template>
    <div class="pagina">
        <div class="card-container">
            <div class="title">
                <h1>Elderly Care :  Your smart partner for a healthy and conscious lifestyle</h1>
            </div>
            <div class="cards">
                <Card class="card">
                    <template #header>
                        <img alt="user header":src="products.length > 0 ? products[1].productImageUrl : ''" /> <!--//cambiar aqui-->
                    </template>
                    <template #title>{{ products.length > 0 ? products[1].productName : '' }}</template><!--//cambiar aqui-->
                    <template #subtitle>{{ products.length > 0 ? products[1].productPrice : '' }}</template><!--//cambiar aqui-->
                    <template #content>
                        <p class="m-0">
                            {{ products.length > 0 ? products[1].productDescription : '' }} <!--//cambiar aqui-->
                        </p>
                    </template>
                    <template #footer>
                        <div class="buttons">
                            <Button class="cart-button" icon="pi pi-shopping-cart" aria-label="Cart" @click="handleBuyClick"/>
                            <Button class="buy-button" icon="pi pi-angle-right" label="More Info" @click="handleCartClick"/>
                        </div>
                    </template>
                </Card>
                <Card class="card">
                    <template #header>
                        <img alt="user header":src="products.length > 0 ? products[1].productImageUrl : ''" /><!--//cambiar aqui-->
                    </template>
                    <template #title>{{ products.length > 0 ? products[1].productName : '' }}</template><!--//cambiar aqui-->
                    <template #subtitle>{{ products.length > 0 ? products[1].productPrice : '' }}</template><!--//cambiar aqui-->
                    <template #content>
                        <p class="m-0">
                            {{ products.length > 0 ? products[1].productDescription : '' }}<!--//cambiar aqui-->
                        </p>
                    </template>
                    <template #footer>
                        <div class="buttons">
                            <Button class="cart-button" icon="pi pi-shopping-cart" aria-label="Cart" @click="handleBuyClick" />
                            <Button class="buy-button" icon="pi pi-angle-right" label="More Info" @click="handleCartClick" />
                        </div>
                    </template>
                </Card>
            </div>
        </div>

        <div class="image-container">
            <img alt="Abuelos" src="../assets/ProductsImage.png" />
        </div>
    </div>
</template>

<script>
import axios from 'axios';
    export default {
        data() {
            return {
                products: []
            }
        },
        methods: {
            handleCartClick() {
                this.$router.push('/infoproducts');
            },
            handleBuyClick(){
                this.$router.push('/payment-methods');
            }
        },
        mounted() {

            axios
                .get('https://oneupbackend.zeabur.app/api/oneup/v1/products')
                .then(response => {
                    this.products = response.data;
                    
                })
                .catch(error => {
                  console.log(error);
                });
        }
    }
</script>


<style scoped>

    .pagina {
        display: flex;
        justify-content: space-between;
        width: 100%;
        height: 100%;
        
    }
    .title{
        text-align: center;
        margin-left: 5%;
        margin-top: 10%;
        margin-bottom: -5%;
        
    }
    .card-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
       
        
    }
    .cards {
        display: flex;
        flex: 0 0 70%;
        padding-top: 10%;
        justify-content: center;
       
        
    }
    .card {
        align-self: flex-start;
        margin-right: 50px;
        width: 400px;
        
    }
    .card img{
        width: 100%;
        padding: 20px;
       
    }
    .buttons {
        display: flex;
    }
    .cart-button {
        margin-right: 30px;
    }
    .buy-button {
        width: 300px;
        text-align: center;
    }
    .image-container {
        
        flex: 0 0 30%;
        display: flex;
        
    }
    .image-container img {
        width: 100%;
        height: 100vh;
        object-fit: cover;
        
    }
</style>