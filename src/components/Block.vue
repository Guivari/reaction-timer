<template>
<div class="block" v-if="showBlock" @click="clicked" :class="{active: isActive}">
    <p v-show="!isActive">Click here...</p>
    <p v-show="isActive">GO!</p>
</div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: true,
            isActive: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.isActive = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        clicked() {
            if (this.isActive) {
                this.showBlock = false
                this.isActive = false
                this.stopTimer()
            }
        },
        startTimer() {
            this.reactionTime = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            console.log(this.reactionTime)
            clearInterval(this.reactionTime)
            this.$emit('end', this.reactionTime)
        }
    }

}
</script>

<style>
.block {
    width: 400px;
    padding: 100px 0;
    border-radius: 20px;
    text-align: center;
    margin: 40px auto;
    background: red;
    color: white;
    max-height: 100px;
}

.active {
    background: green;
}

.active:hover {
    cursor: pointer;
}

</style>