<template>
  <div class="galleryContainer">

          <div class="searchbar"> 
            <input
              class="main-search"
              type="text"
              name="search"
              placeholder="Search item..."
              v-model= "searchedTitle"
              v-on:keyup.enter="searchProduct(searchedTitle)"
            />
            </div>
  <div class="navbar-div">
    <ul class="main-ul">
    <li class="main-li-categories">
        <button class="button-sort" @click="filterByCategory('showAll')">Show all</button>
      </li>
      <li class="main-li-categories">
        <button class="button-sort" @click="filterByCategory('electronics')">Electronics</button>
      </li>
      <li class="main-li-categories">
        <button class="button-sort" @click="filterByCategory('jewelery')">Jewelery</button>
      </li>
      <li class="main-li-categories">
        <button class="button-sort" @click="filterByCategory('men\'s clothing')">Men's clothing</button>
      </li>
      <li class="main-li-categories">
        <button class="button-sort" @click="filterByCategory('women\'s clothing')">Women's clothing</button>
      </li>
    </ul>

    <div class="sortBtn">
       <button class="sort-Btn" @click="lowToHigh">Price: Low to High</button>
       <button class="sort-Btn" @click="highToLow">Price: High to Low</button>
    </div>
  </div>
    <div class="products">

      
      <ul class="main-ul-products">
    
        <li
          class="product-li-class"
          v-for="product in filteredProducts"
          :key="product.id"
        >
          <img @click="getPopupDetails(product)" :src="product.image" :id="product.id" class="imgMain-products" />
          <h1 class="product-name">{{ product.title }}</h1>
          <p class="price-item">{{ product.price }} $</p>          
          <button @click="sendToCartFromGallery(product)" class="btn-product">Add item</button>
         
          
        </li>

      </ul>
      </div>
      <Popup :product="clickedProduct" @send-Product="sendToCartFromPopUp" @close-Popup="showPopup= false" v-if="showPopup" />
    </div>
      

</template>

<script>


export default {
  name: "Getgallery",
  components: {
      Popup: () => import('./Popup.vue'),
     
  },
  data() {
    return {
      products: [],
      filteredProducts: [],
      clickedProduct: null,
      showPopup: false,
      searchedTitle: ''
     
    };
  },
  props:{
    cart: Array,
    search: String
  },
  methods: {
    filterByCategory(category){
        if(category === 'showAll'){
            this.filteredProducts = this.products;
            return;
        }

        this.filteredProducts = this.products.filter(product => {
            return product.category === category;
            
        })
    },
    searchProduct(searchedTitle){
      this.filteredProducts = this.products.filter(product=>{
        return product.title.includes(searchedTitle);
        
      })
    },
    getPopupDetails(product){
        this.showPopup = true;
        this.clickedProduct = product;
    },

  sendToCartFromPopUp(){
    this.cart.push(this.clickedProduct);
    this.$emit('getCartFromGallery',this.cart);
    
  },

  sendToCartFromGallery(product){
    this.cart.push(product);
    this.$emit('getCartFromGallery',this.cart);
 
    
  },

  lowToHigh(){
    this.filteredProducts.sort(function(lowest, highest){
        return lowest.price - highest.price;
    }); 
    
  },
    highToLow(){
    this.filteredProducts.sort(function(lowest, highest){
        return highest.price - lowest.price;
    }); 
    
  },


   
  },
  created() {
    fetch("https://fakestoreapi.com/products/")
      .then((res) => res.json())
      .then((json) => (this.products = this.filteredProducts = json));
  
  },
};
</script>

<style scoped>
/*responsive*/
@media (max-width: 1200px) {
  .main-ul-products {
    grid-template-columns: 50% 50%;
  }
}

@media (max-width: 767px) {
  .footer-col {
    width: 50%;
    margin-bottom: 30px;
  }
}
@media (max-width: 574px) {
  .footer-col {
    width: 100%;
  }
}

/*********************************/
/* Products */
/*********************************/

.select {
  margin-top: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.category {
  margin-left: 50%;
}

.product-name {
  font-size: 22px;
  text-align: center;
  width: 250px;
}

.galleryContainer {
  display: block;
  justify-content: center;
  margin: 0rem 23rem;
}

.main-ul-products {
  display: grid;
  grid-template-columns: 25rem 25rem 25rem;
  grid-template-rows: 30rem 30rem 30rem 30rem 30rem;
  column-gap: 1rem;
  row-gap: 1rem;
  justify-content: space-between;
  margin-top: 2rem;
}

.imgMain-products {
  height: 170px;
  width: 170px;
}

.product-name {
  font-size: 1.2rem;
  margin-top: 1.5rem;
}

.product-li-class {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border: 1px solid rgb(0, 0, 0);
  height: 100%;
  border-radius: 10px;
  box-shadow: 0 2.4rem 4.8rem rgba(0, 0, 0, 0.075);
}

.description-item {
  font-size: 1.2rem;
}

.btn-product {
  background-color: antiquewhite;
  height: 50px;
  width: 150px;
}

.main-ul { 
  display: flex;
  text-decoration: none;
  list-style: none;
  gap: 0.2rem;
}


.navbar-div {
  display: flex;
  justify-content: space-between; 
  width: 100%;
  height: 0%;
  gap: 1rem;

}

.button-sort {
  background-color: #0096db;
  color: white;
  height: 35px;
  width: 110px;
  border: 1px solid black;
}
.searchbar {
  display: flex;
  height: 3.5rem;
  justify-content: flex-end;
}

.main-search {
  height: 2.5rem;
  width: 16.4rem;
}

.sortBtn {
    display: flex;
    justify-content: flex-end;
    gap: 0.2rem;
}

.sort-Btn {
  background-color: #0096db;
  color: white;
  height: 35px;
  width: 130px;
  border: 1px solid black;
}



/*********************************/
/* KORT */
/*********************************/

.price-item {
  color: grey;
  font-size: 30px;
  padding: 10px 0px;
}

.padd {
  padding: 10px 0px 0px 0px;
}

.card button:hover {
  opacity: 0.7;
}
</style>
