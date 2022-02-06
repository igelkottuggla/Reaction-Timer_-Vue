<template>
   <div class="results"  :class="{pyro: isAwesome}">
       <p>Reaction Time: {{score}} ms </p>
       <p class="rank"> {{ rank }} </p>
       <div class="before"></div>
        <div class="after"></div>
    </div>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null,
            high: 320,
            average: 399,
            isAwesome: false
        }
    },
    mounted() {
        if(this.score < this.high) {
            this.rank = 'As quick as a flash!'
            this.isAwesome = true
        } else if(this.score <= this.average) this.rank = "Rapid reflexes"
        else this.rank = "Snail's pace... "
    }
}
</script>

<style>
    .results {
        position: relative;
        padding: 2.5rem 1rem;
        font-size: 1.5rem;
        color: #ffffff;
    }
    .rank {
        font-size: 2.5rem;
    }
</style>