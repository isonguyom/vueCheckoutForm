<script>
    export default {
        props: ["name", "des", "price", "qty", "image"],
        emits: ['toggle-disabled']
    }

</script>

<template>
    <section class="pr-card">
        <button class="del-btn" @click="$emit('toggle-disabled')">x</button>
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
    height: 100px;
    margin-bottom: 15px;
    font-size: 0.8rem;
    border: 1px solid rgb(218, 217, 217);
    border-radius: 3px;
    padding: 0.5rem;
    background-color: rgba(165, 65, 26, 0.048);
}

.del-btn {
    position: absolute;
    top: 4px;
    right: 0;
    border: none;
    cursor: pointer;
    font-size: 1rem;
    z-index: 3;
}

.pr-card h2, .pr-card h3, .pr-card b {
    font-weight: 600;
    font-size: 0.9rem;
}

.pr-card h2 {
    color: rgb(165, 42, 26);
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
    height: 80px;
}
</style>