<template>
  <q-page class="flex flex-center">
    <q-btn label="Create File" @click="createFile" />
  </q-page>
</template>

<script>
// Filesystem module
const fs = require("fs");

//
const { dialog } = require("electron").remote;

export default {
  name: "PageIndex",

  methods: {
    createFile() {
      let content = "Hello, this is the content of the new file.";

      dialog.showSaveDialog(() => {
        if (filename === undefined) {
          console.log("no file name");
          return;
        }

        fs.writeFile(filename, content, err => {
          if (err) {
            console.log(`error writing file ${err.message}`);
            return;
          }

          alert("File successfully created!");
        });
      });
    }
  }
};
</script>
