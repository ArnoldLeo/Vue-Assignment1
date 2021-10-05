<template>
  <div class="container">
    <h1>My Shopping cart!!</h1>
    <div class="box box1">
      <div class="image">
        <img
          src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRjaLW7bhQD2wBNF1R21jhrsEyMNGl-Qon9O9i-mlHAyqW38lwHnWn6GuK65woeSWhm0YRbTHnU&usqp=CAc"
        />
      </div>
      <div class="price">
        <p>Apple iPhone13(Blue 512GB)</p>
        <ul>
          <li>512 GB ROM</li>
          <li>15.49 cm (6.1 inch) Super Retina XDR Display</li>
          <li>12MP + 12MP | 12MP Front Camera</li>
          <li>A15 Bionic Chip Processo</li>
        </ul>
        <p style="font-weight: 600">₹1,09,900</p>
        <button @click="add_delFunc()">Add item</button>
        <div v-show="status">
          <div class="quantity-toggle">
            <button @click="quantity1--">&mdash;</button>
            <input type="text" :value="quantity1" readonly />
            <button @click=" quantity1++">&#xff0b;</button>
          </div>
        </div>
      </div>
    </div>

    <div class="box box2">
      <div class="image image2">
        <img
          src="https://rukminim1.flixcart.com/image/312/312/ksnjp8w0/mobile/w/u/8/galaxy-z-flip3-5g-sm-f711bzeeinu-samsung-original-imag662adrayy6cg.jpeg?q=70"
        />
      </div>
      <div class="price">
        <p>SAMSUNG Galaxy Z Flip3 5G (Cream, 256 GB) (8 GB RAM)</p>
        <ul>
          <li>8 GB RAM | 256 GB ROM</li>
          <li>17.02 cm (6.7 inch) Full HD+ Display</li>
          <li>12MP + 12MP | 10MP Front Camera</li>
          <li>3300 mAh Lithium-ion Battery</li>
          <li>Qualcomm Snapdragon 888 Octa-Core Processor</li>
        </ul>
        <p style="font-weight: 600">₹88,999</p>
        <button @click="add_delFunc2()">Add item</button>
        <div v-show="status2">
          <div class="quantity-toggle">
            <button @click="quantity2--">&mdash;</button>
            <input type="text" :value="quantity2" readonly />
            <button @click="quantity2++">&#xff0b;</button>
          </div>
        </div>
      </div>
    </div>

    <div class="box box3">
      <div class="image image3">
        <img
          src="https://rukminim1.flixcart.com/image/312/312/kdxfc7k0/mobile/c/k/b/mi-10-mzb8923in-original-imafuq8sjfjuj3gv.jpeg?q=70"
        />
      </div>
      <div class="price">
        <p>Mi 10 (Coral Green, 256 GB) (8 GB RAM)</p>
        <ul>
          <li>8 GB RAM | 256 GB ROM</li>
          <li>16.94 cm (6.67 inch) Display</li>
          <li>108MP + 13MP + 2MP + 2MP | 20MP Front Camera</li>
          <li>4780 mAh Battery</li>
          <li>Qualcomm Snapdragon 865 Processor</li>
          <li>Full HD+ 3D Curved E3 AMOLED HDR 10+ Display</li>
          <li>30 W Charging</li>
        </ul>
        <p style="font-weight: 600">₹54,999</p>
        <button v-on:click="add_delFunc3()">Add item</button>
        <div v-show="status3">
          <div class="quantity-toggle">
            <button @click="quantity3--">&mdash;</button>
            <input type="text" :value="quantity3" readonly />
            <button @click="quantity3++">&#xff0b;</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      status: false,
       status2: false,
        status3: false,
      quantity1: 1,
       quantity2: 1,
        quantity3: 1,
    };
  },
  methods: {
    add_delFunc() {
      this.status = !this.status;
    },
    add_delFunc2() {
      this.status2 = !this.status2;
    },
    add_delFunc3() {
      this.status3 = !this.status3;
    }
}}
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
  margin: 10px;
  padding: 10px;
  border-right: brown 2px solid;
}
.image2 {
  padding-right: 20px;
}
.image3 {
  padding: 0 77px;
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
</style>
