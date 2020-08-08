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
                const notification = await axios.get('http://testvue.thetunagroup.com?api=notifications')
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