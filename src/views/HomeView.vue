<template>
  <div class="home page-flex">
    <ModalComponent :modalActive="modalActive" @close="toggleModal">
      <div class="modal-content">
        <h1>Header</h1>
        <p>message</p>
      </div>
    </ModalComponent>
    <button class="btn" @click="toggleModal">Show Modal</button>
  </div>
</template>

<script>
import { ref } from "vue";
import ModalComponent from "@/components/Modal.vue";

export default {
  name: "HomeView",
  components: { ModalComponent },
  setup() {
    const modalActive = ref(false);

    const toggleModal = () => {
      modalActive.value = !modalActive.value;
    };
    return { modalActive, toggleModal };
  },
};
</script>

<style lang="scss" scoped>
@use "../styles/mixin/colors" as colors;

.home {
  background-color: colors.$primary-bg;
  height: 100vh;

  .modal-content {
    display: flex;
    flex-direction: column;
    h1 {
      margin-bottom: 12px;
      font-size: 32px;
    }
    p {
      margin-bottom: 16px;
      font-size: 18px;
    }
  }

  .btn {
    width: 120px;
    background-color: colors.$danger-primary;
    color: colors.$white;
  }
}
</style>
