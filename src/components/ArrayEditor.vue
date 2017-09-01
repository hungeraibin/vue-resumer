<template xmlns:v-on="http://www.w3.org/1999/xhtml" xmlns:v-bind="http://www.w3.org/1999/xhtml">
  <div>
    <h2>{{title}}</h2>
    <el-form>
      <div class="container" v-for="(work, index) in items" v-bind:key="index">
        <el-form-item v-for="key in keys" v-bind:label="labels[key] || key" v-bind:key="key">
          <el-input v-model="work[key]"></el-input>
        </el-form-item>
        <i class="el-icon-circle-close" v-on:click="removeItem(index)"></i>
        <hr>
      </div>
      <el-button type="primary" v-on:click="addItem">添加一项</el-button>
    </el-form>
  </div>
</template>

<script>
  export default {
    props: ['items', 'labels', 'title'],
    computed: {
      keys() {
        return Object.keys(this.items[0])
      }
    },
    methods: {
      addItem() {
        const empty = {};
        this.keys.map((key)=>{
          empty[key] = '';
        });
        this.items.push(empty)
      },
      removeItem(index) {
        this.items.splice(index, 1);
      }
    }
  }
</script>


