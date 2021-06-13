<template>
  <div id="app">
    <div class="modals">
      <Modal
          title="Archive your profile?"
          text="Are you sure you want to archive your profile? You will be able to restore it."
          type="error"
          :buttons="[
          {
            name: 'Cancel',
            type: 'white'
          },
          {
            name: 'Ok',
            type: 'red'
          }
       ]"
          openButtonText="Open error modal"
      />
      <Modal
          title="Your request will be reviewed"
          text="Site administrator will review your data and respond to a request"
          type="info"
          :buttons="[
          {
            name: 'Continue',
            type: 'blue'
          }
       ]"
          openButtonText="Open info modal"
      />
      <Modal
          title="Your request will be reviewed"
          text="Site administrator will review your data and respond to a request"
          type="warning"
          openButtonText="Open warning modal"
      />
      <Modal
          title="Your request will be reviewed"
          text="Site administrator will review your data and respond to a request"
          type="success"
          openButtonText="Open success modal"
      />
    </div>
  </div>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {
    Modal
  }
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  * {
    box-sizing: border-box;
  }
  .modals {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: 24px;
    align-items: center;
    text-align: center;
    padding: 50px;
  }
</style>
