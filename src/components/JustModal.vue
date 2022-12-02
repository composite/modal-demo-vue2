<style>
.modal-root {
    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.25);
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0;
    border: 1px solid transparent;
}
.modal-content {
    border: 1px solid grey;
    background-color: white;
    padding: 1rem;
}
</style>
<script>

import Vue from "vue";

export default {
    data() {
        return {
            contents: []
        }
    },
    methods: {
        showModal(content, props, slot) {
            this.contents.push({content, props: props || {}, slot})
        },
        hideModal(isall) {
            if (isall) this.contents.length = 0
            else this.contents.pop()
        },
        modalLength() {
            return this.contents.length
        },
        isVue(obj) {
            //console.log(obj)
            return obj && (obj instanceof Vue || obj._isVue || typeof obj.render === 'function')
        },
        handleClickOutside(e) {
            if (e.target === e.currentTarget) this.hideModal()
        },
        logger(...args) {
            console.log(...args)
        }
    }
}
</script>
<template>
  <div>
    <div v-for="(c, i) in contents" :key="i" class="modal-root" @click="handleClickOutside">
      <component v-if="isVue(c.content)" :is="c.content" v-bind="c.props">
        <component v-if="isVue(c.slot)" :is="c.slot"></component>
        <div v-if="!isVue(c.slot)" class="modal-sub">{{c.slot}}</div>
      </component>
      <div v-if="!isVue(c.content)" class="modal-content">{{c.content}}</div>
    </div>
  </div>
</template>
