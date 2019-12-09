<template>
  <div id="app">
    <section class="modal-btns">
      <button class="modal-btns__btn" @click="simpleModal.isOpen = true">Open model window</button>
      <button class="modal-btns__btn" @click="formModal.isOpen = true">Open model window</button>
    </section>
    <transition name="modal">
      <Modal v-if="simpleModal.isOpen" @close="simpleModal.isOpen = false" title="New Modal">
        <div slot="body">
          <p>Simplest modal window</p>
          <button
            class="modal-btns__btn"
            @click.prevent="simpleModal.isOpen = false"
          >Close model window</button>
        </div>
      </Modal>
    </transition>
    <transition name="modal">
      <Modal v-if="formModal.isOpen" @close="modalClose(formModal)">
        <form slot="body" @submit.prevent="modalClose(formModal)">
          <label>
            Name:
            <input type="text" v-model="formModal.name" />
          </label>
          <label>
            email:
            <input type="text" v-model="formModal.email" />
          </label>
        </form>
      </Modal>
    </transition>
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";
export default {
  name: "app",
  components: {
    Modal
  },
  data() {
    return {
      simpleModal: {
        isOpen: false
      },
      formModal: {
        isOpen: false,
				name: "",
				email: ""
      }
    };
  },
  methods: {
    modalClose(name) {
      for (let item in name) {
        if (typeof name[item] === "string") {
          name[item] = "";
        }
      }
      name.isOpen = false;
    }
  }
};
</script>
