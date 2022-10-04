<script>
    export default {
        props: ["name", "des", "price", "qty", "image"]
    }

</script>

<template>
    <section class="pr-card">
        <div class="pr-card-img">
            <div class="pr-img">
            <img :src="image" alt="">
            </div>
            <div>
                <h2 class="pr-name">{{ name }}</h2>
                <p class="pr-des">{{ des }}</p>
            </div>
        </div>
        <div>     
            <h3 class="pr-price">N{{ price }}</h3>
            <p class="pr-price"><b>Qty:</b> {{ qty }}</p>
        </div>
    </section>
</template>

<style scoped>
.pr-card {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 120px;
    margin-bottom: 20px;
    font-size: 0.8rem;
}

.pr-card-img {
    width: 60%;
    display: flex;
    align-items: center;
}

.pr-card-img .pr-img {
    width: 30%;
}
.pr-card-img img {
    height: 90px;
}
</style>