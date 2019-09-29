<template>
  <div id="app">
    <header>Click Speed Contest ⏱️</header>
    <main @click="counter += 1">
      <div class="start-button"><transition name="pop">
        <button
          class="bttn-fill bttn-md bttn-primary"
          v-on:click="startClickContest(); countDownTimer()"
          v-show="showBtn"
        >Start click contest</button></transition>
      </div>
      <transition name="pop">
      <div v-show="btnClicked" class="stats">
        <div class="result">
          <div class="time">Il reste
            <span class="result-visual">{{countDown}}s</span>
          </div>
          <div class="click-counts">Vous avez cliquez
            <span class="result-visual">{{counter}}</span> fois
          </div>
          <div class="cps">Cela représente
            <span class="result-visual">{{counter / plage}} CPS</span>
          </div>
        </div>
      </div></transition>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      counter: 0,
      plage: 10,
      btnClicked: false,
      showBtn: true,
      placement: -1,
      countDown: 10
    };
  },
  methods: {
    startClickContest: function() {
      this.showBtn = false;
      this.btnClicked = true;
      this.counter = 0;
      this.placement = 5;

      this.clickContest();
    },
    clickContest: function() {
      setTimeout(() => {
        this.showBtn = true;
        this.score = this.counter;
        this.placement = -1;
        this.btnClick = false;
      }, this.plage * 1000);
    },
    countDownTimer() {
      if (this.countDown > 0) {
        setTimeout(() => {
          this.countDown -= 1;
          this.countDownTimer();
        }, 1000);
      }
    }
  }
};
</script>

<style lang="scss" scoped>
@import url(https://cdn.jsdelivr.net/gh/ganapativs/bttn.css/dist/standalone/fill.css);
@import url(https://fonts.googleapis.com/css?family=Roboto+Mono:400,700&display=swap);
 @import url(https://fonts.googleapis.com/css?family=Roboto:400,500&display=swap);
body {
  font-family: "Roboto" ,Roboto, -apple-system, BlinkMacSystemFont, "Segoe UI", Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  user-select: none;
  font-weight: 500;
}

header {
  font-size: 32px;
  text-align: center;
  margin: 2rem;
  text-shadow: 2px 3px 6px rgba(0, 0, 0, 0.2);
    font-family: "Roboto" ,Roboto, -apple-system, BlinkMacSystemFont, "Segoe UI",Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
font-weight: 500;
user-select: none;
}
.bttn-fill {
font-family: 'Roboto',Roboto, -apple-system, BlinkMacSystemFont, "Segoe UI",Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;;
font-style: normal;
font-weight: 500;
}
main {
  display: flex;
  margin-top: 30vh;
  flex-direction: column;
  align-items: center;
height: 100vh;
user-select: none;
}

.result-visual {
  font-style: normal;
  font-weight: bold;
  font-size: 20px;
  color: #FBFF50;
}

.result {
  margin-top: 2.5rem;
  background: #A4B8FF;
  color: white;
  font-family: "Roboto Mono", Roboto Mono, monospace;
  box-shadow: 0px 16px 40px rgba(0, 0, 0, 0.16);
  border-radius: 4px;
  padding: 13px;
  font-size: 20px;
}

.pop-leave {
transition: opacity 2s;

opacity: 1;
} 
.pop-leave-active {
opacity: 0;
transition: opacity 2s;
} 

.pop-leave-to {
  opacity:0;
}

.pop-enter-active {
    /* -webkit-animation-duration: 0.75s;
  animation-duration: 0.75s;
  -webkit-animation-name: bounceIn;
  animation-name: bounceIn; */
    -webkit-animation-name: fadeInUp;
  animation-name: fadeInUp;
  animation-duration: 0.75s;
} 
/* .pop-enter, .pop-leave-to /* .fade-leave-active below version 2.1.8{
  opacity: 0;
} */

/* .pop-leave-active, .pop-leave {
transition: opacity 2s;
} */

@-webkit-keyframes fadeInUp {
  from {
    opacity: 0;
    -webkit-transform: translate3d(0, 100%, 0);
    transform: translate3d(0, 100%, 0);
  }

  to {
    opacity: 1;
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
  }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    -webkit-transform: translate3d(0, 100%, 0);
    transform: translate3d(0, 100%, 0);
  }

  to {
    opacity: 1;
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
  }
}

.fadeInUp {
  -webkit-animation-name: fadeInUp;
  animation-name: fadeInUp;
}
</style>
