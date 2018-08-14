<template>
  <div class="home">
    <div ref="ckeditor" class="editor" style="margin-top: 100px;"></div>
  </div>
</template>
<script>
import InlineEditor from '@ckeditor/ckeditor5-build-inline'
// import InlineEditor from '@ckeditor/ckeditor5-editor-inline/src/inlineeditor'
// import Bold from '@ckeditor/ckeditor5-basic-styles/src/bold'
// import Italic from '@ckeditor/ckeditor5-basic-styles/src/italic'

export default {
  data () {
    return {
      editor: null
    }
  },
  mounted () {
    this.init()
  },
  methods: {
    init () {
      const el = this.$refs.ckeditor
      // InlineEditor.builtinPlugins.map(plugin => {
      //   console.log(plugin.pluginName)
      // })
      InlineEditor.create(el, {
        // plugins: [
        //   'Bold', 'Italic'
        // ],
        // toolbar: [
        //   'bold', 'italic'
        // ]
      }).then(editor => {
        this.editor = editor
      }).catch(err => {
        console.log(err.stack)
      })
    }
  },
  components: {
  }
}
</script>
<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.ck.ck-editor__editable.ck-editor__editable_inline, .editor {
  width: 100%;
  line-height: 30px;
  min-height: 40px;
  color: #333;
  font-size: 1rem;
  border: 1px solid #dcdfe6;
  padding: 5px 10px;
  word-break: break-word;
  &:hover {
    border-color: #c0c4cc;
  }
  &.ck-focused {
    border-color: #08a7a1;
    box-shadow: none;
  }
  &[disabled] {
    border: none;
    padding: 11px 0;
  }
  & > :first-child {
    margin-top: 0;
  }
  & > :last-child {
    margin-bottom: 0;
  }
  &.ck-rounded-corners {
    border-radius: 5px;
  }
}

.ck.ck-balloon-panel {
  position: absolute;
}

.ck.ck-content {
  [x-underline] {
    &:hover {
      background-color: #e8edf3;
    }
  }
}
.ck.ck-content {
  [highlight] {
    color: #f00;
  }
}
.editor-disabled {
  word-break: break-word;
  font-size: 14px;
  line-height: 20px;
  .highlight {
    color: #f00;
  }
  li {
    list-style: none;
  }
}
.editor-disabled .image {
  margin: 0;
  clear: both;
  text-align: center;
  & > img {
    display: block;
    margin: 0 auto;
    max-width: 100%;
  }
}
.editor-disabled {
  & .image-style-side,
  & .image-style-align-left,
  & .image-style-align-center,
  & .image-style-align-right {
    max-width: 50%;
  }
  & .image-style-side {
    float: right;
    margin-left: var(--ck-image-style-spacing);
  }
  & .image-style-align-left {
    float: left;
    margin-right: var(--ck-image-style-spacing);
  }
  & .image-style-align-center {
    margin-left: auto;
    margin-right: auto;
  }
  & .image-style-align-right {
    float: right;
    margin-left: var(--ck-image-style-spacing);
  }
}
</style>
