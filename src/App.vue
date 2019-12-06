<template>
  <div id="app">
    <section class="modal-btns">
      <button class="modal-btns__btn" @click="simpleModal.isOpen = true">Open model window</button>
			<button class="modal-btns__btn" @click="formModal.isOpen = true">Open model window</button>
    </section>
    <transition name="modal">
      <Modal v-if="simpleModal.isOpen" @close="simpleModal.isOpen" title="New Modal">
        <div slot="body">
					<p>Simplest modal window</p>
          <button class="modal-btns__btn" @click.prevent="isModelOpen = false">Close model window</button>
        </div>
      </Modal>
    </transition>
		<transition name="modal">
			<form slot="body">

			</form>
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
				formData: {

				}
			}
    };
  },
  methods: {
  }
};
</script>
