<template>
  <teleport to="body">
      <div v-if="show" @click="tryClose" class="backdrop"></div>
    <transition name="dialog">
      <dialog open v-if="show">
        <div>
          <span class="error-text">{{ errorText }}</span>
        </div>
        <div class="button-positions">
          <button @click="tryClose">Close</button>
        </div>
      </dialog>
    </transition>
  </teleport>
</template>

<script>
export default {
  props: ["errorText","show"],
  emits:['close'],
  methods: {
    tryClose() {
      this.$emit('close');
    },
  },
};
</script>

<style scoped>
dialog {
  position: fixed;
  top: 40vh;
  left: 37%;
  min-width: 25%;
  min-height: 15%;
  z-index: 100;
  border-radius: 12px;
  border: none;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  overflow: hidden;
  background-color: rgb(255, 255, 255, 0.5);
}
button {
  text-decoration: none;
  padding: 5px 10px;
  font: inherit;
  background-color: rgb(0, 0, 0, 0.5);
  border: 1px solid black;
  color: white;
  cursor: pointer;
  border-radius: 30px;
  display: inline-block;
  opacity: 0.5;
  box-shadow: 1px 2px rgba(0, 0, 0, 0.5);
}
button:hover{
    color: black;
    background-color: rgba(255, 255, 255, 0.75) ;
    transform: scale(1.05);
    transition: all 0.3s ease-in-out;
}
.button-positions {
  display: flex;
  justify-content: right;
  margin-top: 10%;
}
.error-text{
font-size: 20px;
font-weight: bold;
color: white;
text-shadow: 3px 3px rgba(0, 0, 0, 0.26);
}
.backdrop{
    position: fixed;
    top: 0;
    left: 0;
    height: 100vh;
    width: 100%;
    background-color: rgba(0, 0, 0, 0.25);
    z-index: 10;
}
.dialog-enter-from,
.dialog-leave-to {
  opacity: 0;
  transform: scale(0.7);
}
.dialog-enter-active {
  transition: all 0.3s ease-out;
}
.dialog-leave-active {
  transition: all 0.3s ease-in;
}
.dialog-enter-to,
.dialog-leave-from {
  opacity: 1;
  transform: scale(1);
}
@media only screen and (max-width: 728px){
  dialog{
    left: 35%;
    min-width: 33%;
    min-height: 20%;
  }
  .button-positions {
    margin-top: 12%;
  }
  .error-text{
    font-size: 17px;
  }
  button{
    font-size: 14px;
  }
}
@media only screen and (max-width: 480px) {
  dialog{
    left: 30%;
    min-width: 45%;
    min-height: 15%;
  }
  .button-positions {
    margin-top: 15%;
  }
  .error-text{
    font-size: 15px;
  }
  button{
    font-size: 12px;
  }
}
</style>
