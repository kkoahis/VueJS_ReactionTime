<template>
    <h1 class="score">Your reaction: {{ score }}ms</h1>
    <p class="rank">Your are {{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = "go pro bro!"
        } else if (this.score < 500) {
            this.rank = "normal"
        } else {
            this.rank = "chicken"
        }
    }
}
</script>

<style>
.score {
    text-align: center;
    width: 350px;
    margin: 20px auto;
    padding: 10px;
    border-radius: 5px;
    background: #12d0a1;
    color: white;
}

.rank {
    font-style: 1.4em;
    color: crimson;
    font-weight: bold;
}
</style>