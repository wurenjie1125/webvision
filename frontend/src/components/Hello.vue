<template>
    <div class="codemirror">
      <div class="edit-container">
        <p>html</p>
        <codemirror v-model="html" :options="editorOptionsHTML"></codemirror>
        <p>css</p>
        <codemirror v-model="css" :options="editorOptionsCSS"></codemirror>
        <p>js</p>
        <codemirror v-model="js" :options="editorOptionsCSS"></codemirror>
      </div>
      <div class="result-iframe">
        <iframe id="ifr">{{body}}</iframe>
      </div>
    </div>
</template>
<script>
  import { codemirror, CodeMirror } from 'vue-codemirror'
  import '../../node_modules/codemirror/keymap/sublime.js'
  import '../assets/css/code-edit.css'


  export default {
  components: {
    codemirror
  },
  data () {
    return {
      html: '<div>12121</div>',
      css:'*{margin:0;padding:0}',
      js:'console.log("3323")',
      editorOptionsHTML: {
        // codemirror options
        tabSize: 4,
        mode: 'text/html',
        theme: 'seti',
        lineNumbers: true,
        line: true,
        // sublime、emacs、vim三种键位模式，支持你的不同操作习惯
        keyMap: "sublime",
        // 按键映射，比如Ctrl键映射autocomplete，autocomplete是hint代码提示事件
        extraKeys: { "Ctrl": "autocomplete" },
        // 代码折叠
        foldGutter: true,
        gutters: ["CodeMirror-linenumbers", "CodeMirror-foldgutter"],
        // 选中文本自动高亮，及高亮方式
        styleSelectedText: true,
        highlightSelectionMatches: { showToken: /\w/, annotateScrollbar: true },
        // more codemirror config...
        // 如果有hint方面的配置，也应该出现在这里
      },
      editorOptionsCSS:{
        // codemirror options
        tabSize: 4,
        mode: 'css',
        theme: 'seti',
        lineNumbers: true,
        line: true,
        // sublime、emacs、vim三种键位模式，支持你的不同操作习惯
        keyMap: "sublime",
        // 按键映射，比如Ctrl键映射autocomplete，autocomplete是hint代码提示事件
        extraKeys: { "Ctrl": "autocomplete" },
        // 代码折叠
        foldGutter: true,
        gutters: ["CodeMirror-linenumbers", "CodeMirror-foldgutter"],
        // 选中文本自动高亮，及高亮方式
        styleSelectedText: true,
        highlightSelectionMatches: { showToken: /\w/, annotateScrollbar: true },
        // more codemirror config...
        // 如果有hint方面的配置，也应该出现在这里
      },
      editorOptionsJS:{
        // codemirror options
        tabSize: 4,
        mode: 'text/javascript',
        theme: 'seti',
        lineNumbers: true,
        line: true,
        // sublime、emacs、vim三种键位模式，支持你的不同操作习惯
        keyMap: "sublime",
        // 按键映射，比如Ctrl键映射autocomplete，autocomplete是hint代码提示事件
        extraKeys: { "Ctrl": "autocomplete" },
        // 代码折叠
        foldGutter: true,
        gutters: ["CodeMirror-linenumbers", "CodeMirror-foldgutter"],
        // 选中文本自动高亮，及高亮方式
        styleSelectedText: true,
        highlightSelectionMatches: { showToken: /\w/, annotateScrollbar: true },
        // more codemirror config...
        // 如果有hint方面的配置，也应该出现在这里
      }
    }
  },
  computed:{
    body:function(){
        var script = document.createElement('script');
        script.innerHTML = this.js;
        script = script.toLocaleString()  ;
        return this.html+script
    }
  },

  created(){
      console.log(this)
    console.log('this is current editor object', this.editor)
  },
  mounted(){

  },
  methods:{
    loadJS:function(scr){
      var ifr = document.querySelector('#ifr');
      var ifrdoc = ifr.contentWindow.document.body;
      var scriptNode = ifr.contentWindow.document.getElementsByTagName('script')[0];
      if(scriptNode){
        scriptNode.parentNode.removeChild(scriptNode)
      }
      var script = ifr.contentWindow.document.createElement('script');
      script.innerHTML = scr;
      ifrdoc.appendChild(script)
    }
  },
  watch:{
    html:function(val){
      var ifr = document.querySelector('#ifr');
      var ifrdoc = ifr.contentWindow.document.body;
      ifrdoc.innerHTML = val;
      this.loadJS(this.js)
    },
    css:function(val){
      var ifr = document.querySelector('#ifr');
      var ifrdoc = ifr.contentWindow.document.head;
      ifrdoc.innerHTML = '<meta charset="utf-8"><style>'+val+'</style>'

    },
    js:function(val){
      this.loadJS(val)

    }
  }



}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

