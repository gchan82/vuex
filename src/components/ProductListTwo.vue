<template>
<div id="product-list-two">
  <h2>Product List Two</h2>
  <ul>
    <li v-for="product in saleProducts">
      <span class="name">{{product.name}}</span>
      <span class="price">${{product.price}}</span>
    </li>
  </ul>
  <button v-on:click="reducePrice(4)">Reduce Price</button>
  <!--click -> $4 discount goto line 35-36 dispatch to store-->
</div>
</template>

<script>
import {
  mapActions
} from 'vuex'
import {
  mapGetters
} from 'vuex'

export default {
  strict: true,
  computed: {
    products() {
      return this.$store.state.products;
    },
    ...mapGetters([ // maps getters in store.js on line 15 to properties below
      'saleProducts'
    ])
    /* saleProducts(){
       return this.$store.getters.saleProducts; // get 50% sale, send to line 5 saleProducts    
       }
       */
  },
  methods: {
    ...mapActions([ // map actions from store to properties below
      'reducePrice'
    ])

    //reducePrice: function(amount){ 
    //this.$store.dispatch('reducePrice', amount) // goes to store.js actions line 33
    /*this.$store.state.products.forEach(product => {
      product.price -= 1;
    })*/
    // this.$store.commit('reducePrice'); // commit reducePrice mutation in store.js, button "reducePrice" line 10 fires this. Note: instead of commit directly, should dispatch action due to async nature of requesting data.
  },
  components: {

  },
  data() {
    return {

    }
  }
}
</script>

<style scoped>
#product-list-two {
  background: #d1E4ff;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0, 2);
  margin-bottom: 30px;
  padding: 10px 20px;
}

#product-list-two ul {
  padding: 0;
  list-style-type: none;
}

#product-list-two li {
  margin-right: 10px;
  margin-top: 10px;
  padding: 20px;
  background: rgba(255, 255, 255, 0.7);
}

.price {
  font-weight: bold;
  color: #860CE8;
  display: block;
}
</style>
