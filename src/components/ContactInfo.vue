<template>
  <div>
    <a href="#" @click.prevent="open">{{contact.name}}</a>
    <transition v-if="showModal">
      <div class="modal-frame">
        <h1>{{contact.name}}'s contact information</h1>
        <p>Number(s) : {{contact.number.map(x => x.value).join( " | " )}}</p>
        <p>Address(es): {{ contact.address.map(x => x.value).join( " | " ) }}</p>
        <p>Email(s) : {{ contact.email.map(x => x.value).join(" | ") }}</p>
        <a href="#" @click.prevent="close">Back to the list</a>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showModal: false
    };
  },
  props: ["contact"],
  methods: {
    open() {
      this.showModal = true;
    },
    close() {
      this.showModal = false;
    }
  }
};
</script>
<style scoped>
.modal-frame {
  position: fixed;
  top: 50%;
  left: 25%;
  z-index: 99;
  width: 50%;
  background-color: #fff;
  border: 2px solid rgb(110, 110, 110);
  border-radius: 16px;
  box-shadow: 3px 3px 5px rgba(0, 0, 0, 0.3);
  padding: 30px 10px;
}

.deleteButton {
  position: absolute;
  left: 38px;
  color: rgb(221, 59, 59);
}
</style>