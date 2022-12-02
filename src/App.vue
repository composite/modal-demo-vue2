<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <p><button @click="() => this.showModal()">모달창 열기</button></p>
    <JustModal ref="modal" />
  </div>
</template>

<script>
import JustModal from './components/JustModal.vue'
import ModalContent from "@/components/ModalContent";

export default {
  name: 'App',
  components: {
    JustModal
  },
  data() {
    return {
      comp: ModalContent
    }
  },
  methods: {
    async showModal() {
      this.$refs.modal.showModal(this.comp, { modal: this.$refs.modal }, '첫번째 모달창')
    }
  }
}
</script>

<style>
#app {
  text-align: center;
}
</style>
