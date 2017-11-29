<template>
    <div class="col-xs-12 col-sm-6">
        <p v-if="selectedServer === ''">Server Details are currently not updated</p>
        <div v-else>
            <p>Selected Server</p>
            <div class='serverId'>ID# {{ selectedServer.id }}</div>
            <div class='serverStatus'>Status: {{ selectedServer.status }}</div>
            <button @click="changeStatus">Change Status</button>
        </div>
    </div>

</template>

<script>
    import { eventBus } from '../../main'
    export default {
        data: function() {
            return {
                selectedServer: ''
            }
        },
        methods: {
            changeStatus() {
                this.selectedServer.status = 'Normal'
            }
        },
        created() {
            eventBus.$on('serverWasSelected', (server) => {
                this.selectedServer = server
            })
        }
    }
</script>

<style>

</style>
