 <template>
  <div>
    <h2>Contact List</h2>

    <router-link to="/">Home</router-link>

    <hr />

    <InputForms @newcontact="handler" />
    <List :contacts="newContact.arrayOfData" @contactToDelete="deleteThisContact" />
  </div>
</template>



<script>
import contactlist from "@/components/ContactList";
import InputForms from "@/components/InputForms";
import List from "@/components/List";

export default {
  name: "App",
  data() {
    return {
      newContact: {
        arrayOfData: []
      }
    };
  },
  components: {
    InputForms,
    List
  },
  methods: {
    handler(obj) {
      this.newContact.arrayOfData.push(obj);
    },
    deleteThisContact(index) {
      this.newContact.arrayOfData.splice(index);
    }
  }
};
</script>
