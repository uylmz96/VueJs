<template>
  <div class="container">
    <!-- <MyMyCompMainContainer /> -->
    <div class="cart">
      <h3>Sepet</h3>
      <ul> 
        <li  v-for="(cartItem,index) in cartItems" :key="index">
            {{cartItem}}
        </li>
      </ul>
      <p v-if="cartItems.length==0">Sepetiniz Boş</p>
    </div>
    <!-- Componente nesne göndermek için :product="item" -->
    <!-- Component den dönen $event i yakalamak için  @add2Cart="cartItems.push($event)"-->
    <product @add2Cart="cartItems.push($event)" :product="item" v-for="item in productList" :key="item.id" />  
  </div>
</template>

<script>
// import MainContainer from "@/components/MainContainer";
import Product from "@/components/Product";
export default {
  components: {
    //Componentler 2 şekilde kullanılabilir.
    // MyCompMainContainer: MainContainer, 
    Product  
  },
  data() {
    return {
      productList: [
        {
          id: 1,
          title: "Macbook Pro",
          price: 10000,
          count: 10,
          desc: "Açıklama 1"
        },
        {
          id: 2,
          title: "Iphone",
          price: 1000,
          count: 100,
          desc: "Açıklama 2"
        },
        {
          id: 3,
          title: "Keyboard",
          price: 100,
          count: 1000,
          desc: "Açıklama 3"
        }
      ],
      cartItems : []
    };
  }
};
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.cart{
  margin-bottom: 50px;
}
</style>

