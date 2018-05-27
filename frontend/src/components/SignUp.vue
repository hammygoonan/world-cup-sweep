<template>
  <div>
    <div class="modal" :class="{ 'is-active': showModal }">
      <div class="modal-background"></div>
      <div class="modal-card">
        <header class="modal-card-head">
          <p class="modal-card-title">Sign Up</p>
          <button class="delete" aria-label="close" @click="close"></button>
        </header>
        <section class="modal-card-body">
          <div class="field">
            <label class="label">Name</label>
            <div class="control">
              <input class="input" type="text" placeholder="Your name" v-model="name">
            </div>
          </div>
        </section>
        <footer class="modal-card-foot">
          <button class="button is-success" @click="submit">Submit</button>
        </footer>
      </div>
    </div>
    <button class="button" @click="close">Sign Up</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'sign-up',
  data() {
    return {
      name: '',
      showModal: true,
    };
  },
  methods: {
    submit() {
      axios.post('/user/signup/', { name: this.name });
    },
    close() {
      this.showModal = !this.showModal;
    },
  },
};
</script>
