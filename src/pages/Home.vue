<template>
    <div>
        <notification></notification>
        <main-header></main-header>
        <carousel></carousel>
    </div>
</template>

<script>
    import mainHeader from "../components/Header";
    import carousel from "../components/Carousel"
    import notification from "../components/Notification"

    export default {
       components: {
           notification,
           mainHeader,
           carousel
       },
        
    }
</script>
