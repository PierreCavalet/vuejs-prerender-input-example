<template>
  <div class="hello">
    <h1>prerender</h1>
    <input v-model="foo" v-prerender id="foo" type="text" />
    <input v-model="bar" v-prerender id="bar" type="text" />
  </div>
</template>

<script>

export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      foo: '',
      bar: '',
      prerenderFocusId: null
    }
  },
  created () {
    if (document.getElementById('foo')) {
      this.foo = document.getElementById('foo').value
    }
    if (document.getElementById('bar')) {
      this.bar = document.getElementById('bar').value
    }
    this.prerenderFocusId = document.activeElement.id
  },
  mounted () {
    if (this.prerenderFocusId) {
      document.getElementById(this.prerenderFocusId).focus()
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
}

a {
  color: #42b983;
}
</style>
