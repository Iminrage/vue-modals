<template>

    <div class="modal">
      <div class="modal__backdrop" @click="modalClose"></div>
      <div class="modal__window">
        <h3 class="modal__title">{{ title }}</h3>
        <div class="modal__body">
          <slot name="body"></slot>
        </div>
        <button class="modal__close" type="button" @click="modalClose">x</button>
      </div>
    </div>

</template>
<script>
export default {
  name: "Modal",
  props: {
    title: {
      type: String,
      required: true,
      default: "Modal Window!"
    }
  },
  mounted() {
    document.body.addEventListener("keyup", e => {
      if (e.keyCode === 27) {
        this.$emit("close");
      }
    });
  },
  methods: {
    modalClose() {
      this.$emit("close");
    }
  }
};
</script>