<template>
    <div id="app">
      <div class="header-image">
      <div>
        <button class="button-sort" @click="goToGallery">Home</button>
        <button class="button-sort"  @click=goToContact>Contact us</button>
      </div>
        <a href="index.html"
          ><img
            src="https://i.ibb.co/jrpR7f0/logo.png"
            class="loga"
            alt="logo"
            border="0"
        /></a>
        <div>
            <button class="button-sort"  @click=goToCart >Cart ({{cartFromGallery.length}})</button>
            <button class="button-sort"  @click=emptyCart>Empty</button>
        </div>
      </div>


      <header class="main-header">
        <nav class="main-nav">

        </nav>
   
      </header>

 
  <Getcartpage :cart="cartFromGallery" v-if="cartVisible" @decrease="deleteFromCart" @deleteProduct="removeItemsFromCart"/>
  <Getgallery :cart="cartFromGallery" v-if="galleryVisible" @getCartFromGallery="getCart"/>
  <Contactus v-if="contactVisible" />

  <!-- ta bort footern så länge
  <section>
    <footer class="footer">
      <div class="fot-container">
        <div class="row">
          <div class="footer-col">
            <h4>What we do</h4>
            <ul>
              <li><a href="#">About us</a></li>
              <li><a href="#">Services</a></li>
              <li><a href="#">privacy policy</a></li>
            </ul>
          </div>
          <div class="footer-col">
            <h4>Get help</h4>
            <ul>
              <li><a href="contact.html">Contact us</a></li>
              <li><a href="#">Shipping</a></li>
              <li><a href="#">Return</a></li>
              <li><a href="#">Order status</a></li>
              <li><a href="#">Payments</a></li>
            </ul>
          </div>
          <div class="footer-col">
            <h4>online shop</h4>
            <ul>
              <li><a href="#">Electronics</a></li>
              <li><a href="#">Jewelery</a></li>
              <li><a href="#">Men's clothing</a></li>
              <li><a href="#">Women's clothing</a></li>
            </ul>
          </div>
          <div class="footer-col">
            <h4>follow us</h4>
            <div class="social-links">
              <a href="#"><i class="fab fa-facebook-f"></i></a>
              <a href="#"><i class="fab fa-twitter"></i></a>
              <a href="#"><i class="fab fa-instagram"></i></a>
              <a href="#"><i class="fab fa-linkedin-in"></i></a>
            </div>
          </div>
        </div>
      </div>
    </footer>
  </section>
  !-->
    
    </div>
</template>

<script>
import Getgallery from './Getgallery.vue'
import Getcartpage from './Getcartpage.vue'
import Contactus from './Contactus.vue'

export default {
    name: 'Body',
    components:{
      Getgallery,
      Getcartpage,
      Contactus
    },
    data(){
      return{
        galleryVisible: true,
        cartVisible: false,
        contactVisible: false,
        cartFromGallery: [],
        textSearch: '',
        id: null,
        indexToDelete: null,
        
        
      };
    },
    methods:{
      goToCart(){
        this.cartVisible = true;
        this.galleryVisible = false;
        this.contactVisible = false;
      },
      goToContact(){
        this.contactVisible =true;
        this.cartVisible = false;
        this.galleryVisible = false;
      },
            goToGallery(){
        this.contactVisible =false;
        this.cartVisible = false;
        this.galleryVisible = true;
      },
    getCart(cart){
      this.cartFromGallery = cart;
      console.log(this.cartFromGallery);
    
    },

    emptyCart(){
      this.cartFromGallery = [];
    },

    deleteFromCart(id) {
       this.indexToDelete = this.cartFromGallery.findIndex((c) => c.id == id);
     if (this.indexToDelete != -1) {
       console.log(this.indexToDelete);
        this.cartFromGallery.splice(this.indexToDelete, 1);

        console.log(this.cartFromGallery);
     }
    },

    removeItemsFromCart(id){
     this.cartFromGallery = this.cartFromGallery.filter((c) => c.id !== id);

     console.log(this.cartFromGallery);
        
    
    }
    }

}
</script>

<style scoped>

/**********************************/
/* HEADER */
/*********************************/
.main-header {
  width: 100%;
}

.header-image {
  display: flex;
  justify-content: space-evenly;
  align-items: flex-end;
  margin-bottom: 1rem;
}

.main-ul {
  display: flex;
  gap: 2rem;
  list-style: none;
  justify-content: center;
  padding-top: 16px;
  cursor: pointer;
}

.main-li-categories {
  font-weight: bold;
  font-size: 1.5rem;
}

