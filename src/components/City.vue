<template>
    <div  v-if="this.passedCity != ''">
        <h2>{{passedCity}}</h2>
    </div>
</template>

<script>
export default {
    name: 'City',
    props: ['passedCity']
}
</script>