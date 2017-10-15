<template>
  <div id="helloworld" class="hello">
    <h1>{{ msg }}</h1>
    <row type="flex" justify="center" align="middle" class="code-row-bg">
      <Col span="8">
        <div class="bg">
          <ul v-for="nums in matrix">
            <li class="box" v-for="num in nums" v-text="num"></li>
          </ul>
        </div>
      </Col>
    </row>
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
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0]
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



.box{
  width: 50px;
  height: 50px;
  margin: 2px;
  background-color: orange;
  font-size: 3.6em;
  color: red;
  font-weight: bold;
  border-radius:8px;
  position: relative;
}

.bg{
  width: 250px;
  height: 250px;
  background-color: burlywood;
  margin:30px auto;
  border-radius:10px;
  position: absolute;
}
</style>
