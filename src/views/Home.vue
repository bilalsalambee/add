<template>
  <div class="home">
     <h1>Electron Auto Update Example</h1>
  <p id="version"></p>
    <img alt="Vue logo" src="../assets/logo.png" />
    <h1>hello this is me </h1>
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>

// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
    const { ipcRenderer } = require('electron');
    const version = document.getElementById('version');
    
    ipcRenderer.send('app_version');
    ipcRenderer.on('app_version', (event, arg) => {
      ipcRenderer.removeAllListeners('app_version');
      version.innerText = 'Version ' + arg.version;
    });

export default {
  name: "Home",
  components: {
    HelloWorld
  }
};
</script>
  <style>
    body {
      box-sizing: border-box;
      margin: 0;
      padding: 20px;
      font-family: sans-serif;
      background-color: #eaeaea;
      text-align: center;
    }
  </style>
