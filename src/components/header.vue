<template>
    <header>
        <h1 class="title">Budget-Tracker</h1>
        <div class="total-sobra">
            <h2>Total</h2>
            <p>R${{ totalSobra }}</p>
        </div>
    </header>
</template>

<script>

export default {
    name: 'Header',
    props: {
        totalSobra: Number,
    }
}

</script>

<style scoped>
    header {
        display: flex;
        background-color: rgb(48, 48, 48);
        color: aliceblue;
        height: 100px;
        align-items: center;
        justify-content: space-between;
        padding: 15px 30px;
        border-bottom: 10px solid rgb(255, 0, 157) ;
    }
    .total-sobra > p{
        background-color: rgb(255, 0, 157);
        font-weight: bold;
        font-size: large;
        text-align: center;
        border-radius: 5px;
    }
</style>