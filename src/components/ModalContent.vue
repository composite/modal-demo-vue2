<style>
.modal-content {
    border: 1px solid grey;
    background-color: white;
    padding: 1rem;
}
</style>
<script>
    import ModalContent from './ModalContent.vue'
    export default {
        props: ['modal'],
        data() {
          return {
            comp: ModalContent
          }
        },
        methods: {
            showMoreModal() {
                this.modal.showModal(this.comp, {modal: this.modal}, '여기서부터 중첩 모달창')
            }
        }
    }
</script>
<template>
    <div class="modal-content">
        <slot />
        <div style="text-align:center">
            <button @click="showMoreModal">모달창 더 띄우기</button>
            <button @click="() => modal.hideModal()">닫기</button>
        </div>
    </div>
</template>
