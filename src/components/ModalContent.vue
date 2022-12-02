<style>
.modal-content {
    border: 1px solid grey;
    background-color: white;
    padding: 1rem;
}
</style>
<script>
    const component = {
        props: ['modal'],
        data() {
          return {
            comp: component
          }
        },
        methods: {
            showMoreModal() {
                this.modal.showModal(this.comp, {modal: this.modal}, '여기서부터 중첩 모달창')
            }
        }
    }
    export default component
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
