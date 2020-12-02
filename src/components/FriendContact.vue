<template>
  <li>
    <h2>{{ name }} {{ isFavourite ? "(Favourite)" : "" }}</h2>
    <button @click="$emit('toggle-favourite', this.id)">Toggle favourite</button>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
    <button @click="$emit('delete', id)">Delete</button>
  </li>
</template>

<script>
export default {
  // props: ['name', 'phoneNumber', 'emailAddress', 'isFavorite'],
  props: {
    id:{
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true
    },
    emailAddress: {
      type: String,
      required: true
    },
    isFavourite: {
      type: Boolean,
      required: false,
      default: false
    },
  },
  emits:  ["toggle-favourite", "delete"],
 /* emits: {
    "toggle-favourite" : function(id){
      if(id){
        return true;
      }
      else{
        console.warn("Id is missing!");
        return false;
      }
    }
  },*/
  data() {
    return {
      detailsAreVisible: false,
      friendIsFavourite: this.isFavourite,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
  },
};  
</script>