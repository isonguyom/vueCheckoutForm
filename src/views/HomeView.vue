<script>
import ProductCard from '../components/ProductCard.vue';
import PaymentForm from '../components/PaymentForm.vue';

let id = 0;

export default {
  components: { ProductCard, PaymentForm },
  data() {
    return {
      products: [
        { id: id++, name: "Campari Bitter 1L", des: "Italian Bitter", price: "9,000", qty: 5, img: "/src/assets/Campari_1.png" },
        { id: id++, name: "Hennessy V.S.O.P", des: "French Cognac", price: "50,000", qty: 2, img: "/src/assets/VSOP_1.png" },
        { id: id++, name: "Remy Martin VSOP", des: "Master's art of blending", price: "38,000", qty: 3, img: "/src/assets/remy-martin.webp" },
      ],
      amount: 0,
      vat: 0,
      total: 0
    }
  },

  methods: {
    calAmount() {
      
      this.amount = (9000 * 5) + (50000 * 2) + (38000 * 3)
  
    },
  },

  mounted() {
    this.calAmount(),
    this.vat = Math.ceil(0.2 * this.amount),
    this.total = this.vat + this.amount
  }
}
</script>

<template>
  <main>
    <h1>Checkout Form</h1>
    <div class="wrapper">
      <div class="payment-wrapper">
        <PaymentForm :total="total"></PaymentForm>
      </div>
      <div>
        <h1>Cart</h1>
        <ProductCard v-for="product in products" :name="product.name" :des="product.des" :price="product.price"
          :qty="product.qty" :image="product.img"></ProductCard>

          <div>
            <p><b>Amount:</b> {{ amount }}</p>
            <p><b>VAT:</b> {{ vat }}</p>
            <p><b>Gross Total:</b> {{ total }}</p>
          </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  min-height: 100vh;
}

.payment-wrapper {
  width: 100%;
}

@media (min-width: 768px) {
  .wrapper {
    display: flex;
    justify-content: space-between;
    
  }

  .wrapper > div {
    width: 45%;
  }
}
</style>