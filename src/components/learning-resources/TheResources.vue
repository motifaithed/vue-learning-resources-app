<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')" :mode="storedResBtnMode"
      >Stored Resources</base-button
    >
    <base-button @click="setSelectedTab('add-resource')" :mode="addResBtnMode"
      >Add Resource</base-button
    >
  </base-card>
  <component :is="selectedTab"></component>
</template>
<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';
export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'Official vue guide docs',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'search everything',
          link: 'https://www.google.com',
        },
      ]
    };
  },
  provide(){
    return{
        resources: this.storedResources
    }
  },
  computed:{
    storedResBtnMode(){
      return  this.selectedTab === 'stored-resources' ? null : 'flat';    
    },
    addResBtnMode(){
        return  this.selectedTab === 'add-resource' ? null : 'flat';
    }
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
  },
};
</script>
