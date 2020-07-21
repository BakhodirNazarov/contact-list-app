<template>
  <div class="container mt-3">
    <div class="card p-3">
      <form class="mb-3">
        <input type="search" placeholder="Search....." v-model="search" />
      </form>
      <div>
        <ul class="list-group-flush" v-if="contacts.length">
          <li
            class="list-group-item lead d-flex justify-content-between"
            v-for="(contact,index) in filteredNames"
            :key="index"
          >
            <contact-info :contact="contact"></contact-info>
            <a href="#" @click.prevent="deleteUser(contact.name)">Delete</a>
          </li>
        </ul>
        <p v-else>Currently you have no contacts to show</p>
      </div>
    </div>
  </div>
</template>


<script>
import ContactInfo from "./ContactInfo";
export default {
  components: {
    ContactInfo
  },
  data() {
    return {
      search: ""
    };
  },
  props: ["contacts"],
  computed: {
    filteredNames() {
      return this.contacts.filter(x => {
        return x.name.toLowerCase().match(this.search.toLowerCase());
      });
    }
  },
  methods: {
    deleteUser(user) {
      let toDelete = null;
      let con = this.contacts;
      for (let i = 0; i < con.length; i++) {
        if (this.contacts[i].name === user) {
          toDelete = i;
        }
      }
      this.$emit("contactToDelete", toDelete);
    }
  }
};
</script>