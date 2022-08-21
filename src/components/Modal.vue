<template>
  <transition name="modal-animation">
    <div v-show="modalActive" class="modal page-flex">
      <transition name="modal-inner-animation">
        <div v-show="modalActive" class="modal-inner box-shadow">
          <CloseIcon @click="handleClose" class="modal-close cursor-pointer" />

          <!-- Content -->
          <slot />
          <button @click="handleClose" class="btn">Close</button>
        </div>
      </transition>
    </div>
  </transition>
</template>

<script>
import CloseIcon from "@/features/Icons/CloseIcon.vue";
export default {
  name: "ModalComponent",
  components: { CloseIcon },
  props: ["modalActive"],
  setup(props, { emit }) {
    const handleClose = () => emit("close");

    return { handleClose };
  },
};
</script>

<style lang="scss" scoped>
@use "../styles/mixin/colors" as colors;

.modal {
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 0;
  left: 0;
  background-color: colors.$background-transparent;

  .modal-inner {
    position: relative;
    width: 85%;
    max-width: 640px;
    background-color: colors.$white;
    padding: 24px 16px;
    border-radius: 12px;

    .modal-close {
      position: absolute;
      top: 12px;
      right: 12px;
      width: 20px;
      height: 20px;
      &:hover {
        color: colors.$danger-primary;
      }
    }

    .btn {
      width: 80px;
      background-color: colors.$danger-primary;
      color: colors.$white;
    }
  }
}
</style>
