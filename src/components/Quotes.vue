<template>
        <button id="show-modal" @click="showModal = true">Show random quote</button>
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
    background-color: transparent;
    border:0;
    margin-inline: 0.5rem;
}
</style>