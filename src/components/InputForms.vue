<template>
  <div class="container card">
    <form class="d-flex flex-column align-items-center justify-content-center">
      <label for="name">Enter the name</label>
      <input type="text" id="name" v-model="title" />
      <label for="number">Enter the number</label>
      <input
        type="text"
        id="number"
        v-for="(obj, index) in numbers"
        :key="index + 'a'"
        v-model="obj.value"
        class="mb-2"
      />
      <button @click.prevent="addNumber" class="btn btn-info mt-1 mb-1">+</button>
      <label for="address">Enter the address</label>
      <input
        type="text"
        id="address"
        v-for="(obj, index) in addresses"
        :key="index + 'b'"
        v-model="obj.value"
        class="mb-3"
      />
      <button @click.prevent="addAddress" class="btn btn-info mt-1 mb-1">+</button>
      <label for="email">Enter the e-mail</label>
      <input
        type="email"
        id="email"
        v-for="(obj, index) in emails"
        :key="index"
        v-model="obj.value"
        class="mb-3"
      />
      <button @click.prevent="addEmail" class="btn btn-info mt-1 mb-1">+</button>
      <button @click.prevent="onSubmit()" class="btn btn-primary mt-5">Add to the list</button>
      <hr />
    </form>
  </div>
</template>

<script>
import contactlist from "@/components/ContactList";
import InputForms from "@/components/InputForms";
import List from "@/components/List";
import contactlistVue from "../views/contactlist.vue";

export default {
  components: {
    List
  },
  data() {
    return {
      numbers: [
        {
          value: ""
        }
      ],
      addresses: [
        {
          value: ""
        }
      ],
      title: "",
      emails: [
        {
          value: ""
        }
      ],
      content: ""
    };
  },
  methods: {
    addNumber() {
      if (this.numbers[this.numbers.length - 1].value.trim()) {
        this.numbers.push({ value: "" });
      } else {
        this.$alert("Input cannot be blank. Please doublecheck your input.");
      }
    },
    addAddress() {
      if (this.addresses[this.addresses.length - 1].value.trim()) {
        this.addresses.push({ value: "" });
      } else {
        this.$alert("Input cannot be blank. Please doublecheck your input.");
      }
    },
    addEmail() {
      if (this.emails[this.emails.length - 1].value.trim()) {
        this.emails.push({ value: "" });
      } else {
        this.$alert("Input cannot be blank. Please doublecheck your input.");
      }
    },
    onSubmit() {
      let numberValidation = this.numbers.map(el => el.value === "");
      let addressValidation = this.addresses.map(el => el.value === "");
      let emailsValidation = this.emails.map(el => el.value === "");

      let len =
        numberValidation.length +
        addressValidation.length +
        emailsValidation.length;

      for (let i = 0; i < len; i++) {
        if (
          numberValidation[i] === true ||
          addressValidation[i] === true ||
          emailsValidation[i] === true ||
          this.title.trim() === ""
        ) {
          return this.$alert("you have an empty space");
          break;
        }
      }
      const newContact = {
        name: this.title,
        number: this.numbers,
        address: this.addresses,
        email: this.emails
      };

      this.$emit("newcontact", newContact);

      this.title = "";
      this.numbers = [{ value: "" }];
      this.addresses = [{ value: "" }];
      this.emails = [{ value: "" }];
    }
  }
};
</script>
