<template>
    <div v-if="show" class="modal">
        <div class="modal__wrapper">
            <div class="modal__wrapper__header">
                <button class="modal__wrapper__button" @click="$emit('close')">X</button>
                <h2>Quote for today is:</h2>
            </div>
            <Quote />
        </div>
    </div>
</template>


<script>
import Quote from './Quote.vue'
export default {
    name: 'Modal',
    components: {
        Quote
    },
    props:{
        show: Boolean
    }
}
</script>

<style lang="scss" scoped>
.modal{
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
    &__wrapper{
        display: flex;
        flex-direction: column;
        min-width: 300px;
        width:90%;
        background-color: #fff;
        top:30%;
        border-radius: 5px;
        margin:auto;
        position: relative;
        &__header{
            text-align: center;
        }
        &__button{
            background-color: transparent;
            border:0;
            position: absolute;
            right:0;
            margin:0.5rem;
        }
    }
}

</style>