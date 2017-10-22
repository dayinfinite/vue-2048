<template>
  <div id="helloworld" class="hello">
    <h1>{{ msg }}</h1>
    <div class="container">
      <div class="game-container">
          <!-- <div class="game-message game-over"></div> -->
          <div class="grid-container">
            <div class="grid-row">
              <div class="grid-cell"></div>
              <div class="grid-cell"></div>
              <div class="grid-cell"></div>
              <div class="grid-cell"></div>              
            </div>
            <div class="grid-row">
              <div class="grid-cell"></div>
              <div class="grid-cell"></div>
              <div class="grid-cell"></div>
              <div class="grid-cell"></div>              
            </div>
            <div class="grid-row">
              <div class="grid-cell"></div>
              <div class="grid-cell"></div>
              <div class="grid-cell"></div>
              <div class="grid-cell"></div>              
            </div>
            <div class="grid-row">
              <div class="grid-cell"></div>
              <div class="grid-cell"></div>
              <div class="grid-cell"></div>
              <div class="grid-cell"></div>              
            </div>                        
          </div>
        </div>
        <div class="tile-container" v-for="(vs, k1) in matrix" :key="k1">
          <div v-if="v" class="tile" :class=" 'tile-position-' + k2 + '-' + k1 " v-for="(v, k2) in vs" :key="k2">
            <div class="tile-inner">{{v}}</div>
          </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'helloworld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      value: [0, 100],
      matrix: [
        [0, 2, 2, 8],
        [0, 16, 0, 64],
        [32, 0, 32, 8],
        [0, 16, 2, 4]
      ]
    }
  },
  mounted () {
    window.addEventListener('keydown', this.keyevent.bind(this))
  },
  methods: {
    keyevent: function (e) {
      var emptySet = []
      var size = 4
      for (var i = 0; i < size; i++) {
        for (var j = 0; j < size; j++) {
          if (this.matrix[i][j] === 0) {
            emptySet.push([i, j])
          }
        }
      }
      if (e.keyCode === 37) {
        this.KeyLeft()
      }
      if (e.keyCode === 38) {
        this.KeyUp(emptySet)
      }
      if (e.keyCode === 39) {
        this.KeyRight()
      }
      if (e.keyCode === 40) {
        this.KeyDown()
      }
    },
    KeyLeft: function () {
      var flag = Math.floor(Math.random())
      alert(flag)
    },
    KeyUp: function (emptySet) {
      var flag = Math.floor(Math.random() * emptySet.length)
      console.log(emptySet[flag])
    },
    KeyRight: function () {
      alert('KeyRight')
    },
    KeyDown: function () {
      alert('KeyDown')
    },
    random2_4 () {
      return Math.floor(Math.random * 100) >= 50 ? 4 : 2
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
  text-align: center;
}

a {
  color: #42b983;
}

div {
  display: block;
}
.container {
  width: 500px;
  margin: 0 auto;
}

.game-container {
  margin-top: 25px;
}

.game-message {
  display: none;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background: rgba(238, 228, 218, 0.5);
  z-index: 100;
  text-align: center;
  -webkit-animation: fade-in 800ms ease 1200ms;
  -moz-animation: fade-in 800ms ease 1200ms;
  animation: fade-in 800ms ease 1200ms;
  -webkit-animation-fill-mode: both;
  -moz-animation-fill-mode: both;
  animation-fill-mode: both;
}

.grid-container {
    margin-top: 40px;
    position: relative;
    padding: 15px;
    cursor: default;
    touch-action: none;
    background: #bbada0;
    border-radius: 6px;
    width: 500px;
    height: 500px;
    box-sizing: border-box;
    position: absolute;
}

.grid-cell {
    width: 106.25px;
    height: 106.25px;
    margin-right: 15px;
    float: left;
    border-radius: 3px;
    background: rgba(238, 228, 218, 0.35);  
}

.grid-cell:last-child {
  margin-right: 0; 
}

.grid-row {
  margin-bottom: 15px;
}

.grid-row:last-child {
    margin-bottom: 0;
}

.grid-row:after {
    content: "";
    display: block;
    clear: both;
}

.tile-container {
  position: absolute;
  z-index: 2;
}

.game-message {
  display: none;
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background: rgba(238, 228, 218, 0.5);
    z-index: 100;
    text-align: center;
    -webkit-animation: fade-in 800ms ease 1200ms;
    -moz-animation: fade-in 800ms ease 1200ms;
    animation: fade-in 800ms ease 1200ms;
    -webkit-animation-fill-mode: both;
    -moz-animation-fill-mode: both;
    animation-fill-mode: both;
}

.game-over {
  display: block;
}

.tile-container {
  position: absolute;
  right: 73%;
  top: 50%;
  z-index: 2; 
}

.tile, .tile .tile-inner {
  width: 107px;
  height: 107px;
  line-height: 116.25px; }
.tile.tile-position-0-0 {
  -webkit-transform: translate(0px, 0px);
  -moz-transform: translate(0px, 0px);
  transform: translate(0px, 0px); }
.tile.tile-position-0-1 {
  -webkit-transform: translate(0px, 121px);
  -moz-transform: translate(0px, 121px);
  transform: translate(0px, 121px); }
.tile.tile-position-0-2 {
  -webkit-transform: translate(0px, 242px);
  -moz-transform: translate(0px, 242px);
  transform: translate(0px, 242px); }
.tile.tile-position-0-3 {
  -webkit-transform: translate(0px, 363px);
  -moz-transform: translate(0px, 363px);
  transform: translate(0px, 363px); }
.tile.tile-position-1-0 {
  -webkit-transform: translate(121px, 0px);
  -moz-transform: translate(121px, 0px);
  transform: translate(121px, 0px); }
.tile.tile-position-1-1 {
  -webkit-transform: translate(121px, 121px);
  -moz-transform: translate(121px, 121px);
  transform: translate(121px, 121px); }
.tile.tile-position-1-2 {
  -webkit-transform: translate(121px, 242px);
  -moz-transform: translate(121px, 242px);
  transform: translate(121px, 242px); }
.tile.tile-position-1-3 {
  -webkit-transform: translate(121px, 363px);
  -moz-transform: translate(121px, 363px);
  transform: translate(121px, 363px); }
.tile.tile-position-2-0 {
  -webkit-transform: translate(242px, 0px);
  -moz-transform: translate(242px, 0px);
  transform: translate(242px, 0px); }
.tile.tile-position-2-1 {
  -webkit-transform: translate(242px, 121px);
  -moz-transform: translate(242px, 121px);
  transform: translate(242px, 121px); }
.tile.tile-position-2-2 {
  -webkit-transform: translate(242px, 242px);
  -moz-transform: translate(242px, 242px);
  transform: translate(242px, 242px); }
.tile.tile-position-2-3 {
  -webkit-transform: translate(242px, 363px);
  -moz-transform: translate(242px, 363px);
  transform: translate(242px, 363px); }
.tile.tile-position-3-0 {
  -webkit-transform: translate(363px, 0px);
  -moz-transform: translate(363px, 0px);
  transform: translate(363px, 0px); }
.tile.tile-position-3-1 {
  -webkit-transform: translate(363px, 121px);
  -moz-transform: translate(363px, 121px);
  transform: translate(363px, 121px); }
.tile.tile-position-3-2 {
  -webkit-transform: translate(363px, 242px);
  -moz-transform: translate(363px, 242px);
  transform: translate(363px, 242px); }
.tile.tile-position-3-3 {
  -webkit-transform: translate(363px, 363px);
  -moz-transform: translate(363px, 363px);
  transform: translate(363px, 363px); }

.tile {
  position: absolute;
  -webkit-transition: 100ms ease-in-out;
  -moz-transition: 100ms ease-in-out;
  transition: 100ms ease-in-out;
  -webkit-transition-property: -webkit-transform;
  -moz-transition-property: -moz-transform;
  transition-property: transform; }
  .tile .tile-inner {
    border-radius: 3px;
    background: #eee4da;
    text-align: center;
    font-weight: bold;
    z-index: 10;
    font-size: 55px; }
  .tile.tile-2 .tile-inner {
    background: #eee4da;
    box-shadow: 0 0 30px 10px rgba(243, 215, 116, 0), inset 0 0 0 1px rgba(255, 255, 255, 0); }
  .tile.tile-4 .tile-inner {
    background: #ede0c8;
    box-shadow: 0 0 30px 10px rgba(243, 215, 116, 0), inset 0 0 0 1px rgba(255, 255, 255, 0); }
  .tile.tile-8 .tile-inner {
    color: #f9f6f2;
    background: #f2b179; }
  .tile.tile-16 .tile-inner {
    color: #f9f6f2;
    background: #f59563; }
  .tile.tile-32 .tile-inner {
    color: #f9f6f2;
    background: #f67c5f; }
  .tile.tile-64 .tile-inner {
    color: #f9f6f2;
    background: #f65e3b; }
  .tile.tile-128 .tile-inner {
    color: #f9f6f2;
    background: #edcf72;
    box-shadow: 0 0 30px 10px rgba(243, 215, 116, 0.2381), inset 0 0 0 1px rgba(255, 255, 255, 0.14286);
    font-size: 45px; }
    @media screen and (max-width: 520px) {
      .tile.tile-128 .tile-inner {
        font-size: 25px; } }
  .tile.tile-256 .tile-inner {
    color: #f9f6f2;
    background: #edcc61;
    box-shadow: 0 0 30px 10px rgba(243, 215, 116, 0.31746), inset 0 0 0 1px rgba(255, 255, 255, 0.19048);
    font-size: 45px; }
    @media screen and (max-width: 520px) {
      .tile.tile-256 .tile-inner {
        font-size: 25px; } }
  .tile.tile-512 .tile-inner {
    color: #f9f6f2;
    background: #edc850;
    box-shadow: 0 0 30px 10px rgba(243, 215, 116, 0.39683), inset 0 0 0 1px rgba(255, 255, 255, 0.2381);
    font-size: 45px; }
    @media screen and (max-width: 520px) {
      .tile.tile-512 .tile-inner {
        font-size: 25px; } }
  .tile.tile-1024 .tile-inner {
    color: #f9f6f2;
    background: #edc53f;
    box-shadow: 0 0 30px 10px rgba(243, 215, 116, 0.47619), inset 0 0 0 1px rgba(255, 255, 255, 0.28571);
    font-size: 35px; }
    @media screen and (max-width: 520px) {
      .tile.tile-1024 .tile-inner {
        font-size: 15px; } }
  .tile.tile-2048 .tile-inner {
    color: #f9f6f2;
    background: #edc22e;
    box-shadow: 0 0 30px 10px rgba(243, 215, 116, 0.55556), inset 0 0 0 1px rgba(255, 255, 255, 0.33333);
    font-size: 35px; }
    @media screen and (max-width: 520px) {
      .tile.tile-2048 .tile-inner {
        font-size: 15px; } }
  .tile.tile-super .tile-inner {
    color: #f9f6f2;
    background: #3c3a32;
    font-size: 30px; }
    @media screen and (max-width: 520px) {
      .tile.tile-super .tile-inner {
        font-size: 10px; } }
</style>
