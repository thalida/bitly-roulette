<template>
  <div id="app">
    <h1 class="header">a random bit.ly</h1>
    <div class="bitly-container">
      <a 
        class="bitly-link" 
        :href="'http://'+bitlyUrl" 
        v-on:click="onClick()"
        target="_blank">
        {{bitlyUrl}}
      </a>
    </div>
    <a class="footer-link" href="https://thalida.com" target="_blank">thalida</a>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      bitlyUrl: this.getBitly(),
    }
  },
  methods: {
    getRandomInt(min, max) {
      min = Math.ceil(min);
      max = Math.floor(max);
      return Math.floor(Math.random() * (max - min)) + min; //The maximum is exclusive and the minimum is inclusive
    },
    getRandomChar() {
      const alpha = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z'];
      const charIdx = this.getRandomInt(0, alpha.length);
      const makeUppercase = this.getRandomInt(0, 2);

      let char = alpha[charIdx];
      return makeUppercase ? char.toUpperCase() : char;
    },
    getBitly() {
      const numChars = 4;
      let bitlyUrl = 'bit.ly/';

      for (let i = 0; i < numChars; i += 1) {
        bitlyUrl += this.getRandomChar();
      }

      return bitlyUrl;
    },
    onClick() {
      this.bitlyUrl = this.getBitly();
    }
  }
}
</script>

<style lang="scss">
html {
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: inherit;
}

body {
  margin: 0;
  padding: 0;
}

#app {
  display: flex;
  flex-direction: column;
  padding: 64px 8px;

  background: linear-gradient(-45deg, #FFA0A0, #FF7179, #D4A0FF, #668AFF, #50AEFF);
  background-size: 500% 500%;
  -webkit-animation: Gradient 45s linear infinite;
  -moz-animation: Gradient 45s linear infinite;
  animation: Gradient 45s linear infinite;
  
  color: #fff;
  font-family: 'Signika', Helvetica, Arial, sans-serif;
  text-align: center;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

html,
body,
#app {
  height: 100%;
}

.header {
  flex: 0 0 auto;
  padding: 0;
  margin: 0;
}

.bitly-container {
  display: flex;
  flex: 1 1 auto;
}

.bitly-link {
  margin: auto;
  color: #fff;
  font-size: 48px;
  text-decoration: none;
  transition: text-shadow 400ms linear;
  text-shadow: 1px 1px 1px rgba(255, 255, 255, 0);

  &:hover {
    text-shadow: 1px 2px 3px rgba(0, 0, 0, 0.3);
  }
}

.footer-link {
  flex: 0 0 auto;
  text-decoration: none;
  transition: color 200ms linear;

  &:hover {
    color: rgba(255, 255, 255, 1);
  }
}

.header,
.footer-link {
  font-size: 16px;
  font-weight: 100;
  color: rgba(255, 255, 255, 0.7);
}


@-webkit-keyframes Gradient {
  0% {
    background-position: 0% 50%
  }
  50% {
    background-position: 100% 50%
  }
  100% {
    background-position: 0% 50%
  }
}

@-moz-keyframes Gradient {
  0% {
    background-position: 0% 50%
  }
  50% {
    background-position: 100% 50%
  }
  100% {
    background-position: 0% 50%
  }
}

@keyframes Gradient {
  0% {
    background-position: 0% 50%
  }
  50% {
    background-position: 100% 50%
  }
  100% {
    background-position: 0% 50%
  }
}
</style>
