<template>
  <base-dialog v-if="!inputIsValid" title="Input Not Valid!" @confirmError="confirmError">
    <p>Atleast one input is not valid.</p>
    <p>Please check all input</p>
    <template #actions>
       <base-button @click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="title" ref="inputTitle" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          name="description"
          id="description"
          row="3"
          ref="inputDescription"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" name="link" id="link" ref="inputLink" />
      </div>
      <div>
        <base-button type="submit">Submit</base-button>
      </div>
    </form>
  </base-card>
</template>
<script>
export default {
  data() {
    return {
      inputIsValid: true,
    };
  },
  inject: ['addResource'],
  methods: {
    submitData() {
      const enteredTitle = this.$refs.inputTitle.value;
      const enteredDescription = this.$refs.inputDescription.value;
      const enteredLink = this.$refs.inputLink.value;

      if (
        enteredTitle.trim() === '' ||
        enteredDescription.trim() === '' ||
        enteredLink.trim() === ''
      ) {
        this.inputIsValid = false;
        return;
      }

      const resource = {
        id: new Date().toISOString(),
        title: enteredTitle,
        description: enteredDescription,
        link: enteredLink,
      };
      this.addResource(resource);
    },
    confirmError(){
        this.inputIsValid = true;
    }
  },
};
</script>
<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
