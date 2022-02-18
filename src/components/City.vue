<template>
    <div  v-if="this.passedCity != ''">
        <p>{{passedCity}}</p>
    </div>
</template>

<script>
export default {
    name: 'City',
    props: ['passedCity']
}
</script>

<style lang="scss" scoped>
div{
    display: flex
}
p{
    font-size: 1.2rem;
    font-weight: bold;
    margin:auto;
}
</style>