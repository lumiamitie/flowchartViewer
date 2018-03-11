<template>
    <div class="ui container">
        <div class="u-padding"></div>
        <h1 class="ui header u-topmargin">Mermaid Flowchart
            <div class="sub header">Ybigta Webdev Study Frontend Team</div>
        </h1>
        <app-viewer :relations="defaultRelations"></app-viewer>
        <app-editor :listRelation="defaultRelations"></app-editor>
    </div>
</template>

<script>
import Viewer from './components/Viewer.vue'
import Editor from './components/Editor.vue'
    
export default {
  name: 'app',
  data () {
    return {
      defaultRelations: [
            {
                sourceId: 'A',
                sourceName: '',
                targetId: 'B',
                targetName: ''
            },
            {
                sourceId: 'C',
                sourceName: '',
                targetId: 'B',
                targetName: ''
            },
            {
                sourceId: 'B',
                sourceName: '',
                targetId: 'D',
                targetName: 'End'
            }
        ]
    }
  },
  components: {
      'app-viewer': Viewer,
      'app-editor': Editor
  }
}
</script>

<style>
    .u-topmargin {
        margin-top: 30px;
    }
</style>
