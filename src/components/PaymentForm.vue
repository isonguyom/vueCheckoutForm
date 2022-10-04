<script>
    export default {
        props: ["total"]
    }

</script>

<template>
    <div>
        <h2>Payment Details</h2>
        <div class="card-type-wrapper">
            <div></div>
            <div></div>
            <div></div>
        </div>
        <form action="">
            <div class="form-control">
                <label for="cardHolder">Holder Name</label>
                <input type="text" name="holder" id="cardHolder">
            </div>
            <div class="form-control">
                <label for="cardNumber">Card Number</label>
                <input type="number" name="card-number" id="cardNumber">
            </div>
            <div class="form-control-wrapper">
                <div class="form-control">
                    <label for="validity">Valid Until</label>
                    <input type="date" name="validity" id="validity">
                </div>
                <div class="form-control">
                    <label for="cvc">CVC</label>
                    <input type="number" name="cvc" id="cvc">
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
    justify-content: space-between;
    margin: 10px 0 30px;
}

.card-type-wrapper > div {
    width: 30%;
    height: 50px;
    background-color: grey;
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

form .form-control-wrapper input {
    width: 70px;
    display: block;
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