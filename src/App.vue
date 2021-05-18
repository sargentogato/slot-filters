<template>
  <div id="app">
    <h3 v-show="showMessage">{{ messageClosed }}</h3>
    <modal-bootstrap>
      <template v-slot:headerSlot>
        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
        <button
          type="button"
          class="close"
          data-dismiss="modal"
          aria-label="Close"
          v-on:click="closedModalMessage"
        >
          x
        </button>
      </template>
      <template v-slot:bodySlot>
        <h1>Cambio de moneda</h1>
        <input type="text" v-model="inputText" class="col-3" />
        <p>
          El cambio de {{ messageInput }} en dolares son {{ currencyExchange }}
        </p>
      </template>
      <template v-slot:footerSlot>
        <button
          type="button"
          class="btn btn-secondary"
          data-dismiss="modal"
          v-on:click="closedModalMessage"
        >
          Close
        </button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </template>
    </modal-bootstrap>
  </div>
</template>

<script>
import modalBootstrap from "./components/modalBootstrap.vue";
export default {
  name: "app",
  components: { modalBootstrap },
  data() {
    return {
      inputText: "",
      regex: /^[0-9]*$/,
      messageClosed: "Has cerrado el Modal",
      showMessage: false,
    };
  },
  computed: {
    messageInput() {
      const checkNumber = this.regex.test(this.inputText);
      if (checkNumber) {
        return `${this.inputText}€`;
      } else {
        return this.alertMessage();
      }
    },
    currencyExchange() {
      let euros = this.inputText * 1.23;
      return euros + "$";
    },
  },
  methods: {
    alertMessage() {
      this.inputText = "";
      alert("You have to text only numbers");
    },
    clean() {
      const btn = document.querySelectorAll("button");

      for (const button of btn) {
        button.addEventListener("click", () => {
          return (this.inputText = "");
        });
      }
    },
    closedModalMessage() {
      this.showMessage = true;

      setTimeout(() => {
        this.showMessage = false;
      }, 3000);
    },
  },
  mounted() {
    this.clean();
  },
};
</script>

<style scoped>
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: tomato;
  height: 100vh;
}

h3 {
  margin-block-end: 1rem;
}
</style>
