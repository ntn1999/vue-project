<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(favorite)' : '' }}</h2>
    <button @click="toggleIsFavorite">Change Favorite</button>
    <button @click="toggleDetails">Show Details</button>
  </li>
  <ul v-if="detailsAreVisible">
    <li><strong>Phone:</strong>{{ phoneNumber }}</li>
    <li><strong>Email:</strong>{{ emailAddress }}</li>
  </ul>
</template>
<script>
export default {
  name: 'FriendContact',
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFavorite: {
      type: Boolean,
      required: false,
    },
  },
  emits: ['toggle-favorite'],
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleIsFavorite() {
      this.$emit('toggle-favorite', this.id);
    },
  },
};
</script>
