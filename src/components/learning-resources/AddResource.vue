<template>
  <base-dialog v-if="inputInvalid" @close="inputInvalid = false">
    <template #default>
      <p>Unfortunately at least one input value is invalid</p>
      <p>Check all inputs and verified you entered at least one character</p>
    </template>
    <template #actions>
      <base-button @click="inputInvalid = false">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitEntry">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="titulo" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          type="text"
          ref="descripcion"
        />
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" ref="link" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ['add'],
  data() {
    return {
      inputInvalid: false
    };
  },
  methods: {
    submitEntry() {
      console.log('Entro en submitentry');
      const titulo = this.$refs.titulo.value;
      const descripcion = this.$refs.descripcion.value;
      const link = this.$refs.link.value;

      if (
        titulo.trim() === '' ||
        descripcion.trim() === '' ||
        link.trim() === ''
      ) {
        this.inputInvalid = true;
        return;
      }

      this.add(titulo, descripcion, link);
    }
  }
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
</style>
