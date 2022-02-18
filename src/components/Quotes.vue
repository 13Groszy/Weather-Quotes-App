<template>
        <button id="show-modal" @click="showModal = true">Draw a random quote</button>
        <Teleport to="body">
    <modal :show="showModal" @close="showModal = false"></modal>
  </Teleport>
</template>

<script>
import Modal from './Modal.vue'
export default {
    name: 'Quote',
    data() {
        return {
            showModal: false
        }
    },
    components: {
        Modal
    }
}
</script>
<style lang="scss" scoped>
button{
    background-color: rgb(8, 151, 233);
    border:0;
    border-radius: 5px;
    padding:0.5rem;
    margin-bottom:5vh;

    @media (max-width: 320px) {
        display: none;
    }
}
</style>