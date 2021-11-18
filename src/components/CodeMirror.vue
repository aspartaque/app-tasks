<template>
  <div id='Codemirror'>

    <div class="task">
      <h2>javascript developer test</h2>
      <textarea v-model="model" id="editor"></textarea>
      <div class="card card-block">
        <pre>{{ model }}</pre>
      </div>
      <button id="txtName" @click="addMessage" class="btn">run</button>
      <h1 v-if="result == 'navI'">Success!</h1>
      <h2 id="p"></h2>
      <div id="frame">
        <iframe id="preview" frameborder="0" width="100%"></iframe>
      </div>
    </div>

  </div>
</template>

<script>
// import Vue from 'vue'
import * as CodeMirror from 'codemirror'
import 'codemirror/lib/codemirror.css'
import 'codemirror/theme/dracula.css'
import 'codemirror/mode/javascript/javascript.js'
import 'codemirror/addon/edit/closetag.js'
// import 'codemirror/mode/xml/xml.js'

var model = {
  text: "var name = 'Ivan';",
}
var result = '2';

export default {
  name: 'App',
  data() {
    return {
      model: model.text,
      result: result.text,
    };
  },
  mounted() {
    this.editor = CodeMirror.fromTextArea(document.getElementById('editor'), {
      lineNumbers: true,
      theme: 'dracula',
      mode: 'javascript',
      tabSize: 2,
      autoCloseTags: true,
    });
    //var scope = this;
    // this.editor.on('change', function(cm) {
    //   scope.model = cm.getValue();
    // });
  
  },
  methods: {
    addMessage(){
      // let jsCode = this.editor.getValue();
      let jsCode = '<scri' + 'pt>' + this.editor.getValue() + '</scr' + 'ipt>';
      let preview = document.querySelector("#preview").contentWindow.document;
      preview.open();
      preview.write(jsCode);
      preview.close();
    },
    GoNext() {
      this.status1 = true
    },
  },
};
</script>

<style>
  .CodeMirror {
    text-align: left;
  }
  .btn {
    width: 240px;
    height: 40px;
    background: none;
    border: 1px solid #282a36;
    color: #8690cb;
    transition: .3s;
  }
  .btn:hover {
    cursor: pointer;
    border: 1px solid #d34666;
    background: #282a36;
  }
  #frame {
    border: 1px solid #8690cb;
  }
</style>