.main-li-categories a {
  text-decoration: none;
  color: black;
}

a:hover {
  opacity: 0.6;
}

.main-li-contact {
  font-weight: bold;
  font-size: 1.5rem;
}

.loga {
  width: 10rem;
}

.button-sort{
    background-color: #0096db;
    color: white;
    height: 35px;
    width: 110px;
    border: 1px solid black;

}

.select {
  margin-top: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.category {
  margin-left: 50%;
}


/*********************************/
/* FOT */
/*********************************/
.fot-container {
  max-width: 1170px;
  margin: auto;
}
.row {
  display: flex;
  flex-wrap: wrap;
}
ul {
  list-style: none;
}
.footer {
  background-color: #24262b;
  padding: 70px 0;
  margin-top: 150px;
}
.footer-col {
  width: 25%;
  padding: 0 15px;
}
.footer-col h4 {
  font-size: 18px;
  color: #ffffff;
  text-transform: capitalize;
  margin-bottom: 35px;
  font-weight: 500;
  position: relative;
}
.footer-col h4::before {
  content: "";
  position: absolute;
  left: 0;
  bottom: -10px;
  background-color: #e91e63;
  height: 2px;
  box-sizing: border-box;
  width: 50px;
}
.footer-col ul li:not(:last-child) {
  margin-bottom: 10px;
}
.footer-col ul li a {
  font-size: 16px;
  text-transform: capitalize;
  color: #ffffff;
  text-decoration: none;
  font-weight: 300;
  color: #bbbbbb;
  display: block;
  transition: all 0.3s ease;
}
.footer-col ul li a:hover {
  color: #ffffff;
  padding-left: 8px;
}
.footer-col .social-links a {
  display: inline-block;
  height: 40px;
  width: 40px;
  background-color: rgba(255, 255, 255, 0.2);
  margin: 0 10px 10px 0;
  text-align: center;
  line-height: 40px;
  border-radius: 50%;
  color: #ffffff;
  transition: all 0.5s ease;
}
.footer-col .social-links a:hover {
  color: #24262b;
  background-color: #ffffff;
}


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

/* CONTACT FORMULÄR */

/***************************/
/* CTA SECTION*/
/***************************/
.section-cta {
  padding: 0 0 12.8rem;
  background-color: #fdf2e9;
}

.cta {
  display: grid;
  grid-template-columns: 2fr 1fr;
  /* background-color: #e67e22; */
  box-shadow: 0 2.4rem 4.8rem rgba(0, 0, 0, 0.015);
  border-radius: 11px;
  background-image: linear-gradient(to right bottom, #eb984e, #e67e22);
  overflow: hidden;
}

.cta-text-box {
  padding: 4.8rem 6.4rem 6.4rem 4.8rem;
  color: #45260a;
}

.cta-text {
  font-size: 1.8rem;
  line-height: 1.8;
  margin-bottom: 1.8rem;
  color: #333;
}

.cta .heading-secondary {
  /* color: #45260a; */
  color: inherit;
  margin-bottom: 3.2rem;
}

.cta-img-box {

  background-size: cover;
  background-position: center;
  height: auto;
  width: auto;
}

.cta-form {
  display: grid;
  grid-template-columns: 1fr 1fr;
  column-gap: 3.2rem;
  row-gap: 2.4rem;
}

.cta-form label {
  display: block;
  font-size: 1.6rem;
  font-weight: 500;
  margin-bottom: 1.2rem;
}

.cta-form input,
.cta-form select {
  width: 100%;
  padding: 1.2rem;
  font-size: 1.8rem;
  font-family: inherit;
  color: inherit;
  border: none;
  background-color: #fdf2e9;
  border-radius: 9px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
}

.cta-form input::placeholder {
  color: #aaa;
}

.cta *:focus {
  outline: none;
  box-shadow: 0 0 0 0.8rem rgba(230, 125, 34, 0.5);
}

.btn,
.btn:link,
.btn:visited {
  display: inline-block;

  font-size: 2rem;
  font-weight: 600;
  padding: 1.6rem 3.2rem;
  border-radius: 9px;
  text-decoration: none;

  /* for .btn it self */
  border: none;
  cursor: pointer;
  font-family: inherit;

  /* transition: background-color 0.3s; */
  transition: all 0.3s;
}

.btn--form {
  background-color: #45260a;
  color: #fdf2e9;
  align-self: end;
  padding: 1.2rem;
}

.btn--form:hover,
.btn--form:active {
  background-color: #fff;
  color: #555;
}

.heading-secondary {
  font-size: 4.8rem;
}


</style>