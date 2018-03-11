<template>
    <div class="u-topmargin u-downmargin">
        
        <form class="ui form">
            <h3 class="ui dividing header">Add Relation</h3>
            <div class="inline fields">
                <label>Source</label>
                <div class="two wide field">
                    <input type="text" placeholder="Source ID" v-model="newRelation.sourceId">
                </div>

                <div class="six wide field">
                    <input type="text" placeholder="Source Name" v-model="newRelation.sourceName">
                </div>
                <label>Target</label>
                <div class="two wide field">
                    <input type="text" placeholder="Target ID" v-model="newRelation.targetId">
                </div>
                <div class="six wide field">
                    <input type="text" placeholder="Target Name" v-model="newRelation.targetName">
                </div>
            </div>
            <button class="ui secondary button u-downmargin"
                    @click.prevent="addItem()">
                Add Item
            </button>
        </form>
        
        <h3 class="ui dividing header">Relation List</h3>
        <table class="ui celled table">
            <thead>
                <tr>
                    <th>Source ID</th>
                    <th>Source Name</th>
                    <th>Target ID</th>
                    <th>Target Name</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(relation, idx) in listRelation">
                    <td>{{ relation.sourceId }}</td>
                    <td>{{ relation.sourceName }}</td>
                    <td>{{ relation.targetId }}</td>
                    <td>{{ relation.targetName }}</td>
                    <td><button class="ui red small button" @click="removeItem(idx)">Remove
                        </button></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    props: ['listRelation'],
    data() {
        return {
            newRelation: {
                sourceId: '',
                sourceName: '',
                targetId: '',
                targetName: ''
            }
        }
    },
    methods: {
        addItem() {
            this.listRelation.push(this.newRelation);
            this.newRelation = {
                sourceId: '',
                sourceName: '',
                targetId: '',
                targetName: ''
            }
        },
        removeItem(idx) {
            this.listRelation.splice(idx, 1);
        }
    }
}
</script>

<style>
    .u-downmargin {
        margin-bottom: 30px;
    }
</style>