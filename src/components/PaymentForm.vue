<script>
    export default {
        props: ["total"]
    }

</script>

<template>
    <div>
        <h1>Payment Details</h1>
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
            <button type="submit">Pay N{{ total }}</button>
        </form>
    </div>
</template>

<style scoped>
.card-type-wrapper {
    display: flex;
    justify-content: space-between;
    margin: 30px 0;
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
    padding: 10px 7px;
}

form .form-control-wrapper input {
    width: 70px;
    display: block;
}

form button {
    width: 100%;
    padding: 10px;
    cursor: pointer;
    margin-top: 20px;
}
</style>