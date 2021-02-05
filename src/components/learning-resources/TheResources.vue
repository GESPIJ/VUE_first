<template>
  <base-card>
    <base-button
      @click="changeSelected('stored-resources')"
      :class="storeResourceButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="changeSelected('add-resource')"
      :class="addResourceButtonMode"
      >Add Resource</base-button
    >
    <component :is="selected"></component>
  </base-card>
</template>

<script>
import StoredResources from './StoredResources';
import AddResource from './AddResource';
export default {
  components: {
    StoredResources,
    AddResource
  },
  provide() {
    return {
      resources: this.storedResources,
      add: this.addElement,
      deleteResource: this.deleteElement
    };
  },
  data() {
    return {
      selected: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official guide',
          description: 'Official VUE documentation',
          link: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google',
          link: 'https://google.org'
        }
      ]
    };
  },
  computed: {
    addResourceButtonMode() {
      return this.selected == 'add-resource' ? null : 'flat';
    },
    storeResourceButtonMode() {
      return this.selected == 'stored-resources' ? null : 'flat';
    }
  },
  methods: {
    changeSelected(select) {
      this.selected = select;
    },
    addElement(title, desc, url) {
      console.log('Estoy ejecutando el metodo addresource');
      this.storedResources.push({ id: title, title, desc, url });
      this.selected = 'stored-resources';
      console.log(this.storedResources);
    },
    deleteElement(id) {
      console.log('Entrando en delete element');
      const index = this.storedResources.findIndex(res => res.id == id);
      this.storedResources.splice(index, 1);
      //const newStore = this.storedResources.filter(res => res.id != id);
      //this.storedResources = newStore;
    }
  }
};
</script>
