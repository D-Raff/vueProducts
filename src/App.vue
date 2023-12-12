<template>
  <div class="wrapper">
    <div class="row" v-if="products.length">
      <!-- v-if will remove the element from the dom. v-show is the same as display none. v-show will be used if you dont need an else statement -->
      <!-- check if we have data inside our array. can also just use the variable name "products" -->
      <div class="prodCard" v-for="product in products" :key ="product.id">
        <!-- don't use if statememnt and for loops on the same div. when using for loops make use of a key. make sure the div is unique. v-bind:key="product.id" is the same thing as the :key="product.id" -->
        <div class="card-header">
          <h3>
            {{ product.prodName }}
            <!-- we use the variable given in the for loop(product in this case) -->
          </h3>
        </div>
        <div class="card-body">
          <img @mouseenter="onMouseEnter" @mouseleave="onMouseLeave" :src="product.image" :alt="product.prodName" loading="lazy">
          <!-- if you gave the product an image link already, use :src="product.image" -->
          <p :class="product.amount > 420 ? 'expensive' : 'cheap'">R{{ product.amount.toFixed(2) }}</p>
          <!-- using a ternary operator(if statement) to change things inside of the p  shortcut ->
          :class="{expensive : product.amount > 420}"
          -->
        </div>
        <div class="card-footer"><a href="" type="button">view details</a></div>
      </div>
    </div>
    <!-- <div v-else>
      <h2>Sorry, our products are out of stock</h2>
    </div> -->
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    // data is also referred to as reactive state.
    return {
      products: [
        {
          id: 1,
          prodName: 'Python Crash Course',
          category: 'Python',
          amount: 400.9999,
          image: 'https://i.postimg.cc/MKDLBPYm/Python-Crash-Course-cover.jpg'
        },
        {
          id: 2,
          prodName: 'Python Programming',
          category: 'Python',
          amount: 900.4586,
          image: 'https://i.postimg.cc/rFcbKX5p/Python-Programming-for-Beginners-cover.jpg'
        },
        {
          id: 3,
          prodName: 'Mastering C++',
          category: 'C++',
          amount: 1800.896,
          image: 'https://i.postimg.cc/Ss9zrpfT/Mastering-C-Programming.jpg'
        },
      ]
      // products: []
    }
  },
  components: {

  },
  methods: {
    onMouseEnter(){
      alert("Hello There")
    },
    onMouseLeave(){
      alert("Bye")
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  .wrapper :is(.row) {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }

  .prodCard {
    width: 18rem;
  }

  .prodCard :is(>*, img) {
    width: 100%;
    aspect-ratio: 1/1;
  }

  .expensive {
    font-weight: bolder;
    color: darkkhaki;
  }

  .cheap {
    color: black;
  }
}
</style>
