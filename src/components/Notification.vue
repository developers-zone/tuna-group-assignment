<template>
    <b-alert show dismissible variant="danger">
        {{ notificationMessage }} 
    </b-alert>
</template>

<script>
    import axios from "axios";
    export default {
        data() {
            return {
                notificationMessage: ''
            }
        },
        created () {
            this.getNotification()
        },
        methods: {
            async getNotification() {
                const notification = '{"response":"success","status ":200,"notifications":"Our cinemas will begin to reopen from 31 July"}';
                this.notificationMessage = notification.data.notifications
            }
        }
    }
</script>

<style lang="css">
    .alert {
        margin-bottom: 0!important;
    }
</style>
