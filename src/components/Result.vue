<template>
<div class="result">
    <p>Reaction time - {{ score }}ms</p>
</div>
</template>

<script>
export default {
    props: ['score']
}
</script>

<style>
.result{
    width: 400px;
    padding: 100px 0;
    border-radius: 20px;
    text-align: center;
    margin: 40px auto;
    background: cadetblue;
    color: white;
    max-height: 100px;
}
</style>