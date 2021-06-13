<template>
  <div class="modal-block">
    <button
      @click="showModal()"
      class="open-button"
      type="button"
    >
      {{ openButtonText }}
    </button>
    <div
      v-if="show"
      :class="'modal-content ' + type"
    >
      <button
        @click="showModal()"
        class="close-button"
        type="button"
      >
        <img src="../assets/close_icon.svg" alt="">
      </button>
      <div class="top">
        <h3>
          {{ title }}
        </h3>
        <p>
          {{ text }}
        </p>
      </div>
      <div
          class="buttons"
      >
        <button
            v-for="button in buttons"
            :key="button.name"
            type="button"
            :class="button.type"
            @click="showModal()"
        >
          {{ button.name }}
        </button>
      </div>
    </div>
    <div v-if="showOverlay" class="overlay"></div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    title: String,
    text: String,
    type: String,
    buttons: Array,
    openButtonText: String
  },
  data: function () {
    return {
      show: false,
      showOverlay: false
    }
  },
  methods: {
    showModal: function () {
      this.show = !this.show;
      this.showOverlay = !this.showOverlay;
    }
  }
}
</script>

<style scoped>
  .open-button {
    padding: 12px 80px;
    font-size: 16px;
    line-height: 150%;
    background-color: #4299E1;
    border-radius: 100px;
    border-width: 0;
    color: #fff;
    cursor: pointer;
    transition: .25s;
  }
  .open-button:hover {
    filter: saturate(0.5);
  }
  .modal-content {
    position: fixed;
    top: 50%;
    left: 50%;
    z-index: 10;
    transform: translate(-50%, -50%);
    display: inline-block;
    background-color: #FFFFFF;
    box-shadow: 0 10px 15px rgba(44, 82, 130, 0.1),
                0 4px 6px rgba(44, 82, 130, 0.05);
    border-radius: 8px;
  }
  .modal-content .top {
    padding: 40px 50px 50px 104px;
  }
  .modal-content h3 {
    position: relative;
    margin-top: 0;
    margin-bottom: 8px;
    font-weight: 600;
    font-size: 20px;
    line-height: 150%;
    color: #1A202C;
  }
  .modal-content h3:before {
    content: '';
    position: absolute;
    left: -16px;
    top: 50%;
    transform: translate(-100%, -50%);
    width: 48px;
    height: 48px;
    border-radius: 50%;
    background-position: center 5px;
    background-repeat: no-repeat;
  }
  .modal-content p {
    max-width: 370px;
    margin-top: 0;
    margin-bottom: 0;
    font-size: 16px;
    line-height: 150%;
    color: #4A5568;
  }
  .close-button {
    position: absolute;
    right: 24px;
    top: 24px;
    z-index: 2;
    padding: 0;
    border-width: 0;
    background-color: transparent;
    cursor: pointer;
  }
  .modal-content .buttons {
    min-height: 96px;
    padding: 24px;
    background-color: #F5F5F7;
    border-radius: 0 0 8px 8px;
    text-align: right;
  }
  .modal-content .buttons button {
    padding: 12px 80px;
    font-size: 16px;
    line-height: 150%;
    border-radius: 100px;
    border: 1px solid transparent;
    color: #fff;
    cursor: pointer;
    transition: .25s;
  }
  .modal-content .buttons button:not(:last-of-type) {
    margin-right: 16px;
  }
  .modal-content .buttons .white {
    padding-left: 50px;
    padding-right: 50px;
    background-color: transparent;
    color: #2C5282;
    border: 1px solid #2C5282;
  }
  .modal-content .buttons .red {
    padding-left: 100px;
    padding-right: 100px;
    background-color: #C81E1E;
  }
  .modal-content .buttons .blue {
    padding-left: 80px;
    padding-right: 80px;
    background-color: #4299E1;
  }
  .modal-content.error h3:before {
    background-color: #FED7D7;
    background-image: url("data:image/svg+xml,%3Csvg width='32' height='29' viewBox='0 0 32 29' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M15.876 3.032a.291.291 0 00-.108.114L2.054 26.48a.352.352 0 00-.004.366c.032.06.074.1.108.12.03.02.068.034.132.034h27.426a.24.24 0 00.132-.034.326.326 0 00.11-.12.353.353 0 00-.006-.366L16.24 3.146a.293.293 0 00-.108-.114.26.26 0 00-.128-.032.26.26 0 00-.128.032zm2.088-.9a2.26 2.26 0 00-3.92 0L.33 25.466C-.584 27.022.512 29 2.29 29h27.426c1.778 0 2.876-1.98 1.96-3.534L17.964 2.132z' fill='%23C53030'/%3E%3Cpath d='M14.004 23a2 2 0 114.001 0 2 2 0 01-4.001 0zm.196-12.01a1.807 1.807 0 011.8-2 1.81 1.81 0 011.8 2l-.7 7.014a1.104 1.104 0 01-2.2 0l-.7-7.014z' fill='%23C53030'/%3E%3C/svg%3E");
  }
  .modal-content.info h3:before {
    background-color: #D7F5FE;
    background-image: url("data:image/svg+xml,%3Csvg width='32' height='29' viewBox='0 0 32 29' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M15.876 3.032a.291.291 0 00-.108.114L2.054 26.48a.352.352 0 00-.004.366c.032.06.074.1.108.12.03.02.068.034.132.034h27.426a.24.24 0 00.132-.034.326.326 0 00.11-.12.353.353 0 00-.006-.366L16.24 3.146a.293.293 0 00-.108-.114.26.26 0 00-.128-.032.26.26 0 00-.128.032zm2.088-.9a2.26 2.26 0 00-3.92 0L.33 25.466C-.584 27.022.512 29 2.29 29h27.426c1.778 0 2.876-1.98 1.96-3.534L17.964 2.132z' fill='%232F80ED'/%3E%3Cpath d='M14.004 23a2 2 0 114.001 0 2 2 0 01-4.001 0zm.196-12.01a1.807 1.807 0 011.8-2 1.81 1.81 0 011.8 2l-.7 7.014a1.104 1.104 0 01-2.2 0l-.7-7.014z' fill='%232F80ED'/%3E%3C/svg%3E");
  }
  .modal-content.warning h3:before {
    background-color: #FEF1D7;
    background-image: url("data:image/svg+xml,%3Csvg width='32' height='29' viewBox='0 0 32 29' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M15.876 3.032a.291.291 0 00-.108.114L2.054 26.48a.352.352 0 00-.004.366c.032.06.074.1.108.12.03.02.068.034.132.034h27.426a.24.24 0 00.132-.034.326.326 0 00.11-.12.353.353 0 00-.006-.366L16.24 3.146a.293.293 0 00-.108-.114.26.26 0 00-.128-.032.26.26 0 00-.128.032zm2.088-.9a2.26 2.26 0 00-3.92 0L.33 25.466C-.584 27.022.512 29 2.29 29h27.426c1.778 0 2.876-1.98 1.96-3.534L17.964 2.132z' fill='%23F2994A'/%3E%3Cpath d='M14.004 23a2 2 0 114.001 0 2 2 0 01-4.001 0zm.196-12.01a1.807 1.807 0 011.8-2 1.81 1.81 0 011.8 2l-.7 7.014a1.104 1.104 0 01-2.2 0l-.7-7.014z' fill='%23F2994A'/%3E%3C/svg%3E");
  }
  .modal-content.success h3:before {
    background-color: #E6FED7;
    background-image: url("data:image/svg+xml,%3Csvg width='32' height='29' viewBox='0 0 32 29' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M15.876 3.032a.291.291 0 00-.108.114L2.054 26.48a.352.352 0 00-.004.366c.032.06.074.1.108.12.03.02.068.034.132.034h27.426a.24.24 0 00.132-.034.326.326 0 00.11-.12.353.353 0 00-.006-.366L16.24 3.146a.293.293 0 00-.108-.114.26.26 0 00-.128-.032.26.26 0 00-.128.032zm2.088-.9a2.26 2.26 0 00-3.92 0L.33 25.466C-.584 27.022.512 29 2.29 29h27.426c1.778 0 2.876-1.98 1.96-3.534L17.964 2.132z' fill='%23219653'/%3E%3Cpath d='M14.004 23a2 2 0 114.001 0 2 2 0 01-4.001 0zm.196-12.01a1.807 1.807 0 011.8-2 1.81 1.81 0 011.8 2l-.7 7.014a1.104 1.104 0 01-2.2 0l-.7-7.014z' fill='%23219653'/%3E%3C/svg%3E");
  }
  .overlay {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 8;
    background-color: rgba(0, 0, 0, .4);
  }
</style>