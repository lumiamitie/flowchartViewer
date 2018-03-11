<template>
    <div class="u-topmargin">
        <h3 class="ui dividing header">Relation Graph</h3>
        <div class="ui attached segment u-fixed-height">
            <h4>Flow Chart</h4>
            <div id="flow">{{ graphRelation }}</div>
        </div>
        <div class="ui attached segment">
            <h4>Mermaid Code</h4>
            <div style="white-space: pre">{{ graphRelation }}</div>
        </div>
        <div class="ui attached segment">
            <button class="ui secondary button" @click="renderFlow()">
                Render FlowChart
            </button>
        </div>
    </div>
</template>

<script>
import mermaid from 'mermaid'

export default {
    beforeCreated() {
        mermaid.mermaidAPI.initialize({
            startOnLoad:false
        });
    },
    props: ['relations'],
    methods: {
        renderFlow() {
            var element = this.$el.querySelector('#flow');
            var insertSVG = function(svgCode, bindFunction) {
                element.innerHTML = svgCode;
            };
            
            if ( this.$el.querySelector('#svg-flow') ) {
                this.$el.querySelector('#svg-flow').remove()
            }
            mermaid.mermaidAPI.render('svg-flow', this.graphRelation, insertSVG);
        },
        graphize(rel) {
            var sid = rel.sourceId,
                sname = rel.sourceName === '' ? '' : '[' + rel.sourceName +']',
                tid = rel.targetId,
                tname = rel.targetName === '' ? '' : '[' + rel.targetName +']';
            return [sid, sname, '-->', tid, tname].join('');
        }
    },
    computed: {
        graphRelation() {
            var listRelation = ['graph LR'];
            for (let i=0; i<this.relations.length; i++) {
                var relation = this.relations[i];
                listRelation.push(this.graphize(relation))
            }
            return listRelation.join('\n')
        }
    }
}
</script>

<style>
    .u-fixed-height {
        min-height: 300px;
    }
</style>