<template>
  <div id="app">
    <button @click="incValue">Increament the value</button>
    <b-tabs
      ref="datas"
      v-model="activetabid"
      :animated="false"
      size="is-small"
      @change="onTabChange"
    >
      <b-tab-item
        v-for="data in datas"
        :key="data.id"
        :label="data.name"
      >
        {{data.name}}
      </b-tab-item>
    </b-tabs>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      activetabid: 0,
      datas: []
    }
  },
  methods: {
    async onTabChange(value) {
      return alert('The vlaue is ' + value);
    },
    incValue() {
      this.$nextTick(() => {
        var numString = this.activetabid.toString();
        var id = this.activetabid;
        this.datas.push({id:id,name:numString});
        this.activetabid = this.activetabid + 1;
      });
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
