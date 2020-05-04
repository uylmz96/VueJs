<template>
  <div class="product">
    <strong> Title : {{product.title}} </strong>
    <p>Açıklama : {{product.desc}} </p>
    <strong>Fiyat : {{product.price}} |  Adet : {{product.count}} </strong>
    <br><br>
    
    <button @click="add2Cart(product)"> Sepete Ekle</button>
  </div>
</template>

<script>
export default {
    //Parentdan gelen nesneyi prop ile alıp kullanabiliriz.
    props:["product"],
    data() {
        return {
            
        }
    },
    methods: {
        add2Cart(product){
            //Component den parent'a nesne göndermek için $emit ile fırlatılır.
            this.$emit("add2Cart",product)
        }
    },
};
</script>





<style>
.product {
  border: 2px dashed black;
  padding: 2px;
  width: 300px;
  margin-bottom: 5px;
}
.product:hover{
    border: 2px solid green;
    transition: all 2;
    background-color: lime;
}
</style>