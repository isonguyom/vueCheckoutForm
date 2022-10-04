<script>
import ProductCard from '../components/ProductCard.vue';
import PaymentForm from '../components/PaymentForm.vue';

let id = 0;

export default {
  components: { ProductCard, PaymentForm },
  data() {
    return {
      products: [
        { id: id++, name: "Campari Bitter 1L", des: "Italian Bitter", price: "9,000", qty: 5, img: "/src/assets/Campari_1.png", disabled: false },
        { id: id++, name: "Hennessy V.S.O.P", des: "French Cognac", price: "50,000", qty: 2, img: "/src/assets/VSOP_1.png", disabled: true },
        { id: id++, name: "Remy Martin VSOP", des: "Master's art of blending", price: "38,000", qty: 3, img: "/src/assets/remy-martin.webp", disabled: false },
      ],
      amount: 0,
      vat: 0,
      total: 0
    }
  },

  methods: {
    calAmount() {
      let totalPr = 0
      for (let i = 0; i < this.products.length; i++) {
        let prPrice = ""
        if (this.products[i].disabled == false) {
          prPrice = this.products[i].price.replace(",", "")
          totalPr += parseInt(prPrice) * this.products[i].qty
        }
      }
      // Calculate total amount
      this.amount = totalPr
      this.vat = Math.ceil(0.15 * this.amount)
      this.total = this.vat + this.amount
    },

    toggleDisabled(product) {
      product.disabled = !product.disabled
      this.calAmount()
    }
  },

  mounted() {
    this.calAmount()      
  }
}
</script>

<template>
  <main>
    <h1>Checkout Form</h1>
    <div class="wrapper">
      <div>
        <h2>Cart</h2>
        <ProductCard v-for="product in products" :name="product.name" :des="product.des" :price="product.price"
          :qty="product.qty" :image="product.img" @toggle-disabled="toggleDisabled(product)"
          :class="{disabled: product.disabled }"></ProductCard>

        <div class="summary">
          <p><b>Amount:</b> <span>₦{{ amount }}</span></p>
          <p><b>VAT:</b> <span>₦{{ vat }}</span></p>
          <p><b>Gross Total:</b> <span>₦{{ total }}</span></p>
        </div>
      </div>
      <div class="payment-wrapper">
        <PaymentForm :total="total"></PaymentForm>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  min-height: 100vh;
}

.wrapper {
  margin-top: 25px;
}

b {
  font-weight: 600;
}

h2 {
  margin-bottom: 7px;
  color: rgb(165, 42, 26);
  font-size: 1.2rem;
}

.payment-wrapper {
  width: 100%;
  margin-top: 40px;
}

.summary {
  margin-top: 15px;
}

.summary span {
  text-align: right;
  float: right;
}

.disabled {
  opacity: 0.4;
}

@media (min-width: 768px) {
  .wrapper {
    display: flex;
    justify-content: space-between;

  }

  .wrapper>div {
    width: 45%;
    margin-top: 0;
  }
}
</style>