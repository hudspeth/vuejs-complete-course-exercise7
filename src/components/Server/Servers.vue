<template>
    <div class="col-xs-12 col-sm-6">
        <ul class="list-group">
            <li @click="getDetails(server)"
                    class="list-group-item"
                    v-for="server in servers">
                Server #{{ server.id }} : Status: {{ server.status }}
            </li>
        </ul>
    </div>
</template>

<script>
    import { eventBus } from '../../main'
    export default {
        data: function() {
            return {
                servers: [
                    { id: 1, status: "Normal"},
                    { id: 2, status: "Critical"},
                    { id: 3, status: "Unknown"},
                    { id: 4, status: "Normal"},
                    { id: 5, status: "Down"}
                ]
            }
        },
        methods: {
            getDetails(selection) {
                this.server = selection
                eventBus.serverSelected(selection)
            }
        }
    }
</script>

<style>

</style>
