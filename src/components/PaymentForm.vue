<script>
export default {
    props: ["total"],

    data() {
        return {
            card: "",
            cardNum: "",
        }
    },

    watch: {
        cardNum() {
            this.checkCardType()
        }
    },


    methods: {
        onlyNums(e) {
            e.target.value = e.target.value.replace(/[^0-9.]/g, '').replace(/(\..*)\./g, '$1');
        },

        cardNumFormatting(e) {
            if (e.target.value !== "") {
                e.target.value = e.target.value.replace(/[^0-9.]/g, '').replace(/(\..*)\./g, '$1').match(/.{1,4}/g).join(' ');
            }
        },

        checkCardType() {
            if (this.cardNum !== "") {
                if (this.cardNum.match(/^5[1-5]/) || this.cardNum.match(/^2[2-7]/)) { ///^5(?=.*[1-5])/g
                    this.card = "master"
                }else if (this.cardNum.match(/^4/)) {
                    this.card = "visa"
                }else if (this.cardNum.match(/^5[0][67]/) || this.cardNum.match(/^5[6]/)) {
                    this.card = "verve"
                }else {
                this.card = ""
                }
            } else {
                this.card = ""
            }
        },

        changeToDate(e) {

            e.target.type = 'month'
        },

    },

}

</script>

<template>
    <div>
        <h2>Payment Details</h2>
        <div class="card-type-wrapper">
            <h1 class="mastercard" v-if="card === 'master'">
                <img src="../assets/mastercard.svg" alt="Master Card">
            </h1>
            <h1 class="visa" v-else-if="card === 'visa'">
                <img src="../assets/visa.svg" alt="Visa">
            </h1>
            <h1 class="verve" v-else-if="card === 'verve'">
                <img src="../assets/verve.png" alt="Verve">
            </h1>
            <h1 class="no-card" v-else>
                Invalid Card
            </h1>
        </div>
        <form action="">
            <div class="form-control">
                <label for="cardHolder">Holder Name</label>
                <input type="text" name="holder" id="cardHolder">
            </div>
            <div class="form-control">
                <label for="cardNumber">Card Number</label>
                <input type="text" name="card-number" id="cardNumber" v-model="cardNum" maxlength="19"
                    @keyup="cardNumFormatting">
                <p>{{ cardNum }}</p>
            </div>
            <div class="form-control-wrapper">
                <div class="form-control">
                    <label for="validity">Valid Until</label>
                    <input type="text" name="validity" id="validity" placeholder="MM/YYYY" @focus="changeToDate">
                </div>
                <div class="form-control">
                    <label for="cvc">CVC</label>
                    <input type="password" name="cvc" id="cvc" maxlength="3" @input="onlyNums">
                </div>
            </div>
            <button type="submit">Pay ₦{{ total }}</button>
        </form>
    </div>
</template>

<style scoped>
h2 {
    color: rgb(165, 42, 26);
    font-size: 1.2rem;
}

.card-type-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 10px 0 30px;
    min-height: 100px;
}

.card-type-wrapper h1 {
    text-transform: uppercase;
    color: rgb(156, 154, 154);
    display: flex;
    justify-content: center;
    align-items: center;
}

.card-type-wrapper h1 img {
    height: 90px;
    display: block;
}

.card-type-wrapper h1.no-card {
    height: 90px;
    background-color: rgb(212, 212, 212);
    padding: 15px;
    width: 100%;
    font-weight: 700;
}


form {
    width: 100%;
}

.form-control-wrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
}

form .form-control {
    width: 100%;
    margin-bottom: 20px;
}

form input {
    width: 100%;
    padding: 12px 7px;
    border: 1px solid rgb(218, 217, 217);
    margin-top: 3px;
}

form input:hover {
    border-color: rgb(165, 42, 26);
}

form .form-control-wrapper input {
    width: 70px;
    display: block;
}

form .form-control-wrapper input#validity {
    width: 120px;
}

form button {
    width: 100%;
    padding: 15px;
    cursor: pointer;
    margin-top: 20px;
    border: none;
    background-color: rgb(165, 42, 26);
    color: #fff;
}

form button:hover {
    background-color: rgb(121, 25, 13);
}
</style>