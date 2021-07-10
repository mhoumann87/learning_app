<template>
  <base-dialog v-if="inputIsInvalid" title="Invalid Input" @close="closeDialog">
    <template #default>
      <p>Unfortunally, one or more of the inputs are invalid.</p>
      <p>Please check your inputs and make sure that your input are valid.</p>
    </template>

    <template #actions>
      <base-button @click="closeDialog">Ok</base-button>
    </template>
  </base-dialog>

  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" id="title" name="title" ref="titleInput" />
      </div>

      <div class="form-control">
        <label for="description">Discription</label>
        <textarea
          name="description"
          id="description"
          rows="3"
          ref="descInput"
        ></textarea>
      </div>

      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" name="link" id="link" ref="linkInput" />
      </div>

      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
  export default {
    inject: ['addRecousce'],
    data() {
      return {
        inputIsInvalid: false,
      };
    },
    methods: {
      submitData() {
        const enteredTitle = this.$refs.titleInput.value;
        const enteredDescription = this.$refs.descInput.value;
        const enteredLink = this.$refs.linkInput.value;

        if (
          enteredTitle.trim() === '' ||
          enteredDescription.trim() === '' ||
          enteredLink.trim === ''
        ) {
          this.inputIsInvalid = true;
          return;
        }

        // console.log(enteredLink, enteredTitle, enteredDescription);
        this.addRecousce(enteredTitle, enteredDescription, enteredLink);
      },
      closeDialog() {
        this.inputIsInvalid = false;
      },
    },
  };
</script>

<style scoped>
  label {
    font-weight: bold;
    display: block;
    margin-bottom: 0.5rem;
  }

  :is(input, textarea) {
    display: block;
    width: 100%;
    font: inherit;
    padding: 0.5rem;
    border: 1px solid #ccc;
  }

  :is(input, textarea):focus {
    outline: none;
    border-color: #3a0061;
    background-color: #f7ebff;
  }

  .form-control {
    margin: 1rem 0;
  }
</style>
