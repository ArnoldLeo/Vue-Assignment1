<template>
  <div class="container">
    <h1>My Shopping cart!!</h1>
    <div v-for="product in products" :key="product.id" class="box">
      <div class="image">
        <img class="img" :src="product.srcImg" />
      </div>
      <div class="price">
        <p>{{ product.name }}</p>
        <ul v-html="product.description"></ul>
        <p style="font-weight: 600">&#8377;{{ product.price }}</p>
        <button @click="product.status = !product.status">Add item</button>
        <div v-show="product.status">
          <div class="quantity-toggle">
            <button @click="updateCart(product, 'subtract')">&mdash;</button>
            <span class="cart__quantity">{{ product.quantity }}</span>
            <button @click="updateCart(product, 'add')">&#xff0b;</button>
          </div>
        </div>
      </div>
    </div>
    {{totalPrice()}}
    <div class="nav__cart">
      <button class="cartBtn" @click="showCart = !showCart">Cart</button>
      <span class="total-quantity">{{ totalQuantity }}</span>
      <div v-if="showCart && finalPrice>0" class="cart-dropdown">
        <ol class="cart-dropdown__list">
          <li v-for="product in cart" :key="product.id">
            {{ product.name }} x {{ product.quantity }}=&#8377;{{product.total }}<button class="remove" @click="updateCart(product, 'delete')">Remove</button>
          </li>
        </ol>
        Total=&#8377;{{finalPrice}};
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      products: [
        {
          id: 1,
          name: "Apple iPhone13(Blue 512GB)",
          srcImg:
            "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRjaLW7bhQD2wBNF1R21jhrsEyMNGl-Qon9O9i-mlHAyqW38lwHnWn6GuK65woeSWhm0YRbTHnU&usqp=CAc",
          description:
            "<li>512 GB ROM</li><li>15.49 cm (6.1 inch) Super Retina XDR Display</li><li>12MP + 12MP | 12MP Front Camera</li><li>A15 Bionic Chip Processo</li>",
          quantity: 0,
          price: 110000,
          total:0,
          status: false,
        },
        {
          id: 2,
          name: "SAMSUNG Galaxy Z Flip3 5G (Cream, 256 GB) (8 GB RAM)",
          srcImg:
            "https://rukminim1.flixcart.com/image/312/312/ksnjp8w0/mobile/w/u/8/galaxy-z-flip3-5g-sm-f711bzeeinu-samsung-original-imag662adrayy6cg.jpeg?q=70",
          description:
            "<li>8 GB RAM | 256 GB ROM</li><li>17.02 cm (6.7 inch) Full HD+ Display</li><li>12MP + 12MP | 10MP Front Camera</li><li>3300 mAh Lithium-ion Battery</li><li>Qualcomm Snapdragon 888 Octa-Core Processor</li>",
          quantity: 0,
          price:90000,
          status: false,
          total:0,
        },
        {
          id: 3,
          name: "Mi 10 (Coral Green, 256 GB) (8 GB RAM)",
          srcImg:
            "https://static.digit.in/default/c4062f46aa76aa44a95c5ee690c5ad8dc07485e9.jpeg?tr=n-product_detail_leader_thumb",
          description:
            "<li>8 GB RAM | 256 GB ROM</li><li>16.94 cm (6.67 inch) Display</li><li>108MP + 13MP + 2MP + 2MP | 20MP Front Camera</li><li>4780 mAh Battery</li><li>Qualcomm Snapdragon 865 Processor</li><li>Full HD+ 3D Curved E3 AMOLED HDR 10+ Display</li><li>30 W Charging</li>",
          quantity: 0,
          price: 55000,
          status: false,
          total:0,
        },
      ],
      showCart: false,
    };
  },
  computed: {
    cart() {
      return this.products.filter((product) => product.quantity > 0);
    },
    totalQuantity() {
      return this.products.reduce(
        (total, product) => total + product.quantity,
        0
      );
    },
    finalPrice() {
      return this.products.reduce(
        (total, product) => total + product.total,
        0
      );
    },
  },
  methods: {
    updateCart(product, updateType) {
      for (let i = 0; i < this.products.length; i++) {
        if (this.products[i].id === product.id) {
          if (updateType === "subtract") {
            if (this.products[i].quantity !== 0) {
              this.products[i].quantity--;
            }
          } else if (updateType === "add") {
            this.products[i].quantity++;
          }
            else{
              this.products[i].quantity=0;
            }
          break;
        }
      }
    },
    totalPrice(){
      for (let i = 0; i < this.products.length; i++){
        this.products[i].total=(this.products[i].quantity*this.products[i].price);
      }
      // console.log(this.products)
    }
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  background-color: #2c3e50;
  width: 900px;
  margin: 10px auto;
  justify-content: center;
}
h1 {
  color: aliceblue;
  text-align: center;
  margin-bottom: 5px;
}
.box {
  width: 85%;
  display: flex;
  justify-content: center;
  background-color: white;
  margin: 10px auto;
  border: tomato 2px solid;
}
.image {
  border-right: 2px solid brown;
  margin: 10px;
}
.img {
  margin: 10px;
  padding: 10px;
  width: 300px;
  height: 300px;
  object-fit: none;
  border: rgb(207, 188, 188) 2px solid;
}
.price {
  margin: 10px 0 10px 50px;
  padding: 10px;
  align-items: center;
}
p {
  font-size: 25px;
  font-style: bold;
}
ul {
  margin: 10px;
}
li {
  margin-left: 20px;
  line-height: 25px;
}
button {
  margin: 10px 0;
  padding: 10px;
  cursor: pointer;
  font-size: 15px;
  font-weight: bold;
  background-color: crimson;
  border-style: none;
  color: white;
  border-radius: 5px;
}
button:hover {
  background-color: orange;
}
.quantity-toggle {
  display: flex;
  align-content: center;
  align-items: center;
}
input {
  height: 40px;
  text-align: center;
  width: 50px;
  border: 2px solid grey(160, 153, 153);
  border-radius: 4px;
}

.nav__cart {
  margin: 0 auto;
  text-align: center;
}
.cartBtn {
  margin: 10px auto;
  padding: 10px 20px;
}
.cart-dropdown {
  background: white;
  border: 1px solid lightgray;
  border-radius: 10px;
  box-shadow: 0 0 2px rgba(0, 0, 0, 0.2);
  color: #333;
  font-size: 1.3rem;
  overflow: auto;
  padding: 0 1rem;
  width: 200px;
  margin: 0 auto;
}
.cart-dropdown__list {
 margin:10px;
}
.cart__quantity {
  border: 2px solid grey;
  padding: 20px;
  border-radius: 100%;
}
.total-quantity {
  text-align: center;
  color: aliceblue;
  background: lightblue;
  border-radius: 50%;
  font-weight: bold;
  padding: 8px;
  top: -18px;
  position: relative;
  left: -20px;
}
ol{
  text-decoration: peru;
}
</style>
