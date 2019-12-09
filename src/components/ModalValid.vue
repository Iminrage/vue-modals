<template>
  <Modal @close="$emit('close')">
    <form slot="body" @submit.prevent="onSubmit">
      <div>
        <div v-if="$v.name.$error">
          <p v-if="!$v.name.required">Required name!</p>
          <p v-if="!$v.name.minLength">Not enough symbols!</p>
        </div>
        <input type="text" v-model.lazy="$v.name.$model" />
      </div>
      <div>
        <div v-if="$v.email.$error">
          <p v-if="!$v.email.required">Required email!</p>
          <p v-if="!$v.email.email">Incorrect email!</p>
        </div>
        <input type="text" v-model.lazy="$v.email.$model" />
      </div>
			<button type="submit">submit!</button>
    </form>
  </Modal>
</template>

<script>
import Modal from "./Modal.vue";
import { required, minLength, email } from "vuelidate/lib/validators";
export default {
  name: "ModalValid",
  components: {
    Modal
  },
  data() {
    return {
      name: "",
      email: ""
    };
  },
  validations: {
    name: {
      required,
      minLength: minLength(2)
    },
    email: {
      required,
      email
    }
	},
	methods:{
		onSubmit(){
			this.$v.$touch();
			if (!this.$v.$invalid) {
				this.$v.$reset();				
				this.$emit("close")
			}
			
		}
	}
};
</script>

<style scoped>
</style>