<template>
    <div>
        <p>Reaction Time - {{ score }} - Ms</p>
        <p class="rank">{{ rank }}</p>
    </div>
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
                this.rank = 'Perfect Timing'
            }   else if (this.score < 400) {
                this.rank = 'Not Bad'
            }   else {
                this.rank = 'Bad Timing'
            }
        }
    }
</script>

<style scoped>
    .rank {
        font-size: large;
        color: black;
        font-weight: bold;
    }

</style>