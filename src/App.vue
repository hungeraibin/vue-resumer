<template>
  <div id="app">
    <Topbar class="topbar"/>
    <main>
      <Editor class="editor"/>
      <Preview class="preview"/>
    </main>
  </div>
</template>

<script>
  //注册
  import Topbar from './components/Topbar.vue'
  import Editor from './components/Editor.vue'
  import Preview from './components/Preview.vue'
  export default {
    components: {
      Topbar, Editor, Preview
    }
  }
</script>

<style lang="scss" rel="stylesheet/scss">
  html, body, #app {
    height: 100%;
    overflow: hidden;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    height: 100vh;
    display: flex;
    flex-direction: column;
  }

  main {
    display: flex;
    flex: 1;

    > .preview {
      flex: 1;
    }

    > .editor {
      width: 20em;
    }
  }
</style>
